---
title: "Upgrade and GRUB problem"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by HP dv4 on 2010-05-22
I have recently upgraded my Ubuntu 9.10 to 10.04. I had no problem until it went to reboot and then it pulled up GRUB as usual. The problem was the it says, "cannot find "put_grub"", and then it goes into GRUB rescue. I think it important to mention that Ubuntu is installed on an external drive. I have had a problem similar to these before in which I had to relocate Grub off of my internal drive. An answer would be greatly appreciated as I can't get into Ubuntu, but I can thankfully get into Windows.

---

### Post by HP dv4 on 2010-05-22
A correction to the above.
It says "error: the symbol 'grub_puts_' not found" instead of what I said above.

---

### Post by menace101 on 2010-05-22
I have roughly the same problem, so I'm going to add to this so someone doesn't have to post the same thing twice. I upgraded to 10.04 from 9.10 except my Windows 7 partition and my Ubuntu partition are on the same internal hard drive. I can load Grub fine without my external hard drive plugged in, but if that's plugged it, it goes into rescue, also, I can no longer load my Windows 7 partition.. so two problems in one, I guess..

And HP dv4, I hope you don't mind me tagging along.. =]

---

### Post by HP dv4 on 2010-05-22
We'll just wait for an answer

---

### Post by slick_nick on 2010-05-23
Another one here. AMD64 with 2 SATA drives, only one operating system: Ubuntu, where the arrival of Lucid Lynx this afternoon broke my GRUB in the same manner as the poor souls above. 

Found this, haven't tried it yet: [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

If I could get my dang box to boot from USB, I might be trying unetbootin to running SuperGrub [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) to see if that did anything...

[COLOR="Red"]EDIT: Just did this, going down for reboot, wish me luck! [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)


Double Edit: SOLVED! See the above link. It's easy![/COLOR]

---

### Post by HP dv4 on 2010-05-23
I can't get that to work either. Since I have Ubuntu on an external drive, I'm just going to format that drive and redo the Ubuntu installation. I installed GRUB in the wrong place anyway, so this will also fix that. I'm getting a bit sick of all of these problems.

---

