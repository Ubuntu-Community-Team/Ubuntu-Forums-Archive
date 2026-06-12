---
title: "Question On Supported Video Cards"
date: 2009-02-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2009-02-18
Hello everyone, I have two machines I'll be loading Jaunty onto. One has an Nvidia 9800GT, and the other has an Intel Graphics Accelerator. Does anyone know if those two cards will work in Jaunty? I know that X is pretty broken right now so I wanted to ask first. Thanks!

---

### Post by ronacc on 2009-02-18
Nvidia is doing fine right now , I can't comment on Intel I havent got one .

---

### Post by Chainz on 2009-02-18
Yes, this Nvidia should work fine.

When it comes to Intel integrated, see Phoronix site, thay have tested 9.04 Alpha 4 on their netbook with integrated Intel card onboard:

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_904_speed&num=1]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_904_speed&num=1")

---

### Post by OliW on 2009-02-18
Another thumbs up for nvidia.

---

### Post by jlacroix on 2009-02-18
Thanks guys, it looks like Nvidia will work fine. I'm still unsure of Intel though. I'd be interested to hear from someone that has a recent Intel based machine and could say how well it's working or not.

---

### Post by Tich666 on 2009-02-18
I have an Intel 4500MHD and it works.
Performance is somewhat acceptable using UXA, utterly crap using EXA though.

Basically it's a tradeoff between performance and stability right now, I'm unable to run compiz without my desktop locking up within 10 seconds. KWin seems to work fine, but it's been a week or longer since I've tried it.

For now I prefer gnome without compositing though, as I connect my 22" monitor to the laptop and intel can't handle a virtual desktop bigger than 2048x2048 with 3d acceleration enabled and working.
Compositing will work even if you set the virtual size bigger, but once you move windows out of the 2048 pixel range there's artifacts remaining.

---

