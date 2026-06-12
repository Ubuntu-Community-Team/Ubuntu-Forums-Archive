---
title: "Uninstalling Ubuntu from a Duel Boot question"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by talvon on 2006-06-07
The last time I dabbled in duel booting, I ended up having to reformat my whole HD. This was because I had installed SuSe, and it didn't detect my USB modem, so I couldn't access the internet.

So I went back into windows, and deleted all the partitions except the windows one, but when I rebooted the computer the GRUB loader loaded up and said there was no partitions, and in BIOS I tried many things to load other HD partitions etc, and in the end I just had to format the whole thing to get it back.

Now, my question is, can I safely remove Ubuntu from a duel boot machine without this problem again, ie it will boot into windows straight away, as I currently lack the funds for a 2nd HD :)

TIA

---

### Post by RRS on 2006-06-07
[These directions]("http://www.users.bigpond.net.au/hermanzone/p18.htm") should help you.

Basically you want to remove grub first because after you remove Ubuntu grub will hang while looking for it when it's no longer there.

---

### Post by talvon on 2006-06-07
Ok, I've added that site to favourites.

Thanks a lot :)

---

