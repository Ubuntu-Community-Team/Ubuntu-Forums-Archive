---
title: "XFCE broke my Ubuntu"
date: 2006-07-13
forum: Installation &amp; Upgrades
---

### Post by Peter Mount on 2006-07-13
Hi

I installed XFCE last night with:

sudo aptitude update
sudo aptitude install xubuntu-desktop

This was onto Ubuntu 6.06 with the Kubuntu desktop

When I went to log into Xubuntu it wouldn't let me get passed the Log in Screen. I just kept being taken back to the Kubuntu log in screen. I tried removing the xubuntu-desktop but I still had the same problem.

I found a similar problem at:

[http://www.ubuntuforums.org/showthread.php?t=186577](http://www.ubuntuforums.org/showthread.php?t=186577)

I have no data on that hard drive yet so I'm thinking I should just wipe it and install Kubuntu 6.06, which I downloaded last night on my other hard drive. I'll just install a couple of Gnome apps on Kubuntu like gFTP and Bluefish (in case Quanta+ crashes).

With Xubuntu is it safer to download the Xubuntu iso and just use the CD to install on a separate partition or hard drive (I've got two hard drives)? I've read the Xubuntu desktop is still in Beta. I'm running a business so even though I want to try Xubuntu I don't want it to wreck the partition with my data on it.

Thanks

---

### Post by dan_kent on 2006-07-14
This sounds like a .ICEathourity problem

Try this link

[URL="http://www.ubuntuforums.org/showthread.php?t=134400&highlight=session+lasted+10+seconds"]login in safe mode, which will take you to a command prompt
the do 'sudo RM [/URL]

If you're wanting to run Xfce because you have an old slow machine then I've found you're better installing Xubuntu from scratch and not upgrading from Ubuntu with the Xfce packages. With a fresh install you don't get all the gnome junk that you won't need and hence a nippier machine

Dan

---

### Post by Peter Mount on 2006-07-14
Thanks dan_kent

I tried that link but it didn't seem to work. I just wiped the hard drive and installed Kubuntu. I'll download Xubuntu and I'll check that out seperately from Kubuntu.

Have fun

---

### Post by loell on 2006-07-14
:) its rare to have a smiling face after all that ;) 
but thats a good thing..

---

### Post by Peter Mount on 2006-07-14
Hi

I now think it is KDE that broke my Ubuntu (not XFCE). I installed Kubuntu on it's own last night and now I have the same problem again.

I'm going to try a possible solution I found in kubuntuforums.net, i.e. deleting the .Xauthority file (or similarly named file starts with "X") in the home directory. If that doesn't work I'll try installing Xubuntu on it's own. If that fails I'll just try Ubuntu (with Gnome).

---

### Post by Peter Mount on 2006-07-15
Hi

I just intalled Xubuntu. It's a case of "so far so good". I guess it suits my old computer anyway (Pentium 2-350 with 448mg ram). As long as it's stable and can do what I want it to do I should be fine with it.

Have fun

---

### Post by Peter Mount on 2006-07-15
Hi

I wiped Xubuntu and installed Ubuntu. Xubuntu was nice and quick but I found it a bit lacking in features. Maybe I'll try it again when the next version comes out.

Ubuntu seems fast enough so far

Have fun

---

### Post by loell on 2006-07-15
xfce aims to be simple and straightforward
and i think it will always be.

---

### Post by drtvasudevan on 2006-07-15
yes! i think one needs to install the distro based on what applications one will run and just not because there are more applications.especially in slower machines.
i do run xfce which is decidedly faster when i just want to browse and mail.
if i need to do some serious office work i boot to gnome.

tv

---

