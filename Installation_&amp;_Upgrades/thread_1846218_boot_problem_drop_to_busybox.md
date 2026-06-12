---
title: "boot problem drop to busybox"
date: 2011-09-18
forum: Installation &amp; Upgrades
---

### Post by siengland on 2011-09-18
OK, I recently installed ubuntu 11.04 on my computer as dual boot with windows 7 (both are 64 bit versions).

Basically, my computer boots as normal to grb 1.99, giving options of ubuntu, ubuntu recovery, memtest and windows 7. Windows works fine, it boots as normal, but when I select ubuntu, it does any of the following:

1. Stays on the purpley screen grub defaults to and doesn't ever boot
2. Goes to black screen with cursor and never boots
3. Very occassionally boots staight into linux (hardly ever)
4. (Most common) drops to busybox built-in shell

I know from busybox I can type exit and it then gives some errors, which are too fast for me to read, then boots fine, but its a lot of hassle, and it doesn't always go here anyway.

I've tried purge and reinstall of grub, and it does exaclty the same. Also when I reinstalled ubuntu, I got the same result. 

I've no idea what to do, so if anyone can help that'd be great.

Thanks in advance for any answers :)

---

### Post by drs305 on 2011-09-18
A couple of your issues sound like video card problems. If this is the case, at the grub menu:
Press 'e' to edit the menuentry.
Cursor to the end of the 'linux' line and remove 'quiet splash' and add 'nomodeset'
CTRL-x to boot.
If it boots, go to Additional Drivers and try to install/reinstall your video card.

Note: Manually editing the menuentry in this manner is non-persistent. It won't permanently change your Grub settings/menu.

---

### Post by siengland on 2011-09-21
hey 

cheers for the tip, but all that happened is it dropped to busybox again, but this time gave me a load of text about all my drivers, and when it finally booted in, it couldn't find any additional drivers anyway - nor could it run unity which it normally can!

I'm gonna try rebooting and reinstalling the video card without changing the grub menu, but other than that, I'm not really sure what else I can do.

Hope you or somone else can help more! :P

---

### Post by drs305 on 2011-09-21
Of the four items you mention, only #4 could probably be a failure of Grub 2. 
1. If you get a purple screen, Grub has passed control to the OS.
2. The blinking cursor on a black screen is usually a video problem. If Grub has a problem, it will either tell you what it is or leave you at a 'grub' or 'grub rescue' prompt.
3. If the problem is with Grub, it will be consistent. It will pass control to the OS or fail *every time*.

This is not to say that the kernel options passed by Grub (the entries at the end of the 'linux' line such as *nomodeset* don't have an effect. Using the proper option solves certain problems, but Grub is just the messenger.

> I know from busybox I can type exit and it then gives some errors, which are too fast for me to read, then boots fine, but its a lot of hassle, and it doesn't always go here anyway.

This would be the area I think needs investigating but I'm not an expert on the boot process from the time Grub passes control to the appearance of the Desktop. You could try booting the Recovery mode and see if one of those options (such as Safe Graphics) proceeds to the Desktop.  

Hopefully your efforts will resolve it or someone else will be able to provide specific steps to help.

---

