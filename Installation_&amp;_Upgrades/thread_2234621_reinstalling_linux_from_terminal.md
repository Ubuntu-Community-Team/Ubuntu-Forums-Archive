---
title: "reinstalling linux from terminal?"
date: 2014-07-15
forum: Installation &amp; Upgrades
---

### Post by Jin_Long on 2014-07-15
i can't log in to my main account on ubuntu. i type in my password and the login screen goes away, and all i see it my background (which was changed to a blue screen with a mouse). to get out of it, i have to restart my computer. i can log in through ubuntu plasma though, which is what i'm using right now, where i can use the applications.

i can't reinstall from plasma though, because when i try to open the disk drive from plasma, no folders will open.
also, i can't reinstall from disk when the computer boots because my drive is encrypted.

the only thing i've found that i can do is ctrl-alt-f1 from the login screen or while logged in to another version of linux.
any guidance on how to reinstall?

---

### Post by terrykiwi83 on 2014-07-16
Can you access terminal?

Ctrl + ALT + T

---

### Post by Bucky Ball on 2014-07-16
> **terrykiwi83 said:**
> Can you access terminal?

Ctrl + ALT + T

> **Jin_Long said:**
> 
the only thing i've found that i can do is ctrl-alt-f1 from the login screen ...

? Clearly, that's the only thing the OP can do. ;)

Okay, there are details missing. You were using Ubuntu and decided to try Xubuntu desktop or you were using Xubuntu to start with, as the blue screen and mouse are an Xubuntu thing. Please describe exactly what you were doing prior to this. Update? Upgrade? Install new software?

Did you just switch on or reboot the machine and this is what happened. Unusual for it to just 'happen' without any user action prior to the error. Please give more detail about what you did prior to this and any error messages and exactly what flavour and release of Ubuntu you are using.

---

### Post by Jin_Long on 2014-07-16
Bucky Ball:

the last few things i did was:
to try to install ati-driver x.org, because i was trying to get my webcam working
install different webcam software
run bleachbit as a way of clearing the free space to try to optimize my computer

... but now i've gone and screwed things up further, because i tried to follow instructions from alternative googled sites. i tend to be impatient.
now my drive is unmounted on top of all this.


so...
i went and got an external hard drive (3tb toshiba canvio desk) and "installed" linux on that instead, because i was fed up with my laptop harddrive (it was only 150gb anyway). it went through the full linux installation, but, although i changed the boot order to USB over CD ROM over eSata, it still won't boot from my external hard drive. i'd prefer to use that anyway, since it had a ton more space. i'm at a complete loss though.


re: xubuntu
no, i didn't specifically install xubuntu. it's just that, from the main user login screen, if you click the little ubuntu logo icon next to the username, it gives you the option to login through openbox, plasma, etc. i don't know if all versions of ubuntu do this, but i'm using 64bit v14.04, which does have that option.


i've taken my hard drive out, and hopefully i can boot from my external hard drive. any idea how to configure my computer to do so? toshiba satellite l655-11t. i'm just running off the ubuntu disk right now.

---

### Post by grahammechanical on 2014-07-16
> [COLOR=#000000]i can't reinstall from plasma though, because when i try to open the disk drive from plasma, no folders will open.[/COLOR]

That is from Kubuntu. So, at some point you installed alternative desktops on to the default desktop. A default Ubuntu 14.04 will only give us the option to load a Ubuntu desktop. The options to load Open Box, Plasma, etc., only get there if we install the alternative desktops of Xubuntu and Kubuntu.

Just to clear up something from your first post. We cannot re-install from inside the operating system. We use an ISO image burned to a DVD disk or a USB memory stick to install Ubuntu or to re-install Ubuntu or its flavours.

That external hard drive might well be a based upon USB technology but the BIOS may well be seeing it as a hard drive. Try changing the boot priority of the hard drives. You may well find that external USB hard drive listed under Hard drives in the BIOS.

Regards.

---

### Post by Jin_Long on 2014-08-04
i dealt with the whole issue by getting a  new 1 tb hard drive bcuz i had 250gb, and switching to linux mint  instead. now before i install anything, i'll make sure that the software  is completely compatible with linux mint kde on a tosh satellite.  problem dealt with

> **grahammechanical said:**
> Just to clear up something from your first post. We cannot re-install from inside the operating system. We use an ISO image burned to a DVD disk or a USB memory stick to install Ubuntu or to re-install Ubuntu or its flavours.

ya i wish i had realized that sooner, instead of being an idiot. before getting the new hard drive i burned the iso, upgraded, and reinstalled, but decided to switch to mint. i'm glad i went through that all bcuz i found out about multiboot, went and got a 16gb gorilla drive (pretty tight), and made sure to back up an iso through multi to it. i figure this way, i can mount a few others to it and run them live to experiment and learn about some other versions, at least just for the hell of it. black arch caught my eye (and not just because i'm in stl, either :-p)

> **grahammechanical said:**
> 
That external hard drive might well be a based upon USB technology but the BIOS may well be seeing it as a hard drive. Try changing the boot priority of the hard drives. You may well find that external USB hard drive listed under Hard drives in the BIOS.

Regards.

wow. well when i was looking around, i didn't see any menus for alternative hard drives, which was frustrating because i figured, "common sense: it's plugged up to the usb, i'll put usb first, then try varying the order of the rest of the list since it's not working, and wth is going on?" so quite frankly, i'm not sure what you're talking about; maybe one day i'll learn. but mint as a primary is ****ing sexy, so its all good. thanks for your support, even though i didn't understand and took the easy way out

(since the thread is done, i guess i'll talk to people via pm so this waste of data can rot in the abyss)

---

