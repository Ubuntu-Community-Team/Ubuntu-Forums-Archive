---
title: "Almost Got Edgy Right...  Still More Issues Though (USB Maybe???)"
date: 2007-02-25
forum: Installation &amp; Upgrades
---

### Post by djrobthaman on 2007-02-25
Hi,

I couldn't tell you exactly what I did right, but I finally got edgy to install on my PC after many failed tries.  So I installed all the upgrades and also installed the proprietary ati drivers and vlc.  Turned it off last night and it seemed to be fine, but now It won't boot up.  If i turn off the quiet parameter in the boot the last message I get before it stops doing anything is:

"No PS/2 controller found.  Probing ports directly"

This makes sense I suppose because I don't have a PS/2 keyboard or mouse.  I have a wireless USB keyboard/mouse combo.

Also another thing that happened was that there are now two versions of ubuntu listed on the grub loader:  ubuntu 2.6.17-10 and ubuntu 2.6.17-11.  Is that due to the upgrades?

One last thing... I don't know if there's something to this, but for some reason before I couldn't get ubuntu to load properly unless I let the timer on the grub run out so that the automatic selection of ubuntu would be made.

So, I guess my questions are:

Could there be an issue somewhere with the USB ports?  The keyboard and mouse worked just fine before.

If it is a USB problem, is there a way to force the load sequence to forget about usb, but still have the keyboard and mouse work once ubuntu is fully loaded (it would really suck if I couldn't enter username and password to get in).

If I ever get back in to my system, is it okay to just delete what looks to be the older ubuntu image (2.6.17-10) from it's detected OSs?

Thanks a million,
Douglas

---

### Post by johnc4510 on 2007-02-25
It sounds more like a kernel problem. If you can, try booting to the older kernel and see if that boots for you. At the grub menu use your up and down arrows to select the 2.6.17-10 kernel.  If it does boot, I would say it is defintely a kernel problem. I don't know if I can help you further or not, but report any findings back here.

---

### Post by djrobthaman on 2007-02-25
John,

I've tried to boot both kernels and neither does.  I haven't actually turned off the quiet parameter on the older one though.  I'll do that and see what it has to say for itself.

Also, I'm not sure if this means anything, but I went into the grub's command line and pretty much rewrote (or tried to rewrite) all the commands that I saw when I pressed 'e' on one of the kernels and after I typed in the root and kernel commands with all the parameters nothing happened (i can only assume nothing should happen until you enter the boot command).  But when I typed in the initrd command the system froze.

Does that mean anything?

(I did this more than once and each time this happened... also, if I only typed in the root and kernel commands before the boot command it showed the same log as if I just selected whichever kernel it was)

Could there be a problem there?

Douglas

---

### Post by johnc4510 on 2007-02-25
Well, I'm not sure that it was a good idea to edit GRUB. I can not help you with that, but maybe someone will help you to reinstall the proper grub by using the cd in rescue mode. Sorry I couldn't be of more help, but I'm sure someone else will.

---

### Post by djrobthaman on 2007-02-25
Sorry, I guess it sound like I was doing some edit of grub itself.  That's not what I did.  I looked at what the commands were that grub was executing when I made a selection for a kernel (just instead of pressing enter when you have it selected press 'e') and then went to grub command line (press 'c' when you're in the main menu) and typed in those comands.  I have not actually done anything to grub itself.

Also, tried loading up the old kernel without the quiet parameter and all that gets displayed is "Starting up..." so that doesn't fare well for that.

Anyway, thanks for all your help,
Douglas

---

### Post by djrobthaman on 2007-02-25
I don't know what happened.  I turned on the PC and let it automatically default to the latest ubuntu kernel and left it doing it's thing for about 45 mins.  Then restarted and ubuntu started up like there was nothing wrong in the first place.  Although I think this is awesome, I'm a little concerned that the next time I restart I may not be able to get back on.

Eh.  Whatever.  Works now.  Who thinks long term anyway. :)

---

