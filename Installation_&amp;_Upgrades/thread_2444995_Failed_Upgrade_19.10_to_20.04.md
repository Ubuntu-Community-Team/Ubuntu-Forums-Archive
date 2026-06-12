---
title: "Failed Upgrade 19.10 to 20.04"
date: 2020-06-07
forum: Installation &amp; Upgrades
---

### Post by cvlc on 2020-06-07
Hi,

The update to 20.04 failed with a white "something went wrong" screen, and a "close session" button. 
Steps : Used Apt upgrade to update to latest, and rebooted. Then I used "Update Manager" GUI which had an "upgrade" button. 

Download went smoothly, then about 5 / 10 min of updates and after that the said white screen appeared. I rebooted from another tty, but after Grub I'm stuck with the laptop vendor logo from the Bios (pressing escape doesn't hide plymouth so i'm not sure it even gets to that). I can boot back to the white screen by choosing an older kernel and recovery mode from grub.

I don't usually use Ubuntu, is there a quick command to force launch the upgrade again so that hopefully it finishes properly ?

Thanks, have a great day !

---

### Post by dino99 on 2020-06-08
Glance at 'journalctl -b' output from a terminal to know about errors (red lines) and warnings (yellow lines)
you can also edit /etc/default/grub to remove 'quiet' from it, then save and run 'update-grub' to take effect and reboot without the purple splash screen.

---

### Post by CatKiller on 2020-06-08
> **cvlc said:**
> I don't usually use Ubuntu, is there a quick command to force launch the upgrade again so that hopefully it finishes properly ?

It may be that the normal package management things (**apt update**, **apt upgrade**) are sufficient for you now, but, since you asked, the command to start the upgrade process from the command line is **do-release-upgrade**.

If you aren't able to boot normally, a useful tool is to boot from a live USB, mount the partition that contains your install, and **chroot** to it. That way you can run all your commands as if you'd booted into your install, but with the support infrastructure of the live environment.

---

### Post by cvlc on 2020-06-08
Hi,

Thanks for your answers. Will try that and report back

---

### Post by ActionParsnip on 2020-06-09
You can also boot to the 20.04 install media and upgrade that way. It will be offered as an option in the installer

---

### Post by cvlc on 2020-06-20
Hi,

I managed to boot with recovery mode on an older kernel (latest one panicked even in recovery mode). I activated network support, dropped to root console, ran dpkg --reconfigure -a, and an another upgrade and autoremove, and everything works. For some reason the upgrade had apparently stopped halfway... 

thanks for your help !

---

