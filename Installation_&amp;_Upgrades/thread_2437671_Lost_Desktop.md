---
title: "Lost Desktop"
date: 2020-02-27
forum: Installation &amp; Upgrades
---

### Post by angel mike on 2020-02-27
I have lost the Desktop trying to remove a .dbus file so I just get a a Title: 'Ubuntu  18.04' (etc) then next 2 lines 'login' and 'password ' have Dell XPS13

---

### Post by goinglinux on 2020-02-27
It's possible that you accidentally got to a virtual terminal. If the line you described as 'Ubuntu 18.04' (etc) also includes the letters 'tty' followed by a number, you can try this key combination to get back to the desktop: Press Ctrl+Alt+F7 all at the same time.

---

### Post by angel mike on 2020-02-28
Thanks for replying Larry - the key comb did not work - just a series of symbols. If I login it gives the welcome lines and info on docs/management/support  web sites.I am trying to getDell to confirm how I boot with a usb or dvd.  In the bios it says add a boot mode but no option for these two modes.

---

### Post by angel mike on 2020-02-28
Just to add it does say I last logged in on tty1
Mike

---

### Post by CelticWarrior on 2020-02-28
It's CTRL+ALT+F7

---

### Post by goinglinux on 2020-02-28
Thanks for the correction. I'll edit my post for the typo in case someone else runs across it.

---

### Post by oldfred on 2020-02-29
With a Dell it is normally f12 to get UEFI/BIOS boot menu. That will show bootable devices. If booting an Ubuntu live installer on flash drive and newer UEFI based hardware you should have two boot options, one "UEFI:name" and one "name" where second is BIOS boot. And name is name or label of flash drive.

I seems like you are booting in recovery mode. That is normally the second grub boot menu entry. Or as mentioned above changed grub to boot just to a terminal.

If you do not get grub menu, press escape right after Dell logo, if UEFI or hold shift key right after Dell logo if BIOS.
And then boot recovery mode to get to a terminal. 
Recovery mode as a menu of options.

---

### Post by angel mike on 2020-03-01
Thanks for all the responses,
The  CTRL+ALT+F7 does not produce anything.
So I am intending to reload Ubuntu from an external USB or CD,
On this Dell XPS13 7390 the BIOS has no provision for booting an external drive only the GRUB2 .
Using f12 produces a list of Boot Settings which do not include an external boot option
Ubuntu
UEFI  PC601.......YB050 1 2
UEFI PC601........YB050 1
Linux Firmware Updater

The BIOS boot sequence selection does have the option to add another one but not external drives.
At the moment the booting is done by the BIOS so I need to change to the GRUB2 Boot Loader - but the /sys/firmware/efi folder is missing which would contain vnlinuz and intrd* files.
I cannot understand why Dell ships a Ubuntu 18.04 version without making the facility of booting from external drives readily available. I am in touch with Dell Technical but they seem to be be Windows orientated !
Thanks for the link Oldfred which I will look at but doubtful if it will be useful.

---

### Post by ajgreeny on 2020-03-01
Have you any idea what those two entries in the F12 boot menu are; have you tried selecting and booting from them, and if so what happens?
> UEFI PC601.......YB050 1 2
UEFI PC601........YB050 1

---

### Post by oldfred on 2020-03-01
Dell has essentially same UEFI across many similar models. So these are all users with Dell & what they did.

Dell 7791 UEFI update & some settings
[https://ubuntuforums.org/showthread.php?t=2431450&page=3](https://ubuntuforums.org/showthread.php?t=2431450&page=3)
Ubuntu 19.10 Provides Good Out-Of-The-Box Support For The Dell XPS 7390 Icelake Laptop
[https://www.phoronix.com/scan.php?page=article&item=dell-xps7390-ubuntu1910&num=1](https://www.phoronix.com/scan.php?page=article&item=dell-xps7390-ubuntu1910&num=1)
[https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-7390-More-Options](https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-7390-More-Options)
[https://wiki.ubuntu.com/Dell/XPS/XPS-13-7390-2-in-1](https://wiki.ubuntu.com/Dell/XPS/XPS-13-7390-2-in-1)
[https://ubuntuforums.org/showthread.php?t=2431791](https://ubuntuforums.org/showthread.php?t=2431791)
Dell XPS 15 Series 7590 (2019)
[https://askubuntu.com/questions/1161456/how-to-run-ubuntu-on-new-dell-xps-15-7000-series-7590](https://askubuntu.com/questions/1161456/how-to-run-ubuntu-on-new-dell-xps-15-7000-series-7590)
[https://github.com/TillmannBerg/Ubuntu-Dell-XPS-15-2019](https://github.com/TillmannBerg/Ubuntu-Dell-XPS-15-2019)

Dell XPS 15 Intel
[https://github.com/TillmannBerg/Ubuntu-Dell-XPS-15-2019/blob/master/README.md](https://github.com/TillmannBerg/Ubuntu-Dell-XPS-15-2019/blob/master/README.md)

---

### Post by angel mike on 2020-03-01
Thanks ajgreeny - the first is a safe recovery mode which gives a series  of lines that could  not find items and finally 
Initramfs Unable to find a medium containing a live file system .The second just gtes to the login and pssword screen with tty in the top right.. 
I am now looking through oldfred's extensive list! Thanks oldfred

---

### Post by angel mike on 2020-03-03
No joy so far but I have found a promising  lead on this [https://www.techwalla.com/articles/how-to-reinstall-ubuntu-via-command-line](https://www.techwalla.com/articles/how-to-reinstall-ubuntu-via-command-line)
But for some reason entering the command in the tty screen:sudo dpkg-reconfigure -phigh-a  does not work - command not found. Does anyone know why?

---

