---
title: "grub installation problem - now in bad state"
date: 2013-02-12
forum: Installation &amp; Upgrades
---

### Post by puzzledByLinux on 2013-02-12
Hi,
I am an amateur, and was trying to install Kubuntu 12.10 alongside a pre-existing Windows 7 installation on my Lenovo Z580 laptop. I can give more details later, but it seemed to be a pretty vanilla, uneventful installation as far as I could tell.

BUT I did somehow manage to hose grub. Now on power up, I fail to get the grub boot menu, but get only the grub command line:
grub>

but I noticed these two things (after a lot of reading and fiddling):

1. If I do
grub> chainloader (hd0,msdos1)+1
grub> boot
I get the grub menu and can boot windows 7 from it.

2. I can also boot windows 7 directly if I do:
grub> chainloader (hd0,msdos2)+1
grub> boot

(I am unable to boot kubuntu at all, but that problem will be addressed in a separate thread.)

My objective is to fix this behavior so as to get the grub boot menu on power up. If I have not given enough information to diagnose my grub problem, please let me know and I will post any additional files and/or output that you ask for. I appreciate your help. Thanks.

---

### Post by oldfred on 2013-02-12
Welcome to the forums.

May be best to run this.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)
   
Is your system UEFI? BootInfo Report will show us details.
       Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)


Some can boot but then need nomodeset for video issues or other boot parameters for certain hardware issue.
       
 Boot-Repair --> Advanced options --> GRUB options tab --> tick the "Uncomment GFXMODE" option --> Apply
Boot-Repair --> Advanced options --> GRUB options tab --> tick "Add kernel option: nomodeset" --> Apply
       
 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by puzzledByLinux on 2013-02-12
Hi oldfred,
Thanks for the rapid reply!

I, perhaps foolishly, ran Boot Repair first, and now I only get a "grub-rescue" prompt. Anyway, after that, I ran Boot Info and got the lengthy report pasted below. Any advice in the direction of restoring the grub menu on power up would be most appreciated. Thanks!

  [http://paste.ubuntu.com/1641105/](http://paste.ubuntu.com/1641105/)

---

### Post by puzzledByLinux on 2013-02-12
Link to grub info report given above.

---

### Post by puzzledByLinux on 2013-02-12
I reran Boot Repair, and ... the problem is solved. I get the boot menu and all is well. Thanks oldfred!!

---

### Post by oldfred on 2013-02-12
Glad that worked.

Not sure why you had to run it twice?

---

