---
title: "Desperately Need Help Getting Wireless To Work In Kubuntu"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2009-03-29
Hello everyone,

I have a Gateway M7315u laptop and I'm using Kubuntu 64-bit (Jaunty). My wireless router is set up as WEP with a Hex key and mac address filtering. (I only use WEP because it's the only way I can get online with my Nintendo DS).

With Intrepid, I had no problems whatsoever. I could even use a live CD of either Ubuntu or Kubuntu 64 or 32-bit and it would work with no configuration or extra drivers at all. Right now I have a Windows Vista partition (my college requires it) and I'm stuck using that whenever I want to get online wirelessly. I can't stand Vista and it's really driving me nuts. I also tried disabling mac address filtering on my router.

Any help is appreciated. I filed a bug a while ago, but it hasn't been fixed yet. I even tried to install wicd but when I attempt to do that, it wants to remove a whole bunch of important packages.

Do any of you have a similar configuration as mine and have been successful?

:frown:

---

### Post by caryb on 2009-03-29
Try turning off hidden ssid in the router if enabled, That worked for me.


Cary

---

### Post by Reiger on 2009-03-30
> 
Any help is appreciated. I filed a bug a while ago, but it hasn't been fixed yet. I even tried to install wicd but when I attempt to do that, it wants to remove a whole bunch of important packages.


Those (max 3) packages are unimportant: these are just a layer on top of the important tools ifconfig, iwconfig, and wpa_supplicant. WICD replaces them with its own implementation (one which in my epxerience works better).

---

### Post by jlacroix on 2009-03-30
> **caryb said:**
> Try turning off hidden ssid in the router if enabled, That worked for me.


Cary

Sorry, I forgot to mention that it's not hidden.

> **Reiger said:**
> Those (max 3) packages are unimportant: these are just a layer on top of the important tools ifconfig, iwconfig, and wpa_supplicant. WICD replaces them with its own implementation (one which in my epxerience works better).

I thought about that, but I can't help with testing the included system if I remove it. :(

---

### Post by Vico Vicario on 2009-04-01
Right now Kubuntu network manager plasmoid has a bug and cannot accept a WEP hex key if it is input in ASCII. For example, if your key is 'hello' then it is ASCII, and you need to translate to hex 68656c6c6f. WEP hex keys written in ASCII are evil but many routers allow it and many people use them.

V.

---

### Post by jlacroix on 2009-04-01
> **Vico Vicario said:**
> Right now Kubuntu network manager plasmoid has a bug and cannot accept a WEP hex key if it is input in ASCII. For example, if your key is 'hello' then it is ASCII, and you need to translate to hex 68656c6c6f. WEP hex keys written in ASCII are evil but many routers allow it and many people use them.

V.

My key is all numbers, is that the same thing?

---

### Post by Vico Vicario on 2009-04-01
It can be numeric and still be ascii. For example 1350 should be replaced by 31333530.

V.

---

### Post by jlacroix on 2009-04-01
It looks like my router is set up with a passphrase and there is no option to use anything else other than the "default key", which I have no idea what it is.

If I disable the password altogether, and just rely on mac address filtering, is that enough?

---

### Post by Vico Vicario on 2009-04-01
You can always reset your router to delete the passphrase.

Mac address is certainly not enough. You can set any mac you want with **macchanger**. And you can sniff all clients with **Kismet** to grab some MACs. (Although having 2 clients with the same MAC brings havoc to a network.)

WEP is utterly useless by the way. Takes from 10 min (for a 40bit key) to 10 hours (for a 128 bit key) to break any WEP network using aircrack-ng.

If you care about security, then you **need** WPA2.

Good luck,

V.

---

### Post by jlacroix on 2009-04-01
> **Vico Vicario said:**
> You can always reset your router to delete the passphrase.

Mac address is certainly not enough. You can set any mac you want with **macchanger**. And you can sniff all clients with **Kismet** to grab some MACs. (Although having 2 clients with the same MAC brings havoc to a network.)

WEP is utterly useless by the way. Takes from 10 min (for a 40bit key) to 10 hours (for a 128 bit key) to break any WEP network using aircrack-ng.

If you care about security, then you **need** WPA2.

Good luck,

V.

Thank you. I do care about security, but the wife and I play Nintendo DS, which requires WEP, sadly. :(

---

