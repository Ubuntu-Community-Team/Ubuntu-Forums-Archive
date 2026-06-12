---
title: "Reinstalled Windows, grub won't work. (UBUNTU UNUSEABLE)"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by Ryupower on 2008-06-05
hello,I had to reinstall windows and then GRUB was gone. With the LiveCD I did:

>sudo grub
>find /boot/grub/stage1
 
put the result ( which was hda0,1) in like this:
>setup (hda0)
>quit


I rebooted and my grub menu was there. I selected the Linux kernel I Wanted to boot, but it gave me an error telling me that the device isn't bootable or something like that.

So I tried the thing over again, but this time I got:
> 
grub> find /boot/grub/stage1
 (hd0,1)

grub> setup (hd0)           

Error 12: Invalid device requested

grub> find /boot/grub/stage1
 (hd0,1)

grub> setup (hd0)

Error 12: Invalid device requested


Why am I getting this? And how can I boot from ubuntu again? I really don't feel like reinstalling feisty, upgrading twice to hardy, editing my Xorg, and installing all the load of software I want again for the fourth time in 4 weeks. 


I really appreciate your help, thank you.

---

### Post by petzworld999 on 2008-06-05
You forgot to set the root.

```


grub> find /boot/grub/stage1
(hd0,1)

grub> setup (hd0)

Error 12: Invalid device requested

grub> find /boot/grub/stage1
(hd0,1)

grub> setup (hd0)

Error 12: Invalid device requested 


```

Instead, do 

```


grub> find /boot/grub/stage1
(hd0,1)

root (hd0,1)

grub> setup (hd0)


```

---

### Post by Ryupower on 2008-06-05
XD how dumb of me to forget that, thanks.

But when I rebooted, it still didn't work. :(
I tried every one of the ubuntu entries besides the memtest. And I keep on getting a message that says that the partition "can't be mounted".

Is it because I installed ubuntu on a JFS-formatted partition, rather than EXT2/3?

---

### Post by Ryupower on 2008-06-05
someone?

---

### Post by ssican on 2008-06-05
Recovering Ubuntu after installing Windows:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)

EDIT
Grub - Error 12:
[http://users.bigpond.net.au/hermanzone/p15.htm#12_](http://users.bigpond.net.au/hermanzone/p15.htm#12_)

---

