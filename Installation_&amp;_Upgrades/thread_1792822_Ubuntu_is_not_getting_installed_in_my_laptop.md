---
title: "Ubuntu is not getting installed in my laptop"
date: 2011-06-28
forum: Installation &amp; Upgrades
---

### Post by reddylast on 2011-06-28
```

```Hi,

I tried to install ubuntu 10.04 and 11.04, but did't successed . After many attempts when I tried to install ubuntu 10.04 in text-mode, I was able to install it completely. But when I reboot my laptop after completion of installation process it displayed me a blank pink screen (which is ubuntu theme) & nothing else and laptop get halted. Same things happened when I try to install ubuntu in normal mode (graphics mode). When I tried to install it.....it displayed few messages on screen (but no error messages)..and after 2 or 3 screen my laptop get halted and I see only blank pink screen.

Do my graphics card is causing this problem ? or anything else ?

My Laptop Configurations are as :

Processor : Intel(R) core (TM) 2 Duo CPU T6500 @2.10GHz  2.10 GHz
Intalled Memory : 4.00 GB (3.75 GB usuable)
Display Adaptor : NVIDIA GetForce 8200M G 
Hard Disk : 320 GB

Currently win-7 (64-bit) is installed in my laptop.



Please help me.

Thanks in Advance.

Regards,
Reddy

---

### Post by mörgæs on 2011-06-29
Hi, welcome to the fora.

There is a lot of advice for Nvidia here:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by reddylast on 2011-06-29
Mörgæs, Thank you so much for your help. Above thread link helped me a lot. Now I  finally managed to intall ubunt 11.04 on my laptop.

I followed following steps to install it...

1. Ran Webi.exe file (inside win -7) and extracted all files into a separated directory.
2. rebooted my computer after completion of above process.
3. This time I rebooted my computer with ubuntu (instead of win-7).
4. Then it took me to screen of menu with 3 different options ( generic mode, recovery mode & win-7).
5. there I choose recovery mode & being able to login to the system (after following few steps).
6. After login, I opened terminal and typed following commands to resolve graphics card related issues :

$ cd /etc/default
$ sudo getedit grub

and changed line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to

GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"

$ sudo update-grub

7. Then I connected my internet and updated my drivers by system>>administrator>>additional drivers. (however I think this step was not necessary at that time...I would also have been done this latter :) )

8. Rebooted my computer again.

9. This time I choose genetic mode ....aaahaaa...everything worked fine..


Hope this may help others too..:) :) :)

:)
:)
:)

Regards,
Reddy

---

### Post by mörgæs on 2011-06-29
Good that you got it working! Please mark the thread 'solved' using 'thread tools'.

---

