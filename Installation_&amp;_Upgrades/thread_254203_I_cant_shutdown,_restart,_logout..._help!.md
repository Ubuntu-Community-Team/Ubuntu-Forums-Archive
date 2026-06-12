---
title: "I cant shutdown, restart, logout... help!"
date: 2006-09-09
forum: Installation &amp; Upgrades
---

### Post by daniminas on 2006-09-09
Hi. First, sorry my english, i'm Uruguayian. I been installed the 64 bit ubuntu, and everything works verry good .. but when i want to log out, shutdown, restart, etc.. the computer crash... I can't switch to the console too.

Please help, and thanks in advance
Edit/Delete Message

---

### Post by curtisf14 on 2006-09-09
Could you provide a few more details of the problem?  For example, are you not able to start Ubuntu at all?  Or if you can, are you just not able to log in?  Or does your computer just decide to crash at random times when you log out, shutdown, restart, etc?

---

### Post by daniminas on 2006-09-09
Yes, i can logIN!!!all the ubuntu sistem work PERFECT!.. but, I CANT shutdown, restart, logOUT.. (a mean: this happend when i click shutndown,restart,logout). I can hear de 'bye' sound of ubuntu, but then crash... This happend always!!.. the pc hung up showing a black screen, with some with randoms squares on the screen.

Please help.. and sorry my english :)

---

### Post by daniminas on 2006-09-11
ive a Intel 865G chipset with a /775i65G motherboard, and this happend only in the graphic mode.. :( i mean, if i intro in the recovery mode i can shutdown..

---

### Post by italian_boy on 2006-09-11
I've got the same error (posted in the thread called "Shutdown problem")
I also have 64 bit Dapper
I hope we find a solution
in the meantime, I suggest to use command line commands such as "shutdown" an d "halt", or to disable usplash and see what happens

---

### Post by xbose on 2006-10-28
Had the same problem with 32 bit ubuntu edgy eft :( 
i uploaded a video on youtube so you can watch here ...

[http://www.youtube.com/watch?v=nm5DjFxuq_Q](http://www.youtube.com/watch?v=nm5DjFxuq_Q)

thanks for any help ..

---

### Post by muriloq on 2006-11-01
Same problem here, using both Ubuntu and Xubuntu Edgy Eft (32-bit), after normal installation and using the live CDs. 

After clicking at logout or pressing Ctrl+Alt+Backspace everything (windows, panel, etc.) disappears from the screen, except the wallpaper and the mouse arrow (which still can be moved). 

After that I can't go to other consoles (Ctrl+Alt+F1), nor shutdown X (Ctrl+Alt+Backspace).

---

### Post by bsussman on 2006-11-01
> **italian_boy said:**
> 
in the meantime, I suggest to use command line commands such as "shutdown" an d "halt", or to disable usplash and see what happens

halt is a bad habit unless shutdown does not work - on older systems it causes a harder shutdown than 'shutdown -h now'.    But if shutdown does not work, it is very possible that halt wont either.  Then cmd/alt/delete or pwroff may be needed.

On newer systems it doesn't matter as much but using safe habits is a good idea.

---

### Post by koprioni on 2006-12-02
HI guys!I have the same problem at logout restart...i think it has to be something with the graphics.I have an ati mobility x700.
If someone could help plz...
Same as the video above->EXACTLY

---

### Post by Sef on 2006-12-03
> "shutdown" an d "halt"

To shutdown from the command line:

```
sudo shutdown -h now
```

---

### Post by koprioni on 2006-12-03
the solution is:
make a back up first:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
then open menu.lst:
sudo gedit /boot/grub/menu.lst
and place at the end of each kernel line "vga=788"
Thnx to someone(i cant remember)

---

### Post by eNtoS on 2006-12-10
I've got the same problem, i tried setting the vga= option but it doesnt solve anything...

anyone solved this yet?

---

