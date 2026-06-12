---
title: "install stalls with &quot;failed to start x server&quot;"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by unclokie on 2007-05-28
I have followed the install proceedure both for the standard 7.04 and alternate methods of install and I continualy get this sane error. I suspect it has to do with my graphics board/driver and I have a LINUX driver that I downloaded from the NVIDIA website but I don't know how to get the driver changed without getting the UBUNTU to boot fully.HELP PLEASE!
Attached are the screens I see when it fails:














;

---

### Post by Blender on 2007-05-28
Could you attach your **/var/log/Xorg.0.log** file?

---

### Post by NZ-Wanderer on 2007-05-28
I'm no expert, but here is what I did when an upgrade broke my graphics...

First off, get into safe mode (recovery mode I think it called) so you get a command prompt after typing in your name and password

Then I typed: ```
sudo wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/NVIDIA-Linux-x86-1.0-9746-pkg1.run
```
(to get the latest drivers)

Then I typed ```
sudo sh NVIDIA-Linux-x86-1.0-9746-pkg1.run
```
(And followed all the prompts)

Then just rebooted the computer and it WORKED :) :)

Hope this is maybe of some help, Appoligies if it's not..

---

