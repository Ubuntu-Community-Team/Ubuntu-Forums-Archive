---
title: "Ubuntu netbook remix 10.10 Dual boot trouble"
date: 2011-02-20
forum: Installation &amp; Upgrades
---

### Post by Dright on 2011-02-20
I'm trying to install ubuntu netbook remix on my Acer AOD 255-1345.

I followed the instructions [here]("http://www.ubuntu.com/netbook/get-ubuntu/download") but after showing a bit of text at the start of the boot, all I get is a black screen with a blinking underscore on the top left.

Any ideas?

Win7 is the original OS if that helps.

-Dright

---

### Post by Dright on 2011-02-21
Could someone who knows please respond? I really want to get linux up and running.

---

### Post by wilee-nilee on 2011-02-21
So there are a couple of types of installs. There is a wubi which is from the windows environment. The other is a partitioned dual boot with a usb or cd , can you let us know. If your intention is a partitioned install have you resized the windows leaving a unallocated for Ubuntu?

---

### Post by Dright on 2011-02-21
I went with using a usb to install it. When I looked over the files though there was a file called Wubi and it had the sheild beside it typically for an installer.

What I had hoped is that I could just have followed the instructions on the site and end up with a functional dual boot, so I don't really any preferences for the way it's installed as long as I can launch either OS at boot without needing the usb afterwards.

Edit: *facepalm* I just looked up what wubi was. I'm going to try running wubi from the usb while windows is booted which I think is what I need to do. I'll edit again if it works (assuming nobody posts before I get back).

Edit Again: Okay, so now I know what I'm actually trying to do. I want to use wubi to install ubuntu beside windows. When I switch the boot order to my usb however, I get the abovementioned black screen which does nothing. Could you tell me what needs to be done to get it up and running, or do you need more information?

---

### Post by Dright on 2011-02-21
I also forgot to say that the OS version is *starter*.

---

### Post by rippsrock on 2011-02-21
There is a previously identified issue with the broadcom drivers in the Acer Aspire model you quoted.  There is another post on Ubuntuforums that covers blacklisting them, but I am still trying to find it once again.  I haven't had success yet, but several Acer Aspire users have cited good results.  Good luck, and if I find the article here, I'll try to repost.

Edit: forgot to say, may be same model or not, but exact same behavior is quoted.

---

### Post by Dright on 2011-02-21
Big thank you if you can find it =D

---

### Post by Dright on 2011-02-22
> **AtlantafalconsRule said:**
> My acer aspire one D255-1134 works perfectly out of the box of linux. The only thing that needs to be done is to install the proprietary driver for the wifi chip =).

Specs
Atom N550 1.5Ghz dual core
1GB ram
NM10
250GB harddisk

I found it =P (I think, tell me if this looks right).

---

### Post by Dright on 2011-02-22
I've seen that the drivers are in fact, not up to date. However I'm having trouble finding the new ones.

Windows says they are all good.

---

### Post by Dright on 2011-02-23
I do still need help with this, I haven't found the answer. I will try another USB soon.

I want to know, if I use the install inside function (which works fine) am I able to continue trying to install another copy of UNR beside windows 7 before I delete the first one?

---

