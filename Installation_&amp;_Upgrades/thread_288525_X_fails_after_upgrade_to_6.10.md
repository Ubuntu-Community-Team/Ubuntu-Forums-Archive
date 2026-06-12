---
title: "X fails after upgrade to 6.10"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by mnshsnghl on 2006-10-30
Hi,
   I upgraded desktop from dapper to Edgy (6.10) yesterday, upgraded through (update-manager -c), and after upgrade when I rebooted I found the X not able to run. I get the following error while I run gdm , or startx ---

(EE) module ABI major version (0) doesnt match the server's version (1)
(EE) failed to load module "i810" (module requirement mismatch, 0)
(EE) no drivers available.

On my other desktop, when I upgraded I got into the same problems, but then I tried the live CD installation, and that went to pretty fine.. and X is also starting up nicely. 
Any clue why the above is failing and how can I fix it. I dont want to do a fresh installation, coz I have lots of data on this machine.

Also as I read in one of the site, when I did X -ignoreABI, the X shows up, but when I put following in xorg.conf, it doesnt work -
Section ServerFlags
  Option "ignoreABI" "true"
endsection


Thanks.

---

### Post by KaosX on 2006-10-30
try the following

```

sudo apt-get install xserver-xorg-video-i810

```

if you run into more issues run one of these bad boys

```

sudo dpkg-reconfigure xserver-xorg

```

which is how I fixed the same exact issue you're getting, remember for the amount of memory for the vid card, its in kb not mb.

---

### Post by mnshsnghl on 2006-10-30
> **KaosX said:**
> try the following

```

sudo apt-get install xserver-xorg-video-i810

```

if you run into more issues run one of these bad boys

```

sudo dpkg-reconfigure xserver-xorg

```

which is how I fixed the same exact issue you're getting, remember for the amount of memory for the vid card, its in kb not mb.
You rock man!! it works :) Why shouldnt it automatically do that :))

---

