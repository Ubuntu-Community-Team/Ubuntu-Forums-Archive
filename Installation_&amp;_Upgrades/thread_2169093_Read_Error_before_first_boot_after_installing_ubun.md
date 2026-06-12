---
title: "Read Error before first boot after installing ubuntu 12.04 LTS"
date: 2013-08-20
forum: Installation &amp; Upgrades
---

### Post by Vixx_Daru on 2013-08-20
I am not new to Ubuntu, though I am not an expert either. I am a casual Ubuntu user, learning few things whenever a problem arises. I have been using Ubuntu for 5 years and I am a regular visitor at UbuntuForums and I am very grateful to all the answers I found here all these years. I never found it necessary to start a new thread here as all my problems got solved in other already available threads. I found the solutions for each and every problem I got in the phase of upgrading my Ubuntu from 9.10 to 13.04 and back to 12.04. I am very grateful for such a great help from U. Thanks a lot.

But, I have come up with a strange problem recently with my Ubuntu installation. I have been trying to solve it for 3 days continuous, but not able to solve it. So, I am posting this new thread with my specific problem. I don't know whether anyone else gone through this problem before. Please help me....

I am using a HP laptop with....
[LIST]
[*]Intel Core 2 Duo, 4GB RAM.
[*]Ubuntu 12.04 as my base OS.
[*]320gb HDD
[*]disk partitions :
[LIST]
[*]root (i.e., /)
[*]home (i.e., /home)
[*]swap area
[/LIST]
[/LIST]

I was using Ubuntu 12.04 for a while and everything was working fine. One evening when I started my system, there was boot time error: 
[B]error: hd0 out of disk 
[/B]
As I was having a separate partition for my root (/) and being sure there won't be any data loss, the very first thought I got was to do a fresh install, so I put a live USB and installed Ubuntu 12.04. I came up with the **same error again**. Then I started doing my research on different ubuntu forums including this one trying every solution suggested.
After doing a few more re-installations, I came up with **different errors**:
[U][B]
once:[/B][/U]
[B]error: hd0 out of disk
grub rescue>
[/B]
_**some other time:**_
**error: you need to load a kernel first**

_**some other time:**_
**grub>**

_**some other time:**_
[B]GRUB MENU
showing the choices, if I select the latest kernel (which is the only one, as it is the fresh install), it shows a blank screen with a blinking cursor.
[/B]
_**The solutions I tried:**_

[LIST=1]
[*]lot of **reinstallations** in the thought that there might be some problem at the time of installation
[*]**Boot-Repair **from a *live USB* with no errors
[*]**GRUB purge and re-install **from a *live CD* with no errors
[/LIST]

At last, my system is showing only one error:
**Read Error**

The very first thing I was not able to understand from the help posts is the reason why those errors are arising..
what is the meaning of **hd0 our out of disk**?
what is the meaning of **Read Error**?
what is the meaning of getting a error like **you need to load a kernel first** on the first boot after a fresh install?

I tried all the solutions that I found useful and those I understood. But all went in vain. I am still suffering from this problem of not able to boot. 
Please suggest me what to do. I'll be grateful to you for the solution of my problem. Thanks in advance.

---

