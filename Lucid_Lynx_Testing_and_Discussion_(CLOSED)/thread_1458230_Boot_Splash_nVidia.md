---
title: "Boot Splash nVidia"
date: 2010-04-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by -humanaut- on 2010-04-19
I was wondering if anyone new if the bootsplash screen was going to be improved by the R.C. for nVidia card users? nouveu is ambitious but I like my compiz and 3d effects but that 16 Color splash screen is kind of annoying.

---

### Post by cb951303 on 2010-04-19
> **-humanaut- said:**
> I was wondering if anyone new if the bootsplash screen was going to be improved by the R.C. for nVidia card users? nouveu is ambitious but I like my compiz and 3d effects but that 16 Color splash screen is kind of annoying.

unless nvidia decides to support kms (which they repeatedly said they won't) i don't think it will be improved.

---

### Post by -humanaut- on 2010-04-19
not a show stopper for me but thats pretty lame I wonder if theres a way to use VESA just for the Bootsplash

---

### Post by whatever on 2010-04-19
you may use uvesafb to get a nice looking bootsplash. Just install "v86d" (universe), put something like
```
uvesafb mode_option=1280x1024-32@60 mtrr=3 scroll=ywrap
``` in /etc/initramfs-tools/modules and run
```
sudo update-initramfs -u
```

There won't be kms with proprietary nvidia drivers because nvidia won't GPL their drivers.

---

### Post by -humanaut- on 2010-04-19
> **whatever said:**
> you may use uvesafb to get a nice looking bootsplash. Just install "v86d" (universe), put something like
```
uvesafb mode_option=1280x1024-32@60 mtrr=3 scroll=ywrap
``` in /etc/initramfs-tools/modules and run
```
sudo update-initramfs -u
```There won't be kms with proprietary nvidia drivers because nvidia won't GPL their drivers.

I know nVidia's not supporting KMS this seems to work thanks buddy

---

### Post by FrancoNero on 2010-04-19
> **-humanaut- said:**
> I was wondering if anyone new if the bootsplash screen was going to be improved by the R.C. for nVidia card users? nouveu is ambitious but I like my compiz and 3d effects but that 16 Color splash screen is kind of annoying.

especially since most of the time I just see a black screen. by the time the 16color splash comes up, the system is so far bootet that i see it for about 2 seconds before i get to the login screen. ridiculous

---

### Post by ToxicBurn on 2010-04-19
I wonder if it would be the time to start thinking about getting a ATI card i hear they are doing really well with drivers now

---

