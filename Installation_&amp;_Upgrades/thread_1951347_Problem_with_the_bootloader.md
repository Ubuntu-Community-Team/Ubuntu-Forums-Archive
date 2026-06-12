---
title: "Problem with the bootloader"
date: 2012-04-02
forum: Installation &amp; Upgrades
---

### Post by egimon on 2012-04-02
Ok, so here's my problem. There is this pc I need do fix, it's some kind of old Fujitsu Siemens laptop, and I was going to install Ubuntu v. 11.10, instead of Windows XP (of which, apparently was the former os). As I soon found, the boot loader was missing, so I couldn't install ubuntu (or any other linux) from a disc. I also found out that the owner of this computer had changed his hard drive.

How can I fix this?




Ps. As I hope you've already understood, I do not have the XP discs

---

### Post by critin on 2012-04-02
You should be able to boot a live iso cd if you can find the boot key when pc is first turned on.  Can you get into bios to change boot order to cd first?

---

### Post by egimon on 2012-04-02
Well... When I put in the discs, I go to the BIOS and choose to boot the cd, the trouble is that after I've done that it just says "bootmgr missing". However, I was just able to boot Norton Recovery Tool (useless), and "DSL-linux", and they were somehow selfbooting. What to do???

---

### Post by oldfred on 2012-04-02
If other CDs boot then you may not have burned Ubuntu liveCD correctly. If CD does not boot then it goes to next in BIOS boot list, usually hard drive. 

The Bootmgr missing error is from Windows in the hard drive MBR not finding a Windows partition with the windows boot files including Bootmgr.

You want to burn at slowest speed CD allows. I now use USB flash drives as my computers allow boot from USB but some also have issues with some types of flash drives.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by egimon on 2012-04-02
In short, I can access BIOS

---

### Post by egimon on 2012-04-02
I can burn one more then, but I am using the Windows 7 Disc Image Burner

---

### Post by egimon on 2012-04-02
I've tried various linux versions, and just two will actually boot, it's the "tiny linux", "PLAQ", and the windows-based Norton Bootable

---

### Post by egimon on 2012-04-02
I just checked the Ubuntu.iso, and it's all right.

---

### Post by egimon on 2012-04-02
Is it possible that I can install Ubuntu through the DSL - Tiny linux thing? And if so, do I have to install the DSL first?

---

### Post by oldfred on 2012-04-02
You say it is an older system. What are the specs? Perhaps it does not meet the minimums, so the smaller systems you have tried work but not the full Ubuntu?

You might try Lubuntu or some of the other lightweight systems if that is the issue.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by egimon on 2012-04-02
It's a Fujitsu Siemens AMILOPro V2055
It has 'round 1 GB RAM
Newly installed 320 GB Hard Drive
1,2 GHz intel Celeron M

---

### Post by oldfred on 2012-04-02
Is it perhaps a graphic issue. If you press any key just as CD loads this screen do you get to a menu? Then try f6 and nomodeset although sometimes other options may be required.

---

### Post by egimon on 2012-04-02
Well, nothing happens, and it skips right to the harddrive boot, where the error says "BOOTMGR" missing. I don't think it's a spec's issue... One more thing is that if I am going to use the only linux that works with that computer, I have trouble making it read the hard drive /finding the right place to install... Any more ideas??? 

Thanks in advance!

---

### Post by egimon on 2012-04-02
I might have one more theory, the only discs that worked were printed on dvds (all of the dvds), while the cds i've tried doesn't seem to work. Could this might be the cause, although it has a DVD/CD-rom reader?

---

### Post by oldfred on 2012-04-02
Some have had issues with DVDs when CDs worked. And I think some have had issues with certain brands of CDs. 

Years ago I had issues with one computer's CD drive. It would only read CDs it created not any from any other computer. 

Will computer boot USB flash drives? It may be too old? It seems about 2005 or 2006, most BIOS we updated to boot flash drives or USB devices.

---

### Post by egimon on 2012-04-02
Well, one of the the boot options is USB Storage Disk (I googled it, but it seems to be an outdated term=)... I've tried it earlier today, but I'd might just give it one more go.

---

### Post by egimon on 2012-04-02
Doesn't work, I'll try to find some other discs then

---

### Post by oldfred on 2012-04-02
My portable boots flash drive without issue. But desktop has many USB choices and it was only by coincidence I found the USB flash drive is not a USB device but just another hard drive under hard drives to boot.

I also had issues if I have more than one flash plugged in. Only the bootable one should be in and plugged in as you power up so BIOS can find it.

---

### Post by egimon on 2012-04-02
It doesn't even detect it, even if i remove the hard drive, any clues?

---

### Post by oldfred on 2012-04-02
I have not used it, but some report this works. But I think you have to have some CD working to do initial load.

Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

Some have just pulled the hard drive and plugged it into another computer to install.

---

### Post by critin on 2012-04-02
> **egimon said:**
> Is it possible that I can install Ubuntu through the DSL - Tiny linux thing? And if so, do I have to install the DSL first?

If DSL boots it should install.  Sure, they say they are good systems so you may not want to install ubuntu.  At any rate, once you get an OS on there, you can always install another either over or beside it.

---

### Post by egimon on 2012-04-02
Well this is indeed frustrating...

---

### Post by egimon on 2012-04-02
To sum up my problem right now; USB Memory Sticks does'nt seem to work, my only empty discs doesn't seem to work with the disc reader, the only two funtioning bootable discs are one with the useless "PLAQ", not doing anything other than loading the kernel (not even an interface), and the DSI Linux. 

The DSI Linux loads, and I get into the desktop, however installing the thing seems to be difficult. Any ideas from that?

---

### Post by critin on 2012-04-02
I believe DSL has some good Help tips on the DSL live desktop.  Try to find it and it should tell you how to install.

---

### Post by egimon on 2012-04-03
My first problem is that DSL only uses bash codes, and I can't find the harddrive through DSL at all, so the installer doesn't work. In addition to all of this; I can't find any empty dvds to use... 
This will be my last attempt at fixing this pc, any more clues, or hints? 

Thx

---

