---
title: "ubuntu 10.10 on a separate ssd and win 7 on fake raid0 array"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by Kfiat on 2011-05-11
Hi, i have recently installed ubuntu on my laptop (as one and only os)  and i`m pretty happy with it. Now I would like to dual boot between win7  hp64 and ubuntu 10.10 on my desktop. I would like to install ubuntu  10.10 on a separate ssd drive, win 7 is placed on a fake raid0 array. Could you please give  me some advice how to achieve the following:

1) ubuntu 10.10 as a default booting os without showing boot selection screen,
2) win 7 as a secondary booting os via boot selection screen (i`d much prefer if it simply depended on which drive - ssd or fake raid I would choose to boot from bios - my mobo - ga-p35-ds3p)
3) make those 2 os`s totally and absolutely separate when it comes to  boot manager so I can simply physically remove ssd with ubuntu anytime  without dire consequences for win 7 boot.
I`d really appreciate if someone could point me in the right  direction.

Cheers

---

### Post by jerrrys on 2011-05-11
here&#8217;s how it works for me...
    
    i have 4 hdd&#8217;s that i keep on line.  any drive or drives can be removed, inserted, moved to a different slot, it will not matter to grub.  when i install to a harddrive i will pull all other drives except the one to be installed on.  after the install all hdd&#8217;s are plugged in and should be automatically recognize by grub.  if not. a 'sudo update-grub&#8217; will fix it..
    
    this works well with linux however i do not run windows and think it will work just the same, but can&#8217;t say for sure.

---

