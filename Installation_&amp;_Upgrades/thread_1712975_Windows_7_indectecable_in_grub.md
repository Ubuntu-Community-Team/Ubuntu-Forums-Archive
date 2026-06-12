---
title: "Windows 7 indectecable in grub"
date: 2011-03-23
forum: Installation &amp; Upgrades
---

### Post by hhtun21 on 2011-03-23
[SIZE=2]I have installed windows seven after installing ubuntu ( 10.10 )
( this is my first day with Ubuntu :)  )
I have followed the instructions in this video to restore Grub :
[http://www.youtube.com/watch?v=ajs9rO5upZA](http://www.youtube.com/watch?v=ajs9rO5upZA)

I have now grub at the booting but Windows 7 is not inside this list.
In my boot list there are :

[SIZE=1]Ubuntu, With Linux 26,35-28 generic
Ubuntu, With Linux 26,35-28 generic ( recovery mode)
Ubuntu, With Linux 26,35-22 generic
Ubuntu, With Linux 26,35-22 generic ( recovery mode)
Memory test (memtest86+)
Memory test (memtest86+ serial console 115200 )
Microsoft Windows XP professional ( on /dev/**sbd1** ) --> my second harddisk[/SIZE]

How can I add windows seven to the list ?
Thanks and sorry for my bad English[/SIZE]

---

### Post by matt_symes on 2011-03-23
Hi

Is this a WUBI install or an install to a partition.

Boot into Ubuntu. Open a terminal and run the boot info script in my signature. The instructions are on the web page. Post the result.txt file back between code tags.

To do this copy and paste the file into your reply. Hightlight the text and hit the # button above where you are typing.

This should tell us everything we need t know about your set up.

Kind regards

---

### Post by Quackers on 2011-03-23
Welcome to UF.
Have you run ```
sudo update-grub
``` in the terminal from your Ubuntu desktop?

---

### Post by hhtun21 on 2011-03-23
Thank you all
now all is right after running this : ```
sudo update-grub
```

---

### Post by Quackers on 2011-03-23
Excellent :-)  Enjoy!

---

