---
title: "How to Find and Install the Latest Stable Linux Kernel"
date: 2011-10-30
forum: Installation &amp; Upgrades
---

### Post by GreenRaccoon on 2011-10-30
Here's an easy how-to guide on how to find the latest mainline, stable, or longterm Linux kernel and how to upgrade to it.

You can open System Monitor and go to the first tab to see what kernel you currently have.

First, check out [http://www.kernel.org/](http://www.kernel.org/) to see the latest kernel that you want.

Then, go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") and scroll down to the one you found on the other site.

Open up the link, then download (the order is important here):
linux-headers-..._all.deb
linux-headers-...i386.deb (or linux-headers-...amd64.deb if you're using 64 bit)
linux-image-...i386.deb (or linux-image-...amd64.deb for 64 bit)

Then just run these through Ubuntu Software Center (double click them, or right-click and select Ubuntu Software Center).  Make sure you install them in this order; if you don't, Ubuntu Software Center won't let you install them.

-----EDIT-----

The Ubuntu kernel team seems to have started splitting the kernel into four packages now. The instructions are the same, except you'll need to install one more package at the end:
linux-image-extra-...i386.deb (or linux-image-extra-...amd64.deb if you're using 64 bit)

This fourth package should be installed last, after the other three.

---

### Post by GreenRaccoon on 2011-11-07
I've been having problems with Ubuntu Software Center (4.0.5) freezing up while installing these packages.  Another way to install these is through Terminal.  I'm explaining two days to do this through Terminal. If you don't put anything on your desktop, then the first method is easier and faster; if you have .deb folders on your desktop, then skip down a bit to the second method.

For the first method, first download the packages to the Desktop ("~/Desktop").  If you download them to your "Downloads" folder ("~/Downloads"), then just open up the file manager and copy and paste it to the desktop.

Then press "ctrl + alt + t" to open up Terminal.  Change directory to the Desktop by doing this:

```
cd ~/Desktop
```
Then install all of the .deb packages on the Desktop using "dpkg -i". [COLOR=Red]If you have other .deb packages on the Desktop besides these 4, you should use the second method explained later.[/COLOR]
```
sudo dpkg -i *.deb
```Done!

Here's the second method. First, download the packages. Then press "ctrl + alt + t" to open up Terminal.  Change to the place where you downloaded the packages, which is probably "~/Downloads". (Make sure "Downloads" is capitalized)

```
cd ~/Downloads
```List the ".deb" packages in this folder.
```
ls *.deb
```Then install the packages using "dpkg -i".  [COLOR=Red]The order is very important here![/COLOR]  Replace the "..." with the full name: whatever "ls" showed.  Alternatively, you can open up the Downloads folder (using the file manager, which is called nautilus), copy the name of the package, and paste it in Terminal.  However, when pasting things into Terminal, you have to use "ctrl + shift + v" instead of "ctrl + v".
```
sudo dpkg -i linux-headers-..._all.deb linux-headers-...i386.deb linux-image-...i386.deb
```For 64 bit:
```
sudo dpkg -i linux-headers-..._all.deb linux-headers-...amd64.deb linux-image-...amd64.deb
```
-----EDIT-----

It seems that the Ubuntu kernel team has started a new system of using four .deb packages instead of just three. Just tag "linux-image-extra-...i386" or "linux-image-extra-...amd64" to the end of the command line in the Terminal. It'll look like this:
```
sudo dpkg -i linux-headers-..._all.deb linux-headers-...i386.deb linux-image-...i386.deb linux-image-extra-...i386
```For 64 bit:
```
sudo dpkg -i linux-headers-..._all.deb linux-headers-...amd64.deb linux-image-...amd64.deb linux-image-extra-...amd64
```
Again, make sure you do it in this order. If "dpkg -i" doesn't work, I'm sure you can use "gdebi" instead. To do this, just replace "dpkg -i" with "gdebi".

---

### Post by nah40 on 2011-11-23
> **GreenRaccoon said:**
> Here's an easy how-to guide on how to find the latest mainline, stable, or longterm Linux kernel and how to upgrade to it.

First, check out [http://www.kernel.org/]("http://www.kernel.org/") to see the latest kernel that you want.

Then, go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") and scroll down to the one you found on the other site.

Open up the link, then download:
linux-headers-..._all.deb
linux-headers-...i386.deb (or linux-headers-...amd64.deb if you're using 64 bit)
linux-image-...i386.deb (or linux-image-...amd64.deb for 64 bit)

Then just run these through Ubuntu Software Manager.I have downloaded the files but cannot figure out how to use the Ubuntu software Manager to install. Please provide info. I guess my brain quit functioning.

---

### Post by GreenRaccoon on 2011-11-25
> **nah40 said:**
> I have downloaded the files but cannot figure out how to use the Ubuntu software Manager to install. Please provide info. I guess my brain quit functioning.

My Ubuntu Software Center likes to freeze while installing non-supported packages too.  Have you tried installing them through Terminal?  That's worked much better for me.  The tutorial to do that is a couple comments up.

---

### Post by MG&amp;TL on 2011-11-25
> **nah40 said:**
> I have downloaded the files but cannot figure out how to use the Ubuntu software Manager to install. Please provide info. I guess my brain quit functioning.

If it doesn't freeze, right click on package -> Ubuntu Software Centre

---

### Post by GreenRaccoon on 2011-11-25
> **MG&TL said:**
> If it doesn't freeze, right click on package -> Ubuntu Software Centre

Thanks, MG&TL.  I think I misread his (or her) comment.

---

