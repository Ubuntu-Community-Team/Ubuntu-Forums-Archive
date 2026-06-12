---
title: "Ubuntu Hardy Heron on USB stick"
date: 2008-07-12
forum: Installation &amp; Upgrades
---

### Post by peakshysteria on 2008-07-12
Not sure this is the right thread, but if I'm wrong i guess a mod can move it to the right place!? Here goes:

Is it possible to install Ubuntu Hardy Heron 8.04 on a USB stick _from Windows or an existing Ubuntu installation_ and run it from [COLOR="Red"]**OSX, Windows or Linux**[/COLOR]? Going on holiday soon and it would be sweet to bring Hardy on my 8 GB OCZ Rally2 :)

---

### Post by scragar on 2008-07-12
[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar) (or printer-freindly version: [http://www.debuntu.org/book/export/html/160](http://www.debuntu.org/book/export/html/160) )

that any good for ya?

as for finding the disk, personally I find it easier to mount it and check from the **mount** command, avoids mistakes.

---

### Post by peakshysteria on 2008-07-12
Thanks man. I've found several guides for how I can make a persistent install of Ubuntu to my USB stick. [Pendrivelinux]("http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/") seems like the best and most rich solution so far. But the _main_ question is how I can make it boot both on OSX, Windows and (any) linux. All my home machines are running Ubuntu. All my work stations are running Windows. Some of my friends are running OSX. So since I'm from time to time are using all OS's it would be sweet to always bring along my own setup.

---

### Post by Spaceman9 on 2008-07-12
You might want to look at this site [http://www.dreamlinux.com.br/](http://www.dreamlinux.com.br/)

It has an installer on the live cd for usb thumb drives.

---

### Post by peakshysteria on 2008-07-12
Thanks man. [Dreamlinux]("http://www.dreamlinux.com.br/tutorials/3.0/usb-install/usb-install.html") seems very nice. But I can't find any information about if it is cross platform capable. Will this run from my USB on both OSX, Windows and Linux?

---

### Post by Spaceman9 on 2008-07-12
Hardware Requirements XFCE: Pentium III 128 MB RAM HDD 4GB free. GNOME:Pentium III 256 MB RAM HDD 4GB free.

Alternative install: USB Memory Stick with 1 GB. See documentation or Dreamlinux Forums First Stop for details.

---

### Post by peakshysteria on 2008-07-12
Thats the requirements for the installation. It really looks like Dreamlinux only can be runned on exsisting linux installs:
> [URL="http://www.dreamlinux.com.br/desktopedition/usblive-overview.html"]Dreamlinux USB Flash Memory
[/URL]
By using our new "Dream_On_A_Pen" philosophy you can boot your Dreamlinux on any computer that is able to boot from a pen-drive (USB Flash Memory).

Dreamlinux Customized + USB Flash Memory

Besides, once running from a pen-drive, you will be able to keep your data safe inside it. All you need to do is create folders to store your data, music, videos, you name it. They not only will be accessible inside your Dreamlinux pen-drive Operating System, they can be read in any other computer running any Linux distro. 

---

### Post by Spaceman9 on 2008-07-12
It doesn't say in the doc's but I don't know of any reason why it wouldn't work with OSX. If you have a second thumb drive you could try it. Dreamlinux is almost pure Debian linux and Ubuntu is based on Debian so both should work with OSX. OSX is based on FreeBSD which is based on UNIX just like Linux. And PC-BSD is the desktop/laptop version of FreeBSD. I like PC-BSD but it has a ways to go to be as easy to use as Ubuntu.

---

### Post by MattBD on 2008-07-12
Do you mean you want to be able to boot Ubuntu from a USB stick like you would with a live CD, or do you actually want to run it within another OS?

---

### Post by peakshysteria on 2008-07-12
I would like to be able to boot Ubuntu Hardy from the USB stick no matter which OS/machine is available. Meaning I can always access my browser, bookmarks, files, settings etc....And of course I would like to use my own themes and wallpapers and my favorite apps and save files like I do on my main machine/Ubuntu.

---

### Post by MattBD on 2008-07-12
In that case, I'd use the tutorials at Pendrivelinux. They include persistent installs, so you can keep things like bookmarks.

The tutorial for persistent Ubuntu install from live cd is at [http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)

I found this only worked properly if you installed LiLO as per the fix at the bottom.

Once this is done it should boot OK on pretty much any machine that has a BIOS capable of booting from USB regardless of OS - it completely bypasses the existing OS so it doesn't matter what's on there, it's just a matter of having hardware that Ubuntu supports. I haven't tried it on a Mac yet.

---

### Post by peakshysteria on 2008-07-12
I'll give it a go at the beginning of next week. Thanks man. I'll let you all hear how it goes.

---

### Post by KingTermite on 2008-07-14
> **peakshysteria said:**
> Not sure this is the right thread, but if I'm wrong i guess a mod can move it to the right place!? Here goes:

Is it possible to install Ubuntu Hardy Heron 8.04 on a USB stick _from Windows or an existing Ubuntu installation_ and run it from [COLOR="Red"]**OSX, Windows or Linux**[/COLOR]? Going on holiday soon and it would be sweet to bring Hardy on my 8 GB OCZ Rally2 :)

No problems.  If you create a persistent boot USB device of Linux (or any OS really), then you should have no problem booting it as long as the computer can boot from a USB device. The existing OS doesn't matter because it never comes in to play. The boot would go straight from bootstrap/BIOS to the USB device and would never even "know" what OS was on the hard drive.

The reason it says it can access that existing hard drive is probably just because Linux knows the file systems of DOS/Windows/OSX and many others and can easily mount them to be accessible.

---

### Post by KingTermite on 2008-07-14
> **peakshysteria said:**
> Thats the requirements for the installation. It really looks like Dreamlinux only can be runned on exsisting linux installs:
I'm guessing you meant this part when you stated this:
> 
Besides, once running from a pen-drive, you will be able to keep your data safe inside it. All you need to do is create folders to store your data, music, videos, you name it. They not only will be accessible inside your Dreamlinux pen-drive Operating System, they can be read in any other computer running any Linux distro. 

If I'm reading it correctly, all thats saying is that you can see the data on the pen drive only from other Linux computers (because it will be formatted in a Linux filesystem - not Windows or OSX). 

The opposite should always be true, you shouldn't have any problem reading the hard drives of the other computers (as Linux can access those file systems), but if you boot in to those operating systems (and not your pen drive version of Linux), then you probably won't be able to see the data on your pen drive as Windows and OSX don't recognize the Linux filesystems. If you boot into a computer running a Linux distro (and not your pen drive Linux), then you can still plug in the pen drive and see the files because the Linux you booted to can read the file system of the pen drive linux stick.

---

### Post by Rallg on 2008-07-14
It is possible to install software in Windows, so that you can read (and copy) a Linux file over to Windows. It is also possible to install a Windows shell extension that allows you to write to Linux.

So, if your reason for using Linux on USB is solely because you think that Windows users won't be able to see your files, then you are out of luck.

Windows and Linux do not usually recongize each others' file permissions, so you usually cannot protect files just by ownership.

---

