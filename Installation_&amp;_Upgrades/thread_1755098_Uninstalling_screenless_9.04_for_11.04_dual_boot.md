---
title: "Uninstalling screenless 9.04 for 11.04 dual boot"
date: 2011-05-10
forum: Installation &amp; Upgrades
---

### Post by EmmGeeImage on 2011-05-10
OK, here's my delemma...

I have Ubuntu 9.04 currently installed on my HP computer. Now, per my comment and question, which was never answered... I cannot see the login screen, but see the bios and splash screens. I have tried various work arounds, to get the screen to come back, but seemed to fail with every command at the prompt. Main answer from the prompt... "Cannot open display."

This is the same exact monitor that works in Windows XP, without fail.

Now that I need Windows to deal with Video applications, Windows MUST stay on this PC... or I don't get paid. 

I use Ubuntu for audio and all other applications.

Here's the issue...


I can see  the screen with Ubuntu's 11.04 disk, testing the new version. I'm able to go into "monitors" and adjust the resolution to fit the screen. 

This same thing cannot be done in 9.04.

I'm trying to replace 9.04 with 11.04. However, the dual boot install wants to install it next to 9.04... and not over it. I also need to keep Windows.

Now how do I accomplish keeping Windows XP and overwriting Ubuntu 9.04? I am confused by the partitions, and when I only Keep that Green "(NTFS)" part, or simply take one partition away, "there is no set root" comes up.

I cannot install Windows after Ubuntu, because the Computer Manufacturer (HP...aka trash PC company) will not let me keep any other operating systems on it, and will use the whole drive.

Please help to get this 9.04 uninstalled, to use 11.04. It will not ask to overwrite it either.

---

### Post by mörgæs on 2011-05-11
If you boot a live CD, you can run Gparted and delete the 9.04 partitions.

---

### Post by EmmGeeImage on 2011-05-11
I tried that, with the 11.04 DVD. Seems that if I take any part of the partition away, I get "no root" message. Also, seems that it wants to lay Ubuntu 11, next to 9. I do not want both.

Seems that What I have now is not going to uninstall 9.04 and fresh install 11.04. That's where Windows has a simpler advantage. But hate windows... with a passion.

Tried the 9.04 disk... literally saw nothing beyond the splash page. Same as 9.04 already installed.

Tried that "Gpart" thingy, you spoke of above... seems 9.04 has keys next to the  partition numbers. I can delete Swap and unallocated partitions, or even the NTFS, windows parts. However, Uuntu 11.0's "Gpart" program did not give me an option to log into those to delete them, or simply let me delete those partitions with 9.04 on them.

Am I stuck reformatting, via Microsoft?? Kinda looks like this upgrade thing is out of control. 

How can the program that "just works," not work well for me??? Well, at least for the moment.

Any thoughts on how to get this 9.04 either formatted, overwritten, or simply uninstalled? I cannot log into it  and see anything, beyond the splash, From the DVD setup or already installed program/OS. By the way, "recovery" mode does not let me see the program either.

I really need help on this one.

On a side note: 11.04's testing area misreports my screen size as 26." Never knew I was 11" bigger than that (has a complex now). I only had a 15" monitor in Windows.

---

### Post by mörgæs on 2011-05-11
Could you post an exact error message from Gparted or a screen picture, please?

---

