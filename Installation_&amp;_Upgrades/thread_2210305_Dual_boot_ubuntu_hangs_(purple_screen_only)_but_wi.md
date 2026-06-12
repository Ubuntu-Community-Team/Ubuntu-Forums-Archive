---
title: "Dual boot ubuntu hangs (purple screen only) but windows perfect"
date: 2014-03-10
forum: Installation &amp; Upgrades
---

### Post by tane2 on 2014-03-10
Hi all, 

I am an Ubuntu novice but have been doing a few searches and trying different things to fix my problem to no avail. 
My problem is : 
 - Running Dualboot w7 and ubuntu 13.1. I am unable to boot into the Ubuntu operating system* as it just hang on the purple screen every time I try. It won't let me into the sign on screen or anything. *It has let past the purple screen and therefore log in twice after a bunch of random button pressing. 
- See attched pics for more info
My Situation is:
- Installed using a USB made with UNETbootin. Have done this 4 times before with no troubles (even on current machine) but only as a single operating system. 
- Mostly followed he instructions listed [here]("http://lifehacker.com/5403100/dual-boot-windows-7-and-ubuntu-in-perfect-harmony")

 for my dual boot set-up but a couple of things varied. 
- Computer is and Acer Aspire S3 'ultrabook' with an i3-2367M CPU, 4gb Ram and a 120gb Samsung 840 SSD. 
-SSD is partitioned as follows: From left to right: 
                   
                     -100mb NTFS  'system reserved' (almost certain this was created by windows)
                     -19.9GB NTFS 'C:' This is where windows is installed
                     -  Extended partition 
                           - 16gb ext4 for ubuntu
                           - 5gb swap partition
                     - 70.79 GB FAT32 Storage drive for shared files

I am new to Ubuntu and really really like it. I want to use ubuntu predominantly have windows for things like uni work and word processing.
Any help is seriously appreciated. Hopefully there's an answer out there!

P.s i have added a couple of pics which might aid diagnosis. I took the during a couple of failed boots

---

### Post by ubfan1 on 2014-03-10
To slow SSDs to allow them to boot, try adding:
libata.force=noncq
to the grub line starting with "linux".  At the grub menu, edit the grub commands by typing "e" (instructions on screen), and adding the
item to where the "quiet splash" items are.

Another thing to look at is the rest of the grub commands setting up the device.  You would expect the disk references to be for (hd0,... but if you see hd1, that probably is the problem.  Edit all the hd1 s back to hd0 (and if you see sdb s change them back to sda s too). If that allows you to boot, immediately run sudo update-grub to fix the problem.

---

### Post by oldfred on 2014-03-10
Often a video issue which is past what Boot-Repair can fix, but post link to BootInfo report just to be sure everything is correct first.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

If an Ultrabook, do you have dual video. And can you control which video mode it uses to boot or does it just auto switch?
If booting with nVidia you need nomodeset, but if Intel then other boot parameters usually required. 

      
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

Other Acer's, may have similar issues?

 How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)
Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Added new msata drive post #3
[http://ubuntuforums.org/showthread.php?t=2174844](http://ubuntuforums.org/showthread.php?t=2174844)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)
Acer UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64 June 2012
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)

---

### Post by tane2 on 2014-03-10
Hi, I am currently on a live usb. I have done the boot info report. Ths link is :[http://paste.ubuntu.com/7070206/](http://paste.ubuntu.com/7070206/)
Cheers

---

### Post by oldfred on 2014-03-10
Install looks normal and in BIOS boot mode for both Windows & Ubuntu.

Do you get to grub menu? or a grub rescue or grub> error?

If you can get to grub menu, try boot options for video mode either nomodeset or one or more needed for Intel depending on what video mode you boot with.

---

### Post by tane2 on 2014-03-10
I get the grub menu. I am pretty sure I only have one video card (Intel HD graphics 3000). Does this mean nomodset is worth trying or do I only try that when you have two video cards?

---

### Post by tane2 on 2014-03-10
Just tried to edit the grub like ubfan1 recommended. I am not sure if I put the command he mentioned in the right spot as it didn't work. I have attached a pic of where I pasted it.
[https://drive.google.com/file/d/0B5DwKxOt4SznYWRvRVl0bGhjbG1QTzN2UEh6bG96Y3ZNRHdz/edit?usp=sharing](https://drive.google.com/file/d/0B5DwKxOt4SznYWRvRVl0bGhjbG1QTzN2UEh6bG96Y3ZNRHdz/edit?usp=sharing)

---

### Post by tane2 on 2014-03-10
@ ubfan1 are you able to elaborate on the following?
My noob brain cannot understand what i need to do..sorry :(. 
> **ubfan1 said:**
> 
Another thing to look at is the rest of the grub commands setting up the device.  You would expect the disk references to be for (hd0,... but if you see hd1, that probably is the problem.  Edit all the hd1 s back to hd0 (and if you see sdb s change them back to sda s too). If that allows you to boot, immediately run sudo update-grub to fix the problem.

---

### Post by oldfred on 2014-03-10
Your set root looks ok.

But do not add a line to boot stanza, but just like the example for nomodeset, you replace or put next to quiet splash on linux line.
I prefer to replace quiet splash as then you see the boot process scroll by (quickly) and may be able to see issues. Otherwise you have to look in /var/logs/dmesg which all all the lines you see when you do not have quiet splash.

You can add several boot options, just separate by space. Note in Linux case is important and most command do not use capitals. Also even spaces can be important.

---

### Post by tane2 on 2014-03-10
Hi, 
I tried what you said and have attached pics. It didn't seam to work. I got some more pics of the errors that popped up and what I did to get them. [https://drive.google.com/folderview?id=0B5DwKxOt4SznT0VwODliY21NOHc&usp=sharing](https://drive.google.com/folderview?id=0B5DwKxOt4SznT0VwODliY21NOHc&usp=sharing)

---

### Post by ubfan1 on 2014-03-10
Your grub.cfg picture uses the hd0, so that is not the problem  -- did you try the  modification to the  line starting with   linux  .....    libata.force=noncq quiet splash ...?  If that doesn't help, maybe the SSD is named something else, but the errors seem to indicate it's not found at all.  Did you turn off raid?  If you can get to a grub prompt, (even from live media), you might try the grub command line (type "c")  then see what disks grub sees by using the tab key for command completion:    at the grub prompt, type   set  root=(hd    and grub should either fill in the 0 or give you a list of choices.  (if from live media, the usb may be 0, and ssd 1, but I'm looking for higher numbers, like 2... to see if some other device got the next slot.

---

