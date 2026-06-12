---
title: "Ubuntu 9.10 doesn't boot after install!"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by RaptorZX3 on 2010-01-05
I had an old Ubuntu installed, and i had an ATI video card at the time, but since i switched to Nvidia video card, it wasn't working at all, so i wasn't able to do anything at all.

Now here's what i've done since i downloaded Ubuntu 9.10:

1- erase both Linux partitions (swap and ext3)
2- install Ubuntu 9.10
3- reboot my computer

now at this point, it was showing "GRUB 1.5" loading and telling me "error 15" and it wasn't able to boot at all.

After checking on the net, i found a way to delete the old GRUB 1.5 from the boot sequence (the "fixmbr" command when using WinXP CD and pressing R for Repair command lines)

So i did the FIXMBR command and now Windows XP boot as it should. After that, i erased both partitions again (i use about 12gb of hard disk space for Ubuntu) and re-installed Ubuntu 9.10. After installation, it rebooted my computer, but there was no GRUB menu to let me choose which OS to load!

Now how could i fix this problem?

thank you for helping me!

---

### Post by drs305 on 2010-01-05
> **RaptorZX3 said:**
>  After installation, it rebooted my computer, but there was no GRUB menu to let me choose which OS to load!

Now how could i fix this problem?

thank you for helping me!

That is the new default behavior of Grub 2 on the initial install. To view the menu, open this file for editing:
```
gksu gedit /etc/default/grub
```

Put a # symbol in front of this line to force the menu to be displayed:
> **[COLOR="Red"]#[/COLOR] **GRUB_HIDDEN_TIMEOUT=0
Note the default time is shown in "GRUB_TIMEOUT" if you want to change it.
Save the file, then run this command to update the menu:
```
sudo update-grub
```
Reboot.

For other common tasks in Grub 2, refer to this link:
[Grub 2 - 5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")

Click on any of the G2 links in my signature line to learn more about Grub 2.

---

### Post by RaptorZX3 on 2010-01-05
ok i booted a "tryout" of Ubuntu from the CD, opened that file, but the # symbol is already there on this line, but it doesn't show the GRUB menu when my computer boot-up, it goes directly in WinXP without any menu, and i can't remove the # symbol and can't save...it says i don't have the rights.

---

### Post by drs305 on 2010-01-06
> **RaptorZX3 said:**
> ok i booted a "tryout" of Ubuntu from the CD, opened that file, but the # symbol is already there on this line, but it doesn't show the GRUB menu when my computer boot-up, it goes directly in WinXP without any menu, and i can't remove the # symbol and can't save...it says i don't have the rights.

Your first post seemed to indicate you can boot normally into Ubuntu but can't see the menu. You would not try to fix this from the LiveCD since your Ubuntu installation is performing the way it was designed to. 

Boot normally, when you get into Ubuntu, run this command from a terminal (Applications, Accessories, Terminal):
```
gksu gedit /etc/default/grub
```
Then modify the file as previously discussed, save it and reboot.

The two lines should look like this:
> 
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"


---

### Post by RaptorZX3 on 2010-01-06
no, right now i CAN'T get into Ubuntu. If i let my computer boot up normally without any CD in my drive, it goes in Windows XP automatically without any GRUB menu.

Why does the GRUB 2.0 doesn't automatically install itself with Ubuntu 9.10?

---

### Post by drs305 on 2010-01-06
> **RaptorZX3 said:**
> no, right now i CAN'T get into Ubuntu. If i let my computer boot up normally without any CD in my drive, it goes in Windows XP automatically without any GRUB menu.

Why does the GRUB 2.0 doesn't automatically install itself with Ubuntu 9.10?

It may be booting through the GRUB 2 menu without displaying anything - if that is the case hold down the SHIFT key during boot to see if the GRUB 2 menu appears. If it does, see if there are any Ubuntu options. Try one to see if it boots into Ubuntu. If you get into Ubuntu, edit the menu file as indicated in the previous post. YOu can also change the "DEFAULT=" entry to point to the Ubuntu kernel you want to boot. Count the "menuentry", starting with 0. 

If no GRUB 2 menu appears, reinstall GRUB 2 from the LiveCD. 
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by RaptorZX3 on 2010-01-06
i tried holding SHIFT and it doesn't work. So my guess is i will have to re-install GRUB2...

---

