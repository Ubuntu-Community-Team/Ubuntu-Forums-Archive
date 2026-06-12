---
title: "How to stop volume from mounting at boot"
date: 2013-02-02
forum: Installation &amp; Upgrades
---

### Post by Nesaskewatch on 2013-02-02
Somehow and in spite of myself, I managed to install Ubuntu on an Asus N56VJ with UEFI. That successful campaign is chronicled [here]("http://ubuntuforums.org/showthread.php?t=2105622"). While doing it I decided instead of moving the windows D:\ (Data) partition -- which was left by windows partition manager smack in the middle of the drive -- I would use the unallocated space in front of it as a /share partition, formatted in NTFS for sharing files between operating systems. That went fine, but ocasionally when I boot it freezes just before the splash screen. When it does not freeze it stops during the splash screen saying something like "/share failed to mount. Press S to skip, M for manual recovery" etc. I press S as I do not want share to mount and it boots fine. 

I decided that the next time it froze I would try pressing S and, what do you know, it worked. My question is; how do I prevent that drive from mounting at boot, and why is it trying to mount in the first place? I didn't give it a mount point, at least I don't think I did. Though I did label it /share... Anyway, here is a pic of my drive in gparted. SDA7 is the miscreant volume

[IMG]http://i.imgur.com/a50UI4Z.png?1[/IMG]

Thanks in advance for any replies.

---

### Post by presence1960 on 2013-02-02
```

```From terminal run ```
gksu gedit /etc/fstab
```

Find the line that references your share. remove that line. On toolbar click Save. Close file. Reboot. The /etc/fstab file controls what volumes are mounted at boot.

The reference will be by UUID. If you need to find the volume's UUID run this command from terminal: ```
blkid
```

---

### Post by sudodus on 2013-02-02
... or keep the entry in /etc/fstab and add the option noauto to the options field (the fourth field)

See ```
man fstab
```

---

### Post by Nesaskewatch on 2013-02-02
Thanks for both tips. Worked like a treat. That fstab manual is perfect. This entry has me a bit worried though: "...it  is  the duty  of  the system administrator to properly create and maintain this file". I'll do my best!

Thanks!

---

### Post by presence1960 on 2013-02-02
> **Nesaskewatch said:**
> Thanks for both tips. Worked like a treat. That fstab manual is perfect. This entry has me a bit worried though: "...it  is  the duty  of  the system administrator to properly create and maintain this file". I'll do my best!

Thanks!

Enjoy!! Don't forget to mark this thread as "Solved".

---

### Post by Nesaskewatch on 2013-02-02
> **presence1960 said:**
> Enjoy!! Don't forget to mark this thread as "Solved".lol Thanks pal. I was busy fiddling with that file and forgot.

---

