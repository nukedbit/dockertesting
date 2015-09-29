# NukedBit DockerTesting

[![Build status](https://ci.appveyor.com/api/projects/status/1u8x31rhemdjjh0h/branch/master?svg=true)](https://ci.appveyor.com/project/nukedbit/nukedbit-dockertesting/branch/master)


This library was developed for easy and quick provision of a docker image using DockerRemote Api, this is aimed to be used on integrations testing, on a private vm, in fact currently no authentication meccanism is provided.

Currently only mongodb container is implemented using tutum/mongodb

        var dockerUrl = new Uri("DOCKER_URL");
        var client = new DockerClientConfiguration(dockerUrl)
             .CreateClient();
        var factory = new ContainerFactory(client);
        
        var testContainer = factory.Create(ContainerType.MongoDb, "anyname");

### Create Container

        await testContainer.CreateAsync(); 

### Start Container

        var started = await testContainer.StartAsync();             

### Get Container Ports (Private/Public)           

        await testContainer.GetPorts();

### Stopping Container

        await testContainer.Stop();        

### List all containers
        
        await Container.GetAllExistings(client,ContainerType.MongoDb)

### Remove

        await testContainer.Remove()


Each time the container is stopped the container is also removed so you get a clean container at each start

To connect to mongodb you must use the public port that should be 29017 and 30017 for admin


		Install-Package NukedBit.DockerTesting 