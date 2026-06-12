---
title: "Fixing the nvidia driver issue"
date: 2009-12-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Robin Nixon on 2009-12-16
For me, on a 32-bit computer, the following solution (courtesy of [sevenmachines]("https://launchpad.net/%7Esevenmachines")) enabled the 195.22 nvidia drivers, and restored my desktop to its full resolution of 1680 x 1050.[INDENT]**In order click each of the following .deb packages, and install it using the Gdebi Package Installer when prompted:**[INDENT]
[LIST]
[*][https://launchpad.net/~sevenmachines/+archive/nvidia+1/+files/nvidia-195-kernel-source_195.22-0ubuntu0~sevenmachines2_i386.deb]("https://launchpad.net/%7Esevenmachines/+archive/nvidia+1/+files/nvidia-195-kernel-source_195.22-0ubuntu0%7Esevenmachines2_i386.deb")
[*][https://launchpad.net/~sevenmachines/+archive/nvidia+1/+files/nvidia-195-libvdpau_195.22-0ubuntu0~sevenmachines2_i386.deb]("https://launchpad.net/%7Esevenmachines/+archive/nvidia+1/+files/nvidia-195-libvdpau_195.22-0ubuntu0%7Esevenmachines2_i386.deb")
[*][https://launchpad.net/~sevenmachines/+archive/nvidia+1/+files/nvidia-glx-195_195.22-0ubuntu0~sevenmachines2_i386.deb]("https://launchpad.net/%7Esevenmachines/+archive/nvidia+1/+files/nvidia-glx-195_195.22-0ubuntu0%7Esevenmachines2_i386.deb")
[/LIST]
     [/INDENT]**Restart your computer to complete the installation.**
[/INDENT]I don't know whether all three are required, but the first two are needed by the third one. Other packages for 64-bit computers etc are available on sevenmachines' launchpad site at:[INDENT][https://launchpad.net/~sevenmachines/+archive/nvidia+1/+packages]("https://launchpad.net/%7Esevenmachines/+archive/nvidia+1/+packages")
[/INDENT]

---

### Post by gnomeuser on 2009-12-16
And whatever you do NOT use dkms 2.1.1.0-0ubuntu3, as this version has a missing then statement in the dkms_installer which results in crippling your machine on bootup. 

There is recovery to be made should you have made the mistake of using the previous version. Boot a LiveCD and edit /usr/lib/dkms/dkms_installer

Find 

      if [ -L /vmlinuz -a -e /vmlinuz ]
      then <-- insert then here
	linktarget="$(basename "$(readlink /vmlinuz)")"

save and reboot your machine.

I repeat, using dkms 2.1.1.0-0ubuntu3 will screw you over, it's dangerous. Use dkms 2.1.1.0-0ubuntu5 or higher and be saved the horror.

---

