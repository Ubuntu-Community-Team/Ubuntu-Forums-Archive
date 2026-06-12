---
title: "Install Problem: Can't access tty; job control turned off"
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by ncwalker on 2007-08-03
Help!  i hope someone can help with my problem.

Installed Fiesty Server to a P3.  :)  Seems good, so I want to create a workstation.  Here are the specs: 

Compaq Presario 5000 (Model 5BW137)
Chipset Intel i810e (Celeron 664.5 MHz)
256 MB RAM

When I boot with the Desktop install disk the words

Loading please wait ...

appear for a second (and change font for a split second)

Then the splash screen appears for 10 seconds or so and then it says

bin/sh: can't access tty; job control turned off
(initramfs)

It says this if I try to install, if I try to install in safe mode, or if I try to check the CD (I have checked it on another machine; O.K.)

If I try to boot with the splash screen out of the way text flies by but then I see: 

FDC 0 is a post 1991 82077

end request: I/O error, dev fd(), sector 0
end request: I/O error, dev fd(), sector 0
end request: I/O error, dev fd(), sector 0
end request: I/O error, dev fd(), sector 0 

(18 times)

and then 

bin/sh: can't access tty; job control turned off
(initramfs)

Did the memory test: no errors
Tried two different 20 Gig HD no change

This machine was running windows XP (very slowly) before I tried this.

I h ave searched the forums and found a few posts with this problem but nothing that would help.  Any suggestions about what I can try?  Many thanks!!

BTW: I confess I was desperate and tried to install SUSE 10.2 .  YaST runs into trouble and a text screen shows up saying, "Your computer doesn't fulfill all the requirments for a graphical installation.  There is less than 96 MB of memory or the X server could not be started"  Does this explain anything?

Noel Walker
Ubuntu Noob (but I like it so far)

---

### Post by dimeotane on 2007-08-03
I'm encountering a similar problem installing Feisty on a compaq deskpro EN.  I managed to get MEPIS on it alright.
I'm pretty sure I've got over 256mb on the system so it shouldn't be a memory problem. 
The floppy disk light comes on prior to the error coming up.

Booting with option two "safe graphics mode" and entering this boot option "all_generic_ide"  (press F6).  Got me the furthest... to a failed X server.... but once I set up the xorg.conf to the correct video device pci address it works!  I now have a brand new Feisty install on the compaq deskpro en... 

Here's what else seemed to 'help': I can bypass this error using the 3rd option "Install with driver update CD " option and pressing enter at both options. The install CD works for a bit and the progress bar shows 100%, and the system hangs on  a black screen.  I tried F6 to enter "noapic nolapic" as boot options, but to no avail. 

one thread says to try this... it got me a bit further in the install before freezing on a black screen:

[I][I]At the LiveCD initial boot screen:
o Select F6 for more options
o Add the following option to the beginning of the options list:
break=top
o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

You will now boot into the LiveCD normally.[/I]



Another comment that's been made:

*the error message in the subject line can occur for MANY different specific reasons. What all of these reasons seem to have in common is that the new 2.6.20-15 kernel used by Fiesty chokes when it encounters hardware or combinations of hardware that its boot-up routines aren't coded to handle properly. When it chokes, it almost always spits out that error message at the end. *

---

### Post by ncwalker on 2007-08-04
I got it!

Took another look through forums and found a post

**Feisty LiveCD /bin/sh: can't access tty; job control turned off - Weird Workaround**

by klytu that suggested leaving a floppy in the drive during installation.  It worked. I am up and running and posting this from the machine that wasn't working!  

Thanks everyone!  Cheers

---

### Post by Soebam on 2007-09-03
My friend has this problem, and doesn't have a floppy drive on his laptop. What to do!

---

### Post by Leptailurus on 2007-09-05
> **ncwalker said:**
> I got it!

Took another look through forums and found a post

**Feisty LiveCD /bin/sh: can't access tty; job control turned off - Weird Workaround**

by klytu that suggested leaving a floppy in the drive during installation.  It worked. I am up and running and posting this from the machine that wasn't working!  

Thanks everyone!  Cheers

[SIZE="4"] Thankyou[/SIZE]  ncwalker (and klytu) :grin:

After two days of trying to install Ubuntu, this Linux newbie was ready to give up,  ](*,)  then I found your post... 
                            [SIZE="4"]It works![/SIZE]    
                                                                        [COLOR="Magenta"][SIZE="5"] Hooray![/SIZE][/COLOR]	\\:D/

---

### Post by wrtrdood on 2007-09-18
> **Soebam said:**
> My friend has this problem, and doesn't have a floppy drive on his laptop. What to do!

Try a USB stick.  I stuck one in and it worked perfectly!  What an odd solution...\\:D/

---

### Post by Prymalfury on 2007-10-02
> **dimeotane said:**
> I'm encountering a similar problem installing Feisty on a compaq deskpro EN.  I managed to get MEPIS on it alright.
I'm pretty sure I've got over 256mb on the system so it shouldn't be a memory problem. 
The floppy disk light comes on prior to the error coming up.

Booting with option two "safe graphics mode" and entering this boot option "all_generic_ide"  (press F6).  Got me the furthest... to a failed X server.... but once I set up the xorg.conf to the correct video device pci address it works!  I now have a brand new Feisty install on the compaq deskpro en... 

Here's what else seemed to 'help': I can bypass this error using the 3rd option "Install with driver update CD " option and pressing enter at both options. The install CD works for a bit and the progress bar shows 100%, and the system hangs on  a black screen.  I tried F6 to enter "noapic nolapic" as boot options, but to no avail. 

one thread says to try this... it got me a bit further in the install before freezing on a black screen:

[I][I]At the LiveCD initial boot screen:
o Select F6 for more options
o Add the following option to the beginning of the options list:
break=top
o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

You will now boot into the LiveCD normally.[/I]



Another comment that's been made:

*the error message in the subject line can occur for MANY different specific reasons. What all of these reasons seem to have in common is that the new 2.6.20-15 kernel used by Fiesty chokes when it encounters hardware or combinations of hardware that its boot-up routines aren't coded to handle properly. When it chokes, it almost always spits out that error message at the end. *

I followed the instructions to a "T," but when I got to the modprobe piix part, that worked, but the exit did not.

Am I dense, or is this a common problem?

---

### Post by ceton on 2008-01-01
Regarding [COLOR="Red"]***/bin/sh: Can’t access tty; job control turned off***[/COLOR]

Apparently, there are a bizillion reasons that this error occurs, but in my case, it was because the Ubuntu Live CD couldn't recognize some of the hardware on the machine I was installing to.  (I was able to install it successfully on other machines--it was just one troublesome machine).

Here is what worked for me:
[LIST=1]
[*]When the bootup screen appears, [COLOR="Blue"]***press F6***[/COLOR]
[*][COLOR="blue"]**Type**[/COLOR] the following:  [COLOR="Blue"]***acpi=off irqpoll***[/COLOR]
[*][COLOR="blue"]**Press**[/COLOR] the [COLOR="blue"]***Enter***[/COLOR] key.
[*]View the Live CD and install Ubuntu.
[/LIST]

You have to make sure that this problem is resolved when Ubuntu boots, too.  To do that:

[LIST=1]
[*]Boot your computer so that GRUB is displayed.
[*][COLOR="blue"]**Press**[/COLOR] the "[COLOR="Blue"]***e***[/COLOR]" key to go into edit mode.
[*][COLOR="blue"]**Press**[/COLOR] "[COLOR="Blue"]***o***[/COLOR]" to add a new line to the script.
[*][COLOR="blue"]**Type**[/COLOR] the following:  [COLOR="Blue"]***acpi=off irqpoll***[/COLOR]
[*][COLOR="blue"]**Press**[/COLOR] the [COLOR="blue"]***Escape***[/COLOR] key.
[/LIST]

In the event that acpi=off doesn't work try replacing the entry above with one of the following:
[LIST]
[*]acpi=force irqpoll
[*]nacpitimer irqpoll
[/LIST]

You may have to revisit the second set of steps when you upgrade ubuntu.

I hope this helps.

---

