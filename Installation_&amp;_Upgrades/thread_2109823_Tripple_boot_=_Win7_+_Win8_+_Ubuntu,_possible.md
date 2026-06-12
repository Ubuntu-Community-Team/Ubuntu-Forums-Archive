---
title: "Tripple boot = Win7 + Win8 + Ubuntu, possible?"
date: 2013-01-28
forum: Installation &amp; Upgrades
---

### Post by javierdl on 2013-01-28
I hope it's not too much to ask.
I imagine the procedure would not be too different from the one to have a dual boot with Win8 + Ubuntu. 
Just as long as one starts by setting up Win7 + Win8 dual boot first, then add Ubuntu. I just don't know for sure, and don't have much time to experiment on my own. Basically I'm trying to avoid wasting my time on a path that'll take me no where. 
So I was hoping some one would be able to either confirm this based on hands-on experience, or at least be able to speculate based on knowledge and similar experience. 
 
Thanks in advance guys,
 
JDL

---

### Post by offgridguy on 2013-01-28
You could have a look here.

[http://ubuntuforums.org/showthread.php?t=2107958&highlight=triple+boot](http://ubuntuforums.org/showthread.php?t=2107958&highlight=triple+boot)

---

### Post by oldfred on 2013-01-28
As mentioned in offgridguy's link.

Best to keep both Windows installs in primary partitions, then you may be able to directly boot from grub. Windows only installs its boot files into the active partition or the one with the boot flag.

Still applies even though discussing Vista. (Unless you have UEFI.)
       To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

    
Also applies if just dual booting Windows:
       
WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by javierdl on 2013-01-28
Sorry didn't mention it, I don't have UEFI.
 
Thanks a bunch guys, this is great, just what I needed. First off I love to see that it is "possible"!
I shall take it from here :)
 
JDL

---

### Post by javierdl on 2013-01-28
Actually, before I go any further...
 
I only have 1 copy of Vista (full), win7 (upgrade), win8 (upgrade). 
I'm just concerned that the Win7 setup app will tell me that another copy has been installed with the same product key num in a different partition, while I'm attempting to install Win8.
Any idea whether this will happen?
Thanks guys,
JDL

---

### Post by oldfred on 2013-01-29
Do not know details, but to do a full install you cannot use an upgrade disk.

---

### Post by Thee on 2013-01-29
One Windows installation does not care about other Windows installations key.

---

### Post by javierdl on 2013-01-29
Good to hear! 
Thank you guys! :)
 
Now all I need is time to get this done ;)
 
JDL

---

