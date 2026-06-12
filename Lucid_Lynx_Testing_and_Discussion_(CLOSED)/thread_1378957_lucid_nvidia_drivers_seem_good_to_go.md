---
title: "lucid nvidia drivers seem good to go"
date: 2010-01-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mc4man on 2010-01-12
or pretty much so (didn't test from fresh install (maybe tomorrow or A2

But taking an install that was on the 7mach.. ppa, it's now on lucid drivers and all works well.

removed the ppa, un-installed the ppa's nvidia settings package, used hardware driver to activate the 185 drivers, did an update/upgrade and rebooted to the 190.53 drivers

Then in appearances re-activated compiz effects and all is as 'normally expected'  (- testing without using ppa's

---

### Post by kahumba on 2010-01-12
Good, hope that gets delivered for Alpha2 cause that's the reason I'm not testing Lucid.

---

### Post by zenarcher on 2010-01-12
Same here.  I'm waiting for A2 for the same reason.

Cheers,
zenarcher

---

### Post by dino99 on 2010-01-12
yeah i got it too,

recently i can't boot coz of gdm trouble. So, today i spend some free time to digg that problem:

 in fact i've not had /etc/gdm/custom.conf in place. Reconfiguring gdm did not help, so i copy/paste the karmic's one, that's all.

Now Lucid boot as expected  :D

Have nvidia 195 installed and running.

---

### Post by autocrosser on 2010-01-12
I also set the nvidia-current drivers up last night---removed the sevenmachines PPA & it all seems good to go.....running very well here.

---

### Post by mc4man on 2010-01-13
Almost is still the operative word, a daily installed now still needed a very little nudge in right direction to get the 190. (nvidia-current) up and running w/ desktop effects enabled if desired

Not totally unexpected with the main bug on nvidia still 'in progress',

---

### Post by Robin Nixon on 2010-01-18
I see that according to this:

[http://www.computerworld.com.au/article/332802/linux_conf_au_latest_linux_kernel_release_due_early_march/](http://www.computerworld.com.au/article/332802/linux_conf_au_latest_linux_kernel_release_due_early_march/)

Nvidia support will be built right into the kernel from version 2.6.33.

---

### Post by amano on 2010-01-18
But NOT the official drivers. -nv will be replaced by -nouveau. That's the whole deal. 

And the article talks about the 2.6-33 kernel while Ubuntu will ship the 2.6.32 kernel. Not that it will matter much because nouveau will probably be backported manually but just for the record.

---

