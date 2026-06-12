---
title: "Upgraded to 16.10 cant login"
date: 2016-10-14
forum: Installation &amp; Upgrades
---

### Post by vman762 on 2016-10-14
I manually updated to 16.10 using the sudo function in the terminal after all was complete the system prompts to restart I select y to complete the installation. The system resets I attempt to login and I discover that I can no longer login. It acts as if it's trying to login then it just loops to the main login screen. Please help.

Truly,

A loser

I tried the F1+ctrl like the user did in the similar post but nothing happens my resolution is different (larger) than usual just like the prior post.

---

### Post by vman762 on 2016-10-14
I manually updated to 16.10 using the sudo function in the terminal after all was complete the system prompts to restart I select y to complete the installation. The system resets I attempt to login and I discover that I can no longer login. It acts as if it's trying to login then it just loops to the main login screen. Please help.

Truly,

A loser

---

### Post by Impavidus on 2016-10-15
First try the usual suspect. Sometimes the GUI crashes immediately because it has no write permission in some hidden files in your home directory, sending you back to the login screen. This is usually caused by incorrect use of sudo.

At the login screen, hit ctrl+alt+F2. Use your username and password to login. Then use this command:```
ls -l .Xauthority .ICEauthority
```(that's ell es space dash ell)
It should show something like```
-rw------- 1 username username 9018 okt 15 09:52 .ICEauthority
-rw------- 1 username username   55 okt 15 09:51 .Xauthority
```If it shows **root** instead of your username, fix it with```
sudo chown username:username .Xauthority .ICEauthority
```substituting your username.

Then run```
logout
```and return to the GUI with ctrl+alt+F7.

---

### Post by Gridwalker on 2016-10-15
**EDIT**
Moved to new post (see next comment)

---

### Post by oldfred on 2016-10-15
@vman762
       May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) 

@Gridwalker
Probably best to start your own thread unless issue is exactly the same which is rare.

---

### Post by vman762 on 2016-10-15
Thanks for responding. For some reason that's unknown to me It's not letting me log in there either? I haven't changed my password since I've been using ubuntu. Please advise.

---

### Post by vman762 on 2016-10-15
Thanks for responding! 

Boot info [http://paste2.org/Y7cO6DB7](http://paste2.org/Y7cO6DB7)

---

### Post by oldfred on 2016-10-15
Do not use Boot-Repair's auto fix. That installs grub to both drives.
You want to keep Windows boot loader in sda's MBR and have grub2's boot loader in sdb.
But do use Boot-Repair's advanced options to choose your Ubuntu install and reinstall grub to drive sdb.

But it looks like you have a broken Windows.
Windows only boots from primary NTFS partitions with boot flag, or only primary NTFS partition you have is sda4.
But it does not show all the boot files, you are missing bootmgr & /Boot/BCD. If those files are really there and script just missed then then you are ok. It says it was hibernated, so it may not have been able to see files.
But if missing you need your Windows repair disk to run repairs to readd them.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html) 
    
You also show an old install of wubi. As Boot-Repair mentioned best to houseclean that out.

---

### Post by vman762 on 2016-10-15
The Windows is broken and an old install that I no longer use. Please advise.

---

### Post by oldfred on 2016-10-15
If you reinstall grub boot loader to sdb, can you then boot. 
If simple reinstall of grub to sdb does not work, use Boot-Repair's advanced mode to uninstall/reinstall all of grub. That resets everything.

What video card/chip?
Upgrades do not like proprietary drivers, you have to uninstall all proprietary drivers & ppas before upgrading & then reinstall after upgrading.
If nVidia or AMD that also can be an issue.

---

### Post by howefield on 2016-10-15
Duplicate threads merged.

---

### Post by vman762 on 2016-10-15
I'm using Nvidia GeForce 6800gs

---

### Post by oldfred on 2016-10-15
Not sure what driver is correct for that model, do not download from nVidia, just check for correct version.
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

But you should be able to use nomodeset when booting and then install correct proprietary driver from repository.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by vman762 on 2016-10-15
I tried to reinstall grub using sudo grub-install /dev/sdc5 and I received grub-install: error: failed to get canonical path of `aufs'. Please advise of reinstalling grub

---

### Post by oldfred on 2016-10-15
You do not install grub to a partition, only to a drive.
So not to sdc5, but if you want grub boot loader to boot from sdc
sudo grub-install /dev/sdc
But your install was in sdb per last Boot-Repair info script???

If still errors use Boot-Repair to uninstall & reinstall all of grub in advanced options.

---

### Post by vman762 on 2016-10-15
Boot successfully repaired [http://paste2.org/F17jZLhx....a](http://paste2.org/F17jZLhx....a) broken Wubi was detected should I fix it before the reboot?

---

### Post by oldfred on 2016-10-16
Link does not work.
You have to fix wubi from inside Windows.
Wubi may be un-installed like any app, but many have issues and have to use the manual process.

---

### Post by os2 on 2016-10-16
Why are you repairing the boot loader if you can't log-in?

As others have suggested switch to a tty terminal (CTRL+ALT+F1). Log-in as root. Assuming that the root password has been set. It's always a good idea to have a password and account for root set before doing any system administration.
Once you have logged in check that your user still exists by doing cat /etc/group.

---

### Post by vman762 on 2016-10-23
True...I thought the same thing....anyway I reinstalled...everything works fine....thanks for all of the suggestions.....

---

### Post by os2 on 2016-10-23
That's the Windows way. When in trouble reinstall.

Anyway set a root password. Ubuntu install does not set a password for root by default.

```

# sudo passwd root

```

---

### Post by oldfred on 2016-10-23
Ubuntu & the forum do not recommend a root password only use sudo or you may open system to attack.

 Forum rules on root vs. sudo
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://xkcd.com/149/](http://xkcd.com/149/)

---

### Post by os2 on 2016-10-23
My Ubuntu got attacked last night.

---

