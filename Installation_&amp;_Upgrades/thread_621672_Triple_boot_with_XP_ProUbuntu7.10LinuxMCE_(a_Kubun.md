---
title: "Triple boot with XP Pro/Ubuntu7.10/LinuxMCE (a Kubuntu distro)"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by frekimedia on 2007-11-23
So here's my situation...I want to set up the an install of Windows XP Pro (SP2), Ubuntu 7.10 Server Ed., and LinuxMCE 0704 (which is a Kubuntu distro). I've never been able to get a dual- or triple-boot to work. I'd prefer to have GRUB so I can choose which install to use every time i start up. 

I'll be fresh installing all of these OSs on a 120GB hard drive with a second 40GB drive for storage/backup purposes. What would be the best way to go about doing this? Thanks in advance for your help.

---

### Post by Mithrilhall on 2007-11-24
XP first, and I would install the distro you plan on using the most last. Both Linux distros should detect the other OSs on the system and make the appropriate changes to GRUB for you.

---

### Post by frekimedia on 2007-11-24
How do you set up the GRUB boot-loader after the installs?

---

### Post by meierfra on 2007-11-24
Unless something goes wrong,  grub will be set up automatically. You might want to disconnect the 40GB  hard-drive while installing the OS's  to avoid confusion.

---

### Post by frekimedia on 2007-11-25
I think my problem was that in the past I've installed Windows last. installing Ubuntu last worked perfectly.

I think now that I've done all this I want to do away with the Ubuntu server (no GUI, and I kind of need that on this box) and just do a dual-boot with XP and Ubuntu 7.10 Desktop ed...maybe Kubuntu later on.

---

### Post by chattanoga on 2007-11-26
> **frekimedia said:**
> So here's my situation...I want to set up the an install of Windows XP Pro (SP2), Ubuntu 7.10 Server Ed., and LinuxMCE 0704 (which is a Kubuntu distro). I've never been able to get a dual- or triple-boot to work. I'd prefer to have GRUB so I can choose which install to use every time i start up. 

I'll be fresh installing all of these OSs on a 120GB hard drive with a second 40GB drive for storage/backup purposes. What would be the best way to go about doing this? Thanks in advance for your help.

I borrow this thread.
I did almost exactly the same install.
I have XP and Ubuntu 7.04 on HDA, and installed LinuxMCE on HDB (just bought it and inserted it for this occation, ie the HD was not formated).
The install went fine but when I reboot without the DVD, LinuxMCE does not show up in Grub.
Any suggestions?

Edit:
Just looked at my BIOS and the HDs are listed something like this:
IDE channel 0 (master) Hitachi ..... 320Gb
IDE channel 0 (slave)  Maxtor ......  250Gb
Should I try to move the new HD to another MoBo connector?


Edit2: When I changed the boot-order to start with the Maxtor (the new HD) it booted fine into LinuxMCE but gave me no other choices.
Maybe I would be better of first installing Kubuntu, and putting LMCE on top when everything works (video card, etc..)?

---

### Post by dragon_788 on 2007-11-28
The problem is you have two separate grub installs. What you'll want to do is on the first (dual OS) drive add a new grub entry that points to the 2nd drive (which will then load grub and after a small delay go into LinuxMCE). Drives are referenced as hd0, hd1 etc with hd0,0 being the first partition on the first disk and hd1,0 being the first partition on the 2nd disk.

---

### Post by dragon_788 on 2007-11-28
frekimedia, don't "do away with" your Ubuntu server edition install, just install a GUI on it. apt-get install kdesktop or gnome-desktop should do the trick (Google for better instructions).

---

