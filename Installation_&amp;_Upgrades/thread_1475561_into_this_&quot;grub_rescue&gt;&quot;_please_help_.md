---
title: "into this &quot;grub rescue&gt;&quot; please help me :("
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by maizuddin35 on 2010-05-07
Hey Linuxers .

I have my Ubuntu Lucid as the primary boot for my pc. At that time, when grub loads there will be a list of my Ubuntu and down below is my boot to windows seven.

For your information, I've installed Ubuntu and Windows seven on different harddisk.

Just now, I'd just format my window seven. and install it back. When I want to format the windows and install it back, I unplug the sata cable for my ubuntu, because I'm scared if when I format my windows, the ubuntu will take effect, because of my experience dealing with it, I did that.

So now, can anyone please help me with the "grub rescue>_" I want to boot up my beloved ubuntu back.can anyone ...I really do need your help guys.

---

### Post by Rumpty on 2010-05-07
So you have plugged your Ubuntu drive back in after installing W7 on another drive? Presumably Ubuntu is the "first" hard drive now, and should still have the grub menu with the Ubuntu boot option.

---

### Post by maizuddin35 on 2010-05-07
yes. now.My ubuntu drive is my primary drive. but there is no grub menu.what should i do?

---

### Post by Zireth ZH on 2010-05-07
Try this link pal... i hope this helps u [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by maizuddin35 on 2010-05-07
thanks. I try this out first. I will reply back if threre is any more problem .

---

### Post by dino99 on 2010-05-07
sudo grub-mkconfig && update-grub

[http://ubuntuforums.org/showthread.php?t=1467891&page=2](http://ubuntuforums.org/showthread.php?t=1467891&page=2) post 14

---

### Post by maizuddin35 on 2010-05-07
@dino99 : the output is this :
[I]
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?)[/I]

---

### Post by maizuddin35 on 2010-05-07
Now im trying with this one. is it ok?

[http://ubuntuforums.org/showthread.php?t=1306900](http://ubuntuforums.org/showthread.php?t=1306900)

I do it. and it end up saying this :

*grub-setup: error: cannot stat /media/a1633404-870b-4a51-8e2c-a7c5ef0844cb//boot/grub//boot.img*.

what does that mean?

---

### Post by maizuddin35 on 2010-05-07
I solve it!
thanks to you guys for reply back to me.

I follow this instruction on this link

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")

on this section
**Recover Grub 2 via LiveCD**

just now, I need to recover back my windows boot inside the grub.anyone got link?

---

