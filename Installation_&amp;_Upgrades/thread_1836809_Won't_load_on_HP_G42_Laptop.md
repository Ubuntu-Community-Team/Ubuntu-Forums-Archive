---
title: "Won't load on HP G42 Laptop"
date: 2011-08-31
forum: Installation &amp; Upgrades
---

### Post by notoptimus on 2011-08-31
I'm using an HP G42 Laptop. I used to have Ubuntu installed and I frequently installed other Linux to try them out. Now when I try to install or run a live CD or USB it works until I select to try or install, it just goes black after the loading screen. It might have something to do with the Oneiric Alpha I tried (I know, terrible idea) I'm not sure if I got any working after that but it's the last one I remember installing. I also tried using Wubi, it installs fine but I get the same problem when I try to boot it.

---

### Post by Quackers on 2011-08-31
Welcome to UF :-)

What graphics card is installed on that system?
You may need a boot option such as nomodeset. See below for details on how to 

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by notoptimus on 2011-08-31
I think it's AMD M880G with ATI Mobility Radeon HD 4250. I already tried nomodeset and the other options; nomodeset left the same problem and the others -if I remember correctly- caused their own. I'd like to emphasize that I had the same graphics card as I used to when I was using Ubuntu and other Linux distros in the past.

---

### Post by Hakunka-Matata on 2011-08-31
Have you tried the F6 Key?  I haven't seen that option displayed during install since several versions back and thought it didn't exist anymore.  But I just saw where a fellow hit F6 to a black screen with blinking cursor and it brought up the boot options menu.  He was installing 11.04 - 64 and said it worked on the 11.04 - 32 bit too.  [http://ubuntuforums.org/showthread.php?p=11207581#post11207581](http://ubuntuforums.org/showthread.php?p=11207581#post11207581)   Can anyone confirm that?

---

### Post by notoptimus on 2011-08-31
Yes, the F6 key is where the boot options Quackers suggested and they are not working. Thanks for trying to help guys, but these are workarounds, it used to work fine, can anyone tell me what went wrong?!? Or how to actually fix it?

---

### Post by notoptimus on 2011-08-31
It's not giving a black screen anymore in any boot option. Instead I'm getting some text that starts with "Kernel panic - not syncing: attempting to kill unit!" and ending with "panic occurred, switching back to text console"

---

### Post by Hakunka-Matata on 2011-09-01
11.10 Alpha 1 ?  I tried alpha 3 and it nearly melted my monitor, "I'm laughing a bit right now" maybe moving to the alpha 3 build would progress your endeavour?
[http://cdimage.ubuntu.com/releases/oneiric/alpha-3/](http://cdimage.ubuntu.com/releases/oneiric/alpha-3/)

Good Luck

---

### Post by notoptimus on 2011-09-01
No, it was Alpha 3, but it's long deleted.

---

### Post by notoptimus on 2011-09-01
Oneiric beta booted fine on the live cd. I don't get this at all but I'm happy it's working again. Thanks guys!

---

