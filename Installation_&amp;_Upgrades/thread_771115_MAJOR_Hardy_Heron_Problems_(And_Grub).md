---
title: "MAJOR Hardy Heron Problems (And Grub)"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by Invader Amoto on 2008-04-27
Ok, first of all, let me ask you guys a question about grub and partitioning. I have 2 hard drives: one sata and one ide. On the ide, I have one ext3 partition that I planned to use for /home in however many Ubuntu os's I install. (Hardy is horribly unstable for me, so I want 7.10 also, but I'll get to that later) On the sata drive, I have a 350 MB ext3 partition for /boot, a 2 GB swap, a 80 or so GB NTFS (which i plan to install windows xp on), and an extended partition with three ext3 partitions in it (which is where i would install hardy and gutsy, and have a place for backup of important files). I think my problems come from having Hardy and Gutsy on one extended partition, although I'm not really sure how grub works with partitions. I don't feel like explaining the problems I've been having, mostly because I forget what order everything I tried happened. But I've had Error 15 and 17 in Grub. I've had Grub only show one os when I had both gutsy and hardy installed.

Now, my questions are:
Does that setup even make sense for what I'm doing?
Which hard drive should i install grub on the MBR for it to show my XP, Gutsy, and Hardy installations so i can choose easily?
If I install gutsy, then hardy, then XP, how can I update Grub to show all three?
Can someone give me a short explanation of how grub works(I thought I knew until I ran into these problems)?




Ok now for the even more annoying, but I think hardware related problems with Hardy Heron. I have an nvidia 7900 GS, and an Asus M2V-MX with onboard VIA DeltaChrome GPU. I tried installing Hardy with the nvidia enabled in bios and my monitor plugged in through it. The live cd all works perfectly (thats what i'm using right now). Then I restarted my comp after the install and it shows grub, then shows the ubuntu loading screen, then when the log on screen is supposed to show up it shows a white screen with an even whiter rectangle where i assume the textbox is where you type your username. Oh the mouse is there also. I decided to type in my username and password and although no text came up it started to log me in. Then where it's supposed to show my desktop, it showed two whitesh bars on the top and bottom of the screen and in between is a brownish rectangle. Basically what the desktop should look like except its two colors, and everything is like whitish. Also I tried clicking on the panels like where the quit button would normally be but nothing happened. Alt, Ctrl, Backspace worked and brought me back to the all white log in screen. So then I though maybe it was my Nvidia graphics card. I turned off the comp and took it out and reinstalled. This time it showed the log in screen but around my mouse there's a rectangle, that seems to erase whatever window is open and show the desktop behind it. I can log in and everything and everything works except the annoying problem of where ever the mouse goes it erases a small part of the window. And it leaves a trail of erased rectangles across the windows. And sometimes there's a trail of the mouse pointer too. It's really annoying. 
Now for another really annoying problem with Hardy that i also had with the beta: Hard Lock Ups.
There are quite a few people having similar problems where litterally nothing will work. I posted my problem and what i believe to be the problem here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996")
My name on launchpad is also Invader Amoto, in case you want to see what the problem is.

And I think those are the only problems with Hardy that I'm having.

Thanks in advance,
Invader Amoto

---

### Post by Invader Amoto on 2008-04-27
bump...nobody knows how grub works?
i'm stuck using the live cd until someone tells me how to get 7.10 working, or maybe even 8.04

---

### Post by kshtjsnghl on 2008-04-27
Hi first thing that i think is that you can always delete the partition through the gnome partition editor while running on the live cd and then install the complete thing again.
secondly, you can always edit the grub menu by - /boot/grub/menu.lst
add the name of the os you want the grub to display and its location as explained in that file.

Use - sudo gedit /boot/grub/menu.lst

---

### Post by psyburn on 2008-04-27
Fist off you need to install Windows (XP) first then Linux...

Second you'll need to have a different / (root) partition for each Linux

so roughly what I would do

20 GB Primary NTFS XP
10 GB Logical ext3 Gusty /
10 GB Logical ext3 Hardy /
 1 GB Logical swap

take the rest and make it /home ext3

To answer your Grub question (yes I'm answering it last)
The last install of Linux will keep the list of Operating Systems.

So if you take and install XP then Gutsy and finally Hardy, the list (/boot/grub/menu.lst) will be on the Hardy partition.

---

### Post by Invader Amoto on 2008-04-28
Thanks for the help. I never tried editing the grub menu.
And about installing XP first, do I really have to?
I hate installing XP, and I only plan to install it if I feel like playing The Sims 2 or some other games, haha.
Although, I assume i could just edit Grub to show XP as a choice.

I think i'm actually gonna just use the hardy live cd though. On Gutsy, i have no sound with my tv tuner card, and Hardy is horribly unstable. The only downside to the live cd is no desktop effects and if i shut down my comp i lose all the stuff i installed or save. When theres a fix to the hard lock ups I'll install hardy for sure though.

Thanks again.

---

### Post by Invader Amoto on 2008-04-28
Well I've tried another attempt to install hardy, to no avail. Same problems as before. Then i tried installing Gutsy on a second partition (grub worked as planned, thanks again guys :)) and strangely i had exactly the same problem as i did with hardy.
This leads me to believe it has to do with certain update(s), because near the end of the install, it checks for updates (i think).
So this leads me to believe that maybe disconnecting my comp from the internet while installing and not allowing it to update might solve my problem. Of course not having updates could prove even worse an idea than just using the live cd.

---

### Post by flyboy284 on 2008-04-30
You don't have to install windows first, but you do have to edit or reinstall grub after installing windows.

To Fix grub after windows:
boot the live cd
open teminal
type "sudo grub"
type "find /boot/grub/stage1"
type "root (hd?,?)" //put in the output from the location of stage 1
type "setup (hd0)" //if you want grub in the MBR
type "quit"
reboot you system and grub should work.

---

### Post by Invader Amoto on 2008-05-02
Thanks flyboy

AND I HAVE FINALLY FIXED THIS PROBLEM!
I´m very happy about it. But the stupid thing is that i just had to use the alternate cd.
I just got it working so i dont know if the hard lock ups are still here.

Im so happy.
:o:):D:p:-D:lol::grin::biggrin:

---

