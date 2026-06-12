---
title: "ubuntu 16.04 r9 380x"
date: 2017-06-30
forum: Installation &amp; Upgrades
---

### Post by raynskitty on 2017-06-30
Every time i install the amd pro drivers it always sends me here..(Image) i have tried installing it about 3 times and i get the same thing, forcing me to have to reinstall Ubuntu. Is there something I'm unaware of? 

[ATTACH=CONFIG]275815[/ATTACH]

---

### Post by QIII on 2017-06-30
Hello!

Please do not post such large images.  Some users have data limits or slow connections.  Use the "paper clip" icon to use the Forums' attachment functionality.

Are you running 16.04.2?  Could you please describe exactly how you are trying to install the AMDGPU-PRO driver?

---

### Post by raynskitty on 2017-06-30
Sorry for the large picture.

This is how i installed the drivers.

[https://www.youtube.com/watch?v=jUXcvZ9TAsE](https://www.youtube.com/watch?v=jUXcvZ9TAsE)

---

### Post by QIII on 2017-06-30
I'm not going to finish watching the YouTube video.  To be honest, YouTube is probably not a good source for instructions on how to do anything.  You don't know if the producer of the video knows their stuff and you have no access to them if it doesn't.  Just ask here.  There are a lot of us -- and we catch each other's mistakes.

Did you see AMD's own instructions [here]("http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx")?  That's how I install it.  Please review that and see if your YouTube video caught everything.  

You might try to use AMD's instructions for uninstalling, then try to reinstall.  We'll be here to help further if things don't work out.

---

### Post by raynskitty on 2017-07-01
Well let me give this a try.. Wish me luck!

---

### Post by 101kitty on 2017-07-01
No it did not work.. I got this error ```
 /dev/sda2: clean, 405636/7266304 files, 20547775/29056768 blocks. 
``` 

I did everything that was asking on the and site.. how do o fix this?

---

### Post by raynskitty on 2017-07-01
Well i after i took a power nap and did a little research i found out i needed to disable my Intel integrated graphics... I'm guessing i did everything right.

```
$ dpkg -l amdgpu-pro
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  amdgpu-pro     17.10-446706 amd64        Meta package to install amdgpu Pr 
```

---

