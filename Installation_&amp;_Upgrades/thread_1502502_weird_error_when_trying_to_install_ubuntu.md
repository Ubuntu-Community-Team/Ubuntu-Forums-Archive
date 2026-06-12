---
title: "weird error when trying to install ubuntu"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by ciminera on 2010-06-05
hello, this is my first post, i have a laptop running ubuntu and i thought it was time to run it on my desktop too. however, after following the instructions to the letter to make a 10.04 live cd, it wont run on my desktop

i have set it to boot from cd drive, and it shows me a purpley coloured screen and at the bottom has a pic of a keyboard then an = sign and a man in a circle.

after this, whereas on my laptop, the new version just went to a screen with the ubuntu logo and loaded fine, the desktop gets a black screen with lots of text on it. 

thinking perhaps my pc doesnt support the new ubuntu, i thought i would try 9.10, which loaded the menu, but then when i clicked any of the options there, i got the exact same screen with the exact same messages on. 

need to get it running as i formatted the pc only to find my windows disk was ruined near the end of reinstalling it and it wont let me finish installing windows so its a dead machine atm. 


thanks for any suggestions

---

### Post by ciminera on 2010-06-05
anybody? :(

---

### Post by DrMelon on 2010-06-05
I think the most helpful thing would be to copy down some of the text from the Desktop, at the black screen - this is important, because it's likely an error message. And once we know what the problem is, I'm sure people will be able to help much better.

---

### Post by ciminera on 2010-06-05
hey, yeah theres a tonne of it but the last 2 lines are

[0.600375][<c07a3308>] kernel_init + 0x0/0xb
[0.600438][<c0104087>] kernel_thread_helper + 0x7/0x10


since then i made a disk of the alternate install. managed to get to the menu screen, but when i press install i get a message saying kernel panic etc. 

i think i have spaffed the registry on the machine as when i had my windows problem i got an error saying that the license could not be authenticated so i followed some instructions from some website saying to change the drive letter. and the serious lack of ability to do anything has been since then. so i think im gonna have to wait til i can get hold of another windows disk and try recover it and fix the registry before i can install ubuntu.

---

### Post by Daddyo-613 on 2010-06-05
I had the same problem on two different machines. I already had Ubuntu 9.10 installed and tried to upgrade to the newest version 10.04. When the operating system tried to reboot, error messages came up such as "Kernel Panic" and VFS unable to mount root fs on unknown block (0.0) etc. Don't worry it's not likely your machine. There have been a lot of problems with the install and upgrade versions of Ubuntu 10.04.

Rather than try to correct the problem by editing the Grub boot program, you might want to use a live CD version of Ubuntu 9.10. Of course that would mean that you'd have get access to a working machine with an internet connection and a functioning read/write CD burner but if you don't have a functioning copy of that other O/S anyway you might as well give Ubuntu a try.

Don't give up. There are lots of friendly people online who will guide you.

Good Hunting

---

### Post by ciminera on 2010-06-06
yeah i got the same message with the 9.10 disk too. 

so plan is, get hold of another windows disk, run regfix to sort out the registry with my fingers crossed, and then either just install ubuntu 10.04 on it then or run them side by side.

i wont give up, i have been using ubuntu since the day after the acer aspire one was launched in the uk so this is my third version now and i love it. had no problems with it in a couple of years, then i dig out an old pc and have more problems in 48 hours with windows than ive had with ubuntu.

---

### Post by Daddyo-613 on 2010-06-07
I've come across a number of discussions about the differences in how 9.10 and 10.04 treat existing partitions. If the Grub is pointing to the partition that has an older Kernel and not the new one that you want to use as the active Kernel problems occur.

You might get some ideas 1by looking at this official Ubuntu WIKI:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Partition%20alignment%20changes%20may%20break%20some%20systems]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Partition%20alignment%20changes%20may%20break%20some%20systems") 

Good luck.

---

### Post by frank1e on 2010-06-07
> **ciminera said:**
> hello, this is my first post, i have a laptop running ubuntu and i thought it was time to run it on my desktop too. however, after following the instructions to the letter to make a 10.04 live cd, it wont run on my desktop

i have set it to boot from cd drive, and it shows me a purpley coloured screen and at the bottom has a pic of a keyboard then an = sign and a man in a circle.

after this, whereas on my laptop, the new version just went to a screen with the ubuntu logo and loaded fine, the desktop gets a black screen with lots of text on it. 

thinking perhaps my pc doesnt support the new ubuntu, i thought i would try 9.10, which loaded the menu, but then when i clicked any of the options there, i got the exact same screen with the exact same messages on. 

need to get it running as i formatted the pc only to find my windows disk was ruined near the end of reinstalling it and it wont let me finish installing windows so its a dead machine atm. 


thanks for any suggestions

I've seen a lot of people havingf this same problem and haven't seen any solutions on these forums so far. I also have trhis exact problem.  Come on guys yall are supposed to be experts =) Someone helps us out apparently a bunch of ppl have this problem and noone can find a fix. BTW I've tried the nomodeset options and they haven't worked for me.  Any help much appreciated!

---

### Post by Daddyo-613 on 2010-06-09
Frank1e is right. I think 10.04 wasn't really ready for release. It's much to buggy. When you have an update that doesn't update and causes your GRUB to be unable to mount the partition that has your kernel on it, there has to be a problem with whomever approved this version for release.

I suspect that the slavish adherence to the 6 month release cycle has resulted in 10.04 being released on an unsuspecting public before its basic functionality was reasonably tested. I don't expect it to be perfect but I do expect it to load without causing a kernel panic and messing up my machine. If they're going to release a version that they know isn't ready, at least give us a warning.

As I understand it the purpose of the 6 month cycle is in part, to instill public confidence in the distribution and thereby attract more users to Linux. Well that's not going to work, if the operating system they rush out the door can't even load properly.

I don't mean to sound unduly harsh, but the way I see it, someone dropped the ball on this one.

---

### Post by jbaksh on 2010-07-08
It seems i have found a quick way to bypass this and get to the installation. I came across this same problem trying to install this on my Toshiba laptop with Windows 7 Home Premium installed.

I thought it was either 1 of 2 things. maybe even both - either windows 7 or the AMD processor in my laptop. Well to be honest i'm still not sure because it works fine when i tried it on my desktop with Windows XP Professional and an Intel processor.

Anyways i have no programming knowledge but i do have a bit of I.T. experience so here's what you can try...it worked for me.

Firstly when the screen comes up with the keyboard and the little man in the circle, hit the ESC key. It should bring up an installation menu.

At the bottom of this screen you'll see a bunch of options that require you to use the FUNCTION keys. 

Hit the F6 key for more options and in the list, select "acpi=off" and press ENTER or SPACEBAR to mark it (a little 'X' will show up next to it)

Press ESC to get back to the menu options and select the installation option.

After this the screen should go black and you'll see the nice purple UBUNTU screen that will guide you into the installation setup.

NOTE* - If deselecting the "acpi=off" option does not work you can also try deselecting the "noapic" option in addition to the first and see how it works out.

At the end of the installation it may take a while to complete the final steps between 95% - 100% where you'll see it saying doing something with the "dpkg".

I just left it and it completed for itself. If it does get stuck for an excessively long time, you can always hard reset your system

Now here's the tricky part. After the installation i rebooted my system and selected Ubuntu from the GRUB boot menu and guess what...same bunch of weird code. So here's what you do:

At the boot menu, the first option highlighted should be Ubuntu, with Linux 2.6.32-21-generic (or something to that effect)

Press 'E' on your keyboard before anything loads.

At the next screen you'll see a bunch of code (don't worry it's short).

Look for one of the lines (should be the 7th or so) that has "quiet splash" at the end

Navigate to the end of this line and after the words "quiet splash" hit space and type "acpi=off" (without quotes)

Then press CTRL and X to continue booting into Ubuntu.

You may see a message saying Cannot reserve MIMO Region but it quickly disappears and voila...Ubuntu

There is a way to edit the GRUB boot file via terminal to add the "acpi=off" option, so here's that step as well.

After you've booted into Ubuntu, go to

Applications --> Accessories --> Terminal

As long as you're running 10.04 (which i assume you all are) you would no longer be editing the "menu.lst". You'll now need to edit the GRUB configuration

At the terminal prompt type - "gksudo gedit /boot/grub/grub.cfg" (without quotes) and it will bring up a graphical editor that says DO NOT EDIT THIS FILE at the top...ignore it just this once =)

Just scroll through and look for the same "quiet splash" entry. When you find it, do the same thing and type a space after it then add "acpi=off". Click save. Close terminal and restart your system to test it out.

Hopefully everything should be fine from there. Hope this helps everyone out. Take care...

P.S. i'm not a Linux or Ubuntu Guru so i can't answer any technical questions. I just happened to figure this out bit by bit and thought i'd help out. Cheers all =)

---

### Post by jalor@yousee.dk on 2010-09-17
I get this exact same error on my _existing_ Ubuntu 10.04 after some kernel upgrade.

I get this error ONLY with kernel 2.6.32-24-generic. Luckily, grub has an older kernel entry for 2.6.32-21-generic. When I use that I can boot and use my linux system with no problems...

---

### Post by lukolugra on 2010-11-30
i am gettin a similar issue but instead of text i see crazy purple patters on bottom and crazy blue patterns on top

---

### Post by robbie d on 2010-12-02
I tried setting both those options and still got the same error.
Ubuntu was so easy to install on my old Dell, why does the new version seem so hard on Toshiba?

---

