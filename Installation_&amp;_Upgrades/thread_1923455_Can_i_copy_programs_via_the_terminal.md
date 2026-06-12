---
title: "Can i copy programs via the terminal?"
date: 2012-02-10
forum: Installation &amp; Upgrades
---

### Post by davidc60 on 2012-02-10
Hi,
I have a spare, fully-installed copy of Ubuntu 11.10 on an USB. It is starting to go on the blink so I will be re-installing my Ubuntu 11.10 ISO again on to a different USB. On that original, fading USB I had downloaded and installed Gparted and the Restricted Extras package. 

All I need to know is whether it is possible to specifically copy those downloads/installs (Gparted and Restricted Extras) from the original, fading USB on to the new, fresh installation on the second USB (ie. via the terminal (dd))? 

(I know that I could copy (dd) the whole of the original USB over to a second USB but I don't want to do that again and I appreciate that I could simply download and reinstall Gparted etc again from the internet but I simply want to learn how to copy over individual programs, if it is actually possible to do that at all).
Thanks,
davidc

---

### Post by drmrgd on 2012-02-10
If you just strictly want to copy something (no syncing, no automatic deletion, etc), then you just need to use the 'cp' command:

```
man cp
```

So, assuming the folder where your programs are on your flash drive is called, "programs" and your drives automatically mount to /media:

```
cp -r /media/flashdrive1/programs/ /media/flashdrive2/
```

That'll copy the programs folder from the first to the second flash drive.  If it's just 1 file, you don't need the '-r' option....well, might as well just read the man file :p

Hope it helps

---

### Post by savanna on 2012-02-10
OK, for learning purposes :-)

Packages you've downloaded and installed are kept in /var/cache/apt/archives. So you could copy the files you need (or all - easier) to the same directory on your new USB key.

eg

sudo su -
cp /media/source/var/cache/apt/archives/* /media/target/var/cache/apt/archives

Or copy the packages you want to ~, and install them manually with:

sudo dpkg -i foo.deb

---

### Post by collisionystm on 2012-02-10
> **savanna said:**
> OK, for learning purposes :-)

Packages you've downloaded and installed are kept in /var/cache/apt/archives. So you could copy the files you need (or all - easier) to the same directory on your new USB key.

eg

sudo su -
cp /media/source/var/cache/apt/archives/* /media/target/var/cache/apt/archives

Or copy the packages you want to ~, and install them manually with:

sudo dpkg -i foo.deb


System updates are also kept here.

---

### Post by collisionystm on 2012-02-10
Just run ubuntu from your new usb, plug in your old one into another usb port and copy and paste the files

---

### Post by dabl on 2012-02-10
> **davidc60 said:**
> ... I simply want to learn how to copy over individual programs, if it is actually possible to do that at all).


Not sure what you mean by "downloaded", but if you mean "installed via apt-get or the GUI package manager (synaptic)", then no, you're not going to be able to cleanly copy the installed packages.  The reasons are, (1) all of the package is not normally installed in a single location in the filesystem, and (2) to run, you also need the unique dependencies for each package, and unless you wrote them down while it was installing, you don't know how to solve that.

Using "cp" is trivially easy, for copying files or directories, including individual .deb package files.

There are also ways to make your own little local repository of your installed packages -- [[COLOR="SeaGreen"]**aptoncd**[/COLOR]](http://aptoncd.sourceforge.net/) comes to mind.

I hope there's a useful answer in there somewhere.  :)

---

### Post by davidc60 on 2012-02-10
Thanks for the helpful replies. In response specifically to 'dabl', yes, I did use the package manager to organise the downloads/installs. Your advice about 'aptoncd' is very useful and I'll do that in the future as I have been experimenting recently with alot of Linux OS's on various partitions and disks.

davidc

---

### Post by dabl on 2012-02-10
> **davidc60 said:**
> ... I have been experimenting recently with alot of Linux OS's on various partitions and disks.


Don't forget to give [[COLOR="SeaGreen"]**siduction**[/COLOR]](http://siduction.org/index.php?module=news&lang=en) a spin.  :D

---

