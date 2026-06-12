---
title: "wubi install leads to &quot;grub rescue&gt;&quot;"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by jakerman999 on 2010-07-28
A friend of mine recently decided to make the switch to open source operating systems (hooray!) after learning about WUBI, and they asked for my help installing it.  not having a recent live cd(7.10) we downloaded a new iso and mounted it.  the auto-run dialog appeared and we proceeded through the "install inside windows" using a secondary hard-drive as the designated windows device.  

success, reboot into ubuntu.  then it asked to update, fine.  need another reboot, alright.  

```
error: no such device: (hard drive serial number).
grub rescue>
```

ls displays hd0 hd1 and fd1 inside brackets, ls with modifiers says unknown filesystem type, and nothing else works.  can anyone help me here?

---

### Post by bcbc on 2010-07-28
a recent grub update is overwriting the windows bootloader with grub. You can reinstall the windows bootloader from a windows repair cd/dvd (fixmbr for xp, bootrec.exe /fixmbr for vista/7) or install the lilo bootloader from a live CD:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

---

### Post by jakerman999 on 2010-07-29
burned a fresh live cd, and installed the lilo boot-loader. rebooted and found an operating system choices menu.  windows xp works fine, but the Ubuntu option just reboots the computer.  what can I do to fix this?

---

### Post by bcbc on 2010-07-29
> **jakerman999 said:**
> burned a fresh live cd, and installed the lilo boot-loader. rebooted and found an operating system choices menu.  windows xp works fine, but the Ubuntu option just reboots the computer.  what can I do to fix this?

Did you just install Ubuntu - so you would lose nothing if you reinstalled? That's probably the easiest - but **if you reinstall you will lose any data or customization you've made**; also don't run any grub updates, until someone fixes this latest issue.

---

### Post by bcbc on 2010-07-29
> **bcbc said:**
> Did you just install Ubuntu - so you would lose nothing if you reinstalled? That's probably the easiest - but if you reinstall with wubi don't run any grub updates, until someone fixes this latest issue.

I didn't make this clear, but if you reinstall it will remove any changes you made before. (It deletes the old install before reinstalling). I only suggest this if you haven't done much customization or have any important data.

---

### Post by jakerman999 on 2010-07-30
would it be possible to reinstall wubi, run the upgrade, then install lilo before the reboot?  or even install and use lilo instead of grub entirely?

---

### Post by bcbc on 2010-07-30
> **jakerman999 said:**
> would it be possible to reinstall wubi, run the upgrade, then install lilo before the reboot?  or even install and use lilo instead of grub entirely?

Reinstall and run the updates, but a) either don't update grub-pc or grub-common, or b) make sure that if you update you don't tell grub to install to /dev/sda. (At this point I am not yet clear on whether the user clicks on the /dev/sda checkbox or whether it's done automatically). 

When I ran a test, I saw a screen that said - []Skip installation of grub?. The correct thing for wubi is to check that box and click on Forward. If you click Forward without checking it, it prompts you to install grub and gives you a choice of []/dev/sda. It's when you check that box that it overwrites the windows bootloader. (I believe, but am not certain - if you saw something different let me know)

Also, after running updates you could run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and it will tell you what the bootloader is in the RESULTS#.txt. run it before rebooting, and if it says "grub2 is installed in /dev/sda" (right at the top) then you'll have to install lilo. If it says "Windows or Lilo is installed in /dev/sda" then no problem.

---

### Post by jakerman999 on 2010-07-31
> **bcbc said:**
> Reinstall and run the updates, but a) either don't update grub-pc or grub-common, or b) make sure that if you update you don't tell grub to install to /dev/sda.  


Took option a.  Linux works fine now.  RESULT.TXT says lilo is on sda.  Grub still wants me to update it.  Can I remove the package with an apt-get command or something similar?  If not, can I disable up dates to it? 

Thanks in advance.

---

### Post by bcbc on 2010-07-31
> **jakerman999 said:**
> Took option a.  Linux works fine now.  RESULT.TXT says lilo is on sda.  Grub still wants me to update it.  Can I remove the package with an apt-get command or something similar?  If not, can I disable up dates to it? 

Thanks in advance.

You need grub to boot wubi. There might be a way to suppress grub updates from showing, but I don't know it.

---

### Post by jakerman999 on 2010-08-01
> **bcbc said:**
> You need grub to boot wubi. There might be a way to suppress grub updates from showing, but I don't know it.

alright, thanks anyway.  topic marked as solved.

---

### Post by kenbuntu75 on 2010-10-16
> **bcbc said:**
> a recent grub update is overwriting the windows bootloader with grub. You can reinstall the windows bootloader from a windows repair cd/dvd (fixmbr for xp, bootrec.exe /fixmbr for vista/7) or install the lilo bootloader from a live CD:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

While this thread indeed worked for me I'd like to add a bit of info. I scrapped my grub by accident, and used an XP cd to boot the repair console. Yet the 'fixmbr' command printed nothing and a next command prompt appeared. Upon reboot, grub was not fixed.

The problem was I had XP SP3 installed, and had used a XP SP2 disc for the fix and it didn't work. Once I used a SP3 disc, my system was restored. 

Hope this helps.

---

### Post by chadporsche997 on 2010-10-23
> **jakerman999 said:**
> A friend of mine recently decided to make the switch to open source operating systems (hooray!) after learning about WUBI, and they asked for my help installing it.  not having a recent live cd(7.10) we downloaded a new iso and mounted it.  the auto-run dialog appeared and we proceeded through the "install inside windows" using a secondary hard-drive as the designated windows device.  

success, reboot into ubuntu.  then it asked to update, fine.  need another reboot, alright.  

```
error: no such device: (hard drive serial number).
grub rescue>
```ls displays hd0 hd1 and fd1 inside brackets, ls with modifiers says unknown filesystem type, and nothing else works.  can anyone help me here?

I am having this same issue with my WUBI:
[CODE]error: no such device: (hard drive serial number).
grub rescue>
and I tried booting from a Live CD and got the same result.  I am running Windows Vista on my Acer and just installed Wubi the other night and it was running great now I have this hiccup.  Please help!

---

