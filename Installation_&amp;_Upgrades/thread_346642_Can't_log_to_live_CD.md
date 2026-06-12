---
title: "Can't log to live CD"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by iLHuevo on 2007-01-26
Hello everyone.
I decided to install Ubuntu 6.10 so I downloaded de CD image and burn it. 
When I try to log into the desktop to install Ubuntu I get the following message: 
**I've detected a panel already running, and will now exit**
This message keeps coming again and again and I just can't get the desktop running so as to install Ubuntu.
I've already check the CD and no error was found.
If anyone could help me I would be very happy.

PS: I want to apologise for my English, it's not my native language and I have not speek or write for a wile.

EDIT: I forgot to mention that I have no experience with Linux.

---

### Post by louieb on 2007-01-26
Got to go to work. But quickly. The Live CD should boot straight to the desktop.  I have never seen or heard of your problem. Sorry not much help here.  Check the psychocats link for a good description of how the live CD install should work. or Try the alternate CD.

---

### Post by rediron on 2007-02-06
Confirmed, 6.10 boot CD is broken.  

Regular and safe boot menu options get by with no errors until X starts and then it tries to start x with automatically logging in user [ubuntu].  While the desktop is loading (splash progress indicator screen), it starts another instance of x with a gdm screen.  Error message "panel already running ..." message is displayed briefly before x is crashed and restarted.  It does this loop process about 5 times before freezing completely. 

I've been able to ctrl-alt-f1 before it displays the first "panel already running" message  and then at the console I've killed -9 xorg.   The machine then is able to live at text console.   I've tried commenting out the auto user login stuff in the /etc/.../xorg.conf file to no avail; it still tries to login ubuntu user multiple times then crashes.  After that I can't get back to the console.
 
I've checked the cd with itself, with checksum and by reburning a fresh.  It is built broken.

I've tried this on multiple machines all with the same result.

---

