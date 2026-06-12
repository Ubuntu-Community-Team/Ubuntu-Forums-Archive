---
title: "Install without CD drive"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by PfromD on 2010-01-16
I have an irritating problem that is a malfunctioning CD drive on my HP Pavilion (zv6000). Which I've come to understand is all too common.
But on top of that I once had Mandrake installed in dual-boot with winXP on separate partitions. I had an accident which erased the linux partition, but not the boot loader, so I still have to select XP to boot. And I don't know how to work around that, though it's probably quite easy.
The thing is that I used ubuntu on my stationary PC some time ago and loved it, along with growing more and more annoyed with Windows, but that PC has broken down :(
I would really love to have ubuntu on my laptop .. but how on earth do I do that without the CD drive?
I do have a USB pen with plenty room for the ubuntu iso if that's the way to go about it.

---

### Post by New5teve on 2010-01-16
I had to get a .img file (which is available with ubuntu 9.04) and i used unetbootin to create the startup usb stick. After the install was complete i upgraded it to 9.10
I'm new to ubuntu as well, i hope this helps.

---

### Post by C.S.Cameron on 2010-01-16
I think you can get XP to boot again by sticking in the original CD and get to the console and run "Fix MBR", oops that requires a CD drive I guess.
There is a Ubuntu application that will fix a windows MBR but I forget the name and believe it is no longer in the repositories. (see edit)

It is easy to make a boot pendrive from windows, (as New5teve mentions).
Download the Ubuntu iso.
Download Unetbootin for Windows.
Plug in your flash drive
Open unetbootin and select Diskimage, point to the iso.
Select your flashdrive location at the bottom.
Hit OK.
Prior to booting the pendrive open BIOS and select the pendrive as first hard drive.

Edit:
Found it, you can download ms-sys for fixing windows boot loader here:
[http://ms-sys.sourceforge.net/#Download](http://ms-sys.sourceforge.net/#Download)

---

### Post by PfromD on 2010-01-16
I'm glad that you caught at least some of your mistakes by yourself :)
I.e The problem is not booting Windows as it boots fine .. once I've done the annoying selection of booting windows. But the selection is in Mandrakes boot loader mind you. Can't remember its name right now as it takes me .2 secs to get past the boot screen -hit "end" and "enter"- so I never pay attention. But I can't just turn on the laptop and then, say to go the bathroom, as Mandrake is still the default and that just ends with the boot loader crying about some major boot crisis. 
You don't say .. the OS has to be present to boot? duh!
Should I expect the install method by New5teve to overwrite the present Mandrake boot loader, or first attempt to fix it as if Mandrake was never installed and then try?
When looking via msconfig I can't see anything that should make the Mandrake boot loader precede windows .. but then again, msconfig shows the system AFTER being selected in Mandrake's boot loader.

---

### Post by PfromD on 2010-01-16
Errr ... as far as I can see, the ms-sys fixer is for Linux. I Can't "make" in dos prompt ... unless there's some prog that enables me to do so.

---

### Post by C.S.Cameron on 2010-01-18
ms-sys can be used via Ubuntu Live CD or Live USB to fix the MS boot loader.
If you install Ubuntu from a Live USB it should fix you up with a new grub and it will not be necessary to fix your Windows MBR.

---

### Post by PfromD on 2010-01-18
That's what I reckoned. The auto-fix with an Ubuntu install that is. I'm going to go ahead and give it a try sometime tomorrow.

---

### Post by PfromD on 2010-01-24
So I finally got around to fetching unetbootin and do the USB trick. What a clever little tool that is.
And man it installs quickly! .. almost brought tears to my eyes to get Ubuntu up and running this easy. Too bad it's on a crappy laptop that needs to have WinXP on it too :(
Now only awaits the mammoth task of setting the whole thing up the way it used to be when I used Fiesty Fawn, Gutsy Gibbon, Hardy Heron. But I'm never letting go again. Never ever!
Thanks for pointing me to unetbootin.

---

