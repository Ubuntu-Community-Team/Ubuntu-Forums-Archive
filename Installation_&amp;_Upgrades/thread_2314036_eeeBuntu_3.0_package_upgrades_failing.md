---
title: "eeeBuntu 3.0: package upgrades failing"
date: 2016-02-17
forum: Installation &amp; Upgrades
---

### Post by mlevin77 on 2016-02-17
I've just fired up an Asus notebook with eeeBuntu 3.0 on it. I haven't used it in a couple of years. At this point all I want is to run the latest version of Skype on it. When I tried to install Skype manually from a .deb file, it told me that one of the dependencies couldn't be found, so I figured I'd update everything. When I use the package manager to update all packages (which used to work fine), it fails with a bunch of errors. Attached is a screenshot of what I see - can anyone tell me how to get this back to being able to update all my stuff?

---

### Post by MAFoElffen on 2016-02-17
That OS was based on Ubuntu Jaunty 9.04. It was released 2009 by eeeBuntu.org, which then re-orged shortly after that as AuroraOS, which then died and went away. What you are running hasn't had any support since late 2009. The site and repo's went away back in 2010.

Recommendation? There is no clean upgrade path from 9.04 to current... especially from eeebuntu.

If you backed up your data onto a thumbdrive... You could do a fresh install of an Ubuntu flavor. Then copy your data over to it. Depending if you have the 900 or 1000 model and how much memory you have, and your personal preferences would determine which branch might be best for you.

---

### Post by mlevin77 on 2016-02-18
I see. Is there any path to getting the latest Skype working on this thing? That's really all I want. Otherwise, what's the easiest way to install a new branch on this device? I used to remember but no longer do.

---

### Post by ajgreeny on 2016-02-18
If you want a *Ubuntu based OS on that machine I suspect that Lubuntu 14.04 will be your best choice, but it does depend on the exact hardware it has.

Go to [http://cdimages.ubuntu.com/lubuntu/releases/trusty/release/](http://cdimages.ubuntu.com/lubuntu/releases/trusty/release/) and download the appropriate architecture version, probably the 32 bit.

You will see there are four numbered versions of the **lubuntu-14.04-desktop-i386.iso**, 14.04, 14.04.1, 14.04.2 and 14.04.3 which are basically the same but use different series of kernel and xorg graphics.  I suggest you stick with the 14.04.1 version as it will not require major upgrades of kernel and xorg, but the later versions will do as their kernel and xorg support ends.  Don't worry about this detail; just go for the 14.04.1 version and as long as the machine will boot from a USB memory stick you should be fine.

Come back for more detail on installing if you need to, or read [http://ubuntuforums.org/showthread.php?t=2230389](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by mlevin77 on 2016-02-18
Hmm, so I made a thumbdrive of 10.04.1 using unetbootin but the Asus doesn't see it in the list of things to boot, in the boot screen. Any idea how to make it recognize it?

---

### Post by ajgreeny on 2016-02-18
Ubuntu 10.04.1(or any other *ubuntus of that numbered version) are no use to you as they are all out of support and you will not be able to use it safely, not install anything from the repositories. Try 14.04.1 as I suggested.

AS for the ability to boot to a live USB, you should find info in any manual you have for the machine, but it is usually arrived at by either setting it in the BIOS, or by pressing a key at boot-up/power-on, eg F8, F11.

---

### Post by mlevin77 on 2016-02-18
Sorry, that was a typo in my last post, I did indeed use 14.04.1 from the link you gave.  And I do know how to get to the boot-up screen, which lists a variety of OS's to boot from (snapshots of my current system), but it doesn't seem to see the USB stick. I got into the BIOS setup and all I see is "priority" settings for the internal disk vs. CDROM (which I don't have) vs. external device (presumably USB flashdrives). But the flashdrive I put in doesn't seem to appear on the list of boot options when it gets to that.

---

### Post by ajgreeny on 2016-02-18
Is the list of devices to boot missing the USB drive even if it is inserted before you power up?
Did you transfer the ISO file as an image to the USB and not simply copy it to the drive?
How did you create the USB boot drive; what application did you use?

---

### Post by mlevin77 on 2016-02-18
> Is the list of devices to boot missing the USB drive even if it is inserted before you power up?

  yes, although I didn't try a coldboot - I just turned it off and on; it may have preserved state somehow?

> Did you transfer the ISO file as an image to the USB and not simply copy it to the drive?
> How did you create the USB boot drive; what application did you use?

    yep; I used an application called Unetbootin, on a Mac, using the ISO as source.

---

