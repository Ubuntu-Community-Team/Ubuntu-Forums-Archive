---
title: "Installation quits-looses keyboard"
date: 2005-07-04
forum: Installation &amp; Upgrades
---

### Post by maryjo on 2005-07-04
On my first attempt to install I read that Ubuntu will not install over another GNU/Linux so I cancelled installation and went back into windows XP to disc management and deleted the partition for Linspire to free up the space.  Now I notice that I still have the dual boot showing Linspire but if I try to boot it up, it just sits there at the opening screen.  I don't know how to get it out of the boot.

On my second attempt to install, I couldn't complete the installation process.  I got to "Enter a password for the new user..." and can't get a response on screen to the word I am entering. The blanks stay blank and the yellow cursor at the first blank stays there.   I couldn't go any further so I aborted.

The last thing I noticed is that the installation must have partially "taken" even though I aborted. I looked in my XP disk management screen and see I have the new partitions installed and they are "Healthy."

So here are the problems:
1. Linspire still shows at boot up even though I deleted it. How to remove it from boot?
2. Why can't I type a password?
3. I guess I should delete the new partitions and get the free space back before doing anything else?

Mayday!

Help will be greatly appreciated.

Mary Jo
Ocala, FL

---

### Post by maryjo on 2005-07-04
I am sorry....I just realized that I don't actually loose the keyboard, just the ability to type.  I can use the keyboard to tab back through screens but when I get to the password screen, I simply cannot get keyboard to respond to the blank spaces where the password should go.  Seems like the "Tab back/forward" key works and the enter key works but nothing happens with the regular keys.

Mary Jo
Ocala, FL

---

### Post by maryjo on 2005-07-04
I don't know if I should make a seperate thread of this but it is part of what I am experiencing with my original post.

The last thing I noticed is that the installation must have partially "taken" even though I aborted.  I looked in my XP disk management screen and see I have the new partitions installed and they are "Healthy."

So here are the problems:
1.  Linspire still shows at boot up even though I deleted it.  How to remove it from boot?
2.  Why can't I type a password?
3.  I guess I should delete the new partitions and get the free space back before doing anything else?

Mayday!

Mary Jo
Ocala, FL

---

### Post by MasterPatricko on 2005-07-04
Linspire on the boot menu should get removed when Ubuntu installs the new MBR. Did you get that far in the installation?

---

### Post by maryjo on 2005-07-04
I think not.  There is no Ubuntu in the boot menu, Just xp & linspire, although linspire was deleted by me.

I got to slide 16 of the installation guide, there wasn't much at all left to do but the system wasn't letting me type in a password.  Now I can't find the installation guide slides.

I really need help here.  I gave up on Mandrake.  I liked Linspire but not the constant sales pitch.  I had a wonderful experience with Ubunto Live and right now a real bummer with this installation.  I am disappointed.

Mary Jo
Ocala, FL
Hotter than the hammers of......!

---

### Post by codejunkie on 2005-07-04
the reason the linspire grub menu is still there is grub is installed on the mbr on the main harddisk if you want to remove it you have to put in your windows xp cd boot from it like you were going to install windows but choose recovery console instead 
when you enter the recovery console it will ask you to choose a windows installation do that and then it will ask you for a administrator password if you entered an administrator password when you installed windows that would be it if you didn't just press enter when you get to the command prompt there type fixmbr press enter there and that should install the default windows boot loader.

---

### Post by maryjo on 2005-07-05
That sounds straightforward enough.  Since today is a workday it will have to wait until tonight...assuming life doesn't get in my way, LOL.  Will let you know how I make out.

Mary Jo
Ocala, FL
Looking at a hot & humid week in the mid 90s

---

### Post by maryjo on 2005-07-07
codejunkie

Well, I succeeded in wiping my drive clean.  There go my genealogy files.  Photos.  Yikes!  In the process now of reinstalling.  I am too tired to be upset.

Onward with the adventure.

Mary Jo  ](*,) 

OMG...and my address book!   :-#

---

