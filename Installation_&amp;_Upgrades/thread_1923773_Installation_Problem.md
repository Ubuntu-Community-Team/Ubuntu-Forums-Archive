---
title: "Installation Problem"
date: 2012-02-11
forum: Installation &amp; Upgrades
---

### Post by salmanmajid on 2012-02-11
Hi I am new to Ubuntu. I downloaded Ubuntu 11.10 and wrote the .ISO on a CD. I rebooted the computer but it says "BOOT FAILURE PLEASE INSERT SYSTEM DISK". I ran the setup from Windows XP Home and then click "Demo and Full Installation" and then "Help Me Reboot from CD". I received message WindowBackend not supported and "cd_path" not found.

---

### Post by darkod on 2012-02-11
Did you copy the .iso file to the cd or you used an option Burn CD from Image? You need to burn the cd from that image, not just burn the files on it.

If you open the cd on another computer it should have files and folders on it, not just a single .iso file.

If the cd is created correctly, next thing to look at is the boot order in BIOS. The CD-ROM needs to be before HDD in the order, so that it boots from the cd before trying to boot from the hdd.

---

### Post by salmanmajid on 2012-02-11
Thanks brother, when I burned my first CD, I had extracted the files from the ISO and wrote those files on the CD root. Nothing happened "BOOT FAILURE INSERT SYSTEM DISK" was what I was getting. Then I copied ISO only on the CD, same error. So what I am going to do now is (as you have suggested), use a CD burner software and use option BURN CD from ISO??? What if I want to run the setup from my Windows desktop? Thanks.

---

### Post by darkod on 2012-02-11
Extracting the files copies them, but doesn't create a boot process for the cd. That's why it can't boot.

You need to use the Burn from Image option, or what ever it is called in the burning software you are using. Only like that it will be bootable cd.

PS. If you don't have any burning software, ImgBurn is a free windows software for burning cds. You will find it on google.

---

### Post by drmrgd on 2012-02-11
> **salmanmajid said:**
> Thanks brother, when I burned my first CD, I had extracted the files from the ISO and wrote those files on the CD root. Nothing happened "BOOT FAILURE INSERT SYSTEM DISK" was what I was getting. Then I copied ISO only on the CD, same error. So what I am going to do now is (as you have suggested), use a CD burner software and use option BURN CD from ISO??? What if I want to run the setup from my Windows desktop? Thanks.

Just to add to what darkod said, here is come community documentation on how to make a bootable Ubuntu CD from the ISO image:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

That should help walk you through the process.

In answer to your other question, like most OS installations, the system needs the hard disk to be unmounted at the time of installation.  This is especially the case when you're going to dual boot and mess with the partition table.  So, you have to boot from the installation CD and install from there.  It's the same case for installing Windows if I remember correctly (been a long time!).

---

### Post by salmanmajid on 2012-02-18
Thanks a lot for your help. Burning the Image solved the problem. I am sure I will be back with more questions. Thanks again.

---

