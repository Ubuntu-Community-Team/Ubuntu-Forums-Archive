---
title: "Upgrade to 7.04 broke scanner"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by 999alfred on 2007-11-17
I upgraded from 6.1 to 7.01 the other night and now I cannot use my Canon FB630U USB scanner, which worked fine using scanimage and xsane, with the scanbuttond running.

But, now after upgrading to 7.04, it's broke.

Here's what happens using scanimage.
# scanimage -L
device `canon630u:libusb:003:002' is a CANON Canoscan FB630U flatbed scanner

#scanimage -T
This just hangs forever unitl I CTRL-C to abort.

What broke??? I need my scanner back.

999alfred

---

### Post by torgrot on 2007-11-17
Have you installed all of the updates for 7.04.  I believe the unpatched version broke something in the USB driver for most scanners.  I thought there was a patch later that fixed it though.  I have that scanner and it works in 7.10 now and I am pretty sure it worked after one patch in 7.04.

torgrot

---

### Post by 999alfred on 2007-11-18
As far as I know all updates are in place for 7.04. And here is a real head sctacher. THE SCANNER DOES WORK!!

I tried scanimage -T a again and it hung. I just left it and about 4-5 minutes later the scanner took off and passed the test. after that I ran scanimage -T again and it worked immeaditly.  I could then go to xsane and it worked.

So why is it taking so long the first time?

Is this also tied to a problem I have with it taking up to thirty seconds between print jobs on my usb printer, a Brother 1440?

999alfred

But why is it taking so long

---

