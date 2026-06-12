---
title: "Graphical problem (?) during and after installation of Ubuntu 10.10"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by jbyram on 2010-10-31
Let me provide some hardware info first, just in case my problem is tied to it:

Motherboard: Asus A8N-SLI Premium nForce 4 SLI
CPU: AMD Athlon 64 X2 4400
RAM: 2 GB OCZ DDR400
Videocard: BFG GeForce 7800 GT 256MB
HDD: Maxtor DiamondMax 10 6L200S0
Optical Drive: Lite-On 16x DVD+/-R Burner Model SOHW-16935
NIC: Linksys WMP54G v4.1

The machine listed above, I've had sitting around for a while, so I decided to go ahead and make it a "full-time" Linux machine (I've dabbled with various distros in the past, but nothing ever serious); I decided to go with Ubuntu 10.10 32-bit. 

After downloading the ISO from here, I burned it to a CD-R, changed BIOS settings, and popped it in to load. It starts to load up fine, but when it gets to the splash screen, it just freezes - the screen I get is a grey, striped, static-looking screen. After trying to reboot a few times, I think that either the ISO or the CD is bad, so to make sure, I pop the CD into 2 other (newer) computers to see what happens. The CD works perfectly, loading up properly and going straight to the screen that gives me the option to try Ubuntu before installing or to install right away. Just in case, I decide to try a USB boot. I used Universal USB Installer, change BIOS settings, stick the USB drive into the computer, and I get the same result as with the CD. Again, I plug the USB drive into the other 2 computers, and it loads just fine.

Thinking maybe, for some odd reason, it might have to do with me using a 32-bit version on a 64-bit machine (I'm trying to eliminate all possible issues), I download the 64-bit version. Again, I try to install via a CD-R and a USB drive, and I get the same thing.

I then try to bypass the splash screen, so I hit ESC while it's loading and I get the main menu. Under MODES (F4), I don't see "Safe graphics mode" option, so that's out. For the fun of it, I select the option try Ubuntu without changing anything to my computer. Again, it locks up with the same screen.

Finally, I download the 64-bit alternative install image from here (one of the mirrors). I'm actually able to do a text-based installation of Ubuntu with it, but when the installation finishes and I reboot my computer, once again at the splash screen, it locks up. I've tried hitting ESC and F1-F6 while it's loading to get ANYTHING other than the splash screen, but nothing. In fact, I don't even get an option to change my boot configuration or anything.

Two side notes concerning this problem:

-First, as I mentioned above, I've dabbled with various older distros on this same machine. In the past, I've used and installed Ubuntu, Mint, and Fedora, and haven't had this problem, so for this to happen now is a bit mind-boggling. 

-Second, I'm having this exact problem with Mint 10 32-bit, Fedora 13 32-bit, and OpenSuse 11.3 64-bit. The EXACT problem.

So yeah, I'm lost on what to do from here. If I've left out anything that might be of help, let me know; I've played around with Linux, but I'm still fairly new to it, so it wouldn't surprise me if I've missed something or overlooked something. Any help on this would be greatly appreciated (I really think that something concerning my hardware has decided to not play nice with these newer versions of these distros, since older ones installed fine).

---

### Post by stingray69 on 2010-11-01
I'm having a similar experience with Mint 10RC and Ubuntu 10.x. I don't know how our problems might be related since I'm using a Dell laptop with ATI graphics but the symptoms are nearly identical.

Try the suggestions in [this thread (starting on page 2)](http://ubuntuforums.org/showthread.php?t=1461029&page=2). You might find something that works. Holding both shift keys while booting (after the BIOS screen) brings up the grub menu and allows you to edit.

I also found that using the nomodeset option with the live CD helps (either hit F6 and select nomodeset or delete "quiet splash" and type "nomodeset" for the boot options). This allowed me to boot the Mint 10RC LiveCD but upon install I encounter the same grey/black stripey screen you described. Unfortunately this doesn't completely fix the issue with the Ubuntu 10.10 CD for me. I only got the stripes on 3/4 of the screen but the whole display blinked with the cursor and no windows or icons are visible. After failure with Ubuntu 10.10 I went back to 10.04 to see if I could just upgrade to 10.10. Using nomodeset I was able to install and run 10.04 perfectly but when I upgraded to 10.10 and restarted I got a white screen instead of the splash. I can tell ubuntu is loading and running because I get the ubuntu sound for the login screen and I can type my password and then get the ubuntu welcome sound but I can't see anything.

I don't mean to hijack your thread (I'm still trying to fix this) but I hope this helps.

---

### Post by jbyram on 2010-11-01
So, a quick update to this problem...

After rebooting many times, I somehow managed to access to GRUB Bootloader menu(?) (I think that in my impatience, I rebooted while Ubuntu was trying to load -- that's the only way I've been able to replicate the results of getting the GRUB menu to actually appear). From here, I entered "Recovery Mode," which after selecting a few options, I was able to get to the login screen and log into my desktop. From here, I was able to set up my network connection and download an NVidia driver. After installing and rebooting, the screen doesn't freeze up at the splash page, and sends me directly to the login screen.

Sooo...clearly, the issue was that I needed a graphics driver installed, but this still leaves a problem/question on my end. In both the graphical installation and the text-based installation, I don't remember seeing anything that would have allowed me to go out and download/install drivers for my graphics card. 

Now, I don't know if this *is* the workaround for this, but essentially I had to enter via a "safe mode" just to download drivers for my graphics card just to get the splash page and login screen to appear properly; there has to be a "correct" way to get this to work, right? Having looked at dozens of Linux magazines, it's always been suggested that with the more "friendly" distros like Ubuntu, you just drop the CD into the drive, boot up, and go. I could understand if I was using some really old hardware, but the parts in my machine are all on the Linux compatibility list. Also, as I mentioned earlier, I've installed older versions of Ubuntu (I believe 8.04) and Mint (which is based on Ubuntu, right) on this same machine, and everything went smooth and worked right out of the box. There hasn't been some hardware support dropped from the newest Linux kernels since I last used a distro, has there?

Again, any explanation would be great. Thanks!

---

### Post by jbyram on 2010-11-01
Hey, it's all good, "hijack" or not. Any bit helps, and the "both Shift keys" hint will help anyways if I need to access the GRUB menu.

I've got some books on Unix/Linux (I want to really learn Linux), but they do me no good if I can't even get the installation working. That's the most frustrating part.

I'd still like to know why I'm having this issue, especially since older versions gave me no problems whatsoever.

---

### Post by iKeirNez on 2012-12-15
> **jbyram said:**
> So, a quick update to this problem...

After rebooting many times, I somehow managed to access to GRUB Bootloader menu(?) (I think that in my impatience, I rebooted while Ubuntu was trying to load -- that's the only way I've been able to replicate the results of getting the GRUB menu to actually appear). From here, I entered "Recovery Mode," which after selecting a few options, I was able to get to the login screen and log into my desktop. From here, I was able to set up my network connection and download an NVidia driver. After installing and rebooting, the screen doesn't freeze up at the splash page, and sends me directly to the login screen.

Sooo...clearly, the issue was that I needed a graphics driver installed, but this still leaves a problem/question on my end. In both the graphical installation and the text-based installation, I don't remember seeing anything that would have allowed me to go out and download/install drivers for my graphics card. 

Now, I don't know if this *is* the workaround for this, but essentially I had to enter via a "safe mode" just to download drivers for my graphics card just to get the splash page and login screen to appear properly; there has to be a "correct" way to get this to work, right? Having looked at dozens of Linux magazines, it's always been suggested that with the more "friendly" distros like Ubuntu, you just drop the CD into the drive, boot up, and go. I could understand if I was using some really old hardware, but the parts in my machine are all on the Linux compatibility list. Also, as I mentioned earlier, I've installed older versions of Ubuntu (I believe 8.04) and Mint (which is based on Ubuntu, right) on this same machine, and everything went smooth and worked right out of the box. There hasn't been some hardware support dropped from the newest Linux kernels since I last used a distro, has there?

Again, any explanation would be great. Thanks!

I was having the same issue with 12.10, installing from a USB Drive. I used the nomodeset option you suggested and it worked, except 3/4 would be the bottom of the screen and 1/4 would be the top. So basically the top quarter was on the bottom and the 3 bottom quarters were on the top. To solve this is just unplugged and replugged in the VGA cable and it worked.

Would just like to say thanks as I didn't want to have to install Windows to use Wubi to install Ubuntu.

---

### Post by lisati on 2012-12-15
This thread relates to 10.10. A lot has changed with the 12.xx releases, and we're rapidly approaching the time for 13.04

If a thread hasn't had a response in over a year, it's sometimes best to start a new thread, with a link back to the old thread and an explanation that you're experiencing a similar problem.

Thread closed.

---

