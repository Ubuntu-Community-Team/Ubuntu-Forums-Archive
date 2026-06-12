---
title: "Ubuntu 11.04 Wrong Installion"
date: 2011-05-29
forum: Installation &amp; Upgrades
---

### Post by heyappleknife on 2011-05-29
I accidentally selected the wrong way to install Ubuntu while installing it. I installed it by restarting my computer and installing. I installed it on my hard drive with Windows 7 on it. I want to keep Windows 7. I have another hard drive I'm trying to install Ubuntu on. I'm wondering if I install Ubuntu on that other hard drive then can I delete the Ubuntu partition I have installed on my Win7 drive without ANY problems going to Ubuntu and Win 7?

---

### Post by Bucky Ball on 2011-05-29
Have you installed using 'Use whole disk' on the Win partition? If so, Win7 will be gone.

If you install Ubuntu on a different hard drive (or partition) to Win then it will pick up the Win install (and any other OS) and add that to the grub selection at boot without you having to do much. To achieve what you want to do you need to do a manual install, not automatic, when you get to the partitioning section of the installation and select or create the correct partition/disk where you want to install Ubuntu.

---

### Post by jerrrys on 2011-05-29
it will mess up your boot.  do you have your windows rescue cd?

beat by bb...hope you didnt, but if you did

---

### Post by heyappleknife on 2011-05-29
Windows 7 is still here. As I said it's but on the SAME hard drive as Windows just a different partition.


So wait. If I delete my current Ubuntu partition and reinstall Ubuntu I will still be able to access Win 7?

Usually I correctly install it.

---

### Post by Bucky Ball on 2011-05-29
If you update grub you probably will be able to boot Windows7. Not sure about grub2 but open a terminal (Applications>Accessories>Terminal) and try:

```
sudo update-grub
```Another good tool is Grub Customiser. You will be able to see all OS on your machine and add them to the boot menu with one click.

Just one thing: Is your machine just booting straight into Ubuntu and not giving you any options for anything else? If so, at boot hit (repeatedly) escape (could be shift in 11.04) and that should bring up your grub menu, probably with Win7 on it.

If that is the case you can change that permanently in Ubuntu. Let us know how you went.

---

### Post by heyappleknife on 2011-05-30
First. I was able to get to Windows and Ubuntu. Second, I didn't realize Ubuntu installed on the hard drive I wanted so I don't need help. Now. I will need help on another computer but I'll wait to start up a new Thread.

---

### Post by dFlyer on 2011-05-30
> **heyappleknife said:**
> First. I was able to get to Windows and Ubuntu. Second, I didn't realize Ubuntu installed on the hard drive I wanted so I don't need help. Now. I will need help on another computer but I'll wait to start up a new Thread.

Please mark this thread RESOLVED.

---

