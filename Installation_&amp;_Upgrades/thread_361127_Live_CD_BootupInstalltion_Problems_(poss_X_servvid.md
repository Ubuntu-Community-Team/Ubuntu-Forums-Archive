---
title: "Live CD Bootup/Installtion Problems (poss X serv/vid card related)"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by greenxeyezz on 2007-02-14
Okay, some friends at work turned me to ubuntu.

So i decided to start.

I downloaded the 6.06 LTS Version and the 6.10 Version.

Was having problems just BOOTING to a live  CD or instllation.

The first 10 times, it would lock up about 90% through and I would have to restart.

Tried the 6.06 LTS version, and it said something about X server erroring out and i couldnt even see the log file

i then went to 6.10 and got the "boot" option to show up. had a string of things to try, so i added noapic and nolapic at the end.

Managed to get the bar to go across and then i got another X server error. something about no screen detected.


I do not want to delete the HD currently as it has my windows installation and i think i could at least be able to "dual" boot these or at least see the LIVE CD working.


Any suggestions?!?!



I have 1 gig ram
p4 3.4 ht
ati x700 pro 256 with latest windows drivers
sata 160 gig hd

---

### Post by Afkpuz on 2007-02-15
I had this problem too.  I'm also running an ati x700 and the X server error has to do with the driver that linux is using.  There are probably other work arounds, but this is what worked for me.  Download another copy of linux (6.06 LTS), but get the alternate version.  You can find alternates on the ubuntu website download section.  Put it on CD and restart.  "Install in text mode".  Hopefully, that will let you install the base system, then, you'll need to change your video driver.

Just boot from your hard drive and you'll either be taken to a command promt, or to an error window. Just exit out of the error window and you should get a command prompt. Enter your username and password that you made during install. 

Now you need to enable the restricted repository.  This link explains how:
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

Then, enter each of these lines into the command prompt: 

    ```
 sudo apt-get update

     sudo apt-get install linux-restricted-modules-$(uname -r) 

     sudo apt-get install xorg-driver-fglrx

     sudo depmod -a

     sudo aticonfig --initial

     sudo aticonfig --overlay-type=Xv

```

Finally, reboot and test. Type this into the command prompt.

    ```
 sudo shutdown -r now
```


That fixed it for me, and it should for you too.  All this information can be found at this site.
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

Also, if you decide to use 6.10, use this site.
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)


Good luck!

---

