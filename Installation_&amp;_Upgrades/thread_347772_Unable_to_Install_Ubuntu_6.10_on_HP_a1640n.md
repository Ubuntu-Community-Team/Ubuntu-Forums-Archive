---
title: "Unable to Install Ubuntu 6.10 on HP a1640n"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by teich on 2007-01-27
Hi All,

I've been trying to install Ubuntu 6.10 on my father's new HP a1640n.  The XP system failed catastrophically and was unrecoverable, and was unreturnable because the rebate had been sent in.

However, I'm having some problems.  The installer boots from CD but after choosing Install, i see "Loading Linux Kernel", a few green letters flying around in the background, then the screen goes black and a blinking underscore sits in the upper right indefinitely.  I have done this with both the Live CD and the alternate install CD ("Install in Text Mode"), with multiple download attempts using bittorrent.

I am fairly new to this myself so I am not really sure what to do at the moment.  Any help is appreciated.

The full hardware specs of the a1640n are here:
[http://www.compusa.com/products/product_info.asp?product_code=341267&pfp=#ts](http://www.compusa.com/products/product_info.asp?product_code=341267&pfp=#ts)

Thanks.
Alex

---

### Post by bward1 on 2007-01-27
I'm interested to know more about how the XP system failed catastrophically.  That might provide some insight especially if it is a hardware problem.

---

### Post by housam on 2007-01-28
Your laptop specs are OK.Now , I suppose that you have a free laptop. Boot from the CD and use the Gparted to reformat the entire HDD to ext3 ( in case that you w'll not install windows again).
If it doesn't work , try to reburn the iso at a slower speed i.e 4x or 2x.

---

### Post by teich on 2007-01-28
bward1: 
After three days of appearing to work fine, the system stopped booting entirely.  It is unclear why.  Safe mode and recovery partition would both start up and then freeze partway into the process.  It took 3 weeks for them to send separate recovery CDs, which we just used today.  Everything looks OK now, in windows.  But I'd still like to get a dual boot running if possible (I have an Ubuntu/XP system on my laptop and am very happy with it).

housam:
I originally used GParted on the SystemRescueCD to make the linux partitions when things started going wrong.  I did not format the system recovery partition but only formatted and resized the (broken) windows partition.  Also, I burned the alternate install CD that I tried at the slowest speed possible, I believe 2x.

Thanks for the help.  Any ideas?
Alex

---

### Post by teich on 2007-01-28
Update:
I tried burning an ubuntu desktop CD from the computer's now-working windows install, at 2x.  It gave the same problems.  Then I tried using the boot options line (F6) and used acpi=off noacpi.  This got me into the Live CD, where it gets to the desktop and I see the error

"There was an error starting the GNOME Settings Daemon.

Some things, such as themes sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. [.. some other stuff...]"

At this point the mouse and keyboard both do nothing and I am unable to make the system respond.  How can I tell if this is a mouse and keyboard driver issue or if it is the system hanging completely?  And what do I do?

Thanks.
Alex

---

### Post by bward1 on 2007-01-28
What type of keyboard and mouse are you using.  If for example you are using bluetooth, then that might cause some problems.  I always try and use a PS/2 keyboard for the install, but i would think a usb mouse and keyboard would work.  People smarter than I might be able to point you more in the right direction with the exact error messages and the exact keyboard and mouse.

---

### Post by teich on 2007-01-28
Keyboard and mouse are both PS/2 with nothing fancy or different as far as I can tell.  They came right out of the box with the computer and so are the cheap, standard kind of hardware.

---

### Post by teich on 2007-02-01
Anyone?

---

### Post by jarviw on 2007-02-09
what you should try, to help yourself to have a better hold of the problem, is during your GRUB booting, press **e** to edit your boot script.

it will take you to your boot script, something looking like this:

> 
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot


(this is basically the boot script in /boot/grub/menu.lst)

you should edit the kernel line, and delete **quiet splash** from it.
(you should also remove noacpi, acpi=off for this testing)

> kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro

then press **b** to boot.

this way linux will boot with all the information displayed.  it will probably get stuck at some point, and well, that's probably where your problem is.


...................

I had trouble booting my old old sony vaio before, same "symptom" as you did (not a very informative symptom), worked when I turned off acpi (but I need acpi for the PCMCIA card), blah blah blah... ended up fixing it with a BIOS upgrade.

I also had trouble booting an ubuntu installed onto a USB HD, again, not very informative symptom of stuck during boot.  then I figured it's an issue with the USB device with that desktop system, as it got stuck setting up the USB.
...... 

so, try the verbose booting first.  that should lead you to the real problem.

---

### Post by Avidtk on 2007-02-09
> **teich said:**
> Update:
I tried burning an ubuntu desktop CD from the computer's now-working windows install, at 2x.  It gave the same problems.  Then I tried using the boot options line (F6) and used acpi=off noacpi.  This got me into the Live CD, where it gets to the desktop and I see the error

"There was an error starting the GNOME Settings Daemon.

Some things, such as themes sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. [.. some other stuff...]"

At this point the mouse and keyboard both do nothing and I am unable to make the system respond.  How can I tell if this is a mouse and keyboard driver issue or if it is the system hanging completely?  And what do I do?

Thanks.
Alex

Hi Alex, I have the same problem, all the details are precisely the same, I have Epox MB 5LDA+GLI,Intel D CPU 3.2 GHz, 2.00 GB of RAM, NVIDIA GeForce 6600 display Card, 250.00G SATA System drive and a 300.00 G SATA drive for storage, this Hardware worked very well with WIN XP Pro.
Anyhelp

---

### Post by Avidtk on 2007-02-09
> **teich said:**
> Update:
I tried burning an ubuntu desktop CD from the computer's now-working windows install, at 2x.  It gave the same problems.  Then I tried using the boot options line (F6) and used acpi=off noacpi.  This got me into the Live CD, where it gets to the desktop and I see the error

"There was an error starting the GNOME Settings Daemon.

Some things, such as themes sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. [.. some other stuff...]"

At this point the mouse and keyboard both do nothing and I am unable to make the system respond.  How can I tell if this is a mouse and keyboard driver issue or if it is the system hanging completely?  And what do I do?

Thanks.
Alex

I had the same problem, after 6 hours and many Installs I unplug  the PS2 Keyboard , Mouse " while my System still hanging " and pluged in a USB  Keyboard and Mouse now I can move the cursor and log on with the Keyboard, I rebooted many times with no problems, I do not know why the PS2 Keyboard and Mouse are hanging the System up , so try to use  a USB  Keyboard and Mouse  ????

Avidtk

---

### Post by teich on 2007-02-10
jarviw -- That definitely sounds like the right way to proceed to me.  Unfortunately the computer is not within physical reach at the moment.  I'll give it a shot next time I am there.  Thanks for the tip.

avidtk -- I'll try that as well.  Strange that ps/2 would be more problematic than USB.. but ok.  Worth a try.

Thanks.
Alex

---

### Post by flash3843 on 2007-02-15
I too have an HP a1640n running 6.10.  I also tried ACPI=off, but that messed up access to USB devices.  Using the boot option,  pci=nommconf,  lets me boot the system successfully.  Note that as yet I have no idea if that option will cause other problems.  It hasn't for me thus far.

Ubuntu is the ONLY distribution I've tried that actually boots on my system, and finds all the hardware including sound device and wireless card.

Hope this works for you.

---

