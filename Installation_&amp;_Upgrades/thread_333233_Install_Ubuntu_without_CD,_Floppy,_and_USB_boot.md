---
title: "Install Ubuntu without CD, Floppy, and USB boot"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by DarkNemesis618 on 2007-01-07
I have a Toshiba laptop that I want to install Ubuntu on, but here's the issue.  The laptop has no CD-ROM, Floppy Drive, and I can't boot from a USB CD-ROM, floppy or even a thumb drive.  ](*,)  Does anyone know of a method that would allow me to install it?  It currently has Windows XP on it but I really don't want XP, I want Ubuntu.  Any ideas?  Thanks.

---

### Post by Koybe on 2007-01-07
You can put an external floppy/cdrom drive to install it.
Or if the network card permit it, maybe you can go for a PXE boot install on a network. But i don't know how to proceed exactly, you'll have to search the forum/web ;)

---

### Post by justifier on 2007-01-07
a hard drive install? take the ard drive out the laptop, if possible, put it in another, install it to that, only go to the bit where it asks you to take out the CD, take the CD out and as it reboots switch the machine off, put the HDD back in the laptop, boot up and finish the installation process, thats how i do it on my laptop that has the same problem!!!. i realise its abit of a pain in the backside but, hey, its the only way of doing it.

goodluck!!!

---

### Post by gmc on 2007-01-07
> **Koybe said:**
> You can put an external floppy/cdrom drive to install it.
Or if the network card permit it, maybe you can go for a PXE boot install on a network. But i don't know how to proceed exactly, you'll have to search the forum/web ;)

I sincerely doubt this would be an viable option. If the machine in question doesn't support booting from floppy/cdrom/usb-drive, it probably won't support PXE network booting.

Unfortunately, it sounds like hooking the drive up to a machine that does support one of the above options would be the only way to install any alternate operating system.

Gord

---

### Post by gmc on 2007-01-07
> **DarkNemesis618 said:**
> I have a Toshiba laptop that I want to install Ubuntu on, but here's the issue.  The laptop has no CD-ROM, Floppy Drive, and I can't boot from a USB CD-ROM, floppy or even a thumb drive.  ](*,)  Does anyone know of a method that would allow me to install it?  It currently has Windows XP on it but I really don't want XP, I want Ubuntu.  Any ideas?  Thanks.

What model of Toshiba laptop is this?

As I see it, you have a couple of options here. Take the harddrive out of the laptop and hook it upto another laptop that does support booting from an alternate source, or if you have the ram for it (at least 512 megs), download [vmware for windows]("http://www.vmware.com/download/server/"), and a copy of [ubuntu vmware image]("http://www.vmware.com/vmtn/appliances/directory/648") and run the system that way.

Gord

---

### Post by marktechey on 2007-01-07
If you have an internet connection you can try this. Install instlux on windows xp. Go to the following link to download, [http://sourceforge.net/project/downloading.php?group_id=151507&use_mirror=superb-east&filename=instluxNETUbuntu6_06english.exe&83243983](http://sourceforge.net/project/downloading.php?group_id=151507&use_mirror=superb-east&filename=instluxNETUbuntu6_06english.exe&83243983) 
then install instlux on Windows XP. It should automatically restart your computer, but if it doesn't, you can restart it manually. When your computer reboots you should have the option to install Ubuntu 6.06. Select that, follow instructions. Then, you can upgrade to Ubuntu 10 later if you want to.
     Other ideas are found on the following web page. Under advance.
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by pla7ma on 2007-01-13
the laptop should have netboot possibilities in this case, which will by far be the smoothest thing if you have another linux machine available on your network as a server. Install the server according to this [https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer), make a netboot from the laptop. I installed a machine without cdrom  yesterday like this, I was surprised how easy these things are nowadays.

---

### Post by confused57 on 2007-01-13
Here's another link I had in my bookmarks, never tried it myself:
[http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)

---

