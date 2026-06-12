---
title: "[SOLVED] can't reinstall windows"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by kalikid on 2008-05-10
A friend did a total install of Ubuntu 8.04 on my desktop, effectively wiping out windows I want to reinstall xp & do a dual boot with Ubuntu. But my xp disk isn't recognized on startup, so I am basically immobilized. When I get to my desktop, the windows disk does show up.

I get no messages of any sort during startup. My cd drive flashes initially & then goes out. There is absolutely no hesitation during the Ubuntu startup. Any thoughts how I can reinstall or am I just SOL?

I know the cd drive's ok.

Thanks for any help.

---

### Post by Pumalite on 2008-05-10
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Format your drive ntfs. Then try again.

---

### Post by kalikid on 2008-05-11
Pumalite -- Thanks for your reply. I burned the GParted live CD, but don't see an option that specifies ntfs configuration. There are several options offered: auto configuration, Do X, noapic, framebuffer, force vesa driver, force 1740 driver, Force 1810 driver, etc. Would the auto configuration option be the correct one to choose?

Thanks again.

---

### Post by Pumalite on 2008-05-11
You have to boot first; once in you'll have graphics of your drives. Then start using it. Check the documentation.

---

### Post by kalikid on 2008-05-11
Thanks for the heads up, Pumalite--you got me half way there. What I was describing actually was the boot menu I got with the GParted live disk. I was not presented with what you described.
 
For those of you in a similar position as mine; and like myself probably not as astute as the average Linux user, I found the following links helpful in how to use the GParted boot disk to repartition:


1[I]2/5/2007.

Re: How to use gparted

The menu you get is about what kind of graphics (video) driver you require.
For most computers you can let GParted automatically decide for itself, (the first option), but if you have a special video card you can specify exactly what driver you want to use.
If X fails to start you use the 'forcevideo' script, so you have to type that at the terminal and it will ask you which video driver you want, usually I type 'vesa', which is the generic video driver. Then it asks for resolutions. That depends on what kind of monitor you have. 1024x768 is standard. Most monitors are 75% as high as they are wide. If you have a widescreen monitor then yours might be different.
Then if you're lucky this time 'x', your graphical user interface, should start and you can use GParted.

Regards, Herman [/I]

Another helpful link that shows a visual use of GParted step by step is 

[http://howtoforge.com/partitioning_with_gparted](http://howtoforge.com/partitioning_with_gparted)

Cheers.

---

### Post by Pumalite on 2008-05-11
Congrats!

---

