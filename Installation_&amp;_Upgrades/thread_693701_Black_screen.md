---
title: "Black screen"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by wireman on 2008-02-11
Ubuntu virtual virgin needs some help installing 7.10.

Downloaded, burned and run as live cd, no problem.
Decided to install to 2nd hard drive so that future changes/additions would be saved.
Installed 7.10 from CD eventually after partitioning (took some time to discover that 'no root drive specified' means call it / and not /root) all appeared ok.
Restarted and allowed it to boot to Ubuntu automatically on timer. Progress bar completes, then black screen, monitor goes to standby.
Restarted and selected 2nd option, recovery mode. This starts a scrolling screen loading various items followed by ok. Eventually it stops with a line something like the following prompt:-
root@mypc:~# _

Windows, on a separate drive starts ok when selected at start up and is unaffected so dual boot seems right.


Advice would be greatly appreciated. Any further details required will be quickly provided.

Thanks in advance.

---

### Post by renzokuken on 2008-02-11
recovery mode just boots you into a console. the line you see (as above) is the command line.

you could run 

```
sudo dpkg-reconfigure xserver-xorg
``` at this prompt to try and configure you grafix card/chip and monitor specs then try booting normally again

---

### Post by wireman on 2008-02-11
Thankyou renzokuken for your very quick response :) .
The code you provided took me into around 20 screens asking various technical questions which I have managed to bluff my way through.
On restarting all is well, user and password screens were presented just as I expected on the 1st run. I presume automatic detection of hardware failed in some way.
Forever in your debt.
Now I get to delve into the world of Ubuntu.
To quote the Californian Governer "I'll be back", no doubt.

Thanks again

---

