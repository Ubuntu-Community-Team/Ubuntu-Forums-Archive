---
title: "Dual boot with 12.10 and Windows XP - even after boot-repair"
date: 2012-12-08
forum: Installation &amp; Upgrades
---

### Post by shr33kanth on 2012-12-08
Hello,
I installed Ubuntu 12.10 on an old Sony Vaio with Windows XP and ran into boot-up problem. 

I ran boot-repair after booting in live-cd mode and got:
[http://paste.ubuntu.com/1420128/](http://paste.ubuntu.com/1420128/)

After choosing repair option, boot-repair said the partition table has been fixed: 
[http://paste.ubuntu.com/1420130/](http://paste.ubuntu.com/1420130/)

I boot again and the screen still shows only
"error: no such partition 
grub rescue>"

Could some one please advise what to do next? (I've already tried re-installing 12.10 once).

Thanks in advance.

---

### Post by oldfred on 2012-12-09
Welcome to the forums.

I would try boot repair again. This does not look quite right as it has both partition 1 and partition 6. Not sure if just an issue with boot script or your install of grub.

Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in [COLOR=Red]partition 1[/COLOR] for (,[COLOR=Red]msdos6[/COLOR])/boot/grub.

If that does not work, you can manually reinstall grub.

       sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda


You can also try manual boot:
       
 Manual boot:
See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)

---

### Post by Mister08 on 2012-12-09
> **shr33kanth said:**
> Hello,
I installed Ubuntu 12.10 on an old Sony Vaio with Windows XP and ran into boot-up problem. 

I ran boot-repair after booting in live-cd mode and got:
[http://paste.ubuntu.com/1420128/](http://paste.ubuntu.com/1420128/)

After choosing repair option, boot-repair said the partition table has been fixed: 
[http://paste.ubuntu.com/1420130/](http://paste.ubuntu.com/1420130/)

I boot again and the screen still shows only
"error: no such partition 
grub rescue>"

Could some one please advise what to do next? (I've already tried re-installing 12.10 once).

Thanks in advance.

A good utility I have used in the past when this happened was Super Grub. It will fix MBR and many other things. Give it a try instead of messing with repair discs. [http://www.supergrubdisc.org/](http://www.supergrubdisc.org/) I personally prefer to use the original Super Grub, it isn't as advanced but seems more user friendly and effective. Rescatux is also a good tool to have on-hand, but is a much larger download

---

