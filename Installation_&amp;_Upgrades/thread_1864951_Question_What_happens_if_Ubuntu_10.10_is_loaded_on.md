---
title: "Question: What happens if Ubuntu 10.10 is loaded on failed 11.10?"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by Gorrest on 2011-10-19
I am not a computer programmer.  I pushed the upgrade for 11.04 to 11.10 and have reached the purple screen and "Booting System Without Full Network Configuration"  and the "checking battery state".  I can get the Grub menu but rebooting means right back to the purple screen.  I put in a USB stick with 10.10 on it and  it works but I did not click download - I only used test 10.10 off the USB stick.  What would happen if I downloaded 10.10 on top of the failed 11.10 installation?  Would the computer become totally confused?  I am posting this from a scond computer with 10.10 which reminds me that 11.04 is available, but no way will I chance messing this computer up.  The computer with the failed 11.10 update has an Asus board with Radeon 4200 onboard +  Sempron 140 CPU and 2 gb of DDR2 Ram and a WD 500 gb HDD -  I would pull the HDD out and erase it if a HDD external eraser existed and insert it back and load Ubuntu 10.10 from the USB stick - that would definitely work!

---

### Post by critin on 2011-10-19
> **Gorrest said:**
>  What would happen if I downloaded 10.10 on top of the failed 11.10 installation?  Would the computer become totally confused?

Do you mean 'if I INSTALLED 10.10 over 11.10?  Instead of  'DOWNLOADED'?  Two different things.

I've done this type of installation lots of times and it gives me no problems.  Just choose to erase and install when it gets to screen where you choose where to install.  Be sure it picks the correct partition, unless you're using the entire disk.  If you have more than one OS, you will choose 'something else', and then choose the right partition.  It will overwrite the old installation.

critin

A Tip:  On the update manager, there is a 'settings' link at the bottom of the page.  Click on that and change the settings to 'don't notify of upgrades', or only LT versions, whatever it says. Then it won't remind you to upgrade until a stable version comes out.

---

### Post by Gorrest on 2011-10-19
Thnx for help.  My sole experience with downloading  a  OS is twice  on new HDD's from  the USB stick with Ubuntu 10.10 on it. Partition?  That is what I need to learn about since a new or blank HDD does not need a partition.  You are correct - I could click on the don't notify of upgrade or I could resist clicking on it .....or the upgrade could not be offered until more sorted out - that would work too.

---

### Post by critin on 2011-10-19
> [I]<<Partition?  That is what I need to learn about since a new or blank HDD does not need a partition.>>

Okay, if this is the only os on the disk, just choose, Erase and install--use entire disk.  No partitioning needed.  You can always install another OS at a later time and it will install alongside this one if you wanted to.  It will partition itself.  It's very easy and safe in my experience as a newbie.

> <<or the upgrade could not be offered until more sorted out.  <<  I pushed the upgrade for 11.04 to 11.10 [/I]>>

It sounds as if you upgraded to 11.04 then again to 11.10 at the same sitting, that's pretty intensive.

Many users have no issues with upgrades, but this seems a particularly difficult one.  I didn't upgrade **after reading the forums**,  but I downloaded a fresh os and installed on a separate partition so I could test it safely.  It does everything I want it to do so far.  I just don't care for the menu option, so won't be using it for work.

[I]critin 
[/I]

---

### Post by Gorrest on 2011-10-19
I had 11.04 working with all the updates through a few days ago - I resisted clicking on upgrade to 11.10 for several days.  The USB stick with 10.10 on it is months old but I think I will try it anyway.  It is a brown screen initially with a choice of test or download - I have used test but I don't remember what happens when I push download - does the download begin immediately or does  another page pop up with more choices?  My worry of course is having 11.04 and a failed 11.10 and 10.10 on the HDD and how does the computer sort them out?  I would hate to see that purple screen again with "Booting system without full network configuration".

---

### Post by critin on 2011-10-20
If you click Install, it will go to the same install page that it does in the Live mode.  (What you're calling the 'Test mode, which is also correct.)  I like to choose Try/test and then install from the desktop. I feel I have more control from there.   It doesn't matter though--your choice.

It will erase everything and format the disk before beginning the install, so you will basically will be installing on a clean disk.

If you have any personal files you want to keep, copy them onto another flash drive before doing anything else.

critin

---

### Post by Gorrest on 2011-10-20
OK, thank you sir.  My advice to everyone  is unless you have time and expertise, just wait on 11.10 and download it to a USB stick.

---

### Post by critin on 2011-10-21
I recommend using the LT 10.04.  It and 10.10 are stable with no issues (for me).  Try newer versions in virtual or separate disk *and leave your perfectly working OS alone*.  

If it ain't broke...why break it?

critin

---

