---
title: "libgl1-mesa-dri broken?"
date: 2007-08-02
forum: Installation &amp; Upgrades
---

### Post by useResa on 2007-08-02
After today's update (running Feisty) I got stuck with a broken libgl1-mesa-dri package.

When I try to re-install the package using Synaptic the following is indicated
```
libgl1-mesa-glx (version 6.5.2-3ubuntu7) will be upgraded to version 6.5.2-3ubuntu8
libgl1-mesa-dri (version 6.5.2-3ubuntu8) will be re-installed
```When I click apply an error occurs, being:
> E: /var/cache/apt/archives/libgl1-mesa-glx_6.5.2-3ubuntu8_i386.deb: trying to overwrite `/usr/lib/libGL.so.1', which is also in package nvidia-glxWhen I try to overcome this using the terminal, and issue the command
**sudo apt-get upgrade**, the result is the following```
0 rdrijsen@rdrijsen-laptop: ~
Thu Aug 02, 22:50 $ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libgl1-mesa-dri: Depends: libgl1-mesa-glx (= 6.5.2-3ubuntu8) but 6.5.2-3ubuntu7 is installed
E: Unmet dependencies. Try using -f.
```When doing as suggested and issue the command sudo apt-get install -f the result is
```
0 rdrijsen@rdrijsen-laptop: ~
Thu Aug 02, 22:50 $ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgl1-mesa-glx
The following packages will be upgraded:
  libgl1-mesa-glx
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0B/143kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 235395 files and directories currently installed.)
Preparing to replace libgl1-mesa-glx 6.5.2-3ubuntu7 (using .../libgl1-mesa-glx_6.5.2-3ubuntu8_i386.deb) ...
Unpacking replacement libgl1-mesa-glx ...
dpkg: error processing /var/cache/apt/archives/libgl1-mesa-glx_6.5.2-3ubuntu8_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libGL.so.1', which is also in package nvidia-glx
Errors were encountered while processing:
 /var/cache/apt/archives/libgl1-mesa-glx_6.5.2-3ubuntu8_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```Any suggestions on how this can be resolved?

---

### Post by mont on 2007-08-02
I have the same problem.
Now it is impossible to install new applications also.

must find a solution to this.

---

### Post by useResa on 2007-08-03
Okay ... the problem has been fixed ... but I am not sure whether it was the right procedure. These are the steps that I have taken or -- which is more correct -- I had to taken in some case.
[LIST=1]
[*]Locked the package libgl1-mesa-glx so it stayed at version 7 (version 8 was the new candidate) and the upgrade could not be performed due to the broken liblg1-mesa-dri
[*]Removed the broken package libgl1-mesa-dri, which in the process also removes ubuntu-desktop, xorg and a 3rd package which I thought I would be able to remember (stupid me :(). **Ignored** the restart indication!
[*]Unlocked libgl1-mesa-glx and selected all upgradable packages and ran the upgrade. This one stopped at libgl1-mesa-glx because of /usr/lib/libGL.1.so which is also part of nvidia-glx.
[*]Locked libgl1-mesa-glx again and removed nvidia-glx (completely)
[*]Unlocked libgl1-mesa-glx and upgraded. Now with success.
[*]Re-installed nvidia-glx and ubuntu-dekstop (last one also installs xorg).
[*]Now performed the restart[/LIST]This resulted in a broken xorg. Tried a re-install of nvidia-glx but unfortunately no success. Fortunately I had a copy of a download nvidia driver still at my box (NVIDIA-Linux-x86-1.0-9755-pkg1.run).
Went into the directory, changed to root and ran the program.
After this restarted the computer (sudo shutdown -r now) and was back in business.

So, I resolved it ... but I am convinced there is a more efficient and easier way to do this. But this did if for me.

---

### Post by useResa on 2007-08-04
From others I have learned that this issue might also be solved by issuing the following command
```
dpkg-divert --remove /usr/lib/libGL.1.so
```A lot easier  :D

---

