---
title: "howto get a bootsplash??"
date: 2005-07-21
forum: Installation &amp; Upgrades
---

### Post by ~Gh05t~ on 2005-07-21
hi all,
ive tried to install a bootsplash for my kubuntu 5.04, because the standard text-bootscreen suxx on a desktop machine. :wink: 

Ive searched google and the wiki and found some solutions with debian-sources. 
First one wanted me to download some splashy sources, but the links to the packages were broken. 
Second one had an equal idea, but with a  deb-source from debian.bootsplash.de, to install the debian-bootsplash-package. 
APT refused to install that with the message, that this package would need libc6 >2.3.2-lc1-4 or sth, my version is 2.3.2-lc1-20ubuntu (or sth.), so ive downloaded the package and installed it with dpkg without any problem, but even with no other messages like asking me for my initrd. So ive tried to add the bootsplash-part to my existing initrd manually with the splash-command and a splash-config ive downloaded before, but that doesnt took any effect.

Any idea what i coult do to get that shit run on my system??

thx4help

~Gh05t~

---

### Post by djselbeck on 2005-07-21
Hello,

there is a thread in the Howto section

[here]("http://ubuntuforums.org/showthread.php?t=41709")

DJSelbeck

---

### Post by ~Gh05t~ on 2005-07-22
hmmm... its not nice (i get the ugly black console before and after the nice bootsplash for a moment as well as in verbose mode), but it seems to work... thanks  :smile: 
How do i get a real nice verbose mode and grub-splash?

Iam talking about sth. like that:

[http://www.kde-look.org/content/pre2/26495-2.jpeg](http://www.kde-look.org/content/pre2/26495-2.jpeg)
[http://www.kde-look.org/content/pre3/26495-3.jpeg](http://www.kde-look.org/content/pre3/26495-3.jpeg)

Ive installed a grub-splash, but its just a bad resolution picture in the background... how do i change the menu-style? 
And is it possible to get a higher resolution picture in the background? That on the picture above seems to be, and i have another machine with suse 9.1, that seems to be, too...

---

### Post by djselbeck on 2005-07-22
[QUOTE=~Gh05t~]hmmm... its not nice (i get the ugly black console before and after the nice bootsplash for a moment as well as in verbose mode), but it seems to work... thanks  :smile: 
How do i get a real nice verbose mode and grub-splash?

Iam talking about sth. like that:

[http://www.kde-look.org/content/pre2/26495-2.jpeg](http://www.kde-look.org/content/pre2/26495-2.jpeg)
[http://www.kde-look.org/content/pre3/26495-3.jpeg](http://www.kde-look.org/content/pre3/26495-3.jpeg)[ 

Ive installed a grub-splash, but its just a bad resolution picture in the background... how do i change the menu-style? 
And is it possible to get a higher resolution picture in the background? That on the picture above seems to be, and i have another machine with suse 9.1, that seems to be, too...[/QUOTE]
 Hello,

I think SuSE has a Splashscreen which is integrated in the Kernel. If you want it you have to recompile your kernel and this is a lot of work.

DJSelbeck

---

### Post by ~Gh05t~ on 2005-08-09
why is it much work to recompile the kernel? Ive done that so much times now, one more wont hurt me...  :wink: 
but what do i have to change on the kernel to get such nice gfx-grubmenus + bootsplash? Did anybody got  that working for ubuntu?

---

### Post by djselbeck on 2005-08-09
Hello,

it is much work because the hald don't work with every kernel. I've tried it with Ubuntu serveral times because my Saitek X45 Joystick is not supported by Kernel version 2.6.10 so i tried to compile the newest 2.6.12.3 kernel. I've finished it and my system booted. At first all looks great but then i noticed there where no CDDrives nor USB Harddisks. So i tried an older one (2.6.11.12). Now it works but i've to modify a startscript to let ubuntu boot. All in all it is not very easy to have a self-compiled kernel running

DJSelbeck

---

### Post by ~Gh05t~ on 2005-08-10
i do noch want do write a kernel from scratch, i do not even need to reconfigure it from scratch. I just apt-get the prepatched ubuntu-sources (2.6.11), change the 2 or 3 things i have to change and compile it again... whats the problem? Ive already done that very often (mostly for my debian and my LFS  ;-) )

The point is, that i dont know which features of which programs are missing... if i turn on that function in the kernel... do i need a patched grub or sth. to get gfx-menus? And what do i have to do if i want a real bootsplash with gfx-console etc (not only the poor splashy)?

---

### Post by ~Gh05t~ on 2005-08-18
OK, i got bootsplash and grub-gfxboot working on my ubuntu  :)  :) 

Bootsplash worked with ubuntu-kernel 2.6.11 (2.6.10 should work, too), but that is crashing on my notebook (even the unpatched version), so i installed 2.6.12.4 from kernel.org, that works perfect!! Only thing that doesnt work atm is the progress bar, but iam working on that.

grub-gfxboot works, too, but i didnt found any ubuntu-themes till now. If i have some time ill create one  ;-) 

If somebody's interested how to install that stuff just ask me  ;-) 

~Gh05t~

---

### Post by myha on 2005-09-08
[QUOTE=~Gh05t~]OK, i got bootsplash and grub-gfxboot working on my ubuntu  :)  :) 

Bootsplash worked with ubuntu-kernel 2.6.11 (2.6.10 should work, too), but that is crashing on my notebook (even the unpatched version), so i installed 2.6.12.4 from kernel.org, that works perfect!! Only thing that doesnt work atm is the progress bar, but iam working on that.

grub-gfxboot works, too, but i didnt found any ubuntu-themes till now. If i have some time ill create one  ;-) 

If somebody's interested how to install that stuff just ask me  ;-) 

~Gh05t~[/QUOTE]
Man if u can help me do this it would really make my day - week!  :):)
I think you should write how-to for this...  :-P

---

### Post by ollesbrorsa on 2005-09-08
I second that! A Howto would be excellent.

Consider yourself asked  ;-)

---

