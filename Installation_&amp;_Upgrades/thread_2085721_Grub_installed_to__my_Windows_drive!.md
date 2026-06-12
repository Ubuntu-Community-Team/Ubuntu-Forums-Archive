---
title: "Grub installed to  my Windows drive!"
date: 2012-11-18
forum: Installation &amp; Upgrades
---

### Post by rmp5s on 2012-11-18
I plugged a drive into my computer through USB, booted to a Ubuntu 12.10 DVD I made and installed Ubuntu 12.10 to the USB drive.  Everything went as planned.  I unplugged the USB hard drive and now, when I try to boot to my original Windows install on a totally separate drive, it says "grub error" and won't boot...

I REALLY need a fix to this.  

A - I never saw this coming
B - I have things I REALLY need on the drive
C - the drive is encrypted with TrueCrypt.  Otherwise, I'd just plug it in and pull off what I need...

Please, please, please...any and all info and/or help is greatly appreciated.

---

### Post by Mr_JMM on 2012-11-18
Ubuntu hasn't killed your Windows drive. Please amend the thread title.

You installed Ubuntu on an external drive. It installed Grub menu. You removed the drive. Grub can't find the information it needs.

Have you tried plugging the drive back in?

Have you tried putting the UbuntuDVD back in the DVD drive, booting into a live session and reinstalling grub to the Windows drive?

Again, please amend your thread title.

---

### Post by rmp5s on 2012-11-18
> **Mr_JMM said:**
> Ubuntu hasn't killed your Windows drive. Please amend the thread title.

You installed Ubuntu on an external drive. It installed Grub menu. You removed the drive. Grub can't find the information it needs.

Have you tried plugging the drive back in?

Have you tried putting the UbuntuDVD back in the DVD drive, bbooting into a live session and reinstalling grub to the Windows drive?

Again, please amend your thread title.

I use the thread title as a bit of a joking affront.  Definitely not to be taken 100% literally. I will change it.

Anyway...yes, I plugged a SATA drive into my laptop through USB and installed Ubuntu on it.

No, I haven't tried plugging the external SATA drive into it again, nor have I tried booting to the DVD again.  I will do this.

How can I remedy this issue should either of these things help?

---

### Post by Mr_JMM on 2012-11-18
> **Mr_JMM said:**
> ...booting into a live session and reinstalling grub to the Windows drive?

10char

---

### Post by rmp5s on 2012-11-18
> **Mr_JMM said:**
> 10char

What?

Not sure how to change thread title. If a mod wants to change it, have at it.

I plugged the USB drive back in...nothing. Neither booted. Black screen. Nothing happened.

So I put the DVD back in and booted to it. It booted...not sure what to do now.

Local Windows HDD is in, Ubuntu USB drive is plugged in, booted to DVD now. 

Words of wisdom GREATLY appreciated...

---

### Post by rmp5s on 2012-11-18
Really wish I could change the thread title...don't know how to.

But yea...anyone?  Hint, tip or trick to get me back into the old Windows drive?

:-D

On a side note...I'm by no means a Linux n00b but, admittedly it's been a month or 2 since checking out Ubuntu and...uh...when did Ubuntu get so awesome?!  It was really good before but wow...on a live CD, it found my wireless NIC, bluetooth, keyboard, trackpad WITH scrolling, battery, sound card, everything...AND it has thunderbird pre-installed.

This is very, very good.  I'm legitimately impressed.  But...just as when I used Ubuntu Netbook Remix forever ago, it comes down to power management.  If only the power control was better (the thing is SCREAMING along right now and I'm not doing anything but typing here...) I would easily happily run this day to day.   (PC is an HP DV6T w/ an i7-2720QM, bluetooth, blu-ray drive, 500GB Momentus XT, 8GB RAM, AMD 6770M if you're wondering.)

---

### Post by rmp5s on 2012-11-18
Got a GRUB editor...not sure what to do still...lol

[http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order](http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order)  

Again...any help appreciated...

---

### Post by oldfred on 2012-11-19
Changed title.

When doing a full install to any second drive internal or external, you have to use manual install as grub defaults to installing to sda with all the auto install options. With manual install you get the option to install to the MBR of the second drive.

Encrypted Windows could be a big issue. Grub not only installs to the MBR, but grub's core.ing is in the next 30 plus sectors after the MBR. Encryption code may be in that same area. Not sure if just installing a Windows boot loader will work or not. Do not know Windows encryption and how it works. Supposed Windows boot partition  was separate so you could encrypt the main partition, so it then should be repairable. But other encryption tools verify MBR and other things that may then not be ok??

Boot repair can  restore a standard Windows like boot loader or you can use your Windows install DVD or recovery CD to repair Windows.

       How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)


Boot Repair can install a Windows work alike (but not encryption based) boot loader to the internal drive and install grub2's boot loader to the external drive.

 Post the link to the BootInfo report that this creates.

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

If you are getting black screen, that may also be separate video issue. Boot-Repair can change grub's default to get menu to show, but Ubuntu may need some boot parameters to boot. What video card/chip do you have?

 Boot-Repair --> Advanced options --> GRUB options tab --> tick the "Uncomment GFXMODE" option --> Apply
    
       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by rmp5s on 2012-11-19
> **oldfred said:**
> Changed title.

When doing a full install to any second drive internal or external, you have to use manual install as grub defaults to installing to sda with all the auto install options. With manual install you get the option to install to the MBR of the second drive.

Encrypted Windows could be a big issue. Grub not only installs to the MBR, but grub's core.ing is in the next 30 plus sectors after the MBR. Encryption code may be in that same area. Not sure if just installing a Windows boot loader will work or not. Do not know Windows encryption and how it works. Supposed Windows boot partition  was separate so you could encrypt the main partition, so it then should be repairable. But other encryption tools verify MBR and other things that may then not be ok??

Boot repair can  restore a standard Windows like boot loader or you can use your Windows install DVD or recovery CD to repair Windows.

       How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)


Boot Repair can install a Windows work alike (but not encryption based) boot loader to the internal drive and install grub2's boot loader to the external drive.

 Post the link to the BootInfo report that this creates.

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

If you are getting black screen, that may also be separate video issue. Boot-Repair can change grub's default to get menu to show, but Ubuntu may need some boot parameters to boot. What video card/chip do you have?

 Boot-Repair --> Advanced options --> GRUB options tab --> tick the "Uncomment GFXMODE" option --> Apply
    
       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Thank you. I will look into this this afternoon. 

The drive is encrypted with True Crypt if that tells anyone anything.

---

### Post by YannBuntu on 2012-11-19
> **rmp5s said:**
> I plugged a drive into my computer through USB, booted to a Ubuntu 12.10 DVD I made and installed Ubuntu 12.10 to the USB drive.  Everything went as planned.  I unplugged the USB hard drive and now, when I try to boot to my original Windows install on a totally separate drive, it says "grub error" and won't boot...

I REALLY need a fix to this.

Please run [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). It should ask you if the Ubuntu disk is removable or not. Answer "Yes".
Then click the "Recommended Repair" button, and reboot the pc.

If any problem, please indicate the URL that will appear.

---

### Post by rmp5s on 2012-11-19
> **YannBuntu said:**
> Please run [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). It should ask you if the Ubuntu disk is removable or not. Answer "Yes".
Then click the "Recommended Repair" button, and reboot the pc.

If any problem, please indicate the URL that will appear.

I just ran Boot-Repair.  It gave me this URL:

[http://paste.ubuntu.com/1370226/](http://paste.ubuntu.com/1370226/)

I'm going to reboot now.  *fingers crossed*

---

### Post by rmp5s on 2012-11-19
> **rmp5s said:**
> I just ran Boot-Repair.  It gave me this URL:

[http://paste.ubuntu.com/1370226/](http://paste.ubuntu.com/1370226/)

I'm going to reboot now.  *fingers crossed*

Yup...nothin. Still won't boot the Windows drive. :-(

---

### Post by YannBuntu on 2012-11-19
Your filesystem seems broken, and Boot-Repair didn't manage to fix it via fsck.
I recommend you try to fix it via TestDisk. If still no joy, try to recover your lost documents via TestDisk.

EDIT: follow OldFred's advice below instead.

---

### Post by oldfred on 2012-11-19
It is not showing anything since it is encrypted.

I did find this. The truecrypt boot loader is required.

[http://www.truecrypt.org/docs/?s=rescue-disk](http://www.truecrypt.org/docs/?s=rescue-disk)

---

