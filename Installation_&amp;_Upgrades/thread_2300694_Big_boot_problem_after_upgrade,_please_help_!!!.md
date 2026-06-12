---
title: "Big boot problem after upgrade, please help !!!"
date: 2015-10-27
forum: Installation &amp; Upgrades
---

### Post by rob141 on 2015-10-27
Hello every one. Here is the situation

- I had ubuntu version 14.04 and all was working great. Today while i was at work, i was logged in my laptop trough teamviewer and i decided to start the upgrade to 15.04 remotelly so this way i would not have to wait when i would get home later.

- So i did start it and all seemed to go well although i saw some error while installing that i had to click continue with no other choices if i remember.

- when the upgrade was over, i was still connected and login to ubuntu through teamviewer and since its an upgrade, i decided to reboot. Then i could not connect anymore on my laptop.

- When i got home, my laptop had a black screen so i manually powered it off. Then when i powered it back on, when i got to the OS choosing option ( i have still windows 7 on dual boot just in case ) so i choose ubuntu as usual and then i just got the error that you can see on the picture i have add as attachment to this thread. 

- I have still the ubuntu live cd of version 14.04 and it still work if i boot with it but i dont know how to fix this problem.

Do i have to re-install everything or is there something i can do to fix this ? please i would rather have a way to fix this then to loose everything and re-install.

---

### Post by courseinmiracles2 on 2015-10-27
Is it an old laptop? 32 or 64 bit?

---

### Post by rob141 on 2015-10-27
thx for the fast reply, i have a gateway 64bit and i had also installed the version 64bit of ubuntu 14.04 originally.

---

### Post by courseinmiracles2 on 2015-10-27
This might be worth reading over:
[http://askubuntu.com/questions/35722/what-is-kernel-panic](http://askubuntu.com/questions/35722/what-is-kernel-panic)

But if I were you I'd re-install 14.04.
There's a lot of things that could have cause this...sorry!

---

### Post by rob141 on 2015-10-28
Thx but i'd rather not have to re-install and if ever i really have to, i will install version 15.10 instead of going back to 14.04. Is there any way to fix this ?

---

### Post by rob141 on 2015-10-28
I must add that when i boot, i can actually get to the boot loader and choose advance options then i see a bunch of ubuntu version ( i think it is that ). Its says generic and safemode and 1 or 2 diferent one wich i cant remember right now. They all have numbers at the end and the newest one finish with 51 so i tried 50 and 49 and no luck i still could not boot but do i have to go lower in the numbers or is there anything i could do with that ?

---

### Post by kansasnoob on 2015-10-28
I believe that 14.04 should not be offering direct upgrades to 15.04. But it is so I filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1510920](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1510920)

Hopefully I'll get an answer there soon.

---

### Post by rob141 on 2015-10-28
Thx but if i run the 15.10 live cd, is there any way that i can run the terminal and see the logfile of what happend exactly ? What error i may have had during the upgrade to 15.04. I am not completelly sure that i had version 14.04, i originally download and installed version 14.04 LTS but somehow i think that i may have done an ungrade to version 14.10 if i am not mistaken. When i try to boot and before it end up giving the kernal panic error, i see ubuntu 15.04 so i guest that at some point the upgrde kinda succeeded. Is there a way that i can only re-install the kernel itself without redoing everything ?

---

### Post by kansasnoob on 2015-10-28
It turns out this is intentional:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1497024](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1497024)

So when 15.04 reaches EOL I guess we'll also see 14.04 -> 15.10 upgrades.

I'm not surprised to see borkage after such an upgrade though.

---

### Post by kansasnoob on 2015-10-28
Being certain to use the -s suffix you could maybe see what would happen if you ran:

```
apt-get install linux-generic -s
```

You could look in /var/log/dist-upgrade to see if you can figure out what went wrong, but the logs are long and time consuming to read.

---

### Post by rob141 on 2015-10-28
I will try this as soon as i get home and i may post either the log file or part of it here. 

I also remember yesterday, while the upgrade was going on, seeing some fglrx errors. Does it make a difference if i had installed the propriatary driver from ATI instead of the ati drivers from ubuntu ?

---

### Post by rob141 on 2015-10-29
Thx very much for the help but unfortunatelly, nothing worked, So i just reinstalled version 14.04. I think i will stay this way for a while before even thinking of going throught this again loll.  Still thank you very much for your help ;)

---

