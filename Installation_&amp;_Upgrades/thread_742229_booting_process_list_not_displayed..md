---
title: "booting process list not displayed."
date: 2008-04-01
forum: Installation &amp; Upgrades
---

### Post by t0e on 2008-04-01
As soon as i hit enter on ubuntu from grub my monitor goes black and in the cent my monitor is displaying Signal out of range set monitor to: 1024x786 60hz. it stays like this until the login screen randomly pops up after being like that for awhile. It works normally from here on.

my monitor is actually set set to 1024x786 V:60Hz H:48kHz. found by pressing monitor buttons.

and my grub menu.lst looks like this:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e72d7cc4-24b9-43c7-adasdad228acc52472b ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

thanks.

---

### Post by Herman on 2008-04-01
:) Try following the procedure outlined in this link and see if it helps you, [Temporarily Edit the GRUB Menu]("http://users.bigpond.net.au/hermanzone/p15.htm#Temporarily_Edit_the_GRUB_Menu").

Regards, Herman :)

---

### Post by deepakait2006 on 2008-04-01
i m a new user trying to switch to ubuntu..i m facing a problem installing it...it is showing
buffer input output error hda block no 0
buffer input output error hda block no 1
buffer input output error hda block no 2
and so on..
please give some suggetions ...

---

### Post by Herman on 2008-04-01
> i m a new user trying to switch to ubuntu..i m facing a problem installing it...it is showing
buffer input output error hda block no 0
buffer input output error hda block no 1
buffer input output error hda block no 2
and so on..
please give some suggetions ... Sorry, but frankly I don't know. :confused:

I don't see what your problem has in common with the original subject of this thread, so I'm afraid you are unlikely to attract the attention of anyone who might know.
I think it would be best for you to start your own thread with a title that will help the right people to find you, maybe something like 'buffer input output error hda block no 0 in install CD' or something like that.

Did you run an md5sum test on your downloaded Ubuntu .iso file to make sure it wasn't corrupt before you burnt it to your CD?
Here's a link about that, maybe that will help you, [Why integrity check your downloaded .iso?]("http://www.users.bigpond.net.au/hermanzone/p17.htm#Why_integrity_check_your_downloaded_.iso")

Regards, Herman :)

---

### Post by t0e on 2008-04-03
thanks herman but i know how to edit it temporally but dont know what to edit it to??

---

### Post by Herman on 2008-04-03
> title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=e72d7cc4-24b9-43c7-adasdad228acc52472b ro **[COLOR=Red]quiet splash[/COLOR]** vga=[COLOR=Red]**791**[/COLOR]
initrd        /boot/initrd.img-2.6.22-14-generic
quietYou could try removing the commands 'quiet' and 'splash' for now, just to see if you can at least get the scrolling text in your monitor as you computer is booting up.
If you still don't see anything, then edit 'vag=791' to 'vga=ask', and let the computer tell you what number it thinks should go there instead of '791'.
Remember what number works so you can edit your /boot/grub/menu.lst file with it later to make it permanent.
> At the end of that line, make a space and then type 'vga=[COLOR=Sienna]**ask**[/COLOR]', (without the inverted commas). 
Then press the 'Enter' key. 
Press 'b' to boot.
On the next screen, it should say,
Starting up . . . 
Press<RETURN> to see video modes available, <SPACE> to continue or wait 30 secs



Press 'Enter'.  !Don't press you space bar or you'll have to do it all again!

It should give you a choice of vga settings you can try in an effort to get some display during boot-up.
Video adapter: VESA  VGA
Mode:  COLSxROWS:
0  0F00  80x25
1  0F01  80x50
2  0F02  80x43
3  0F03  80x28
4  0F05  80x30
5  0F06  80x34
6  0F07  89x60

Enter mode number or 'scan': _In my laptop I can type in 'scan', which doesn't do anything for me, but it might fix yours. I'd say try that first.
Then, there's a choice of numbers between 1 and 6 that correspond with different capabilities of your display. 
Hopefully that will sooner or later let you to be able to see the text messages that normally run behind the boot splash screen during a regular boot-up, but show up to tell you what's wrong when there are errors. Then whatever the problem is that's holding up the booting procedure can be solved,depending on what the exact problem turn out to be.That won't fix your boot splash but it'll give you something to look at better than 'signal out of range' while your computer is booting up.

---

