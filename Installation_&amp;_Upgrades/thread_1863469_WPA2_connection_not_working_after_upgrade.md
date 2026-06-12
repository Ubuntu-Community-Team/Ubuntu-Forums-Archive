---
title: "WPA2 connection not working after upgrade"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by tmfs on 2011-10-17
Hi, 

I upgraded from 11.04 to 11.10 on my HP dm4t laptop. After a few reboots (it was hanging at a blank screen with a blinking cursor or on the splash screen on a lot of boots), everything seems to be working fine except the wireless

I cannot connect to my WPA2 Personal network. It asks me for the password and even after I enter it, it tries to connect for a while (say 2-3 minutes) before asking for my password again. This is also happening if I boot from an ubuntu 11.10 liveUSB.

Any help would be appreciated.

I've an Intel Centrino Wireless Card.

---

### Post by tmfs on 2011-10-17
To add more info, syslog reads -

NetworkManager[943]: <warn> Couldn't disconnect supplicant interface: This interface is not connected
NetworkManager[943]: <info> (wlaon0): supplicant interface state: scanning -> inactive
NetworkManager[943]: <warn> No agents were available for this request.
NetworkManager[943]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
NetworkManager[943]: <warn> Activation (wlan0) failed for access point (47)
NetworkManager[943]: <info> Marking connection '47 5' invalid.
NetworkManager[943]: <warn> Activation (wlan0) failed.
NetworkManager[943]: <info> device state change: failed -> disconnected (reason 'none') [120 30 0]

---

### Post by garvinrick4 on 2011-10-17
So it is not due to upgrade because 11.10 on USB drive is not working also.
Is it the 1000 card or something else?
```
lspci -nn | grep 0280
```

---

### Post by tmfs on 2011-10-17
Yes, it's

Intel Corporation Centrino Wireless-N 1000 [8086:0084]

---

### Post by tmfs on 2011-10-18
I should also mention that I checked this thread out 

[http://ubuntuforums.org/showthread.php?t=1844396](http://ubuntuforums.org/showthread.php?t=1844396)

but the problem there "iwlagn 0000:0d:00.0: fail to flush all tx fifo queues"

does not apply in my case.

---

### Post by garvinrick4 on 2011-10-18
My Comcast Broadband went down for a while, l
lost Television, Phone and internet. 
 > "iwlagn 0000:0d:00.0: fail to flush all tx fifo queues"That is good you do not have this have not seen a fix yet besides running the 2.6.38 kernel with 11.10.

what does
```
locate iwlagn
```give you modules with iwlagn.ko and headers with config/iwlagn.h

---

### Post by tmfs on 2011-10-18
Yes, it gives me both. Specifically

In fact it shows 4 .ko modules and 3 .h files. Three of the .ko and two of the .h files are from the 2.6.38 kernel and the other .ko and .h from the 3.0.0-12 kernel

---

### Post by garvinrick4 on 2011-10-18
Have you tried to boot the 2.6.38 kernel and see if iwlagn works.

---

### Post by tmfs on 2011-10-18
Tried it but it's still the same.

Also tried recovery mode but that didn't help either.

---

### Post by tmfs on 2011-10-19
I should also mention that I've the 64 bit version

---

### Post by tmfs on 2011-10-19
bump

---

### Post by tmfs on 2011-10-19
Are there any other suggestions on what might help?

---

### Post by tmfs on 2011-10-19
Another update: I tried reinstalling. While the reinstall didn't help, interestingly, it did manage to connect to the wireless during the upgrade (even though it wasn't working when I was just using the LiveUSB and isn't working now).

---

### Post by kafkaian on 2011-10-20
I'm having the same problem with my Realtek Semiconductor 192SE Wireless LAN Controller [10ec:8192]. WEP seems fine though.

I'm also suffering from an oscillating brightness control. Just keeps automatically going bright and dark without any influence from me!!!!!!!!!!!!

---

### Post by kafkaian on 2011-10-20
> **kafkaian said:**
> I'm having the same problem with my Realtek Semiconductor 192SE Wireless LAN Controller [10ec:8192]. WEP seems fine though.

I'm also suffering from an oscillating brightness control. Just keeps automatically going bright and dark without any influence from me!!!!!!!!!!!!Solved the first issue by using updated Samsung wireless drivers. Now just the oscillating brightness

---

### Post by tmfs on 2011-10-20
Ok, I tried dmesg again after the reinstall and now it's telling me

"wlan 0: link is not ready"

Does anyone know why that is happening?

---

### Post by tmfs on 2011-10-28
Bump

---

