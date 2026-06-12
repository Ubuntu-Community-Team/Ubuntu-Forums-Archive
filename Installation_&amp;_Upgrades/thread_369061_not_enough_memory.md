---
title: "not enough memory?"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by YigalB on 2007-02-24
I tried installing Ubunto 6.10 on P3, with 192MB memory, and it hung up during the installation.
Once I added 64MB (making it 256MB) it went well. Could it be the memory wasn't enough? if so - why didn't the installer simply alerted me when I started the process?

One more thing: during the early stages, the screen was black for long moments, with no message. This is not a good situation to be in - I suggest that there will be "something" on the screen all the time, so the user will not be thinking: "ohhh, let's restart".

Yigal

---

### Post by Herman on 2007-02-24
Hello YigalB, 
I have easily installed Ubuntu in a computer with as little as 128 Mb of RAM using the 'Alternate' Install CD. Click on my sig link to see how to use the 'Alternate' CD.

If you want to use the 'Desktop' CD, it will also work fine with 256 MB of RAM provided you make a swap area first with [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php").
Don't ask me why, but GParted LiveCD can run with hardly any RAM, I guess it's probably because doesn't have such a lovely big heavy desktop to load. 
Once you make a swap area for it, the Ubuntu 'Desktop' Live/Install CD will run without any problems. It needs the swap area to make up for the lack of RAM. You will notice a huge difference! The 'Desktop' installer will install faster than the 'Alternate' CD installer once it has a pre-made swap area, I have timed them both in low RAM computers.

Regards, Herman :)

---

### Post by YigalB on 2007-02-24
Thanks Herman!

I will try that on the next PC.

---

