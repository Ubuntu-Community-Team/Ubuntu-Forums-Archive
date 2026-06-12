---
title: "Downloaded software can only access home folder"
date: 2019-10-19
forum: Installation &amp; Upgrades
---

### Post by nano.ge on 2019-10-19
Hi.

I'm fairly new to Ubuntu and Linux in general. I've got Ubuntu 19.04 installed along Windows 10. OS is great, and fills all my needs and more.
Only one thing: I've noticed that only software downloaded and installed through Ubuntu Software app can access all volumes and drives in my computer, but anything that was downloaded from any other source only can access the /home folder. 
I suppose it's a security thing, but I'm not savvy enough to figure out a workaround by myself. There are some programs from reputable sources (Blender, GIMP, Inkscape), though being present in Ubuntu Software they are mostly outdated versions. 
Can programs be "flagged" to access locations other than the /home folder?

Thanks in advance and sorry if my english leaves a lot to be desired.

Nano

---

### Post by TheFu on 2019-10-19
Welcome to snap packages.  If you avoid snap packages, all will be well, as far as this issue is concerned.  Snaps aren't all bad and there might be a workaround, but I don't know what it is. I've been able to completely avoid all snaps by staying on 16.04.
If you avoid "Software Center" when looking to install packages, that is a way to completely avoid snaps, except for  at install time packages.  Synaptic is the older GUI package installation tool.  Or you can use the shell/terminal to install packages.

If you want to try and relax the constraints on snaps, [https://ubuntu.com/blog/a-guide-to-snap-permissions-and-interfaces](https://ubuntu.com/blog/a-guide-to-snap-permissions-and-interfaces) is a guide.  [https://askubuntu.com/questions/1033344/how-to-give-snaps-access-to-somedir](https://askubuntu.com/questions/1033344/how-to-give-snaps-access-to-somedir) has a snapd developer responding to a question about this.

---

### Post by Impavidus on 2019-10-20
Software installed from snap packages (as opposed to deb packages) is limited in what directories it can access. This is for security. Snaps are designed to allow software creators to distribute the software to Ubuntu systems without Canonical (the company behind Ubuntu) or the Ubuntu community being involved. As this software is less trusted, it's more limited in what it can do. As it isn't integrated into the entire system, it's bundled with all dependencies, making less efficient use of disk space and memory. I think you can configure per snap which locations it can access, but I never tried to find out how. I don't use any snaps on 19.04.

As you've seen, the same software is available as deb packages from the official repositories. For most software (Firefox being a notable exception), the versions are fixed shortly before the Ubuntu version is released and stay the same for as long as that Ubuntu release is supported. That means that by now the software on Ubuntu 19.04 is about 7 months outdated. For most uses that shouldn't really be a problem. Important bugfixes, in particular security fixes, are backported, so it won't be any less secure.

If you want the latest releases of all software at once instead of next April/October, or if you want to use LTS releases and for particular software you don't want to wait until next April in an even year, you can use [PPAs]("https://help.ubuntu.com/community/PPA"). Those provide deb packages from alternative sources, outside the official Ubuntu repositories. PPAs may provide the latest software sooner, but are less secure and may destabilise your system.

---

