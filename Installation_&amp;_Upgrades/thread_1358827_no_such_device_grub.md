---
title: "no such device grub"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by ubudog on 2009-12-18
Hi, I am not new to Ubuntu, used it for 3 years.  I have a desktop that I wanted to install Ubuntu on.  I booted with the live cd and installed it, no error.  Then I rebooted it, but at the grub menu, it said "error:no such device" and then it had some long number.

Any help appreciated.

---

### Post by Tclarkie on 2009-12-18
can u please post ur /boot/grub/grub.cfg file please

---

### Post by ubudog on 2009-12-19
> **Tclarkie said:**
> can u please post ur /boot/grub/grub.cfg file please

I tried to use the recovery mode to drop to a root shell, but when I tried to boot it, it said "no such device."  So I cannot access a terminal.

---

### Post by Tclarkie on 2009-12-20
Lol, sorry. Any how do u have an available Ubuntu live cd, if so great, if not, get one. Boot off the cd and mount the hdd, then open /boot/grub/grub.cfg, and copy paste the contents into a post

---

### Post by ubudog on 2009-12-20
> **Tclarkie said:**
> Lol, sorry. Any how do u have an available Ubuntu live cd, if so great, if not, get one. Boot off the cd and mount the hdd, then open /boot/grub/grub.cfg, and copy paste the contents into a post

Ok, might be a couple of days until I respond.  Need to get a new monitor.

---

### Post by ubudog on 2009-12-21
Nevermind, got it figured out.

---

### Post by bobbypos on 2010-01-09
Could you please post your solution? I'm having the exact same problem. :( Thanks!

---

### Post by ubudog on 2010-01-09
I just downgraded to 9.04.

---

### Post by drs305 on 2010-01-09
Edit: ubudog, glad you 'solved' your problem. I meant to respond to MrATM. Since your problem was resolved I didn't think you'd mind providing him this space to assist.

> **bobbypos said:**
> Could you please post your solution? I'm having the exact same problem. :( Thanks!

The details are sketchy, but it sounds like the error "no such device" plus a "long number" is probably an error stating that it can't find a UUID.

If you post your error message in more detail we can probably help. Download and run this script will probably tell us what we need to know:
[http://sourceforge.net/projects/bootinfoscript/]("http://sourceforge.net/projects/bootinfoscript/")

Download to your Desktop, then run:
```
sudo bash ~/Desktop/boot_info_script047.sh
```
Copy the contents of RESULTS.txt into your response, highlight it, and then click on the # symbol in the menu above so the entry is placed within a message box.

---

### Post by MrATM on 2010-01-09
What was your problem? I seem to be having the same one.

---

### Post by ubudog on 2010-01-09
> **drs305 said:**
> The details are sketchy, but it sounds like the error "no such device" plus a "long number" is probably an error stating that it can't find a UUID.

If you post your error message in more detail we can probably help. Download and run this script will probably tell us what we need to know:
[http://sourceforge.net/projects/bootinfoscript/]("http://sourceforge.net/projects/bootinfoscript/")

Download to your Desktop, then run:
```
sudo bash ~/Desktop/boot_info_script047.sh
```
Post the contents of RESULTS.txt. In your reply, please copy the entry, highlight it, and then click on the # symbol in the menu so the entry is placed within a message box.

I fixed it by downgrading to Jaunty.

---

