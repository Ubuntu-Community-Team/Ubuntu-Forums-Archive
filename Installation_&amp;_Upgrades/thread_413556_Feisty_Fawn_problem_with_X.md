---
title: "Feisty Fawn problem with X"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by slayerlink on 2007-04-19
Hi all
I can't boot Feisty Fawn live cd, Xserver crashes, this is the error:

(EE)Vesa(0): No matching modes
(EE)Screen(s) found, but none have a usable configuration
Fatal server error:
     no screens found

I reconfigured X whit dpkg-reconfigure xserver-xorg, but the problem persists, my graphic card is ATI Mobility Radeon X1400.

I need feisty xDD, please help me xD.

---

### Post by orbital on 2007-04-19
> **slayerlink said:**
> Hi all
I can't boot Feisty Fawn live cd, Xserver crashes, this is the error:

(EE)Vesa(0): No matching modes
(EE)Screen(s) found, but none have a usable configuration
Fatal server error:
     no screens found

I reconfigured X whit dpkg-reconfigure xserver-xorg, but the problem persists, my graphic card is ATI Mobility Radeon X1400.

I need feisty xDD, please help me xD.

I have the exact same problem with the exact same graphics card... Hopefully someone can help

---

### Post by carpex on 2007-04-19
Same problem here with x1400 and Feisty x64.

GL

---

### Post by kellemes on 2007-04-19
Guys, have you looked at the logfiles? They can get you on the road maybe?
/var/log/Xorg.0.log(.old)

---

### Post by carpex on 2007-04-19
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/89853](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/89853)

I am trying the fix and getting back...

GL

---

### Post by orbital on 2007-04-19
> **carpex said:**
> [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/89853](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/89853)

I am trying the fix and getting back...

GL

Page found

---

### Post by carpex on 2007-04-19
I just tried changing the HorizSync and VertRefresh and that didn't fix it. dpkg-reconfigure xserver-xorg didn't work either....

GL

---

### Post by orbital on 2007-04-19
> **carpex said:**
> I just tried changing the HorizSync and VertRefresh and that didn't fix it. dpkg-reconfigure xserver-xorg didn't work either....

GL

I tried that too, did nothing.

---

### Post by arquetipo on 2007-04-19
i have an asus 2 duo with an x1600 card

same problem with xserver

---

### Post by Immolatus on 2007-04-19
maybe get the firmware on disk or usb and install it in text mode?

---

### Post by carpex on 2007-04-19
Could do, but they did not supply a .deb for a x64 install, which is what I am looking for. 

GL

---

### Post by carpex on 2007-04-19
...

---

### Post by G-Force on 2007-04-19
Same problem here, Asus M6Va with an ATI Mobility Radeon X700.

---

### Post by arquetipo on 2007-04-19
Let's try to focus on this topic. Joining the discussion it will be easier to fix.

[http://ubuntuforums.org/showthread.php?t=413713](http://ubuntuforums.org/showthread.php?t=413713)

---

### Post by GeorgeFRS on 2007-04-19
Same problem here. First appeared in Fiesty Herd 5, but im now using the release cd. Works with both amd64 and i386. I have a mobility x700 with a 1280x800 panel.

The fix at [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/89853](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/89853) seems to work for me. Steps I took were:

1) Wait for ubuntu to load to black screen with no hdd activity

2) Press ctrl+alt+f6

3) type "sudo nano /etc/X11/xorg.conf" and press enter

4) Find the line:

Section "Monitor"

5) Underneath that line put the two lines

HorizSync         36-52
VertRefresh     36-60

6) press ctrl+o then ctrl+x

7) Press ctrl+alt+F7 to get back to the black screen then ctrl+alt+backspace to restart the X server

Not sure if this will fix it for anyone else but its worth a shot...

---

### Post by JFreakDK on 2007-04-19
I have a similar problem with my ATI x1600 on my HP nc8430 laptop

---

### Post by patrick1314 on 2007-04-19
Hi

I just posted this in the other thread, so I'll post here too.

"I had the same problem with my X1400 card not 5 minutes ago.

What I did was follow the normal *[I]manual*[/I] install instructions on the ATI Linux Wiki: [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.36.5_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.36.5_Driver_Manually)

But instead of downloading the driver with firefox as I normally would, I used 'wget'.

```
wget -c https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.36.5-x86.x86_64.run
```

Apart from that, I followed the instructions exactly and it worked like a charm."

---

### Post by KennyG3987 on 2007-04-19
[http://ubuntuforums.org/showthread.php?t=413997](http://ubuntuforums.org/showthread.php?t=413997)

try this worked for me

---

### Post by orbital on 2007-04-20
Thanks

---

### Post by slayerlink on 2007-04-20
> **GeorgeFRS said:**
> Same problem here. First appeared in Fiesty Herd 5, but im now using the release cd. Works with both amd64 and i386. I have a mobility x700 with a 1280x800 panel.

The fix at [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/89853](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/89853) seems to work for me. Steps I took were:

1) Wait for ubuntu to load to black screen with no hdd activity

2) Press ctrl+alt+f6

3) type "sudo nano /etc/X11/xorg.conf" and press enter

4) Find the line:

Section "Monitor"

5) Underneath that line put the two lines

HorizSync         36-52
VertRefresh     36-60

6) press ctrl+o then ctrl+x

7) Press ctrl+alt+F7 to get back to the black screen then ctrl+alt+backspace to restart the X server

Not sure if this will fix it for anyone else but its worth a shot...

Before startx more problems, omg

Fatal server error:
Caught signal 11. Server aborting

:popcorn:

---

### Post by FraserKp on 2007-04-20
In the header of the xorg.conf file are the lines:
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

..this got me going again with X on Feisty. Although I do have to now figure out how to get my ati acceleration working again.

---

### Post by ambien on 2007-04-21
Same problem. P4 ATI X1300

Never got acceleration to work in Edgy Eft...

*BUT*

I found a quick fix for the moment!

Press escape while grub is loading, and load using 'kernel 2.6.17-10'

This loads up well enough, but I don't have acceleration. Plus it seems even slower than Edgy without acceleration :(

---

### Post by w1ski on 2007-05-24
Why does the command sudo dpkg -reconfigure xserver.xorg not work.  Gives errors???

I have only a terminal work with - no gui.  None of the solutions work????

Thanks...

---

### Post by bert79 on 2007-05-24
me to i have a ATI RADEON 7000

---

### Post by Ub1476 on 2007-05-25
Lucky day;)

Follow this guide: [Linky]("http://ubuntuforums.org/showthread.php?t=448809&highlight=feisty+fawn")

Works!

Cheers
Ub

---

