---
title: "ubuntu 15.04 broken drivers"
date: 2015-04-25
forum: Installation &amp; Upgrades
---

### Post by cgameing on 2015-04-25
ubuntu 15.04 broken drivers

Quick note: can anyone explain how to add spoiler tabs so i can hide the logs.
Steam Games wont start
and Minecraft Feed The Beast Fluids make the game crash, i tried installing the latest AMD drivers but that just made my system unstable, and i barely managed to get unity working so i could unistall them (when i got unity working the resolution was stuck at the minimum size and some gui was missing)

None of these problems happened when i was using 14.04
they only started now that im using 15.04

I got a r7-240 gpu
and if it makes a difference a a6-6400k cpu (but i dont use its graphics)

Any help is good help
Thanks

logs:

FTB trying to render fluids

```
---- Minecraft Crash Report ----
// My bad.

Time: 25/04/15 5:18 PM
Description: Unexpected error

java.lang.IllegalArgumentException: Cannot create a fluidstack from a null fluid
    at net.minecraftforge.fluids.FluidStack.<init>(FluidStack.java:29)
    at net.minecraftforge.fluids.FluidStack.<init>(FluidStack.java:59)
    at cofh.thermaldynamics.duct.fluid.TileFluidDuct.<init>(TileFluidDuct.java:41)
    at cofh.thermaldynamics.duct.fluid.TileFluidDuctFragile.<init>(TileFluidDuctFragile.java:39)
    at cofh.thermaldynamics.duct.DuctFactory$8.createTileEntity(DuctFactory.java:84)
    at cofh.thermaldynamics.duct.BlockDuct.func_149915_a(BlockDuct.java:90)
    at cofh.core.block.BlockCoFHBase.createTileEntity(BlockCoFHBase.java:63)
    at net.minecraft.world.chunk.Chunk.func_150806_e(Chunk.java:850)
    at net.minecraft.world.World.func_147438_o(World.java:2540)
    at cofh.core.block.BlockCoFHBase.onNeighborChange(BlockCoFHBase.java:187)
    at net.minecraft.world.World.func_147453_f(World.java:3875)
    at net.minecraft.world.World.func_147455_a(World.java:2603)
    at net.minecraft.world.chunk.Chunk.func_150806_e(Chunk.java:851)
    at net.minecraft.world.World.func_147438_o(World.java:2540)
    at net.minecraft.client.network.NetHandlerPlayClient.func_147273_a(NetHandlerPlayClient.java:1113)
    at net.minecraft.network.play.server.S35PacketUpdateTileEntity.func_148833_a(SourceFile:55)
    at net.minecraft.network.play.server.S35PacketUpdateTileEntity.func_148833_a(SourceFile:10)
    at net.minecraft.network.NetworkManager.func_74428_b(NetworkManager.java:212)
    at net.minecraft.client.multiplayer.PlayerControllerMP.func_78765_e(PlayerControllerMP.java:273)
    at net.minecraft.client.Minecraft.func_71407_l(Minecraft.java:1590)
    at net.minecraft.client.Minecraft.func_71411_J(Minecraft.java:961)
    at net.minecraft.client.Minecraft.func_99999_d(Minecraft.java:887)
    at net.minecraft.client.main.Main.main(SourceFile:148)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:497)
    at net.minecraft.launchwrapper.Launch.launch(Launch.java:135)
    at net.minecraft.launchwrapper.Launch.main(Launch.java:28)


A detailed walkthrough of the error, its code path and all known details is as follows:
---------------------------------------------------------------------------------------

-- Head --
Stacktrace:
    at net.minecraftforge.fluids.FluidStack.<init>(FluidStack.java:29)
    at net.minecraftforge.fluids.FluidStack.<init>(FluidStack.java:59)
    at cofh.thermaldynamics.duct.fluid.TileFluidDuct.<init>(TileFluidDuct.java:41)
    at cofh.thermaldynamics.duct.fluid.TileFluidDuctFragile.<init>(TileFluidDuctFragile.java:39)
    at cofh.thermaldynamics.duct.DuctFactory$8.createTileEntity(DuctFactory.java:84)
    at cofh.thermaldynamics.duct.BlockDuct.func_149915_a(BlockDuct.java:90)
    at cofh.core.block.BlockCoFHBase.createTileEntity(BlockCoFHBase.java:63)
    at net.minecraft.world.chunk.Chunk.func_150806_e(Chunk.java:850)
    at net.minecraft.world.World.func_147438_o(World.java:2540)
    at cofh.core.block.BlockCoFHBase.onNeighborChange(BlockCoFHBase.java:187)
    at net.minecraft.world.World.func_147453_f(World.java:3875)
    at net.minecraft.world.World.func_147455_a(World.java:2603)
    at net.minecraft.world.chunk.Chunk.func_150806_e(Chunk.java:851)
    at net.minecraft.world.World.func_147438_o(World.java:2540)
    at net.minecraft.client.network.NetHandlerPlayClient.func_147273_a(NetHandlerPlayClient.java:1113)
    at net.minecraft.network.play.server.S35PacketUpdateTileEntity.func_148833_a(SourceFile:55)
    at net.minecraft.network.play.server.S35PacketUpdateTileEntity.func_148833_a(SourceFile:10)
    at net.minecraft.network.NetworkManager.func_74428_b(NetworkManager.java:212)
    at net.minecraft.client.multiplayer.PlayerControllerMP.func_78765_e(PlayerControllerMP.java:273)

-- Affected level --
Details:
    Level name: MpServer
    All players: 1 total; [EntityClientPlayerMP['USERNAME'/143, l='MpServer', x=43.31, y=94.31, z=70.00]]
    Chunk stats: MultiplayerChunkCache: 20, 20
    Level seed: 0
    Level generator: ID 00 - default, ver 1. Features enabled: false
    Level generator options: 
    Level spawn location: World: (3,81,80), Chunk: (at 3,5,0 in 0,5; contains blocks 0,0,80 to 15,255,95), Region: (0,0; contains chunks 0,0 to 31,31, blocks 0,0,0 to 511,255,511)
    Level time: 5104786 game time, 2303614 day time
    Level dimension: 0
    Level storage version: 0x00000 - Unknown?
    Level weather: Rain time: 0 (now: false), thunder time: 0 (now: false)
    Level game mode: Game mode: survival (ID 0). Hardcore: false. Cheats: false
    Forced entities: 27 total; [EntityItem['item.item.string'/142, l='MpServer', x=69.56, y=70.13, z=105.97], EntityZombie['Zombie'/82, l='MpServer', x=25.47, y=21.00, z=55.94], EntityClientPlayerMP['USERNAME'/143, l='MpServer', x=43.31, y=94.31, z=70.00], EntityHat['unknown'/24, l='MpServer', x=8.50, y=66.62, z=8.50], EntityCreeper['Creeper'/94, l='MpServer', x=40.50, y=27.00, z=55.50], EntitySpider['Spider'/95, l='MpServer', x=40.28, y=71.00, z=49.97], EntityConcussionCreeper['Concussion Creeper'/96, l='MpServer', x=37.50, y=71.00, z=52.50], EntitySpider['Spider'/97, l='MpServer', x=43.00, y=71.00, z=50.22], EntityCreeper['Creeper'/101, l='MpServer', x=56.50, y=38.00, z=54.50], EntityItem['item.item.string'/103, l='MpServer', x=59.66, y=71.13, z=51.19], EntityBat['Bat'/104, l='MpServer', x=62.78, y=49.22, z=86.47], EntityTFNagaSegment['unknown'/44, l='MpServer', x=0.00, y=0.00, z=0.00], EntityTFNagaSegment['unknown'/45, l='MpServer', x=0.00, y=0.00, z=0.00], EntityTFNagaSegment['unknown'/46, l='MpServer', x=0.00, y=0.00, z=0.00], EntityTFNagaSegment['unknown'/47, l='MpServer', x=0.00, y=0.00, z=0.00], EntityTFNagaSegment['unknown'/48, l='MpServer', x=0.00, y=0.00, z=0.00], EntityTFNagaSegment['unknown'/49, l='MpServer', x=0.00, y=0.00, z=0.00], EntityTFNagaSegment['unknown'/50, l='MpServer', x=0.00, y=0.00, z=0.00], EntityCreeper['Creeper'/114, l='MpServer', x=62.56, y=70.00, z=94.06], EntityTFNagaSegment['unknown'/51, l='MpServer', x=0.00, y=0.00, z=0.00], EntitySpider['Spider'/115, l='MpServer', x=67.00, y=71.00, z=91.09], EntityTFNagaSegment['unknown'/52, l='MpServer', x=0.00, y=0.00, z=0.00], EntitySpider['Spider'/116, l='MpServer', x=67.34, y=71.00, z=95.25], EntityTFNagaSegment['unknown'/53, l='MpServer', x=0.00, y=0.00, z=0.00], EntitySpider['Spider'/117, l='MpServer', x=68.63, y=71.00, z=103.81], EntityTFNagaSegment['unknown'/54, l='MpServer', x=0.00, y=0.00, z=0.00], EntityTFNagaSegment['unknown'/55, l='MpServer', x=0.00, y=0.00, z=0.00]]
    Retry entities: 0 total; []
    Server brand: fml,forge
    Server type: Non-integrated multiplayer server
Stacktrace:
    at net.minecraft.client.multiplayer.WorldClient.func_72914_a(WorldClient.java:373)
    at net.minecraft.client.Minecraft.func_71396_d(Minecraft.java:2432)
    at net.minecraft.client.Minecraft.func_99999_d(Minecraft.java:916)
    at net.minecraft.client.main.Main.main(SourceFile:148)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:497)
    at net.minecraft.launchwrapper.Launch.launch(Launch.java:135)
    at net.minecraft.launchwrapper.Launch.main(Launch.java:28)

-- System Details --
Details:
    Minecraft Version: 1.7.10
    Operating System: Linux (amd64) version 3.19.0-15-generic
    Java Version: 1.8.0_45-internal, Oracle Corporation
    Java VM Version: OpenJDK 64-Bit Server VM (mixed mode), Oracle Corporation
    Memory: 3403852352 bytes (3246 MB) / 4600627200 bytes (4387 MB) up to 4600627200 bytes (4387 MB)
    JVM Flags: 22 total; -Xms4500m -Xmx4500m -XX:MaxPermSize=128M -XX:NewRatio=3 -Xrs -XX:+UseThreadPriorities -XX:CMSFullGCsBeforeCompaction=1 -XX:SoftRefLRUPolicyMSPerMB=20480 -XX:+CMSParallelRemarkEnabled -XX:+UseParNewGC -XX:+UseAdaptiveSizePolicy -XX:+DisableExplicitGC -Xnoclassgc -Xoss4M -Xss4M -XX:+UseFastAccessorMethods -XX:+UseCMSInitiatingOccupancyOnly -XX:CMSInitiatingOccupancyFraction=75 -XX:UseSSE=4 -XX:+UseCMSCompactAtFullCollection -XX:ParallelGCThreads=4 -XX:MaxTenuringThreshold=3
    AABB Pool Size: 0 (0 bytes; 0 MB) allocated, 0 (0 bytes; 0 MB) used
    IntCache: cache: 0, tcache: 0, allocated: 15, tallocated: 95
    FML: MCP v9.05 FML v7.10.112.1370 Minecraft Forge 10.13.3.1370 145 mods loaded, 145 mods active
    mcp{9.05} [Minecraft Coder Pack] (minecraft.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    FML{7.10.112.1370} [Forge Mod Loader] (forge-1.7.10-10.13.3.1370-1.7.10.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    Forge{10.13.3.1370} [Minecraft Forge] (forge-1.7.10-10.13.3.1370-1.7.10.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    appliedenergistics2-core{rv2-beta-pre9} [AppliedEnergistics2 Core] (minecraft.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    Aroma1997Core{1.0.2.13} [Aroma1997Core] (Aroma1997Core-1.7.10-1.0.2.13.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    CodeChickenCore{1.0.4.35} [CodeChicken Core] (minecraft.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    InfiniBows{1.3.0 build 20} [InfiniBows] (minecraft.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    MobiusCore{1.2.3} [MobiusCore] (minecraft.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    NotEnoughItems{1.0.4.90} [Not Enough Items] (NotEnoughItems-1.7.10-1.0.4.90-universal.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    ThaumicTinkerer-preloader{0.1} [Thaumic Tinkerer Core] (minecraft.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    OpenModsCore{0.6} [OpenModsCore] (minecraft.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    <CoFH ASM>{000} [CoFH ASM Data Initialization] (minecraft.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    debug{1.0} [debug] (denseores-1.5.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    appliedenergistics2{rv2-beta-pre9} [Applied Energistics 2] (appliedenergistics2-rv2-beta-pre9.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    Aroma1997CoreHelper{1.0.2.13} [Aroma1997Core|Helper] (Aroma1997Core-1.7.10-1.0.2.13.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    AromaBackup{0.0.0.5} [AromaBackup] (AromaBackup-1.7.10-0.0.0.5.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    BiblioCraft{1.10.2} [BiblioCraft] (BiblioCraft[v1.10.2][MC1.7.10].jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    Mantle{1.7.10-0.3.2.jenkins184} [Mantle] (Mantle-1.7.10-0.3.2.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    Natura{2.2.0} [Natura] (natura-1.7.10-2.2.0.1.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    BiomesOPlenty{2.1.0} [Biomes O' Plenty] (BiomesOPlenty-1.7.10-2.1.0.1067-universal.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    BiblioWoodsBoP{1.9} [BiblioWoods Biomes O'Plenty Edition] (BiblioWoods[BiomesOPlenty][v1.9].jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    IC2{2.2.695-experimental} [IndustrialCraft 2] (industrialcraft-2-2.2.695-experimental.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    CoFHCore{1.7.10R3.0.0RC7} [CoFH Core] (CoFHCore-[1.7.10]3.0.0RC7-211.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    BuildCraft|Core{6.4.4} [BuildCraft] (buildcraft-6.4.4.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    Forestry{3.4.0.7} [Forestry for Minecraft] (forestry_1.7.10-3.4.0.7.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    BiblioWoodsForestry{1.7} [BiblioWoods Forestry Edition] (BiblioWoods[Forestry][v1.7].jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    BiblioWoodsNatura{1.5} [BiblioWoods Natura Edition] (BiblioWoods[Natura][v1.5].jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    ThermalFoundation{1.7.10R1.0.0RC7} [Thermal Foundation] (ThermalFoundation-[1.7.10]1.0.0RC7-62.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    ThermalExpansion{1.7.10R4.0.0RC7} [Thermal Expansion] (ThermalExpansion-[1.7.10]4.0.0RC7-141.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    BigReactors{0.4.2A2} [Big Reactors] (BigReactors-0.4.2A2.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    BinnieCore{2.0-pre8} [Binnie Core] (binnie-mods-2.0-pre8.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    Botany{2.0-pre8} [Botany] (binnie-mods-2.0-pre8.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    ExtraBees{2.0-pre8} [Extra Bees] (binnie-mods-2.0-pre8.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    ExtraTrees{2.0-pre8} [Extra Trees] (binnie-mods-2.0-pre8.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    Genetics{2.0-pre8} [Genetics] (binnie-mods-2.0-pre8.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    AWWayofTime{v1.3.0b} [Blood Magic: Alchemical Wizardry] (BloodMagic-1.7.10-1.3.0b-3.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    Baubles{1.0.1.10} [Baubles] (Baubles-1.7.10-1.0.1.10.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    Thaumcraft{4.2.3.5} [Thaumcraft] (Thaumcraft-1.7.10-4.2.3.5.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    Botania{r1.5-165} [Botania] (Botania r1.5-165.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    BuildCraft|Transport{6.4.4} [BC Transport] (buildcraft-6.4.4.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    BuildCraft|Silicon{6.4.4} [BC Silicon] (buildcraft-6.4.4.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    BuildCraft|Builders{6.4.4} [BC Builders] (buildcraft-6.4.4.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    BuildCraft|Energy{6.4.4} [BC Energy] (buildcraft-6.4.4.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    BuildCraft|Factory{6.4.4} [BC Factory] (buildcraft-6.4.4.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    BuildCraft|Compat{6.4.0} [BuildCraft Compat] (buildcraft-compat-6.4.1.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    CarpentersBlocks{3.3.5} [Carpenter's Blocks] (Carpenter's Blocks v3.3.5 - MC 1.7.10.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    ChickenChunks{1.3.4.17} [ChickenChunks] (ChickenChunks-1.7.10-1.3.4.17-universal.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    Railcraft{9.5.0.0} [Railcraft] (Railcraft_1.7.10-9.5.0.0.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    TwilightForest{2.3.4} [The Twilight Forest] (twilightforest-1.7.10-2.3.4.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    ForgeMultipart{1.1.1.320} [Forge Multipart] (ForgeMultipart-1.7.10-1.1.1.320-universal.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    chisel{2.3.7.34} [Chisel 2] (Chisel2-2.3.7.34.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    CompactSolars{4.4.39.315} [Compact Solar Arrays] (CompactSolars-1.7.10-4.4.39.315-universal.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    ComputerCraft{1.73} [ComputerCraft] (ComputerCraft1.73.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    CustomMainMenu{1.2} [Custom Main Menu] (CustomMainMenu-MC1.7.10-1.2.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    MineFactoryReloaded{1.7.10R2.8.0RC8} [MineFactory Reloaded] (MineFactoryReloaded-[1.7.10]2.8.0RC8-86.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    EnderIO{1.7.10-2.2.8.349} [Ender IO] (EnderIO-1.7.10-2.2.8.349.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    EnderStorage{1.4.5.27} [EnderStorage] (EnderStorage-1.7.10-1.4.5.27-universal.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    EnderTech{1.7.10-0.3.0.364} [EnderTech] (EnderTech-1.7.10-0.3.0.364.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    EnderZoo{1.7.10-1.0.9.18} [Ender Zoo] (EnderZoo-1.7.10-1.0.9.18.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    ExtraUtilities{1.2.2} [Extra Utilities] (extrautilities-1.2.2.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    factorization.notify{1.0} [Factorization Notification System] (Factorization-1.7.10-0.8.88.8.8888g.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    factorization.dimensionalSlice{0.8.88.8.8888g} [Factorization Dimensional Slices] (Factorization-1.7.10-0.8.88.8.8888g.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    factorization{0.8.88.8.8888g} [Factorization] (Factorization-1.7.10-0.8.88.8.8888g.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    factorization.misc{0.8.88.8.8888g} [Factorization Miscellaneous Nonsense] (Factorization-1.7.10-0.8.88.8.8888g.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    FastCraft{1.19} [FastCraft] (fastcraft-1.19.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    FlatSigns{2.1.0.19} [Flat Signs] (FlatSigns-1.7.10-universal-2.1.0.19.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    funkylocomotion{1.0} [Funky Locomotion] (funky-locomotion-1.7.10-beta-5a.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    iChunUtil{4.1.3} [iChunUtil] (iChunUtil-4.1.3.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    Hats{4.0.1} [Hats] (Hats-4.0.1.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    HatStand{4.0.0} [HatStand] (HatStand-4.0.0.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    HelpFixer{1.0.7} [HelpFixer] (HelpFixer-1.0.7.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    IC2NuclearControl{2.1.2a} [Nuclear Control 2] (IC2NuclearControl-2.1.2a.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    inpure|core{1.7.10R1.0.0B9} [INpureCore] (INpureCore-[1.7.10]1.0.0B9-54.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    inventorytweaks{1.58-147-645ca10} [Inventory Tweaks] (InventoryTweaks-1.58-147.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    IronChest{6.0.62.742} [Iron Chest] (ironchest-1.7.10-6.0.62.742-universal.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    Waila{1.5.10} [Waila] (Waila-1.5.10_1.7.10.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    JABBA{1.2.1} [JABBA] (Jabba-1.2.1a_1.7.10.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    journeymap{5.0.1} [JourneyMap] (JourneyMap5.0.1_Unlimited_MC1.7.10.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    TConstruct{1.7.10-1.8.3.build919} [Tinkers' Construct] (TConstruct-1.7.10-1.8.3b.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    ThaumicTinkerer{unspecified} [Thaumic Tinkerer] (ThaumicTinkerer-2.5-1.7.10-471.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    MagicBees{1.7.10-2.1.22} [Magic Bees] (magicbees-1.7.10-2.1.22.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    MineFactoryReloaded|CompatAppliedEnergistics{1.7.10R2.8.0RC8} [MFR Compat: Applied Energistics] (MineFactoryReloaded-[1.7.10]2.8.0RC8-86.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    MineFactoryReloaded|CompatAtum{1.7.10R2.8.0RC8} [MFR Compat: Atum] (MineFactoryReloaded-[1.7.10]2.8.0RC8-86.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    MineFactoryReloaded|CompatBackTools{1.7.10R2.8.0RC8} [MFR Compat: BackTools] (MineFactoryReloaded-[1.7.10]2.8.0RC8-86.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    MineFactoryReloaded|CompatBuildCraft{1.7.10R2.8.0RC8} [MFR Compat: BuildCraft] (MineFactoryReloaded-[1.7.10]2.8.0RC8-86.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    MineFactoryReloaded|CompatChococraft{1.7.10R2.8.0RC8} [MFR Compat: Chococraft] (MineFactoryReloaded-[1.7.10]2.8.0RC8-86.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    MineFactoryReloaded|CompatExtraBiomes{1.7.10R2.8.0RC8} [MFR Compat: ExtraBiomes] (MineFactoryReloaded-[1.7.10]2.8.0RC8-86.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    MineFactoryReloaded|CompatForestry{1.7.10R2.8.0RC8} [MFR Compat: Forestry] (MineFactoryReloaded-[1.7.10]2.8.0RC8-86.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    MineFactoryReloaded|CompatForgeMicroblock{1.7.10R2.8.0RC8} [MFR Compat: ForgeMicroblock] (MineFactoryReloaded-[1.7.10]2.8.0RC8-86.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    MineFactoryReloaded|CompatIC2{1.7.10R2.8.0RC8} [MFR Compat: IC2] (MineFactoryReloaded-[1.7.10]2.8.0RC8-86.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    Mystcraft{0.11.0.00} [Mystcraft] (mystcraft-1.7.10-0.11.0.00.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    MineFactoryReloaded|CompatMystcraft{1.7.10R2.8.0RC8} [MFR Compat: Mystcraft] (MineFactoryReloaded-[1.7.10]2.8.0RC8-86.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    MrTJPCoreMod{1.0.5.11} [MrTJPCore] (MrTJPCore-1.7.10-1.0.5.11-universal.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    ProjRed|Core{4.5.15.75} [ProjectRed] (ProjectRed-1.7.10-4.5.15.75-Base.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    ProjRed|Exploration{4.5.15.75} [ProjectRed-Exploration] (ProjectRed-1.7.10-4.5.15.75-World.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    MineFactoryReloaded|CompatProjRed{1.7.10R2.8.0RC8} [MFR Compat ProjectRed] (MineFactoryReloaded-[1.7.10]2.8.0RC8-86.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    MineFactoryReloaded|CompatRailcraft{1.7.10R2.8.0RC8} [MFR Compat: Railcraft] (MineFactoryReloaded-[1.7.10]2.8.0RC8-86.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    MineFactoryReloaded|CompatRP2{1.7.10R2.8.0RC8} [MFR Compat: RP2] (MineFactoryReloaded-[1.7.10]2.8.0RC8-86.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    MineFactoryReloaded|CompatSufficientBiomes{1.7.10R2.8.0RC8} [MFR Compat: Sufficient Biomes] (MineFactoryReloaded-[1.7.10]2.8.0RC8-86.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    MineFactoryReloaded|CompatThaumcraft{1.7.10R2.8.0RC8} [MFR Compat: Thaumcraft] (MineFactoryReloaded-[1.7.10]2.8.0RC8-86.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    MineFactoryReloaded|CompatThermalExpansion{1.7.10R2.8.0RC8} [MFR Compat: Thermal Expansion] (MineFactoryReloaded-[1.7.10]2.8.0RC8-86.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    MineFactoryReloaded|CompatTConstruct{1.7.10R2.8.0RC8} [MFR Compat: Tinkers' Construct] (MineFactoryReloaded-[1.7.10]2.8.0RC8-86.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    MineFactoryReloaded|CompatTwilightForest{1.7.10R2.8.0RC8} [MFR Compat: TwilightForest] (MineFactoryReloaded-[1.7.10]2.8.0RC8-86.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    MineFactoryReloaded|CompatVanilla{1.7.10R2.8.0RC8} [MFR Compat: Vanilla] (MineFactoryReloaded-[1.7.10]2.8.0RC8-86.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    MineTweaker3{3.0.9B} [MineTweaker 3] (MineTweaker3-1.7.10-3.0.9C.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    numina{0.4.0.100} [Numina] (Numina-0.4.0.100.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    powersuits{0.11.0.178} [MachineMuse's Modular Powersuits] (ModularPowersuits-0.11.0.178.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    Morph{0.9.1} [Morph] (Morph-Beta-0.9.1.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    NEIAddons{1.12.5.17} [NEI Addons] (neiaddons-mc1710-1.12.5.17.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    NEIAddons|Botany{1.12.5.17} [NEI Addons: Botany] (neiaddons-mc1710-1.12.5.17.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    NEIAddons|Forestry{1.12.5.17} [NEI Addons: Forestry] (neiaddons-mc1710-1.12.5.17.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    NEIAddons|CraftingTables{1.12.5.17} [NEI Addons: Crafting Tables] (neiaddons-mc1710-1.12.5.17.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    NEIAddons|ExNihilo{1.12.5.17} [NEI Addons: Ex Nihilo] (neiaddons-mc1710-1.12.5.17.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    neiintegration{1.0.7} [NEI Integration] (NEIIntegration-MC1.7.10-1.0.7.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    NotEnoughCodecs{0.3} [NotEnoughCodecs] (NotEnoughCodecs-1.7.10-0.3-snapshot-11.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    notenoughkeys{@MOD_VERSION@} [NotEnoughKEys] (NotEnoughKeys-1.7.10-1.0.0b29.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    ObsidiPlates{3.0.0.18} [ObsidiPlates] (ObsidiPlates-1.7.10-universal-3.0.0.18.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    OpenMods{0.6} [OpenMods] (OpenModsLib-1.7.10-0.6.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    OpenPeripheralCore{0.5.0} [OpenPeripheralCore] (OpenPeripheralCore-1.7.10-0.5.0.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    OpenPeripheral{0.2.0} [OpenPeripheralAddons] (OpenPeripheralAddons-1.7.10-0.2.0.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    OpenBlocks{1.3} [OpenBlocks] (OpenBlocks-1.7.10-1.3.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    OpenPeripheralIntegration{0.1.0} [OpenPeripheralIntegration] (OpenPeripheralIntegration-1.7.10-0.1.0.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    PneumaticCraft{1.6.3-65} [PneumaticCraft] (PneumaticCraft-1.7.10-1.6.3-65-universal.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    ProjRed|Transmission{4.5.15.75} [ProjectRed-Transmission] (ProjectRed-1.7.10-4.5.15.75-Integration.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    ProjRed|Compatibility{4.5.15.75} [ProjectRed-Compatibility] (ProjectRed-1.7.10-4.5.15.75-Compat.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    ProjRed|Integration{4.5.15.75} [ProjectRed-Integration] (ProjectRed-1.7.10-4.5.15.75-Integration.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    ProjRed|Illumination{4.5.15.75} [ProjectRed-Illumination] (ProjectRed-1.7.10-4.5.15.75-Lighting.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    RedstoneArsenal{1.7.10R1.1.0RC7} [Redstone Arsenal] (RedstoneArsenal-[1.7.10]1.1.0RC7-65.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    ResourceLoader{1.0} [Resource Loader] (ResourceLoader-1.0.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    StevesCarts{2.0.0.b18} [Steve's Carts 2] (StevesCarts2.0.0.b18.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    StevesFactoryManager{A93} [Steve's Factory Manager] (StevesFactoryManagerA93.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    ThaumicExploration{0.6.0} [Thaumic Exploration] (ThaumicExploration-1.7.10-1.1-37.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    ThermalDynamics{1.7.10R1.0.0RC7} [Thermal Dynamics] (ThermalDynamics-[1.7.10]1.0.0RC7-98.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    TiCTooltips{1.2.3} [TiC Tooltips] (TiCTooltips-mc1.7.10-1.2.3.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    TMechworks{0.2.14.100} [Tinkers' Mechworks] (TMechworks-1.7.10-0.2.14.100.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    Translocator{1.1.1.14} [Translocator] (Translocator-1.7.10-1.1.1.14-universal.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    WailaHarvestability{1.1.2} [Waila Harvestability] (WailaHarvestability-mc1.7.x-1.1.2.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    witchery{0.23.2} [Witchery] (witchery-1.7.10-0.23.2.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    WR-CBE|Core{1.4.1.9} [WR-CBE Core] (WR-CBE-1.7.10-1.4.1.9-universal.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    WR-CBE|Addons{1.4.1.9} [WR-CBE Addons] (WR-CBE-1.7.10-1.4.1.9-universal.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    WR-CBE|Logic{1.4.1.9} [WR-CBE Logic] (WR-CBE-1.7.10-1.4.1.9-universal.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    McMultipart{1.1.1.320} [Minecraft Multipart Plugin] (ForgeMultipart-1.7.10-1.1.1.320-universal.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    aobd{2.5.0} [Another One Bites The Dust] (AOBD-2.5.0.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    denseores{1.0} [Dense Ores] (denseores-1.5.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    ForgeMicroblock{1.1.1.320} [Forge Microblocks] (ForgeMultipart-1.7.10-1.1.1.320-universal.jar) Unloaded->Constructed->Pre-initialized->Initialized->Post-initialized->Available
    OpenModsLib crash transformers: [stencil_patches:FINISHED],[movement_callback:FINISHED],[map_gen_fix:FINISHED],[gl_capabilities_hook:FINISHED],[player_render_hook:FINISHED]
    AE2 Version: beta rv2-beta-pre9 for Forge 10.13.2.1230
    Mantle Environment: Environment healthy.
    CoFHCore: -[1.7.10]3.0.0RC7-211
    ThermalFoundation: -[1.7.10]1.0.0RC7-62
    ThermalExpansion: -[1.7.10]4.0.0RC7-141
    MineFactoryReloaded: -[1.7.10]2.8.0RC8-86
    TConstruct Environment: Environment healthy.
    RedstoneArsenal: -[1.7.10]1.1.0RC7-65
    ThermalDynamics: -[1.7.10]1.0.0RC7-98
    Stencil buffer state: Function set: GL30, pool: internal, bits: 8
    AE2 Integration: IC2:ON, RotaryCraft:OFF, RC:ON, BC:ON, MJ6:OFF, MJ5:OFF, RF:ON, RFItem:ON, MFR:ON, DSU:ON, FZ:ON, FMP:ON, RB:OFF, CLApi:OFF, Waila:ON, InvTweaks:ON, NEI:ON, CraftGuide:OFF, Mekanism:OFF, ImmibisMicroblocks:OFF, BetterStorage:OFF
    Launched Version: 1.7.10-Forge10.13.3.1370-1.7.10
    LWJGL: 2.9.1
    OpenGL: Gallium 0.4 on AMD OLAND GL version 3.0 Mesa 10.5.2, X.Org
    GL Caps: Using GL 1.3 multitexturing.
Using framebuffer objects because OpenGL 3.0 is supported and separate blending is supported.
Anisotropic filtering is supported and maximum anisotropy is 16.
Shaders are available because OpenGL 2.1 is supported.

    Is Modded: Definitely; Client brand changed to 'fml,forge'
    Type: Client (map_client.txt)
    Resource Packs: []
    Current Language: English (US)
    Profiler Position: N/A (disabled)
    Vec3 Pool Size: 0 (0 bytes; 0 MB) allocated, 0 (0 bytes; 0 MB) used
    Anisotropic Filtering: Off (1)


This is the log for me trying to start bsiege:

Running Steam on ubuntu 15.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1428965940)
Installing breakpad exception handler for appid(steam)/version(1428965940)
Installing breakpad exception handler for appid(steam)/version(1428965940)
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
Installing breakpad exception handler for appid(steam)/version(1428965940)
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
Installing breakpad exception handler for appid(steamwebhelper)/version(20150413151658)
Installing breakpad exception handler for appid(steamwebhelper)/version(1428938218)
[0425/172716:ERROR:nss_util.cc(1018)] Failed to load NSS libraries.
Installing breakpad exception handler for appid(steamwebhelper)/version(20150413151658)
Installing breakpad exception handler for appid(steamwebhelper)/version(1428965940)
Installing breakpad exception handler for appid(steamwebhelper)/version(1428965940)
Installing breakpad exception handler for appid(steam)/version(1428965940)
Installing breakpad exception handler for appid(steam)/version(1428965940)
Installing breakpad exception handler for appid(steam)/version(1428965940)
Installing breakpad exception handler for appid(steam)/version(1428965940)
Installing breakpad exception handler for appid(steam)/version(1428965940)
FillInMachineIDInfo took a total of 6 milliseconds
Installing breakpad exception handler for appid(steam)/version(1428965940)
Installing breakpad exception handler for appid(steam)/version(1428965940)
Installing breakpad exception handler for appid(steam)/version(1428965940)

** (steam:5869): WARNING **: Unknown device type 14

** (steam:5869): WARNING **: Could not create object for /org/freedesktop/NetworkManager/Devices/0: unknown object type
Installing breakpad exception handler for appid(steam)/version(1428965940)

** (steam:5869): WARNING **: Ignoring invalid property 'address-labels'

** (steam:5869): WARNING **: Ignoring invalid property 'address-labels'
Generating new string page texture 2: 48x256, total string texture memory is 49.15 KB
Generating new string page texture 3: 256x256, total string texture memory is 311.30 KB
Installing breakpad exception handler for appid(steam)/version(1428965940)
Installing breakpad exception handler for appid(steam)/version(1428965940)
Adding licenses for the following package(s): 0, 218, 8183, 21327, 21341, 21353, 21359, 21469, 44226, 44625, 45123, 47466, 59273, 59607, 64700, 64701, 65525, 66253
roaming config store loaded successfully - 1547 bytes.
migrating temporary roaming config store
Installing breakpad exception handler for appid(steam)/version(1428965940)
Failed to init SteamVR because it isn't installed
ExecCommandLine: ""/home/USERNAME/.local/share/Steam/ubuntu12_32/steam" "
Installing breakpad exception handler for appid(steam)/version(1428965940)
System startup time: 6.41 seconds
[0425/172722:ERROR:renderer_main.cc(227)] Running without renderer sandbox
Generating new string page texture 71: 128x256, total string texture memory is 442.37 KB
Generating new string page texture 72: 64x256, total string texture memory is 507.90 KB
Generating new string page texture 73: 32x256, total string texture memory is 540.67 KB
Generating new string page texture 74: 512x256, total string texture memory is 1.06 MB
Generating new string page texture 75: 128x256, total string texture memory is 131.07 KB
Generating new string page texture 76: 128x256, total string texture memory is 1.20 MB

(steam:5869): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5869): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5869): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5869): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5869): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5869): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5869): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5869): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5869): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5869): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5869): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5869): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5869): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5869): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5869): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5869): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5869): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.
Generating new string page texture 83: 384x256, total string texture memory is 1.59 MB
Generating new string page texture 84: 24x256, total string texture memory is 1.61 MB
Generating new string page texture 85: 8x256, total string texture memory is 1.62 MB
KeyValues Error: LoadFromBuffer: missing {   (current key: '<!DOCTYPE') in file appnews [offset: 14]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'public') in file appnews [offset: 62]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'http://www.w3.org/TR/html4/loose.dtd') in file appnews [offset: 102]

KeyValues Error: LoadFromBuffer: missing {   (current key: '<html>') in file appnews [offset: 118]

KeyValues Error: LoadFromBuffer: missing {   (current key: '<META') in file appnews [offset: 136]

KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 151]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'content') in file appnews [offset: 160]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'text/html; charset=UTF-8') in file appnews [offset: 189]

KeyValues Error: LoadFromBuffer: missing {   (current key: '<title>Steam') in file appnews [offset: 213]

KeyValues Error: LoadFromBuffer: missing {   (current key: '::') in file appnews [offset: 230]

KeyValues Error: LoadFromBuffer: missing {   (current key: '<link') in file appnews [offset: 241]

KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 257]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 263]

KeyValues Error: LoadFromBuffer: missing {   (current key: '/favicon.ico') in file appnews [offset: 282]

KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 297]

KeyValues Error: LoadFromBuffer: missing {   (current key: '/>') in file appnews [offset: 307]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 313]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'http://steamcommunity-a.akamaihd.net/public/shared/css/motiva_sans.css?v=F3z3QpekjE2f') in file appnews [offset: 404]

KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 417]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'type') in file appnews [offset: 423]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'text/css') in file appnews [offset: 435]

KeyValues Error: LoadFromBuffer: missing {   (current key: '<link') in file appnews [offset: 446]

KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 530]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'rel') in file appnews [offset: 535]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'stylesheet') in file appnews [offset: 552]

KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 563]

KeyValues Error: LoadFromBuffer: missing {   (current key: '>') in file appnews [offset: 571]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 577]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'http://steamcommunity-a.akamaihd.net/public/shared/css/shared_global.css?v=85A8XhHt87x5') in file appnews [offset: 670]

KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 683]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'type') in file appnews [offset: 689]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'text/css') in file appnews [offset: 701]

KeyValues Error: LoadFromBuffer: missing {   (current key: '<link') in file appnews [offset: 712]

KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 790]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'rel') in file appnews [offset: 795]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'stylesheet') in file appnews [offset: 812]

KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 823]

KeyValues Error: LoadFromBuffer: missing {   (current key: '>') in file appnews [offset: 831]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 837]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'http://steamcommunity-a.akamaihd.net/public/css/skin_1/global.css?v=jY0bK3Xg7RE7&amp;client=0') in file appnews [offset: 936]

KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 949]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'type') in file appnews [offset: 955]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'text/css') in file appnews [offset: 967]

KeyValues Error: LoadFromBuffer: missing {   (current key: '<link') in file appnews [offset: 978]

KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 1065]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'rel') in file appnews [offset: 1070]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'stylesheet') in file appnews [offset: 1087]

KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 1098]

KeyValues Error: LoadFromBuffer: missing {   (current key: '>') in file appnews [offset: 1106]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 1112]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'http://steamcommunity-a.akamaihd.net/public/css/skin_1/header.css?v=quvm2wU5yG0p') in file appnews [offset: 1198]

KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 1211]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'type') in file appnews [offset: 1217]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'text/css') in file appnews [offset: 1229]

KeyValues Error: LoadFromBuffer: missing {   (current key: '<script') in file appnews [offset: 1242]

KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 1260]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'src') in file appnews [offset: 1265]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'http://steamcommunity-a.akamaihd.net/public/javascript/prototype-1.7.js?v=.55t44gwuwgvw') in file appnews [offset: 1364]

KeyValues Error: LoadFromBuffer: missing {   (current key: '<script') in file appnews [offset: 1377]

KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 1395]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'src') in file appnews [offset: 1400]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'http://steamcommunity-a.akamaihd.net/public/javascript/scriptaculous/_combined.js?v=9XVsa_Ni33oN&amp;l=english&amp;load=effects,controls,slider,dragdrop') in file appnews [offset: 1564]

KeyValues Error: LoadFromBuffer: missing {   (current key: '<script') in file appnews [offset: 1577]

KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 1595]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'src') in file appnews [offset: 1600]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'http://steamcommunity-a.akamaihd.net/public/javascript/global.js?v=tlXhri_onc_Z&amp;l=english') in file appnews [offset: 1705]

KeyValues Error: LoadFromBuffer: missing {   (current key: '<script') in file appnews [offset: 1718]

KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 1736]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'src') in file appnews [offset: 1741]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'http://steamcommunity-a.akamaihd.net/public/javascript/jquery-1.11.1.min.js?v=.isFTSRckeNhC') in file appnews [offset: 1844]

KeyValues Error: LoadFromBuffer: missing {   (current key: '<script') in file appnews [offset: 1857]

KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 1875]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'src') in file appnews [offset: 1880]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'http://steamcommunity-a.akamaihd.net/public/shared/javascript/tooltip.js?v=.nCjeRtNcVhbG') in file appnews [offset: 1980]

KeyValues Error: LoadFromBuffer: missing {   (current key: '<script') in file appnews [offset: 1993]

KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 2011]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'src') in file appnews [offset: 2016]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'http://steamcommunity-a.akamaihd.net/public/shared/javascript/shared_global.js?v=BESEFoKTgss6&amp;l=english') in file appnews [offset: 2135]

KeyValues Error: LoadFromBuffer: missing {   (current key: '<script') in file appnews [offset: 2148]

KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 2166]

KeyValues Error: LoadFromBuffer: missing {   (current key: '>$J') in file appnews [offset: 2171]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'jQuery.noConflict();') in file appnews [offset: 2195]

KeyValues Error: LoadFromBuffer: missing {   (current key: '(') in file appnews [offset: 2204]

KeyValues Error: LoadFromBuffer: missing {   (current key: 'JSON') in file appnews [offset: 2211]

KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 2221]

KeyValues Error: LoadFromBuffer: missing {   (current key: '||') in file appnews [offset: 2240]

KeyValues Error: LoadFromBuffer: missing {   (current key: '||') in file appnews [offset: 2255]

KeyValues Error: RecursiveLoadFromBuffer:  got } in key in file appnews [offset: 2440]
), 
KeyValues Error: LoadFromBuffer: missing {   (current key: ';') in file appnews [offset: 2458]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'type') in file appnews [offset: 2464]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'text/javascript') in file appnews [offset: 2482]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'var') in file appnews [offset: 2493]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 2500]
(*)*), 
Bad expression token: ]KeyValues Error: LoadFromBuffer: missing {   (current key: '||') in file appnews [offset: 2535]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: ''UA-33779068-1']);') in file appnews [offset: 2585]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: ''0.4']);') in file appnews [offset: 2624]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '1,') in file appnews [offset: 2635]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'In',') in file appnews [offset: 2649]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '2]);') in file appnews [offset: 2684]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '2,') in file appnews [offset: 2695]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'Type',') in file appnews [offset: 2714]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '2]);') in file appnews [offset: 2749]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '3,') in file appnews [offset: 2762]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: ''news',') in file appnews [offset: 2775]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '_gaq.push(['_setCustomVar',') in file appnews [offset: 2808]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: ''Method',') in file appnews [offset: 2837]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: ',') in file appnews [offset: 2843]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '_gaq.push(['_trackPageview']);') in file appnews [offset: 2917]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '900000]);') in file appnews [offset: 2941]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '{') in file appnews [offset: 2951]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'ga') in file appnews [offset: 2956]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'document.createElement('script');') in file appnews [offset: 2998]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 3019]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'ga.async') in file appnews [offset: 3030]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'true;') in file appnews [offset: 3047]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 3059]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 3062]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'document.location.protocol') in file appnews [offset: 3091]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: ''https://ssl'') in file appnews [offset: 3107]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: ''http://www')') in file appnews [offset: 3123]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: ''.google-analytics.com/ga.js';') in file appnews [offset: 3162]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 's') in file appnews [offset: 3166]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'document.getElementsByTagName('script')[0];') in file appnews [offset: 3240]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 's);') in file appnews [offset: 3248]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: ')();') in file appnews [offset: 3262]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '</head>') in file appnews [offset: 3278]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<center>') in file appnews [offset: 3294]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'header') in file appnews [offset: 3306]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'contains') in file appnews [offset: 3320]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'browsing') in file appnews [offset: 3334]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'if') in file appnews [offset: 3344]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'in') in file appnews [offset: 3351]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<div') in file appnews [offset: 3363]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 3379]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>') in file appnews [offset: 3388]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'class') in file appnews [offset: 3395]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'content') in file appnews [offset: 3405]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<div') in file appnews [offset: 3422]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 3429]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>') in file appnews [offset: 3441]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'id') in file appnews [offset: 3445]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'logo_holder') in file appnews [offset: 3459]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<a') in file appnews [offset: 3473]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 3506]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>') in file appnews [offset: 3519]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'src') in file appnews [offset: 3524]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'http://steamcommunity-a.akamaihd.net/public/images/header/globalheader_logo.png') in file appnews [offset: 3611]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 3617]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'height') in file appnews [offset: 3625]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '44') in file appnews [offset: 3636]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 3640]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'alt') in file appnews [offset: 3645]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'Steam Logo') in file appnews [offset: 3660]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '</a>') in file appnews [offset: 3684]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<!--[if') in file appnews [offset: 3700]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'IE') in file appnews [offset: 3707]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<style') in file appnews [offset: 3724]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 3735]
(*)*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>') in file appnews [offset: 3754]
(*)*), 
Bad expression token: [KeyValues Error: LoadFromBuffer: missing {   (current key: '</style>') in file appnews [offset: 4083]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<div') in file appnews [offset: 4100]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 4135]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'id') in file appnews [offset: 4139]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'SuperNav') in file appnews [offset: 4150]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<a') in file appnews [offset: 4161]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 4181]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 4187]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'http://store.steampowered.com/') in file appnews [offset: 4240]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 4856]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>') in file appnews [offset: 4866]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '</a>') in file appnews [offset: 4880]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'class') in file appnews [offset: 4887]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'menuitem supernav') in file appnews [offset: 4912]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 4929]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 4935]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'http://steamcommunity.com/') in file appnews [offset: 4984]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 5640]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>') in file appnews [offset: 5656]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '</a>') in file appnews [offset: 5676]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'class') in file appnews [offset: 5683]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'MenuItem') in file appnews [offset: 5698]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 5737]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>') in file appnews [offset: 5747]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '</a>') in file appnews [offset: 5759]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'class') in file appnews [offset: 5766]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'MenuItem') in file appnews [offset: 5781]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 5816]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>') in file appnews [offset: 5828]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '</a>') in file appnews [offset: 5841]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<script') in file appnews [offset: 5855]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 5873]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>') in file appnews [offset: 5911]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '{') in file appnews [offset: 5944]
(*#logo_holder*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: ');') in file appnews [offset: 6146]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: ');') in file appnews [offset: 6159]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<div') in file appnews [offset: 6171]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 6188]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>') in file appnews [offset: 6203]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'id') in file appnews [offset: 6207]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'global_action_menu') in file appnews [offset: 6228]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<div') in file appnews [offset: 6247]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 6303]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>') in file appnews [offset: 6316]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'class') in file appnews [offset: 6323]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'header_installsteam_btn_leftcap') in file appnews [offset: 6363]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<div') in file appnews [offset: 6381]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 6416]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '></div>') in file appnews [offset: 6433]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'class') in file appnews [offset: 6440]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'header_installsteam_btn_content') in file appnews [offset: 6478]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 6517]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>') in file appnews [offset: 6534]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'Steam') in file appnews [offset: 6550]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '</div>') in file appnews [offset: 6592]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'class') in file appnews [offset: 6599]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'global_action_link') in file appnews [offset: 6624]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 6761]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>Login</a>') in file appnews [offset: 6793]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<span') in file appnews [offset: 6818]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 6848]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'id') in file appnews [offset: 6852]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'language_pulldown') in file appnews [offset: 6879]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 6929]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>language</span>') in file appnews [offset: 6957]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'class') in file appnews [offset: 6964]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'popup_block') in file appnews [offset: 6980]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 7000]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'style') in file appnews [offset: 7007]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'display: none;') in file appnews [offset: 7024]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<div') in file appnews [offset: 7043]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 7055]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '></div><div') in file appnews [offset: 7072]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 7085]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '></div><div') in file appnews [offset: 7102]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 7114]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '></div><div') in file appnews [offset: 7131]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 7145]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '></div><div') in file appnews [offset: 7162]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 7177]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '></div><div') in file appnews [offset: 7194]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 7206]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '></div><div') in file appnews [offset: 7223]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 7239]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '></div><div') in file appnews [offset: 7256]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 7268]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '></div>') in file appnews [offset: 7286]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'class') in file appnews [offset: 7293]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'popup_body popup_menu shadow_content') in file appnews [offset: 7332]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<a') in file appnews [offset: 7368]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 7392]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 7398]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '?l=bulgarian&appid=346010&count=3&maxlength=300&format=vdf') in file appnews [offset: 7466]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 7513]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>&#1041;&#1098;&#1083;&#1075;&#1072;&#1088;&#1089;&#1082;&#1080;') in file appnews [offset: 7548]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<a') in file appnews [offset: 7584]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 7608]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 7614]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '?l=czech&appid=346010&count=3&maxlength=300&format=vdf') in file appnews [offset: 7678]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 7721]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>&#269;e&#353;tina') in file appnews [offset: 7743]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<a') in file appnews [offset: 7779]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 7803]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 7809]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '?l=danish&appid=346010&count=3&maxlength=300&format=vdf') in file appnews [offset: 7874]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 7918]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>Dansk') in file appnews [offset: 7937]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<a') in file appnews [offset: 7973]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 7997]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 8003]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '?l=dutch&appid=346010&count=3&maxlength=300&format=vdf') in file appnews [offset: 8067]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 8110]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>Nederlands') in file appnews [offset: 8133]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<a') in file appnews [offset: 8178]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 8202]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 8208]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '?l=finnish&appid=346010&count=3&maxlength=300&format=vdf') in file appnews [offset: 8274]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 8319]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>Suomi') in file appnews [offset: 8339]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<a') in file appnews [offset: 8375]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 8399]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 8405]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '?l=french&appid=346010&count=3&maxlength=300&format=vdf') in file appnews [offset: 8470]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 8514]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>Français') in file appnews [offset: 8537]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<a') in file appnews [offset: 8573]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 8597]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 8603]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '?l=german&appid=346010&count=3&maxlength=300&format=vdf') in file appnews [offset: 8668]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 8712]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>Deutsch') in file appnews [offset: 8733]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<a') in file appnews [offset: 8769]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 8793]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 8799]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '?l=greek&appid=346010&count=3&maxlength=300&format=vdf') in file appnews [offset: 8863]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 8906]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>&#917;&#955;&#955;&#951;&#957;&#953;&#954;&#940;') in file appnews [offset: 8935]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<a') in file appnews [offset: 8971]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 8995]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 9001]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '?l=hungarian&appid=346010&count=3&maxlength=300&format=vdf') in file appnews [offset: 9069]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 9116]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>Magyar') in file appnews [offset: 9139]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<a') in file appnews [offset: 9175]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 9199]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 9205]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '?l=italian&appid=346010&count=3&maxlength=300&format=vdf') in file appnews [offset: 9271]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 9316]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>Italiano') in file appnews [offset: 9339]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<a') in file appnews [offset: 9375]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 9399]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 9405]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '?l=japanese&appid=346010&count=3&maxlength=300&format=vdf') in file appnews [offset: 9472]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 9518]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>&#26085;&#26412;&#35486;') in file appnews [offset: 9543]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<a') in file appnews [offset: 9579]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 9603]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 9609]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '?l=koreana&appid=346010&count=3&maxlength=300&format=vdf') in file appnews [offset: 9675]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 9720]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>&#54620;&#44397;&#50612;') in file appnews [offset: 9743]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<a') in file appnews [offset: 9779]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 9803]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 9809]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '?l=norwegian&appid=346010&count=3&maxlength=300&format=vdf') in file appnews [offset: 9877]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 9924]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>Norsk') in file appnews [offset: 9946]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<a') in file appnews [offset: 9982]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 10006]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 10012]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '?l=polish&appid=346010&count=3&maxlength=300&format=vdf') in file appnews [offset: 10077]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 10121]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>Polski') in file appnews [offset: 10141]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<a') in file appnews [offset: 10177]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 10201]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 10207]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '?l=portuguese&appid=346010&count=3&maxlength=300&format=vdf') in file appnews [offset: 10276]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 10324]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>Português') in file appnews [offset: 10352]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<a') in file appnews [offset: 10388]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 10412]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 10418]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '?l=brazilian&appid=346010&count=3&maxlength=300&format=vdf') in file appnews [offset: 10486]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 10533]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>Português-Brasil') in file appnews [offset: 10575]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<a') in file appnews [offset: 10611]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 10635]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 10641]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '?l=romanian&appid=346010&count=3&maxlength=300&format=vdf') in file appnews [offset: 10708]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 10754]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>Român&#259;') in file appnews [offset: 10778]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<a') in file appnews [offset: 10814]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 10838]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 10844]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '?l=russian&appid=346010&count=3&maxlength=300&format=vdf') in file appnews [offset: 10910]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 10955]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>&#1056;&#1091;&#1089;&#1089;&#1082;&#1080;&#1081;') in file appnews [offset: 10984]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<a') in file appnews [offset: 11020]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 11044]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 11050]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '?l=schinese&appid=346010&count=3&maxlength=300&format=vdf') in file appnews [offset: 11117]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 11163]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>&#31616;&#20307;&#20013;&#25991;') in file appnews [offset: 11188]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'Chinese)</a>') in file appnews [offset: 11231]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'class') in file appnews [offset: 11238]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'popup_menu_item tight') in file appnews [offset: 11266]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 11325]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'onclick') in file appnews [offset: 11334]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'ChangeLanguage( 'spanish' ); return false;') in file appnews [offset: 11387]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '(Spanish)</a>') in file appnews [offset: 11431]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'class') in file appnews [offset: 11438]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'popup_menu_item tight') in file appnews [offset: 11466]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 11525]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'onclick') in file appnews [offset: 11534]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'ChangeLanguage( 'swedish' ); return false;') in file appnews [offset: 11586]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '(Swedish)</a>') in file appnews [offset: 11630]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'class') in file appnews [offset: 11637]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'popup_menu_item tight') in file appnews [offset: 11665]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 11725]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'onclick') in file appnews [offset: 11734]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'ChangeLanguage( 'tchinese' ); return false;') in file appnews [offset: 11792]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '(Traditional') in file appnews [offset: 11818]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<a') in file appnews [offset: 11854]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 11878]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 11884]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '?l=thai&appid=346010&count=3&maxlength=300&format=vdf') in file appnews [offset: 11947]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 11989]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>&#3652;&#3607;&#3618;') in file appnews [offset: 12010]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<a') in file appnews [offset: 12046]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 12070]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 12076]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '?l=turkish&appid=346010&count=3&maxlength=300&format=vdf') in file appnews [offset: 12142]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 12187]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>Türkçe') in file appnews [offset: 12210]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<a') in file appnews [offset: 12246]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 12270]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 12276]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '?l=ukrainian&appid=346010&count=3&maxlength=300&format=vdf') in file appnews [offset: 12344]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 12391]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>&#1059;&#1082;&#1088;&#1072;&#1111;&#1085;&#1089;&#1100;&#1082;&#1072;') in file appnews [offset: 12428]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<a') in file appnews [offset: 12454]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 12478]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 12484]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'http://translation.steampowered.com') in file appnews [offset: 12528]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 12537]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>Help') in file appnews [offset: 12545]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'translate') in file appnews [offset: 12565]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '</div>') in file appnews [offset: 12594]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '</div>') in file appnews [offset: 12622]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '</div>') in file appnews [offset: 12658]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<div') in file appnews [offset: 12671]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 12681]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'style') in file appnews [offset: 12688]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'display: none') in file appnews [offset: 12717]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'type') in file appnews [offset: 12723]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'text/javascript') in file appnews [offset: 12741]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'g_sessionID') in file appnews [offset: 12757]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '') in file appnews [offset: 12761]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'g_steamID') in file appnews [offset: 12775]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'false;') in file appnews [offset: 12788]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'InitMiniprofileHovers') in file appnews [offset: 12813]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '$J(') in file appnews [offset: 12838]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: ');') in file appnews [offset: 12849]
(*$('.supernav').v_tooltip(*), 
KeyValues Error: RecursiveLoadFromBuffer:  got } in key in file appnews [offset: 13011]
function(), 
KeyValues Error: LoadFromBuffer: missing {   (current key: ');') in file appnews [offset: 13016]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: ';') in file appnews [offset: 13042]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '$J('[data-community-tooltip]')') in file appnews [offset: 13076]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '}') in file appnews [offset: 13081]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '$J(') in file appnews [offset: 13100]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '{') in file appnews [offset: 13121]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'http:') in file appnews [offset: 13212]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'http:') in file appnews [offset: 13318]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'http:') in file appnews [offset: 13419]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '}') in file appnews [offset: 13435]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '/header') in file appnews [offset: 13447]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '-->') in file appnews [offset: 13461]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'primary') in file appnews [offset: 13478]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'gray') in file appnews [offset: 13494]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'content') in file appnews [offset: 13512]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '-->') in file appnews [offset: 13524]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'content') in file appnews [offset: 13545]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'with') in file appnews [offset: 13558]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'header') in file appnews [offset: 13573]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '-->') in file appnews [offset: 13584]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'class') in file appnews [offset: 13591]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'error_ctn') in file appnews [offset: 13603]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<div') in file appnews [offset: 13614]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 13623]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>') in file appnews [offset: 13633]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'id') in file appnews [offset: 13637]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'mainContents') in file appnews [offset: 13652]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<h2>Error</h2>') in file appnews [offset: 13683]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '</div>') in file appnews [offset: 13701]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'id') in file appnews [offset: 13705]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'BG_bottom') in file appnews [offset: 13717]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<div') in file appnews [offset: 13729]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 13739]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>') in file appnews [offset: 13761]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<p') in file appnews [offset: 13775]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 13789]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>') in file appnews [offset: 13799]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'error') in file appnews [offset: 13809]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'encountered') in file appnews [offset: 13827]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'processing') in file appnews [offset: 13843]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'request:<br><br>') in file appnews [offset: 13870]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<h3>There') in file appnews [offset: 13889]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'an') in file appnews [offset: 13898]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'communicating') in file appnews [offset: 13917]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'the') in file appnews [offset: 13930]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'Please') in file appnews [offset: 13941]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'again') in file appnews [offset: 13967]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<p') in file appnews [offset: 13981]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 13994]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>Here's') in file appnews [offset: 14003]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'link') in file appnews [offset: 14011]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'the') in file appnews [offset: 14021]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'community') in file appnews [offset: 14034]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'class') in file appnews [offset: 14041]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'linkStandard') in file appnews [offset: 14060]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 14088]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>home') in file appnews [offset: 14107]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '</div>') in file appnews [offset: 14126]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'clear') in file appnews [offset: 14133]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'all') in file appnews [offset: 14141]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '</div>') in file appnews [offset: 14160]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<!--') in file appnews [offset: 14174]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '-->') in file appnews [offset: 14186]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'id') in file appnews [offset: 14190]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'footer_spacer') in file appnews [offset: 14212]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<div') in file appnews [offset: 14222]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 14231]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>') in file appnews [offset: 14240]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'class') in file appnews [offset: 14247]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'footer_content') in file appnews [offset: 14264]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<span') in file appnews [offset: 14277]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 14290]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '><img') in file appnews [offset: 14299]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 14384]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'width') in file appnews [offset: 14391]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '96') in file appnews [offset: 14402]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 14407]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'border') in file appnews [offset: 14415]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '0') in file appnews [offset: 14422]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 14435]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '/></span>') in file appnews [offset: 14455]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'id') in file appnews [offset: 14459]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'footerText') in file appnews [offset: 14472]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '&copy;') in file appnews [offset: 14490]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'Corporation.') in file appnews [offset: 14507]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'rights') in file appnews [offset: 14524]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'all') in file appnews [offset: 14539]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'are') in file appnews [offset: 14552]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'of') in file appnews [offset: 14561]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'respective') in file appnews [offset: 14579]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'in') in file appnews [offset: 14586]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'US') in file appnews [offset: 14593]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'other') in file appnews [offset: 14619]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'geospatial') in file appnews [offset: 14635]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'on') in file appnews [offset: 14643]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'website') in file appnews [offset: 14654]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'provided') in file appnews [offset: 14666]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<a') in file appnews [offset: 14676]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 14685]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 14691]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'https://steamcommunity.com/linkfilter/?url=http://www.geonames.org') in file appnews [offset: 14777]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<br>') in file appnews [offset: 14801]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'class') in file appnews [offset: 14808]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'valve_links') in file appnews [offset: 14822]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '<a') in file appnews [offset: 14837]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 14888]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'target') in file appnews [offset: 14896]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '_blank') in file appnews [offset: 14912]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'Policy</a>') in file appnews [offset: 14937]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '|') in file appnews [offset: 14948]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'href') in file appnews [offset: 14954]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'http://www.valvesoftware.com/legal.htm') in file appnews [offset: 15001]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 15010]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '>Legal</a>') in file appnews [offset: 15035]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '&nbsp;<a') in file appnews [offset: 15049]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '=') in file appnews [offset: 15103]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'target') in file appnews [offset: 15111]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '_blank') in file appnews [offset: 15125]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: 'Subscriber') in file appnews [offset: 15150]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '</span>') in file appnews [offset: 15193]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '</div>') in file appnews [offset: 15212]
(*function()*), 
KeyValues Error: LoadFromBuffer: missing {   (current key: '</center>') in file appnews [offset: 15226]
(*function()*), 
/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/tier1/../tier1/KeyValues.cpp (2562) : Assertion Failed: Error while parsing text KeyValues for resource appnews
Assert( Assertion Failed: Error while parsing text KeyValues for resource appnews ):/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/tier1/../tier1/KeyValues.cpp:2562

Installing breakpad exception handler for appid(steam)/version(1428965940)
CAPIJobRequestUserStats - Server response failed 2
Generating new string page texture 87: 128x256, total string texture memory is 1.75 MB
assert_20150425172722_19.dmp[5973]: Uploading dump (out-of-process)
/tmp/dumps/assert_20150425172722_19.dmp
Installing breakpad exception handler for appid(steam)/version(1428965940)
Running Steam on ubuntu 15.04 64-bit
STEAM_RUNTIME has been set by the user to: /home/USERNAME/.local/share/Steam/ubuntu12_32/steam-runtime
ExecCommandLine: "/home/USERNAME/.steam/root/ubuntu12_32/steam steam://open/driverhelperready"
ExecSteamURL: "steam://open/driverhelperready"
Game update: AppID 346010 "Besiege", ProcID 6083, IP 0.0.0.0:0
ERROR: ld.so: object '/home/USERNAME/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/USERNAME/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
Found path: /home/USERNAME/.local/share/Steam/steamapps/common/Besiege/Besiege.x86_64
Mono path[0] = '/home/USERNAME/.local/share/Steam/steamapps/common/Besiege/Besiege_Data/Managed'
Mono path[1] = '/home/USERNAME/.local/share/Steam/steamapps/common/Besiege/Besiege_Data/Mono'
Mono config path = '/home/USERNAME/.local/share/Steam/steamapps/common/Besiege/Besiege_Data/Mono/etc'
/dev/input/js0: driver version: 2.1.0 (20100)
: Too many axes; using axes 0 - 19 and ignoring axes 20 - 36
: Too many buttons; using buttons 0 - 19 and ignoring buttons 20 - 74
/dev/input/js0: fd 8, buttons 20, axes 20, name Microsoft Microsoft® 2.4GHz Transceiver v8.0
/dev/input/js0: axis  0: raw -32767, mapped 0.000000
/dev/input/js0: axis  1: raw -32767, mapped 0.000000
/dev/input/js0: axis  2: raw -32767, mapped 0.000000
/dev/input/js0: axis  3: raw -32767, mapped 0.000000
/dev/input/js0: axis  4: raw -32767, mapped 0.000000
/dev/input/js0: axis  5: raw -32767, mapped 0.000000
/dev/input/js0: axis  6: raw -32767, mapped 0.000000
/dev/input/js0: axis  7: raw -32767, mapped 0.000000
/dev/input/js0: axis  8: raw -32767, mapped 0.000000
/dev/input/js0: axis  9: raw -32767, mapped 0.000000
/dev/input/js0: axis 10: raw      0, mapped 0.000000
/dev/input/js0: axis 11: raw      0, mapped 0.000000
/dev/input/js0: axis 12: raw -32767, mapped 0.000000
/dev/input/js0: axis 13: raw -32767, mapped 0.000000
/dev/input/js0: axis 14: raw -32767, mapped 0.000000
/dev/input/js0: axis 15: raw -32767, mapped 0.000000
/dev/input/js0: axis 16: raw -32767, mapped 0.000000
/dev/input/js0: axis 17: raw -32767, mapped 0.000000
/dev/input/js0: axis 18: raw -32767, mapped 0.000000
/dev/input/js0: axis 19: raw -32767, mapped 0.000000
/dev/input/js0: axis 20: raw -32767, mapped 0.000000
Aborted (core dumped)
Game removed: AppID 346010 "Besiege", ProcID 6083 
```

Any help is good help
Thanks

---

### Post by sgian on 2015-04-25
If any help is good help...go back to 14.10 for now is my suggestion.  But before you revert to 14, when you check for proprietary drivers in 15.04, make sure there is a driver for the cpu with 15.04, which wasn't necessary before.

I have an AMD A4-6300 and am not impressed with driver support for AMD compared to Intel.  My Intel Pentium G3258 works great on 15.04, on the other hand.  The AMD I have needed to have the proprietary driver for the CPU enabled before it would work better.  My AMD doesn't have a graphics card though, and I suspect that your issue is with the graphics card support.  You could try removing the card and seeing if that makes 15.04 more stable for you, my son is playing minecraft on that computer right now or I would verify that steam works too without the card.

For minecraft, I've noticed that Oracle Java 8 seems more stable on my computers than openJDK, even for pre-1.8 minecraft.  You could try that before reverting.

---

### Post by cgameing on 2015-04-25
I can try installing java 8
And is there a way to downgrade ubuntu (without reinstalling the os after backing up all my data)
I have a spare motherboard with a decent cpu i could try swaping out, but i dont know if that will make a difference.

As for the cpu drivers, I have another part that says unknown, but the driver name is amd 64 cpus or something,
I can choose to not use this device but i dont think clicking that button would be wise

---

### Post by cgameing on 2015-04-25
Just saying, there needs to be 2 spoilers for the 2 logs

---

### Post by cgameing on 2015-04-25
Simple fix, for some reason installing the drivers from the official amd website dident work

This seemed to work for me
sudo apt-get install linux-headers-generic
sudo apt-get install fglrx-updates xvba-va-driver libva-glx1 libva-egl1 vainfo

Generate a fresh xorg.conf BEFORE REBOOTING! 
sudo amdconfig --initial If you are using multiple AMD graphics cards or AMD dual graphics (i.e.: notebook users), use: 

sudo amdconfig --adapter=all --initial

reboot 
and to check if it worked
fglrxinfo


source
[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

thx cya

---

