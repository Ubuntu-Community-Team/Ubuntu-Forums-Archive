---
title: "Network Manager refuses to start after update"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zmjjmz on 2009-10-12
I recently did a fairly massive update, and I hadn't read the partial upgrade sticky yet so I went through with it. After I rebooted, nm-applet was there saying that NetworkManager wasn't running. I tried to start NetworkManager manually, but I got this error in the syslog:
```

<info> starting...
<info> modem-manager is now available
<ERROR>#011[1255334074.910022] main (): Failed to initialize the network manager: (unknown)
traceback:
#011NetworkManager(main+0xbd7) [0x807d657]
#011/lib/libc.so.6(__libc_start_main+0xe6) [0xe916b56]
#011NetworkManager [0x805cfa1]

```
It repeats that for a while, with different numbers. I'm hoping someone can tell me something about this, because in the meantime I have no connection at all, and I can't get the libatasmart4 dependency to get ceni running.

By the way, this is running on a Dell Mini 910 (Broadcom BCM4312 for wireless) with 1GB RAM and a 16B SSD.
eth1 is listed as an interface in ifconfig.

---

### Post by rb0171610 on 2009-10-12
> **zmjjmz said:**
> I recently did a fairly massive update, and I hadn't read the partial upgrade sticky yet so I went through with it. After I rebooted, nm-applet was there saying that NetworkManager wasn't running. I tried to start NetworkManager manually, but I got this error in the syslog:
```

<info> starting...
<info> modem-manager is now available
<ERROR>#011[1255334074.910022] main (): Failed to initialize the network manager: (unknown)
traceback:
#011NetworkManager(main+0xbd7) [0x807d657]
#011/lib/libc.so.6(__libc_start_main+0xe6) [0xe916b56]
#011NetworkManager [0x805cfa1]

```
It repeats that for a while, with different numbers. I'm hoping someone can tell me something about this, because in the meantime I have no connection at all, and I can't get the libatasmart4 dependency to get ceni running.

By the way, this is running on a Dell Mini 910 (Broadcom BCM4312 for wireless) with 1GB RAM and a 16B SSD.
eth1 is listed as an interface in ifconfig.
Are you able to manage your connection from the command line?

---

### Post by zmjjmz on 2009-10-12
> **rb0171610 said:**
> Are you able to manage your connection from the command line?

Probably, but I'm not so sure how.

---

### Post by rb0171610 on 2009-10-12
> **zmjjmz said:**
> Probably, but I'm not so sure how.

is eth1 your wireless device? it happens to be on my dell / broadcom.

---

### Post by rb0171610 on 2009-10-12
> **zmjjmz said:**
> Probably, but I'm not so sure how.

[http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/](http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/)

---

### Post by zmjjmz on 2009-10-12
> **rb0171610 said:**
> is eth1 your wireless device? it happens to be on my dell / broadcom.

Yes, and I'm going to try some stuff I got through google. Hopefully I can at least get ceni installed.

---

### Post by rb0171610 on 2009-10-12
> **zmjjmz said:**
> Probably, but I'm not so sure how.

ifconfig wlan0
iwconfig wlan0 essid NETWORK_ID key WIRELESS_KEY
dhclient wlan0

these three commands, replacing wlan0 with the name of your dev, probably eth1

---

### Post by zmjjmz on 2009-10-12
> **rb0171610 said:**
> ifconfig wlan0
iwconfig wlan0 essid NETWORK_ID key WIRELESS_KEY
dhclient wlan0

these three commands, replacing wlan0 with the name of your dev, probably eth1

The second gives me this error:
```
Error for wireless request"Set Encode" (8B2A) :
SET failed on device eth1 ; Invalid argument.

```

I'm using WPA2, so I think I need to go through wpa_supplicant for this.

---

### Post by rb0171610 on 2009-10-12
> **zmjjmz said:**
> The second gives me this error:
```
Error for wireless request"Set Encode" (8B2A) :
SET failed on device eth1 ; Invalid argument.

```

I'm using WPA2, so I think I need to go through wpa_supplicant for this.

Possibly true, you need WPA supplicant.  I am using WEP.
Meaning: True, it is possible that you might need WPA supplicant.  I am using WEP.

---

### Post by rb0171610 on 2009-10-12
> **rb0171610 said:**
> Possibly true, you need WPA supplicant.  I am using WEP.

u posted the output but not the exact command you used

---

### Post by zmjjmz on 2009-10-12
> **rb0171610 said:**
> Possibly true, you need WPA supplicant.  I am using WEP.

In that post, actually, the poster said that the network he was connecting to used WPA2.

---

### Post by rb0171610 on 2009-10-12
> **zmjjmz said:**
> In that post, actually, the poster said that the network he was connecting to used WPA2.

Yes he told me that finally. What is your point? I want to know what command he used that gave him the output he posted to me. 
The output he gave can be given back in a variety of scenarios, regardless of the encryption method.

---

### Post by zmjjmz on 2009-10-12
> **rb0171610 said:**
> Yes he told me that finally. What is your point? I want to know what command he used that gave him the output he posted to me. 
The output he gave can be given back in a variety of scenarios, regardless of the encryption method.

I'm not entirely sure that you're talking to/about me, but that error was generated by the iwconfig eth1 essid NETWORK_ID key s:NETWORK_KEY stuff.

---

### Post by rb0171610 on 2009-10-12
> **zmjjmz said:**
> I'm not entirely sure that you're talking to/about me, but that error was generated by the iwconfig eth1 essid NETWORK_ID key s:NETWORK_KEY stuff.

I realize that.  But since I don't know what was put into the command line exactly it makes it a little difficult to help troubleshoot the problem.  I would hope he did not type exactly: 
*iwconfig eth1 essid NETWORK_ID key s:NETWORK_KEY*
 
with a return of:

[I]Error for wireless request"Set Encode" (8B2A) :
SET failed on device eth1 ; Invalid argument.[/I]
I am talking to you.

Cheers.

---

### Post by zmjjmz on 2009-10-12
> **rb0171610 said:**
> I realize that.  But since I don't know what was put into the command line exactly it makes it a little difficult to help troubleshoot the problem.  I would hope he did not type exactly: 
*iwconfig eth1 essid NETWORK_ID key s:NETWORK_KEY*
 
with a return of:

[I]Error for wireless request"Set Encode" (8B2A) :
SET failed on device eth1 ; Invalid argument.[/I]
I am talking to you.

Cheers.

No, I put in my essid and password, using the s: to use a string password.

---

### Post by zmjjmz on 2009-10-12
Never mind that, I got wl working too.
I got ceni to work though :D

---

