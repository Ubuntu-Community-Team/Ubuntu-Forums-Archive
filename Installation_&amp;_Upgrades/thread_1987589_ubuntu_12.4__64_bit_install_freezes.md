---
title: "ubuntu 12.4  64 bit install freezes"
date: 2012-05-26
forum: Installation &amp; Upgrades
---

### Post by interceptorV8 on 2012-05-26
since the last version of ubuntu with the annoying side panel, i decided to devote the next 6 months to linux mint.  well i was going to give ubuntu another try. 

i downloaded the torrent of the .iso, made a disc, rebooted, tried to install and when the ubuntu screen opens, the flashing balls underneath the ubuntu logo alternate and go through the motions for a few minutes before it just freezes.  balls stop blinking... it just hangs there; frozen.

so i make another disc thinking perhaps the first was a bad disc.  again, the same problem.

i downloaded the .iso directly from the site this time rather than the torrent.   again - same problem

i then downloaded the full DVD version from the site and made a live usb drive with UNetbootin...  surprise surprise...  same problem.

so right now, ubuntu 12.4 isn't looking very promising if the damn thing won't even get past the welcome screen.  i've been a loyal follower of ubuntu since gutsy...    i'm starting to lose faith in ubuntu and shuttleworth.

---

### Post by TheFu on 2012-05-26
Do you see the boot options menu?  There's a "validate media" option above the "memory test" - no need to reburn media over and over - just run that check. If the problem happens before that point in the boot process, then it is probably a hardware, driver or BIOS issue.  I know, that doesn't really help too much.

I've heard that video drivers are an issue - try choosing a VGA install option.
Is there a way to stop the fancy graphics display during boot/install? That could help.

It might be useful to try non-optical installation media - a flash stick or a network install instead if you know the **video driver/card** is not the cause of this problem.

Sorry, I'm not much help.

---

### Post by interceptorV8 on 2012-05-26
i did the validate media option for the usb live flash drive and it passed.  i dunno.  i'll fiddle with it some more.  i also tried using my old 11.10 live disc and i had the same problem.  it freezes at the ubuntu logo.


> **TheFu said:**
> Do you see the boot options menu?  There's a "validate media" option above the "memory test" - no need to reburn media over and over - just run that check. If the problem happens before that point in the boot process, then it is probably a hardware, driver or BIOS issue.  I know, that doesn't really help too much.

I've heard that video drivers are an issue - try choosing a VGA install option.
Is there a way to stop the fancy graphics display during boot/install? That could help.

It might be useful to try non-optical installation media - a flash stick or a network install instead if you know the **video driver/card** is not the cause of this problem.

Sorry, I'm not much help.

---

### Post by TheFu on 2012-05-27
> **interceptorV8 said:**
> i did the validate media option for the usb live flash drive and it passed.  i dunno.  i'll fiddle with it some more.  i also tried using my old 11.10 live disc and i had the same problem.  it freezes at the ubuntu logo.

Sounds like a hardware failure to me.  I'd look at video and hdd controllers first.  Have you pressed the button to see the boot messages behind the graphics yet?  When we have problems, fancy graphics aren't helpful.

Sorry, I don't recall the exact button to press, but ESC seems logical. There's probably a "boot options" how-to somewhere on this site.

---

### Post by Quackers on 2012-05-27
What video card is installed? You may need a boot option like nomodeset for the system to load properly.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

