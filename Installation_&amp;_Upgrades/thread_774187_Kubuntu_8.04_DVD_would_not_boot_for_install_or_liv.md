---
title: "Kubuntu 8.04 DVD would not boot for install or live"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by Kdar on 2008-04-29
I burned the Kubuntu 8.04 DVD. Restarted computer and got to the Kubuntu menu (where it say: live version, install, boot from hard drive... etc)

However, I can not install or even do live run of Kubuntu.

When I click those two options.. It seem to be loading.. But then.. It print out some error(s).

This error say something like this: type 'help' for list of commands, and it also prints error messages about every 5 sec....

What can I do? I want to install Kubuntu 8.04.. But with this weird problem I am not sure how can I do it.

---
My specs.
Q6600
8800GT
2GB RAm
etc..

---

### Post by dstew on 2008-04-29
Check the CD integrity first (menu item I think). If it checks out OK, it might be that the Live CD software has some problem running your hardware. If that is the case, you can try the Alternate Install CD. You get it from the same Ubuntu download page, check the box beneath the Start Download button. It installs the same Ubuntu desktop system, but uses a text-based installer that is easier on your system and might work better.

---

### Post by Kdar on 2008-04-29
I tried to do DVD check as well, but I get the same error.

PS. There is what I get
> "BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)"

Another thing..
Today I try to boot and tried to start installation  Ubuntu and it seemed to work. Both live demo and installation were able to start without any problems.

However.. I still want to install using Kubuntu DVD...

---

### Post by dstew on 2008-04-29
The error you get means that the CD's linux kernel was unable to load and/or execute, so it drops you to the BusyBox command line, which is the command line of a tiny initial RAM file system. It could mean the disk is bad, or your hardware is incompatible with the linux kernel on the disk.

Did you check the md5 sum of the .iso before you burned it?

---

### Post by Kdar on 2008-04-29
hmm I am sorry.
But how can I check md5 of that ISO file?

All I have is ISO file of that DVD.. and thats all. (I downloaded using torrents)

---

### Post by lemming465 on 2008-04-29
> But how can I check md5 of that ISO file?
Compare it to the MD5SUMS file at the site you got the torrent file from.  For bonus points, verify the detached GPG signature :)

Also, if Ubuntu live desktop is running OK, but the Kubuntu DVD is causing problems, what you could do is:

1. install ubuntu
2. use *sudo apt-cdrom* to register your Kubuntu DVD (minimizes downloads if it's readable)
3. use *sudo apt-get install kubuntu-desktop* to add Kubuntu.  Or kubuntu-kde4-desktop if you prefer bleeding edge stuff.  The -desktop packages are meta-packages which depend on the real stuff, so that it will be easy to install.

I routinely run with both ubuntu-desktop and kubuntu-desktop installed, as I like some of the applications from both camps.

---

