---
title: "Clean install w/o cd/dvd/usb/floppy, but with a working installation of 7.10"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by grenness on 2008-02-23
I have an old piece of computer that I use as a home server - it's a 700Mhz something with 512MB RAM (or less, I don't quite remember), the good thing is that it's a tower with plenty of space for harddisks.
It is currently running Ubuntu 7.10, but I want to change to Xubuntu to see if I can squeeze some more performance from it.
Problem is, since I installed 7.10 from a CD a few months ago, I bought an additional IDE harddisk and used the power and IDE data cable for the CD drive to connect the new harddisk, and I am now out of both power and data cables (I have a total of four HDD's in it now).
I don't want to bother installing an additional IDE controller, and I would like to avoid open up the computer and swapping cables back and forth between one of the harddisks and the CD drive.
Is it possible to make a clean Xubuntu installation by starting with the current installation?
Make the computer restart, go into installation mode as if the CD was loaded and booted from, and take it from there?

I am able to follow instructions for Terminal commands, but I like it better in GUI - which btw is the reason that I don't want to install Ubuntu server without GUI although I know it would free up lots of resources.

Might just add that this computer used to run Windows 2003 Server, and it was slo-o-o-o-w, but with Ubuntu 7.10 it's actually pretty good, but I'm pushing my luck as it keeps getting more and more tasks - file server, multimedia server, torrent downloader, "cctv" server (two USB webcams, although I'm having a hard time making the computer recognize my cams, think I need to buy new ones), etc. etc.!

Thanks,
Christopher

---

### Post by Pumalite on 2008-02-23
Maybe this:
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)
I haven't look into it, so, I don't know if Xubuntu is there.

---

### Post by grenness on 2008-02-24
Thanks, I will examine it more when I have some spare time.
Since you haven't looked much into it, you probably wouldn't know, but maybe someone else: it says I need to alter my DHCP server - I run IPcop as DHCP server on a separate (even older) machine, does anyone know whether IPCop is suited to play part in this solution?

I also need to add that my computer (the one I want to clean install) neither has a floppy disk drive (don't know why) nor do I think the Bios is capable of network booting (PXE).

Thanks again,
Christopher

---

### Post by Pumalite on 2008-02-24
Sorry not to be of more help. Good luck.

---

### Post by dstew on 2008-02-24
If your are interested in performance, rather than disk space, I think you can just```
sudo apt-get install xubuntu-desktop
```That leaves the Ubuntu-specific packages on the disk, but you should now have the option to run under Xubuntu.

---

### Post by grenness on 2008-02-25
Thanks, that might be what I will end up with, instead of trying to achieve what I originally wanted - I know my "terminal limitations" so I fear that I might end up with lots of frustrations and no good solution.

But I will wait and see if others chip in with tips on how to reach the original goal before I do anything.

~Christopher

---

### Post by Cattista on 2008-03-05
I used [this]("http://www.psychocats.net/ubuntu/purexfce") to switch from ubuntu to xubuntu. It removes the packages installed with ubuntu and then installs xubuntu-desktop. Not sure if it would be classified as a "clean" install, but at least you don't have to reinstall everything.

---

### Post by HyRax on 2008-03-05
The sudo method will probably the best way to go for you, but you mention that despite the age of your machine, it has a couple of USB ports - you could source yourself a cheap USB CD/DVD drive from somewhere and use that to do a fresh disc install (though if your machine is USB 1.1, it will be awfully slow to install, but once done, you'll be fine).

---

