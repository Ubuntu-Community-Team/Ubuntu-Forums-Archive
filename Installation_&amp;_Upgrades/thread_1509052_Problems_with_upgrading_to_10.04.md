---
title: "Problems with upgrading to 10.04"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by tzirtzi on 2010-06-13
Hello all :)

I've been running netbook remix 9.04 on a Toshiba NB200 netbook for about six months without any really major problems. One problem that it does have (and this is a hardware problem, not to do with linux), is that when it's been on for a while and then is restarted or switched on only a short time after being turned off, it won't start - this seems to be something to do with overheating. Either way, for whatever reason, it can't restart.

Yesterday I clicked to upgrade to 10.04. It appeared to run smoothly until restarting - at which point it wouldn't start, as expected, as described above. However then when I started it again after letting it cool down, it didn't managed to start properly into Ubuntu, but stopped with an error. It did this every time I started it, so I put 10.04 (not netbook remix this time) onto a usb stick, started it from that, backed up my files, wiped it and installed from there. This time it managed to start into the OS, but every time I tried to start it again after that, same thing. So I reinstalled it again. Same thing. However, this time I have worked out that directly after selecting Ubuntu on grub, it goes to a cursor on a black screen - if I then press Enter, it sits for 6-10 minutes and then starts successfully. If I don't press Enter, it goes to the error after about 30 seconds. The full error message is:

> Gave up waiting for root device. Common problems:
    - Boot args (cat /proc/cmdline)
    - Check route delay= (Did the system wait long enough?)
    - Check route= (Did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disc/by-uuid/6a8f4c5f-64b5-4ad9-99a4-c4717233d804 does not exist. dropping to shell!

Could anyone enlighten me as to what might be going on here? Might it be some compatibility problem with the hardware (I had problems when originally trying to get ubuntu working on this netbook)? Might I be able to fix it - it's not very practical having to wait so long for my computer to start every time...

Thanks in advance! :)

---

### Post by darkod on 2010-06-13
Grub2 on the MBR might be looking for the older partition UUID that was overwritten with the latest install.

To see your UUIDs type:

sudo blkid

Check whether that 6a8fxxxxx UUID exists. If it doesn't, the error is quite normal. Boot your ubuntu, and to make sure you reinstall grub2 to the MBR just do:

sudo grub-install /dev/sda (I guess your hdd is /dev/sda if you have only one, change in the command if needed)

See if the error is still there after that.

---

### Post by tzirtzi on 2010-06-14
Thanks very much for your reply :) I've tried *sudo blkid*, but the UUID in question is not missing - I've checked, and it refers to the extended partition on which ubuntu is installed. Is there any point in trying the *sudo grub-install...* regardless? And would that wipe the rest of the grub boot options?

---

### Post by darkod on 2010-06-14
It doesn't wipe any boot options. But if the UUID exists and it's reported it doesn't, there is not much point trying the grub-install.

---

### Post by tzirtzi on 2010-06-14
Okay, I won't try that then.. is there anything else I might try?

---

### Post by darkod on 2010-06-14
When you get the boot menu, highlight the ubuntu entry but don't hit Enter, hit 'e' instead. That will show the boot lines.
Delete the line starting with search.
After that press Ctrl+X to boot.

If that worked, if it boots faster, there is a way to disable the search line so you don't have to do the same every boot.

---

### Post by tzirtzi on 2010-06-14
Hmm. Doesn't *seem* to change anything. The booting seems to have got a bit faster - this afternoon it has been only taking maybe 2 minutes - so it's a little hard to tell, but I still get the black screen where I have to press enter to prevent it getting an error message and quite a long wait.

---

### Post by tzirtzi on 2010-06-19
Hello again,

I'm still getting exactly the same problem - now that I've been using it for a few days it seems that the startup time varies widely and randomly. Sometimes it's as quick as 2 minutes, sometimes as long as 10. It still gets that same error message if I don't press enter (a lot of times) when it first goes to the black screen when starting after selecting Ubuntu on Grub. 

I was wondering if anyone could offer me any more suggestions?

Thanks

---

### Post by tzirtzi on 2010-06-27
Just bumping this thread again in the hope someone might have any suggestions for what I could try.

I don't know if it makes any difference, but I've worked out that I have to press enter until the cursor is at the bottom of the screen - any less, and I get the error message. Bizarre as that sounds...

---

### Post by darkod on 2010-06-27
If you have only one hdd, that is named /dev/sda. Once you manage to successfully boot ubuntu, execute in terminal:

sudo grub-install /dev/sda
sudo update-grub

If you have more hdds, you have to install grub2 to the disk you are booting from, usually the disk where ubuntu is installed. But if you are not sure, post first the results of:

sudo fdisk -l

and we'll see which commands you need to run.

---

### Post by tzirtzi on 2010-06-28
I only have one hd, so I've tried that - it doesn't seem to have had any effect, I'm afraid..

---

