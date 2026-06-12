---
title: "Upgrade from 10.10 to 11.04 failed - can't get to the desktop"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by Veikko on 2011-04-28
Hey,

I used Kubuntus kpackagekit to upgrade to natty. The process started well, it downloaded everything and started to install 11.04. But then all of a sudden during Installing stage I got this error message: 

"Distribution upgrade process exited with code 1"

and 

"Your system might be unusable".

And it sure is unusable because after reboot I can only see Kubuntu 10.10 loading screen and 

"The disk drive for / is not ready yet or not present".

There also are options for either skip mounting or manually mount hard disks. I don't have a clue how to manually mount... I get same message if I try to boot to safe mode. Does this mean I have to go to clean install? I really don't want to do that because last time it took a couple of months to get ubuntu to co-operate well enough with my laptop.

Luckily win7 still works so that I can ask help from Ubuntu community!

---

### Post by gusman21 on 2011-04-29
> **Veikko said:**
> Hey,

I used Kubuntus kpackagekit to upgrade to natty. The process started well, it downloaded everything and started to install 11.04. But then all of a sudden during Installing stage I got this error message: 

"Distribution upgrade process exited with code 1"

and 

"Your system might be unusable".

And it sure is unusable because after reboot I can only see Kubuntu 10.10 loading screen and 

"The disk drive for / is not ready yet or not present".

There also are options for either skip mounting or manually mount hard disks. I don't have a clue how to manually mount... I get same message if I try to boot to safe mode. Does this mean I have to go to clean install? I really don't want to do that because last time it took a couple of months to get ubuntu to co-operate well enough with my laptop.

Luckily win7 still works so that I can ask help from Ubuntu community!

Upgraded my server "sudo do-release-upgrade"
sane result.

---

### Post by Anony-X on 2011-04-29
i got this after my computer rebooted mid upgrade, unsure on a fix, im just downloading the live cd and hoping i can upgrade the damaged drive that way

---

### Post by milasudril on 2011-04-29
The same happened to me. I tried the new live-cd and it did not mount the disk drive i planned to reinstall to. It is an USB drive. When i looked at the live-cd start-up log i have got the message "USB device descriptor error read/64 -110" if that is a clue. Luckly i could reinstall 10.04.

---

### Post by Veikko on 2011-04-29
I successfully upgraded Ubuntu using Ubuntu live-cd with USB-stick. Now there isn't folder view anymore in the kde plasma desktop. Compiz doesn't work at all anymore neither does my brightness control... All gtk-based applications like firefox and ubuntu software center are really slow (well okay those were slow in maverick also. I don't know what broke them a couple of weeks ago). The kpackagekit and several widgets including weatherwidget are missing. 

Maybe I should revert back to the maverick... Atleast I know what to do in the weekend!

PS. Unity looks nice.

---

### Post by CentralCaFan on 2011-04-29
I had the same issue it seems... in an upgrade attempt from Maverick with Kubuntu. Ending in an error in the installation phase of the upgrade, I remember specifically the message ""Your system might be unusable". I rebooted and saw only kubuntu loading screen template. There was a prompt indicating problems with mounting hard disk. After another attempt to reboot the result was bootloader screen but that could only send me to the root login prompt.
 
Fortunately, backed up everything just prior to upgrade attempt so relying on the backup now and then a clean installation.

---

### Post by ricardisimo on 2011-04-29
I've got a bad extra internal storage drive in my machine, that I didn't even think about when I clicked on the upgrade to 10.04. Now the upgrade manager is stuck on "Installing the upgrades", and just keeps saying over and over again "cannot read from '/dev/sdb/". We're going on a full day at this point.

Any way to interrupt it? I tried CTRL+C, but it warned me that this would leave the system "in a broken state". I'm on regular Ubuntu, 10.10 fully updated, not KDE.

---

### Post by milasudril on 2011-04-30
Kernel bug?

---

### Post by glentrobfc on 2011-05-01
Actually  did this as an install.  HP netbook with windows 7, Linux Mint 10, 11.04 ubuntu beta-2, and fusion installed in sda7.  The 11.04 beta-2 (gnome) is ext3 mounted as / in sda8 with /home in sda9 formatted btrfs.
I installed the release kubuntu 11.04 into /dev/sda7 formatted btrfs mounted as /.  I mounted /dev/sda9 as /home (without format).  I installed grub into the mbr (/dev/sda).

When I boot I initially get a n error message from grub2 "error: sparse file not allowed - press any key'.  If I either just wait 10 seconds or press any key it proceeds to boot into kubuntu and I get the login window in KDE.

Attempting to login I enter the password and get a small blank white screen which flashes on for about 3 seconds and then I am back at the login window.  If I choose to do a console login I can do that successfully.
I have access to all of my normal /home stuff (Documents, etc.) and everything looks okay.  I can startx there successfully, but if I exit I will eventually get back to the login window prompt at which point I can't login.

I even tried changing passwords from the console login, just in case there was some linkage issue with whatever the KDE login window was using for password.  That did not change the behavior, I still cannot login to KDE.

Any ideas?

---

### Post by ricardisimo on 2011-05-06
I was able to grab all of my indispensable files via the LiveCD and a very large flash drive. Then I pulled out the bad storage disc and did a fresh install.

Unity sucks, by the way. I'm going to give it another couple of weeks to see if I get used to it, but so far it is the definition of failure: less options and yet more difficult to operate. How does one beat that? Charge for it, maybe.

---

