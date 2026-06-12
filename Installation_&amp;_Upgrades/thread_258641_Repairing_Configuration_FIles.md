---
title: "Repairing Configuration FIles"
date: 2006-09-16
forum: Installation &amp; Upgrades
---

### Post by linnuxxy on 2006-09-16
I modified a configuration file located at /etc/X11/xkb/rules/ without backuping it !!!!


How can I restore the original files... using apt... using dpkg or manualy downloading ....

I tried 'sudo apt-get --reinstall --purge install xkeyboard-config" but the command didnot repair the files...

Please help me out!!!

---

### Post by aysiu on 2006-09-16
This might be overkill, but have you tried ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```?

---

### Post by linnuxxy on 2006-09-17
i don't think it is the right solution.....

I would be ok if you point me where can I download the files manually, although I think it should be provided such way... just like Windows Repair thing!!!

---

### Post by aysiu on 2006-09-17
Which config file did you modify? Maybe I can post mine?

---

### Post by linnuxxy on 2006-09-18
All the files in the directory /etc/X11/xkb/rules/
Thank you...

---

### Post by aysiu on 2006-09-18
You're telling me you modified *all* those files? That's a bit to post, especially since some are symlinks.

Well, here's a .tar.gz of them. I'm not sure if my files will work for your computer, but it's worth a shot. If they don't, you can also try booting a live CD and copying the /etc/X11/xkb/rules files from there.

---

### Post by linnuxxy on 2006-09-19
Thanks man... 

Working great now!!!

Thanks again!!!

---

