---
title: "X doesn't start after 6.10 to 7.04 upgrade"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by Clegg on 2007-05-05
Hi, I had a fully functional computer, with 6.10 on it. Then, 7.04 came out. I saw some features I liked, so I decided to upgrade. I run the upgrade from the Terminal, as said in the sticky up top, reboot, and when it gets to the point where X should start... it doesn't. Any reason why, and more importantly, how can I fix this?

Specs, incase you need them:
[SIZE="1"]AMD Athlon 3300+
2 GB Ram
nVidea 4000 series video card[/SIZE]

Thanks in advance.

---

### Post by finalzero on 2007-05-05
If your system is able to boot i.e. get past the grub menu etc then you might be okay and it could just be a graphics config issue.

When you get a blank screen, confirm your system is not frozen by pressing the num-lock key a few times to confirm it goes on and off.

Then press CTRL + ALT + F1  (or ALT + F1) to switch to a terminal window. You should see a login prompt, login and you should now be at the prompt.  You need to view your log file to look for any errors, type the following:

$:  sudo tail /var/log/syslog

Look for any error messages as this will indicate what went wrong.

---

### Post by zvacet on 2007-05-06
If you can use terminal type

```
 sudo dpkg-reconfigure xserver-xorg
```

select **nv** instead of **nvidia** and after that you can go an update your drivers

If you can not use terminal boot in recovery and type same command without sudo.

---

