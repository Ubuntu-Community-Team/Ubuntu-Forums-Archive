---
title: "Installation trouble: wis-go2007"
date: 2007-09-16
forum: Installation &amp; Upgrades
---

### Post by tipdrinker on 2007-09-16
Hi I bought the ADS Tech DVD Xpress DX2 for my computer and in order for it to work i need to install wis-go2007. However when i enter make on the terminal i get this error message! aargh! what do i do?

kev@89-125-52-231:~/Desktop/wis-go7007-linux-0.9.8$ cd wis-go7007-linux-0.9.8-patched
kev@89-125-52-231:~/Desktop/wis-go7007-linux-0.9.8/wis-go7007-linux-0.9.8-patched$ make

***** Using kernel source in /lib/modules/2.6.20-16-lowlatency/build *****

make modules -C /lib/modules/2.6.20-16-lowlatency/build M=/home/kev/Desktop/wis-go7007-linux-0.9.8/wis-go7007-linux-0.9.8-patched/kernel
make: *** /lib/modules/2.6.20-16-lowlatency/build: No such file or directory.  Stop.
make: *** [all] Error 2
kev@89-125-52-231:~/Desktop/wis-go7007-linux-0.9.8/wis-go7007-linux-0.9.8-patched$ 


man i hope i get a reply. I really need this to work!
:(:confused::mad:

---

### Post by Pumalite on 2007-09-16
Do you have build-essential installed?
sudo apt-get install build-essential

---

### Post by tipdrinker on 2007-09-16
yeah i have it

---

### Post by Pumalite on 2007-09-16
Do your headers correspond to your kernel version?

---

### Post by tipdrinker on 2007-09-16
ok i searched for 2.6.20-16-lowlatency in the synaptic package manager and im currently downloading whatever is not installed. lets see if that works...

---

### Post by tipdrinker on 2007-09-16
worked!

---

### Post by Pumalite on 2007-09-16
Glad it worked for you!

---

### Post by tipdrinker on 2007-09-16
ok next step. In order for my dvd xpress dx2 to work i need to add a patch called wis-go7007-linux-20061021.diff
does anyone know where i'm supposed to put it or what im supposed to do with it?

---

