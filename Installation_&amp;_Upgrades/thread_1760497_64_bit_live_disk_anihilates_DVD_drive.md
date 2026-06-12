---
title: "64 bit live disk anihilates DVD drive"
date: 2011-05-17
forum: Installation &amp; Upgrades
---

### Post by incognito on 2011-05-17
[SOLVD (tl-dr version): <Ctrl-Alt-Delete> was used to exit out of a recognized initramfs boot error using an md5sum-checked 64 bit 11.04 ubuntu.com iso disk. The OEM hp BIOS then did not recognize the now also locked DVD drive on restarting the computer. Performing a SystemRestore reactivates the DVD drive allowing the disk to be ejected as the BIOS loads by pressing the DVD drive's eject button. The DVD drive then again appears in the BIOS and under My Computer in Windows 7. Using Linux Mint Debian also results in a live-initramfs error but does not harm the drive. Exit again does not work, but <Ctrl-Alt-Delete does nothing...]

A warning to all.

I was eagerly waiting to test linux on my new HP s5560f. I downloaded, burned and checked the 64 bit iso from the ubuntu site. I then restart the computer with the disk in. After the bios runs there is a brief flash of a screen with isolinux... at the top, then a screen with the ubuntu name over a flashing progress bar, and then a busybox splash with a prompt. Nothing happens save for the help command working. I then hit Ctrl-Alt-Delete. OEM Windows 7 starts but my BluRay/DVD drive is no more-- not in BIOS, my computer, nada. Pressing the open door button does nothing. Best bet from the hp forums is to open the case, unplug the drive, reboot, plug in the drive and hope it works. If not, you lose your computer to warranty that may or may not do anything about it. Regardless, hours shot.

On searching the forum and buglists this type of error has been reported before since Lucid (?). This is not the Ubuntu that I had loved; this is a menace. User beware...

---

### Post by tgm4883 on 2011-05-17
> **incognito said:**
> A warning to all.

I was eagerly waiting to test linux on my new HP s5560f. I downloaded, burned and checked the 64 bit iso from the ubuntu site. I then restart the computer with the disk in. After the bios runs there is a brief flash of a screen with isolinux... at the top, then a screen with the ubuntu name over a flashing progress bar, and then a busybox splash with a prompt. Nothing happens save for the help command working. I then hit Ctrl-Alt-Delete. OEM Windows 7 starts but my BluRay/DVD drive is no more-- not in BIOS, my computer, nada. Pressing the open door button does nothing. Best bet from the hp forums is to open the case, unplug the drive, reboot, plug in the drive and hope it works. If not, you lose your computer to warranty that may or may not do anything about it. Regardless, hours shot.

On searching the forum and buglists this type of error has been reported before since Lucid (?). This is not the Ubuntu that I had loved; this is a menace. User beware...

That doesn't make any sense. Post the bugs, this is something I'd like to see.

---

### Post by incognito on 2011-05-17
A couple minutes with google and searching the forums yields the following:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/626622](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/626622)
[http://ubuntuforums.org/showthread.php?t=879993](http://ubuntuforums.org/showthread.php?t=879993)
[http://ubuntuforums.org/showthread.php?t=660715](http://ubuntuforums.org/showthread.php?t=660715)
[http://ubuntuforums.org/showthread.php?t=1451366](http://ubuntuforums.org/showthread.php?t=1451366)
[http://fossplanet.com/f10/%5Bbug-625143%5D-re-live-cd-does-not-boot-up-gives-error-message-139825/](http://fossplanet.com/f10/%5Bbug-625143%5D-re-live-cd-does-not-boot-up-gives-error-message-139825/)
[http://fossplanet.com/f10/%5Bbug-774349%5D-%5Bnew%5D-natty-11-04-64bit-live-cd-wont-boot-147221/](http://fossplanet.com/f10/%5Bbug-774349%5D-%5Bnew%5D-natty-11-04-64bit-live-cd-wont-boot-147221/)
[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/754130](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/754130)
[https://bugs.launchpad.net/ubuntu/+bug/774349](https://bugs.launchpad.net/ubuntu/+bug/774349)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/774419](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/774419)
[http://ubuntuforums.org/showthread.php?t=1737048](http://ubuntuforums.org/showthread.php?t=1737048)
[http://ubuntuforums.org/showthread.php?t=1753855](http://ubuntuforums.org/showthread.php?t=1753855)

---

### Post by Quackers on 2011-05-17
Hmm, I see BusyBox prompts, post-install booting problems, nomodeset boot options, but nothing about losing a dvd drive.

Did I miss something?

---

### Post by incognito on 2011-05-17
No, the DVD drive is a new complication on top of the rest that seem to be a recurring problem.

---

### Post by Quackers on 2011-05-17
I see. But the title of your thread seems to blame Ubuntu's 64 bit live cd for destroying your dvd drive! That definitely seems to be your main point, I would say.
That's like saying you played a Britney Spears cd and the cd drive stopped working, so you blame Britney Spears. :-)

So you are asking about the BusyBox problem then.
Did you check the md5sum of the downloaded iso file?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by incognito on 2011-05-17
Yes, I did an md5sum.

In short the initramfs error, or events leading up to it, on my system appears to have caused the drive to be removed from the bios configuration and so too from Windows 7.

Whilst figuring out how to make the drive barf out the Ubuntu CD someone suggested doing a SystemRestore. This returned the DVD drive to bootable status launching the above sequence yet once again on automatic reboot from SystemRestore. From the busy box ash shell line with a initramfs error exit did not work or the suggested init=bootarg. A hard reboot and pressing the eject button barfs out the disk (now coaster) with BIOS and Windows 7 now recognizing the dvd drive again.

I am pretty sure that an audio CD would not unmount/disable a DVD drive. I am pretty sure that as noted in some of the bug posts that BSOD-like errors are sure to deter everyone one from noobs to hardware-loving/hassle-avoiding admins from Ubuntu. I will mark this thread solved and edit a TL;DR on top of my first post. There seems to be no workaround so I will try the Mint Debian release as a replacement for now.

---

### Post by Quackers on 2011-05-17
Have you tried to play an audio cd or a movie on dvd? What happens?
I would suggest it is much more likely to be a software/driver/hardware problem rather than the contents of a dvd causing the drive to disappear from your system.

As for the BusyBox/initramfs prompt, there could be several causes.

---

### Post by incognito on 2011-05-17
Once the Ubuntu disk was barfed out the drive is again functioning (see my last post and the SOLVD tl;dr summary added on top of the original for details).

---

### Post by tgm4883 on 2011-05-17
You didn't mark your thread as solved. And I don't see how any of that would disable your DVD drive.

---

### Post by incognito on 2011-05-20
Hi:

tl-dr: I did mark the thread as solved with the original post edited with a fix for getting the DVD drive back. I have learned that openSUSE 11.4 does not generate this error maybe because they use dracut not initramfs.

Details:

The same live-initramfs occurred with the Mint LMDE disk. Fedora 15 beta just seizes up. Google results say this type of error seems common since 2008-2009 with various causes particularly on Debian and its derivatives. For my hp chipset some have had luck changing to the RAID drive configuration in BIOS or changing hp specific graphic settings in BIOS. 

From the Ubuntu initramfs man page I emailed the listed contact, a Debian initramfs maintainer. He suggested contacting those running the not-debian error generating distros. Catch 22.

I was going to struggle through this, but I just picked up the current Linux Pro Magazine with an openSUSE 11.4 dvd-- live boot no problem. Google informed me that SUSE had substituted dracut for initramfs years ago. Google also had no mention of busybox initramfs or dracut start up errors on SUSE. I do not have hours to waste trying to figure out complex start up errors. To whom do the developers think this will appeal? Sadly, I am looking at being a small lizard rather than a meekrat.

---

