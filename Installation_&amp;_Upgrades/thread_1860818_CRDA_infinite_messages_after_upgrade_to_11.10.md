---
title: "CRDA infinite messages after upgrade to 11.10"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by Xylian on 2011-10-15
Hi,
yesterday I've upgraded my Ubuntu 11.04 installation to 11.10 and I'm having troubles with CRDA, since it's flooding the syslog with continuous messages.. I've set the following:
```

# cat /etc/modprobe.d/cfg80211.conf 
options cfg80211 ieee80211_regdom="EU"

```
But something wrong happens at boot:
```

cfg80211: Calling CRDA for country: EU
cfg80211: Timeout while waiting for CRDA to reply, restoring regulatory settings
cfg80211: Restoring regulatory settings including user preference
cfg80211: Keeping preference on module parameter ieee80211_regdom: EU
cfg80211: Calling CRDA for country: US
cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[...]

```
And then udev keeps sending regulatory domain settings for country 97:
```

cfg80211: Calling CRDA for country: 97
cfg80211: Timeout while waiting for CRDA to reply, restoring regulatory settings
cfg80211: Keeping preference on module parameter ieee80211_regdom: EU
cfg80211: Adding request for country EU back into the queue
cfg80211: Adding request for country EU back into the queue
cfg80211: Adding request for country EU back into the queue
cfg80211: Adding request for country EU back into the queue
cfg80211: Adding request for country EU back into the queue
cfg80211: Adding request for country EU back into the queue
cfg80211: Kicking the queue
cfg80211: Calling CRDA to update world regulatory domain
[...]

```

Monitoring UDEV messages to the kernel, I see continuous messages like the following one:
```

# udevadm monitor --environment kernel
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

KERNEL[1950.592767] change   /devices/platform/regulatory.0 (platform)
UDEV_LOG=3
ACTION=change
DEVPATH=/devices/platform/regulatory.0
SUBSYSTEM=platform
MODALIAS=platform:regulatory
COUNTRY=00
SEQNUM=2829

```

Any idea about how to solve the problem? I've seen there was a bug related to kernel 3 here: [https://bugzilla.novell.com/show_bug.cgi?id=700159#c0]("https://bugzilla.novell.com/show_bug.cgi?id=700159#c0")

---

### Post by tobler on 2011-11-17
I have same problem here.
My wireless is on channel 13 and laptop does not connect after reboot. I tried to run command:
  sudo COUNTRY=FI crda
But it gives error:
  Failed to set regulatory domain: -7

So then I had to add /etc/modprobe.d/wireless file with content;
  options cfg80211 ieee80211_regdom=EU

After reboot my laptop still does not get into channel 13
  sudo iwlist f

dmesg tells more detailed error:
  cfg80211: Calling CRDA for country: 97
  cfg80211: Timeout while waiting for CRDA to reply, restoring regulatory settings

So now I can get network working only by removing all wireless kernel modules and loading them back again. So then(?) this ieee80211_regdom=EU is registered and I can get all channels.
dmesg:
  Keeping preference on module parameter ieee80211_regdom: EU

So there are bugs somewhere which is not reported widely yet. Or people are just using channels 1-11 only.
I read somewhere document that Ubuntu clock settings are used to get location and regulatory setting. So then running this command manually. But as it does not work neither I had to push location via kernel module option.

Thinking to leave Ubuntu and changing somewhere else (not Ubuntu based). Maybe Fedora is my next option...

br, Tobler

---

### Post by ygoe on 2011-12-02
Considering this thread is the only Google result on the exact error message (that is not a code patch that contains the message string), and nobody cares in this thread, I have created an Ubuntu bug here: [https://bugs.launchpad.net/ubuntu/+bug/899335](https://bugs.launchpad.net/ubuntu/+bug/899335) Hope it gets more attention over there.

---

### Post by Tesla01 on 2012-04-18
Hi,
 
are there some news about that? Or would it be fixed in 12.04?
 
I have a similar problem here, I also can't use channel 12 & 13 with the awus036nhr (rtl8192cu module).
In syslog it says things like:
 
[FONT=Calibri]"Disabling freq 2467 as custom regd has no rule that fits a 20 mhz wide channel"[/FONT]
 
regardless of which iw reg set xx I do..
 
Very annoying.. especially because it works under Windows on the same hardware..

---

### Post by Tesla01 on 2012-04-18
Has someone tried to recompile the Kernel without using CRDA?
 
with CONFIG_CFG80211_INTERNAL_REGDB ?

---

