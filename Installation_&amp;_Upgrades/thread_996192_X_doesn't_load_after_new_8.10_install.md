---
title: "X doesn't load after new 8.10 install"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by Estesark on 2008-11-28
Hi,

I just installed Ubuntu 8.10 (amd64) on my laptop, which is an HP Pavilion dv5-1060eo with an AMD Turion X2 Ultra 64 processor and an ATI Radeon HD 3450 graphics card. The live CD booted fine. I used it for a while to make sure stuff generally worked, but I didn't install or remove any packages - pretty much the only change I made was to the system clock, I think. Then I installed, using the live installer, and tried to reboot into the new installation. The graphical loading screen - with the Ubuntu logo and the progress bar - came up as expected, but after that I ran into trouble.

The screen displayed a few lines of text that disappeared too quickly for me to see. After that, I got a message something along the lines of "kinit: no resume, booting normally". Then instead of being taken to a GNOME login window, I got the console login window. There was no message of X trying to load or anything.

I tried sudo dpkg --configure -a and rebooted, the same thing happened.

Then I tried startx, and got this output:

```
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux dv5 2.6.27-7-generic #1 SMP Fri Oct 24 UTC 2008 x86_64
Build Date: 24 October 2008 09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (build@crested.buildd)
Before reporting problems, check http://wiki.x.org
to make sure you have the latest version
Module Loader present
Markers: (--) probed, (++) from config file, (--) default setting, (++) from command line, (!!) notice, (II) informational, (MM) warning, (II) error, (MI) not implemented, (??) unknown.
(--) Log file: "/var/log/Xorg.0.log", Time: Fri Nov 28 22:16:50 2008
(--) Using config file: "/etc/X11/xorg.conf"
(EE) Failed to load module "flgrx" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found
giving up.

xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process  (errno 3): Server error.
```

I'm not sure what to do from here. It could be difficult to download anything from the console, because my only means of internet access is a 3G Mobile Broadband connection run through a USB stick. I don't know how to connect to it manually.

What should I do? The only advice I have found so far is to do what I have already done (with dpkg and startx), and I'm hesitant to follow any other guides because none of them seems to match my situation very well. I fear I would make things worse. I'd rather try and get help from the experts (that's you :)).

Any help would be much appreciated. Thanks in advance.

PS: I wasn't sure whether to post this thread in "Hardware & Laptops", "x86 64-bit Users" or this forum, so please move it if I got it wrong.

---

### Post by ghostworkz on 2008-11-28
Run lspci and look the the bus id or pci id of your video adapter.  When you find it, edit your xorg.conf and add it under your devices.  Should look like this:

```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

```

---

### Post by Estesark on 2008-11-28
Thanks, I'll try that. What can I use to edit it though - nano?

---

### Post by ibutho on 2008-11-28
You can use any editor you like. If you are comfortable using nano, then go ahead and use it.

---

### Post by Estesark on 2008-11-28
What I meant was, which text editors are available from the console in a default installation? I've only really used Gedit before, which obviously can't be used in this situation.

---

### Post by sadiqdude on 2008-11-28
u can edit it using vi in command line or in the terminal type > vi 'filename' the required file will be opened for u
and then u can change the contents of the file by pressing key 'i' after making changes press esc key and then 'wq' enter the file will be saved and modified..........:):):)

---

### Post by sadiqdude on 2008-11-28
vi is very powerful editor ubuntu has vim in it...vi editor can be used in gui or commandline it is flexible too:popcorn:

---

### Post by ghostworkz on 2008-11-28
Any text editor will work.  Nano, pico, or vi.  My boss rags on me because I like to use nano.  It's simple and to the point.

---

### Post by Estesark on 2008-11-29
Well, I tried following the advice that was given, but it wasn't straightforward.

First of all, "lspci" produced too much output for one screen, and I couldn't work out a way to scroll. As my graphics card wasn't visible, I had to look in the list of PCI vendors to find ATI's ID, which is 1002. Then I could use lspci -d 1002:* to show only the ATI products, which brought up my graphics card and its relevant details.

Then I edited xorg.conf as best I could, although I wasn't quite sure what to put for "driver" - I just put "ATI" in the end, which presumably wasn't right. Then I tried "startx" again, same problem. Tried rebooting, same problem.

In the end I figured it might be easier just to try a fresh install, so I popped in the CD and selected "Install Ubuntu" from the menu, rather than "Try Ubuntu without touching your computer" as I had before. That way I could be sure that I wouldn't mess anything up, and I could make sure that it wasn't just a problem with the installation.

Well, it worked, and I'm posting this from within Ubuntu now. I haven't tried enabling the restricted 3D driver yet, but at least the open source one seems to be working fine.

Thanks for the help, guys.

---

