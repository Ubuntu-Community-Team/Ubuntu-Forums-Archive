---
title: "Help! I can't boot into Ubuntu or Windows (Grub Error)"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by scott28w on 2007-03-07
I just installed ubuntu 6.10 on a new 250 GB WD Hard Drive.  My goal is to dual boot between this and my internal hard drive which has Windows xp.  When I restarted and tried to boot into Ubuntu I got Grub 1.5 Error 21.  When I tried windows I got Error 5. 

By default, the Grub was installed to Hd0.  From reading other posts, I think this may be my problem since my windows hard drive  is SATA, which if I understand correctly means I should have chosen SDA as the location for the grub? I know when I installed it my 80GB (windows) HD was sda and my external was sdb.  So my question is:

a) How can I get back into windows for the time being. I assume I have to reinstall the original bootloader? I just need to get that back and worry about Ubuntu over the weekend.

b) If I were to reinstall Ubunutu from the live CD, and install grub to the correct place, would this get rid of the grub that's supposedly installed on HD0?

By the way I'm very very new to all of this so I may not understand everything.

Your help is greatly appreciated.

---

### Post by Kateikyoushi on 2007-03-07
To get back to windows fast restore the mbr.

Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer.

Is the smaller drive a pata drive ?

---

### Post by confused57 on 2007-03-07
> **Kateikyoushi said:**
> To get back to windows fast restore the mbr.

Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer.

Is the smaller drive a pata drive ?
Do what Kateikyoushi suggests to get your Windows booting, then you might want to read over this thread for setting up your external drive:

[http://www.ubuntuforums.org/showthread.php?t=363306&page=4](http://www.ubuntuforums.org/showthread.php?t=363306&page=4)

---

### Post by scott28w on 2007-03-07
Thanks for the help booting back into windows. It was a big relief..

Kateikyoushi: I'm not sure what a pata drive is.  As far as I can tell I think it's sata?  I'm not really familiar with all this.

Thanks for the link too, I will check that out in more detail when I attempt to do this again.

---

