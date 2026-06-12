---
title: "Quiet splash hangs in Intrepid"
date: 2008-09-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Piraja on 2008-09-24
Dear all,

I did not find any post reporting exactly the same problem. After upgrading to Intrepid Ibex, the quiet splash has not worked properly on my laptop (Acer Travelmate 2354). It hangs at about one fifth of the process bar. The thing to do is, of course, to boot without quiet splash. Works fine. Actually the surprising detail is that it works fine: the boot-up process does not hang in the verbose mode (i.e. since I have removed "quiet splash" from the relevant line in menu.lst), but everything seems to work and at least on a quick look-up, also /var/log/messages seems fine to me.

This is a minor nuisance, since I can always boot without quiet splash. But quiet splash did not hang in this way in Hardy, so perhaps this is a bug in the Alpha version of Intrepid? Just wondering should I report it...

---

### Post by lswest on 2008-09-24
post the output of the following commands:
```
cat /etc/fstab
sudo blkid
```

Your swap file probably has a different UUID now, so we need to change that value in your fstab file.

---

### Post by Piraja on 2008-09-24
Swap UUID's are identical:

```
piraja@ubuntu-laptop:~$ [COLOR="SeaGreen"]cat /etc/fstab[/COLOR]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=3d7ae871-4faa-4b17-a889-7f96f311ac10 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
[COLOR="Green"]UUID=290e1215-6b61-4f65-b76b-5ecf895a6fd7[/COLOR] none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1 /home ext3 nodev,nosuid 0 2
piraja@ubuntu-laptop:~$ [COLOR="Green"]sudo blkid[/COLOR]
[sudo] password for pprasane: 
/dev/sda1: UUID="d81fa2b9-1eab-4ef3-ac86-eab243a68e29" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="3d7ae871-4faa-4b17-a889-7f96f311ac10" TYPE="ext3" 
/dev/sda5: TYPE="swap" [COLOR="Green"]UUID="290e1215-6b61-4f65-b76b-5ecf895a6fd7[/COLOR]" 
piraja@ubuntu-laptop:~$ 
```

---

### Post by lswest on 2008-09-24
Hmm, try rebooting and take note of the error or process when the splash disappears.

A similar thing happened with me in Hardy, but it was due to the swap UUID changing.

---

### Post by Piraja on 2008-09-24
Thanks, but the splash does not actually disappear. On the contrary, if I have the "quiet splash" in the grub menu (as I let menu.lst be automatically updated with a kernel upgrade), the process bar freezes and I have to press the power button to shut down the machine (no key combination seems to work). But the boot-up goes very fast and fine if I remove the "quiet splash" and I'm not really missing the graphical splash. Verbose is fine with me, so I manually remove both "quiet splash" and "quiet" from the latest kernel in menu.lst. Well, anyhow, I hope that if this is a bug in Intrepid, it will be fixed before the official release.

---

### Post by lswest on 2008-09-25
Very probably will be, it might just be that some beta program is causing the splash to hang or just a combination of things.

---

### Post by cariboo on 2008-09-25
You should really direct your intrepid questions here:

[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

as you will probably get quicker and better answers. I had a problem with usplash disappearing during boot up, but here have been a lot of updates today and that solved the problem. One of the updates was a kernel update, that is waht cured the problem.

Jim

---

### Post by Piraja on 2008-09-25
Dear LSWest and Jim,

thanks, I didn't realize I should have posted to I.I. Testing ad Discussion... I reported a bug, but since then some recent update seems to have changed the situation: [https://bugs.launchpad.net/bugs/274155](https://bugs.launchpad.net/bugs/274155)

---

### Post by justynbutler on 2008-10-04
I am having exactly the same issue as you Piraja on the Intrepid Ibex Beta.

During boot the progress bar consistently hangs at one fifth and everything stops. I have left it for around 5 minutes and there is no change, I have to hold the power button of my laptop to switch off.

However if I remove the "quiet splash" options in the kernel boot parameters it boots fine!

I have not found any bugs for this issue. I will probably file one once I have thoroughly tested the phenomenon.

---

### Post by Piraja on 2008-10-04
> **justynbutler said:**
> I have not found any bugs for this issue. I will probably file one once I have thoroughly tested the phenomenon.
Hey, I filed it already: [https://bugs.launchpad.net/bugs/274155](https://bugs.launchpad.net/bugs/274155) (see my previous post).

---

