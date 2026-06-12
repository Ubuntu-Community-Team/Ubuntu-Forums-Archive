---
title: "D-Link WUA-2340 USB Wireless Adapter"
date: 2013-01-25
forum: Installation &amp; Upgrades
---

### Post by Pyramist on 2013-01-25
Hey everyone how's it going?  I've decided to install Ubuntu 12.10 on my old Dell Desktop instead of Windows XP to try it out.  I use a D-Link WUA-2340 USB Wireless Adapter on that computer to connect to the internet (no built in wireless adapter).  I did a clean install of Ubuntu 12.10 via a Pen Drive USB.  And this is where my issue comes in: A) I have no internet access even while installing the OS and B) Once it's all installed and I log in, I get a blank background and an error message telling me that "Compiz has closed unexpectedly).  This is my first time with Ubuntu so I'm pretty inexperienced.  I do have access to the internet on my laptop (Windows 7), so if there's anyway to transfer the drivers or whatever I need from the laptop to the desktop via USB, that would be awesome.

I've done some research and found people with similar problems, but not all of these problems at the same time.  I've tried a few methods I've seen online but to no avail.  Any help would be sincerely appreciated.  Thanks!!

---

### Post by omeomi on 2013-01-25
A) You will need ndiswrapper to install the driver, see this thread: [http://ubuntuforums.org/showthread.php?t=861855](http://ubuntuforums.org/showthread.php?t=861855)

B) You probably don't have the right videodriver installed yet. For now you can try logging in using the 2D unity version (select in the login screen) which should work. Once you get the internet fixed you will probably be able to install the right driver

---

### Post by meteorrock on 2013-01-25
Try to use a 'hypervisor' to put that ubuntu distro you want to use on your dell machine. That way you can get that distro up and installed in a "virtual hard drive" and get it up and going. You can later choose to do a dual boot option later if you like it.

Check out VMware online and download that app on your Windows OS you have. The hypervisor will use your existing drivers that are powering your wi fi and sort of piggyback on your host OS.

Your guest OS will open inside of a program called a virtualization. It is like an emulator for your Windows OS. Then choose to mount or install your ubuntu distro through your hypervisor. 

The VMware hypervisor is a friendly program with wizards to walk you through the whole setup on getting your linux build you want installed. This way you do not have to fuss about whether your ubuntu distro you want to look over will support your wi fi drivers and cards. After you get the distro up, ubuntu will then fetch your needed drivers if you want.

Here is the link for VMware. It is a free program for personal use. [http://www.vmware.com/](http://www.vmware.com/)

This link here is for the free download of VMware. [https://my.vmware.com/web/vmware/info/slug/desktop_end_user_computing/vmware_workstation/9_0](https://my.vmware.com/web/vmware/info/slug/desktop_end_user_computing/vmware_workstation/9_0)

~~~~~~~~~~~~~~~~~~~`

Once you got your ubuntu distro up and going in that 'hypervisor', you will need to download the tools for a full desktop in your terminal. Only use this code below if your VMware hypervisor fails to get the vm tools you will need for it. 

Here is the codes you will need. 

```
sudo apt-get install open-vm-tools
```
```
sudo apt-get install open-vm-dkms
```
```
sudo apt-get install open-vm-toolbox
```

I hope this helps you. I think this would be the easies solution to save from having to look for drivers for your wifi and other devices on your machine. :)

~~~~~~~~~~~~~~~~~~~~~
:KS Help develop on XDA forums for their flagship android devices at this link here [http://forum.xda-developers.com/forumdisplay.php?f=860](http://forum.xda-developers.com/forumdisplay.php?f=860)

---

### Post by Impavidus on 2013-01-25
Try a wired internet connection. It should work and enable you to install the drivers you need (both wireless and graphics).

---

### Post by Pyramist on 2013-01-25
I've tried everything listed and I'm having a lot of issues still.  I keep getting error messages when I try to run 'make install' or 'make' for ndiswrapper that say:

make[2]: Leaving directory `/usr/src/ndiswrapper-1.57/ndiswrapper-1.57/driver'
make[1]: *** [ndiswrapper.ko] Error 2
make[1]: Leaving directory `/usr/src/ndiswrapper-1.57/ndiswrapper-1.57/driver'
make: *** [install] Error 2

---

### Post by mörgæs on 2013-01-25
Please give a complete hardware description.

---

### Post by Pyramist on 2013-01-26
How can I view my hardware specs?  I'm continuing to have problems but I've made some progress.

I connected my desktop to the internet via an Ethernet cable, and re-installed Ubuntu 12.10, this time with internet connection.  My current problem is that every time I log in, I still get just the background image with no bar at the top or anything.

---

### Post by mörgæs on 2013-01-26
My guess is that the computer (especially the screen card) is not powerful enough for Ubuntu. If that's the case you should consider X/Lubuntu.

Please run 
```
sudo lshw > lshw.txt
```and post the result.

---

### Post by Pyramist on 2013-01-26
It's not even letting me access terminal now when I press Ctrl+Alt+T.  Is there another way to open it so I can run that command??

---

### Post by mörgæs on 2013-01-26
The lshw-command can run in a live boot.

You could also go straight to the testing and install one of the other Buntus.

---

### Post by Pyramist on 2013-01-27
Ok I re-installed Ubuntu 12.10 and I was able to access the terminal  (still just a background image after logging in) and ran the command  'sudo lshw > lshw.txt' and it reads: "PCI (sysfs)" for about ten  seconds and then disappears.

---

### Post by mörgæs on 2013-01-28
Sounds good. Now you have a file called lshw.txt in your home directory. Please post the contents in CODE tags.

---

