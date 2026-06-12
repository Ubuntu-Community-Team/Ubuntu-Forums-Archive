---
title: "No bootable device"
date: 2013-08-25
forum: Installation &amp; Upgrades
---

### Post by miguel3 on 2013-08-25
I'm new to this short of stuff but I try my best to read the forums for fixes before I post anything. I'm also going to try and be as detailed as possible. 

So i successfully dual booted ubuntu 12.04 with windows 7 on my gf's hp dv4 laptop. After a couple months i went in to ubuntu to update it to 13.04. The upgrade was taking awhile and i fell asleep. when i woken up in the morning i restarted the laptop. When i restarted it i was not able to boot into either ubuntu or windows. I tried booting with a live cd and a usb, which both did not work. I tried a couple other things like boot-fix and update grub through the ubuntu recovery but those also did not work. Finally i decided to do a system restore with my repair disc. My repair disc would not start up same as with the live cd( just hung on a black screen with a blinking cursor and then when to the grub menu)

Someone said that my hard drive was fried and i needed to get another one. I did not want to give up so i borrowed my moms hp 2000 netbook (with windows 8) and switched out the hard drives to see if my gf's would work. On my moms laptop i was able to use the live cd to get into ubuntu with my gfs hard drive. From there i recovered all opf the files she needed like pictures and documents. Then i decided to re-install ubuntu. I picked the option "erase disk and install ubuntu". After this i was only to boot into ubuntu on my moms laptop through boot options menu F9. 

Since i seen ubuntu working on my moms laptop(even though i could only boot through the boot options menu) i now decided to put the hard drive back into my gfs laptop. Now i dont even get the grub menu like before. All i see is** No bootable device -- insert boot disk and press any key. **I tried using my recovery disc like before but i get the same result (black screen with a blinking cursor) then it goes to the screen with No bootable device. I tried the live cd and usb and both of those did not work either. So now im here asking for help. I just want to be able to get windows 7 working again so my gf can use it for school. thanks guys

---

### Post by oldfred on 2013-08-25
Windows 8 systems use UEFI and gpt partitioning and have secure boot as a setting.
Most Windows 7 systems are BIOS with MBR partitioning (a few new one's were also UEFI). 
The two are not compatible unless in same mode -UEFI or BIOS.
And then Ubuntu has to be in the same boot mode as Windows.
And some newer Windows 7 systems were installed in BIOS mode, but actually had UEFI, so Ubuntu may be UEFI but should be BIOS?

Best to post details:
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by miguel3 on 2013-08-25
thanks for the reply olfred, 

im going to do everything you posted but i have a basketball game at 2 so ill will once i get back.

quick question though. do i try all this on my gfs laptop or switch the hard drive to my moms laptop? im just asking because my gfs one wont boot any cd's or usb

---

### Post by miguel3 on 2013-08-25
> **oldfred said:**
> Windows 8 systems use UEFI and gpt partitioning and have secure boot as a setting.
Most Windows 7 systems are BIOS with MBR partitioning (a few new one's were also UEFI). 
The two are not compatible unless in same mode -UEFI or BIOS.
And then Ubuntu has to be in the same boot mode as Windows.
And some newer Windows 7 systems were installed in BIOS mode, but actually had UEFI, so Ubuntu may be UEFI but should be BIOS?

Best to post details:
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)


[COLOR=#000000]thanks for the reply olfred, [/COLOR]

[COLOR=#000000]im going to do everything you posted but i have a basketball game at 2 so ill will once i get back.[/COLOR]

[COLOR=#000000]quick question though. do i try all this on my gfs laptop or switch the hard drive to my moms laptop? im just asking because my gfs one wont boot any cd's or usb[/COLOR]

---

### Post by oldfred on 2013-08-25
As long as you do not run any auto repairs with Boot-Repair on your Mom's laptop and just run the BootInfo report first.
Manual repairs should also work but that gf's system will not boot USB or CD is an issue.
Some laptops get locked up in BIOS after too many boot errors. Sometimes a full hard reboot works. You have to shutdown, remove battery, and press start button to remove any residual power. Then it may let you back into BIOS to boot from USB or CD. Also you should have an f-key (f12 on mine) to one time boot CD or Flash drive.

---

### Post by miguel3 on 2013-08-25
ok i was able to get the BootInfo report. [http://paste.ubuntu.com/6027145/](http://paste.ubuntu.com/6027145/)

I did the boot repair and this is the other url [http://paste.ubuntu.com/6027150/](http://paste.ubuntu.com/6027150/)

ok i found out why i could boot with the usb stick. i created the live usb on the wrong drive instead of my usb.

I ran the boot repair through the live usb and then after i installed ubuntu all over again. 

I deleted my windows partition so i no longer a dualboot. I still want to recover using my windows recovery disc. Is this possible?

I still have the problem trying to boot off a cd. I put my recovery disc and it hangs on a black screen with a blinking cursor then it goes into ubuntu. I tried using a live cd of ubuntu to see if that would work. That live cd did the same as my recovery disc.

---

### Post by oldfred on 2013-08-25
That shows no Windows at all and a UEFI boot with gpt partitioning and efi partiton.

If you had a Windows install with data you did not backup before hand stop using system. Every use overwrites more data.

---

