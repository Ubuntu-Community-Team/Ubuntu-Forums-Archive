---
title: "Ubuntu Install Problems...."
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by 2tired on 2008-05-10
I went to install the newest version of ubuntu, everything seemed to be ok until the reboot process. The ubuntu boot loader screen came up with the status bar going back and forth then went to a screen that said busybox error, type help for more commands. I tired to download the iso from different areas, burning it at different speeds and still get the same error after it seems to install. Just to see if it was the hard drive, I installed the 7.10 version and it still worked, Any ideas why I can't get ubuntu 8.04 installed on my hard drive???:confused:

---

### Post by Pumalite on 2008-05-10
Maybe your hardware. Post your specs.

---

### Post by 2tired on 2008-05-10
Amd athlon x2 3800+
2.5gb ram
128 mb video card, turbocache up to 512 mb
machspeed motherboard
win tv 150 tv card

are the recommended specs for 8.04 different then 7.10?

---

### Post by EXCiD3 on 2008-05-10
Can you post the error if it gave any info on the problem? Is your video card an nvidia?

---

### Post by Pumalite on 2008-05-10
> **2tired said:**
> Amd athlon x2 3800+
2.5gb ram
128 mb video card, turbocache up to 512 mb
machspeed motherboard
win tv 150 tv card

are the recommended specs for 8.04 different then 7.10?

Try the Alternate CD.

---

### Post by 2tired on 2008-05-12
Thank you all for the fast responses, as far as the video card, yes it is a nvidia, and the alternate cd is being downloaded now. All the error says after the ubuntu status bar goes back and forth for 10 mins or more then it stops and says on a black background with white writting is busybox error and to type help for more commands.. Is this version different than 7.10, cause I am using that now and have no problems?

---

### Post by 2tired on 2008-05-13
I tried the alternate cd, same error came up, the error says busybox v1.1.3 (debian 1:1.1.3-5 ubuntu1120) Built in shell (ash) enter help for a list of built in commands. I have no idea what this means, I have made countless discs all installed the same on 2 seperate hard drives. Anyone have any ideas?

---

### Post by Pumalite on 2008-05-13
Try some boot parameters. They are to be used alone or in different combinations until you hit the right one:
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)
The most common:

noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off vga=0x317 vga=791

---

### Post by EXCiD3 on 2008-05-13
I know that on some HP laptops the "all_generic_ide" boot parameter helped to get users past a crash in previous versions that dropped them to a busybox terminal with a tty job control error. I doubt it will help but its worth a shot.

---

### Post by 2tired on 2008-05-18
> **Pumalite said:**
> Try some boot parameters. They are to be used alone or in different combinations until you hit the right one:
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)
The most common:

noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off vga=0x317 vga=791

I am not really sure how to set these parameters, so if you could explain the process..thanks. And one more thing, why does the live cd work and the install doesn't??:(

---

### Post by EXCiD3 on 2008-05-18
To use boot parameters just hit F6 at the first menu you get to on the live cd and add them as a parameter in the boot line. I'm can't really say why the livecd works and the install doesnt as im not really sure. Usually if you have a problem it shows up in both places, livecd and install (if you can get that far).

---

### Post by 2tired on 2008-05-18
I tried to use different boot parameters, nothing worked. Right now I am running off of the live cd. Upon install I noticed that the hard drive I am trying to install to is scsi1 instead of hda1, anyone know why? Thanks again for all the fast responses!!:confused:

---

### Post by EXCiD3 on 2008-05-18
Correct me if im wrong, but recent kernels use sdX naming scheme for hard drives anymore. Only Grub use hdX when it detects hard drives.

It sounds like its a problem with your scsi controller...unfortunately lots of people have been having this trouble with hardy and i havent found any fixes for this yet. :(

---

### Post by 2tired on 2008-05-18
> **EXCiD3 said:**
> Correct me if im wrong, but recent kernels use sdX naming scheme for hard drives anymore. Only Grub use hdX when it detects hard drives.

It sounds like its a problem with your scsi controller...unfortunately lots of people have been having this trouble with hardy and i havent found any fixes for this yet. :(

Well at least I know it wasn't anything I did. I hope there will be a fix soon...until then I guess I will reload 7.10 and use it until it is not supported. Thanks again for your time EXCiD3, and hopefully they will let us know when a fix is available or if a new iso has to be downloaded and used. Thanks again and I hope to be on 8.04 soon....:)

---

### Post by EXCiD3 on 2008-05-18
Yeah unfortunately this seems to be the case. Glad to help a fellow Ubuntu user. There has been a lot of talk about an 8.04.1 release which seems to be needed...hopefully it will be fixed then.

You may want to post a bug report on [http://www.launchpad.net](http://www.launchpad.net) so the developers know about it and have something to work with. They would know much more than I do and might have a possible solution for it. Thats about as much guidance as i can give you. Good luck! :)

---

