---
title: "New Unbuntu user"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by Slipshandy on 2010-03-12
I have just installed the new Ubuntu and have most things working on my Hp 6735s, i have beed playing around and find that i cannot change the Visual effects, it looks for the drivers and doesnt find them, could you please advise what i need to do to get this working. The graphics card i believe is a ATI Radoen 3200. Any help would be great, also dumb it down for me as i have been so used to windows im not that up on terminology of everything. Cheers in advance 

Tom

---

### Post by tommcd on 2010-03-12
To find out what graphics card you have, open a terminal (applications > accessories > terminal) and type this command:
```
lspci | grep -i vga
```
and hit enter. It will output your graphics card info. For example on my system:
```

bash-3.1# lspci | grep -i vga
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)
bash-3.1# 

```
Post your output from that command here.
The easiest way to install graphics card proprietary drivers on Ubuntu is to go to: system > administration > hardware drivers. If it lists and ATI or Nvidia driver and offers to install it then click yes to install it.
Write back if you need more help.

And welcome to the Ubuntu forums!

---

### Post by pastalavista on 2010-03-12
If you have an internet connection, make sure your Software Sources (System->Administration menu) has "Proprietary Drivers...(restricted)" enabled with a check. After a reload of the packages, see if the Hardware Drivers app finds you something. If you've already done all that, search the forums with Google [site:ubuntuforums.org ATI Radeon 3200] and you should find what you need.

---

