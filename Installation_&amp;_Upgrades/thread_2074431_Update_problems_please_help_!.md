---
title: "Update problems please help !"
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by hahaikillu23 on 2012-10-21
i keep getting this error



Failed to fetch [http://ppa.launchpad.net/ferramroberto/filezilla/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/ferramroberto/filezilla/ubuntu/dists/precise/main/source/Sources)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/ferramroberto/filezilla/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/ferramroberto/filezilla/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/ferramroberto/filezilla/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/ferramroberto/filezilla/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by jerrrys on 2012-10-21
Those are PPA's for 12o4 and if I understand, you are running 12.10.  So just uncheck or remove them.

---

### Post by The Cog on 2012-10-21
Duplicates merged.

---

### Post by docpaed on 2012-10-21
I am also unable to upgrade 12.04 to 12.10 64 bit version. I clicked upgrade as per ubuntu updates, downloading went fine, then as it was installing, an error message appeared stating that it could not find lib and that I should report this as a bug. I clicked to continue, and the process hung on the restart phase for about half an hour when I decided to manually power down and up again the process. 
When this restarted after powering down, a message appeared stating could not locate disk and I pressed manual recovery, it has now opened to a screen with my original background without any icons, does not fit my 19" LCD monitor and had to use the old ctrl, alt, del so that I could get out. 
I am now writing from my windows 7. I had installed the original 12.04 inside windows, as this computer's hard drive was partitioned into 3 by Compaq, hence it was too difficult a process for a newbie like me to set it up as a side by side install.
Help is urgently appreciated as I cannot no longer get to any of the ubuntu programs

---

### Post by darkod on 2012-10-21
I don't know if it will work, but for interrupted upgrade process you can try this:
1. Boot the recovery mode option from the grub2 boot menu. If the menu doesn't show (you have only ubuntu), hold Shift during boot so that it shows.
2. When the recovery menu shows up, select Drop to root shell.
3. When the shell opens, remount root as read/write with:
```
mount -o rw,remount /
```

4. After root is remounted as read/write, try running this:
```
apt-get install -f
dpkg --configure -a
```

After that finsihes reboot and see if it helped.

---

