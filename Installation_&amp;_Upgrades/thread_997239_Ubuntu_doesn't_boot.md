---
title: "Ubuntu doesn't boot"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by Dotkito on 2008-11-29
When I installed Ubuntu off the disk, I rebooted and I selected Ubuntu. After that, the Ubuntu Splash screen popped up and then it was a black screen and it said "Type "Help" for more info, blah blah blah". Any help?

---

### Post by trazan2010 on 2008-11-29
[B][CENTER]i have the same proplame any help plz
& i triad to istall it at "VMware Workstation" and it worked good but when i install it in the real pc dosen't work
any help?
[/CENTER][/B]

---

### Post by unknown user on 2008-11-29
[FONT="Tahoma"]I have something like this where I have just updated to 8.10 and now when I boot up I get the login screen and then after that I just get a blue screen with the mouse, nothing more.[/FONT]

---

### Post by falcon61102 on 2008-11-29
> **Dotkito said:**
> When I installed Ubuntu off the disk, I rebooted and I selected Ubuntu. After that, the Ubuntu Splash screen popped up and then it was a black screen and it said "Type "Help" for more info, blah blah blah". Any help?

Are you sure you installed the Desktop version of Ubuntu and not one of the alternate versions or even the Server edition?

What are your computer specs?

---

### Post by falcon61102 on 2008-11-29
> **trazan2010 said:**
> [B][CENTER]i have the same proplame any help plz
& i triad to istall it at "VMware Workstation" and it worked good but when i install it in the real pc dosen't work
any help?
[/CENTER][/B]

You need to be a little more specific in saying that it doesn't work.  What specifically doesn't work?  Were you able to complete the install?

---

### Post by falcon61102 on 2008-11-29
> **unknown user said:**
> [FONT="Tahoma"]I have something like this where I have just updated to 8.10 and now when I boot up I get the login screen and then after that I just get a blue screen with the mouse, nothing more.[/FONT]

Your problem is more than likely a graphical issue because from the sounds of it, Ubuntu is booting up, it's just not loading GNOME properly.  Have you tried starting up the Recovery mode?  It's normally the second entry on the GRUB.

---

### Post by trazan2010 on 2008-11-29
> **falcon61102 said:**
> You need to be a little more specific in saying that it doesn't work.  What specifically doesn't work?  Were you able to complete the install?
sorry my english not good
my proplame is after install and reboot the boot screen show and the small orange thing come right and left for ever and the system not start and that didn't happend in the "VMware Workstation" and the system start in it

---

### Post by falcon61102 on 2008-11-29
Have you attempted to boot up in the Recovery mode?

If you can start up in the Recovery mode you can access the system logs and find out what is preventing a normal startup.

When you were running in the VWware Workstation, since you were using a virtual enviornment some of your hardware may have been overlooked and now that you are trying to run it normally, that hardware may be causing some issues.  What type of system do you have?

---

### Post by unknown user on 2008-11-29
[FONT="Tahoma"]Hi Falcon, I have tried this yes and the system does the same thing lets me log in and then hangs on the blue screen and not loading any of my desktop. Is there any command line that I can type as in the blue screen I can get the terminal window up?

If I was to download the desktop version and then run it on the laptop, would this wipe all my existing settings and data?[/FONT]

---

### Post by night_fox on 2008-11-29
You would need to make your windows partition smaller and then install Ubuntu in the empty space. Resizing is slightly risky so make sure you back up anything important.

---

### Post by trazan2010 on 2008-11-29
> **falcon61102 said:**
> Have you attempted to boot up in the Recovery mode?

If you can start up in the Recovery mode you can access the system logs and find out what is preventing a normal startup.

When you were running in the VWware Workstation, since you were using a virtual enviornment some of your hardware may have been overlooked and now that you are trying to run it normally, that hardware may be causing some issues.  What type of system do you have?
the Recovery mode has the same proplame stop write more lines and the system not start thats happend in 8.4 and 8.10 plz help i am going to be crazy i can't use ubuntu in the virtual machinei need it to be a primery system
and my system nowis windows xp sp2
and this proplame happend after i changed the proccecor from celeron 1.7/128 to p 2.00/512 and the SDRAM from 256 to 512 plz help
oh i remeberd some thing when i buy my new hard disk from my friend we used norton ghost to copy windoes partion and i had proplame with the master boot and i used windows xp cd to change the master boot to work with windows as it was show to me"grap" and my friend told me to do whati did to fix this proplame and i think that may be the reason for this proplame 
do you have a answer of my qus?
and i need the tow system on my pc linux and windows
i hope that you can understand me with my bad english:oops::oops:

---

### Post by falcon61102 on 2008-11-29
> **unknown user said:**
> [FONT="Tahoma"]Hi Falcon, I have tried this yes and the system does the same thing lets me log in and then hangs on the blue screen and not loading any of my desktop. Is there any command line that I can type as in the blue screen I can get the terminal window up?[/FONT]

If you press CTL + ALT + F1 you should switch to the console mode.

> **unknown user said:**
> If I was to download the desktop version and then run it on the laptop, would this wipe all my existing settings and data?

No, as night_fox said you can readjust your partitions without losing data.  What version are you using now?

---

### Post by falcon61102 on 2008-11-29
Tarzan2010,

The processor and RAM upgrade you did should not have an effect on the Ubuntu.  

And your install of Ubuntu was after you used the WinXP CD to fix the MBR, correct?  If so, that shouldn't be affecting anything either.

What are your system specs?

---

### Post by trazan2010 on 2008-11-29
> **falcon61102 said:**
> Tarzan2010,

The processor and RAM upgrade you did should not have an effect on the Ubuntu.  

And your install of Ubuntu was after you used the WinXP CD to fix the MBR, correct?  If so, that shouldn't be affecting anything either.

**What are your system specs?**
yes it was after using windows xp cd to fix MBR .
sorry i can't understand your last qus.
i told you my english not good:shock::shock::oops::oops:

---

### Post by falcon61102 on 2008-11-29
Ok, since you installed Ubuntu after fixing the MBR, that should not be an issue either.

My question is what are the details of your computer?  You listed your processor and RAM, but what other hardware do you have?

---

### Post by trazan2010 on 2008-11-30
> **falcon61102 said:**
> Ok, since you installed Ubuntu after fixing the MBR, that should not be an issue either.

My question is what are the details of your computer?  You listed your processor and RAM, but what other hardware do you have?
thats screenshot about my pc hardware
[IMG]http://trazan2010.googlepages.com/pc.JPG[/IMG]

---

### Post by unknown user on 2008-11-30
Falcon, I tried this pressing Control, Alt and F1 whilst logged in and seeing the blue screen and I was taken to a screen which looked like to DOS screen with the courser flashing after 'unknown-laptop login_'

Is this the screen that you meant and where do I go from here?

Cheers,

---

### Post by falcon61102 on 2008-11-30
Yeah, that's the console.  You can login using the Text based system and use that to fix any errors that you have.  What you may want to do is check your system log by:
```
dmesg
```

That will display the last system actions and hopefully allow you to see what is causing the errors.

---

### Post by trazan2010 on 2008-12-01
thanks all my proplame was the partion table and i solved it

---

