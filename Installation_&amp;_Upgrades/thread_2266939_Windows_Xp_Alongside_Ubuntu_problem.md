---
title: "Windows Xp Alongside Ubuntu problem"
date: 2015-02-26
forum: Installation &amp; Upgrades
---

### Post by yudhish-mathoorasing on 2015-02-26
Hello everyone, my problem is that I am unable to install windows xp alongside a Ubuntu 14.10 (installed on full partition). I searched over the web on how to deal with that particular problem but it appears that I am still unable to install Windows XP. I am getting the blue screen of death everytime I try to boot from the windows xp cd. Please, can anyone help me out on this one.

Here's a screenshot of my partitions (gparted):
[ATTACH=CONFIG]260228[/ATTACH]

---

### Post by grahammechanical on 2015-02-26
Assuming that this is not a problem with the XP install CD, then I would suggest that installing XP first and Ubuntu second is the better way to do this. I remember hearing years ago that Windows needs to be at the start of the disk.

Not only that in this present situation if you get XP installed you will not be able to load Ubuntu because the Windows boot manager does not recognise any other OS but those from Microsoft. Whereas, the Linux boot loader called Grub will detect an Windows OS and list it in the boot menu.

If you do succeed in getting XP installed you will next be asking for help to load Ubuntu. So, I recommend installing XP first and Ubuntu second.

Regards.

---

### Post by yudhish-mathoorasing on 2015-02-26
Thanks for the reply. Because I've installed ubuntu first and on full partition, I am unable to re-format my computer with the windows cd. Everytime the windows setup has finished loading, the blue screen of death appears. In that sense, I can only install linux operating systems. I don't know why but I just can't install any windows OS. :/ Any suggestions? BTW: the windows cd worked perfectly on another pc.

---

### Post by Mark Phelps on 2015-02-26
It might be because you have the boot flag set on the Linux partition -- which does not need it -- and that may be "confusing" the Windows installer because it needs the boot flag set on the Windows partition.  You should reboot using the Ubuntu installation media, run GParted, and remove the boot flag.

---

### Post by yudhish-mathoorasing on 2015-02-26
I removed the boot flag using gparted on ext4 partition. Would it make things better for windows, if I give the ntfs partition a boot flag.

---

### Post by yudhish-mathoorasing on 2015-02-26
Ok, so I did just what you told me but unfortunately, still stuck with the blue screen of death. 
Here's what the blue screen of death has to say: [I apologize for the image quality]
[ATTACH=CONFIG]260229[/ATTACH][ATTACH=CONFIG]260230[/ATTACH]

---

### Post by yancek on 2015-02-26
According to the link below, you may be better off leaving the space unpartitioned rather than having a prepared ntfs partition, scroll about half way down the page.  This doesn't make much sense but I've never used xp.

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm/](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm/)

Did you now mark the ntfs partition as active?  The link below to another thread at these forums gives a pretty detailed explanation.  If that doesn't work, you've got some other problems.

[http://ubuntuforums.org/showthread.php?t=1649050&p=10278677#post10278677](http://ubuntuforums.org/showthread.php?t=1649050&p=10278677#post10278677)

---

### Post by yudhish-mathoorasing on 2015-02-26
Unfortunately, it did not work. Well I guess it just won't work. Anyways, thanks a lot guys for helping me out.

---

