---
title: "Windows 7 and Ubuntu 10.04 from a PC that initially had Windows XP and Ubuntu 10.04"
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by BJ1110 on 2010-08-25
Hi...

After a while ago, for whatever reason, Windows decided to completely give up on me, leaving 192GB of my hard drive's primary partition unusable. I don't dislike not having Windows on my computer, but I have a lot of programs I use that Wine and PlayOnLinux just can't handle. Not to mention, for some reason, Ubuntu can't pick up my full hardware capabilities.

Now, to clarify, I currently have Windows XP SP3 as my main OS on my main partition. It hasn't worked for a little while. I also have Ubuntu 10.04 on another section of my PC, taking about 39 GB of hard drive space on a separate partition. I want to install Windows 7 over the existing partition for Windows XP, without removing Ubuntu from my computer. Does anyone know if I will be capable of doing this safely? Maybe have a tutorial or something how to help me out with this? I've never attempted to install Windows 7 before, so I don't know what all it does in its installation. I am imagining though, that it is more powerful than the XP installation.

If anyone has any helpful tips, complete instructions or something for me, please let me know! I would love to have this end up working again.

Thanks in advance.

---

### Post by howefield on 2010-08-25
Is Ubuntu on the same disk that you plan on installing Windows 7 ?

If so, that'll probably be your biggest issue, since the Windows bootloader will overwrite grub meaning you'll need to reinstall grub.

There are many tutorials on installing Windows after Ubuntu, search for one of them.

[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by sikander3786 on 2010-08-25
Format the Windows XP drive and put Windows 7 onto it and then reinstall GRUB2 as mentioned on this page. Simple.

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

