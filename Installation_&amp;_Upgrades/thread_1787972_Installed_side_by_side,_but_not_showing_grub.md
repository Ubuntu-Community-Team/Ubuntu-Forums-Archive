---
title: "Installed side by side, but not showing grub"
date: 2011-06-21
forum: Installation &amp; Upgrades
---

### Post by wwe9112 on 2011-06-21
I had installed Kubuntu 11.04 side by side with WIndows 7. I'm certain I didn't over write, i partitioned, and installed to the new partition - im sure lol i think - anyway, i went into partition program in kubuntu and still seen my windows partition and its  not empty and still has roughly what i figured spaced used up on it...so when i boot my pc i cant boot to windows kubuntu loads automatically.  I had installed easybcd or whatever(something along those lines) before installing kubuntu probably bad idea, but that's what i installed...just saying...so can someone help me please and thanks.

---

### Post by Bucky Ball on 2011-06-21
Open a terminal and:

```
sudo update-grub
```

To get to the grub menu at boot you need to hit 'ESC' or 'Shift', can't remember which for 11.04.

You can change the timeout permanently by opening /etc/default/grub, looking for and editing this line:

```
GRUB_TIMEOUT="20"

```
That will give you the menu for 20 seconds at boot. Yours currently would look like this:

```
GRUB_TIMEOUT="0"
 
```

---

### Post by wwe9112 on 2011-06-21
> **Bucky Ball said:**
> Open a terminal and:
 
```
sudo update-grub
```
 
To get to the grub menu at boot you need to hit 'ESC' or 'Shift', can't remember which for 11.04.
 
You can change the timeout permanently by opening /etc/default/grub, looking for and editing this line:
 
```
GRUB_TIMEOUT="20"

```
That will give you the menu for 20 seconds at boot. Yours currently would look like this:
 
```
GRUB_TIMEOUT="0"
 
```
 
OK, i can now get to grub but cant see anything...on my monitor hpw1907 it comes up and says input signal out of range, change to 1440 by 900 at 60hz...sometihng like that not exact but you get the jist lol...if i hit enter when that comes up i can get into kubuntu if i hold down a seecond then hit enter i can get into windows.

---

### Post by wwe9112 on 2011-06-21
OK, I got it!  I had installed startup manager and changed the resolution lol tanks for yoru help, another question though, how do I change my boot up manager to be that easybcd program?  Thanks

---

### Post by Bucky Ball on 2011-06-22
Please post another thread with a descriptive title for your new question. You'll have much more luck getting help.

Good news you fixed the first issue. There is also Grub Customizer and Ubuntu Tweak for tweaking the boot menu/options. Grub Customizer is particularly cool. ;)

---

