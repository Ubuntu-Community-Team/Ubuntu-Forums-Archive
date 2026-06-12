---
title: "Unable to install from iso"
date: 2012-10-13
forum: Installation &amp; Upgrades
---

### Post by mavazz on 2012-10-13
Hello, 

I have a long story I'd like to tell which may offer some clues as to why I'm having these problems.

I recently bought a new computer from System76. They come pre-installed with Ubuntu. I've been running Ubuntu for 3 years now and don't have any need for Windows.

When the computer arrived Ubuntu started up no problem. But before I migrated all of my important documents from my backup of my old computer I decided to try another Linux Distro.

I downloaded Linux Mint 64 bit. Seeing as how I have a brand new computer I figured it could handle 64 Bit. As of now I still don't know if that caused any sort of problem. Anywho, I downloaded LinuxMint 64 bit and attempted to install it from a USB pendrive. To be clear, I followed the instructions and converted the iso using the startup disk creator. I've done this many times before so I'm not new to it. I will say, however, that I've always had more luck with CD's than USB drives.

Anyways, Linux Mint didn't even get the installer running. So, I decided to download the alternate installer for Ubuntu so that I could get FDE set up. I downloaded it, converted it for USB installation and the installation part was up and running without problems. 

I meticulously followed the instructions I read online for setting up FDE. I finished the installation process, rebooted, but then things froze at an error. It was something to do with no video detected. But everything I read online said that it was a common error. However, for everybody else the error would last about 10 seconds, then proceed to boot up. It was an error that was supposedly easing fixed by giving some commands in the terminal. But I could never reach the terminal. 

Anywho, after much frustration and several attempts to reinstall the alternate installer, including no partitioning or encryption, things continued to fail. I've even tried installing the normal install for Ubuntu but the installer won't even load for me. Yes, I've got the USB to boot before the hard disk, etc.

So, right now I can't get any distros to install except the alternate installer, but after installation it refuses to boot properly. 

I've also attempted to install 32 bit. None of those work as well. 

Sadly, when I bought the new computer I opted not to have it built with a dvd drive because I really thought I didn't need it. I've attempted to migrate my dvd burner from my old machine to the new one. Sadly, the new motherboard is incompatible with the much older dvd burner. Or perhaps it is compatible and I just need to go buy the right cables. Either way, that's another hassle I have to worry about.

I've done some reading online and I think I read something about SanDisk USB pendrives causing problems for disk images. That seems totally ridiculous to me, but in the three years I've been running Ubuntu, the USB drives have definitely caused me much more headache than CD drives when it comes to installation. 

Do I need to worry about the SanDisk causing me problems or is that a red herring? 

Do I really need to stop attempting to install Linux from a USB drive and get my DVD drive installed ASAP?

Have I irreparably hashed my hard disk with partitioning and encryption? 

Can't I just start from scratch with a brand new installation?

Any help would be much appreciated!

---

### Post by houseworkshy on 2012-10-13
[http://acronyms.thefreedictionary.com/FDE](http://acronyms.thefreedictionary.com/FDE)
Full disk encription?
Whilst I don't know what has happened I do know of something which may help diagnose and sort out the booting; UbuntuSecureRemix. It has some handy tools which can be used in a diagnostic way and/or to actully fix things.  It also includes an installation of Ubuntu in the image.  
A useful tool to have in the rack anyway so worth a burn, meaning yeah cd/dvd burners are frail things but it is better to have one and they are getting cheaper.  Like mice most boxes will go through several before the box itself fails.  Good to have write once only media for backups amd emergancies.  I've had to resort to live distro and stick when the hd software needs fixing but I don't have time and do have a deadline to meet which needs the computer to do it on.    Also a handy quick way of testing the hardware before diving into software problems which may not exist.  Not quite an essential but a very useful bit of hardware.  A cd/dvd burner should be less than £20.00 which is far cheaper than a dedicated dvd/cd player anyway.  
Meanwhile you could try the UbuntuSecureRemix from the stick
.[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)
 The tool which is pertinant to your problem is called boot-repair.
There are also net installs, I've never done one so can't advise on that so you'd need to read up.  
If you remember your old name and password, assuming default encryption at installation, you should be able to decrypt the drive as long as you haven't formated over it.  Edit after re-reading, if there is no data on the drive that matters you can just wipe the lot and start fresh once you've got a sucessful boot.

---

### Post by mavazz on 2012-10-13
Upon further inspection, it appears it may not be my fault.

If anybody can help me to bypass these known problems it would be a great help!

[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/992496](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/992496)

[http://ubuntuforums.org/showthread.php?t=1743975](http://ubuntuforums.org/showthread.php?t=1743975)

---

### Post by houseworkshy on 2012-10-13
First reported on the first of May this year but also affected the 11.04 edition.  That is one old bug.  
Well 10.04 lts is still supported untill April next year so you could try that,  and the 10.04lts servor edition is still supported for an additional two years after that.
It's a good version.

---

### Post by Lyfang on 2012-10-13
Are you using Ubuntu Live USB creator or UNetbootin?

---

