---
title: "Grub problems! Can't get to my data! Help!"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by dogscoff on 2008-03-25
Hi,

I'm having real trouble with my dell 500m laptop, running Feisty.
It has been absolutely fine for months, and then suddenly it started acting wierd... the touchpad wouldn't respond, nor would a usb mouse. Since I couldn't find any keyboard shortcuts to shut it down gracefully, I had to do a hard reset by hooding down the power button.

Of course then the hard drive wanted fsking, so i did that. But now it refuses to boot! It says Grub error 17.

Fine, I think, I'll boot a live CD, see if the mouse works there, backup all the data, re-install ubuntu and put the data back.

So I downloaded a gutsy live CD. It boots, eventually, but then demands a username and password. I've treid every user/pass combo I can think of and/or google for (root/root user/pass demo/demo, the user/pass that should be on this machine... lots of others) but nothing works! I try alt+f1 to get to a terminal but that's locked with lots of "user not known to the underlying authentication module" errors, so that's useless. However from the login screen I was at least able to determine that the mouse problem wasn't hardware related. 

So I download a grub superdisk ISO to try and fix the bootloader and get to my files that way... 
findf /grub/stage1 /bott/grub/stage1
Error 15 file not found.

So I can't boot from the hard drive, I can't boot from a live CD and I don't know how to fix the bootloader. I can't even pull the HD out and put it in another machine because it's a laptop!!!

What do i do? How can I fix this? I need the data off this machine!

---

### Post by dogscoff on 2008-03-25
I should add, a memory test (initiated from the gutsy live CD) reported no errors after 4 passes and about 90 minutes. I cancelled it because I didn't know how long it would go on for, or if it would ever finish at all.

---

### Post by chex_m8 on 2008-03-25
i'm not sure how to solve your problem, but usually lap top harddrives are easy to access. you just have to undo one of the panels underneath.

---

### Post by buntu_Geek on 2008-03-25
The username for live cd is "ubuntu"  and password is nothing... that means you have to press <enter> when you are asked for the password..

And then... you can restore your grub...

That should work...

But i m not sure about the mouse and touch pad probs...

Hints: 
Check using the "lsusb" command whether your usb mouse is detected....

---

### Post by prshah on 2008-03-25
> **dogscoff said:**
> What do i do? How can I fix this? I need the data off this machine!

If you still have Windows running, you can install the ext2/3 ifs driver to access your linux partitions in Windows. It easy to find, download, install and use. Hint: google is your friend.

---

### Post by dogscoff on 2008-03-27
ubuntu / no password (with various combinations of capitalisation) was one of the passwords I tried, it didn't work.

Anyway, i got it all fixed. I used an old Feisty live CD I had. With that I was able to get to the file system and copy off all the important data. I also fscked the drive from there again, and once I'd done that supergrub was able to repair the bootloader. 

Then I installed Gutsy anyway, since I'd already downloaded the alternate install CD and had an hour or two to spare. Putting the data back on was a breeze (I love the way you can restore thunderbird by just copying in the folder... )

Thanks for the replies. If anyone's interested I have a new problem now but I'll start a new thread for that. =-)

---

