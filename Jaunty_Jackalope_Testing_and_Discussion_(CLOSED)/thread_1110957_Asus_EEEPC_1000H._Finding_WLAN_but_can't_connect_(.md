---
title: "Asus EEEPC 1000H. Finding WLAN but can't connect (9.04 Beta UNR)"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Oputres on 2009-03-30
Well this was odd.

I have an Asus EEEPC 1000H and yesterday I downloaded and installed the 9.04 Beta Ubuntu Netbook Remix (UNR).

It finds the wireless hardware and I can view the different WLANs in my neighbourhood but I can't connect to my WPA/PSK secured WLAN. I'm allways getting back to the pop-up where I add my password.

I can connect to unprotected WLANs but it takes ages. *Edit: It wasn't Jaunty's fault that it took ages to connect, tried with another computer and it was the same - bad reception instead I guess*

I've downloaded the latest upgrades through my wired connection so everything is up to date.

Anyone else having the same problem or know what the problem is - other than that I'm not "Dipped in Ubuntu" yet but playing with a Beta-release?

---

### Post by dbu on 2009-03-30
Yes; I have same issue with EEEpc 901.  WEP or open wireless is fine, but no WPA-for-you -:(

Identical hw running Intrepid+array_eeepc kernels worked well; broken in Jaunty.

---

### Post by bapoumba on 2009-03-30
Moved to Jaunty.

---

### Post by MysticGold04 on 2009-03-30
I had an Eee 1000HA, and I was running Intepid + the Eee Kernel with no issues connecting to WPA type networks.. but I sold it so I can't confirm the issue with Jaunty. Maybe try installing the Eee kernel on Jaunty?

---

### Post by Oputres on 2009-03-30
> **MysticGold04 said:**
> I had an Eee 1000HA, and I was running Intepid + the Eee Kernel with no issues connecting to WPA type networks.. but I sold it so I can't confirm the issue with Jaunty. Maybe try installing the Eee kernel on Jaunty?

Hmm, does anyone know if there is an updated eee kernel that I can use with 9.04 perhaps?

---

### Post by MysticGold04 on 2009-03-30
Here is the Ubuntu section of Array.org.  You could try the 8.10 instructions to see if they work, or contact the developer and see if he thinks it might work, or if he plans on coming out with an updated package. 

```

http://array.org/ubuntu/

```

---

### Post by sgosnell on 2009-03-30
My 900 works fine with both the 9.04 Alpha 6 and with the 2.6.29 kernel.  I haven't yet bothered to install the actual beta, because the alpha has the same things as far as I can tell, with only the kernel being changed (maybe) and I'm using the 2.6.29 kernel anyway.  It works out of the box for me.

---

### Post by gaussian on 2009-03-30
See [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/339891](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/339891)

There is a workaround mentioned there in the comments (downloading and forcing array.org dkms). I don't have Jaunty installed yet, so cannot test this yet.

---

### Post by dirtylobster on 2009-03-31
I can connect to unsecure and WEP networks but not WPA.

Eee 1000H (RaLink RT2860) on Jaunty i386 Beta.

---

### Post by Oputres on 2009-04-01
Okay, so it seems that I'm not the only one with this problem and it is worth to mention again - it's only the WPA-secured wlans that one can't connect to.

How often are kernels updated? Do you think this problem is solved until the release of final 9.04?

---

### Post by nyarnon on 2009-04-01
No problem at all here with current Jaunty alfa completely up to date. Anyway havent had a network problem since I run Jaunty. And just to elaborate I'm connecting on wep,wpa and wpa2 as I use it on different routers.

---

### Post by Oputres on 2009-04-05
I had a small hope that changing network manager to wicd could solve the problem but it didn't if anyone wonders...

Well well, only 18 days left to the final Jaunty, hopefully this issue is solved then [-o<

---

### Post by tanvach on 2009-04-06
A solution involves downgrading the RT2860 driver to version 1.7.1.1 (the last know fully working driver). It seems to work much more reliably for me at least on 1000h.

1) Get the driver from [http://www.array.org/ubuntu/dists/intrepid/eeepc/binary-i386/rt2860-dkms_1.7.1.1_all.deb]("http://www.array.org/ubuntu/dists/intrepid/eeepc/binary-i386/rt2860-dkms_1.7.1.1_all.deb")

2) Go to terminal, and move the pre-installed driver so it won't get loaded.
```

cd /lib/modules/2.6.28-11-generic/kernel/drivers/staging/rt2860/
sudo mv rt2860sta.ko rt2860sta.bak

```

3) Install rt2860-dkms_1.7.1.1_all.deb. It will also install dependencies needed to compile the driver. If it doesn't retrieve the right packages, make sure "build-essential", "linux-header-generic" and "dkms" is installed. Let it run and it should complete without a problem.

4) Restart. The new driver should work automatically.

---

### Post by Oputres on 2009-04-06
> **tanvach said:**
> A solution involves downgrading the RT2860 driver to version 1.7.1.1 (the last know fully working driver). It seems to work much more reliably for me at least on 1000h.

1) Get the driver from [http://www.array.org/ubuntu/dists/intrepid/eeepc/binary-i386/rt2860-dkms_1.7.1.1_all.deb]("http://www.array.org/ubuntu/dists/intrepid/eeepc/binary-i386/rt2860-dkms_1.7.1.1_all.deb")

2) Go to terminal, and move the pre-installed driver so it won't get loaded.
```

cd /lib/modules/2.6.28-11-generic/kernel/drivers/staging/rt2860/
sudo mv rt2860sta.ko rt2860sta.bak

```

3) Install rt2860-dkms_1.7.1.1_all.deb. It will also install dependencies needed to compile the driver. If it doesn't retrieve the right packages, make sure "build-essential", "linux-header-generic" and "dkms" is installed. Let it run and it should complete without a problem.

4) Restart. The new driver should work automatically.

Wohoooooo! Worked like a charm! Thank you!
:guitar:

---

### Post by tawmas on 2009-04-06
I'll try that. Right now, my 1000H cannot even detect my wireless network...

---

### Post by Oputres on 2009-04-06
> **tawmas said:**
> I'll try that. Right now, my 1000H cannot even detect my wireless network...

Are you on the Ubuntu Netbook Remix (UNR)? I didn't have any hardware detection error with UNR. Highly recommended!

---

### Post by tanvach on 2009-04-07
tawmas, if you've installed ndiswrapper before, chances are the ndiswrapper kernel module config file will try to override your card product and vendor IDs.

You need to move or delete "/etc/modprobe.d/ndiswrapper" otherwise the native driver will not get loaded.

---

### Post by tawmas on 2009-04-07
> **tanvach said:**
> tawmas, if you've installed ndiswrapper before, chances are the ndiswrapper kernel module config file will try to override your card product and vendor IDs.

You need to move or delete "/etc/modprobe.d/ndiswrapper" otherwise the native driver will not get loaded.

I didn't install anything pertaining to the the wireless network besides a plain desktop install from the beta ISO. I don't think it pulls down ndiswrapper automatically, but I didn't check.

After installing the downgraded driver, the situation is marginally better (i.e. I see the WLAN and can connect if I'm really close to the wireless router), but it's still failing from places where it didn't fail before, and where other devices don't fail (including my WinMo cell phone).

Now, if I could only remind when that "before" was... :-( I think it was around the -7 kernel.

Right now, I'm quite frustrated about this issue, because I cannot do wireless under any practical conditions.

---

### Post by ludwigbaum on 2009-04-11
Using Jaunty Beta (not UNR) on the Asus 1000H, I could not connect to my WLAN (WPA). The older driver 1.7.1.1 for the rt2860 solved the problem perfectly. Thank you.

---

### Post by Westmeath on 2009-04-11
My eeepc 1000h wifi works ootb with Jaunty (& Jaunty NR).

Tried it with WPA2 & WEP - so far no problems. Must be to do with how each modem/router implements the wifi. 

I installed Jaunty on an old Asus L3500h notebook last week. I had to switch off 802.11g & n on the router or it wouldn't hold a stable connection.

---

