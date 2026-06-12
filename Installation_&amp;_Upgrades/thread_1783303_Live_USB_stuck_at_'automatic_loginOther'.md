---
title: "Live USB stuck at 'automatic login/Other'"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by dugeen on 2011-06-15
I'm trying out 11.04 from a live USB and the first couple of boots were fine, it even recognised my wireless network card.

Then a problem similar to this [https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/492301](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/492301) started happening but I was able to get past it with the suggestions in that bug thread.

But now I'm stuck with a situation where I get as far as a dialogue with two choices, 'Automatic login' and 'Other...'. Whichever one I choose there's a short delay and then I'm back to that dialogue. (I've tried both the 'ubuntu' account and '' with 'Other...', it doesn't make any difference).

There are no messages on any of the consoles accessible with Ctrl-Alt-1..6. #1 has the boot menu still on it and the others are blank.

---

### Post by dugeen on 2011-06-15
I seem to be able to reliably prevent this from happening by taking 'persistent' out of the boot parameters for 'Try Ubuntu without installing.' I'm going to forget about getting persistence working for the time being and see if I can boot consistently without it.

---

### Post by dugeen on 2011-06-16
For info, I think this was happening because after creating the live USB and using it a couple of times, I copied extra unrelated files onto it from Windows. Presumably these overwrote vital parts of the drive. When I made a fresh live USB it began to work reliably.

Persistence doesn't persist though, will address that separately.

---

