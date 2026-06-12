---
title: "New Install and no terminal or graphics"
date: 2021-03-24
forum: Installation &amp; Upgrades
---

### Post by SnoopFogg on 2021-03-24
I installed Ubunut 20.4 as a dual boot on an ASUS FX705GM laptop with an NVIDIA GTX1060

Install appeared successful but the screen froze when I got to the login screen.  

I followed this advice to add "noapic noacpi nosplash irqpoll" instead of "quiet splash" in the grub.
[https://itsfoss.com/fix-ubuntu-freezing/](https://itsfoss.com/fix-ubuntu-freezing/)

Initially this allowed me to login and everything looked fine. 

I updated the Grub to make the change permanent, so now the Grub second line from the bottom says:
linux [load of stuff I haven't changed] ro  noapic noacpi nosplash irqpoll

Then there was a big update and the laptop restarted by itself.

Now I get a login screen and can login, but the screen there is blue and has my name in the top left with "trash" a few spaces below it.  

Ctrl Alt T does nothing.

Alt F2 allows me to write "gnome-terminal" but then it just goes back to the blue screen

I guess this has something to do with the Nvidia graphics but I'm completely stuck now as I can't even access the terminal.

Any help would be much appreciated

---

### Post by TheFu on 2021-03-24
Can you login using <cntl><alt>-F3 followed by a few <enter> presses?   There are multiple terminals, so F1 - F8 should be available. I think F7 is the GUI one, but don't know if 20.04 changed that or not.

Once logged in, you can run **sudo ubuntu-drivers autoinstall**

That's the theory. With 20.04, it should properly find any supported nVidia GPU drivers and install the recommended, tested, version.
If it is a laptop, there could be confusion between any iGPU built-into the CPU and the nVidia GPU.

And be certain to run 
```
sudo apt update
sudo apt full-upgrade 

```at least weekly and especially after a new install.

---

### Post by tea for one on 2021-03-24
> **TheFu said:**
> Can you login using <cntl><alt>-F3 followed by a few <enter> presses?   There are multiple terminals, so F1 - F8 should be available. I think F7 is the GUI one, but don't know if 20.04 changed that or not.

The access to TTY (using Ubuntu 20.04 and gdm3 display manager) has been changed as follows:-

Ctrl Alt F1 > Login Page
Ctrl Alt F2 > GUI Desktop
Ctrl Alt F3 > TTY3
Ctrl Alt F4 > TTY4
Ctrl Alt F5 > TTY5
Ctrl Alt F6 > TTY6

---

### Post by TheFu on 2021-03-24
lightdm appears to use tty7 (F7) for the GUI still, which is used by Mate DE. Other Ubuntu flavors might still use whatever TTY they always did.
Fortunately, trying the different TTYs is about 1 sec of effort for each.

When there are GPU issues, using a different TTY is handy.

---

### Post by SnoopFogg on 2021-03-24
> **TheFu said:**
> Can you login using <cntl><alt>-F3 followed by a few <enter> presses?   There are multiple terminals, so F1 - F8 should be available. I think F7 is the GUI one, but don't know if 20.04 changed that or not.

Once logged in, you can run **sudo ubuntu-drivers autoinstall**

That's the theory. With 20.04, it should properly find any supported nVidia GPU drivers and install the recommended, tested, version.
If it is a laptop, there could be confusion between any iGPU built-into the CPU and the nVidia GPU.

And be certain to run 
```
sudo apt update
sudo apt full-upgrade 

```at least weekly and especially after a new install.

Thanks, it's been a while since I used Ubuntu so forgot about the F1-8 terminals and they work fine.  I did wonder how it would handle the two GPUs, and I tried unplugging the power to see if it reverted back to the built in one (assuming it wasn't using that in the first place). But it didn't make a difference.  Anyway, the update / upgrade seemed to do the trick!  

Thanks everyone

---

