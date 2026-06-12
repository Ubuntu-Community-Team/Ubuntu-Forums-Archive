---
title: "Mysterious error when trying to install Ubuntu 16.04 next to Windows 7"
date: 2018-01-14
forum: Installation &amp; Upgrades
---

### Post by Angeliq on 2018-01-14
I think I may have messed a bit too much with different OS.

I have had Windows and Remix OS on my old laptop (Fujitsu Lifebook T730 with wacom touch screen) but wanted to try out Ubuntu because of overheating in windows. I already got touch to work on Remix OS but I wanted to play around a bit and even try to triple boot Window, Ubuntu and Remix OS but first I tried just installing Ubuntu to avoid compatibility problems.

I completely wiped my HDD installed Ubuntu, worked great.

After that I tried installing Windows but this messed up the bootloader because the windows os was not on the first partition (surprise,surprise...I forgot about windows' bootloader thing)

I decided to start from scratch. I formatted my hdd, created 2 partitions, one for windows (installed and working) and another for Ubuntu.

Now when I try to boot Ubuntu from USB it only goes from the accessibility screen to the Ubuntu loading screen, hangs for a bit, does not load the GUI, and then i get this:

[IMG]https://i.stack.imgur.com/awIrg.jpg[/IMG]

I tried again, it displays the same error but without the "unclean filesystem" error, the last line being:

```
pwconv: failed to change the mode /etc/passwd to 0600
```

I have no idea what to do, the error just stays there and I am unable to type. If I leave the error, it just turns black with a static (non blinking) text cursor and doesn't boot from USB.

Update: I tried to run boot repair, which booted up fine from USB stick. Here is the log dump:

[https://paste.ubuntu.com/26388492/](https://paste.ubuntu.com/26388492/)



I have no idea what to do next...Please help?

---

### Post by Angeliq on 2018-01-14
Since all the other linux distros I have tried boot up normally, I downloaded Ubuntu 14 and tried it and it worked.

I have not found a solution for Ubuntu 16 but I have tried Ubuntu 14 and it seems to work without problems on my system.

The error may have been caused by a faulty installation iso image or general hardware incompatibility (the laptop is 8 years old).

This question is now closed....but I may have more later on. Off to triple boot!

---

