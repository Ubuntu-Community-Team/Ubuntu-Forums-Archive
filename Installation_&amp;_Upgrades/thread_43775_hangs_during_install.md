---
title: "hangs during install"
date: 2005-06-23
forum: Installation &amp; Upgrades
---

### Post by Lambert on 2005-06-23
I am fairly new to linux. I downloaded a copy of ubuntu and tride to install it last night. It went through the core/base install, copied all the packages, set up a user account, then it comes to a screen that says "configuring apt" under the progress bar it says setting up primary installation repository. The progress bar gets to 25% and then the installation just freezes.

My system specs are
msi rs480m2 mb with amd64 3000+
seagate ide ultra 100 120gb 7200 8mb hdd (st3120026a)
integrated ati x200 graphics
memorex optical cd/dvd combo drive
512mb dual channel ram

I have played with and loaded a couple other linux distros on this set up with no problems also ran a couple live cd boots on it. This is the second distro I've had trouble installing though.

Can somebody help? :?

---

### Post by ludzter on 2005-06-23
I have have the same problem, did you fix yours? i have asked around, but they seams to think its a broken iso, but i have downloaded it from 3 diffrent comuters (and new isp´s and new burners)..

so if you know how to solwe this i would looooove to know how...

//Ludde

---

### Post by Lambert on 2005-06-23
No, I can't play more until tonite. I've had some suggestions in other forums such as before starting; add  "ide=nodma" "nodma" "acpi=off" in the command line for install. I'm not 100% sure what this means being new to linux.

I've also been told to unplug any hardware that can be and install it after os is running.

I tried the i386 iso on my pc and am running an amd64 system so two more things I will try is the amd64 iso and also the livecd versions.

Wish I could offer more, waiting on somebody with experience to reply.

If I get it working I post what I did to get it working. Have you tried other distros? Are you new to linux?

---

### Post by mingus on 2005-06-23
[QUOTE=Lambert]I am fairly new to linux. I downloaded a copy of ubuntu and tride to install it last night. It went through the core/base install, copied all the packages, set up a user account, then it comes to a screen that says "configuring apt" under the progress bar it says setting up primary installation repository. The progress bar gets to 25% and then the installation just freezes.

My system specs are
msi rs480m2 mb with amd64 3000+
seagate ide ultra 100 120gb 7200 8mb hdd (st3120026a)
integrated ati x200 graphics
memorex optical cd/dvd combo drive
512mb dual channel ram

I have played with and loaded a couple other linux distros on this set up with no problems also ran a couple live cd boots on it. This is the second distro I've had trouble installing though.

Can somebody help? :?[/QUOTE]

So are you able to get in to Ubuntu?  If so, get in a terminal and switch to root ($su) and do #base-config

This will re-run the second stage of the installation.  When you get to the step of configuring the apt-get repositories, try using only the CD - not the net.  This should give you a vanilla Ubuntu.   It will be easy to add the http repositories later and the updates will be virtually automatic.

---

### Post by Lambert on 2005-06-24
I'm on dial up so it's not connecting to the net but here's where I got to so far.

I tried kubuntu and through another source tried this at the inital boot screen.

boot: linux ide=nodma acpi=off

I was able to finish the installation process and boot onto the drive but I can not get it up and running. I get a "wallpaper" screen or "background" with the kubuntu logo and the cursor shows at the center of the page. It freezes at that point though. Cursor does not move. I can boot into recovery mode but I'm a newbie and don't have a clue what to enter if there is anything that will help me move forward.

I also went back and cleaned the disk and trie ubuntu again. with the same nodma and acpi commands I was able to comoplete install. I can boot into a login screen but it won't recognize a user or password. When I installed I chose the option to not set up a user at that time. Is there something special here I need to type to get onto root? There was a button called session I clicked on, it popped up a prompt,  I chose the second option (don't remember what it said) and my pc froze.

Can anybody guide me on where I should go from here? I really want to get kubuntu going as from my research it seems kde is more popular and probablier a little easier for a newbie.

---

### Post by jsimmons on 2005-06-24
[QUOTE=Lambert]I'm on dial up so it's not connecting to the net but here's where I got to so far.

I tried kubuntu and through another source tried this at the inital boot screen.

boot: linux ide=nodma acpi=off

I was able to finish the installation process and boot onto the drive but I can not get it up and running. I get a "wallpaper" screen or "background" with the kubuntu logo and the cursor shows at the center of the page. It freezes at that point though. Cursor does not move. I can boot into recovery mode but I'm a newbie and don't have a clue what to enter if there is anything that will help me move forward.

I also went back and cleaned the disk and trie ubuntu again. with the same nodma and acpi commands I was able to comoplete install. I can boot into a login screen but it won't recognize a user or password. When I installed I chose the option to not set up a user at that time. Is there something special here I need to type to get onto root? There was a button called session I clicked on, it popped up a prompt,  I chose the second option (don't remember what it said) and my pc froze.

Can anybody guide me on where I should go from here? I really want to get kubuntu going as from my research it seems kde is more popular and probablier a little easier for a newbie.[/QUOTE]
 I have something even more bizarre.

I installed ubuntu twice without any problem.  Now, it hangs in the same place as you guys are seeing.  The first two times I installed, it was onto an 80gb IDE drive. This time, it's a 160gb SATA drive.

I tried the ide=nodma thing, and that didn't work. I guess it's time to try burning a new cd...

EDIT: And that seemed to do the trick.

---

