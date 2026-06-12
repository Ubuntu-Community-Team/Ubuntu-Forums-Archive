---
title: "Low Res Upgrades Beyond 9.04 Simply Fail"
date: 2010-11-08
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2010-11-08
The was another time consuming and difficult matter to work out.  I typically like to work in 1024x768 or 800x600 resolutions for the most part, but you cannot be in such a mode if you plan to do an upgrade.  What happens if you do is that the mouse pointer disappears and so do the Examples and Install icons on the Desktop.  I can't find any way to get them back, which means starting the whole install process over again by forcing a power off and a power on sequence.

Several attempts may either show a frozen mouse pointer on the screen, or you might get lucky and find that you can move it about on the screen, but if you use the left button to click on an icon on the top task manager bar, such as System, the mouse pointer freezes and nothing else happens.  You are back to using the forced power off and power on sequence and starting over.

This particular snag may be specific to certain PCs, such as the Gateway GM5661E that I am trying to get set up.  It has a rather odd BIOS and boot sequence method involved, and how much these factor in is not really understood at this point.

There is a possibility that an upgrade at high resolution might work, but what happens if I then attempt to go back to low resolution?  I don't know yet, but I guess I am going to have to try and see.   Note that these failures have been experienced with both the I386 and the AMD64 downloads and installs/upgrades.

I've been told several times that this is where I should post a question and let others answer in their turn.  I can't quite get a handle on that approach, because I don't drop what I am doing and head here until I exhaust what I see as my range of prospects.

---

### Post by oldefoxx on 2010-11-12
I'm still struggling with the Gateway GM5661E Desktop, and this is going far beyond the rediculous. I've tried every Live install from 9.04 to 10.10, and the only one that consistently works is 9.04.  Of course by the time you apply the 323 patches, you get a warning that 9.04 is no longer supported, with the suggested action of just going ahead with a 9.10 upgrade, which never takes on this machine.

All I could do to find a way around this was to install 9.04 after making sure each of six partitions had been cleaned by reformattion, then using the LiveCD mode after the install and copying the entire contents of the partition installed to, which would be a1, b1, or c1, these being the partition designations after dropping the /dev/sd-- actual drive identifiers, to the other two leading partitions.  Thus, if I manually installed to c1, I would mount the other two partitions,
these being a1 and b1, and use a sudo cp -r / /media/a1/, then when that was done, use sudo cp -r / /media/b1/ so that all three first partitions in this three drive system appeared to be the same as to
their content.  Then finally I could get the grub autoselect process to work, but don't ask me which actual menu.lst or boot process was actually followed.

Updates from 9.04 to 9.10 seem to work, except neither the keyboard or the mouse work after the update.  If I directly try to install 9.10 instead of 9.04, that doesn't work either.  Same for 10.04 and
10.10, again either on top of what I still have there, or after refomatting these three partitions, and the results are even quirkier.
The last effort showed where none could not be mounted on /dev, and a whole bunch of errors about card 1 to card 6 not working with WinTV.

Whatever is going on behind the scenes is driving me and this PC off the deep end.  Ubuntu was fine up until you started on 9.xx, where things to tough, and now you are pushing 10.10 and it is a madhouse.  I managed to get my notebook up to 9.10 after a lot of failed starts,
and thought that would hold, and I guess it is going to have to, because I'm afraid that if I try anything higher on it, it will become just as unuseable as this desktop unit is now.  The rest of my partitions are also blank reformats, and that included a2, b2, and c2,
and other than that I have b3 for a linux swap.

Why couldn't you people just leave good enough alone?  Efforts to download 10.10 and use it as an install just take forever to run, and I never see a finished desktop, just the purplish background, maybe a mouse (which does not move), and a black band at top and botton where the taskbars should appear.

How can I even begin recommending Ubuntu as a possible solution to PC worries if you are going to keep crapping it up like this?  I'm really ready to take off in a new direction if anyone would care to point out a distro that is all that Ubuntu was under everything up to 9.04, when some dark evil shadow became ingrained in the product.

---

### Post by oldefoxx on 2010-11-13
.  Since my previous post, I began again with a single objective:  Try to repeat the limited success I had with 9.04, but use 10.04 LTS 64-bit in its stead.  That meant recleaning the first partition on each of 3 hard drives first, then attempting a manual install on c1.  Lo and behold, on reboot it came up, after I manually told the boot loader which of the three drives to work from.


That was the good news.  The bad news was any attempt to go under System/Preferences/Monitors and change from the highest resolution to a lower one just causes the screen to go black.  You can't even use the keyboard to get into tty mode or reboot.  It's back to power off and power on in order to get anything to happen.

Not the worse of it either.  Staying with the overly high resolution, I did get the appearance to change so that I had white backgrounds instead of black ones. but try to pick any other task or to click on Applications or Places, and the mouse pointer freezes and the keyboard fails to do anything.

If I were to grade Ubuntu right now, I would rate it about like this:

8.04  A+
8.10  A
9.04  C-
9.10  D-
10.04 F
10.10 F-

I don't care about added features and the like.  If you cannot reliably update to it or install it from scratch, then all those fine add-ons and enhancements are absolutely meaningless.  Any time an OS falls into a state of disrepair where the mouse and keyboard are ignored or disabled to the point that yoy have no choice but to kill power in a last desparate act to get control back, then that OX
has been rendered into total trash.

And that is what I am looking at here.  A stack of carefully burned CDs and a few DVDs that represent pure trash.  Words can hardly
express my displeasure at seeing all my time and effort being wasted in this manner.  What happened to you people?  Some rift-raft slip in a side door and suddenly grab control of the mike?  This is the equivalent to me of having a total jerk of a jackass in charge of this country and running it straight into the ground, leaving the biggest crater of all time in his wake for survivors to gawk at in disbelief.  That is if there are going to be any survivors.

---

### Post by oldefoxx on 2010-11-14
I slept on this matter, and woke with the idea that it deserved at least one more close look.  I must be missing something.

So I did fresh installs beginning with c1, then a1, then b1, and repeated the install on c1 a final time.  Each time I pointed the boot loader at the same partition I was installing to.  With that done, i tried a boot from scratch.  Now this was all done using a LiveCD of Ubuntu 10.04 LTS.  I did not boot any of them, just went through the install process each time.

Then I tried a power up boot, and 10,04 fired up fine.  I tried changing the resolution, no problem.   I selected a new background, no problem.  Looking good so far.  Then I called up the Update Manager, and as soon as it came up, I was hung again.  No mouse response, and no keyboard either.

Now as many of you know, lots of new PCs no longer have dedicated PS/2 ports for the mouse and keyboard. You now have to have a Keyboard and mouse that connect through a USB cable.  I have one PC that still has the old style PS/2 plug-in for the keyboard, but you have to go USB for the mouse.

The Gateway GM5661E has the old style connections, but as with other PCs you could opt to just go with USB connections.  Which I do, on occasion.  In fact, having them both connected, if something seems to hang up, I can try the other.

And that is where I found something really wierd taking place. I use a small KVM switch so that I can switch between two PCs using just one keyboard, monitor, and mouse.  It has been working great, but then there is the question of power for its internal logic.  You connect either of two PCs and power it up, you get the power you need, meaning it must be tapped off the mouse or keyboard line from
the powered up PC.

But since 9.10, it seems you can't count on those ports being active, and when you go through the KVM, you can lose the use of the mouse, keyboard, or monitor, maybe all three.  I can look at the bottom of an optical mouse and it no longer displays a red light.  I take it out and plug it back in, and I get the mouse back, at least as far as displaying the red light is concerned.  The keyboard normally shows no lights. but I can hit the caplock, scrolllock, or numlock key and cause a tottle, and if I don't see a light, I know the keyboard is no longer active.  If it is a USB connected keyboard, I can unplug it, wait a few seconds, and see the lights flash for a brief moment, meaning that the keyboard is drawing power, but I can't use a key to cause a change in state, meaning no more lights and the keyboard has been forced to an inactive state.  The monitor should show the output for either of the PCs, but if it doesn't, then all I can see is the power on light, which means it is getting nothing in the form of a signal from the video card.

Now this is all software related.  Know how I know? Because I have had no problems in this area before 9.10, and can still set up and run 9.04 with no such problems, and can even run the LiveCD versions of later releases well enough to get them to install, but then have loads of problems when I try to reboot into the installed version.

I guess the simplist question would be What the Heck Have You People done to screw up port access so bad?  I am trying to work without the KVM switch in the loop any more, but that does not make the problems just go away.  No, I just get a bit further before I am locked out of my own PC.

---

### Post by oldefoxx on 2010-11-17
After a couple more days of effort, and checking back here a few times for amy timely replies. I threw the towel in.  Not matter what I've tried. anything beyond 9.04 was going to fail to work on that PC.  So I just ignored warnings that support for 9.04 was discontinued and reformented my partitions with the supplied Partition Editor, and partition editor amd proceed to install 9.04 in this order: c1, b1, s1, b1, c1.  Each install was done using the manual partition mode, and no reformats were done as that would have changed the UUID assigned that partition.  The second installs for B1 and c1 were just to ensure that /boot/grub/menu/lst was complete in all instances. bicking up on the later installs as well.

I then went around and dod the 323 updates fpr each, then went around again and installed Oracle's VirtualBox for each. Then I took the replaced 250 GB internal drive that I had replaced, hooked it up externally to the notebook,changeed its ownership and permissions to I could write to it as well, copied over all folders and files I wanted accessible on the desktop, attached the drive to the desktop, and copied those to its internal hard drive.  I am almost through configuring the desktop niw, and very little effort was needed with 9.04.  What went wrong with 9.10 and later will have to be someone elses problem to address and resolve.  I hate that they are dropping support for 9.04 because it is the best thing that Ubuntu has going for it right now.  But even with the lack of support, it is worth getting and continuing to use until something that is actually better comes along.  Nothing offered right now is better in basic and assured functionality, and if you don't have that, you have nothing.

---

