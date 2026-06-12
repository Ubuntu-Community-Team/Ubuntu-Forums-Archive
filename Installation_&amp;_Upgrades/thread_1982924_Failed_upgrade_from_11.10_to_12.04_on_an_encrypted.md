---
title: "Failed upgrade from 11.10 to 12.04 on an encrypted filesystem"
date: 2012-05-19
forum: Installation &amp; Upgrades
---

### Post by loksiz on 2012-05-19
Okay, so I was running Ubuntu 11.10 with a dm-crypt/LUKS  encrypted file-system and just tried to update to 12.04 with the Update  Manager.


  It downloaded all the necessary packages and started installing them and suddenly got this error with libc6 : [http://askubuntu.com/questions/129757/im-upgrading-to-ubuntu-12-04-and-the-installation-is-stuck-at-preparing-libc6](http://askubuntu.com/questions/129757/im-upgrading-to-ubuntu-12-04-and-the-installation-is-stuck-at-preparing-libc6)

[URL="http://askubuntu.com/questions/129757/im-upgrading-to-ubuntu-12-04-and-the-installation-is-stuck-at-preparing-libc6"]
[/URL]
  Because of this, I had a reboot in the middle of the upgrade because it clearly seemed to have completely crashed.


  After that, I can no longer boot Ubuntu. It asks me for the password  to open the encrypted partition, says it's successful and I get the boot  screen with the dots looping over and over again. The recovery mode  doesn't work at all.


  I tried booting on a 12.04 live CD to check if my partition was still  there. It is but I can't seem to open it. (I don't know if the  partition is corrupted or if it's because the live CD is unable to open  it).


  Anyway, I'm stuck and I fear I might have to format and reinstall everything (which I do not want to do).


  Doesn't anybody have any pointers? Any tips? Any help would be greatly appreciated at this point. Thanks.

---

### Post by nothingspecial on 2012-05-20
*Thread moved to **Installation & Upgrades**.*

---

### Post by loksiz on 2012-05-20
Okay, so I eventually found a way to solve my problem with this:
[http://askubuntu.com/questions/125649/reboot-during-update-glibc-error/126542#126542](http://askubuntu.com/questions/125649/reboot-during-update-glibc-error/126542#126542)

Here's what I did to restore the upgrade process:

Boot from a live CD, start a terminal (Ctrl + Alt + T) and do the following commands:

sudo -i


apt-get install lvm2

Then, go to the file explorer (Nautilus) and mount the hard drive in question, which should give you a path to it as /media/[random set of letters and numbers]/

Then, go back to the terminal and do the following commands:

cp /lib/x86_64-linux-gnu/libc-2.15.so [path to your hard drive which you can determine from Nautilus]/lib/x86_64-linux-gnu/


cd [path to your hard drive which you can determine from Nautilus]/lib/x86_64-linux-gnu


rm libc.so.6


ln -s libc-2.15.so libc.so.6


cd /mnt


mount -t sysfs sys [path to your hard drive which you can determine from Nautilus]/sys


mount -o bind /dev [path to your hard drive which you can determine from Nautilus]/dev


mount -t proc proc [path to your hard drive which you can determine from Nautilus]/proc


chroot [path to your hard drive which you can determine from Nautilus]


ls # make sure ls does not complain about libc!


apt-get -f install


apt-get dist-upgrade



At some point, one of the apt-get might "fail" and ask you to do a "dpkg --configure -a". Do it as it solves the problem.

Then, you should be able to reboot. Run "Additional Drivers", "Computer Janitor" and "Update Manager" and you should be good to go. At least, it worked for me.

---

