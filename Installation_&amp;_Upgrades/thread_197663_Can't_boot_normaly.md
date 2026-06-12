---
title: "Can't boot normaly"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by Avarus on 2006-06-16
First, I'm sorry if I say stupid things since I'm not familiar with some english terms, but still I want to give it a try...

I've downloaded Ubuntu 6.06 server, burned it on a cd, formated my hard disk (bye bye Win '98 ) and installed Ubuntu as it should (so far so good), then, when I reboot the computer, it's checking all hardware stuff (all [ OK ]). And then it suddenly prompts the following:

Ubuntu 6.06 LTS Server ttyl

**Server login:**
**Password:**

I filled in my username (server) and password (*******), but then I get a whole bunch of text and then this:

**server@Server:~$** (have to fill something in here)

I'm only familiar with Windows, so I don't know what to do now. I've read multiple guides and forums, but it seems it shouldn't go this way, and I haven't found an answer yet. 

Can anyone help me out?

---

### Post by costoa on 2006-06-16
"Can anyone help me out?"

```
sudo apt-get install gnome-desktop
```

(BTW, please don't do this yet.)

Well, I'd say install the desktop version and use the GUI tools to help you learn how things down deep work.

There are many that would say don't install the gui and learn by breaking/fixing things. Personally, both sides have their valid points.  At this point I'd just install the gui.

Any other opinions from the crowd?

---

### Post by ajgreeny on 2006-06-16
If you only installed the server version without a gui, then you have got to exactly the right end point.  If you don't fully understand the command line, then I agree with costoa, and either apt-get install ubuntu-desktop (about a 35 -40 Mb download) or start again with the install CD and do a gui version install.

---

### Post by Avarus on 2006-06-16
How stupid of me! I thought the server version would have a normal GUI like the desktop version, so I thought this was something that shouldn't be there. After all these hours I still haven't learned enough about Ubuntu. I'll download and install the desktop version then...

---

### Post by costoa on 2006-06-16
Many "server" versions do have atleast a minimal GUI so the mistake is quite common. Since Ubuntu tries to save HD space and CPU cycles they've removed the standard GUI from the server version (IMO a good thing). I've been running dapper on an old IBM PL300* (333MHz Cel. / 256M RAM / 40G HD) as a test server flawlessly. I do like the server install.

Try the code I gave above if you have a dsl/cable line. It shows off the coolness in apt-get, otherwise get the desktop cd. Both work well.

Good Luck.

* It's a great machine, very quite and is commonly found in dumpsters. =) RetroBox sells them for like ~$20 although faster versions are finding there way to the trash bin.

---

### Post by SevenRavens on 2006-06-16
I came on this forum because I have the exact same problem. A friend made me the ubuntu boot disk. So... let me get this straight...

The disk I have tried to boot does not have desktop software on it? It is some other type of thing that does not boot up and look something along the lines of icons and a start menu on the bottom?

---

### Post by costoa on 2006-06-16
*"The disk I have tried to boot does not have desktop software on it?"*

If it's the server version then yes, it is absent of any desktop software (~250MBs worth). If you're in the same boat as Avarus and have a dsl/cable line then just apt-get the above command otherwise download "ubuntu-6.06-desktop-i386.iso" (assuming you're not on an AMD64 or PPC machine). 

It might take a while to do but it's quite painless.

---

