---
title: "MBR question"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by ETW Grumpy on 2010-02-25
During a failed Ubuntu install, I started getting the Error 21 message. I tried everything suggested here to no avail. I replaced a CD drive thinking the old one was torched, no help. What I'm thinking about doing is putting the problem HDD in an external enclosure to recover the data that I want. My next question is can I fix the error 21 problem (rewriting the MBR?) from my laptop or would I be better off just wiping the drive and installing Linux only on that drive? The next question is how do I do that from the laptop, I have no experience doing that type of operation. Thanx.

---

### Post by khelben1979 on 2010-02-25
Maybe [this old thread]("http://ubuntuforums.org/showthread.php?t=62717") can help you out?

---

### Post by ETW Grumpy on 2010-02-25
Thanks khelben, but those threads address issues where Grub is accessible or multiple HDD's. I have one HDD with dual partition and it won't boot past the initial Dell splash screen. I would just like to know if it sounds like this HDD is toast before I spend the money on an external enclosure. Thanx.

---

### Post by QIII on 2010-02-25
Does the Dell splash screen stay there, or does the screen go blank after a few moments?

Edit:  Eh.  Sorry.  Reread.  Must be, or you wouldn't be getting the GRUB error.  Never mind.

Let me do some digging.

Edit again:  You may be able to just reinstall GRUB using the LiveCD, or go here and use this highly recommended solution:

[http://www.supergrubdisk.org]("http://www.supergrubdisk.org/")

---

### Post by presence1960 on 2010-02-25
> **ETW Grumpy said:**
> During a failed Ubuntu install, I started getting the Error 21 message. I tried everything suggested here to no avail. I replaced a CD drive thinking the old one was torched, no help. What I'm thinking about doing is putting the problem HDD in an external enclosure to recover the data that I want. My next question is can I fix the error 21 problem (rewriting the MBR?) from my laptop or would I be better off just wiping the drive and installing Linux only on that drive? The next question is how do I do that from the laptop, I have no experience doing that type of operation. Thanx.

I need to see more about your setup & boot process. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by ETW Grumpy on 2010-02-25
presence1960- I've got a Dell Dimension 2400.
 I get the splash screen...Dell BIOS Rev A05...
 Then I get Grub loading stage 1.5.
 Grub loading Error 21

 That's it. No chance to enter text or anything else. 
   Primary Master Drive is the Hard Drive
   Secondary Master Drive CD-ROM
   Secondary Slave Drive CD-ROM

Boot Sequence:
 1. IDE CD-ROM Device
 2. Hard-Disk Drive C:

 I've tried booting with the Ubuntu disk in both CD drives and it won't boot. I know the disk is good because that's what used initially for the install. I just replaced one of my CD drives in case it was bad.

 I even tried booting with an older version of Ubuntu, that didn't work.

 I tried booting with a brand new XP disc and that didn't work.

---

### Post by presence1960 on 2010-02-25
> **ETW Grumpy said:**
> presence1960- I've got a Dell Dimension 2400.
 I get the splash screen...Dell BIOS Rev A05...
 Then I get Grub loading stage 1.5.
 Grub loading Error 21

 That's it. No chance to enter text or anything else. 
   Primary Master Drive is the Hard Drive
   Secondary Master Drive CD-ROM
   Secondary Slave Drive CD-ROM

Boot Sequence:
 1. IDE CD-ROM Device
 2. Hard-Disk Drive C:

 I've tried booting with the Ubuntu disk in both CD drives and it won't boot. I know the disk is good because that's what used initially for the install. I just replaced one of my CD drives in case it was bad.

 I even tried booting with an older version of Ubuntu, that didn't work.

 I tried booting with a brand new XP disc and that didn't work.

Since you just put a new optical drive in I would suspect that the problem has to do with the optical drive(s) since you have the IDE CD_ROM as first device to boot. They aren't reading the disk properly for some reason. I would open up my box and check all connections from the PSU to both optical drives and from mobo to both optical drives. Make sure all connectors are seated firmly & properly.

---

### Post by ETW Grumpy on 2010-02-25
Connections are good for both optical drives and HDD.

---

### Post by presence1960 on 2010-02-25
> **ETW Grumpy said:**
> Connections are good for both optical drives and HDD.

When you boot from the CD try F9- I believe Dell uses that to make a one time selection of which device to boot. Choose the device that has the Live CD.

---

### Post by darkod on 2010-02-25
Also I would get rid of the splash screen. In BIOS there should be setting like Show Logo or similar. Sometimes useful information is shown but this is hidden by the splash screens. I never have them on personally.

---

### Post by ETW Grumpy on 2010-02-25
presence1960- F9 didn't work, but F12 did. Chose CD, same result.

darkod- No place to turn off splash screen that I can find.

---

### Post by khelben1979 on 2010-02-26
About turning off splash screen, maybe [this]("http://ubuntuforums.org/archive/index.php/t-483264.html") can help you?

---

### Post by ETW Grumpy on 2011-01-03
> About turning off splash screen, maybe this can help you? 

khelben1979- Can't do this because I can't get the computer to boot to a command prompt.

Is there a way I can access this drive from my laptop and rewrite the MBR since I'm assuming that's where Grub resides?

---

### Post by ETW Grumpy on 2011-01-03
From the splash screen, it gives me the option to hit F2 to go to setup or F12 to go to Boot Device menu. When I hit F12, I get a list:
 
 1. Normal
 2. Hard Disk Drive C:
 3. IDE CD-ROM Device
 4. System Set Up
 5. IDE Drive Diagnostics
 6. Boot to Utility Partition

4 takes me to the BIOS, 5 does a diagnostic that tells me the cd roms don't support the diagnostic and everything else gives me the Grub error.

---

