---
title: "Grub Error 17"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by Rocky44 on 2007-09-02
I've installed Ubuntu, and I'm getting Grub Error 17 whenever I boot up my computer.  I burned SGD, but that still doesn't work.  When I try to reinstall Grub, it doesn't work.  Then, when I try to boot ubuntu from the cd, it says it was 'unlucky' and failed to boot up.  What I'm running (or trying to.) is a dual boot with Windows on my main drive, and Ubuntu on a slave drive.  Previously, I was getting error 18, but I was able to fix that.  I'm new at this, so if there's any additional information I can provide, just tell me.

Edit:  By cd, I mean SGD.

---

### Post by Pumalite on 2007-09-02
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

Try this from a terminal (Applications/Accessories/Terminal):

Code:

sudo grub
find /boot/grub/stage1
root (hdx,x)
setup (hdx)
quit

Substitute your results from the find command for (hdx,x).

---

### Post by Rocky44 on 2007-09-02
I knew I forgot something.  I did already do that.  

> grub> find /boot/grub/stage1
 (hd1,0)
 (hd1,2)

grub> root (hd1,0)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+17 p (hd1,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.


---

### Post by rsambuca on 2007-09-02
In order to get grub to load properly in this case it needs to be in the MBR, which is hd0, not hd1.

Also, why do you have two grub stage 1 locations (hd1,0) and (hd1,2)?  If you are dual booting XP and ubuntu, there should only be one /boot partition.

---

### Post by Rocky44 on 2007-09-02
I really have no idea.  I do remember I attempted installing ubuntu a number of times, all on the slave drive.  The only thing that could have done that (I think) is the text based boot cd, which I used to install ubuntu, to fix error 18.

---

### Post by Pumalite on 2007-09-02
rsambuca is right.

---

### Post by Rocky44 on 2007-09-02
Okay, so what I should do is run that, but replace setup (hd1) with setup (hd0)?

---

### Post by Pumalite on 2007-09-02
Yes

---

### Post by Rocky44 on 2007-09-02
Okay.  I just did that.  I hope it works.  Thanks guys/girls.

---

### Post by Pumalite on 2007-09-02
Sure, junior.

---

