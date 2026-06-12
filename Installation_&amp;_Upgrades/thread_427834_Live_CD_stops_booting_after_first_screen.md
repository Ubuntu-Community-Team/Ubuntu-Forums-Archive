---
title: "Live CD stops booting after first screen"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by sbweaver on 2007-04-29
I have downloaded and made a bootable CD of Xubuntu Feisty 7.04.  This Live CD has worked on another computer already, so I know the problem is not the CD burn itself.

My computer restarts with the CD in the tray.  I get the Xubuntu first menu, with the options to boot from the live CD, boot with safe graphics mode, etc.  

No matter whether I go straightforward with the standard bootup or with safe graphics, or with other options selected for "special" computers, what happens next is the screen clears to black, the cursor flashes in the top left of the screen, and along the bottom of the screen is:

Int 14: CR2 cf800000 err 00000000 EIP c020c384 CS 00000060 flags 00010007
Stack: c00f7d50 c03f129b c0371d8c 00000002 c00f7d59 000f7d50 00000000 00000000

And that's the last thing that ever happens.  All I can do is restart the computer and try again.  But the result is the same.  (Unless I remove the CD, and then I'm back to WinXP.)

I am running a Compaq Presario SR1110NX machine with 325 Intel Celeron D Processor, 256M PC2700 DDR SDRAM.

Any ideas on how to help get me up and running with the live CD (and hopefully get installed after that)?

Thanks!

Scott

---

### Post by medya on 2007-04-29
"Stack ", seems like a problem with your CPU , I think you should download the Ubuntu for you CPU !

---

### Post by sbweaver on 2007-04-29
Not so sure.  My machine is not a 64-bit, so the regular CD image should have worked.  The suggestions for using the Alternate version doesn't appear to match my situation.  Although, it could be worth a try.

Scott

---

### Post by Elkelk on 2007-05-02
I have a Presario as well and I'm getting the same exact error, so it must be the machine.  I have tried the alternate CD and unfortunately it does the same thing.

---

### Post by BenPeeler on 2007-05-03
I have a presario as well that I am trying to get Ubuntu to install on and its giving me the same lip...  If anyone could provide any insight that would be stellar.

---

### Post by BenPeeler on 2007-05-04
I GOT IT TO WORK!!!! 

Type this after the install cd boots...

linux acpi=off

the hit return

This should start the installer.

---

### Post by JLHenry on 2007-05-04
> **BenPeeler said:**
> I have a presario as well that I am trying to get Ubuntu to install on and its giving me the same lip...  If anyone could provide any insight that would be stellar.

There's got to be something going on.  My Inspiron 6000 (Celeron processor) does pretty much the same thing.  I wonder if there's something about the CPU that's causing the problem . . .I got mine in 2005 . . .

---

### Post by sbweaver on 2007-05-12
Well, after a bit more searching on the internet, it would appear that the install / live cd problem for the Compaq Presario SR1110NX machine is not unique to Ubuntu Linux (and x- / k- / edu- buntus).    I found a thread on another forum (am I allowed to post the link to it?  here it is anyway:   

[www.computing.net/linux/wwwboard/forum/27867.html](www.computing.net/linux/wwwboard/forum/27867.html)

Compaq's in general seem to be resistant to anything other than Gates-OS.  This model in particular is especially resistant to any other flavours of OS'es.

I'll try the suggestion of acpi=off... but I think I already tried almost every conceivable boot option without success.  I even tried booting with DSL Live (an older one running kernel 2.4) and got stuck after it's introductory options page.

I think I'll give topologilinux a try... it can be installed from within Windoze, as either dual-boot or co-linux.  At least there should not be any Live CD hang problems doing it that way.

Good luck anyone else who is in the same boat as me!

Scott

---

### Post by Warmaster Ancaris on 2007-06-01
I've been experiencing the same problem as sbweaver.

At the boot menu, after I tell it to Start or Install. I am greeted with a screen with a flashing cursor at the top and 2 lines of code at the bottom.  The two lines of code are:

Int 14: CR2 f8000000  err 00000000  EIP c020c384  CS  00000060  flags 00010007
Stack: C00f7d50 c03f129b c0371d8c 00000002 c00f7d59 000f7d50 00000000 00000000

Which I believe makes those lines identical to what sbweaver has encountered.  For me it also happened when using the alternative disc.

Now, based on the advice provided by BenPeeler above, I tried the "linux acpi=off" line at the F6 prompt of the boot menu.

It did indeed get me past the situation above, but I have encountered a new problem.  With the use of the line provided by BenPeeler, Ubuntu seems like it's going to load.  It comes to the Ubuntu loading screen, with the orange bar moving back and forth.  Then another screen appears with stuff such as:
"setting preliminary keymap"  Followed by "OK" at the far side, as if working down a checklist.

After these, the screen then start scrolling a long list of various numbers and code.  This is where the problem comes in.  During this process, it will either stop loading/working altogether, or the list of numbers will seemingly go on forever.  It does not always stop on the same line, but some of the lines it has stopped on have included:

[  123.147456] [<c02eeb4c>] error_code+07xc/0x90
[  124.792291] EIP: [<c011c706>] native_apic_write_atomic+0x6/0x10 SS:ESP 0068:f3d83920
[  133.380788] [<c02eeb4c>] error_code+0x7c/0x90
[  162.719812] [<c0129940>] do_exit+0750/0x800
[  162.719912] [<c0126c2b>] printk+0x1b/0x20

These are not the only numbers it has stopped on.  It has stopped on ones as low as beginning with [  108.*] but it has also continued running clear into the [  1200.*] range and shown no sings of stopping (it was at that point I simply shut my computer down).

My computer is also a Compaq Presario.  Seems they're famous for not liking Non-M$ operating systems.  Mine is a Compaq Presario SR1010V, though it's not factory default as I've added hardware to it over the years.  It has a Celeron 2.8GHz processor, 1016MB of ram, a PCI (NOT PCI-E) Radeon 9200 128MB video card, the C drive has 7GB of space free currently.

I'm hoping the above is enough information to help.  This is my first time trying out any Linux OS and I was rather looking forward to it.  Please forgive my naivety in this field.

Thank you in advance.

---

### Post by Lucideus on 2007-06-01
Same exact problem with me, and I have an HP a1230n.

I did acpi=off noacpi in the boot line, and then it took me to this screen, after having shown the Ubuntu loading bar:

[http://img520.imageshack.us/img520/6871/getattachmentaspxfb4.jpg](http://img520.imageshack.us/img520/6871/getattachmentaspxfb4.jpg)

And when I try the same thing in safe graphics mode, it gets me past the loading bar, but then my monitor turns off, shows me my monitor's specs in a red box "Hz 75, 1280x1024" and such, and it plays the Ubuntu drums in the background, but I can't see anything.

Maybe that'll help a tad in solving this?

---

### Post by mailbinoy on 2007-06-14
> **Lucideus said:**
> Same exact problem with me, and I have an HP a1230n.

I did acpi=off noacpi in the boot line, and then it took me to this screen, after having shown the Ubuntu loading bar:

[http://img520.imageshack.us/img520/6871/getattachmentaspxfb4.jpg](http://img520.imageshack.us/img520/6871/getattachmentaspxfb4.jpg)

And when I try the same thing in safe graphics mode, it gets me past the loading bar, but then my monitor turns off, shows me my monitor's specs in a red box "Hz 75, 1280x1024" and such, and it plays the Ubuntu drums in the background, but I can't see anything.

Maybe that'll help a tad in solving this?

try adding irqpoll to the kernel arguments.

---

### Post by Warmaster Ancaris on 2007-06-17
> **mailbinoy said:**
> try adding irqpoll to the kernel arguments.

At the startup menu, I hit F6 and added "linux acpi=off irqpoll", it made no noticable difference in the startup at all.

Also I was given the opportunity recently to try the exact same CD I've been trying to boot with on another computer (an emachine in this case).   It booted up instantly with no problems at all, so I am positive the CD itself is fine.  I guess my Compaq Presario SR1010V just doesn't like Linux, but I really want to get the LiveCD running on it if at all possible.

Do you have any other suggestions I might try?

---

### Post by schnauzer93 on 2007-06-26
I also have the same problem - exactly the same error message. - 

INT 14: CR2 cf800000 err 00000000 EIP c020c384 CS 00000060 flags 00010007 
Stack: c00f7d50 c03f129b c0371d8c 00000002 c00f7d59 000f7d50 00000000 00000000

---

### Post by reynal_sf on 2007-07-02
This is the same problem I'm facing :(  but... I don't get it... it does NOT work on my 2.70 GHz CPU, but it works on my other 2.0 GHz PC? I need a better explanation... any ideas?

[IMG]http://i82.photobucket.com/albums/j264/Airforce_sf/UbuntuError.jpg[/IMG]

---

### Post by reynal_sf on 2007-07-02
1.This is the PC that Ubuntu worked on... Windows XP (32bit) 2.0GHz of Processor, 256MB of RAM, Video 64MB

2.And this is the PC that Ubuntu did NOT worked on... Windows XP (32bit) 2.70GHz of Processor, 512MB of RAM, Video 256BM.

What's the problem? is it that my PC doesn't like Linux...? the 2. is my PC... and the 1. is my brother's PC.

---

### Post by reynal_sf on 2007-07-02
By the way... My PC is a "HP Pavilion a418x"  [Windows XP (32bit) 2.70GHz of Processor, 512MB of RAM, Video 256BM.]

---

### Post by mystery_inc18 on 2007-08-17
Hi frenz......i'm also facing the exact same  prob .....i'm using Compaq Presario SR1130IL desktop pc.......n i get the same  error: [[IMG]http://img01.picoodle.com/img/img01/9/8/17/t_18082007110m_dba0e6d.jpg[/IMG]](http://www.picoodle.com/view.php?img=/9/8/17/f_18082007110m_dba0e6d.jpg&srv=img01)

 i wonder how come compaq does not support linux even though i got a linux os  installed in my pc when i bought it. I had to personally remove linux n install win xp.

Can i install any other version of ubuntu which has been tried n tested (successfully) on a compaq machine ????

---

### Post by fr0stbound on 2007-08-17
i pretty much have the same problem, only i don't have the two lines at the bottom of the screen.

---

### Post by mystery_inc18 on 2007-08-17
ok guys i jus tried out the possible soln given above ......i pressed F6 on the start menu and entered  "linux acpi=off irqpoll" (without the quotes) and IT WORKED:):):)!!!!  I used the exaple folder ...but during my browsing ...the system hanged ......may be it was bcoz of my low ram (256MB) ...now i'm gonna try n install it n then see how it works ...:). I'll get back with my review 2morow

---

### Post by mystery_inc18 on 2007-08-18
i tried t install it thru the LIVE CD, but when i double clicked on "Install" ....nothing happened for about 5 mins then a blank window poped up which i presume was the installation window. After that nothing happened ......the window remained blank for 40 mins after which i rebooted :( :( .
May be its the ram prob .... i only hv 256mb of it :( 
anyways now i'm gonna try n install it w/o the LIVE CD .....any suggestions on how to do that ???

---

### Post by merlinus on 2007-08-18
Use the the Alternate Desktop install cd. It is text-based, but quite straightforward.  And it will not be prey to video card problems.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below the green Start Download text, then click the text to begin.

256MB RAM is not enough to install via the live cd.

-merlin

---

### Post by Warmaster Ancaris on 2007-08-21
To all those having trouble getting the LiveCD to boot, I would ask this:

Do you have two video cards?  Say an integrated card on the motherboard and another one you have put in yourself?

This was my problem.   IF this is the case for you, What you will want to do is at the BIOS startup, enter the setup, switch to your integrated video card, save settings, exit, and turn the computer off.  Switch your monitor cable over to the integrated card, and start the computer up with the LiveCD in the drive.   You may have to use ACPI=off.  This enabled me to get the LiveCD working and I was able to install from there.

---

### Post by reynal_sf on 2007-09-22
I'll try this! I have two video cards (Integrated, and PCI)

---

### Post by reynal_sf on 2007-09-22
I don't think it's the processor, My brother's processor is a P4 2.0GHz, mine is a Celeron R 2.70GHz. Ubuntu works perfectly fine in my brother's PC, and mine gives me the same error you guys are facing. What I did was the following: I changed processor to P4 2.0Ghz and Ubuntu gave me the same error, I have two videos cards tho' (Integrated and PCI).

---

### Post by reynal_sf on 2007-09-22
By that time, my brother had only one video card (Integrated)

---

### Post by reynal_sf on 2007-09-22
I found a solution, Right now I'm using Ubuntu. I had two video cards... I disabled the PCI one, And I stayed with the integrated one. I inserted the Ubuntu 7.04 CD, I pressed F6 and typed "linux acpi=off" it worked fine, it seems like the video cards are giving this problem.

---

### Post by Warmaster Ancaris on 2007-10-28
Good to know we seem to have narrowed down the culprit.

---

### Post by dinosaur on 2007-11-28
> **Warmaster Ancaris said:**
> To all those having trouble getting the LiveCD to boot, I would ask this:

Do you have two video cards?  Say an integrated card on the motherboard and another one you have put in yourself?

This was my problem.   IF this is the case for you, What you will want to do is at the BIOS startup, enter the setup, switch to your integrated video card, save settings, exit, and turn the computer off.  Switch your monitor cable over to the integrated card, and start the computer up with the LiveCD in the drive.   You may have to use ACPI=off.  This enabled me to get the LiveCD working and I was able to install from there.

I was having the same problem as you, but you saved me with this post. ^_^

Thanks bunches.

---

