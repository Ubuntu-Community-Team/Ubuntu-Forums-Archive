---
title: "Installation issues"
date: 2013-01-12
forum: Installation &amp; Upgrades
---

### Post by Ryan Marshman on 2013-01-12
Hello,

I got a static IP and unmetered uploads from my ISP as a part of a new deal and I figured I'd try and set up a server. All I really wanna do is have something to play around with so I'm trying to install Linux on an old laptop with a broken screen. It's reasonably powerful - dual core 1.4, 4gb ram with a reasonable hdd, so I figure it should be enough to have some fun with.

Now, I've tried installing several distributions from burnt isos from the relevant websites (cd integrity errors despite reburning several times and now out of blanks) I've also tried installing from a USB according to google's instructions, somehow I get a CD error there too, finally - I installed win 7 and downloaded wubi to install through there, but get this error again. 

Anyone recognise the error, or have any tips to rectify it?

[IMG]http://www.theoldergamers.com/forum/attachment.php?attachmentid=12591&stc=1&d=1358044048[/IMG]

---

### Post by 2F4U on 2013-01-13
Did you verify the checksum of the downloaded iso file?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

How did you create the liveUSB?

---

### Post by steeldriver on 2013-01-13
You don't say exactly what error - this problem maybe?

[http://askubuntu.com/questions/127398/usb-drive-install-of-ubuntu-12-04-server-fails-cant-find-components-from-cd-r](http://askubuntu.com/questions/127398/usb-drive-install-of-ubuntu-12-04-server-fails-cant-find-components-from-cd-r)

This happened to me a couple of days ago when re-imaging a 12.04 server - the instructions from 'ajay' in the link above worked for me (basically booting from the prepared USB but then actually installing direct from the original iso file)

---

