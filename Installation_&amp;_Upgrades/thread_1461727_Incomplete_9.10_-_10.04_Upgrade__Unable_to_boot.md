---
title: "Incomplete 9.10 - 10.04 Upgrade / Unable to boot"
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by Spade12 on 2010-04-24
Hey guys

I was trying to upgrade from 9.10 to 10.04 RC1 through update-manager graphically.t

My system froze in the process and now I am unable to boot.

I get as far as the splash loading screen but then the ubuntu logo skews towards the bottom of the screen and I am reverted to a console screen with some kind of scan taking place:

[1169.3822319] ===>rt_ioctl_giwscan, 2(2) BSS returned data->length = 489 and it goes on and on 

When I access recovery mode from GRUB I tried cleaning up the packages I get an error "E: could not perform immediate configuration on 'util-linux'..."

So I'm looking for anyway to get this working out.

---

### Post by zvacet on 2010-04-24
Boot in recovery mode and type

```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing
```

and see if it helps

---

### Post by Spade12 on 2010-04-24
The last command isnt valid.  But i did the first two.

Same error.

I feel like it should work if only I were able to install the packages that the "repair broken packages" features got for me.

Unfortunately I still cant get past the immediate configuration error with 'linux-util'

I really dont want to have to start from scratch over this..

---

### Post by zvacet on 2010-04-25
```
sudo apt-get update
```

or 

```
sudo apt-get -f install
```

and post output here.Maybe somebody else will help you if you give that info.

---

### Post by Spade12 on 2010-04-25
SOLVED:

Thanks for the input guys.  But to remedy this problem I had to boot into recovery mode, shell with network access and sudo apt-get install 'util-linux' and then the missing dependency.

After that I was able to repair broken packages from the rescue context menu within recovery mode.

---

### Post by ehanes75 on 2010-04-27
I have the same error message, what dependencies did you need to fix?

---

### Post by Spade12 on 2010-04-27
Like I said I tried apt-get(ting) the util-linux package because that was spouting out an error but when I tried it said I needed some other dependency first like 'net-upstart' or something I forget.  So once I got that, then I was able to get the util-linux package downloaded and installed.

From there I went into the "Repair broken packages" part of the recovery menu and got everything working.

Good luck

---

