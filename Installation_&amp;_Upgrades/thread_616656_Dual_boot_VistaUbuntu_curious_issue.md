---
title: "Dual boot Vista/Ubuntu: curious issue"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by InfernalNeutrino on 2007-11-18
I hope this isn't something that has been answered before, but I did do a search and couldn't find anything on the subject.

So I'm wanting to dual boot my wife's Sony Vaio SZ 491 with Vista and Gutsy, but have run into something ominous enough that I'd like to look into it before completing going ahead with the operation. Here is the situation:

I successfully created a large chunk of free space on the harddrive, and booted from the Live CD just fine. I've been using this website as a guide:
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

I selected the option "guided - use largest continuous free space" from the prepare disk space screen. When I move onto the "migrate documents and settings" screen, it does not find anything to move over, even though there should be two users to migrate over from vista. That is what is concerning me.

The reason for my concern is that a couple of months ago I tried to dual boot my own Vaio with Feisty, and got the same issue. At the time I simply continued the install, and everything appeared to work right until I booted Vista and got errors. Grub seemed to work right, and when booting it came up with the option for booting in either Vista or Feisty as advertised, but when I booted Vista it went into recovery mode and claimed I had damaged the operating system. I apologize that I can't be more specific about what error it had, but at the time I simply decided running only Ubuntu was a better idea:). As it is, I'm quite happy with my choice, but I'd rather not force my wife into using only linux.

So I guess my question is as follows: has anyone else had this migration issue, and has it actually caused errors for anyone else? Thanks!

---

### Post by logos34 on 2007-11-18
I don't use vista so can't say why it's not detecting your email, web browser bookmarks, My Documents and all the rest for each user...although I noticed the screenshot on that apc link is also blank, so maybe this is something specific to vista.  I have XP pro and it always wants to import outlook express, ie7 bookmarks, etc, etc.  The Migration assistent was added only back in Feisty, so maybe there's still a few bugs to be ironed out.

But considering the problem you had previously booting vista with grub I think you really ought to try using vista boot manager to boot linux.  As good as grub is [sometimes it's better to use vista]("https://help.ubuntu.com/community/WindowsDualBoot").  So get EasyBCD and [add linux to vista bootloader]("http://neosmart.net/wiki/display/EBCD/linux").  Remember to install Grub to the bootsector of the linux root partition, NOT the MBR.  i.e. -->'(hd0,x)' and not '(hd0)'

---

### Post by grindboy on 2007-11-29
BUMP! I think quite a few people are having the same problem my self included so some help with it would be nice! :)

---

### Post by Digger78 on 2007-11-29
I recently got a laptop with vista installed :( first thing i did was installed Gutsy :)

On the "prepare disk space" screen i chose "manual" (as i wanted to create a swap partition and a seperate partition for /home)

"migrate documents & settings"  showed nothing

when i rebooted there was an entry for vista in grub and there was no problem booting into either systems.

---

### Post by edwardTheGreat on 2007-11-29
> **Digger78 said:**
> I recently got a laptop with vista installed :( first thing i did was installed Gutsy :)

On the "prepare disk space" screen i chose "manual" (as i wanted to create a swap partition and a seperate partition for /home)

"migrate documents & settings"  showed nothing

when i rebooted there was an entry for vista in grub and there was no problem booting into either systems.

+1 for that

only difference is I'm still using the windows boot loader to boot to GRUB on my ubuntu partition, and then to Ubuntu from there (like logos34 said). Sorry I can't shed any light on your particular problem, maybe if you could try to boot into Vista again, and try to make a record of the actual problem/error message that comes up and post it someone might be able to help a bit.
:popcorn:
Ed

---

