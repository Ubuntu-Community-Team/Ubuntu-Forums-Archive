---
title: "Ndiswrapper + kernel sources"
date: 2005-08-27
forum: Installation &amp; Upgrades
---

### Post by Mozzer on 2005-08-27
Hello, I'm a Ubuntu newbie and so far I've managed to do stuff using existing posts and I feel like I'm making progress and I'm starting to like it.

However, I can't get on the internet because I can't get Ndiswrapper working for my wireless card. Therefore I have to keep switching OS whenever I need more info (which is, unfortunately, a lot). If I can just crack this then it should make my transition from Windows to Linux a whole lot easier.

The problem is in the very first line of the installation:

ln -s /usr/src/linux-<kernel-version> /lib/modules/VERSION/build

I know this is supposed to make a shortcut to the kernel source, but in my case /usr/src/linux-2.6.10-5-386 just doesn't exist so the shortcut doesn't work. 

I have installed the linux-header packages off the CD, and attempted the extra repositories, fakeroot and all sorts of other stuff that's recommended but it mostly seems to rely on using the internet to download stuff which is obviously impossible.

What I actually have in my /usr/src folder is 2 linux-headers folders and 1 rpm folder. So how do I get this linux-2.6.10-5-386?

Thanks in advance
Mozzer

---

### Post by ekravche on 2005-08-27
If you are using a wireless RT2500 or RT2400 card then you can install generic linux drivers for those.  I had to go through the same experience. Here are some links to make the process easier for you.

[https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/)
[http://www.ubuntuforums.org/showthread.php?t=53528](http://www.ubuntuforums.org/showthread.php?t=53528)

---

### Post by Mozzer on 2005-08-29
[QUOTE=ekravche]If you are using a wireless RT2500 or RT2400 card then you can install generic linux drivers for those.  I had to go through the same experience. Here are some links to make the process easier for you.

[https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/)
[http://www.ubuntuforums.org/showthread.php?t=53528](http://www.ubuntuforums.org/showthread.php?t=53528)[/QUOTE]
 Unfortunately the card I am installing is a DWl-510. The Realtek site which provides the Windows driver also has a Linux driver but the makefile did not work.

The download site: [http://tinyurl.com/2theq](http://tinyurl.com/2theq)

The contents of the download: [http://tinyurl.com/bz9um](http://tinyurl.com/bz9um)

Feedback from the makefile:

root@ubuntu:/home/mozzer/driver2 # make
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/mozzer/driver2 MODVERDIR=/home/mozzer/driver2 modules
make[1]: Entering directory `/lib/modules/2.6.10-5-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.10-5-386/build'
make: *** [modules] Error 2

---

### Post by az on 2005-08-29
That driver seems to be made for RedHat.  Your best bet is to use ndiswrapper, or roll up your sleeves and hack the driver to work with Ubuntu.

A properly made driver tarball will autodetect your linux-headers by looking for the symlink it makes to /lib/modules/(yourkernel)/build.  I guess you are saying that this driver does not do that.  As I said, it seems to be made for RedHat.

On the other hand, are you sure you have the proper linux-headers package?

If you are using the stock kernel, install build-essential and linux-headers-2.6.10-5-386.

---

### Post by Mozzer on 2005-08-29
[QUOTE=azz]That driver seems to be made for RedHat.  Your best bet is to use ndiswrapper, or roll up your sleeves and hack the driver to work with Ubuntu.

A properly made driver tarball will autodetect your linux-headers by looking for the symlink it makes to /lib/modules/(yourkernel)/build.  I guess you are saying that this driver does not do that.  As I said, it seems to be made for RedHat.

On the other hand, are you sure you have the proper linux-headers package?

If you are using the stock kernel, install build-essential and linux-headers-2.6.10-5-386.[/QUOTE]
 Well I installed the linux-headers package using apt-get and it asked for the cd and it all seemed to work. I now have the folders "linux-headers-2.6.10-5" and "linux-headers-2.6.10-5" in my /usr/src folder.

I did build-essential and that asked for the CD but it also seemed to want to download stuff from the internet which is impossible without the wireless drivers.

The problem seems to be that I don't have a folder called "linux-2.6.10-5-386" for the shortcut to work.

And, erm... what's the stock kernel?

Thanks for continuing help, Mozzer

---

### Post by az on 2005-08-29
[QUOTE=Mozzer]Well I installed the linux-headers package using apt-get and it asked for the cd and it all seemed to work. I now have the folders "linux-headers-2.6.10-5" and "linux-headers-2.6.10-5" in my /usr/src folder.

I did build-essential and that asked for the CD but it also seemed to want to download stuff from the internet which is impossible without the wireless drivers.

The problem seems to be that I don't have a folder called "linux-2.6.10-5-386" for the shortcut to work.

And, erm... what's the stock kernel?

Thanks for continuing help, Mozzer[/QUOTE]


Install build-essential and linux-headers-2.6.10-5-386.

Those two packages and their dependancies are on your cd.  Install them.  Do not just install the linux-headers-2.6 package.  Install "linux-headers-2.6.10-5-386"

If you have never gone on the net with the machine, or enabled any other repositories other than the cd, it will just "download" them from the cd.  Do not worry.


The stock kernel is the kernel that comes with a fresh install of the OS.  If you do not know what any other kernel is, you are still running the stock kernel and everything is okay.  Do not worry about it.  It is just another reason why this solution would not be working for you.  But this is not the case, so forget about it.

---

### Post by Mozzer on 2005-08-30
[QUOTE=azz]Install build-essential and linux-headers-2.6.10-5-386.

Those two packages and their dependancies are on your cd.  Install them.  Do not just install the linux-headers-2.6 package.  Install "linux-headers-2.6.10-5-386"

If you have never gone on the net with the machine, or enabled any other repositories other than the cd, it will just "download" them from the cd.  Do not worry.


The stock kernel is the kernel that comes with a fresh install of the OS.  If you do not know what any other kernel is, you are still running the stock kernel and everything is okay.  Do not worry about it.  It is just another reason why this solution would not be working for you.  But this is not the case, so forget about it.[/QUOTE]
 Build-essential and linux-headers-2.6.10-5-386 have both been installed.

Neither have produced the folder /usr/src/linux-2.6.10-5-386.

This folder is required in the line of code 
ln -s /usr/src/linux-<kernel-version> /lib/modules/VERSION/build
on the Ndiswrapper installation page.

Without this folder I cannot install Ndiswrapper.

---

### Post by Mozzer on 2005-09-02
[QUOTE=Mozzer]Build-essential and linux-headers-2.6.10-5-386 have both been installed.

Neither have produced the folder /usr/src/linux-2.6.10-5-386.

This folder is required in the line of code 
ln -s /usr/src/linux-<kernel-version> /lib/modules/VERSION/build
on the Ndiswrapper installation page.

Without this folder I cannot install Ndiswrapper.[/QUOTE]
 Ok so somehow (using an ndiswrapper-utils package) I have managed to get Ndiswrapper working... to a point.

I've installed the driver and when I do ndiswrapper -l it says 

Installed ndis drivers:
bcmwl5 driver present, hardware present

So it's great up to there, but when I do modprobe ndiswrapper it gives me this error:

root@ubuntu:/home/mozzer # modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

This occurs whether I use sudo or not. It seems a lot of other people have had a similar problem but I didn't see any definite solutions. Can anyone help?

---

### Post by az on 2005-09-02
[QUOTE=Mozzer]Build-essential and linux-headers-2.6.10-5-386 have both been installed.

Neither have produced the folder /usr/src/linux-2.6.10-5-386.

This folder is required in the line of code 
ln -s /usr/src/linux-<kernel-version> /lib/modules/VERSION/build
on the Ndiswrapper installation page.

Without this folder I cannot install Ndiswrapper.[/QUOTE]


Okay, the symlink /lib/modules/2.6.10-5-386/build" is provided by the linux-headers-2.6.10-5-386 package and point to /usr/src/linux-headers-2.6.10-5-386.  Never mind what it written somewhere else.  You can build the ndiswrapper utils and modules from the ndiswrapper source just like that, out-of-the-box.  It will find that symlink and use the provided headers.  Don't change anything.

I am not quite sure why you have to rebuild ndiswraper anyway.  Is the version provided by default not working for you?  The module is already compiled and installed as part of the stock kernel.  The ndiswrapper comman-line utility is provided by the ndiswrapper-utils package which is on your installation cd.

You should basically just install ndiswrapper-utils (using synaptic, for exampl) and then from a comman line type

sudo ndiswrapper -i (file.inf)
sudo ndiswrapper -l   (which will tell you if the driver is present)
and then 
sudo modprobe ndiswrapper

Then you should be able to configure your wireless device in the desktop netwroking utility.


If all that works, make the module load at boot tim e by insterting the word
ndiswraper
in the /etc/modules file (sudo gedit)

---

### Post by Mozzer on 2005-09-03
[QUOTE=azz]Okay, the symlink /lib/modules/2.6.10-5-386/build" is provided by the linux-headers-2.6.10-5-386 package and point to /usr/src/linux-headers-2.6.10-5-386.  Never mind what it written somewhere else.  You can build the ndiswrapper utils and modules from the ndiswrapper source just like that, out-of-the-box.  It will find that symlink and use the provided headers.  Don't change anything.

I am not quite sure why you have to rebuild ndiswraper anyway.  Is the version provided by default not working for you?  The module is already compiled and installed as part of the stock kernel.  The ndiswrapper comman-line utility is provided by the ndiswrapper-utils package which is on your installation cd.

You should basically just install ndiswrapper-utils (using synaptic, for exampl) and then from a comman line type

sudo ndiswrapper -i (file.inf)
sudo ndiswrapper -l   (which will tell you if the driver is present)
and then 
sudo modprobe ndiswrapper

Then you should be able to configure your wireless device in the desktop netwroking utility.


If all that works, make the module load at boot tim e by insterting the word
ndiswraper
in the /etc/modules file (sudo gedit)[/QUOTE]
 I love you Azz. It's working!

First thing to note is that neither the build-essential or linux-headers-2.6.10-5-386 packages made the symlink. I had to do that manually.

As for being ready out-of-the-box, I check the sybaptic package list and ndiswrapper-utils was installed (having done it manually as I explained earlier) but the ndiswrapper-source was not. So... no idea on that one.

So anyway I uninstalled the ndiswrapper-utils (as it gave an error when I got to the modprobe) and followed the instructions for installation using the source. And by gum it worked! In fact since I created the link thingy, absolutely everything worked!

I could connect to my router downstairs but Firefox kept saying it couldn't find the urls I tried. I changed the connection settings to auto-detect but that didn't help.

One last thing I can switch to Ubuntu for the majority of the time...

---

### Post by jasmuz on 2005-10-04
Hello there. 

Im trying to work the same issue with the D-Link DWL-G510 Wifi Card under Ndiswrapper (I was trying to install it to my server wich runs Knoppix), can you please give me a hand on how you did everything....im going to have to make the server Ubuntu based then or try my luck compiling under Knoppix.

Concerning your Firefox issue, please check if your machine is doing DNS resolution properly.

Hope to hear from you, because of this issue with the card i havent started on my Linux Access Point Project for my Neighboorhood.

Take Care.-

---

### Post by Mozzer on 2005-10-08
Ok, the first thing to do is actually check if ndiswrapper is installed on your copy of Ubuntu because for some reason mine did not. In terminal type

```
ndiswrapper -l
```

(that's a small L by the way)

If it's installed it should say something about no drivers being installed, otherwise it will not recognise the command.

---

### Post by Snocrash on 2005-10-08
I know it might seem like overkill...but because I need to compile custom modules....Paragon-ntfs, ndiswrapper, nvidia or ati drivers, linux-wlan-ng, etc....I will almost always compile my own kernel after install. Even if I just use the stock config file from the distro, things will always build smoother and there is no question about having everything you need and the correct versions needed on the system to build the modules. It really does not take that long to do (30 mins to an hour on a good machine). And besides, building your own kernel is kinda a right of passage for n00bs. Below is a link to the kernel compile howto. I strongly suggest using the ubuntu patched sources with the --initrd flag just to eliminate filesystem issues at boot.

[Kernel Compile Howto]("http://www.ubuntuforums.org/showthread.php?t=56835")

Best of luck.

-Sno

---

