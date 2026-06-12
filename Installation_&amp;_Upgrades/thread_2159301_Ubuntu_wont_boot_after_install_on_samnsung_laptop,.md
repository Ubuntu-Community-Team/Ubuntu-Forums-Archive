---
title: "Ubuntu wont boot after install on samnsung laptop, wont recognize loader"
date: 2013-07-02
forum: Installation &amp; Upgrades
---

### Post by 506thcurrahee on 2013-07-02
after i purchased a samsung 5 series laptop, i went through the BIOS and turned off UEFI, placed it on CMOS only, then disabled quickboot. i then installed Ubuntu (13.04) without fault, partitioning a 50/50 split so i could keep windows 8 and NOT brick the thing just in case ( thank god i did). after the install was complete, i removed the USB drive with the installer and rebooted the system. i went directly into the BIOS into boot selection to put ubuntu as the primary, and it doesnt even give me an option to do it, OR to add the new boot device!

 ive tried this 3 times now, and had to redo my partitions back to normal every time. samsung doesnt have an answer for me, so i am throwing myself at the mercy of the forums!

 has anyone had this same problem? not having the ability to see the linux distro after install as a boot option?? i know its there, the partition is fine, it just wont allow me to get into it!

 please help, i hate windows 8 with a passion:(

---

### Post by oldfred on 2013-07-02
Some systems only boot Windows with UEFI and secure boot on. Did you try booting Windows with UEFI but secure boot off?

If you installed Ubuntu in CSM/Legacy/BIOS mode you cannot easily dual boot as you have to go into UEFI/BIOS and change settings each time.
Some that only install with CSM can be converted to UEFI and still dual boot from grub with UEFI booting with secure boot on or off.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

These specific models were an issue.
 [https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop)
Booting the Ubuntu installer in UEFI mode from a USB disk on certain Samsung laptops (530U3C, NP700Z5C) may trigger a firmware bug that renders the machine unbootable. Users are advised to use caution when installing on Samsung laptops and ensure that they are configured for legacy BIOS mode, not UEFI mode. (1040557) 

But I think these all worked.

 Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)
Samsung series 5 UltraBook, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)

---

### Post by 506thcurrahee on 2013-07-02
> **oldfred said:**
> Some systems only boot Windows with UEFI and secure boot on. Did you try booting Windows with UEFI but secure boot off?

If you installed Ubuntu in CSM/Legacy/BIOS mode you cannot easily dual boot as you have to go into UEFI/BIOS and change settings each time.
Some that only install with CSM can be converted to UEFI and still dual boot from grub with UEFI booting with secure boot on or off.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

These specific models were an issue.
 [https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop)
Booting the Ubuntu installer in UEFI mode from a USB disk on certain Samsung laptops (530U3C, NP700Z5C) may trigger a firmware bug that renders the machine unbootable. Users are advised to use caution when installing on Samsung laptops and ensure that they are configured for legacy BIOS mode, not UEFI mode. (1040557) 

But I think these all worked.

 Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)
Samsung series 5 UltraBook, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)

 yea i am not really too concerned with the windows boot loader, and i am aware that if i do want to go into windows i have to change the BIOS settings back to the quickboot and UEFI. its just not allowing me ANY boot options if i have those off, even with Ubuntu installed, and there is NO option to add another new boot option in the BIOS whatsoever

---

### Post by oldfred on 2013-07-02
What choices do you get in UEFI menu?

You should have something like the blue screen halfway down in this:
 Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by 506thcurrahee on 2013-07-10
> **oldfred said:**
> What choices do you get in UEFI menu?

You should have something like the blue screen halfway down in this:
 Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

 i get C MOS, UEFI, UEFI and C MOS

---

### Post by oldfred on 2013-07-11
And from UEFI do you get a menu? Or is it still just booting Windows?

did you review the similar Samsung models with working installs, some have posted how they did it.

---

### Post by 506thcurrahee on 2013-07-14
> **oldfred said:**
> And from UEFI do you get a menu? Or is it still just booting Windows?

did you review the similar Samsung models with working installs, some have posted how they did it.

 no, it gives no boot menu. in fact, when i go into boot priority, in any of the 3 modes, it gives me a max of 1 option, only the windows boot loader. and thats only in UEFI mode. in any other option, there are no other boot priorities. On top of that, it gives no option or ability to add any others. 

 im at a complete loss.

---

### Post by oldfred on 2013-07-14
It is not boot priority, but in UEFI menu you should have the choice of what to boot. Also from one time boot key what does it say.

       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---

