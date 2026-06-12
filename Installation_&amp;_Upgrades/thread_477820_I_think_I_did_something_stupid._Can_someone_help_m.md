---
title: "I think I did something stupid. Can someone help me fix this mess? Preferably today?"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by Tynach on 2007-06-18
Ok, so my computer worked fine. Absolutely fine. Here are the different hard drives I had at this stage (drive file-system mount-point):

hda1 ext3 /
hda5 swap none
hdb1 ntfs /media/hdb1
hdb2 ext3 /media/hdb2

Then, I buy a 200 GB hard drive from my sister for $60 USD, and I replace it for hdb. So, I need to partition it. So, I use my live CD to partition and install another Ubuntu on the new slave hdb drive. So, in the installation guide, it says:

hda1 ext3 /media/hda1
hda3 swap none
hdb1 ext3 /
hdb2 ext3 /media/hdb2
hdb3 swap none

I don't think about the swap partitions, of which there are now two of.

So, I reboot the computer, and get the GRUB menu. Just fine, except it changed to have the new hdb1 installation at the top, and the hda1 installation at the bottom. I choose to go into my hda1 installation. It boots just fine, except that it is at 640 x 480 screen resolution. I checked my drivers. They're installed and enabled. To be sure, I run Blender (3D app). It runs fine. So, I try to change it. I can't.

At this point, I restore my old xorg.conf file, which I had backed up just in case something like this happened. I reboot, and it doesn't boot. It says there's something wrong with the X server, so it doesn't finish booting. It doesn't even go to a command line.

I reboot (ctrl + alt + del) and go into recovery mode. It boots into it fine, and I type dpkg-reconfigure xserver-xorg I go through the process of reconfiguring X, and I reboot. It still won't boot. I did not back up the weird xorg.conf that allowed at least a 640 x 480 screen, so I have to use my new installation. I try it, and it works just fine. However, it doesn't have all my apps on it, or video/audio codecs. I know I can install them by using the /media/hda1/var/cache/apt/whatever that has the .debs for my apps, but I don't feel like going through the pain of installing them, and I don't have an internet connection on that computer.

So, I try putting my old hdb into the computer, and see if that makes it the same as it used to be. I get a grub error 17, and I cannot even get a list of OS's.

Can someone please tell me something I have not already tried that might or will work to get my old installation up and running?

---

### Post by Tynach on 2007-06-18
bump.

So, 23 people have looked at this, and have been stumped. Sounds very promising for my computer's future.

By the way, I have an ASUS K8N Motherboard, and an nVidia GeForce 6600 LE graphics card. optimum monitor resolution is 1024 x 768 at 85 hz.

---

### Post by jjross on 2007-06-18
it sounds to me like you have grub reading the stage 1 from the wrong partition, when you installed Ubuntu it set grub to read from the partition of the new install.
Look at this How To and hopefully it will lead you to a solution.
[[COLOR="Blue"]Grub How To[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by OzzyFrank on 2007-06-18
I've always fixed GRUB Error 17 with a quick and fairly simple (actually, incredibly simple, but involves the command line) reinstall of GRUB. Here is an excerpt from my Ubuntu guide in case it is the answer you seek:

Remember to replace the drive path with your own; if sharing one drive with Windows, it will be (hd0) for the whole drive or (hd0,0) for the first partition or (hd0,1) for the second partition (if Windows was there first):

Restoring GRUB

You will either need a Super GRUB Disk or your Ubuntu disc, and as long as your drive references are fine everywhere, it will only take a couple of commands to fix things. You will need to decide if GRUB is going in the MBR (master boot record of the drive) or on the partition. If Ubuntu is sharing a drive with Windows, choosing MBR will get back the GRUB menu and let you boot either. If Ubuntu is installed on another drive, and you use a boot manager to boot your partitions, then choosing to install GRUB on the partition may be better. If one doesn't work, then try the other. Simply enter the first command followed by the other. To get to the command prompt on the Super GRUB Disk, type C; to get to the grub> prompt on your Ubuntu CD, go to command line and enter the following before entering the GRUB restore commands:
grub


Restore GRUB to the Master Boot Record (eg: 1st partition on 2nd drive)

root (hd1,0)
setup (hd1)


Restore GRUB to a Partition (eg: 1st partition on 2nd drive)

root (hd1,0)
setup (hd1,0)


Note sure? Find the Partition where GRUB is

At the grub> prompt enter:
find /boot/grub/stage1

---

### Post by Tynach on 2007-06-19
It kind of solves, but not really. Now it shows the old menu, with it thinking my old HD is in place.

I want to be able to boot between my two installations, so I need to completely uninstall grub off both HDs, and then reinstall it. But how do I do this?

By the way, I was messing with my old HD's fstab, and now I don't think that is working properly, and there is no backup file. How do I regenerate my fstab file?

As I say, I did something very, very stupid, and got more than I bargained for.

---

### Post by scannerdarkly on 2007-06-19
I don't understand why you would have 2 Ubuntu installs.  It just doesn't make sense....If I were you instead of spending hours or days trying to figure out how to fix this mistake is back my crap up and reinstall.  I don't know about you but the install process on both my Desktop and Laptop take about 10 to 15 minutes.  If you want to have 2 Linux installs try using a different version like Fedora or OpenSuse.

---

### Post by Vola on 2007-06-19
If you want a boot option for the second hdd you need to edit your hda1 -> /boot/grub/menu.lst and add a new entry. 

You can copy the entry from the boot of second hdd and ensure that this points to (hd1,0)

Anyway why you need a second installation??

---

### Post by Tynach on 2007-06-19
I was actually just fooling around. I got bored, ok :)?

Alright. But now my old installation is going nuts. It boots into a command line, but has only capital letters! Caps lock is not the problem, even commands like ls make all the output capitalized.

---

### Post by OzzyFrank on 2007-06-19
> **scannerdarkly said:**
> I don't understand why you would have 2 Ubuntu installs.  It just doesn't make sense....If I were you instead of spending hours or days trying to figure out how to fix this mistake is back my crap up and reinstall.  I don't know about you but the install process on both my Desktop and Laptop take about 10 to 15 minutes.  If you want to have 2 Linux installs try using a different version like Fedora or OpenSuse.

Uh... yeah... it really isn't all that strange dude...I started that way so I could try things on the "lesser" install before committing them to my main Ubuntu install. I didn't want to be one of those who install it, have a few hours fun before it all goes to hell and then I'm uninstalling it, and then be putting a flame post here about how much I love Windows (conveniently forgetting all the hell IT has given me in the past). If my original Edgy drive hadn't started dying, I'd still be using it for some things, like trying the official upgrade method which has given a few people hell (I did a fresh install of Feisty on my new drive).So, not only doies it make sense, for newbies who want to go through the hassle of maintaining 2 installs is actually a good way to learn and still have one desktop that functions. Weird, but true.

---

### Post by OzzyFrank on 2007-06-19
> **Tynach said:**
> How do I regenerate my fstab file?

Edit it by hand. And yes, you can restore grub, but it will still get its menu listings from /boot/grub/menu.lst, so you will need to edit that correctly.

---

### Post by scannerdarkly on 2007-06-19
> **OzzyFrank said:**
> Uh... yeah... it really isn't all that strange dude...I started that way so I could try things on the "lesser" install before committing them to my main Ubuntu install. I didn't want to be one of those who install it, have a few hours fun before it all goes to hell and then I'm uninstalling it, and then be putting a flame post here about how much I love Windows (conveniently forgetting all the hell IT has given me in the past). If my original Edgy drive hadn't started dying, I'd still be using it for some things, like trying the official upgrade method which has given a few people hell (I did a fresh install of Feisty on my new drive).So, not only doies it make sense, for newbies who want to go through the hassle of maintaining 2 installs is actually a good way to learn and still have one desktop that functions. Weird, but true.

You make a very valid point.  To me it just didn't make any sense, that's all.

---

### Post by OzzyFrank on 2007-06-20
It's also a valid point why the hell would you want 2 Ubuntu installs, hehe. I mean, yeah, if you're gonna maintain another Linux partition, it may as well be another distro. But, just say you take Ubuntu a bit more seriously than just another distro to play with, or have no interest in other distros. Then a second Ubuntu install for trying out settings and programs and updates, etc, is valid as a way of ensuring you don't mess up your main install (I've just posted regarding a security tip about setting shared memory to read-only, and the response was sure it's good, if you don't want to be able to access your system... so another install isn't a bad idea for a testing ground).

Personally, I thought I'd finally start playing around with Linux and have a few pet OSes, and I chose Ubuntu just after the release of Edgy. I've tried a few other Live CDs, but so far Ubuntu is the only Linux I have installed. I will play around with some another time, probably, but when I realised Ubuntu could really be a replacement for Windows, or at least my main OS, I decided to keep setting up Ubuntu.

So me having 2 Edgy drives was not by design, but because I originally installed on an old 10Gb drive to see if it was worth it, then ended up installing again on the 80Gb drive that's now dying. I admit it got a bit tiresome updating 2 installs, but I still should shove in the old 10Gb original install here and there to test things. Or just plan ahead and ask in the forums first (glad I didn't implement those security recommendations without asking here first!!).

---

### Post by scannerdarkly on 2007-06-20
> **OzzyFrank said:**
> It's also a valid point why the hell would you want 2 Ubuntu installs, hehe. I mean, yeah, if you're gonna maintain another Linux partition, it may as well be another distro. But, just say you take Ubuntu a bit more seriously than just another distro to play with, or have no interest in other distros. Then a second Ubuntu install for trying out settings and programs and updates, etc, is valid as a way of ensuring you don't mess up your main install (I've just posted regarding a security tip about setting shared memory to read-only, and the response was sure it's good, if you don't want to be able to access your system... so another install isn't a bad idea for a testing ground).

Personally, I thought I'd finally start playing around with Linux and have a few pet OSes, and I chose Ubuntu just after the release of Edgy. I've tried a few other Live CDs, but so far Ubuntu is the only Linux I have installed. I will play around with some another time, probably, but when I realised Ubuntu could really be a replacement for Windows, or at least my main OS, I decided to keep setting up Ubuntu.

So me having 2 Edgy drives was not by design, but because I originally installed on an old 10Gb drive to see if it was worth it, then ended up installing again on the 80Gb drive that's now dying. I admit it got a bit tiresome updating 2 installs, but I still should shove in the old 10Gb original install here and there to test things. Or just plan ahead and ask in the forums first (glad I didn't implement those security recommendations without asking here first!!).


Yea, I have a desktop and a laptop so my laptop is my testing grounds.  I'm running Fedora 7, OpenSuse10.2, Ubuntu, and of course Windows.  At one point I actually had Mac OS X running on it.  I have a Dell XPS m140 by the way.  But on my desktop I have Ubuntu and Windows on it.  I'm mainly on Ubuntu on my desktop and mainly on one of the linux distro's I have on my laptop.  I'm slowly going away from Windows.  On a side note,  I'm an MCSA working on getting my MCSE. :D

---

