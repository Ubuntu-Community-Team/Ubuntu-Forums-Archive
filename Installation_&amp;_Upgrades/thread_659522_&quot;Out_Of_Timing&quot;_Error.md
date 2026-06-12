---
title: "&quot;Out Of Timing&quot; Error"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by newroad on 2008-01-05
Hi All,

I am trying to install 64 Bit 7.10 Ubuntu in additon to XP Pro (the incumbent). The motherboard has a GeForce 6150SE integrated graphics chipset, which for XP is running 1280*1024 with 32 bit colour.

During the Ubuntu install, it displays the Ubuntu waiting screen for a while, with the blip moving backwards and forwards, and then just the cursor in the top left corner for a while. After that, the screen itself just flashes

"OUT OF TIMING"

then blackness. Given the HDD activity, the install seems to continue for a while, then nothing.

I've tried installing a few times now, hitting F4 to change the Ubunto VGA settings to match those of windows (1280*1024 etc) but no luck.  I've also tried lower settings, e.g. 640*480.  Finally, I've searched this forum and others, and found someone suggesting use of the "noapic" boot switch, which I've also tried.

Any ideas?

Thanks in advance.

Newroad

---

### Post by newroad on 2008-01-06
Hi All,

Sorry if I'm breaking propriety in bumping the post, but does no-one have any ideas?

Regards,  Newroad

---

### Post by Partyboi2 on 2008-01-06
Have you tried the alternate cd to install ubuntu?
[http://releases.ubuntu.com/releases/7.10/](http://releases.ubuntu.com/releases/7.10/)

---

### Post by newroad on 2008-01-06
No, PartyBoi2,

But I will now.

Regards,  Newroad

---

### Post by newroad on 2008-01-06
Hi All,

Two things. I downloaded 64 bit "Feisty Fawn" (7.04 as I recall) and the graphics worked out of the box. Maybe something (questionable?) has been introduced in Gutsy Gibbon (7.10)?

I then had an issue with my TP-Link wireless card. It appeared to be up, but wouldn't work. I therefore have a lot to thank this gentleman for ...

[www.doctort.org/adam](www.doctort.org/adam)

His suggestion to add the following line

*pre-up iwpriv ath0 authmode 2*

to the /etc/network/interfaces file worked! I'd probably still be looking now if I hadn't come across it. Still don't know exactly what it means or does.

Regards, Newroad

---

