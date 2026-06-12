---
title: "Ctrl-Alt-Fx tells &quot;Loading, please wait...&quot;"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by croatcatala on 2007-04-30
I just upgraded to Feisty Fawn, everything seems to work fine, but when I try to open a session with Ctrl-Alt-F1, I get a  screen with the booting messages and a  "Loading, please wait..." text. 

The other F2, F3, etc are just blank, I suppose that's because there waiting for something. The amazing thing is that the X-Session (Ctrl-Alt-F7) works fine, with all the consoles and everything.

I'm not very expert, so I'd be grateful for some hints about where to find the problem. Thanks a lot.

Just as a hint (I don't know if useful), this is the /boot/grub/menu.lst entry (in fact, the one that appears just before the "Loading please wait" msg):

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3e3ce70c-cb8e-4ce8-94fc-b916b1197337 ro quiet splash noapic nolapic
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault

I don't know even where to lookn for an answer, I've tried almost every keyword on Google.

---

### Post by bulldog on 2007-04-30
When do you hit the ctrl-alt-f1?

If Grub appears on your screen, you can select the proper kernel.
Hit enter and wait till ubuntu is booted up.
Log in and when done,you can use the ctrl-alt-f1 to open a console session.

Or maybe I understand you totally wrong here.:)

---

### Post by croatcatala on 2007-04-30
Hi, bulldog, thanks for your reply.

The problem is while Gnome is loaded and running. Of course, I am logged in. Right now, as an example, I am working absolutely fine, I can even open consoles (inside Gnome), but when opening a text console (Ctrl-Alt-F1), that screen appears.

Excuse, but my English is not worth of much comprehension :-)

---

### Post by croatcatala on 2007-04-30
This is the message of booting:
[B]
Booting 'Ubuntu, kernel 2.6.20-15-generic'
root		(hd0,1)
  Filesystem type is ext2fs, partition type 0x83
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3e3ce70c-cb8e-4ce8-94fc-b916b1197337 ro quiet splash noapic nolapic
 [Linux-bzImage, setup=0x1c00, size=0x1a82cc]
initrd		/boot/initrd.img-2.6.20-15-generic
 [Linux-initrd@0x1f64d000, 0x7d2e30 bytes]
savedefault
Loading, please wait...[/B]

It seems that it's hung doing something, but I don't have the slightest idea of how to know what it should be.

---

### Post by bulldog on 2007-04-30
Just tested it,I can access all the tty's in a split second,as you should.

Your English isn't that bad.

Why it's slow for you,can't tell.

You mean the boot is delayed for some reason?
Well let it be and see if things get better,I boot the computer and walk  away,haven't the faintest idea how long it takes.
When I come back with my cup of coffee,I can login and that's what matters.

---

### Post by croatcatala on 2007-04-30
> **bulldog said:**
> 
Which kernel version do you use?


I think I answered to that in the previous message, just while you were writing.

---

### Post by croatcatala on 2007-04-30
Well, I think I've got something...

I took off the "splash" option, and now I can see what happens: just after the f*** "waiting" message, there are these messages:
**init:/etc/event.d/tty1:16:Unknown stanza**
and so on until "tty6"

So probably this is the problem (I hope so). Does anybody know the solution?

Thanks a lot.

EDIT:
Maybe the solution is this... I'll try and reboot
[http://ubuntuforums.org/showthread.php?t=424078](http://ubuntuforums.org/showthread.php?t=424078)

---

### Post by croatcatala on 2007-04-30
PROBLEM SOLVED!!!

It was that ([http://ubuntuforums.org/showthread.php?t=424078 )](http://ubuntuforums.org/showthread.php?t=424078 )). 
Just changing the /etc/event.d/tty* last lines has solved it. I'm going to bed.

---

