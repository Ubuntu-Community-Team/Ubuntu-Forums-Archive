---
title: "Anti-Linux Motherboard?!!? Say it aint so!&gt;!"
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by sp0nge on 2008-04-17
But it is. 

Some may have followed my previous posts regarding a machine I built myself about a year and a half ago now: 

Core 2 Duo 2Ghz
MSI P965-Neo mobo
2GB XDDR
GF 7600GX 512MB

And as it fired up perfectly, the live cd of dapper purring away, the install seemed to be ok, but over and over and over upon startup I would get 

```
GRUB Loading... 
Error 21
``` 

at which point the system would hang indefinitely. I searched the forums for help, and all the suggestions did nothing. I even made contact with a tech from JMicron (the maker of the controller software that is stopping the load) who pretty much told me I am out of luck! 

Well, being the well tempered optimist I am, I decided that if the IDE controller on the hard drive is the problem, I would simply by a SATA drive and circumvent it. The drive arrived yesterday and I've been working on it all day. Installed flawlessly but again, the same error. 

How can it be? I've admitted defeat. The machine will just have to suffer with windows. Luckily, all other machines in the house and business are running gutsy fabulously. Just this one machine that seems incapable of handling GRUB.

Such a sad day. ](*,)

---

### Post by dasunst3r on 2008-04-17
You may want to try using Hardy (the water's fine -- jump on in!).  Don't give up!

---

### Post by Whiffle on 2008-04-17
Have you tried upgrading the bios firmware?

---

### Post by sp0nge on 2008-04-18
I have confirmed that I have the latest firmware installed. 

I will try the upgrade option. can't hurt at this point, right?

Well the upgrade stopped immediately. I got this error:

```
W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler2_0.6-0ubuntu2.2_i386.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler-glib2_0.6-0ubuntu2.2_i386.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/poppler/poppler-utils_0.6-0ubuntu2.2_i386.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
```

---

### Post by zvacet on 2008-04-19
Read [this]("http://users.bigpond.net.au/hermanzone/p15.htm#21") and see if it helps.

---

### Post by sp0nge on 2008-04-23
Thank you for the article, it was good reading. 

I have been given the same suggestions by a tech at JMicron, the company who coded the controller for my hard drive, who basically told me I'm too stupid to realize how to install the OS- which is funny considering there are 2 other machines in my network running feisty flawlessly. 

There is only one hard drive in this machine and it has been recognized as hd0. I have re-installed GRUB time and again and even worked with SuperGRUB a little bit in hopes that would help- it didn't. 

I hope I'm not coming off in the wrong way, but my frustration is overwhelming. I have beaten myself up over this for so long that there seems to be no choice but to accept this machine being stuck in windows hell.. I'm certainly open to try anything that comes to mind though. :confused:

---

### Post by paxmark1 on 2008-04-24
Years ago I had a triple boot and I found I really liked the FreeBSD boot manager.  Of course I was comparing it to lilo, but I still liked it.  

Should be a .deb around

---

