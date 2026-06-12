---
title: "Wireless Internet slow?  Wrong Broadcom Driver."
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by thegodsquirrel on 2009-10-06
Today, I noticed that I was getting really slow download speeds.  Upon calling the ISP I confirmed that their connection was intact by hardwiring to the modem.  (around 16 MBps)  

I check my router settings and all seemed fine, firmware upgrade still slow.  Then I jumped on my wife laptop sporting 9.04 and checked her speed.  16 MBPS over wireless!!!  I immediately checked the driver on my laptop and there it was the old broadcom driver running.  

So you guys may already know this but I more than double my bandwidth with this fix.  I am using the Broadcom STA wireless Driver.  I hope this helps someone.:guitar:

---

### Post by gwydionwaters on 2009-10-08
can you please tell me how you used this driver? i downloaded, complied and installed and it still doesn't work. i am on an hp dv6404ca, 64bit w/ 64 bit 9.10 installed.

---

### Post by alexmurray on 2009-10-08
Install the bcmwl-kernel-source package and that should do the trick.

---

### Post by gwydionwaters on 2009-10-08
no internet, any way to get it online and transfer via usb drive or something? i have internet on this one but not on my new hp laptop. i do have a 'working' driver, the wlan0 show's up but no networks are displayed nor connected to.

---

### Post by gwydionwaters on 2009-10-09
i should add that when i type (the command name evades me) -C network, my wireless shows up like it should and does not say disabled. and when i type the one to list available networks it just say's scan has no results beside wlan0

---

### Post by BXCracer on 2009-10-09
> **gwydionwaters said:**
> no internet, any way to get it online and transfer via usb drive or something? i have internet on this one but not on my new hp laptop. i do have a 'working' driver, the wlan0 show's up but no networks are displayed nor connected to.

bcmwl-kernel-source package is available on the ubuntu karmic cd. Just check the ubuntu cd as installable media under software sources and you are good to go, you can then simply install it from synaptic.

---

### Post by gwydionwaters on 2009-10-09
I don't have synaptic installed yet, I tried to use kpackagekit and it had one dependency so I said install it then I got an error about permissions. I did not get a chance to try it with kdesudo yet. I had to run out and I had just got off work. I will try later tonight.

---

### Post by gwydionwaters on 2009-10-09
it seems that kpackagekit is the problem, even if i use kdesudo or log in as root it still gives an error that i don't have necessary privileges

---

### Post by thegodsquirrel on 2009-10-11
> **gwydionwaters said:**
> can you please tell me how you used this driver? i downloaded, complied and installed and it still doesn't work. i am on an hp dv6404ca, 64bit w/ 64 bit 9.10 installed.

Honestly, I used the Hardware drivers function and it was able to download and install the proper driver with a reboot

---

