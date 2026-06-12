---
title: "Today's updates - Lilo ?"
date: 2008-11-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2008-11-05
Loads of Jaunty updates today (05/11/08). One of them seems to be Lilo. Why would I want Lilo when Grub is the default boot manager ?  Also what's the difference between 
```
sudo aptitude upgrade
sudo aptitude safe-upgrade
```
Each time I've upgraded packages it's suggested I use safe upgrade.

---

### Post by plun on 2008-11-05
I just removed it and did a grub check as safety precaution

```
sudo apt-get remove --purge lilo

sudo update-grub

```

---

### Post by ronacc on 2008-11-05
good grief is that a massive oops , I wonder how many people that one will catch ? Oh well it serves us right for messing with a pre alpha:lolflag:

---

### Post by plun on 2008-11-05
Well...  "Debian Sid" test maybe....):P


[http://wooledge.org/~greg/sidfaq.html](http://wooledge.org/~greg/sidfaq.html)


.

---

### Post by ronacc on 2008-11-05
I saw the debian logos it stuffed into /boot ! I peeked in there to see what changes had been made before I purged lilo:p For safetys sake I never let the dev version install a bootloader , I just add the needed boot stanza to my existing grub on another drive .

---

### Post by Slug71 on 2008-11-05
Can Lilo boot Ext4?
Maybe they are testing for that purpose??

---

### Post by plun on 2008-11-05
> **Slug71 said:**
> Can Lilo boot Ext4?
Maybe they are testing for that purpose??

No, I dont think so....

Plymouth runs with GRUB as I knows it...  a must have for Jaunty


"Debian Sid import" has started... so watch out for the big bang..:lolflag:

[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-November/000510.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-November/000510.html)

---

### Post by philinux on 2008-11-05
I rebooted after the LILO update and no difference. It was installed but not activated. I removed it.

---

### Post by Kevbert on 2008-11-05
Maybe I should raise a bug report if there isn't one already....Oh yes there is...[[COLOR="Red"]here[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/lilo/+bug/293952").

---

### Post by ronacc on 2008-11-05
confirmed report and added comment.

---

### Post by rkrash3423 on 2009-02-06
For anyone that cares....I've been researching about file systems for linux for a few hours now and came across this thread. From what I gather it seems xfs is becoming the standard file system, for several reasons, and for some reason grub doesn't like it. Hence when you try install ubuntu with the live cd with xfs it tells you that "grub often hangs or fails to boot with xfs" or something along those lines. And wouldn't you know it when I tired to do it I got an error message that the grub installation failed to execute (why I started the research) and now I'm downloading the alternate cd to use lilo instead of grub. I'm guessing this is why they are fooling with lilo in the alpha's.....

---

### Post by taavikko on 2009-02-06
> **rkrash3423 said:**
> For anyone that cares....I've been researching about file systems for linux for a few hours now and came across this thread. From what I gather it seems xfs is becoming the standard file system, for several reasons

Where did you gather this information?
I', pretty sure that major distro's aren't moving away from ext
in a near future. 

xfs is a great filesystem, but only few people has the needs to use it as fs. What I have gathered btrfs, when complete, is far more better solution than xfs... 

But maybe someone with more acknowledgement will share some intel for us?

---

### Post by jknight on 2009-04-14
I just ran a dist upgrade to 9.04 beta from 8.10 and I was prompted for lilo config.

---

