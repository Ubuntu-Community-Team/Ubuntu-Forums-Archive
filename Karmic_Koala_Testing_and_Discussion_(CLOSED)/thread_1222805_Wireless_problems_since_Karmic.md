---
title: "Wireless problems since Karmic"
date: 2009-07-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by infamousrev on 2009-07-25
Since updating to Karmic my wireless is acting strange.

It has bursts of working well, and bursts of not working.

So its like working 10 seconds, then not working for 30 seconds, and then working again
lshw :
           *-network
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wmaster0
                version: 01
                serial: 00:22:43:71:51:93
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath9k ip=192.168.1.2 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn

Dmesg:

[ 5936.004068] wlan0: no probe response from AP 00:14:c1:19:ae:f0 - disassociating
[ 5937.376468] wlan0: authenticate with AP 00:14:c1:19:ae:f0
[ 5937.400230] wlan0: authenticated
[ 5937.400243] wlan0: associate with AP 00:14:c1:19:ae:f0
[ 5937.500244] wlan0: RX ReassocResp from 00:14:c1:19:ae:f0 (capab=0x401 status=0 aid=1)
[ 5937.500257] wlan0: associated
[ 5951.101113] wlan0: no probe response from AP 00:14:c1:19:ae:f0 - disassociating
[ 5952.469742] wlan0: authenticate with AP 00:14:c1:19:ae:f0
[ 5952.508261] wlan0: authenticated
[ 5952.508278] wlan0: associate with AP 00:14:c1:19:ae:f0
[ 5952.608238] wlan0: RX ReassocResp from 00:14:c1:19:ae:f0 (capab=0x401 status=0 aid=1)
[ 5952.608251] wlan0: associated
[ 5975.609119] wlan0: no probe response from AP 00:14:c1:19:ae:f0 - disassociating
[ 5976.986571] wlan0: authenticate with AP 00:14:c1:19:ae:f0
[ 5977.024231] wlan0: authenticated
[ 5977.024245] wlan0: associate with AP 00:14:c1:19:ae:f0
[ 5977.124227] wlan0: RX ReassocResp from 00:14:c1:19:ae:f0 (capab=0x401 status=0 aid=1)
[ 5977.124240] wlan0: associated
[ 5985.024144] wlan0: no probe response from AP 00:14:c1:19:ae:f0 - disassociating
[ 5986.410268] wlan0: authenticate with AP 00:14:c1:19:ae:f0
[ 5986.424200] wlan0: authenticated
[ 5986.424213] wlan0: associate with AP 00:14:c1:19:ae:f0
[ 5986.524245] wlan0: RX ReassocResp from 00:14:c1:19:ae:f0 (capab=0x401 status=0 aid=1)
[ 5986.524258] wlan0: associated




Any idea how I can debug this problem? 

I tried disabling WPA, but that had no effect.

---

### Post by taavikko on 2009-07-25
Experiencing the same issue with ath9k module, and somebody reported "internet being flaky" with intel hardware... 

Using wpa or unencrypted AP makes no difference.

---

### Post by t.alex on 2009-07-26
> **taavikko said:**
> Experiencing the same issue with ath9k module

same problem here. well it works more than 10 seconds, but now and then either it disconnects or it just waits a couple of seconds, as if the DNS resolution doesn't work, respectively a wrong server is being used at first and afterwards the correct one -which is clearly not the case (/etc/resolv.conf points only to my router)

```
#lspci -k | grep -A3 "Network controller"
03:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
	Kernel driver in use: ath9k
	Kernel modules: ath9k

```

A downgrade to 2.6.30 doesn't seem to help. Anyone else having these issues?

---

### Post by mariner09 on 2009-07-26
I found that if I removed the backports package, my Intel 4965 became very stable.

---

### Post by meeples on 2009-07-26
my wireless is disconnecting every time i start torrenting or downloading a big file.

backports you say?

---

### Post by bluesscream on 2009-07-27
same problem for me. My recent workaround: replaced network-manager by wicd, hold wicd-window open and every time I get no wlan-response I disconnect and reconnect.
Think it is something with the energy management of the wlan-drivers (here intel4965), seems to me as if it is going to sleep when idle and refuses to wake up, shows randomly behavior, in karmic alpha3 with all repo- and customized kernels. Not reproducable in jaunty and hardy.
Just now it happens again, I'll dis- and reconnect...and now I send.

---

### Post by gnomeuser on 2009-07-27
I have the same problem, I reported it [here](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405555) . Though mine took the disturbing turn of now letting me have absolutely zero wifi (wired works just fine.. but that is hardly any fun).

---

### Post by t.alex on 2009-07-28
confirmed. Thanks for the bug report!

---

### Post by infamousrev on 2009-07-28
I am not really sure about it because of the random nature of this bug.

But can anyone confirm that the problem exist after a suspend resume, but not after a reboot?

---

### Post by setherd on 2009-07-28
issues here as well. for some reason I can connect to my neighbors unsecured wifi without problems.
My own wireless just started working consistently. I'm not sure why. I've been playing with it for an hour.
very weird.

---

### Post by infamousrev on 2009-07-28
After 10 reboots my wireless has not failed me once,

While after a suspend it will malfunction.

So Im pretry sure it must be a suspend resume bug.

---

### Post by nightalon on 2009-07-28
My AR5008 has never worked properly since the days of madwifi.

Initially that was because 9.04 Jaunty was using the 2.6.28 kernel, which has a version of ath9k that is documented as having bugs on the ath9k website.  2.6.30 or later should do the trick, again, according to same said website.

However, THIS THREAD IS FOR KARMIC KOALA 9.10 ALPHA.  Specifically, Alpha 3.  Today I ran the LiveCD and performance was no better.  That was under 2.6.31-3 generic as a kernel.  (amd64 LiveCD, by the way)

Performance of ath9k these days is atrocious!  I love my Atheros cards since they work wonderfully under Windows and MacOS.  I thought since this new driver was open source, it would have great performance. ABSOLUTELY NOT.

By the way, I am updating using a 3G card since I don't have access to my router at the moment.  (someone is sleeping)  So annoying.

---

### Post by kervel on 2009-07-29
> **infamousrev said:**
> After 10 reboots my wireless has not failed me once,

While after a suspend it will malfunction.

So Im pretry sure it must be a suspend resume bug.

seeing the same on an eeepc 1000he (also ath9k). i found that after suspend/resume wifi works flakey

reloading the module after doing suspend/resume seems to be a workaround that works here: rmmod ath9k; modprobe ath9k (as root)

---

### Post by bluesscream on 2009-07-29
Yesterday I took the notebook with me to the office and had no wlan-issues at all. At home - same as before, no resume from some kind of suspend. What was the reason? In office router runs with WPA 1/2 encryption, at home with old WEP, because some weeks ago I had changed this on my home router to give visitors for some days an internet access who had a non-WPA-compliant old wlan-usb-stick, changed this on my machines too and forgot it. So now I switched my home network back to WPA 1/2 and everything works fine without any more wlan issues. So it may be a good idea to review your wlan encryption.
Will developers let less secure WEP die?

---

### Post by excogitation on 2009-08-18
Can you check if
```
sudo service apparmor stop
``` ([diskussed here]("http://ubuntuforums.org/showthread.php?t=1231130&highlight=ath9k")
makes a difference?

I have an AR928X card that sort of works sometimes - but after running that command - it's as it should be (maybe not).

---

### Post by martijntje on 2009-08-18
I have the same problem on my eeepc, while my inspiron 1501 is absolutely fine. Problems are as described: heavy downloads cause the network to hang. Sometimes network-manager even retries to associate with the network (which then often fails).

A workaround for the problem is stopping and starting (restarting doesn't work) network-manager at a moment that internet actually *does* work.

Doing this at a moment that internet does *not* work will cause network-manager to not find any networks at all.

This workaround works until you reboot or suspend.

---

### Post by mukul_s on 2009-08-28
works perfectly fine for me. Using:
Karmic Koala Alpha 4
ath9k
AR928x chipset

---

### Post by nickmcg on 2009-08-28
rt2870 - can't see my wireless network, yet I can see my neighbour's with kernel 2.6.31-8 and 2.6.31-7, yet 2.6.28-15 works fine.

Any ideas?

---

### Post by excogitation on 2009-08-28
> **nickmcg said:**
> rt2870 - can't see my wireless network, yet I can see my neighbour's with kernel 2.6.31-8 and 2.6.31-7, yet 2.6.28-15 works fine.

Any ideas?

I also had troubles with rt2870 (MSI Wind U100) - but with Karmic it does work - so check if there's a backport available or wait for Karmic.

Also [try this thread]("http://ubuntuforums.org/showthread.php?t=960642&highlight=rt2870").

---

### Post by nickmcg on 2009-08-28
It's been working fine with jaunty, it's broken with karmic - the oldest kernel works, but the newer one doesn't.

I don't think it's necessarily the driver as my neighbour's network seems to be visible, but mine isn't. If I manually enter  the details for my network, it won't connect either.

Nick

---

### Post by xc3RnbFO8P on 2009-08-28
> **nickmcg said:**
> rt2870 - can't see my wireless network, yet I can see my neighbour's with kernel 2.6.31-8 and 2.6.31-7, yet 2.6.28-15 works fine.

Any ideas?
Installing the backports solved it for me.

---

### Post by NCLI on 2009-08-28
It seems that people re split on whether to remove or install backports, maybe we should do a poll xD

---

### Post by taavikko on 2009-08-28
> **nickmcg said:**
> It's been working fine with jaunty, it's broken with karmic - the oldest kernel works, but the newer one doesn't.

I don't think it's necessarily the driver as my neighbour's network seems to be visible, but mine isn't. If I manually enter  the details for my network, it won't connect either.

Nick

NM has it's difficulties in connecting to hidden SSID's.
Change the option off in modem's settings and test again.

---

### Post by nickmcg on 2009-08-28
My SSID isn't hidden, the newer kernel just doesn't see my wireless network

I already have backports enabled, what do I need to do to install the backport driver?

TIA

Nick

---

### Post by Matt Behrens on 2009-08-28
> **kervel said:**
> seeing the same on an eeepc 1000he (also ath9k). i found that after suspend/resume wifi works flakey

reloading the module after doing suspend/resume seems to be a workaround that works here: rmmod ath9k; modprobe ath9k (as root)

On my HEB, suspend/resume can tickle that problem.  But sometimes it comes up spontaneously.  Other times, S/R doesn't kick it off.  Sometimes rmmod/modprobe works... other times it doesn't, no matter how many times I try.

The only reliable way to get it all goin' again is ndiswrapper, which is my default mode of operation now, though I've filed appropriate bugs and keep trying new kernels when they show up.

---

### Post by nickmcg on 2009-08-29
It looks like the problem I have with the latest kernels is the network driver rt2800usb, rt2x00usb and rt2x00lib are loaded instead of rt2870sta

---

### Post by biasquez on 2009-08-29
wifi detected but it doesn't work on Ubuntu karmic

[ 13.756879] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[ 13.756881] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[ 13.756930] iwlagn 0000:07:00.0: enabling device (0000 -> 0002)
[ 13.756938] iwlagn 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 13.756949] iwlagn 0000:07:00.0: setting latency timer to 64
[ 13.756964] iwlagn 0000:07:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x565CBE3F
[ 13.909555] iwlagn 0000:07:00.0: Failed, HW not ready
[ 13.909569] iwlagn 0000:07:00.0: PCI INT A disabled

---

### Post by moore.bryan on 2009-10-18
I'm having this same problem now, after a recent fresh install of Karmic. Eventually, I *seemed* to get things working with straight /etc/networks/interfaces & /etc/wpa_supplicant.conf changes.

**Still**, my connection seems to "lag" at times. Is there any movement on this by any of *you*?

---

### Post by josephmc on 2009-10-26
I'm also having disconnect problems on my Dell Studio XPS 13. I find that strange since dell will let you order one preloaded with ubuntu!

I just installed karmic today and it keeps disconnecting and reconnecting every 1-2 minutes. It's unacceptable. This also happened in Jaunty (I even tried wicd and I think I still got flaking problems...nevertheless I want native support with a fresh install!). I miss playing with Linux but I don't have the hours I use to. I need network to just work.

I personally think it might be a WPA problem. I've had these kids of issues before. I want to get this fixed so please let me know if there is any kind of information I can give.

lspci
```
Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
```
using the ath9k module....

---

### Post by mukul_s on 2009-10-27
> **josephmc said:**
> I'm also having disconnect problems on my Dell Studio XPS 13. I find that strange since dell will let you order one preloaded with ubuntu!

I just installed karmic today and it keeps disconnecting and reconnecting every 1-2 minutes. It's unacceptable. This also happened in Jaunty (I even tried wicd and I think I still got flaking problems...nevertheless I want native support with a fresh install!). I miss playing with Linux but I don't have the hours I use to. I need network to just work.

I personally think it might be a WPA problem. I've had these kids of issues before. I want to get this fixed so please let me know if there is any kind of information I can give.

lspci
```
Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
```using the ath9k module....

Hi Joseph,

I am having the same wireless PCI card (AR928X) and running Karmic. I do see the signal strength issues (almost 50% less signal compared to what I get in Windows) but don't have the disconnect issue as mentioned by you. Can you check how much is the signal strength using some old OS or Kernel. May be you are too far away from the wireless router/AP.

---

### Post by dunbrokin on 2009-10-27
I am having the same problem with my Dell Latitude E4300 ...I changed to wicd and that problem still exists...but it is easier to connect and disconnect with wich than with nm.....either way, it is driving me CRAZY also!!

---

### Post by moore.bryan on 2009-10-27
I'm 99% certain this problem isn't with networking, as in the connection, but with dns resolution; however, I'm not sure how to resolve that or even where to begin to look... could someone point me in the right direction?

---

### Post by dunbrokin on 2009-10-27
I have the problem with wireless and with wired.....wired is worse. I have tried all combinations of static/no static IP and with dns....all to no avail.....this is so frustrating....I hope it is fixed tomorrow.

The other problems I have are the screen resolution - when I set it to 1280 x 1024, the top and bottom panels get lost...this was not the case under Jaunty. Also, Sun Virtualbox non-free does not work properly, there is a kernel driver error.

For me, I would have to say that Karmic is a big disappointment compared to Jaunty.

---

