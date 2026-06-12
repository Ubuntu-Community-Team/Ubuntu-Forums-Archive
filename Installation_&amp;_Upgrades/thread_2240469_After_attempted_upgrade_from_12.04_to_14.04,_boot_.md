---
title: "After attempted upgrade from 12.04 to 14.04, boot hangs after entering password"
date: 2014-08-20
forum: Installation &amp; Upgrades
---

### Post by hfinger on 2014-08-20
I have Ubuntu 12.04.4 LTS and Upgrade Manager advised that an upgrade to 14.04.01 LTS was available. Ubuntu 12.04 LTS was completely up-to-date, so I ran the LTS update. However, it froze at update-initramfs (see [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1356033](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1356033) for details).

After leaving the computer for several hours to possibly allow the logjam to break I shut down Ubuntu and reported the failed upgrade. Upon starting up again, the login screen appears but after entering the password, the boot hangs, and I have to use the power switch to shut down.

I downloaded the 14.04 .iso file and booted off it. The options are to install 14.04 as an alternative to the failed 12.04/14.04 upgrade, or completely overwrite the current installation. The latter will wipe all my files and custom installed apps, etc.

So my question is: can you upgrade from a DVD or .iso file while preserving your personal files and custom apps -- without installing an alternative 14.04 OS?
[CENTER][COLOR=#000000]:shock:[/COLOR]
[/CENTER]

---

### Post by tattushenoi on 2014-08-20
Same here. No one seems to have the solution. The problem seems to be that its looking for graphics drivers. If you can install them using terminal somehow it will be solved. But jockey-text doesnt seem to work on 14.04. No idea what to do.

---

### Post by hfinger on 2014-08-20
The problem is that I cannot get to the desktop to open a terminal. Or is there some way of booting into a terminal interface and doing the upgrade via the command line?

---

### Post by tattushenoi on 2014-08-20
You can try failsafe graphics mode. Or the Network enabled mode. But for me both of these failed. Laptop heats up and hangs. I have to force shutdown. If you are able to enter. type in CTRL+ALT+T for terminal. 

Then 
> 
sudo apt-get install ubuntu-drivers-common

Probably this should install the drivers. I am not sure. but please try entering fail safe graphics mode.

---

### Post by tattushenoi on 2014-08-20
Does GRUB appear for you? If yes, then **press 'e'**  on your keyboard. This should take you to grub menu. Go to the second last line using arrow keys [the line before 3.20.67 or what have you] and add '**nomodeset**' at the end. then press CTRL+X. This will reboot your system and you will hopefully be able to login. Once inside do as I said earlier. You will probably need to run 

> sudo dpkg --configure -a

but first run > [COLOR=#000000]*sudo apt-get install ubuntu-drivers-common*[/COLOR] and if the kernel asks to do the previous configure step, only then you do it. 
If [probably when]  it finishes first thing you do is find the **additional drivers UI  from the unity icon on top of the dock** and search for and install proprietary/ legacy drivers [and not open source] for your graphics [nvidia or ATI]. It would also take some time, but once that finishes everything should be stable. The only hurdle is getting to that terminal and executing/ installing common drivers.

---

