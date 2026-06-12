---
title: "Ubuntu server 9.1 on virtual pc 2007 issue"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by NModern on 2010-03-10
Hi i have installed Ubuntu server 9.10 on Microsoft Virtual PC 2007 and now i cannot open it it's not starts.

Please look at the picture

[IMG]http://palsite.tk/ubuntu.jpg[/IMG]

---

### Post by NModern on 2010-03-11
nobody will help?? :(

---

### Post by muylento on 2010-03-11
Exactly same issue. 

You can actually login by typing your username and password, and then you will see only a fraction of the top of the screen. By using the command "clear" you end up seeing what you are typing and a bit of the system response, enough to use vi.

To fix the error with the graphics, I have tried to follow the instructions on [this post]("http://blog.craz8.com/articles/2007/04/01/ubuntu-server-on-virtual-pc") but the file boot/grub/menu.lst does not exist in 9.10. I have tried to use "/etc/grub.d/40_custom" according to the [Grub 2 instructions]("http://ubuntuforums.org/showthread.php?t=1195275"), but I also have a Grub Error: No such Disk that I am afraid does not let the system load that file anyway. I think that the Grub error is related to installing Ubuntu Server with LVM - but I am not sure.

Anyway, if you try the vga=0x314 trick and it works, let me know.

Thanks.

---

### Post by muylento on 2010-03-11
I found the fix. It is a bit cumbersome because you only see the top few lines of the screen, but it is doable.

login with your name and password and wait to see the system's response - the lines will appear above the group of green stuff. Use the "clear" command to get the prompt to the top of the screen.

You need to edit the file /etc/default/grub (will need sudo command for that)- more info [here]("http://ubuntuforums.org/showthread.php?t=1195275")

I used vi and the command Z+ that brings the last line of the file to the top of the screen.

I replaced the "quiet splash" by "vga=791 noreplace-paravirt"

After that update the grub file and restart - it should work now.

---

### Post by TeDiouS on 2010-03-11
Don't know how you feel about using another app. But Virtual box works quite well.
[http://www.virtualbox.org/](http://www.virtualbox.org/)


I haven't had good luck w/ MS's Virtual PC 2007. But the one linked has helped. :-)

---

### Post by NModern on 2010-03-14
Thank's for all.  I will check.

---

### Post by NModern on 2010-03-15
Hi. In my case this line wasn't at the end of the file. But it's worked thank's to everyone

And to avoid difficulties if you have installed ssh you can use putty.


P.S how to place "SOLVED" into the talks subject?

---

### Post by muylento on 2010-03-17
Sorry, it was not at the end of the file for me either, but once you are at the bottom, you could navigate up with just half of the screen visible - which was my problem to start with.

Anyway, I ended up trying virtual box and the feedback was spot on. Not only it works w/o issues, but it feels like it goes way faster than VPC. I am afraid that the MS stuff is optimized only for Windows... I tried the VHD file created by VPC but then made a little experiment reinstalling in vbox, and the installation alone was much faster.

---

