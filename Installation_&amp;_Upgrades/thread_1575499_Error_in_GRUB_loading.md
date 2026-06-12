---
title: "Error in GRUB loading"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by rk45 on 2010-09-15
I'm completely new to Ubuntu sorry, so you'll have to bear with me.

I recently acquired a second hand computer. Its specs are:
Q8200 processor
Asus P5Q Pro motherboard
4GB RAM (I think it's made up of 2x1GB + 1x2GB DDR2-800)
ST3320620A Barracuda 7200.10 HDD (320GB)
Asus EN9800 GT video card

The only peripheral that is plugged in is a wireless mouse and keyboard set.

Palimpsest says that the hard drive has one bad sector, which I  understand shouldn't be the end of the world. Running MemTest86 suggests  that one stick of RAM failed part of test 4.

Now, I'm trying to do a clean install of Ubuntu 9.10 AMD64 onto it, but I'm running into trouble. I downloaded the image file for the installation, then burned a boot disk for it using ImgBurn at the slowest speed possible. It all goes fine up until it asks me to remove the boot disk as it restarts - when it restarts, it gives the message:

"GRUB loading.
no module name found
Aborted. Press any key to exit."

I searched the forums for a solution to this, and found a recommendation for GAG Bootloader. I can set up a key for Ubuntu easily enough, but then trying to boot it yields:

"Sector boot not found or invalid"

I can run Ubuntu 9.10 directly off the boot disk without any issues, which made me think that it might be an issue with the hard drive.

I don't know if it's related, but trying to install an old copy of Windows XP with SP3 resulted in the infamous Trap 00000006 error - Exception error, which didn't come right using the Windows Recovery Console. I have run chkdsk on the hard drive which completed properly. 

Now, can somebody more knowledgeable than I am suggest where to go from here? Would trying a new version of Ubuntu (or an i386 version instead) likely prove helpful? Is it more likely that one of the hardware components is messing things up? Is there a way to get around this GRUB issue that even I, somebody with very little knowledge of the operating system, can understand?

Any help with this issue would be massively appreciated.

---

### Post by psusi on 2010-09-15
Umm, if memtest says you have bad ram, you need to fix that before you do ANYTHING else.

---

### Post by oldfred on 2010-09-15
After you fix your hardware issues. Run this script as it will show where everything is installed.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

