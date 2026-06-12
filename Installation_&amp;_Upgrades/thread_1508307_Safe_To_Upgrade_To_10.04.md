---
title: "Safe To Upgrade To 10.04?"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by SirKablaam on 2010-06-12
About 3-4 weeks ago, I tried upgrading from 9.10 to 10.04 several times, using all of the methods. However, every single one of them had a bug; a black screen, completely blank. I saw other people had this problem and did everything others suggested, but yet I still got that black screen. So I decided to wait a few weeks and see if most of the bugs have been fixed. So is it safe to upgrade now? Thanks! :KS

---

### Post by darkod on 2010-06-12
In most cases these are not bugs. Maybe your video card doesn't work out of the box with 10.04, or another problem, etc.

What did you do after the failed upgrades? Did you clean install 9.10 again? Did you try clean install of 10.04?

The first step you can do is download the Lucid ISO and make a cd with it. Boot with the cd in live mode (or try to) and see if that works fine. Usually if there is video driver problem, the live mode won't work too.

If you notice there is a problem there are things to try for the install to be successful and the problem fixed after that.

---

### Post by sites on 2010-06-12
What motherboard and graphics card are you using?

---

### Post by SirKablaam on 2010-06-12
> **darkod said:**
> In most cases these are not bugs. Maybe your video card doesn't work out of the box with 10.04, or another problem, etc.

What did you do after the failed upgrades? Did you clean install 9.10 again? Did you try clean install of 10.04?

The first step you can do is download the Lucid ISO and make a cd with it. Boot with the cd in live mode (or try to) and see if that works fine. Usually if there is video driver problem, the live mode won't work too.

If you notice there is a problem there are things to try for the install to be successful and the problem fixed after that.

Like I said, I did everything, including the Live CD. And after I failed (about 5 times) I reinstalled 9.10. However, I don't think it was a problem with my video driver since in one installation I got a few options at boot-up, one of which was low-graphics mode. But everything was too small so my eyes were straining and it became a nuisance to having to micromanage each bootup, so once again I (idiotically) tried to reinstall 10.04. If it is a problem with my video driver, my graphics card is a Intel® Graphics Media Accelerator 950. Yeah I know, pretty low-grade, but I'm only 15 and all I could afford is an eMachine :lolflag:
EDIT: Here's my motherboard: Intel® 945GC (the site for my computer says chipset, so I hope I copied the right thing)

---

### Post by darkod on 2010-06-12
Actually you said

>   I tried upgrading from 9.10 to 10.04 several times 

Upgrading is one thing, clean install of an OS is another. For clean install it doesn't matter which version or which OS you had before.

Anyway, lets focus on the latest 10.04 with more specifics.

Did the cd load in live mode correctly, without any issues? If it did, after you install it should work.

---

### Post by SirKablaam on 2010-06-12
> **darkod said:**
> Actually you said



Upgrading is one thing, clean install of an OS is another. For clean install it doesn't matter which version or which OS you had before.

Anyway, lets focus on the latest 10.04 with more specifics.

Did the cd load in live mode correctly, without any issues? If it did, after you install it should work.

Well, I tried upgrading AND doing a clean install; sorry for any confusion. And yes, the CD did load correctly, I saw the menu and everything, checked for defects, the whole works. Also, I selected "Try Ubuntu Without Installation" I got the same black screen problem. Rebooted my computer, selected "Install Ubuntu", watched the progress bars. Ubuntu wanted to restart my computer, and so it did, with the black screen.

---

### Post by darkod on 2010-06-12
Nothing to be sorry about, but you understand that we depend on what you say, we can't know what you did otherwise. :)

The Try Ubuntu giving you black screen was your first sign, in that case it will most probably give you black screen after the install too. And it did.

Can you try booting again with Try Ubuntu, but this time hit any key when you see the ubuntu splash screen. That should show the menu. Hit F6 for advanced options, and see if there is nomodeset there and use it.

If there isn't, highlight the Try Ubuntu option but don't hit Enter, hit 'e' instead. It should show you lines for editing. Move to the end of the line starting with linux, delete quiet splash and type in nomodeset.
Hit Ctrl + X to try to boot into Try Ubuntu and see if that worked.

---

### Post by SirKablaam on 2010-06-13
Well, I burned the .iso to a blank CD with PLENTY of space, so not the entire disc was used :D. However, when I clicked on "Try Ubuntu Without Installing" all it gave me again was a black screen. What else is there for me to do?

---

### Post by darkod on 2010-06-13
> **SirKablaam said:**
> Well, I burned the .iso to a blank CD with PLENTY of space, so not the entire disc was used :D. However, when I clicked on "Try Ubuntu Without Installing" all it gave me again was a black screen. What else is there for me to do?

Look at my previous post.

---

### Post by SirKablaam on 2010-06-13
> **darkod said:**
> Look at my previous post.
Okay, right now I'm running 10.04 OFF the disc using "nomodeset" like you told me. Everything looks PERFECT!!! However, I'm a little timid to do a fresh install. Not because I'll be losing anything valuable, more like "I'm scared it won't work like this" kinda deal. Any more instructions or tips to foolproof this whole ordeal?

---

### Post by darkod on 2010-06-13
> **SirKablaam said:**
> Okay, right now I'm running 10.04 OFF the disc using "nomodeset" like you told me. Everything looks PERFECT!!! However, I'm a little timid to do a fresh install. Not because I'll be losing anything valuable, more like "I'm scared it won't work like this" kinda deal. Any more instructions or tips to foolproof this whole ordeal?

In this situation usually you can go ahead and click the Install icon on the desktop in live mode. That should finish the install process OK.

But on the first restart after finishing the install it will NOT boot without the nomodeset parameter, just like it didn't boot into live mode.
If you have windows installed too, on the first start you will get the boot menu. Highlight the ubuntu entry but hit 'e' not Enter. Again go to the end of the line starting with linux and add nomodeset. That should boot your hdd system correctly. Go into System-Administration-Hardware Drivers to check if new drivers are offered. Maybe some of them will sort out the issue.

If you have only ubuntu, there will be no menu at start. You need to start pressing Shift as soon as the BIOS is done, before ubuntu starts loading. The Shift will show you the menu even when ubuntu is the only OS. After you get the menu do as above.

After you boot it, do the updates and check for drivers as explained above. Then try restarting and don't enter nomodeset, see if it will start on its own.

If it doesn't, restart and this time add nomodeset again. After ubuntu boots, to make the parameter permanent you can open the /etc/default/grub file and add nomodeset in the "" in the GRUB_CMDLINE_LINUX="".

After that run:

sudo update-grub

to create new grub.cfg. That will make the parameter permanent and you shouldn't need to enter it on every boot.

---

### Post by SirKablaam on 2010-06-13
Thank you so so so so much! I've wanted to upgrade for about two months, and now...I finally did! You sir are the most helpful person on here, thank you so much!

---

### Post by darkod on 2010-06-14
> **SirKablaam said:**
> Thank you so so so so much! I've wanted to upgrade for about two months, and now...I finally did! You sir are the most helpful person on here, thank you so much!

You're welcome. Enjoy Lucid now. :)

---

