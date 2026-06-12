---
title: "Problems after xconf config - and downgrading ubuntu."
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by Prowler_1 on 2007-11-13
hi,

I upgraded from 7.04 to 7.10, the sys was runing havy
and programs run unstable, so i tray a Downgrade, back to 7.04.
using this guide: [https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)
but i got stuck an one point  and did not pursue it.

I noticed some problems with xconf config so i use: 
"sudo dpkg-reconfigure xserver-xorg off" command

rebooted bat it wuldent start, i get the ubuntu logo but everything 
froze and the keyboard led's are blinking, & nothing responds!

i rebooted agin, then while booting , the pc compleatly sutdown, 
i get to one or the other situation as described.

other system my pc works fine.  (kanotix) :confused:
i rerun "sudo dpkg-reconfigure xserver-xorg off" command
and make sure inputs are correct, but with the same result.

any way to repair install ubuntu? (or fix the problem)

Thanks.

---

### Post by zvacet on 2007-11-13
```
sudo dpkg --configure -a
```

```
sudo apt-get -f install
```

---

