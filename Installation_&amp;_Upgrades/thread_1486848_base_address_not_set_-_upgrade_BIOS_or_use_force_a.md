---
title: "base address not set - upgrade BIOS or use force_addr=0xaddr"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2010-05-18
Just before Ubuntu screen comes up, I get text message that says something about "base address not set - upgrade BIOS or use force_addr=0xaddr"

I just upgraded PC from 9.10 to 10.04 LTS

What do I do to fix?

John

---

### Post by Soul-Sing on 2010-05-18
A bios upgrade is very tricky imo. When is goes wrong it destroys and your system and your bios.

---

### Post by Bobhuber on 2010-05-18
> **cigtoxdoc said:**
> Just before Ubuntu screen comes up, I get text message that says something about "base address not set - upgrade BIOS or use force_addr=0xaddr"

I just upgraded PC from 9.10 to 10.04 LTS

What do I do to fix?

John
Does the system continue to boot into the Ubuntu Desktop?
If so don't worry about it.

---

### Post by cigtoxdoc on 2010-05-18
Thank you for your reply.  Yes system has always booted correctly, but sound is flaky.  The original error message also includes via686a.

Streaming Internet radio will run for a few minutes, the CPU load will go to 100% and sound stops.  Sound card is C-Media CMI8738.

John

---

### Post by Bobhuber on 2010-05-18
> **cigtoxdoc said:**
> Thank you for your reply.  Yes system has always booted correctly, but sound is flaky.  The original error message also includes via686a.

Streaming Internet radio will run for a few minutes, the CPU load will go to 100% and sound stops.  Sound card is C-Media CMI8738.

John
I have no idea what kind of box (or how old) you are using but it's most likely a problem with Flash or Novell Moonlight if thats what you are using for the streaming audio.I had a big problem with cpu usage and the IcedTea Java plugin until I switched to the latest JRE from there site but I'm using the 64bit version of Lucid.They (and I quote) say that the IcedTea plugin has been fixed with Lucid.

---

### Post by LenK on 2011-07-07
I am completely new to (L)ubuntu. I have a Sager laptop (Intel P3) with an ATI Rage Mobility M3 AGP 2X. I booted 10.10 and 11.04 from the live CD. In both cases I get the message "base address not set - upgrade bios or use force_addr=0xaddr". The desktop displays in pieces, with vertical overlays repeating parts of it, slightly different between the 2 versions. I am guessing that this is related to the error message? I am also guessing that "force_addr..." is a config entry, and that I cannot access it without an install? I would rather not mess with bios, unless it is the only solution. I went ahead with an install, since the laptop was pretty much useless with Windoze. I did not notice the message, but the display is the same.

Thanks in advance - Len

---

### Post by cigtoxdoc on 2011-07-07
All of above still begs the question what do I do to make force_addr=0xaddr .

Can someone provide step-by-step instructions?

Thank you,

John

---

