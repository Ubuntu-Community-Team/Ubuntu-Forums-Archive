---
title: "Ubuntu installed on external hard disk not booting"
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by intull5 on 2011-07-16
Hello! I tried installing ubuntu 11.04 on my 80gb external Hard Disk. I also have a normal ubuntu 11.04 installed on my PC. I partitioned 35gb of the external hard disk for ubuntu and installed it successfully. I restart my computer, hit F12 for the boot menu and select "USB-HDD". But the PC ubuntu boots up not the external hard disk ubuntu. 

Should i do something? Have i gone wrong somewhere?

---

### Post by MIchaelStephens on 2011-07-16
Hi, I have been struggling with the same issue for several weeks now. The only way I can boot Ubuntu at the moment is to boot off of a Supergrub CD or use a USB flash drive.

---

### Post by intull5 on 2011-07-16
I found out that the hard disk itself is not recognized. I inserted another hard disk, which got detected with a separate identifier. But this hard disk is not. I don't know why. Does the booting identify ext4 file systems? Is it because of that?

---

### Post by oldfred on 2011-07-16
My system does not boot USB devices from USB list but from hard drive list. Took me quite a while to realize that.

Post this:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by MIchaelStephens on 2011-07-16
Hi, all I finally got mine to boot..
Booted from LiveCD and partitioned the USB hard drive:
/boot 500 meg ext2, primary, bootable
Swap 4 Gb
/ - 12Gb ext4
/home  rest of the drive ext4

Then installed keeping the above structure.

Success...

---

