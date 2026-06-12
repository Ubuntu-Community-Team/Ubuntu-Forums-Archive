---
title: "Upgraded Ubuntu 10.10 won't go past login terminal"
date: 2010-12-12
forum: Installation &amp; Upgrades
---

### Post by johnykilunda on 2010-12-12
[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]Hello,

I've just upgraded to Ubuntu Maverick 10.10 yesterday from Lucid 10.04. After the completion of the upgrade, I rebooted the machine to login to the desktop.

After selecting the new version from the GRUB menu, the screen goes to the usual black screen where it says, "Starting...".

After a while, the plymouth purple boot screen flashes for a split second, as if it failed to initialized, and it reverts back to the black screen. Then, a **ttyl prompt** appears and the boot just stops there.

If I press Ctrl+Alt+F7, I see another black screen, with text showing the progress of the startup, where it usually ends (but not all the time) after Starting Winbind, or something along those lines.

I've also tried 
1. sudo service gdm stop
    sudo service gdm (re)start

2. sudo rm /etc/X11/Xorg.conf
    sudo dpkg-reconfigure -phigh Xserver-xorg
    sudo shutdown -r now

3. sudo Xorg -configure
    sudo mv Xorg.conf.new /etc/X11/Xorg.conf
    sudo reboot

4. sudo apt-get remove --purge Xserver-Xorg
    sudo apt-get instal Xserver-Xorg
    sudo dpkg-reconfigure Xserver-Xorg
    sudo apt-get install ubuntu-desktop
    sudo reboot

One after the other but all take me back to terminal.

Before this, I have not had boot problems with 10.04 and everything has worked well until now. Any help would be greatly appreciated. Thanks in advance.[/FONT][/FONT][/COLOR]

---

### Post by karthick87 on 2010-12-12
Pls post the output of,

```
cat /etc/default/grub
```

---

### Post by johnykilunda on 2010-12-12
> **karthick87 said:**
> Pls post the output of,

```
cat /etc/default/grub
```


GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2>/dev/null ::echo debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=""

#GRUB_BADRAM="0X01234567,0Xfefefefe,0x89abcdef,0xefefefef"

#GRUB_TERMINAL=console

#GRUB_GFXMODE=640x480

#GRUB_DISABLE_LINUX_UUID=true

#GRUB_DISABLE_LINUX_RECOVERY="true"

#GRUB_INIT_TUNE="480 440 1"

---

### Post by karthick87 on 2010-12-12
Change this line,
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"
to,
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

---

### Post by johnykilunda on 2010-12-13
Thank you!

I miss the purple screen tho'

---

