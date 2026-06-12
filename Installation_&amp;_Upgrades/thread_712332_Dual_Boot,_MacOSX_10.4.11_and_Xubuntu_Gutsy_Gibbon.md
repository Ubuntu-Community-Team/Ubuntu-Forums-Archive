---
title: "Dual Boot, MacOSX 10.4.11 and Xubuntu Gutsy Gibbon"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by sexlax8769 on 2008-03-01
Ok so I downloaded the iso file for Xubuntu Gutsy Gibbon.  I burned it to a cd.  I have the cd in and reboot my Mac (iBook G4) and when it begins to reload I press and hold C.  All that happens is a Earth symbol flashes.. then a folder with the finder logo flashes with a question mark...  and i have already partitoned my drive... i need help!

---

### Post by dstew on 2008-03-01
It sounds like the CD is not bootable. How did you get the CD? Did you make it yourself? Did you burn it as an image, and not as a file? And, you got the PowerPC version, right?

---

### Post by sexlax8769 on 2008-03-01
I downloaded the file xubuntu-7.10-desktop-powerpc.iso    I then burned this to a cd.  Then i tried the restart load from cd thing.  The picture I attached is the screenshot of the disk i burned.

---

### Post by iThinkergoiMac on 2008-03-02
What did you use to burn the CD? If you used the Finder, that may be your problem. Try using a different app to burn the CD (I recommend [Burn]("http://www.versiontracker.com/dyn/moreinfo/macosx/30120")). Let me know if that doesn't work. I agree that it sounds mainly like your CD isn't bootable, as the flashing folder/question mark icon means it can't find a system folder or bootable system.

---

### Post by iThinkergoiMac on 2008-03-02
> **sexlax8769 said:**
> I downloaded the file xubuntu-7.10-desktop-powerpc.iso    I then burned this to a cd.  Then i tried the restart load from cd thing.  The picture I attached is the screenshot of the disk i burned.

Ohhhh... yeah, I see. Here's your problem: you burned the iso file to a CD. An .iso file is a disk image (just like .dmg). So you don't want to burn the file itself to a CD... that doesn't really get you anywhere. Download and install Burn (from my last reply) and use it to open the .iso file and burn it to a CD. The option should be something like "Copy Disk Image to CD" or something along those lines.

That should fix it... let me know if you can't find what I'm talking about!

---

### Post by sexlax8769 on 2008-03-02
OK thanks for that app it worked... sort of, ok so i burned it to the cd.  Rebooted with the cd it went through the first stages of loading it went to where i have to press enter and it types live on the screen, then it went through one more screen of text (i think it said detecting display) then it all went black and that was it, it didnt do anything. i tried again, same result.. pressed all kinds of buttons... but nothin.. :(   :confused:

---

### Post by iThinkergoiMac on 2008-03-02
> **sexlax8769 said:**
> OK thanks for that app it worked... sort of, ok so i burned it to the cd.  Rebooted with the cd it went through the first stages of loading it went to where i have to press enter and it types live on the screen, then it went through one more screen of text (i think it said detecting display) then it all went black and that was it, it didnt do anything. i tried again, same result.. pressed all kinds of buttons... but nothin.. :(   :confused:

What are the specs on your iBook?

(This is all very interesting for me because my family has an iBook G4. I would attempt booting it off the CD if I wasn't going back to college (6 hrs away) today.)

---

### Post by dstew on 2008-03-02
This usually means the Live CD is having trouble with your video. At the opening screen of a live CD boot, there is a chance to enter "help" or something like that (trying to remember the PPC version) and you can try some different boot options. There is one that is video=ofonly. If the boot options don't work there is another thing to try. Let me know.

---

### Post by sexlax8769 on 2008-03-02
Ok so i chose the video=ofonly route.  It loaded no problem.  After it all loaded I double clicked install and ran the installation.  It completed the installation with no error messages whatsoever.  However I restarted my computer and when i did it spat out the cd and froze on the Xubuntu desktop background... i had to hold down the power button to shut it down, upon turning it back on it loaded into mac osx and i can find no signs of xubuntu anywhere....

---

### Post by dstew on 2008-03-03
It is possible you did not install yaboot. You can see if you can boot the Ubuntu partition using the Mac boot options. Hold down the Option key when first booting, you get a little graphical menu. See if you can boot Ubuntu from there. If no, you will probably need to install yaboot. You also might have to create a newworld partiton to boot from.

---

### Post by sexlax8769 on 2008-03-03
Ok so I tried the option function but it didnt work... So where can i download yaboot and how do i install it?

---

### Post by dstew on 2008-03-04
It is part of the installation process, near the end. I skipped it the first time I did a PowerPC install. I think the first clue comes when you are in the partitioner. I remember a warning message that I did not have a newworld partition, but I just ignored it. Then, I think the installer skipped the Yaboot install, because there was not newworld partition. 

Install again, and look carefully for the newworld partition message. I think you create a small partition of this type, about 15 Mb if I remember correctly. If you create that partition, then you get the option to install Yaboot at the end of the installation process.

---

