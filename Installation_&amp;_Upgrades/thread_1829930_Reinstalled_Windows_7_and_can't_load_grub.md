---
title: "Reinstalled Windows 7 and can't load grub"
date: 2011-08-21
forum: Installation &amp; Upgrades
---

### Post by Light_Yagami on 2011-08-21
I just finished my Windows 7 reinstall, and I go to reboot into Linux, and there's not grub loader. I go into a live CD and get into the grub prompt. Here's what I got:
> 
sudo grub
grub> root (hd0,0)

grub> setup (hd0)

Error 17: Cannot mound selected partition
As for additional information, my fstab is listed below:

> 
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda6 swap swap defaults 0 0


---

### Post by Raygreen on 2011-08-21
[COLOR="Teal"][/COLOR][FONT="Garamond"][SIZE="3"]I had the same problem, I then reinstalled Ubuntu and it fixed my Grub where I was able to boot into Ubuntu and Windows. 

I loaded Startup Manager so I could change the boot order on Grub.[/SIZE][/FONT]

---

### Post by Light_Yagami on 2011-08-21
Or I could just look at this link
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
-_- 
Fixed it all first try.

---

### Post by YannBuntu on 2011-08-23
Hello, happy to see that Boot-Repair helped. It is a new tool, so if you have 5 minutes, please help translating it in your language : [https://translations.launchpad.net/boot-repair/trunk](https://translations.launchpad.net/boot-repair/trunk)

regards

---

### Post by Raygreen on 2011-08-26
[SIZE="3"][COLOR="Teal"]I tried that tool and it didn't work. I ran it through the 3 levels and all failed. Seemed like Grub wanted to boot into a version of Ubuntu not on the hard drive.[/COLOR][/SIZE]

I just ended up running Ubuntu 11.04 install again, and Grub was fixed and I was back to having it boot into Windows 7 as my first choice. I think Ubuntu has come improved on itself over the older versions. I started using Ubuntu 7.04. You can't beat it for it being a free OS. If it wasn't for the lack of support for Netflix and iTunes I say it would be a full replacement of Windows. I am still am a fan of Windows. I am running Windows XP on my really old laptop. I had Ubuntu on it too. It ran well with all versions including Ubuntu 11.04. I just found some issues where I had to keep putting my password in to access the wireless connection on my laptop. I like using Ubuntu, but I still have to run Windows to use my Netflix and iTunes to sink up my iPhone.

---

