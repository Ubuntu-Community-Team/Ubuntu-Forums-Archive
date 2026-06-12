---
title: "Keyboard not working after 10/4/2008 update"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Jove on 2008-10-05
I have an MSI laptop which has been running Ubuntu very nicely since Dapper. I upgraded to Intrepid a couple of weeks ago and have been pleased with performance (so far). However, I've been bitten by a nasty after last night's update/upgrade. Basically, the keyboard won't work any more. The keyboard works fine at the BIOS screen and I can select kernels ok via keyboard at the GRUB menu, but when I get to the GDM login screen the keyboard won't respond. Also, booting into recovery mode gives me a text menu where I have no keyboard control either. Also, booting into any of the older kernels from GRUB exhibits the same symptoms. I won't be home to try an external USB keyboard till later today, but are there any kernel options that I can add to the boot line to try to track this down? 

Cheers guys,

Alan

---

### Post by Delvien on 2008-10-05
> **Jove said:**
> I have an MSI laptop which has been running Ubuntu very nicely since Dapper. I upgraded to Intrepid a couple of weeks ago and have been pleased with performance (so far). However, I've been bitten by a nasty after last night's update/upgrade. Basically, the keyboard won't work any more. The keyboard works fine at the BIOS screen and I can select kernels ok via keyboard at the GRUB menu, but when I get to the GDM login screen the keyboard won't respond. Also, booting into recovery mode gives me a text menu where I have no keyboard control either. Also, booting into any of the older kernels from GRUB exhibits the same symptoms. I won't be home to try an external USB keyboard till later today, but are there any kernel options that I can add to the boot line to try to track this down? 

Cheers guys,

Alan

Try to see if the proper region for your keyboard has been chosen, something could of changed during the upgrade/install.

(system>prefs) I believe, I'm not home or I would tell you where to go.

A reconfigure will also ask what keyboard

---

### Post by Sef on 2008-10-05
>  (system>prefs) I believe, I'm not home or I would tell you where to go.

That is correct.  System > Preferences > Keyboard.

---

### Post by Jove on 2008-10-05
Well, yes - but the problem is that I can't get ANY keyboard response - so I can't login. No Capslock or other lights, nada. The keyboard is working though, as I can access the GRUB menu, memtest, etc. It's just that at the GDM screen (or the Recovery Menu if I choose that GRUB menu option) the keyboard is completely dead :(

---

### Post by Delvien on 2008-10-05
> **Jove said:**
> Well, yes - but the problem is that I can't get ANY keyboard response - so I can't login. No Capslock or other lights, nada. The keyboard is working though, as I can access the GRUB menu, memtest, etc. It's just that at the GDM screen (or the Recovery Menu if I choose that GRUB menu option) the keyboard is completely dead :(

Plug in a USB keyboard and see if you can type with that so you are able to check what I suggested.

---

### Post by Jove on 2008-10-05
Yep, plugging in an external USB keyboard let me log in successfully, and after a reboot everything (without reconfiguring anything!) was back to normal. Thanks for the help, guys - that was a weird one!

---

### Post by Delvien on 2008-10-05
No problem!

---

### Post by jonger on 2008-10-11
i had no mouse or keyboard on the update. to solve the problem:

ctrl+alt+F2 at the login screen

then typed

```
sudo apt-get install xserver-xorg-input all
```

then ctrl+alt+del
and it was fixed. but now there is no option for gnome on login option. On xfce now

---

