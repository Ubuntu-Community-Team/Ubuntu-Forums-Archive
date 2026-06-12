---
title: "[SOLVED] Dual Boot Problems"
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by larainzlo07 on 2008-01-01
Whenever I try to dual boot into ubuntu i get to the menu where it allows me to choose 3 different things for ubuntu and my other OS which is XP. I can get into xp fine but when i try to boot into the first option of the ubuntu choices i hit enter and it tries to start it up but nothing happens. Ive let it sit for 20 minutes but still nothing. Any ideas on what to do?

---

### Post by logos34 on 2008-01-01
Try the suggestions [here]("http://users.bigpond.net.au/hermanzone/p15.htm#Temporarily_Edit_the_GRUB_Menu").  Good luck.

---

### Post by larainzlo07 on 2008-01-01
tried all the options that it says when you put vga=ask and got nothing. i also tried doing the section underneath it and got nothing when i tried to boot into ubuntu again.

---

### Post by larainzlo07 on 2008-01-02
bump

---

### Post by larainzlo07 on 2008-01-02
just thought that i might add that after i installed ubuntu i was able run the updates. I was not able to install the restricted driver for my graphics card though because i needed to restart my computer from running the ubuntu updates.

---

### Post by larainzlo07 on 2008-01-02
any help on this i would really like to start using ubuntu?

---

### Post by torgrot on 2008-01-02
A lot of people had problems with the last kernel update.  Take a look at this page [http://users.bigpond.net.au/hermanzone/p15.htm#GRUB_shell](http://users.bigpond.net.au/hermanzone/p15.htm#GRUB_shell) and see if you can update grub.  If you can it will create a new initramfs***** file that will allow you to boot.

torgrot

---

### Post by logos34 on 2008-01-02
on the first ubuntu entry press 'e' to edit, 'e' again on 'kernel' line, and delete 'quiet' option, 'enter' and 'b' to boot...this will give you some idea where it's hanging. Does it respond to ctrl+d or enter after it hangs?

---

### Post by larainzlo07 on 2008-01-02
reinstalling grub works but it still doesnt boot up after waiting a while. im new to linux but its easy to figure out if the os hasnt come up by waiting two or so minutes then something isnt working.

---

### Post by larainzlo07 on 2008-01-02
> **logos34 said:**
> on the first ubuntu entry press 'e' to edit, 'e' again on 'kernel' line, and delete 'quiet' option, 'enter' and 'b' to boot...this will give you some idea where it's hanging. 
i will have to try this bit later but it doesnt respond to ctrl + d or enter when it is hanging

---

### Post by logos34 on 2008-01-02
> **larainzlo07 said:**
> i will have to try this bit later but it doesnt respond to ctrl + d or enter when it is hanging

Can you boot into recovery mode?

If yes then you could try the grub-install method for ['refreshing' /boot]("http://users.bigpond.net.au/hermanzone/p15.htm#Grub_loading_stage1.5") (saving menu.lst beforehand)...or maybe rename menu.lst, delete contents of boot and then run grub-install, and then update-grub to generate new menu.lst...not sure it'll work but it may be worth a shot.

---

### Post by torgrot on 2008-01-02
[http://ubuntuforums.org/showpost.php?p=4007481&postcount=22](http://ubuntuforums.org/showpost.php?p=4007481&postcount=22)  Check this thread out.  Some people had the menu.lst get messed up when the kernel update came out.  The uuid was incorrect in the options and the kernel lines.

torgrot

---

### Post by larainzlo07 on 2008-01-03
one of my friend put ubuntu on his pc and he said he had the same problem as me but his problem was with xorg.conf do you think it could the same problem?

---

### Post by logos34 on 2008-01-03
> **larainzlo07 said:**
> one of my friend put ubuntu on his pc and he said he had the same problem as me but his problem was with xorg.conf do you think it could the same problem?

normally I'd say yes, especially after a kernel update, but it doesn't sound like you're getting that far in the boot process...I mean you'd get an X server error message or something

---

### Post by larainzlo07 on 2008-01-03
thanks for all of the help guys i will not be able to try your suggetions until i get off of work this afternoon but once i am able to i will report back to you guys

---

### Post by larainzlo07 on 2008-01-03
alrighty people i got it up and running. i tried everything that you said and it did not work so i decided to reinstall ubuntu and then when it came time to install my updates after a succesful install i installed my graphics card driver first and everything has been working since. thanks for all of the help

---

### Post by logos34 on 2008-01-03
> **larainzlo07 said:**
> alrighty people i got it up and running. i tried everything that you said and it did not work so i decided to reinstall ubuntu and then when it came time to install my updates after a succesful install i installed my graphics card driver first and everything has been working since. thanks for all of the help

seems like every thread I've responded to lately has turned out exactly opposite of what I thought initially. So, larainzlo, did you take out the 'quiet' option and did it then display any video-related error messages?  Glad you got it working but it would be nice to know a little more about what happened for future reference (if only for my personal edification--and lately I need all I can get!)

---

### Post by larainzlo07 on 2008-01-03
yes i did try that but it just zoomed through everything and it did not hang up

---

