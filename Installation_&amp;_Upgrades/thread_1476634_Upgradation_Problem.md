---
title: "Upgradation Problem"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by rmaries on 2010-05-08
Hi 

I try to upgrade from 9.10 to 10.04. While installation power went off. So system got switched off. While switching on the system again I cant able to log into linux gui. I can log into the recovery mode.

I tried to upgrade from there it is showing gtk error.

I had alternate image file in my downloads folder

Can anyone help me resolve the issue without formatting the system.

Thanks
Maries

---

### Post by nikefalcon on 2010-05-08
If you have a separate partition for /home, all you have to do is reinstall on the primary partition.

[]("http://ubuntuforums.org/showthread.php?t=1475611")

---

### Post by Catharsis on 2010-05-08
Try running the following in a terminal:
```
sudo apt-get update
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get dist-upgrade
sudo apt-get install ubuntu-desktop
```

Edit: Do you mind posting any and all error messages you get too?

---

### Post by nikefalcon on 2010-05-08
check out this thread:
[http://ubuntuforums.org/showthread.php?t=1475611](http://ubuntuforums.org/showthread.php?t=1475611)

---

### Post by rmaries on 2010-05-08
Hi Catharsis 

I tried with the commands you told. the error message coming is E:method cdrom has died unexpectedly
E:Sub-process cdrom returned an error code(127)

while i tried to login in the recovery mode error message coming is
E: BrokenCount >0run-parts: /etc/update-motd.d/90-updates-available exited with return code 255

Regards
Maries

---

### Post by Catharsis on 2010-05-08
Which command produced the error? Try running the commands a couple times all the way through. Also note that I changed 'upgrade' to 'dist-upgrade' above; running "sudo apt-get dist-upgrade" might fix the problem.

If you can't get to a terminal, hold down Shift while you boot to get the grub menu. From there, select your kernel with "(recovery mode)" at the end, and then select "root shell with networking". In this case, you don't need "sudo" in the commands.

You should also check
```
cat /etc/apt/sources.list
```
and make sure the lines have "lucid" and not "karmic".

---

