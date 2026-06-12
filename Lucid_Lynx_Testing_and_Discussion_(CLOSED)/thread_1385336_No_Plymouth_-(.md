---
title: "No Plymouth :-("
date: 2010-01-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by yasasflash on 2010-01-19
Hi guys, i'm using ASUS X51RL model laptop with ATI RAEDON X1100 series VGA.
while booting in to lucid alpha2 (with linux-image generic 2.6.31-15.50) I only get totally black screen but haven't saw any plymouth thing nearby.

Need a help here. :(

---

### Post by yasasflash on 2010-01-19
Any one there?

---

### Post by yasasflash on 2010-01-19
bump

---

### Post by Merk42 on 2010-01-19
It has only been 5 minutes!
Please stop bumping this and be patient.

Even better, look in the [other](http://ubuntuforums.org/showthread.php?t=1384748) [threads](http://ubuntuforums.org/showthread.php?t=1380289) on Plymouth.

---

### Post by garvinrick4 on 2010-01-19
Explain better, have not seen any plymouth thing nearby means what. And I do believe since the get go I was in 2.6.32 if I am wrong I will edit.

---

### Post by yasasflash on 2010-01-19
sorry about the bad english. It means i have never saw a plymouth boot splash after upgrading to lucid. It always started up with

 mounting /dev/bla bla 
 then a blank screen stays about 30 seconds
 suddenly another screen appears with list of error messages. 
 it says fsck completes successfully with no disk errors. 
 and also reports another four errors in main four processes in the init procedure. (I can't read & memorize the whole screen coz it vanish in a second).
can you suggest what could be the reason that i don't see any plymouth in my alpha2?

---

### Post by garvinrick4 on 2010-01-19
> **yasasflash said:**
> sorry about the bad english. It means i have never saw a plymouth boot splash after upgrading to lucid. It always started up with

 mounting /dev/bla bla 
 then a blank screen stays about 30 seconds
 suddenly another screen appears with list of error messages. 
 it says fsck completes successfully with no disk errors. 
 and also reports another four errors in main four processes in the init procedure. (I can't read & memorize the whole screen coz it vanish in a second).
can you suggest what could be the reason that i don't see any plymouth in my alpha2?
Have you gone to command line and CODE:    sudo apt-get install plymouth

It might be saying  Mountall Cannot find plymouth. Give it a shot and see if it is installed.
Never know sometimes it is the simple things.

---

### Post by yasasflash on 2010-01-19
> **garvinrick4 said:**
> Have you gone to command line and CODE:    sudo apt-get install plymouth

It might be saying  Mountall Cannot find plymouth. Give it a shot and see if it is installed.
Never know sometimes it is the simple things.

thanks for the response garvinrick4 but i'm quiet sure that i've installed the plymouth by default. 
here is the output

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
plymouth is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.

```

I've checked in the /lib/plymouth/themes directory also. It contains all the available themes completely. So any idea?

---

### Post by koso on 2010-01-19
Have you tried it with lucid kernel? your seems to be from karmic ...

---

### Post by yasasflash on 2010-01-19
> **koso said:**
> Have you tried it with lucid kernel? your seems to be from karmic ...

This is not a fresh install of lucid. I've upgraded karmic to lucid.

---

### Post by zika on 2010-01-19
> **yasasflash said:**
> This is not a fresh install of lucid. I've upgraded karmic to lucid.Nevertheless, You should have got the new 2.6.32 kernel in course of upgrade...

---

### Post by yasasflash on 2010-01-22
Hey i've made a fresh install of Lucid alpha with kernal 2.6.32.11(updated).
But now my system crash instantly when logged in. I can't even open a terminal window. Screen get blurred and turn in to red.
 
Is it something wrong with the x-server or something with the new Kernal??
***However now i can see the plymouth boot with no worries. it boot like a charm. But now the situtation is more suffering than before.
My VGA is RADEON XPRESS 200m .

In the previous upgraded (to lucid) system (with kernal 2.6.31) i had no problems with these kind of fatal crashes.

please help guys.

---

### Post by Tompalaz on 2010-01-22
have you tried using the mesa driver?
1) go to a tty (Ctrl-Alt-F1) then 
2) sudo nano /etc/X11/xorg.conf
3) under the driver section, type vesa. Then save and run startx.

---

### Post by yasasflash on 2010-01-22
thanks for the reply , but i don't think there will e any xorg.conf file after karmic.
I've tried your method, but as expected there was no file found in the /etc/X11. 
so any other solutions??

---

### Post by Ubuntiac on 2010-01-22
You can create a xorg.conf with just the bits you need. Yes, there isn't one by default, but it will use xorg.conf if it exists.

---

### Post by inportb on 2010-01-22
Wait, what does the Ubuntu Plymouth thingy look like? I have KMS but all I see is the standard usplash-theme-kubuntu animation with flicker-free goodness (which is totally fine with me, but I'm curious).

Oh yeah, on TTY8 I get
> mountall: Could not connect to Plymouth

---

### Post by yasasflash on 2010-01-22
> **inportb said:**
> Wait, what does the Ubuntu Plymouth thingy look like? I have KMS but all I see is the standard usplash-theme-kubuntu animation with flicker-free goodness (which is totally fine with me, but I'm curious).

Oh yeah, on TTY8 I get

hey it's like [http://www.youtube.com/watch?v=MyaGwYrJvFg](http://www.youtube.com/watch?v=MyaGwYrJvFg)

---

### Post by yasasflash on 2010-01-22
> **Ubuntiac said:**
> You can create a xorg.conf with just the bits you need. Yes, there isn't one by default, but it will use xorg.conf if it exists.

Can you pl give me more specific instructions about that. Coz i don't know much about this X-Server/Xorg thing.
I'm asking again; does **VGA driver** make this system crash OR the **2.6.32.11 kernal version**???

---

### Post by Ubuntiac on 2010-01-23
Sounds more like an error in xorg to me. (Xorg is the part that controls your screens and input devices like mice and keyboards).

Can you boot into rescue mode? (Hold shift when it says "booting grub" or whatever it is, then choose the second option down usually.

If you can let us know what it says when you login and enter:

```
cat /var/log/Xorg.0.log | grep EE
```

That should list any errors that have happened with xorg (ok, any line, error or not that has EE in it. Xorg places (EE) in front of any error in the log)

---

### Post by yasasflash on 2010-01-23
> **Ubuntiac said:**
> Sounds more like an error in xorg to me. (Xorg is the part that controls your screens and input devices like mice and keyboards).

Can you boot into rescue mode? (Hold shift when it says "booting grub" or whatever it is, then choose the second option down usually.

If you can let us know what it says when you login and enter:

```
cat /var/log/Xorg.0.log | grep EE
```That should list any errors that have happened with xorg (ok, any line, error or not that has EE in it. Xorg places (EE) in front of any error in the log)

Well here is the output 
```

    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) open /dev/fb0: No such file or directory
(II) XKB: reuse xkmfile /var/lib/xkb/server-D378AD8F86E560F712A83EE36E4E5E92C595B9BD.xkm
(EE) ioctl EVIOCGNAME failed: Inappropriate ioctl for device
(EE) PreInit returned NULL for ""Logitech USB Optical Mouse""
(EE) ioctl EVIOCGNAME failed: Inappropriate ioctl for device
(EE) PreInit returned NULL for ""SynPS/2 Synaptics TouchPad""
(EE) ioctl EVIOCGNAME failed: Inappropriate ioctl for device
(EE) PreInit returned NULL for ""Macintosh mouse button emulation""


```******This output is taken when i booted from the kernal 2.6.31** ****
******When boot into the kernal 2.6.32.11, i couldn't even launch the terminal from the menu. While opening the terminal window, Screen crashes and turn into red******

---

### Post by inportb on 2010-01-23
> **yasasflash said:**
> hey it's like [http://www.youtube.com/watch?v=MyaGwYrJvFg](http://www.youtube.com/watch?v=MyaGwYrJvFg)

Thanks for the link. Yeah, I'm definitely not seeing that, though usplash is slick enough as it is.

---

### Post by Ubuntiac on 2010-01-23
> ******This output is taken when i booted from the kernal 2.6.31** ****
******When boot into the kernal 2.6.32.11, i couldn't even launch the terminal from the menu. While opening the terminal window, Screen crashes and turn into red******

So... Is your 2.6.31 Kernel an install of Karmic or Lucid?

To get the errors from your 2.6.32 kernel, you may need to boot from a LiveCD / LiveUSB stick, open the drive that has your Lucid install (in Nautilus / Dolphin) and look at the Xorg.0.log file on that drive in the /var/log subfolder. Once again, you'd be looking for lines that start with (EE) for error.

---

### Post by yasasflash on 2010-01-23
> **Ubuntiac said:**
> So... Is your 2.6.31 Kernel an install of Karmic or Lucid?

To get the errors from your 2.6.32 kernel, you may need to boot from a LiveCD / LiveUSB stick, open the drive that has your Lucid install (in Nautilus / Dolphin) and look at the Xorg.0.log file on that drive in the /var/log subfolder. Once again, you'd be looking for lines that start with (EE) for error.

Here's what i've done exactly. 

1. made a **fresh install of lucid alpha2** (kernal 2.6.32.11)========> **Playmouth is ok but system crashes** instantly when i try launch any application (even terminal / nautilus)

Then....

2. I've **installed karmic (fresh install)**
3. **Upgraded to lucid alpha2** straight away. (grub shows 2.6.31 and 2.6.32 the both options)
4.When i booted from 2.6.31 there is not plymouth visible. instead it says cannot connect to plymouth.
5.When i booted from 2.6.32.11 there is plymouth but system crash instantly when launching any application. (like i said it can't launch even the terminal)
6. That is why i provided the output (you requested) from the 2.6.31 boot. coz i can't open gedit or nautilus from the 2.6.32. it crashes like hell.

---

### Post by Ubuntiac on 2010-01-23
OK, thanks. That makes things a bit clearer.

> **yasasflash said:**
> 5.When i booted from 2.6.32.11 there is plymouth but system crash instantly when launching any application. (like i said it can't launch even the terminal)
6. That is why i provided the output (you requested) from the 2.6.31 boot. coz i can't open gedit or nautilus from the 2.6.32. it crashes like hell.

OK. I think this is being made more complicated than it needs to be. First up, Lucid is obviously in development and thus unstable. Second, upgrades to a development pre-release are generally more likely to hit bugs than a fresh install. Put those two together and you have a higher chance of hitting something nasty that is harder to track down. 

I would do a fresh install (as you did before), then try to boot and when it fails, use a livecd to open Nautilus / Dolphin and paste the error log file at /media/YOUR_LUCID_INSTALL_DRIVE/var/log/Xorg.0.log.

They key here is that **you're opening Nautilus / Dolphin from the live cd**, and then browsing to /var/log on another drive.

---

### Post by exploder on 2010-01-23
I have nvidea graphics on the machine I am using to test Lucid. Currently Plymouth is not working but the boot time is quick and there are no errors on boot or shut down so I figure it is just a matter of time and this will be resolved. I figure I will just wait and have a little patience because we are only about half way through the development cycle and the boot experience has been given priority.

---

