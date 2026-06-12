---
title: "Problem installing ubuntu win.7 on sep. drives"
date: 2011-08-25
forum: Installation &amp; Upgrades
---

### Post by turomixo on 2011-08-25
I had first tried using an old hard drive laying around.  I ran ubuntu off of the CD.  I used            sudo gparted , and deleted all partitions on it.  Then I formated to ext4.  

The drive appears in both bios, windows and ubuntu, but when I try and install ubuntu, the drive doesn't show up at all.  Even after disconnecting my windows HD.  So I gave up on it, and I instead installed on my external USB drive.  

I disconnected the HD with windows 7 on it, and installed ubuntu to the USB HDD.  It worked fine, and it boots up on startup.  But, when I plug in my windows HD, ubuntu will not boot.  The HD is recognized in bios, but no matter which HD I boot off of it, windows starts right up.  When I disable my windows HD, in bios, but leave connected, and then boot from my external HD, I get an error that there is no bootable media.  

So basically, Ubuntu boots off of my external HD, but only when my other HD is disconnected.  

I have an Asus sabertooth P67 motherboard, windows 7, mybook external HD, and am installing ubuntu 10.10.  

I'm excited about using ubuntu, any help would be appreciated.

---

### Post by Hakunka-Matata on 2011-08-25
Welcome to the forums.
Is your Ubuntu install partition on the USB HDD marked with the boot flag?  That may make a difference as dictated by your computer's BIOS firmware.  Normally that would not be a problem, but I have seen in these forums cases where it did play a role.

---

### Post by oldfred on 2011-08-26
With everything plugged in from a Ubuntu liveCD run this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

Are drives IDE, SATA or mixed?

---

