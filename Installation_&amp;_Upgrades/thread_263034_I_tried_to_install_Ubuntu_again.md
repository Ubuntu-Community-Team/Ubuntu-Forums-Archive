---
title: "I tried to install Ubuntu again"
date: 2006-09-22
forum: Installation &amp; Upgrades
---

### Post by Dazza on 2006-09-22
I installed Ubuntu, well, got to sorting out the partition table and Ubuntu messed it up.

I tried to create a 1024mb linux-swap partition aswell as a 10gb partition for Ubuntu.

When I clicked next to decide which partitions to use what, I had a 103gb partition, a 723Kb partition and the other ubuntu couldn't recognize.

I booted down and tried to get back into XP, but i have a "no operating system" message. Anyway to get this back or did ubuntu **** me over for good?

---

### Post by jocheem67 on 2006-09-22
Load your XP-cd, let it boot up and go to the command-line ( "repair windows"  )..

Just type at the prompt "fixmbr"...

that's all....

If this is too vague for you, then just google on 'fixmbr'..

cheers.

---

### Post by Dazza on 2006-09-22
Yeah thats what I thought to do but better ask for more info, as that probably wont work as Ubuntu deleted teh partition, not ruined the MBR.

Now when I go to repair console it asks for a password, I don't have one, and the blank space doesnt work. Great. Thanks "Most friendly linux os ever".

---

### Post by muffinhead on 2006-09-22
Well if you had followed the direction's during install, you wouldn't of ended up with this problem, and is not the fault of ubuntu.

i.e. If you want to dual boot winxp, and ubuntu, you are supposed to create a seperate partition for ubuntu to use, and format only that partition that ubuntu and the swap file must reside on.

For example, after you create the ubuntu partition, with a partitioning utility, and you have the Ubuntu cd popped in, and booted, you click install. 

Then the install interface will ask you which partition you want to install ubuntu to, choose Manually edit the Partition Table, then choose the newly created partition you want to install ubuntu to, i.e. hda2, hdb2, hda5, or hdb5, dependeng on how many partitions you have it'll be one of those. Click install, and it'll set up the boot loader so you can dual boot.

However make Sure you do not overwrite your Windows XP install, that means as well Do Not install Ubuntu to the Windows XP Partition, and make sure the checkbox labled as format this drive is not checked, that your windows XP resides on.

Window's Xp usually resides on hda1, in other words Hard Disk Drive 1, C:\ drive, so if you want to keep windows xp, Do Not format that Drive, or install ubuntu to that partition.

Hopefully someone can simplify what I wrote, or make it more clear. Hopefully someone can link you to a website or tutorial on Dual-Booting Linux and Windows Speciffically Ubuntu.

Ubuntu is the most user friendly Linux distro in my opinion, it was just one small or big mistake on your part. Alway's make sure to read the directions during install, to prevent mistakes like these:)

Also an alternative is, you can install ubuntu to a virtual machine, such as VMware Player, or VMware Server, if you don't want to risk accidentally losing your data, and still test ubuntu, and get the full experience;)

No I'm not trying to be a jerk, I'm just trying to offer some friendly useful advice, and am sorry if it's taken the wrong way;)

---

### Post by Dazza on 2006-09-23
<snip>

---

### Post by muffinhead on 2006-09-23
I was not trying to be an *** or anything, and you resorted to a flaming insult. I am not protecting Ubuntu, nor am I associated with them. I am just another user of ubuntu, like you were/are.

It seems funny, that I haven't had that problem before, and I've installed/Unistalled Ubuntu, Resized, Deleted and Recreated my Partitions, and I've never botched my Windows XP Install, nor have I messed up, only maybe once when I was fairly new to Linux. Of course, I do use a Windows XP Program,  Partition Magic, to make my Partitions.

And how the heck am I supposed to know how long you've been using linux? I'm not some sort of a mind reader. You acted like I was supposed to know that miraculously.

If you want the Proper help, Try being a little more polite, instead of saying Ubuntu is a Piece of Sh!t, or a piece of crap, Such an attitude, or choice of words, will only will make people less likely to answer your thread, and offer help.

I wasn't being nasty, or giving you an attitude, I was just trying to offer help, and stating what could of possibly went wrong, and it seems you downright insulted me in a yet nonschelont way (excuse my misspelling). I Apologize if it was taken the wrong way, and saying it was entirely your fault, I just have never ran in to such a problem in my 8 months of using linux, and 5 months of using Ubuntu, and yes I am quite a Linux Newbie. I Grew up on Microsoft Windows, and just started recently dual-booting Windows XP and Ubuntu, and use ubuntu for my web browsing. But it doesn't mean I don't know a thing or two;)

---

### Post by jocheem67 on 2006-09-24
The question remains if you did or did not ( or ubuntu ) mess up your vista install, it is kind of crucial.

Maybe it's time to clean up your partitions all the way and start all over again?

---

