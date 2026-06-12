---
title: "Blank Screen on Login"
date: 2010-03-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by victor9098 on 2010-03-15
For the last few days I have been getting the following after turning on my laptop (running UNE 10.04 A3)

> ubuntu lucid (development branch) *laptop name* tty1
*laptop name* login:

Pressing 'alt + F7' skips this and brings me to the normal GUI login screen. I have tried reinstalling GDM and X but no change.

Any thoughts or what I could try?

Thanks

---

### Post by Half-Left on 2010-03-15
I think this might be due to Plymouth dumping people do the wrong TTY or it might even be the login manager.

This used to happen with the E17 login manager, Entrance.

---

### Post by Arla on 2010-03-15
Yeah, I get this too, although it's better than before when it would just leave me sitting at a flashing cursor (fortunately pressing enter at the flashing cursor seemed to take you into the graphical login screen just fine)

---

### Post by victor9098 on 2010-03-15
OK, good to know it is not just me, so fingers crossed there is a fix in the works. Will try to find a bug report on this

---

### Post by AlanR8 on 2010-03-15
Same issue here on my brand spanking new Compaq Mini! Only found out about the Alt+F7 workaround today and it works well. Prior to that I was going into recovery mode and trying from there. A bit hit and miss but the Alt+F7 works.

Quite prepared to accept this during Alpha and maybe Beta but TOTALLY unacceptable if the situation persists into the full release. 

Can't think of why that would happen particularly as 10.04 is to be a Long Term Release.

---

### Post by Cam! on 2010-03-16
Since I updated and turned off my PC, I can't get to the Login screen. I get a terminal-ish Login screen that asks for my Login + Password. I enter them, and it registers, yet I still can't boot into Ubuntu. What should I do?

(Yeah, I have a dirty monitor. I had to use one from the basement. Don't judge!:p)
[IMG]http://img691.imageshack.us/img691/799/camputer.png[/IMG]

---

### Post by kuvanito on 2010-03-16
yes guys
this black screen with the tty1 login is frustrating for me,i know the alt-F7 trick.
i am new to ubuntu(6 to 8 months) and i am showing my friends running windows7 the new OS i got and they all ask me.oh,is that how it boots up? is frustrating,they laugh at me,oh well...

---

### Post by coffeecat on 2010-03-16
> **Half-Left said:**
> I think this might be due to Plymouth dumping people do the wrong TTY or it might even be the login manager.

It seems that Plymouth is behaving differently according to which graphics driver you're using. I'm getting this on my laptop with Intel graphics - fully update a few minutes ago. But not on my desktop using the current proprietary nvidia driver updated a couple of hours ago.

Last time I booted up my ATI graphics (open source driver) laptop it went straight to the gdm login, but I'll update and try again later.

Those being dumped into tty1: what graphics/drivers are you using?

---

### Post by coffeecat on 2010-03-16
> **kuvanito said:**
> they all ask me.oh,is that how it boots up? is frustrating,they laugh at me,oh well...

It's an [SIZE=4][COLOR=Red]ALPHA[/COLOR][/SIZE]. If you want to show off an operating system, don't demonstrate a development version.

---

### Post by teh603 on 2010-03-16
You got yourself a bug report. Try hitting alt-f7 and seeing if that takes you to the gnome desktop.

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/538214](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/538214)

Looks like we may have a partial fix in Beta 1.

---

### Post by grumpymole on 2010-03-16
I get the same.  As teh603 says, alt+F7 should get you back to graphical login.

Cheers

---

### Post by victor9098 on 2010-03-16
I am not always dumped to the tty1 screen. First time I booted today it went straight to GDM. Turned it on another time and I get the tty1 screen. I did not get any updates or make any changed between the two starts. Restart is hit and miss too.

I am using the UNE on a netbook with an intel atom cpu n270 @ 1.60ghz. Graphics card is an Intel mobile 954GME integrated graphics controller (rev 03).

I would suggest not showing off an Alpha release to friends though, apport flashing up every now and then just does not look good. Hell, I would wait for at least a week after the release date before 'showing off' :D

---

### Post by kuvanito on 2010-03-16
ahahhhh
i fixed my black login screen tty1
thank you coffeecat for mentioning drivers,i guess i am not a newb anymore,hehehehe
well,i am using a new video card H545H512 Radeon HD 5450 Video Card - 512MB DDR2, PCI-Express 2.0, DVI, HDMI, VGA
i just went to sypnatic package manager and updated few things,reboot and no more black screens,the gnome desktop is up in one shot,wait until my friends see this now,hehehehehe:p:p:p

---

### Post by coffeecat on 2010-03-16
Well - this is interesting. Last time I used my ATI graphics laptop a day or so ago I updated but didn't reboot. Booted up a few minutes ago and was dumped into tty1. Updated and rebooted - still dumped into tty1. Unlike victor9098's experience, my machines seem to be consistent with the few reboots I've done. But an interesting pattern:

Intel graphics + open source driver - displays the purple Plymouth screen but drops me into tty1

ATI graphics + open source driver - as Intel.

Nvidia graphics + proprietary driver - fails to display Plymouth (shows text messages) but successfully takes me to gdm.

Anyway, it's a changing field. They seem to have fixed the hokey-cokey login screen. No doubt this will be fixed by or shortly after Beta.

In the meantime a fyi for any inexperienced user coming across this thread. The key combination to get to the login screen is Ctrl-Alt-F7, not Alt-F7.

---

### Post by cariboo on 2010-03-16
Merged two threads on the same subject, in the future if you encounter a bug please search this sub-forum before creating a new thread, we've had so many duplicate threads, it's hard keeping track of them all.

---

### Post by victor9098 on 2010-03-16
Mine just did it again on restart.

Yes I get the plymouth 'ubuntu' screen then that goes to the tty1 screen. But 'alt+f7' then takes me to the normal GUI login where I login as normal.

It is not a huge issue, just more frustrating. Only a new issue too, so hopefully they know what they did and how to fix. Beta in 2 days, so hopefully a fix then.

---

### Post by coffeecat on 2010-03-16
> **coffeecat said:**
> The key combination to get to the login screen is Ctrl-Alt-F7, not Alt-F7.

Apologies - half-wrong. :oops:

> **victor9098 said:**
> But 'alt+f7' then takes me to the normal GUI login where I login as normal.

You are right.

If you're in the GUI you have to use ctrl-alt-Fx to go from one tty to another, but I forgot that in a non-GUI tty you can omit the ctrl key.

:-#

---

### Post by mikitz on 2010-04-03
As it turns out I had forgotten to run "sudo apt dist-upgrade"

---

