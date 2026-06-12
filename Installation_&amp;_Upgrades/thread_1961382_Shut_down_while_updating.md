---
title: "Shut down while updating"
date: 2012-04-19
forum: Installation &amp; Upgrades
---

### Post by LT72884 on 2012-04-19
I just installed ubuntu 11.10. I had it working great for about an hour. When i installed i selected the two options on the bottom to install thrid party and all updates. Was having fun with the new interface and the fact the wifi worked. Well, i ran sudo apt-get update && sudo apt-get upgrade. ABout 30 minutes into it, i had to close the terminal sesion, this made it so the command was terminated early, now it wont boot at all. Just gets part way through the bash screens of checking battery and then flashes alot and does nothing. haha is this a reinstall or is there a way to recover it? thanks.

---

### Post by albandy on 2012-04-19
Can you open a terminal?

---

### Post by LT72884 on 2012-04-19
nope. no terminal. maybe threw recovery but then that is read only.. i cant even get passed the bash screen when it is loading the OS. Just tried to reload from live cd and now it says i have no HDD space left, when i know i have 200GB. Also, this time the wifi in live cd is going haywire. it connected for 3 minutes, but once i hit instal, it disconnected.

thaks

---

### Post by albandy on 2012-04-19
Well if you enter in recovery mode, there is a entry in the Recovery menu to remount in read/write mode.

Select the remount option and press enter
then select root and press enter
finally try
apt-get install -f

---

### Post by sudodus on 2012-04-19
When your system is at such an early stage, it is probably easier to reinstall than to try to repair it.

Use it as a lesson on the importance of backup: When you have invested a lot of time in a system, back it up, so that you don't have to spend that time again! And make fresh backups regularly! I use external hard disk drives to backup my systems.

---

### Post by LT72884 on 2012-04-19
the remount opted out with an error=mount -ro. so i know something is wrong. so any apt get stuff wont work since it wont mount as w. ok, new problem. i had it dual booted with xp pro. i went into cp pro, disk management and deleted the linux partion so i could start over. however, now i cant get past the grub rescue prompt. How do i remove grub rescue before i reinstall ubuntu? i kinda want to remove grub and start allll over again. This way, i know how to remove in future.

thanks guys

---

### Post by albandy on 2012-04-19
If you're using XP  boot with the installation cd and enter in the recovery console
then type
FIXBOOT
FIXMBR
this will replace grub with the Windows XP boot loader.

Finally reinstall ubuntu.

---

### Post by sudodus on 2012-04-19
> **LT72884 said:**
> the remount opted out with an error=mount -ro. so i know something is wrong. so any apt get stuff wont work since it wont mount as w. ok, new problem. i had it dual booted with xp pro. i went into cp pro, disk management and deleted the linux partion so i could start over. however, now i cant get past the grub rescue prompt. How do i remove grub rescue before i reinstall ubuntu? i kinda want to remove grub and start allll over again. This way, i know how to remove in future.

thanks guys
This will be done automatically by the installer, so boot from your Ubuntu CD/USB drive and reinstall :-)

For the future you might use the following link:
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1581099_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by LT72884 on 2012-04-19
perfect. even if i didnt do that. reinstalling ubuntu 11.10 should replace the grub loader once again... right? ill try it both ways and see what happens. haha. thanks guys. im studying for chem and its 4am here. sigh.

---

