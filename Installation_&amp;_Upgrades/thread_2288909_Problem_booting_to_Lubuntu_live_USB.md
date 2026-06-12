---
title: "Problem booting to Lubuntu live USB"
date: 2015-07-30
forum: Installation &amp; Upgrades
---

### Post by nizdobs on 2015-07-30
Here's the situation:
I have a PC that I had setup to dual boot: Windows 7 from the hard drive and Lubuntu 14.04 from the SSD. The computer lost power while backing out a failed Windows upgrade and I could no longer boot to windows. My corporate IT guy reinstalled Windows to the hard drive (I should have had him remove the SSD before he did but I didn't think to).

Now I want to reload the bootloader so I can restore my dual boot options. I followed the instructions [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") to try to use Lubuntu Live USB key to install the Boot-Repair tool. My PC does not have a CD/DVD drive so I used UNetBootin to create the Lubuntu Installer on a USB key. Also note that the SSD had Lubuntu 14.04 on it but the Installer USB key had the files for Ubuntu 15.04 on it. The MD5 Sum check against the Lubuntu 15.04 iso file matched.

When I boot my PC I am presented with the standard Live CD bootup menu but when I choose "Try Lubuntu without Installing" the screen goes blank and does not progress. I've tried the same USB key in a different PC and I was able to boot to Lubuntu Live.

Anyone have any idea why my Lubuntu Live won't work on my PC?

Thanks in advance,

- Niz

---

### Post by Bucky Ball on 2015-07-30
When you boot from the USB, hit a key when you see the purple screen with the icon down the bottom (if Lubuntu has that) and you should get to the options 'Try Lubuntu' 'Install' etc. Hit F6 and choose 'nomodeset' from the pop-up menu. You won't see anything happen, but now go 'Try Lubuntu'. Any different?

---

### Post by nizdobs on 2015-07-30
Bucky -

Thanks for the reply. When I boot from USB the choices I'm offered are:
Default
Help
Try Lubuntu without installing
Install Lubuntu
Check disk for defects
Test memory
Boot from first hard disk
Try Lubuntu without installing
Install Lubuntu
OEM install (for manufacturers)
Check disc for defects

And a message under the options that reads: "Press [Tab] to edit Options"

I don't know why some of the choices are repeated. 

Anyway, when I press F6 nothing happens. If I highlight "Try Lubuntu without installing" and then press tab I am presented with the following line of text: 
> >/casper/vmlinuz.efi initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash ---

Is that helpful? Do I want to put the [FONT=Courier New]nomodeset[/FONT] in there somewhere?

Thanks again,

- Niz

---

### Post by nizdobs on 2015-07-30
OK, so I edited the options line to read:
> >/casper/vmlinuz.efi initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash nomodeset

I got a few error messages about no radeon support or some such thing but eventually it showed me the lubuntu desktop.

Thank you Bucky!

---

### Post by Bucky Ball on 2015-07-31
Excellent news! Exactly what you do. If you have the same issue after install, let us know and we can fix and make permanent (this change will be lost if you restart the live media). If you have problems with the install, post a new thread with a descriptive title in ***Installations and Upgrades***. Good luck. :)

---

