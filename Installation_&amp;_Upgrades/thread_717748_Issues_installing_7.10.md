---
title: "Issues installing 7.10"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by stryve on 2008-03-07
I've been using ubuntu personally for about a year or so, and am ready to make an attempt to move to it at my business. My first step will be to load up a machine im currently using with windows xp into a dual boot, and run windows in a VM (a must for our accounting software currently) and test it for about 3 months, if things go smoothly and im ok with the change then i'll leave it, and all future machines will have ubuntu installed using a similar VM type setup. Anyways, i started the install this morning and have hit a frustrating wall. Im currently downloading the alternative install to see if that fixes it but before i go that far i'd like maybe a suggestion or two.

During the install using the live cd everythign works fine up until it tries to start the xwindows environment, at which time my monitor screen flashes 74.6khz / 60khz about 6 times then i get an error saying display:0 has stopped and restarted 6 times and will wait 2 min to try again, something bad is probably going on. Since its loading from the cd i have no way to really force it to load any other way. Running the live cd in safe graphics mode has not made any change. Do i just need to do the install with the alternative cd or is there something im missing?

---

### Post by Pumalite on 2008-03-07
Try the Alternate CD and report back if you still have problems

---

### Post by stryve on 2008-03-07
ok, so alternate was ....a really bad experience. Just to clarify i'm pretty familiar w/ text based installers as i had been using openbsd for ...4-5 years now for our inhouse server, i've done quite a few installs that way but man. Ok so it took each detecting hardware phase about...10 min, then it would suddenly zip from 0% to 100% and move on, then after a good 45 min of installing, it goes to install grub and at 50% it freezes , so im thinking ok no biggie, its been doing this on every step, i go grab some pizza come back about 15 min later and its still sitting there. Long story short i had to fire up the linux system cd, and fix the partitions so my windows partition was set to boot. 

any suggestions?

also should i attempt the livecd using vga mode and try and set my hz lower? i just thought of that.

---

### Post by Pumalite on 2008-03-07
Try editing your boot in Live CD with "vga=791" at the end.

---

### Post by stryve on 2008-03-07
that seemed to work, im writing this from within the live cd installer. Hopefully this goes smoother, its defiantely running a heck of alot faster.

---

### Post by Pumalite on 2008-03-07
Good to know. Good luck.

---

### Post by stryve on 2008-03-07
ok i've made it to where its attempting to install grub again and once again its seem to have locked itself up. Its trying to run update-grub and has been sitting there for about 18 min now. is there anyway to cancel it and i'll try to install lilo or something before i reboot?

also i dont know if it matters but running ps -aux|grep grub shows the following:
```
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
root       701  0.0  0.0   1716   552 ?        S    13:24   0:00 log-output -t grub-installer chroot /target update-grub -y
root       702  0.0  0.0   3900  1344 ?        S    13:24   0:00 /bin/bash /usr/sbin/update-grub -y
root       707  0.0  0.0   3900   644 ?        S    13:24   0:00 /bin/bash /usr/sbin/update-grub -y
root       708  0.0  0.0   3900   832 ?        S    13:24   0:00 /bin/bash /usr/sbin/update-grub -y
root       754  0.0  0.0   3900   612 ?        S    13:24   0:00 /bin/bash /usr/sbin/update-grub -y
root       755  0.0  0.0   3900   652 ?        S    13:24   0:00 /bin/bash /usr/sbin/update-grub -y
ubuntu     886  0.0  0.0   2980   772 ttyp0    S+   13:37   0:00 grep grub
root     32595  0.0  0.0   1708   420 ?        S    13:24   0:00 log-output -t ubiquity --pass-stdout /usr/share/grub-installer/grub-installer /target
root     32596  0.0  0.0   1752   556 ?        S    13:24   0:00 /bin/sh /usr/share/grub-installer/grub-installer /target
```

which looks to me like its got 5 update-grub -y  's going at once. could that be the problem?

---

### Post by Pumalite on 2008-03-07
I would start from scratch burning a new CD after doing md5sum on iso, burning at 4x, etc. Clean your burner lens, just in case.

---

### Post by stryve on 2008-03-07
i'd be ok with that except grub has already installed on my mbr. I just booted up windows manually through grub and that wasn't that big of a deal, but what i'd really like to do is fix grub i'm fairly confident that once i can fix its boot configuration file i'll be set. 

SO

a. can i do that from windows, is there anything that will let me read ext3 so i can edit the file and b. if not how can i boot ubuntu bc using : kernel /vmlinuz root=/dev/sda8    (which is the portion of my HD were the install is) is coming back saying it cannot find the file. any suggestions, beyond redoing the entire installation?

---

### Post by Pumalite on 2008-03-07
Get Knoppix Live CD: [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
Burn to disk and boot from it. It mounts all your drives/partitions automatically at boot. And in Knoppix, you are root.

---

### Post by stryve on 2008-03-07
Pumalite i appreciate the responses, i ended up downloading Ext2IFS which lets me view/edit ext2/3 partitions on windows and created menu.list for grub. Both OS's boot properly now.

The only thing i have left to do is figure out how to boot into the safe mode for Ubuntu but im sure i can find that on the web somewhere.

---

### Post by Pumalite on 2008-03-07
OK. Bon voyage!

---

