---
title: "Ubuntu 11.04 installation blank-screen"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by goricko on 2011-04-28
Hey everyone

Ive been successfully running ubuntu 10.10 desktop on my lenovo s10

Lately i've changed to windows 7, but with the introduction of 11.04 decided to check it out.

Did everything i was meant to (download the .iso, install it on usb etc)

Everything went smoothly until reboot, after the the laptop starts rebooting the black screen appears with a little line at the top left corner that keeps constantly flashing.
I have left it for about an hour but it didnt do anything.
Repeated the installation about 3 times, tried again but same thing

What should i do? Is it the memory stick that is faulty or something wrong with my laptop?

Thanks

---

### Post by slooksterpsv on 2011-04-28
When booting the computer hold down SHIFT for the grub menu to appear, Linux should be at the top, press the e key on the keyboard, go down to a line that looks like this:

linux /boot/vmlinuz..... lots of information after that

Go down to the next line (initrd /boot...) and press the left arrow key so your at the end of linux /boot/vm....

Now press the spacebar and type in nomodeset

Press CTRL+X and see if that helps.

EDIT:

So mine normally looks like:

linux /boot/vmlinuz-2.6.38-8-generic root=UUID=65e6aaee-3822-2342-a1\
3a-882342840824 ro  quiet splace vt.handoff=7

Adding nomodeset makes it look like:
linux /boot/vmlinuz-2.6.38-8-generic root=UUID=65e6aaee-3822-2342-a1\
3a-882342840824 ro  quiet splace vt.handoff=7 nomodeset

---

### Post by Dutch70 on 2011-04-28
By doing everything you should have, I take it you mean that you...
a) checked the md5sum of the downloaded iso.
b) checked the disk for defects
c) selected "Try Ubuntu" to make sure it worked well with your hardware before installing. 

Did you do these things?

The only thing other than those that I could recommend would be selecting different boot options such as nomodeset by pressing F6 when you get to the screen with the stick man & keyboard, I believe.
Edit: slooksterpsv was posting at the same time, and it looks like he is more familiar with nomodeset.
I've never had to use it.

---

### Post by goricko on 2011-04-28
Did what you said but didnt go far

Pressing/holding SHIFT didnt do anything

Pressing f6 didnt work as well

What does work is f12 which brings me to the boot menu and f2 which brings me to start setup

btw as a reminder i am using windows 7...(just in case)

---

### Post by inigo48 on 2011-04-28
i have exactly the same problem.
i got a "loading operating system" line on the top of black screen, if i press the shift i got a "grub loading" line but it doesnt matter because i get a black screen after all, where my monitor write out that, this is not the optimum mode and the recommanded resolution.

some help would be great because right now i have no useful OS at all, only the live usb pednrive...

edit: vga: intergrated nvidia 7025/nForce630a+

---

### Post by slooksterpsv on 2011-04-28
If you see the grub loading... screen continue to hold the shift key till you get a menu that looks like this:

---

### Post by goricko on 2011-04-29
I dont want to look dumb but i did  everything possible after the computer starts up

Pressing SHIFD DOESNT WORK!! NOTHING HAPPENS!

I dont get further than a point when my computer's brand shows up and then when after the brand goes away, all i get is the flicking  line like this "_" and nothing else happens unless i unplug the memory stick. After i unplug the memory stick it says "Problem loading Operating System" (obviously).

GRUB doesnt load! Nothing does... 

So i dont know what else to do. I've tried to load 11.04 like 10 times,  but all i get is the flashing underline!!

It seems i am unable to do the NOMODESET , i wanna know if you have something else to help me install the cursed 11.04

Thanks

---

### Post by Dutch70 on 2011-04-29
See a,b,& c in post #3.

---

### Post by goricko on 2011-04-29
Look

Tried booting with a different memory stick, it booted but at the beggining menu where it says "run ubuntu" "install ubuntu on a current hard drive" etc. Everytime i press enter my laptop makes a loud bleep and doesnt boot (stays the same). 
When i type in "menu" it leads me to the same menu but with a different style, with different options screen.
I tried the NOMODEST thing but no luck, tried alternative boot (or whatever it was called). But failed.
When clicking the "run ubuntu" it gives me an error saying "/casper/vmlinuz/file not found". X(
I dunno what to do, currently i am doing a memory check, which is 24% loaded to see if the hardware is working fine.

See what happens.

---

### Post by goricko on 2011-04-29
Dutch 70

i have read the third post bt i dont know how to do either three options. if you could help me with links or  other help

thanks

---

### Post by TruePurple on 2011-04-29
I have a similar problem, except I didn't upgrade from a disk but from 10.10 and downloading the files through its update process. 

Does seeing these flashing white dashes at the top of my screen mean the update is not happening and it is safe to restart and try things?

---

### Post by hyperrjas on 2011-04-30
Not working, I have the same problem too. Y trying update gru, repair ubuntu this menu grub. I can enter in ubuntu server 11.04 in recovery mode.

Some fix for this problem?

Thanks

---

### Post by goricko on 2011-04-30
So yesterday i tried to install ubuntu using my other memory stick using a rescue mode install
That completely messed up my laptop and it didnt even boot up.

I tried everything on the next day using another memory stick (3rd one) (transcend) and VOILA it boots perfectly.
Thanks guys for helping me go this far. ;) ill have some good time with 11.04

---

### Post by Marric on 2011-04-30
Got same problem here after update from 10.10 to 11.04.

My Computer is an Acer eMachines E527

Found a solution that suited me on:
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/772785](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/772785)

Greetings

---

### Post by Dutch70 on 2011-04-30
Marric, please start your own thread so that both you and the OP can get the undivided attention your problem deserves. 
Read this first...[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1422475[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1422475")

goricko, this should help. 
[[COLOR="RoyalBlue"]HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")
[[COLOR="RoyalBlue"]CDIntegrityCheck[/COLOR]]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck")

Of course the last one is just a matter of selecting "Try Ubuntu" instead of "Install Ubuntu". Which, the integrity check is too.

---

### Post by radugalu on 2011-05-15
Hello, I found a workaround:
 - immediately after boot, start pressing UP and DOWN arrows one after each other (UP, DOWN, UP, DOWN, ...)
 - doing this will show the menu (first thing will be the language selection)
 - after selecting the language, you can choose "Install Ubuntu" (do not press Enter!)
 - then select "nomodeset" by pressing F6
 - then press Escape
 - then press Enter to install

This last part (selecting the "nomodeset" option) is already known on the forums, what I did not found until now (pressing the arrow keys) is a way to get to the menu.

It worked for me... Good luck!

PS: I found it very disappointing that Ubuntu team did not fixed this bug since Ubuntu 9.10 or 10.4... :-(

---

