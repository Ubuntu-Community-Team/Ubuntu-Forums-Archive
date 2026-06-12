---
title: "Wine integration"
date: 2009-09-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by LKjell on 2009-09-24
I heard there was going to be some wine integration but have not seen any yet..

---

### Post by amano on 2009-09-24
And you will not see any. There was feature freeze already. THus noc more features will fall from the sky anymore.

---

### Post by autocrosser on 2009-09-24
Personally--I hope that never comes to pass--at least by default. I do not want Windows in any form in my Linux install--that's what I have a token XP install for--the few times a year I "have to" use it (like updating my Nokia phone)--other than that I do not need & do not use Windows....Linux works very well for almost all my needs.

---

### Post by NCLI on 2009-09-24
Almost true. Either they are aiming for a freeze exception, or it has been deferred to 10.04.

---

### Post by bobince on 2009-09-25
What actually needs to be ‘integrated’? I installed wine-1.2 on Jaunty and EXEs just worked; I was very pleasantly surprised at how simple it was.

---

### Post by LKjell on 2009-09-25
> **bobince said:**
> What actually needs to be ‘integrated’? I installed wine-1.2 on Jaunty and EXEs just worked; I was very pleasantly surprised at how simple it was.
The integration will let you uinstall stuff from software store and let you install wine when you first encounter an .exe file. Like the codec finder

---

### Post by Robin Nixon on 2009-09-25
> **autocrosser said:**
> Personally--I hope that never comes to pass--at least by default. I do not want Windows in any form in my Linux install--that's what I have a token XP install for--the few times a year I "have to" use it (like updating my Nokia phone)--other than that I do not need & do not use Windows....Linux works very well for almost all my needs.

Sometimes you just have no choice such as with Microsoft word files that OpenOffice.org munges, and it does that a lot, BTW. Having Wine alongside Ubuntu saves you rebooting to a Windows partition.

---

### Post by coldReactive on 2009-09-25
> **bobince said:**
> What actually needs to be ‘integrated’? I installed wine-1.2 on Jaunty and EXEs just worked; I was very pleasantly surprised at how simple it was.

A lot needs to be integrated according to this: [https://wiki.ubuntu.com/karmic-wine-integration](https://wiki.ubuntu.com/karmic-wine-integration)

Also, it's already been approved and started: [https://blueprints.launchpad.net/ubuntu/+spec/desktop-karmic-wine-integration](https://blueprints.launchpad.net/ubuntu/+spec/desktop-karmic-wine-integration)

---

### Post by cgroza on 2009-09-25
Wine opens almost my exe...i dont have Windows on my PC...The only thing that remained from wondows days is my fat32 partion...

---

### Post by Gina on 2009-09-25
Last time I tried Wine it wouldn't work with USB devices - I haven't checked if that has changed.

---

### Post by stoffe on 2009-09-25
> **Gina said:**
> Last time I tried Wine it wouldn't work with USB devices - I haven't checked if that has changed.
That's very, very close to 0% data in that post, right there. :)

---

### Post by Gina on 2009-09-25
What I was implying was that I wondered if Wine now supported USB or not - anyone know?

---

### Post by coldReactive on 2009-09-25
> **Gina said:**
> What I was implying was that I wondered if Wine now supported USB or not - anyone know?

You can tell wine to support USB, as per this screenshot I took. Where disk is a USB Flash Drive.

---

### Post by hikaricore on 2009-09-25
I think people expect a little bit more out of WINE than it can current do.
In some people's opinions syncing with itunes and unlocking crappy usb drives = usb support.

WINE is not responsible for vendor locking or crap implementation of features such as encryption.

---

### Post by coldReactive on 2009-09-25
> **hikaricore said:**
> I think people expect a little bit more out of WINE than it can current do.
In some people's opinions syncing with itunes and unlocking crappy usb drives = usb support.

WINE is not responsible for vendor locking or crap implementation of features such as encryption.

This is why ReactOS is being made, mainly.

---

### Post by Gina on 2009-09-25
In fact the USB device I wish to connect is not a flash drive but a weather station that uses Windows software (no equivalent Linux software seems to exist).  VirtualBox works but needs Windows installed into it.  It would be nice if it worked in wine.

---

### Post by forcecore on 2009-09-25
i hope they never include wine out of box NEVER, it is Ubuntu not Windows.

---

### Post by coldReactive on 2009-09-25
> **Gina said:**
> In fact the USB device I wish to connect is not a flash drive but a weather station that uses Windows software (no equivalent Linux software seems to exist).  VirtualBox works but needs Windows installed into it.  It would be nice if it worked in wine.

That's not what wine is for, wine is for running Windows Software, not hardware. ReactOS picks up this slack.

---

### Post by LKjell on 2009-09-26
> **forcecore said:**
> i hope they never include wine out of box NEVER, it is Ubuntu not Windows.
Maybe you should read this then

[http://wiki.winehq.org/ImportanceOfWine]("http://wiki.winehq.org/ImportanceOfWine")

---

### Post by hikaricore on 2009-09-26
> **Gina said:**
> In fact the USB device I wish to connect is not a flash drive but a weather station that uses Windows software (no equivalent Linux software seems to exist).  VirtualBox works but needs Windows installed into it.  It would be nice if it worked in wine.

Exactly the kind of thinking I was talking about.
This type of software/hardware is meant to lock you into a specific os.
WINE in this case is 100% not at fault.

---

### Post by ddrichardson on 2009-09-26
> **LKjell said:**
> Maybe you should read this then

[http://wiki.winehq.org/ImportanceOfWine](http://wiki.winehq.org/ImportanceOfWine)
I've seen this page linked to a lot and don't completely agree with it.

The first argument about the importance of supply diversification overlooks that while Wine facilitates the move from Windows and increased operating system diversity it in fact promotes stagnation and dependance on proprietry applications such as Office - which is still a Microsoft cash cow.

I agree with the statement on homogenous populations but by considering only the operating system we again neglect increasing the homogenous population of application users and they too are susceptible to vulnerabilities - for example Internet Explorer cross platform would still be susceptible to MITB attacks - something where the security of the under lying OS makes no difference.

While it is true that a Windows replacement should run Windows applications, you must consider that some wish to brea the dependancy alltogether for ideological reasons and despite your agreeing or otherwise we should permit the easy addition or removal of such interdependance.

Don't get me wrong, I appreciate Wine and use it myself (Office 2003). However we as a community need to accept that others might want a choice and for the sake of looking at something critically can further reduce our established user base.

---

### Post by bluesscream on 2009-10-01
For my office I depend on a specialized software which is  running and supported only in MSWindows. The server can be installed in linux, but clients/terminals and hardware need windows xp+.
As I'm not in the position to command the holders of rights to port this program to linux, I'd love it running in a full functional wine environment. If this would work, I'd  say windows good bye in my business too and use the free money for supporting the developement of a better genuine linux version of this program.

---

