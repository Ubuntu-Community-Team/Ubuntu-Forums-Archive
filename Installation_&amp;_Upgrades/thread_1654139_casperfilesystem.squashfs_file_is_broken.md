---
title: "casper\filesystem.squashfs file is broken"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by dmeisegeier on 2010-12-27
Hi,
 
I just tried to create a USB drive for installing Ubuntu on another windows based PC and received the following Diagnostic Message when running the Universal USB Installer 1.8.2.0 app:
 
Data error in 'casper\filesystem.squashfs'. File is broken.
 
However, once I click the "close" button I got a message that the installation was done and the process was complete. So I then tried to boot my other PC with the USB drive (I did change the boot order to start with the USB drive) and it looked like it was going to start up but then I got the following 2 messages:
 
(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: invalid argument
 
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
 
I couldn't figure out what to do (I'm new at this), so I reformatted the USB drive and re-ran the USB installer but got the same message. None-the-less, I tried to boot my other PC from the USB drive but got the same 2 messages.
 
Any suggestions?
 
Thanks!
 
David

---

### Post by amsterdamharu on 2010-12-27
You can try to create the usb with [unetbootin]("http://unetbootin.sourceforge.net/") and see if that causes the same problems. If it does than I think your problem lies in the iso file being corrupt.

Sorry to sound a bit like a spammer here pushing the bootin but it always worked wonders for me and most people who I recommend it where some of the Ubuntu or other tools seem to fail.

---

### Post by djpinto on 2011-01-01
I'm having exactly the same problem with my 10.10 USB installation.

It must by the iso file because unetbootin didn't work either.  I downloaded the iso directly from the ubuntu homepage.  I imagine its a bug that will solve itself in time.

I downloaded 10.04.1 iso and that worked fine.  I'm new too and so that's enough to get me started for now.

DP

---

### Post by renegademag on 2011-01-21
Same thing for me too. I just downloaded it last night after downloading the wrong one (desktop instead of netbook which does not let you know it's specific) and have the exact same problem. Does it work or not? If you can't even boot from it, why even release it? I wouldn't consider this "SOLVED" since it's happening right now. What should people do? Why is it so hard to get a version that works or at least HELP with problems like recommend a different version and where to get it. Why on the download page would they have you download a USB drive maker when it already comes with the download? Or why not include it with the download if it's different? Why make this so hard and redundant? I'm frustrated that the desktop version loaded no problem at all with no extra work. The netbook version is so much more work for such little difference. All I did with that was like an easy Mac, click the icon, everything worked out fine. Except the monitor resolution. But with Netbook version, oh ****, I have to go through more hoops than an NBA season. Why? And why is this considered "solved" with no solution? What should the rest of us who have this problem? Go to a board to see the same problem has been solved to find out it's not? What's the solution?

---

### Post by renegademag on 2011-01-21
[http://releases.ubuntu.com/lucid/ubuntu-10.04.1-netbook-i386.iso.torrent](http://releases.ubuntu.com/lucid/ubuntu-10.04.1-netbook-i386.iso.torrent)

Does not exist. What now?

---

### Post by amsterdamharu on 2011-01-21
It's solved because for the poster using unetbootin solved his/her problem. This is a forum and not a but report system.

When exactly do you get an error and on what machine are you trying it on?

---

### Post by howdy123 on 2011-03-25
Hi, I had this same problem, and changing the pen-drive installer didn't help.  For me the problem was my filesystem.squashfs file was corrupted whenever I downloaded it from my crummy wireless network.  Once I plugged into ethernet and re-downloaded the iso, everything worked fine.  Hope that helps.

---

