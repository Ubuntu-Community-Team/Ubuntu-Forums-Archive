---
title: "Installing Ubuntu Over Freespire via USB Drive"
date: 2011-02-18
forum: Installation &amp; Upgrades
---

### Post by Morluna on 2011-02-18
Hi guys, 

I'm relatively new to Linux, so when I was given a copy of Freespire I decided to install it on my Windows laptop. After installing Freespire (which works fine, no problems with the OS) I did some reading on several Linux forums and determined that I might be better off running Ubuntu instead. (Should have done this reading before installing anything, I guess...) In any case, I just want to wipe everything on the hard drive, and start over with Ubuntu.

So on a different Windows-based computer, I downloaded Ubuntu 10.10 and created an image file on a USB drive, as directed by the Ubuntu download page. 

However, when I plug the USB drive into my now Freespire-based laptop, an icon for the USB drive shows up on my desktop, but I can't figure out how to run the installation. When I click on the icon for the USB drive, I just get lots of directories with files inside... but I can't figure out how to run any installation. I'm thinking maybe this installation method is only set up for Windows? But, I'm not sure and I can't find any information on this specific problem anywhere.

Note: I can't access the Internet via the Freespire laptop, so I have to install via USB or CD. Unless someone can help me with setting up a wireless network in Freespire, but that's a separate issue and, seeing as I want to simply replace the entire OS... not really a problem I want to deal with unless it's the only way to install Ubuntu.

If anyone can shed some light on this problem for a newbie, I would really appreciate it. Thanks!

---

### Post by vacco on 2011-02-18
You have to boot from the USB stick. Just plug it in before you start your computer.

Make sure your BIOS is set to boot from USB before Hard Drive.
To access the BIOS, press F2, ESC, or something while you see the splash screen right after powering on the computer (which button to press vary by manufacturer). There is usually a tab called boot where you can change boot order. If there is no USB option (typical for old hardware), your computer probably does not support booting from USB.

If your computer does not support booting from USB, you have to burn a CD. If you are unable to change the boot order of your computer, there is also a greater chance your computer is already configured to boot from CD than there is from USB (especially if you have already installed Freesbie from a CD).

---

