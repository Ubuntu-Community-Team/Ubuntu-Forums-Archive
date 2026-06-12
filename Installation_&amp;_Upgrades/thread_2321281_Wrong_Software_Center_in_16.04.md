---
title: "Wrong Software Center in 16.04"
date: 2016-04-21
forum: Installation &amp; Upgrades
---

### Post by ndstate on 2016-04-21
Hello,

I am a little confused. On the Ubuntu 16.04 beta 2 the new software center was installed. On the final version we are back to the old software center... which only opens after opening it via the terminal. What gives? Thanks


[IMG]http://i.imgur.com/WHrSR2m.png?1[/IMG]

---

### Post by Bashing-om on 2016-04-21
ndstate' Hello;

Known issue .
See the release notes.
[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)
No biggy to remove the icon that you do not want.
> 
Upgrades from previous versions can result in two Software Center icons in the launcher. One for the old Ubuntu Software Center and one for the new Ubuntu Software application. The Ubuntu Software Center icon can be removed if required.


[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by ndstate on 2016-04-21
Hi,

Thanks for your response. This is occurring on a live usb session, not an upgrade. I guess I understand why it could occur with an upgrade, but a fresh install/session doesn't make sense.

---

### Post by RobGoss on 2016-04-21
I'm running 16.04 as well but I still have the old software center icon but when I access it I do have the new software center design.....

---

### Post by ndstate on 2016-04-22
Interesting. If I click the icon nothing happens. The only way to open the software center is via the terminal.

---

### Post by keith54 on 2016-04-22
Hi everybody,

I am also having problems with the software center.

I downloaded and installed a daily build about 3 days before the release of 16.04 (64 bit) in order to avoid the queue on release day. A tactic recommended on several sites with the "promise" that the system would auto update on release day to reflect the version that was finally released.

This install gave me several problems with grub not working properly (see my earlier post) but which was fixed automatically by a Daily update.

However, the same update installed a different version of the software center called (on mouseover) Ubuntu software. This doesn't work at all: I just get a circling dot icon which goes away after about 30 seconds with nothing happening at all. The icon for the Ubuntu software is an orange shopping bag with a big white A on it.

The previous version was a white shopping bag and that seemed to work ok.

The internet has several posts about which software center made it to final release.

Could anyone please tell me which is the one that made it to final release and how to download it and install on my system.

I was unsure if I should start a new thread on this or add it to this thread. Apologies if I made the wrong choice.

Keith

---

### Post by RobGoss on 2016-04-22
> **ndstate said:**
> Interesting. If I click the icon nothing happens. The only way to open the software center is via the terminal.


Are you still swing the old Software center logo, because the new Software center logo is white

I do remember seeing on my new installation of 16.04 but know I only have the old logo but when I click on it, it's the new software center I'm  sure other users have been seeing the same thing.

I'm not sure if it's just a matter of changing the logos image or what.

---

### Post by RobGoss on 2016-04-22
> **keith54 said:**
> Hi everybody,

I am also having problems with the software center.

I downloaded and installed a daily build about 3 days before the release of 16.04 (64 bit) in order to avoid the queue on release day. A tactic recommended on several sites with the "promise" that the system would auto update on release day to reflect the version that was finally released.

This install gave me several problems with grub not working properly (see my earlier post) but which was fixed automatically by a Daily update.

However, the same update installed a different version of the software center called (on mouseover) Ubuntu software. This doesn't work at all: I just get a circling dot icon which goes away after about 30 seconds with nothing happening at all. The icon for the Ubuntu software is an orange shopping bag with a big white A on it.

The previous version was a white shopping bag and that seemed to work ok.

The internet has several posts about which software center made it to final release.

Could anyone please tell me which is the one that made it to final release and how to download it and install on my system.

I was unsure if I should start a new thread on this or add it to this thread. Apologies if I made the wrong choice.

Keith

I believe the new white logo should be the latest in this new release because it's  totally a new design but I'm not sure why we're seeing both

---

### Post by keith54 on 2016-04-22
Hi again,

I checked the "try before you install" pendrive that I made about 3 or 4 days before 16.04 release (from the current daily build) and from which I installed my system.

That does indeed have the white logo software center that is called simply "software" on mouseover.

This works fine, although a little slowly from the pendrive.

As I said before, this was replaced by an auto daily update one or two days before final release by the orange icon called Ubuntu software on mouseover and which doesn't work at all.

Don't know why they would replace a system that worked with one that didn't just a day before final release.

Anyhow, could anyone tell me what are the commands to enter into the terminal to put the white icon software center back onto my system. Preferably, leaving the orange icon Ubuntu software also on my system in case that "springs" back to life at a future date.

Thanks in advance.

Keith

---

### Post by RobGoss on 2016-04-22
I have to try and figure that out as soon as  I get back to my desktop I'm sure it's a simple fix

---

### Post by Frogs Hair on 2016-04-22
I have the new Ubuntu software application , but the icon changed from gnome to Ubuntu the last few days. I've Been running this installation since Beta one.

---

### Post by RobGoss on 2016-04-22
> **Frogs Hair said:**
> I have the new Ubuntu software application , but the icon changed from gnome to Ubuntu the last few days. I've Been running this installation since Beta one.

Yep same here is was the new icon but now it changed to the old one.

---

### Post by grahammechanical on 2016-04-22
It is called re-branding & forking the code. It is not the first time that Ubuntu developers have taken Gnome utilities and made them their own.

In 16.04 we can now install & run snap packaged apps alongside deb packaged apps. There are, as far as I can see, at present only 2 snap apps that are suitable for a desktop environment and they have to be installed through the command line. Later on in the year Ubuntu Software will be offering snap packages. To do this it maybe required modification of the code of Gnome Software. It could also be that the Gnome developers did not want the Ubuntu code to be merged into their Gnome Software code base. So, the Ubuntu developers have had to fork the code.

The fact is 16.04 has Ubuntu software not Gnome software and it uses the original Ubuntu Software Centre (USC) icon. And it may be the case that the Ubuntu Software Centre is still in the 16.04 ISO image.

It is also true that the Ubuntu Software catalogue is not yet as extensive as the Ubuntu Software Centre catalogue. So, that may be another reason for not quickly removing USC from the code base.

Regards.

---

