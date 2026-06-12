---
title: "Problem with usb 2.0"
date: 2018-10-16
forum: Installation &amp; Upgrades
---

### Post by alvarojsr on 2018-10-16
Hello there, it's my very first time trying to install an Linux distribution. I'm having some issues, my motherboard only have 2 usb 3.0 ports and when I try to install using an 2.0 port it just won't work ( device descriptor read/64 error -32// unable to find a medium containing a live file system). When I try to install using one of mine usb 3.0 ports it works but my mouse and keyboard on 2.0 just won't work as well, so I have to use only on of them in the remaining 3.0 port. Also the installation is not recognizing the windows 10 already installed on my ssd. What am I doing wrong?

---

### Post by oldos2er on 2018-10-16
Hi, can you tell us the make/model of your computer, and its hardware specs?

---

### Post by alvarojsr on 2018-10-16
Sure
The mobo is ga970-ud3P am3+
2x8gb 1600 hyperx memory
120 gb SSD for os
1tb hd for files
Fx 8350
Asus Rx 580 8gb
Cooler Master 80-plus Gold 750w psu

---

### Post by alvarojsr on 2018-10-16
It goes like this, when mouse and keyboard are on usb 2.0 keyboard lights almost off and mouse won't even light up
When I put either of them on the usb 3.0 port they work
Edit: added a picture of what happens when I try to install from usb 2.0 port 
edit 2: removed large images as requested 
links for the images : [https://i.imgur.com/Nj6AONJ.jpg](https://i.imgur.com/Nj6AONJ.jpg) and [https://i.imgur.com/RZwlCAA.jpg](https://i.imgur.com/RZwlCAA.jpg)

---

### Post by QIII on 2018-10-16
Hello!

Although the boards are not the same, this issue appears to be common among many Gigabyte boards.  Please see if [this]("https://ubuntuforums.org/showthread.php?t=2326722") helps and let us know the outcome.

Cheers!

---

### Post by alvarojsr on 2018-10-16
I put my keyboard on my 3.0 and usb on the other so I could use it, then chooses "try Ubuntu" to access the OS and be able to use the terminal, typed the command and it says " 'gksudo' not found, did you mean gfsudo?"

---

### Post by alvarojsr on 2018-10-16
New update : by enabling IOMMU on bios i can now use my usb ports 2.0, but now the 3.0 that are dead but whatever i have enough 2.0, the only real problem left is that when i am trying to install alongside windows i either cant even detect the instalation and when i try to use legacy boot, it does detects windows but not the ssd, just the 1 tb hd ( ssd is already AHCI)

---

### Post by QIII on 2018-10-16
Did you change the grub command line to "GRUB_CMDLINE_LINUX="iommu=soft""?

That gives Ubuntu control of iommu when it starts.


By the way:  don't insert large images in your posts.  Some of our users still have slow connections or data limits.  Let them decide if they want to expand a thumbnail -- which you can insert by using the attachment functionality represented by the paperclip button above the text entry box.  For the moment I have removed them.  You can add them again by going to Edit and then Go Advanced.  Then use the paperclip.

---

### Post by alvarojsr on 2018-10-16
> **QIII said:**
> Did you change the grub command line to "GRUB_CMDLINE_LINUX="iommu=soft""?

That gives Ubuntu control of iommu when it starts.


By the way:  don't insert large images in your posts.  Some of our users still have slow connections or data limits.  Let them decide if they want to expand a thumbnail -- which you can insert by using the attachment functionality represented by the paperclip button above the text entry box.  For the moment I have removed them.  You can add them again by going to Edit and then Go Advanced.  Then use the paperclip.

Oops, sorry about that, i was using my phone. Removed the images.

Yes i did, it's working fine, my only issue now is about installing on ssd without erasing windows. Ubuntu can't detect anything when i use normal EFI boot, and with legacy boot it will just ignore the SSD and install alongside with windows on HDD

---

### Post by QIII on 2018-10-16
By "working fine", you should get both USB 2.0 and USB 3.0.

As far as "installing along side", that has not been an option for quite some time.  It's now "Do something else".  Which release of Ubuntu are you attempting to install.

When you get to it ... If you are having issues and want to make absolutely sure you don't wipe Windows, you can always temporarily unplug the Windows drive.

---

### Post by alvarojsr on 2018-10-16
Both are working after I restarted the system.
You mean dual-boot on the same drive isn't a thing? Sorry if I sound too stupid. It's my first time dealing with this, I am trying o learn

---

### Post by QIII on 2018-10-17
Yes, you can dual boot on the same device.  You have to use the Windows partition tools to shrink the Windows partition to provide some empty space.

Then, when installing Ubuntu, select "Something else", which has replaced the "Install alongside Windows" option.  That is why I asked what release of Ubuntu you are attempting to install.  But I see now from your images that you are attempting to install a more recent release.

If you do dual boot on the same device, be very careful not to disturb the Windows partitions already on the device.  Leave them entirely alone.  Do NOT choose "Erase disk and Install Ubuntu".  That will obliterate your Windows installation.  Backing up your entire drive before you begin is advisable.  Things can, and often do, go wrong.

Now here's a question:  If you have not yet installed Ubuntu, how did you complete the IOMMU changes I suggested?  Was that in a Live Session?

---

### Post by alvarojsr on 2018-10-18
Ye I figured it myself, after some time I created an 30 GB partition for Ubuntu on my ssd and installed into it, now it's working fine. And yes it was a live section. Everything went smoothly besides an error I can not remember at installing GRUP2 or something like that ( can't really remember the name) Wich was solved by using legacy installation instead of UEFI
Edit:
Thanks for all the help. I will try to adapt to the new OS.

---

