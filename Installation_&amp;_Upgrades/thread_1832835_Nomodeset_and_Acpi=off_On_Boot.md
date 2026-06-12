---
title: "Nomodeset and Acpi=off On Boot?"
date: 2011-08-25
forum: Installation &amp; Upgrades
---

### Post by MSTRZ on 2011-08-25
Hey there, is there any way to boot up Ubuntu with the nomodeset and acpi=off options both enabled? Like, boot from the hard disk (I have already installed Ubuntu 11.04) with nomodeset and acpi=off?
Thanks.

---

### Post by sanderd17 on 2011-08-25
see my signature

---

### Post by MSTRZ on 2011-08-25
> **sanderd17 said:**
> see my signature

:D :D :D Thank you so very much, this is exactly what I've been looking for! Trying it now...

---

### Post by sanderd17 on 2011-08-25
> **MSTRZ said:**
> :D :D :D Thank you so very much, this is exactly what I've been looking for! Trying it now...

You should thank P4man, he wrote it. But I'm glad it helped you.

---

### Post by MSTRZ on 2011-08-25
> **sanderd17 said:**
> You should thank P4man, he wrote it. But I'm glad it helped you.

Yep, yep yeahh!!! I'm in Ubuntu 11.04, awesome! I'll send a message to P4man straightaway, he needs to be recognised for this!!

---

### Post by MSTRZ on 2011-08-25
Oh, one more thing, it says I don't have the hardware required to run Unity...Where can I get this? Is it a physical problem, or something I can just download?

---

### Post by sanderd17 on 2011-08-25
> **MSTRZ said:**
> Oh, one more thing, it says I don't have the hardware required to run Unity...Where can I get this? Is it a physical problem, or something I can just download?

Normally this means there is a video driver missing (or that the wrong one is used).

You should probably get a notification if a better driver is available, if that is not the case, you should google the name of your graphical card, together with the keyword "Ubuntu". You'll probably arrive at a page that explains installing the driver.

---

### Post by MSTRZ on 2011-08-25
> **sanderd17 said:**
> Normally this means there is a video driver missing (or that the wrong one is used).

You should probably get a notification if a better driver is available, if that is not the case, you should google the name of your graphical card, together with the keyword "Ubuntu". You'll probably arrive at a page that explains installing the driver.

Agh, yes, but I explicitly know for sure that I could install Unity on the old Windows Vista computer before I converted it to Ubuntu...

---

### Post by sanderd17 on 2011-08-25
> **MSTRZ said:**
> Agh, yes, but I explicitly know for sure that I could install Unity on the old Windows Vista computer before I converted it to Ubuntu...

About what "Unity" are you talking? I don't think there is a way to install [Canonical's Unity]("http://unity.ubuntu.com/") in Windows.

---

### Post by MSTRZ on 2011-08-25
> **sanderd17 said:**
> About what "Unity" are you talking? I don't think there is a way to install [Canonical's Unity]("http://unity.ubuntu.com/") in Windows.

Ohhh...They have a different Unity? I'm talking about [www.unity3d.com](www.unity3d.com) 
Do you know the reqs for Canonical's Unity?

---

### Post by sanderd17 on 2011-08-25
> **MSTRZ said:**
> Ohhh...They have a different Unity? I'm talking about [www.unity3d.com...Do](www.unity3d.com...Do) you know the reqs for Canonical's Unity?

If you see "Unity" on this forum, it's always canonical's Unity (because that what you show doesn't work on Ubuntu). 

It needs compositing, so a good graphical driver. Apart from that, it's not so heavy and you'll see if it works or not :P.

But if you don't have compositing, you can always install Unity2D.

---

### Post by MSTRZ on 2011-08-25
> **sanderd17 said:**
> If you see "Unity" on this forum, it's always canonical's Unity (because that what you show doesn't work on Ubuntu). 

It needs compositing, so a good graphical driver. Apart from that, it's not so heavy and you'll see if it works or not :P.

But if you don't have compositing, you can always install Unity2D.


>.> Sorry this took me so long, I didn't realise that there were two pages...
I suppose I'll have to connect to the internet before I do anything...Can't seem to figure out how to do that...

---

### Post by sanderd17 on 2011-08-25
> **MSTRZ said:**
> >.> Sorry this took me so long, I didn't realise that there were two pages...
I suppose I'll have to connect to the internet before I do anything...Can't seem to figure out how to do that...

Yes, internet is essential. Wired network almost always works (never saw someone complaining that it didn't work), but wireless can cause problems with some hardware vendors (I've seen a lot of problems with broadcom cards), but I never had problems with Ubuntu and wireless drivers.

Normally, you should be able to configure the internet in your system settings, but if there is no wireless shown, you need to (again) google your cardname and see if you get any results. To get the name of your card, use the command

```

lspci

```

This will list all computer cards, search your network card in it.

---

### Post by MSTRZ on 2011-08-25
> **sanderd17 said:**
> Yes, internet is essential. Wired network almost always works (never saw someone complaining that it didn't work), but wireless can cause problems with some hardware vendors (I've seen a lot of problems with broadcom cards), but I never had problems with Ubuntu and wireless drivers.

Normally, you should be able to configure the internet in your system settings, but if there is no wireless shown, you need to (again) google your cardname and see if you get any results. To get the name of your card, use the command

```

lspci

```This will list all computer cards, search your network card in it.

Yeah, I did all that and it should be fine, but we have a Windows-server based static IP modem thingy that I guess requires some kind of special password, I'll have to ask our IT guy about it.

EDIT: Hang on, switching my internet cable over to the Ubuntu laptop...

---

### Post by MSTRZ on 2011-08-25
Awesome, I'm online using my cable, but I'd better get off, my Dad hates it when I switch the cables around >:)

---

