---
title: "Realtek 8172 Wireless network not working"
date: 2009-12-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by clivejo on 2009-12-12
I cant seem to get the driver to work under 10.04 64-bit, it seems to install ok but wont scan for networks.

lspci gives the following output :

08:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

Anyone able to get this NIC working under 10.04 64-bit?

---

### Post by MooPi on 2009-12-12
If your new to Linux, (just a guess) version 10.04 is cutting edge and will come with some bugs and trouble. Would probably be a good idea to back down to a stable version (Karmic Koala 9.10). This may or may not solve your wireless problem.

Sorry didn't notice the forum grouping ,Lucid Lynx testing

---

### Post by clivejo on 2009-12-12
I'm new to the forums but I have been testing new releases of Ubuntu for some time.  I just wanted to see if anyone else was experiencing a similar problem or it someone had a fix for it.

---

### Post by yellerKat on 2009-12-13
On my ancient test laptop the built in Intersil Prism Javelin isn't seen at all. Inserting (an equally ancient) PC Card with a Broadcom chip invited me to downlload the fwcutter utility and that **is** working.

I assume updates will be along in a bit; and this isn't yet a reportable bug?

---

### Post by ancientrustic on 2009-12-13
I have the same problem with a Toshiba Satellite 500D. I am running Karmic and have updated to karmic proposed. The ethernet now works but not wireless. I have tried various solutions posted in the forums but none of them work.

---

### Post by IcarusR on 2009-12-14
This thread @ novatech forum explains howto install driver from Realtek.
They talk about 8192Se, but from reading elsewhere this driver works for 8172 as well. 
This works on Karmic, don't know about Lucid.

Read post 1 through carefully as it also describes stuff for wired network as well. Ignore the ndiswrapper stuff, unless you have installed ndiswrapper.

There also should be a readme file in the driver tarball.

[http://forum.novatech.co.uk/showthread.php?p=197789](http://forum.novatech.co.uk/showthread.php?p=197789)

This should probably be registered as a bug on launchpad.

---

### Post by clivejo on 2009-12-14
> I have the same problem with a Toshiba Satellite 500D

Snap, I have same laptop.  

I have compiled the rtl8192se_linux_2.6.0010.1012.2009_64bit and it works fine for a while, but after about 5 mins of use the system locks up.  I have emailed Realtek, but still no word back from them.

Anyone any ideas?

---

### Post by yostral on 2009-12-19
Have you tried reading launchpad :

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all")

It seems to work with many people.

---

### Post by derekmbarnes on 2009-12-30
> **clivejo said:**
> Snap, I have same laptop.  

I have compiled the rtl8192se_linux_2.6.0010.1012.2009_64bit and it works fine for a while, but after about 5 mins of use the system locks up.  I have emailed Realtek, but still no word back from them.

Anyone any ideas?

Better make that three of us. I just got the wireless to work for Karmic half an hour ago.

That said, the 32-bit driver might work better for you than the 64-bit. Don't know for sure; it's just a suggestion.

Now of course, this is a thread for Lucid, and we're here yakking on about Karmic. So I'll just borrow the links in this thread and ship them over to a more appropriate setting. Thanks, guys!

---

### Post by dash86no on 2010-03-15
I just followed the below launchpad thread and got my realtek 8172 working with Ubuntu Lucid alpha 64 bit

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all)

To summarize:

1: Download the latest driver from Realtek's site:
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

2: Unpack the archive, cd into the folder.

3: sudo su

4: make

5: make install

6: reboot

7: Enjoy wireless

---

### Post by chicoinc on 2010-04-13
I'm running Lucid on a Toshiba satellite L500-13p. 

My problem is that Lucid Can't find my D-link router. My wifi can see my neighbours and the one across the street. But not mine. 

lspci -vv gives

14:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
Subsystem: Realtek Semiconductor Co., Ltd. Device 8151
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 19
Region 0: I/O ports at 4000 [size=256]
Region 1: Memory at f2200000 (32-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: rtl819xSE
Kernel modules: r8192se_pci


I have tried installing the card again with the driver from realteks homepage( the tip above)

And just for info my Eee 901 running ubuntu karmic works fine and finds my router just fine.

Hope you can help. And you can overlook the typos 

Michael

---

### Post by chicoinc on 2010-04-19
finally i fixed it.
After I deleted the original driver (from /lib/modules/<version>/kernel/ubuntu) and installed the new one

and thanks to #10 for explaning that 

1: Download the latest driver from Realtek's site:
[http://www.realtek.com/downloads/dow...Downloads=true](http://www.realtek.com/downloads/dow...Downloads=true) (it's the RTL8192SE one)

2: Unpack the archive, cd into the folder.

3: sudo su

4: make

5: make install

6: reboot

7: Enjoy wireless

That did it for me.

---

### Post by eshwar_andhavarapu on 2010-04-27
if you still can't see any wireless networks after installing the realtek driver listed then go to terminal and try

```
ifconfig wlan0 up
```or from the driver readme, go to the folder where the drivers are extracted:

at terminal:

```
sudo su
./wlan0down
./wlan0up
```

---

### Post by moviemaniac on 2010-04-27
Here's a quicker solution for y'all:

Just install this package and you should be fine (it's a dkms package so you don't have to reinstall it on every kernel update): [https://launchpad.net/~matt-price/+archive/mattprice/+files/rtl8192se-dkms_2.6.0015.0127.2010_all.deb](https://launchpad.net/~matt-price/+archive/mattprice/+files/rtl8192se-dkms_2.6.0015.0127.2010_all.deb)
And add this ppa here for updates: [https://launchpad.net/~matt-price/+archive/mattprice](https://launchpad.net/~matt-price/+archive/mattprice)

---

