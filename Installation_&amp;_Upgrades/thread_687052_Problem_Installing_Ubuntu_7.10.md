---
title: "Problem Installing Ubuntu 7.10"
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by Pido on 2008-02-03
When running the Ubuntu CD I burned, I get past the initial loading bar and then the screen freezes and says something along the lines of "Cannot run at this resolution" or something like that I can't really tell because it flashes for half a second if that.

Can anyone suggest anything I can do to fix this problem?

---

### Post by manimal347 on 2008-02-03
Try burning another copy, using good quality media at 16X or slower. Run the verify option when writing out the ISO. A fair amount of errors are caused by defective install media.

Also, is there anything we should know about this machine, anything rather non-standard? 

Try doing a text-install using the alternate-install disc if all else fails and you can't get a good resolution from someone else. As it skips booting the Gnome desktop environment (xwindows) and loads a lot fewer things, it is more likely to work. Don't worry; it holds your hand and gives you the same end-product as the shiny GUI installer.

---

### Post by Pido on 2008-02-03
My Computer Specs:

Radeon X1300/1550 Series Video Card
2gb RAM
AMD Athlon 64 X2 Dual Core processor 4200+

---

### Post by Pido on 2008-02-03
> **manimal347 said:**
> Try burning another copy, using good quality media at 16X or slower. Run the verify option when writing out the ISO. A fair amount of errors are caused by defective install media.

Also, is there anything we should know about this machine, anything rather non-standard? 

Try doing a text-install using the alternate-install disc if all else fails and you can't get a good resolution from someone else. As it skips booting the Gnome desktop environment (xwindows) and loads a lot fewer things, it is more likely to work. Don't worry; it holds your hand and gives you the same end-product as the shiny GUI installer.

I used Deepburner to write the ISO to a CD if that tells you anything.

Would I have to download a different file for the text-install?

---

### Post by Pido on 2008-02-04
Ok I wrote down the exact error,

"Cannot Display This Video Mode"
"1280x1024 60hz"

The text based install you suggested earlier did not work at all, I had problems at the partitioning and actually installing the system.

---

### Post by Pido on 2008-02-04
Bump so more people can provide input,

I'd really like to use Ubuntu and don't feel I should be limited to what I can use on my computer based on my monitor...

---

### Post by LaxFreek on 2008-02-09
Do this, as you are getting the message you should go back to a black screen that is either fully black or has like 4 lines of writing. When you are there press ctrl alt f1 and you will get a bunch more of writing and you will be allowed to run commands. Once you are there run the command 

sudo dpkg-reconfigure -phigh xserver-xorg 

and pick ati cards and then you'll be able to choose resolution. Press space on 1280x1024 and 800x600 then press enter. Then you press ctrl alt backspace to restart the gdm or w/e it is and it should work. I had the same problem and it fixed it cause I had this card. But just to let you know desktop effects will most likely not work on your comp. Didn't for me.

---

### Post by jalirious on 2008-02-10
Hi, I've been attempting to install 64 bit gutsy on my AMD Athlon 64 4800+ processor at work. I get a similar problem to yourself, unfortunately after restarting gnome via 

sudo /etc/init.d/gdm restart (as control-alt-backspace didn't work).

The screen flashes, then goes back to the 'failed to detect your screen & graphics card'


-----hang on, I restarted gnome again and the live cd is up and running! If I don't post again presume it works.

---

