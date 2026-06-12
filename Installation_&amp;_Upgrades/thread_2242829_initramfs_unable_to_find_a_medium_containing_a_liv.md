---
title: "initramfs unable to find a medium containing a live filesystem = just after updates"
date: 2014-09-04
forum: Installation &amp; Upgrades
---

### Post by Tom 6 on 2014-09-04
Hi :)  
I tried updating my LiveUsb using 

sudo apt-get update
sudo apt-get upgrade

but it seemed to run into troubles and grumbled asking me to;  

sudo apt-get -f install  
sudo apt-get autoremove

and then it grumbled wanting me to do "dpkg --configure" so i did the usual;  

sudo dpkg --configure -a


Now when i try to boot up any machine it gets to the funny 2 'icons' at the bottom of the screen, then to the "Ubuntu" with dots under it a bit like the old progress bar type of idea and then before getting to the proper splash-screen it drops to a weird command-line and says;  

(initramfs) unable to find a medium containing a live filesystem

I can boot into a desktop Ubuntu machine to try to chroot (or whatever) into the system or something like that but i have no idea about how to do any of that.  Actually the LiveUsb is Kubuntu rather than Ubuntu but i have had the same problem with Ubuntu before and am just hoping the fix is the same.  Any ideas?  Even a link into some documentation would help!  
Regards from 
Tom :)

---

### Post by ubfan1 on 2014-09-04
While you can certainly update most packages on a persistent Live-USB, not all packages can be updated, like kernels.  Non-UEFI machines are not even booting with grub, so I don't know that any update would actually update the boot menu.  You can look at the documentation on creating a live-USB media, and try to fix the one you have, or make a full install to a USB (see C.S.Cameron's howto, and the pros and cons).  I'd suggest a full install to a different media, then mount the old USB with the casper-rw file or partition and pull off your files into the new system.

---

### Post by Tom 6 on 2014-09-04
Hi :)  
Thanks!  Good plan :)  

It took ages to do the updates so i'd rather not start again from scratch.  Also there are some files and bookmarks in there somewhere.  Your plan sounds like it's either going to totally work or else will give me a greater understanding of what goes on "under the bonnet".  Either way it's a win! 
Regards from 
Tom :)

---

### Post by ian-weisser on 2014-09-04
Ubfan1is right: Live environments are designed for trial use. They are intended to be disposable, functional snapshots. They are not designed for upgrading or long-term use.
The clever hoops through which a Live environment decompresses itself and installs itself into RAM limit the learning possibilities of the environment, especially if you are interested in early boot sequence (Live boots differently than normal Ubuntu), the kernel, and package management/upgrades.

I think you're running into those limitations.

---

### Post by Tom 6 on 2014-09-04
Hi :)  
Yeh, i've always meant to explore this guide
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)
to learn more about that but never had a really pressing reason before.  I think this could be that time for me.  There is nothing really vital that isn't backed-up on an Ubuntu desktop or Debian server but figuring a way of fixing this usb could be helpful.  I do really like having a familiar environment when using other people's machines and feeling safe that i don't leave important files scattered around town.  There are limitations but there is a lot more i could explore about this.  
Thanks and regards from 
Tom :)

---

### Post by Tom 6 on 2014-09-04
Hi :)  
Blimey!  I tried editing a few files but no change so i restored the back-ups i'd made before editing.  I even tried installing grub2 but even that didn't help.  

Finally went with ubfans suggestion but cheated a bit by just downloading a new iso image and installed something to let me open isos as though they are just compressed files.  Then dragged initrd and a vmlinuz across and as if by magic my usb-stick boots-up just fine now.  That was when i suddenly had the big flash-back to having done this before.  Wish i'd remembered that about 12 hours ago!!  

Still all my files are there, and my bookmarks and when i opened Firefox it apologised for my tabs having closed and then reopened all the ones that i'd had open this morning!!
Thanks all!
Regards from 
Tom :)

[Edit:  err i 'had to' run updates again but this time i stopped short of updating the kernel!]

---

