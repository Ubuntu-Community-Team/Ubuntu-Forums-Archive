---
title: "Reinstall Windows"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by crazydjdave on 2010-02-16
Hi, I currently have ubuntu however I want to download a program that is only supported by windows. Is their a way that I can re install windows so that I can dual boot or software that I can download so ubuntu can read microsoft programs

Thanks.

---

### Post by PhilGil on 2010-02-16
There are 3 methods for running Windows programs on your computer.  Your choice will depend on the program you are downloading and the resource requirements.

1. Wine, available in the repository, is a program that will allow you to run some Windows apps seamlessly in Ubuntu.

```
sudo apt-get install wine
```Wine works with a number of Windows programs, but it can be tricky to get them as functional as possible.

2. You can install Windows in a virtual machine hosted on Ubuntu

```
sudo apt-get install virtualbox-ose
```Almost all Windows programs (except games requiring 3d rendering) can be run in a Virtualbox Windows install.  If you have a Windows license, this is probably the least painful way to run Windows programs.

3. You can install windows to dual-boot with Ubuntu.  Typically, installing Windows after Ubuntu will make your Ubuntu install temporarily inaccessible.  There are posts on the forum that will help you to get it working again.

---

### Post by crazydjdave on 2010-02-16
thats the sort of answer i needed however need more help on how to do it all. I need step by step instructions cas i dont trust myself!! Wine does not work so i somehow have to reinstall windows! please help guys xx

---

### Post by lindsay7 on 2010-02-17
Look around here, you should be able to find what you want.

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

---

### Post by PhilGil on 2010-02-17
Here is a good tutorial for setting up Windows XP in VirtualBox.  Don't be daunted by the number of steps - it's easier than it looks and doesn't take a lot of time.

[http://www.linuxjournal.com/content/using-windows-xp-virtualbox-linux](http://www.linuxjournal.com/content/using-windows-xp-virtualbox-linux)

---

