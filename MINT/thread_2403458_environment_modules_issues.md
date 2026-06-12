---
title: "environment modules issues"
date: 2018-10-11
forum: MINT
---

### Post by gostal on 2018-10-11
Hi,

Please forgive me for posting here as I am not an Ubuntu user. I used to be a looong time ago and I really liked it but sadly I had to quit Ubuntu. Chances are that I will become one again in the not too distant future as Ubuntu now is the preferred distro at work replacing OpenSuse which has been on my desktop for several years. Now I am a fairly new user of Linux Mint which I have on a laptop since about six weeks ago. As Mint is based on Ubuntu and compatible to it asking questions also here is relevant.

I have installed the Ubuntu package environment-modules version 4.1.1-1 but there are some issues, see my post at the Mint fora:
[https://forums.linuxmint.com/viewtopic.php?f=47&t=279377]("https://forums.linuxmint.com/viewtopic.php?f=47&t=279377")

There you can see that the program is not initialised during graphical login as **/etc/profile** apparently is not read. I gather from a really old post, now dead, that the situation may be the same in Ubuntu. The old post contained irrelevant answers that were useless. I have solved the problem by editing **~/.bashrc** to directly source **/etc/profile.d/modules.sh** which is put there during installation. See the Mint post for details. My question basically is if there is a way to tell the graphical login process to read **/etc/profile** or something like that.

The other problem is that if I enter **module avail** which queries the system for available modules the output repeats itself. Again, see the Mint post for details. For user added modules this is not the case, however. These are listed once as expected but I hadn't yet tried that at the time of the Mint post. I don't know if this is the case also on Ubuntu but if it is can it be easily fixed?

---

### Post by howefield on 2018-10-11
Thread moved to the "*MINT*" forum.

---

