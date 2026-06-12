---
title: "CD errors during install"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by GrahamM on 2011-01-12
I am having almost same symptoms as described in the post:

[http://ubuntuforums.org/showthread.php?t=1463891&highlight=error+cd+install](http://ubuntuforums.org/showthread.php?t=1463891&highlight=error+cd+install)

However, I don't think my CD/DVD drive is bad. I have used it recently for a number of installs including XP itself and a lot of windows software.

When I installed 8.10 a few years ago, I added all_generic_ide, floppy=off, irqpoll so I tried that again. I got the LiveCD to run except for some reason Foxfire would not work. I tried an install anyway and got as far as entering my name etc and about that time the install crashed. I have repeated this and same thing happened.

Perhaps the install needs a driver for the LG Supermulti Securdisc ?? Or is there something I can enter that might make work more reliably?

I have checked the actual disk by running it on my laptop and installing to an external drive. I also checked the download and it is good. In fact I have downloaded and burned discs on both machines and just get to various stages. Sometimes the LiveCD wouldn't start but it does with the parameters I quoted above.

I tried using a thumb drive, but my old Asus A7V doesn't seem to like it!

So basically question is - Is there anything I can add to make reading from CD more reliable?

---

### Post by ErikNJ on 2011-01-12
...just a quick thought, check if the brand of the CD media is one that your drive is happy with.  Optical media can be very fussy and sometimes some brands of media are better than others (and some brands match certain drives better than others).

---

### Post by GrahamM on 2011-01-12
> **ErikNJ said:**
> ...just a quick thought, check if the brand of the CD media is one that your drive is happy with.  Optical media can be very fussy and sometimes some brands of media are better than others (and some brands match certain drives better than others).

Thanks for reply. I did change my cheap Ridata spindle CDs for a Memorex one, but no change.

I tried to buy a new drive, but nonone locally has IDE cd/dvdroms anymore :( 

Took my LG apart to clean, but lens was very clean even under magnifying glass!

I downloaded the Alt iso and am going to try that tomorrow.

---

### Post by ErikNJ on 2011-01-13
> **GrahamM said:**
> Thanks for reply. I did change my cheap Ridata spindle CDs for a Memorex one, but no change.

I tried to buy a new drive, but nonone locally has IDE cd/dvdroms anymore :( 

Took my LG apart to clean, but lens was very clean even under magnifying glass!

I downloaded the Alt iso and am going to try that tomorrow.

Is there any recommended media for your LG drive?

I've had good luck with Taiyo Yuden media.

Sometimes burning at a slower speed can be useful and be sure to stay within the burn speeds suggested by your media and drive.

I've also found some good info here in the past: [http://club.myce.com/](http://club.myce.com/) ...just don't changed your firmware unless you are sure of what you are doing (and why you are doing it).

---

### Post by GrahamM on 2011-01-13
I tried installing a different drive - this time a straight CDROM. The iso checks out and when I used the LiveCD to check the burned disk it was also OK.

I tried running LiveCD using CDROM and it got to the Splash screen, well 1/2 a splash screen. Install box didn't quite appear - Did get icons in top right, but all I could do is shut down.

Tried with loading parameters (??) mentioned earlier (All_generic_ide floppy=off, irqpoll) that had worked with 8.10 but all I got was a whole series of buffer overflows and read errors and the LiveCD loading was aborted.

This same LiveCD will run on my laptop. But not with either of two different drives on my Desktop. Seems I need to modify the loading parameters, but how?

Athlon 1.0Gb, 896Mb RAM, Nvidia TNT, Two HDs, DVD/DCDROM, CDROM That all runs well under XP.

I haven't tried the Alternate Install yet, but will. But not sure what that does for me and what I need to input.

Maybe I should give up on Meerkat and try and install Intrepid using same method I originally used?

---

### Post by Quackers on 2011-01-13
Have you tried the nomodeset option?
Also Lucid Lynx (10.04) may be a good option. It's a LTS release and may have better hardware support.

---

### Post by GrahamM on 2011-01-13
> **Quackers said:**
> Have you tried the nomodeset option?
Also Lucid Lynx (10.04) may be a good option. It's a LTS release and may have better hardware support.

I did try nomodeset but probably in combination with other parameters. I really don't know what most of those do, so it is a crapshoot.

Right now, I am attempting an install the Alt distribution. It seemed to be going OK, but at first could not detect my network card (wireless). Now it has stopped, saying that a file:///cdrom/pool/main/m/makedev/makedev_2.3.1-89Unbuntu1_all.deb was corrupt (This despite the iso and the burned CD checking out ahead of time.) More errors so now reinstalling base system. This is quite a circus <)

If this install doesn't complete, I think I might try a 8.10 CD (which came in a magazine). That would eliminate any burning errors.

But maybe in morning I will try 10.04 and see if that works.

---

### Post by GrahamM on 2011-01-14
Update - Tried using the ALT CD. It appeared to be getting through the installation, but then there was a problem when installing software. It said to go back and try again - It would retrieve 34 of 35 files and then crash on 35th. I tried moving ahead and installing the Grub bootloader and it also crashed. 

I have recently installed both Windows 2000 and XP on this same machine with never a problem. I deleted W2K with intent of using Ubuntu again (I had used Intrepid in past), But this Meerkat distribution is too much. I think I have to give up and admit defeat.

---

### Post by GrahamM on 2011-01-14
I finally put my old Intrepid 8.10 dvd in my LG DVD/CD drive and let it boot up the live CD - No problems. I then clicked on Install and it chugged away and installed with no special input from me.

But neither 10.10 or 10.10 alt would install despite the files being checked, cds checked and reburned multiple times. 

Now I am running, some further questions:

When I go to Update, I am now given option to update to 9.04. Should I do that or is there a way to update immediately to 10.04 (from 8.10)?

Should I be concerned about my Nvidia RIVA TNT2 video card - I seem to recall messing with drivers for that when I installed 8.10 a few years back. 

If I now try to boot XP directly as I used to, computer hangs. Presumably Ubuntu has removed or disabled the HDs MBR? If I Fdisk that can I reinstate it so that HD can be booted directly?
I can access XP if I boot from the Ubuntu HD using the grub menu but wondered if I can arrange it so either HD still boots.

---

### Post by GrahamM on 2011-01-14
I finally put my old Intrepid 8.10 dvd in my LG DVD/CD drive and let it boot up the live CD - No problems. I then clicked on Install and it chugged away and installed with no special input from me. Even imported my files & settings!

But neither 10.10 or 10.10 alt would install despite the files being checked, cds checked and reburned multiple times. 

Now I am running, some further questions:

When I go to Update, I am now given option to update to 9.04. Should I do that or is there a way to update immediately to 10.04 (from 8.10)?

Should I be concerned about my Nvidia RIVA TNT2 video card - I seem to recall messing with drivers for that when I installed 8.10 a few years back. 

If I now try to boot XP directly as I used to, computer hangs. Presumably Ubuntu has removed or disabled the HDs MBR? If I Fdisk that can I reinstate it so that HD can be booted directly?
I can access XP if I boot from the Ubuntu HD using the grub menu but wondered if I can arrange it so either HD still boots.

---

### Post by GrahamM on 2011-01-14
I finally put my old Intrepid 8.10 dvd in my LG DVD/CD drive and let it boot up the live CD - No problems. I then clicked on Install and it chugged away and installed with no special input from me. Even imported my files & settings!

But neither 10.10 or 10.10 alt would install despite the files being checked, cds checked and reburned multiple times. 

Now I am running, some further questions:

When I go to Update, I am now given option to update to 9.04. Should I do that or is there a way to update immediately to 10.04 (from 8.10)? 

EDIT: I have 10.04 downloaded and burned. LiveCD loaded fine and I am using it at present. Probably nothing to lose by trying an install in morning

If I now try to boot XP directly as I used to, computer hangs. Presumably Ubuntu has removed or disabled the HDs MBR? If I Fdisk that can I reinstate it so that HD can be booted again directly if I abandon the ubuntu install?

---

### Post by GrahamM on 2011-01-16
No responses here so decided to move ahead. Installed 10.04 (burned on same equipment as 10.10) with no problems. Funnily enough, it did not import my XP files as 8.10 had.

Conclusion Meerkat is the problem so far as installation on my computer is concerned. If anyone is interested, it is an Asus A7V with 1Gb Athlon, Nvidia Riva TNT2, 896Mb RAM, ATA100 disabled, Dlink G520 wifi card, PCI cards for Firewire, USB2.0, Sound card. Works perfectly with 8.10, 9.04 and 10.04 but will not even load live CD with 10.10.

No answers here on recovering boot capability of my XP hard drive. No pressing need right now, but I may want to do that in future if I remove the Ubuntu drive.

---

