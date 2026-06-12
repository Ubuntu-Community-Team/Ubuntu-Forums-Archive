---
title: "Installing"
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by esholland on 2007-12-23
I have a two-part question. First, the more general; how do I install things using the script in the install document? Second, the case I'm working on now; specifically, how do I install the realtek info found at:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

Please keep in mind I've been using ubuntu for about 3 days now, and know very little about Terminal and how to work it. I may not even need terminal, but any instructions will need to tell me exactly what to do. If in terminal, I need to know the exact command, not just what to do. Thank you very much,

Erik S. Holland

---

### Post by logos34 on 2007-12-23
No sound?

high def audio support should already be included (alsa drivers).  Look for it like this:

lsmod | grep snd*

i believe it's called 'snd_hd_intel'

---

### Post by esholland on 2007-12-23
I've got sound, I can't seem to input any sound. I know that this realtek thing worked for my windows side, and it was the only driver I could find for xp Professional that worked with my *shame* motherboard audio. Yes, sound output works great, but I need help getting sound input, and apart from that, learning how to install thins in ubuntu that don't install themselves. Thank you for the reply.

---

### Post by oldsoundguy on 2007-12-23
Reatek ON BOARD sound is a problem even on Windows boxes.  I blew it off of one machine that it came on and got a Creative 5.1 card from eBay and have decent sound now.

That MAY NOT be your issue .. but keep it in the back of your mind.

---

### Post by zvacet on 2007-12-24
```
jxvf programtar.bz.2
```

```
cd program
```

You will find there **install** and** read me** files.Read them both and you will know what to do.Probably in **program folder**

1. ./configure
2. make
3. sudo make install

but read it anyway.

---

