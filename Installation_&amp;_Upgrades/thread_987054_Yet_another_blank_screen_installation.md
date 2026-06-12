---
title: "Yet another blank screen installation"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by CursedBlade on 2008-11-19
I have ended up joining the many other threads about blank screen installations but i just cant seem to fix it.

I have tried:

[LIST]
[*]Alternative CD
[*]Booting into LiveCD
[*]Regular install
[*]Safe mode
[*]Removing quiet and changing splash to nosplash
[/LIST]

as well as probably a few other things i cant remember.

None of this works, what happens is **after the loading bar is done the screen just goes blank and theres nothing i can do from there**. I've run out of ideas.

I'm trying to install **Ubuntu 8.04** onto one of my laptops (ECS G320 [http://tinyurl.com/6p5x7x](http://tinyurl.com/6p5x7x))

I dont have massive knowledge of Linux so things may be need to be explained. All i want is to learn some proper Linux skills on a linux dedicated machine and I cant even get it to install!

---

### Post by CursedBlade on 2008-11-19
Just a quick add to this.. this is what i get when i try to use the alternative cd...

[IMG]http://i25.photobucket.com/albums/c60/CursedBlade/moto_0037.jpg[/IMG]

---

### Post by redoscar3 on 2008-11-19
I don't really have an answer for this problem other than to say I suspect Ubuntu is having difficulty properly configuring your video card and perhaps has chosen the wrong driver.

From your photo, I can't tell if your computer is sitting at your login screen or not.  You could try getting into a console display by pressing Ctrl-Alt-F2 and logging in at the console.  This would allow you to examine your /etc/X11/xorg.conf file.

Beyond that, I am at a loss as to what is happening.  If you can get to a text console screen, I will try to help you further.

Red

---

### Post by redoscar3 on 2008-11-19
Also, have you tried to enter "Recovery mode" through the grub menu?  This is selectable by pressing "Esc" when the grub message first hits the screen.

---

### Post by CursedBlade on 2008-11-19
well it wont be the login screen because its not installed yet... All i am managing is to press install on the first menu and then i am presented with that image (when using alternative cd)

---

### Post by redoscar3 on 2008-11-19
Sorry, I was confused about whether you were installed or not.  Seems your problem is that Ubuntu won't even run as a Live CD for some reason.  And you say you have tried the Alternative CD so no sense even trying to go there.

Have you tried the latest version of Ubuntu 8.10 Intrepid Ibex?  I know it uses a much newer kernel and perhaps your computer would be better supported by it.  Just a thought.

---

### Post by CursedBlade on 2008-11-19
Can try it... dont see it making much difference but i'll try...

---

### Post by benson444 on 2008-11-19
I had the same kind of problem with an alternate cd of some distro or other on a laptop some time ago. If I remember right I needed to add a setting to the kernel line before starting the install. Look for an F-key option for adding kernel options/arguments and try putting in

vga=771

---

### Post by redoscar3 on 2008-11-19
You would be surprised at the differences in Ubuntu versions.  Even though it will receive long term support, I have had more than my share of problems with Hardy compared to previous versions of Ubuntu (going back to Dapper Drake when I first this distro).  But I now have Hardy running well on my old Acer Aspire 3003LCi laptop.  But you can't even get past 1st base on your machine with Hardy.  So my suggestion is to try Intrepid and see if you don't have better success.  I know my nephew's Toshiba laptop works much better with Intrepid than Hardy.  Good luck!

---

### Post by CursedBlade on 2008-11-20
redoscar cheers for the help but no luck. However...

BENSON!! You genius! I am installing as we speak... hopefully once the install is done i will be able to actually boot in, we can wait and see.

---

### Post by CursedBlade on 2008-11-21
The alternative installer worked using the vga=771 solution. However i now can not actually get into linux..

details in the following thread...

[http://ubuntuforums.org/showthread.php?p=6222915#post6222915](http://ubuntuforums.org/showthread.php?p=6222915#post6222915)

---

