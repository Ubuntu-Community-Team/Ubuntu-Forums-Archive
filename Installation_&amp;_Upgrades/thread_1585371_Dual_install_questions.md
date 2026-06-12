---
title: "Dual install questions"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by U_buntu on 2010-09-30
Can you do a Dual installation when XP is already installed?

---

### Post by Cavsfan on 2010-09-30
> **U_buntu said:**
> Can you do a Dual installation when XP is already installed?

Sure you can! I have Windows 7 and it had to be installed first.

---

### Post by oldfred on 2010-09-30
XP does not have any tools to resize its partition. With win7 or Vista it is best to use the windows tools to resize the windows partition first. You can just install side by side and the installer will shrink the XP partition (assuming you have space). Or you can use gparted to shrink XP so you have more control over the amount of space you allocate to Ubuntu and then install to the free space created.

Some links:
Resize windows partition info:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows)

Dual Boot Win7 & Ubuntu
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Older but similar:
Dual Boot win/Ubuntu
[http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html)
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

---

### Post by U_buntu on 2010-09-30
So you can not use Ubuntu to grab space? You would need to first make the partition on the windows side, then go for the install?

---

### Post by Cavsfan on 2010-09-30
> **oldfred said:**
> You can just install side by side and the installer will shrink the XP partition (assuming you have space). 

> **U_buntu said:**
> So you can not use Ubuntu to grab space? You would need to first make the partition on the windows side, then go for the install?


Yes, see **oldfred**'s remark above. When you install Ubuntu you will see that option.

---

### Post by U_buntu on 2010-09-30
Ahh ok, i miss read. Thanks

---

### Post by Cavsfan on 2010-09-30
> **U_buntu said:**
> Ahh ok, i miss read. Thanks

I installed after Windows Vista a long time ago and I had to defragment my hard drive before it would allow 
me to create enough room. But, I did that on the windows side. Now, Ubuntu is a lot better and may handle that 
task better now. You will just have to give it a try. I have win 7 now along with Ubuntu.

---

### Post by U_buntu on 2010-09-30
ahh, well thus far I love ubuntu. I wanna get others on it, but incase of some weird flip outs i figured I do a dual boot for em. i personally want completely of windows entirely.

---

### Post by Cavsfan on 2010-09-30
> **U_buntu said:**
> ahh, well thus far I love ubuntu. I wanna get others on it, but incase of some weird flip outs i figured I do a dual boot for em. i personally want completely of windows entirely.

I would do the same, but I keep windows around just for my wife and son (directx 10) and to know what I am doing
to help friends out. When you get the dual boot thing going, you could check out the tutorial in my sig. as it makes things easier.
And if you ever want to know anything about GRUB2 (the bootup menu program) find **drs305**. He has several tutorials about Grub2 
in the tutorial section of the forum.

---

### Post by U_buntu on 2010-09-30
Cool, thanks

---

### Post by Cavsfan on 2010-10-01
> **U_buntu said:**
> Cool, thanks

Sorry I forgot to mention **oldfred **knows a lot about GRUB2 and dual booting with windows. 
So between the two of them there's not a lot they can't figure out!

---

### Post by aNDoz on 2010-10-01
> **oldfred said:**
> XP does not have any tools to resize its partition. With win7 or Vista it is best to use the windows tools to resize the windows partition first. You can just install side by side and the installer will shrink the XP partition (assuming you have space). Or you can use gparted to shrink XP so you have more control over the amount of space you allocate to Ubuntu and then install to the free space created.

Some links:
Resize windows partition info:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows)

Dual Boot Win7 & Ubuntu
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Older but similar:
Dual Boot win/Ubuntu
[http://members.iinet.net.au/~herman546/p23.html]("http://members.iinet.net.au/%7Eherman546/p23.html")
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

If I just install, will it currupt/delete my windows data?
If I use Gparted to shrink the windows partion will I loose/currupt windows data?

---

### Post by oldfred on 2010-10-01
Anytime you edit partitions there is a risk. It is always a good idea to have good backups.

Windows requires 20-30% free space to work well. NTFS has trouble writing when there is not enough room. So just do not shrink windows too much. If Vista or 7 use the tools in those to shrink the windows partitions. If XP use gparted.

---

