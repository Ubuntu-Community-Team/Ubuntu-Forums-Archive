---
title: "Did upgrade now can not run updates"
date: 2016-03-04
forum: Installation &amp; Upgrades
---

### Post by poker master on 2016-03-04
Hi all stuck after doing an upgrade. run into lots of problems. Been using linux for a long time but not much on the command line. Has been real good up to now.

after doing and upgrade of Xubuntu. If i try and run the software updater i get the message that the package system is broken
and to type apt-get install-f.

when i type apt-get install-f it complanes about not being root so i go sudo apt-get install-f and get this

```
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
dan@dan-Aspire-M3970:~$ sudo apt-get install -f
[sudo] password for dan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  comerr-dev hal-info krb5-multidev libafpclient0 libaudio-dev libcups2-dev
  libdrm-amdgpu1 libdrm-dev libgcrypt11-dev libgl1-mesa-dev libglew1.6
  libglu1-mesa-dev libgnutls-dev libgnutlsxx27 libgpg-error-dev libgssrpc4
  libjpeg-dev libjpeg-turbo8-dev libjpeg8-dev libkadm5clnt-mit9
  libkadm5srv-mit9 libkdb5-7 libkrb5-dev liblcms2-dev libmicrohttpd5
  libmng-dev libp11-kit-dev libsdl2 libshairport1 libtasn1-6-dev
  libx11-xcb-dev libxcb-dri2-0-dev libxcb-dri3-dev libxcb-glx0-dev
  libxcb-present-dev libxcb-randr0-dev libxcb-shape0-dev libxcb-sync-dev
  libxcb-xfixes0-dev libxmu-dev libxmu-headers libxshmfence-dev libxt-dev
  libxxf86vm-dev mesa-common-dev x11proto-dri2-dev x11proto-gl-dev
  x11proto-xf86vidmode-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libsdl2-2.0-0
The following NEW packages will be installed:
  libsdl2-2.0-0
0 upgraded, 1 newly installed, 0 to remove and 13 not upgraded.
5 not fully installed or removed.
Need to get 0 B/321 kB of archives.
After this operation, 1,172 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 213371 files and directories currently installed.)
Preparing to unpack .../libsdl2-2.0-0_2.0.2+dfsg1-3ubuntu1.1_i386.deb ...
Unpacking libsdl2-2.0-0:i386 (2.0.2+dfsg1-3ubuntu1.1) ...
dpkg: error processing archive /var/cache/apt/archives/libsdl2-2.0-0_2.0.2+dfsg1-3ubuntu1.1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/i386-linux-gnu/libSDL2-2.0.so.0', which is also in package libsdl2:i386 2.0.3+z4~20140315-8621-1ppa1precise1
Errors were encountered while processing:
 /var/cache/apt/archives/libsdl2-2.0-0_2.0.2+dfsg1-3ubuntu1.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
dan@dan-Aspire-M3970:~$ 
```


So now what do i do also when i boot i get unknown error and after booting sometimes there is a process related to the gimp toolkit but it's Not GTK itself

now  on Ubuntu 14.04 (trusty) was on last LTS version

---

### Post by ajgreeny on 2016-03-04
It sounds as if you did not shutdown the software-updater before running that command.

You can not use two processes that update the system at the same time, so try closing the software-update application, then run the command ```
sudo apt-get install -f
``` again.

---

### Post by grahammechanical on 2016-03-04
If an update/upgrade has not completed and closed the task we may need to re-start to break the lock on the lock file. Then we can run apt-get commands in the terminal or load software updater.

Regards.

---

### Post by poker master on 2016-03-04
does the same thing the point is the software update won't run then tells me to run the above command,When i run the above command, the software updater has already crashed and is no longer a process. but i get the output above. If i run the package manager i get 

 You have 1 broken package on your system!

Use the "Broken" filter to locate it.

not sure what it's trying to tell me any ideas thanks

---

### Post by howefield on 2016-03-04
> **poker master said:**
> Preparing to unpack .../libsdl2-2.0-0_2.0.2+dfsg1-3ubuntu1.1_i386.deb ...
Unpacking libsdl2-2.0-0:i386 (2.0.2+dfsg1-3ubuntu1.1) ...
dpkg: error processing archive /var/cache/apt/archives/libsdl2-2.0-0_2.0.2+dfsg1-3ubuntu1.1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/i386-linux-gnu/libSDL2-2.0.so.0', which is also in package libsdl2:i386 2.0.3+z4~20140315-8621-1ppa1precise1
Errors were encountered while processing:
 /var/cache/apt/archives/libsdl2-2.0-0_2.0.2+dfsg1-3ubuntu1.1_i386.deb

You could try 

```
sudo dpkg -i --force-overwrite libsdl2-2.0-0.deb
```

or whatever the actual file name is if it isn't the above, do you still have any Precise ppas enabled ?

---

### Post by poker master on 2016-03-05
Hi tried both sudo dpkg -i --force-overwrite libsdl2-2.0-0.deb and
sudo dpkg -i --force-overwrite libsdl2-2.0-0.deb 
both come back with 
dan@dan-Aspire-M3970:~$ sudo dpkg -i --force-overwrite libsdl2:i386 2.0.3.deb
dpkg: error processing archive libsdl2:i386 (--install):
 cannot access archive: No such file or directory
dpkg: error processing archive 2.0.3.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libsdl2:i386
 2.0.3.deb
dan@dan-Aspire-M3970:~$

and to answer your question NO, No to any Precise ppas enabled ?
seems like it's looking for the above files. But software update never finishes so the files most likely never get down loaded.
just a guess.  
 
Anyway to use a live CD to fix this mess

---

### Post by howefield on 2016-03-05
Apologies, my fault for not giving you complete information.

You need to run the command from where the .deb file is or tell the command where the package is, eg, assuming it is downloaded and cached in /var/cache/apt/archives/.

```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/libsdl2:i386 2.0.3.deb
```

That isn't likely to be the name of the package, but you can check that by navigating with the file manager to /var/cache/apt/archives/.

---

### Post by poker master on 2016-03-06
No go but it does look like the file does not get downloaded. It looks like the system wants to process the file because the system thinks software update has run. but it crashes. So if i could find a copy of the file in a file archive. Then maybe i can fix it. Also looking at it looks like part of SDL. So maybe trying to uninstall SDL then try a reinstall. But i wonder why the software update crases.

---

### Post by howefield on 2016-03-07
> **poker master said:**
> No go but it does look like the file does not get downloaded. It looks like the system wants to process the file because the system thinks software update has run. but it crashes. So if i could find a copy of the file in a file archive. Then maybe i can fix it. Also looking at it looks like part of SDL. So maybe trying to uninstall SDL then try a reinstall. But i wonder why the software update crases.

Packages can be downloaded from packages.ubuntu.com, eg [http://packages.ubuntu.com/trusty/libsdl2-2.0-0](http://packages.ubuntu.com/trusty/libsdl2-2.0-0)

Scroll down and choose whether you want the 64 bit or 32 bit package. I'd be surprised if that was the issue but you never know.

---

### Post by poker master on 2016-03-08
apt-get does not want to run without error's bet synaptic does so looking at the file it is part of SDL Ver2 so i marked SDL to be removed. It also removed the newer version of kodi. But now i can run updates again. so at the moment it seems to have fixed the issue. I will try later to reinstall the newer Kodi. but for now i want to see if things are better so will wait a bit. The trouble started when i did a system upgrade form the last LTS version to the newest one. I think the old Kodi messed up the upgrade. And upgrading it after did not seem to help any.  
 
Thanks for your help none of the things you pointed out helped much but did point me in the right direction after a bit of thinking so it still saved me alot of time. Did not know where to look for the file. When you pointed that out. I found out it was not there. So it led me to this point. For now seems to work will let you know in a day or so if it still holds true. Have a good Day.....

---

