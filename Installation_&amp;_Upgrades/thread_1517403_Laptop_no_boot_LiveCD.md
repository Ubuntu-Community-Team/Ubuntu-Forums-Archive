---
title: "Laptop no boot LiveCD"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by Don DeGregori on 2010-06-25
I have older Fujitsu P 5010D laptop. No problem with any earlier Ubuntu versions. But,10.04 does not like my laptop! What has happened? (or what were you thinking removing what works?) The LiveCD starts, goes through many moving dots and then everything just stops, probably the next step in the boot sequence. The illness finally gets a little bit better by using Alternate version. I had to choose Low Resolution graphics and a few more options. In fact, I was able to install the Alternate, but have to choose Recovery Mode. Lots of color flashes, and only one display choice 1024 x 768. Monitor (laptop) is Unknown and Refresh rate is 0 Hz. And to top it off wireless doesn't work, even after I downloaded the proper driver that Ubuntu says to. Brought in all the updates. Same trouble. Then I tried the upgrade from 9.10. Took forever! Totally No Joy! I guess I have to go back to 9.10. A sad state of affairs. I think there needs to be a 10.04.1 LTS! to put back my video driver. Then, I'll try again.  :confused:

---

### Post by Don Barzini on 2010-06-25
From one Don to another......:p

That Fujitsu laptop is a bit old. Probably doesn't have a lot of memory and it may be possible the video might even be grabbing some of the machine's memory.

If you can get into **Recovery Mode**, maybe there might be a few things that can be done to bring up a Gnome session.

Have you tried booting with the **nomodeset** option?

If not, try this.....

Boot into the **Recovery Mode** and go to a root session.

Open your **/etc/default/grub** file with a text editor and edit the following line......

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Add the term **nomodeset** to the end of the line within the quotes...

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

Then run **update-grub**...

```
update-grub
```

Type **reboot** and see if the machine now at least boots up to a graphical login.

---

### Post by Don Barzini on 2010-06-25
A link that may also help you.....

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

