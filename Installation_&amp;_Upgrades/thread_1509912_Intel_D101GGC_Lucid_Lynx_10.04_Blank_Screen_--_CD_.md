---
title: "Intel D101GGC Lucid Lynx 10.04 Blank Screen -- CD Problem?"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by HiTechHiTouch on 2010-06-14
I've downloaded 10.04 desktop (twice) and server (once).  The server install will boot fine, but the desktop install goes to a blank screen (and the monitor goes to sleep) after leaving the Live CD menu (Run from CD, Install, Check Files, Boot 1st HD, etc.).

My first try at downloading the desktop CD was using BitTorrent, and appeared to go OK.  Burned the .iso image, booted, and when I got the blank screen I suspected the Intel D101GGC motherboard using the Radeon Xpress 200 chipset had problems

I tried adding boot options (F6) such as *vga=711* and *xforcevesa* and *text*.  No joy

Others seemed to have gotten a successful install so I turned may attention to the CD, suspecting it was a bad download/burn, and downloaded 10.04 desktop again from mirror.pnl.gov/releases/.  The two .iso images compared equal, so I used a different CD burner, with different media and got CDs which compare identical.  Both CDs fail.  

Then I downloaded the server CD from PNL and it ran!  

I could select the "test CD" function, which ran in a text mode and said the server CD was OK.  I started the install, and it went OK.

However, I want the desktop version, not the server.  Any ideas why desktop won't start installing and server will?

---

### Post by HiTechHiTouch on 2010-06-17
I'm somewhat surprised that no one has posted an obvious circumvention -- use the "alternate" (text mode) install CD.

Of course I didn't notice it until reading the Ubuntu Quick Ref book so kindly distributed in PDF format to forum users!

---

