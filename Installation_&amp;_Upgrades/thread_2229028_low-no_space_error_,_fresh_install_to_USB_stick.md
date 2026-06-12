---
title: "low-no space error , fresh install to USB stick"
date: 2014-06-10
forum: Installation &amp; Upgrades
---

### Post by jim57 on 2014-06-10
I have successfully booted 12.04 LTS from an 8 Ghz stick for some time.  The problem started when I decided to upgrade to 14.04LTS. I am receiving low space error messages on a fresh  install on original 8 GHZ and also a 2 GHz stick.  

I have downloaded direct the ISO, and from  the torrent numerous times .  I have used both ubooten windows  578 and universal-USB installer 1,9.5.3 all with the same results.
If I specify a persist of any size, it is full when I boot .  It appears to be populated with duplicate files from dev0loop.  No persist and I still get the error. I format/full the usb stick every time I reload the ISO. 

The system is dual 2 GHZ , 3 GHZ Ram 

It Boots normally but very quickly shows low or no space. 


 Disk utility shows  on the 2GHZ stick 48 % free with a 981MB loop Dev-0
I think  that is about normal.

When I run the disk analyzer it gets fun. 

/ is  100% 4.3 GB
usr  is 2.4 GB 
var is 1.76 GB
The rest of the numbers look reasonable

Remember this is a 2 GHZ stick.

I have exhausted my very limited ubuntu  knowledge.  What have I missed or what am I doing wrong.  It almost looks like it  is loading twice or thinks it is. 

JIM

---

### Post by sudodus on 2014-06-11
Welcome to the Ubuntu Forums :-)

- Are you trying to run a persistent live system from your USB sticks, or are you trying to create an installed system on USB (installed like it would be installed into an internal drive? Or both?

 - Are you also trying to run a system without persistence, which is 'only' live?

- Is it standard Ubuntu or some other flavour (Xubuntu or Lubuntu) which are lighter?

- Do you mean Unetbootin when you write 'ubooten'?

- How did you upgrade to 14.04 LTS?

*Edit*: please read this link, and if you wish also some of the links from it

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

