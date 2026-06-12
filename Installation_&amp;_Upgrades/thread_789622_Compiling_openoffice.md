---
title: "Compiling openoffice?"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by macaholic on 2008-05-10
I have been attempting to compile the openoffice 3.0 beta recently since there are no 64-bit packages. I've got the configuring and dependency issues solved. Now I'm stuck, I have no idea how to compile this java behemoth. After I was done configuring it gave me this:  ```
*
* OpenOffice.org 300 configuration. 
* 
* 
* Configuration part of OpenOffice.org 300 build is finished. 
* 
* NB! Be aware that you might not be able to build OpenOffice.org if you 
* ignore any warning message that were generated during this configuration 
* process. 
* 
*
* USAGE: 
* Source LinuxX86-64Env.Set (in tcsh) or LinuxX86-64Env.Set.sh (in sh)
* in order to set up the build-environment variables.
* 
* 
**************************************************************************** 
Configure completed
You may now run ./bootstrap in /home/matt/Desktop/BEA300_m2
 

```
Running either of those files seems to do nothing at all, and there are no options in them that I can see. Does anyone know what step comes next? I'm totally lost, and the OOo folder structure isn't helping one bit, it's really confusing to figure out. Any help would be greatly appreciated.

---

### Post by tamoneya on 2008-05-10
that is not two seperate files you need to run the command while in the correct directory.  Try this:```
cd /home/matt/Desktop/BEA300_m2
./bootstrap
```

---

### Post by macaholic on 2008-05-10
Sorry, I've been gone for a few hours, I meant to say in my post that I had already ran all of the files, and running bootstrap does nothing, there is no output of any kind.

---

### Post by macaholic on 2008-05-11
So no one has any ideas? I can't find anything searching google over the past 2 days. I really want to try the new beta, but I just can't figure out how to compile it :( .
EDIT: Well I found the openoffice wiki page about it, [http://wiki.services.openoffice.org/wiki/Ubuntu_Build_Instructions](http://wiki.services.openoffice.org/wiki/Ubuntu_Build_Instructions), trying those now.

---

### Post by macaholic on 2008-05-11
Well I figured out more or less how to compile it, but now I get errors. When I run dmake, I get```
Checking module list
build -- version: 1.166

Fetching dependencies for module swext from solver... failed...
Fetching from CVS...  failed
Fetching dependencies for module moz from solver... failed...
Fetching from CVS...  failed
Fetching dependencies for module dictionaries from solver... failed...
Fetching from CVS...  failed
Fetching dependencies for module bitstream_vera_fonts from solver... failed...
Fetching from CVS...  failed
Fetching dependencies for module sdk_oo from solver... failed...
Fetching from CVS...  failed


WARNING! Project(s):
sdk_oo
bitstream_vera_fonts
dictionaries
swext
moz

not found and couldn't be built. Dependencies on that module(s) ignored. Maybe you should correct build lists.

dmake:  Error code 1, while making 'check_modules'

```

---

### Post by macaholic on 2008-05-11
Well unless anyone else has any clue on how to do this, I think I'm throwing in the towel unfortunately, I just can't figure out how to get the dmake step to work. I got it to find sdk_oo, so that doesn't show up anymore, but the rest of them are still there. I just want to use the new openoffice, yet Sun has to make it so hard dor me to do that, I wish they would just make 64-bit packages available.

---

### Post by macaholic on 2008-05-11
Well I think now I'm done, I broker down and forced the isntall of the i386 packages. The files browser and some other stuff looks funky, but other than that it seems to be working. I'm dissapointed, I don't like having to force isntall things when it is possible to install them naturally. If anyone manages to get it working normally, or someone puts up a repository with 64-bit debs, be sure to let me know.

---

