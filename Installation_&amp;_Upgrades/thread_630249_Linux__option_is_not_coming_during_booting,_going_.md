---
title: "Linux  option is not coming during booting, going direct to windows"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by deepakiitm on 2007-12-03
Hi, 
I have Ubuntu, updated version of Kubuntu and Windows XP in my desktop.  Windows XP got some viruses, therefore, i reinstalled it. Now after installing XP, i am not getting the option to select Linux.  It is directly booting XP.  Before intalling the Windows, option was there. During XP installation i formated only C derive (which contains all windows file). I don't want to reinstall Linux because it contains important data. 
What can i do to recover the Linux.
Please help me soon.
System detail: 80G SATA hardisk
                         Intel 32 bit, 3GHz
                         512 DDR RAM
                         Intel mother board

---

### Post by Pumalite on 2007-12-03
Try reinstalling Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by deepakiitm on 2007-12-04
I tried to install the grub by using the procedural, mentioned in both tutorials. first i selected Linux primary partition as a boot by  replacing Windows derive boot option. Then at the terminal i typed following commands.

>sudo grub
grub >
grub >find /boot/grub/stage1

Error 15: file not found

I am getting an error, when trying to find out the stage1. What can i do to overcome it.

---

### Post by Pumalite on 2007-12-05
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by deepakiitm on 2007-12-07
Hi, 
i tried many things, like supper grub disk, system rescue software but still the problem as it is. The problem with these softwares are that system is not able to read the burn image. Even the first boot device is CD.  the link that you mentioned it has a lot things. I didn't get it fully. 
](*,)

Can you tell me some bullet proof solution of this problem.

---

### Post by deepakiitm on 2007-12-10
Hi, i got the linux back. I did it by using super grub.

Thanks for your help.

---

### Post by Pumalite on 2007-12-10
You are welcome. Good luck.

---

