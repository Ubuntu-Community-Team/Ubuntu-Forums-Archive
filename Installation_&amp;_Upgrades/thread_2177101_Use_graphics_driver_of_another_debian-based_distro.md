---
title: "Use graphics driver of another debian-based distro"
date: 2013-09-27
forum: Installation &amp; Upgrades
---

### Post by HarryWild on 2013-09-27
Hi there,

my question might be a bit too specific, but anyway - I hope there is someone out there who can help me out.

I'd like to use lubuntu on my rather old Toshiba Tecra T900 (P3@933MHz, 512MB RAM, 6GB HDD).

The installation went fine, but the graphics are badly distorted. In the upper third of the screen I can see parts of my desktop, but the rest is scrambled beyond recognition.

Since I was not sure if the graphicschip is defective I tried another Distro. I booted with an old Knoppix 6.7-Live-CD and the graphics were perfect.

Altough I would have preferred installing Lubuntu I resigned to the fact, that this was no option for this machine. At least I wanted to install the newest Version of Knoppix so I downloaded Version 7.2 .... and .... surprise ... the graphics were scrambled again.

Looks like that the only working drivers for the T9000 are the ones coming with Knoppix 6.7.

So my question is: Is there a way to extract them somehow from Knoppix 6.7 and use them with the current Version of Lubuntu? I usually work with text-only-linux-servers so I have absolutely no experience with GUI's and there configuration.

For any help - thanks in advance!

Harry

---

### Post by Mark Phelps on 2013-09-27
In general, the answer is no -- because different distro versions often use different X-server versions, and you run into version incompatibility between the X-server and the video drivers.

This is the case, for example, in trying to use an Ubuntu version newer than 12.04.1 with the AMD drivers for the HD 2x/3x/4x-series cards.

---

### Post by HarryWild on 2013-09-27
Thx for the info - I was afraid it's more complicated than it sounds ;)

I'll stick with Knoppix 6.7 then - or WinXP if I really get annoyed by Knoppix.

---

### Post by mörgæs on 2013-09-28
If that solves your problem please mark the thread so.

---

