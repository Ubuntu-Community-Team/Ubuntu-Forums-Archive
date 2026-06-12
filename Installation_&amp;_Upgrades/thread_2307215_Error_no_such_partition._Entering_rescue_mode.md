---
title: "Error: no such partition. Entering rescue mode"
date: 2015-12-22
forum: Installation &amp; Upgrades
---

### Post by George_Jiang on 2015-12-22
Alright, I'm dual booting Windows 10 + 15.10. I was installing a Windows 10 update and left it there. I came back to see
```
Error: no such partition. Entering rescue mode...
```

I tried all of the solutions I got from googling, like typing in
```
ls (hd0,msdos1)/
ls (hd0,msdos1)/boot
ls (hd0,msdos2)/
ls (hd0,msdos1)/boot
``` 
etc. but none of that worked. So I booted Ubuntu from a live usb and I tried the boot repair. It didn't solve the problem, I was getting the same error upon restarting. Here is the paste log, if that is still important though: [URL="http://paste.ubuntu.com/14156248/"]http://paste.ubuntu.com/14156248/

[/URL]Here's the thing though, I launched GParted to check my hard drive, and it seems like my Ubuntu partition has turned into unallocated space, and there is also another empty partition with 2mb of unallocated space. Here is a screenshot: 
[IMG]http://i.imgur.com/bBZHiZg.png[/IMG]

So I think what happened is that grub got deleted, and now I can't boot from it. Can someone help me with this? I don't even care about my lost Ubuntu partition anymore, I just want to get my computer working...

Thank you in advance!

Edit: My idea is that I should try reinstalling Ubuntu, and see what happens. Worst case scenario I wipe my disk.

---

### Post by George_Jiang on 2015-12-23
Ok, I fixed it by reinstalling Ubuntu where it was, and it installed grub right where it belonged too. Everything works as normal now.

---

### Post by MAFoElffen on 2015-12-23
Please revisit this thread, go up to the link "Thread Tools," and mark this thread as "Solved."

---

