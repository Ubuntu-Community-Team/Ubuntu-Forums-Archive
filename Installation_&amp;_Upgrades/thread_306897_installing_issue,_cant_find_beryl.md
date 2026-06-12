---
title: "installing issue, cant find beryl"
date: 2006-11-25
forum: Installation &amp; Upgrades
---

### Post by baalthazar on 2006-11-25
hello ppl..
ive been sufering trying to install beryl following this tutorial [http://cmaverick.wordpress.com/2006/10/25/beryl-en-ubuntu-edgy-con-ati/](http://cmaverick.wordpress.com/2006/10/25/beryl-en-ubuntu-edgy-con-ati/)
and wen i get to the last step AKA **sudo apt-get install beryl emerald emerald-themes**

it says that it cant find the beryl package ](*,) :-? 

can some1 help me fix this?

the last tut i tried was this one [https://help.ubuntu.com/community/BerylOnEdgy](https://help.ubuntu.com/community/BerylOnEdgy) and still having the same problem (even if i alternate the URLS at the source.list)

---

### Post by highneko on 2006-11-25
What graphics card are you using? If you're using nvidia use this: [http://wiki.beryl-project.org/wiki/Install/Ubuntu](http://wiki.beryl-project.org/wiki/Install/Ubuntu) I don't remember how to setup an intel beryl installation, so someone else would have to help you with intel or ati. It's saying package not found, what package do you want? Do you want the latest beryl updated everyday, or maybe Beryl 0.1.2?

---

### Post by baalthazar on 2006-11-25
cool... well.. i am using an ATI, and everything is going well until i tell him to >sudo apt-get install beryl emerald emerald-themes< and then he tell me he cant find the packages. i just want a sweet version to impress my girlfriend and see if i can install it in her pc, the only thing she doesnt have is a graphic card, so i doubt it will work well.. but anyways..

---

### Post by Rontie on 2006-11-26
I installed this package a couple of days ago and went smooth, but now, i can't seem to find a rep that has Beryl on it, i got the XGL running.. just need the windows manager then i'll be good

---

### Post by baalthazar on 2006-11-26
i think there is a repository issue going on.. because following this tutorial [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)
and wen i get to close the add source and tell it to reload, it shows me this error :
**[http://ubuntu.beryl-project.org/dists/edgy/Release:](http://ubuntu.beryl-project.org/dists/edgy/Release:) Unable to find expected entry  main-edgy/binary-i386/Packages in Meta-index file (malformed Release file?)**

is it that the server has crashed or changed of direction?

---

### Post by bulldog on 2006-11-26
Try one of these,

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) edgy main-edgy
deb [http://compiz-mirror.lupine.me.uk/](http://compiz-mirror.lupine.me.uk/) edgy main-edgy
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) edgy main-edgy
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main-edgy

---

### Post by baalthazar on 2006-11-26
:-? its showing me this... still cant find the beryl 

Obj [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                             
Obj [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                 
Ign [http://www.beerorkid.com](http://www.beerorkid.com) edgy/main-edgy Packages                           
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages                   
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages                 
Des:19 [http://ubuntu.compiz.net](http://ubuntu.compiz.net) edgy/main-edgy Packages [3265B]                
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages                      
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
Des:20 [http://www.beerorkid.com](http://www.beerorkid.com) edgy/main-edgy Packages [3265B]
Descargados 39,2kB en 3s (11,8kB/s)
Imposible obtener [http://compiz-mirror.lupine.me.uk/dists/edgy/Release](http://compiz-mirror.lupine.me.uk/dists/edgy/Release)  Unable to find expected entry  main-edgy/binary-i386/Packages in Meta-index file (malformed Release file?)
Imposible obtener [http://ubuntu.beryl-project.org/dists/edgy/Release](http://ubuntu.beryl-project.org/dists/edgy/Release)  Unable to find expected entry  main-edgy/binary-i386/Packages in Meta-index file (malformed Release file?)
Leyendo lista de paquetes... Hecho
E: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.
$ sudo apt-get install beryl emeral emerald-themes
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo información de estado... Hecho
E: No se pudo encontrar el paquete emeral

---

### Post by baalthazar on 2006-11-27
well.. . im going to try and install beryl but with dapper drake, but i doubt there will be much of a diference since the problem seems to be the server not having the files..

any suggestions?

---

### Post by depu on 2006-11-27
it looks more like a server issue but i would like to refer you to the beryl guides at [http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)
just to check up, try removing all the compiz repos that you had added and do a apt-get update
then put only 1 of the compiz repos.
for example add only 
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) edgy main-edgy
and then get the key by running 
wget [http://ubuntu.compiz.net/quinn.key.asc](http://ubuntu.compiz.net/quinn.key.asc) -O - | sudo apt-key add -
in the terminal
run sudo apt-get update

---

### Post by baalthazar on 2006-11-27
thanks for the link dude... but now i think i have a somewhat bigger problem
..
i used this tutorial and it worked great [http://crysol.inf-cr.uclm.es/node/399](http://crysol.inf-cr.uclm.es/node/399)
the problem is that i didnt realize it was for an nvidia card since i have an ati card, and the link there for the ati tutorial is dead.
so, is there a way to fix this or i have to look for another tutorial?

---

### Post by baalthazar on 2006-11-28
argh.. this is driving me insane!
still cant install the damn thing, is there a way to delete every some of the files created?

when u download a file, like all the stuff that was downloaded to install beryl, were does it go? is there a way to delete it in a graphical way? or i can only delete from the console with sudo? and if so, wich is the command? is it del? 

i think i will just install v.6.10 and try then to install it, becasue from what ive got right now (beryl almost functioning) its not working cuz it cant find and Nvidia card, and of course, i have ATI but dont know how to fix that... can some1 help me plz??:confused:

---

### Post by deep.tinker77 on 2006-11-28
> **baalthazar said:**
> argh.. this is driving me insane!
still cant install the damn thing, is there a way to delete every some of the files created?

when u download a file, like all the stuff that was downloaded to install beryl, were does it go? is there a way to delete it in a graphical way? or i can only delete from the console with sudo? and if so, wich is the command? is it del? 

i think i will just install v.6.10 and try then to install it, becasue from what ive got right now (beryl almost functioning) its not working cuz it cant find and Nvidia card, and of course, i have ATI but dont know how to fix that... can some1 help me plz??:confused:


Try this out. It's a link from Artificial Intelligence's blog. I followed the directions on there and they worked like a charm. When in doubt, leech off of a mod :mrgreen: 

[http://polarbeardk.blogspot.com/2006/11/gnome-eyecandy.html](http://polarbeardk.blogspot.com/2006/11/gnome-eyecandy.html)

---

### Post by baalthazar on 2006-11-30
well.. .after suposedly installing beryl,  i am getting this error and ofcourse, its not functioning

 [fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS
[fglrx] API ERROR: could not register entrypoint for ClientActiveVertexStreamATI[fglrx] API ERROR: could not register entrypoint for VertexBlendEnviATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnvfATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2dvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3dvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4dvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3bATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3bvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3sATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3svATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3iATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3ivATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3fATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3fvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3dATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3dvATI
[fglrx] API ERROR: could not register entrypoint for DrawRangeElementsEXT
[fglrx] API ERROR: could not register entrypoint for WeightbvARB
[fglrx] API ERROR: could not register entrypoint for WeightsvARB
[fglrx] API ERROR: could not register entrypoint for WeightivARB
[fglrx] API ERROR: could not register entrypoint for WeightfvARB
[fglrx] API ERROR: could not register entrypoint for WeightdvARB
[fglrx] API ERROR: could not register entrypoint for WeightubvARB
[fglrx] API ERROR: could not register entrypoint for WeightusvARB
[fglrx] API ERROR: could not register entrypoint for WeightuivARB
[fglrx] API ERROR: could not register entrypoint for WeightPointerARB
[fglrx] API ERROR: could not register entrypoint for VertexBlendARB
[fglrx] API ERROR: could not register entrypoint for MultiDrawArraysEXT
[fglrx] API ERROR: could not register entrypoint for MultiDrawElementsEXT
[fglrx] API ERROR: could not register entrypoint for DrawBuffersATI
[fglrx] API ERROR: could not register entrypoint for DrawElementsFGL
[fglrx] API ERROR: could not register entrypoint for DrawWireTrianglesFGL
[fglrx] API ERROR: could not register entrypoint for PNTrianglesiATI
[fglrx] API ERROR: could not register entrypoint for PNTrianglesfATI
[fglrx] API ERROR: could not register entrypoint for TexBumpParameterivATI
[fglrx] API ERROR: could not register entrypoint for TexBumpParameterfvATI
[fglrx] API ERROR: could not register entrypoint for GetTexBumpParameterivATI
[fglrx] API ERROR: could not register entrypoint for GetTexBumpParameterfvATI
[fglrx] API ERROR: could not register entrypoint for BeginVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for EndVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for BindVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for GenVertexShadersEXT
[fglrx] API ERROR: could not register entrypoint for DeleteVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for ShaderOp1EXT
[fglrx] API ERROR: could not register entrypoint for ShaderOp2EXT
[fglrx] API ERROR: could not register entrypoint for ShaderOp3EXT
[fglrx] API ERROR: could not register entrypoint for SwizzleEXT
[fglrx] API ERROR: could not register entrypoint for WriteMaskEXT
[fglrx] API ERROR: could not register entrypoint for InsertComponentEXT
[fglrx] API ERROR: could not register entrypoint for ExtractComponentEXT
[fglrx] API ERROR: could not register entrypoint for GenSymbolsEXT
[fglrx] API ERROR: could not register entrypoint for SetInvariantEXT
[fglrx] API ERROR: could not register entrypoint for SetLocalConstantEXT
[fglrx] API ERROR: could not register entrypoint for VariantbvEXT
[fglrx] API ERROR: could not register entrypoint for VariantsvEXT
[fglrx] API ERROR: could not register entrypoint for VariantivEXT
[fglrx] API ERROR: could not register entrypoint for VariantfvEXT
[fglrx] API ERROR: could not register entrypoint for VariantdvEXT
[fglrx] API ERROR: could not register entrypoint for VariantubvEXT
[fglrx] API ERROR: could not register entrypoint for VariantusvEXT
[fglrx] API ERROR: could not register entrypoint for VariantuivEXT
[fglrx] API ERROR: could not register entrypoint for VariantPointerEXT
[fglrx] API ERROR: could not register entrypoint for EnableVariantClientStateEXT[fglrx] API ERROR: could not register entrypoint for DisableVariantClientStateEXT
[fglrx] API ERROR: could not register entrypoint for BindLightParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindMaterialParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindTexGenParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindTextureUnitParameterEXT[fglrx] API ERROR: could not register entrypoint for BindParameterEXT
[fglrx] API ERROR: could not register entrypoint for IsVariantEnabledEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantBooleanvEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantIntegervEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantPointervEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantBooleanvEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantIntegervEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for GetLocalConstantBooleanvEXT[fglrx] API ERROR: could not register entrypoint for GetLocalConstantIntegervEXT[fglrx] API ERROR: could not register entrypoint for GetLocalConstantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for WindowPos2dARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2fARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2iARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2sARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2ivARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2svARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2fvARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2dvARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3iARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3sARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3fARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3dARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3ivARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3svARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3fvARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3dvARB
[fglrx] API ERROR: could not register entrypoint for BindBufferARB
[fglrx] API ERROR: could not register entrypoint for DeleteBuffersARB
[fglrx] API ERROR: could not register entrypoint for GenBuffersARB
[fglrx] API ERROR: could not register entrypoint for IsBufferARB
[fglrx] API ERROR: could not register entrypoint for BufferDataARB
[fglrx] API ERROR: could not register entrypoint for BufferSubDataARB
[fglrx] API ERROR: could not register entrypoint for GetBufferSubDataARB
[fglrx] API ERROR: could not register entrypoint for MapBufferARB
[fglrx] API ERROR: could not register entrypoint for UnmapBufferARB
[fglrx] API ERROR: could not register entrypoint for GetBufferParameterivARB
[fglrx] API ERROR: could not register entrypoint for GetBufferPointervARB
[fglrx] API ERROR: could not register entrypoint for NewObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for IsObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for UpdateObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for GetObjectBufferfvATI
[fglrx] API ERROR: could not register entrypoint for GetObjectBufferivATI
[fglrx] API ERROR: could not register entrypoint for FreeObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for DeleteObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for ArrayObjectATI
[fglrx] API ERROR: could not register entrypoint for GetArrayObjectfvATI
[fglrx] API ERROR: could not register entrypoint for GetArrayObjectivATI
[fglrx] API ERROR: could not register entrypoint for VariantArrayObjectATI
[fglrx] API ERROR: could not register entrypoint for GetVariantArrayObjectfvATI
[fglrx] API ERROR: could not register entrypoint for GetVariantArrayObjectivATI
[fglrx] API ERROR: could not register entrypoint for ElementPointerATI
[fglrx] API ERROR: could not register entrypoint for DrawElementArrayATI
[fglrx] API ERROR: could not register entrypoint for DrawRangeElementArrayATI
[fglrx] API ERROR: could not register entrypoint for MapObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for UnmapObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for VertexAttribArrayObjectATI
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribArrayObjectfvATI
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribArrayObjectivATI
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NubARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4bvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4ivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4ubvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4usvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4uivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NbvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NsvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NubvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NusvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NuivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttribPointerARB
[fglrx] API ERROR: could not register entrypoint for EnableVertexAttribArrayARB
[fglrx] API ERROR: could not register entrypoint for DisableVertexAttribArrayARB[fglrx] API ERROR: could not register entrypoint for ProgramStringARB
[fglrx] API ERROR: could not register entrypoint for BindProgramARB
[fglrx] API ERROR: could not register entrypoint for DeleteProgramsARB
[fglrx] API ERROR: could not register entrypoint for GenProgramsARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4fARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4dARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4fvARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4dvARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4fARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4dARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4fvARB[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4dvARB[fglrx] API ERROR: could not register entrypoint for GetProgramEnvParameterfvARB[fglrx] API ERROR: could not register entrypoint for GetProgramEnvParameterdvARB[fglrx] API ERROR: could not register entrypoint for GetProgramLocalParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GetProgramLocalParameterdvARB
[fglrx] API ERROR: could not register entrypoint for GetProgramivARB
[fglrx] API ERROR: could not register entrypoint for GetProgramStringARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribdvARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribfvARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribivARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribPointervARB
[fglrx] API ERROR: could not register entrypoint for IsProgramARB
[fglrx] API ERROR: could not register entrypoint for GenFragmentShadersATI
[fglrx] API ERROR: could not register entrypoint for BindFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for DeleteFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for BeginFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for EndFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for PassTexCoordATI
[fglrx] API ERROR: could not register entrypoint for SampleMapATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp1ATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp2ATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp3ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp1ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp2ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp3ATI
[fglrx] API ERROR: could not register entrypoint for SetFragmentShaderConstantATI
[fglrx] API ERROR: could not register entrypoint for CurrentPaletteMatrixARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexubvARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexusvARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexuivARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexPointerARB
[fglrx] API ERROR: could not register entrypoint for StencilOpSeparateATI
[fglrx] API ERROR: could not register entrypoint for StencilFuncSeparateATI
[fglrx] API ERROR: could not register entrypoint for PointParameteriEXT
[fglrx] API ERROR: could not register entrypoint for PointParameterivEXT
[fglrx] API ERROR: could not register entrypoint for GenOcclusionQueriesNV
[fglrx] API ERROR: could not register entrypoint for DeleteOcclusionQueriesNV
[fglrx] API ERROR: could not register entrypoint for IsOcclusionQueryNV
[fglrx] API ERROR: could not register entrypoint for BeginOcclusionQueryNV
[fglrx] API ERROR: could not register entrypoint for EndOcclusionQueryNV
[fglrx] API ERROR: could not register entrypoint for GetOcclusionQueryivNV
[fglrx] API ERROR: could not register entrypoint for GetOcclusionQueryuivNV
[fglrx] API ERROR: could not register entrypoint for MapTexture3DATI
[fglrx] API ERROR: could not register entrypoint for UnmapTexture3DATI
[fglrx] API ERROR: could not register entrypoint for PointParameterfARB
[fglrx] API ERROR: could not register entrypoint for PointParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GenVisibilityQueriesATI
[fglrx] API ERROR: could not register entrypoint for DeleteVisibilityQueriesATI
[fglrx] API ERROR: could not register entrypoint for BeginDefineVisibilityQueryATI
[fglrx] API ERROR: could not register entrypoint for EndDefineVisibilityQueryATI[fglrx] API ERROR: could not register entrypoint for BeginUseVisibilityQueryATI
[fglrx] API ERROR: could not register entrypoint for EndUseVisibilityQueryATI
[fglrx] API ERROR: could not register entrypoint for GenQueriesARB
[fglrx] API ERROR: could not register entrypoint for DeleteQueriesARB
[fglrx] API ERROR: could not register entrypoint for IsQueryARB
[fglrx] API ERROR: could not register entrypoint for BeginQueryARB
[fglrx] API ERROR: could not register entrypoint for EndQueryARB
[fglrx] API ERROR: could not register entrypoint for GetQueryivARB
[fglrx] API ERROR: could not register entrypoint for GetQueryObjectivARB
[fglrx] API ERROR: could not register entrypoint for GetQueryObjectuivARB
[fglrx] API ERROR: could not register entrypoint for DeleteObjectARB
[fglrx] API ERROR: could not register entrypoint for GetHandleARB
[fglrx] API ERROR: could not register entrypoint for DetachObjectARB
[fglrx] API ERROR: could not register entrypoint for CreateShaderObjectARB
[fglrx] API ERROR: could not register entrypoint for ShaderSourceARB
[fglrx] API ERROR: could not register entrypoint for CompileShaderARB
[fglrx] API ERROR: could not register entrypoint for CreateProgramObjectARB
[fglrx] API ERROR: could not register entrypoint for AttachObjectARB
[fglrx] API ERROR: could not register entrypoint for LinkProgramARB
[fglrx] API ERROR: could not register entrypoint for UseProgramObjectARB
[fglrx] API ERROR: could not register entrypoint for ValidateProgramARB
[fglrx] API ERROR: could not register entrypoint for Uniform1fARB
[fglrx] API ERROR: could not register entrypoint for Uniform2fARB
[fglrx] API ERROR: could not register entrypoint for Uniform3fARB
[fglrx] API ERROR: could not register entrypoint for Uniform4fARB
[fglrx] API ERROR: could not register entrypoint for Uniform1iARB
[fglrx] API ERROR: could not register entrypoint for Uniform2iARB
[fglrx] API ERROR: could not register entrypoint for Uniform3iARB
[fglrx] API ERROR: could not register entrypoint for Uniform4iARB
[fglrx] API ERROR: could not register entrypoint for Uniform1fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform2fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform3fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform4fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform1ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform2ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform3ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform4ivARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix2fvARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix3fvARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix4fvARB
[fglrx] API ERROR: could not register entrypoint for GetObjectParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GetObjectParameterivARB
[fglrx] API ERROR: could not register entrypoint for GetInfoLogARB
[fglrx] API ERROR: could not register entrypoint for GetAttachedObjectsARB
[fglrx] API ERROR: could not register entrypoint for GetUniformLocationARB
[fglrx] API ERROR: could not register entrypoint for GetActiveUniformARB
[fglrx] API ERROR: could not register entrypoint for GetUniformfvARB
[fglrx] API ERROR: could not register entrypoint for GetUniformivARB
[fglrx] API ERROR: could not register entrypoint for GetShaderSourceARB
[fglrx] API ERROR: could not register entrypoint for BindAttribLocationARB
[fglrx] API ERROR: could not register entrypoint for GetActiveAttribARB
[fglrx] API ERROR: could not register entrypoint for GetAttribLocationARB
[fglrx] API ERROR: could not register entrypoint for IsRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for BindRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for DeleteRenderbuffersEXT
[fglrx] API ERROR: could not register entrypoint for GenRenderbuffersEXT
[fglrx] API ERROR: could not register entrypoint for RenderbufferStorageEXT
[fglrx] API ERROR: could not register entrypoint for GetRenderbufferParameterivEXT
[fglrx] API ERROR: could not register entrypoint for IsFramebufferEXT
[fglrx] API ERROR: could not register entrypoint for BindFramebufferEXT
[fglrx] API ERROR: could not register entrypoint for DeleteFramebuffersEXT
[fglrx] API ERROR: could not register entrypoint for GenFramebuffersEXT
[fglrx] API ERROR: could not register entrypoint for CheckFramebufferStatusEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture1DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture2DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture3DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for GetFramebufferAttachmentParameterivEXT
[fglrx] API ERROR: could not register entrypoint for GenerateMipmapEXT
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension


can some1 help me fix it? id really like to tryy the Beryl power

---

