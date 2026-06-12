---
title: "Fresh Install of 11.10 Won't Boot..."
date: 2012-02-19
forum: Installation &amp; Upgrades
---

### Post by dwtsend on 2012-02-19
Greetings all,

I should start by saying that this is my absolute first experience with Linux and Ubuntu, so if you are making any suggestions for me, I kindly ask that you explain things in very simple terms and let me know exactly where I need to go to type something in.

First off, the specs:

Motherboard: ASUS A8N-SLI Deluxe
CPU : AMD 64 2.2GHz
Video Card: Nvidia Geforce 7 series, 256MB
Ram: 2GB
HDD: 1 x WD 36GB(SATA Master), 1 x WD 40GB(IDE Master)

I am attempting to install 11.10 32 bit.

My experience:

I made my first installation when I had Windows XP on the machine.  From the install menu, I chose delete everything and install Ubuntu (because this was an old box, and I didn't care about the installation).  I installed it on the 36GB drive (the same one that the XP installation was on).  The installer set everything up and I was on my way.  On the first reboot after the fresh install, I got hung on a purple screen.  No biggie.  I hit reset and tried again.  This time, I got the GRUB menu and I noticed that my XP install was still on the list.  I didn't think much of it because I thought that perhaps it had to get into Linux to finalize the format.  I selected Ubuntu, and this time I got hung on a black screen with a blinking cursor.  Every subsequent restart left me hanging on a black screen with a blinking cursor.  I repeated this exact same process attempting to install on my 40GB drive and the same thing is happening.  Install goes fine and I reboot.  The first reboot after the install gives me the purple screen, and every subsequent restart (selecting Ubuntu from the GRUB menu) gives me the black screen with the blinking cursor.

I've done a lot of internet reading, and here are all the things I have tried with their results:

**Checking install ISO with MD5sum:** I have checked my install iso and the hashes compare OK.

**Booting in Recovery Mode:** When I select recovery mode from the GRUB menu, I get the spam of computer text (similar to booting in safe mode like windows).  However, the text stops and the last thing of significance that it lists is "Failed to execute /init" followed by "Kernel panic - not syncing: no init found".  I'm pretty sure that this is the significant item, however I haven't found any decently explained help on how to go about fixing it, or what is causing it.

**Entering GRUB and modifying parameters:** I have gone into the grub menu and in the line with "quiet" and "splash" I have attempted following them with the "noapic" parameter, as well as replacing with "xforcevesa" and "text nomodeset".  Upon hitting CTRL+X to boot, all options result in the black screen with the blinking cursor.

**Removing second video card:** Originally my system was running SLI Nvidia cards.  After reading a suggestion that Ubuntu has difficulties with multiple video chips, I removed a card.  I have since tried several times with the same black screen and blinking cursor.

If there is another post about this topic that has covered a fix that I have not tried, then I apologize for the redundancy.  However, after 2 days of dedicated searching and reading, I'm not quite sure that there's a solution phrased the way that I need it.  What works for some doesn't always work for others, and I seem to be the "other".  I sincerely appreciate any help that you guys can offer, and once again I wanted to remind you to talk slow because, while I understand computers very well (I'm actually majoring in programming) I don't yet understand the proprietary lingo for a Linux system.  Thanks again, and looking forward to learning more about Linux.

~Dave

*EDIT* Update:  After having poked around and finding [this thread]("http://ubuntuforums.org/showthread.php?t=1743535&highlight=kernel+Panic+init+found"), I made it to step 2 where I altered the boot options in GRUB.  After adding the "nosplash --verbose text" items to the boot line, it was showing me the same text that I get in recovery mode, mentioning the lack of init and the kernel panic and what not.  I think this section is going to be the key for getting this fixed.  Looking forward to someone who can help me out!

---

