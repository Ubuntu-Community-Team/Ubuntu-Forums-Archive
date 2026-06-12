---
title: "Wireless light flashing"
date: 2013-01-25
forum: Installation &amp; Upgrades
---

### Post by kronus980 on 2013-01-25
I'm using an HP HDX 18, on Ubuntu 12.10, with the wireless card: ```
Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
```

Did the most recent kernel upgrade(provided by Ubuntu):
```
3.5.0-23-generic
``` 
restarted, logged in and it's flashing. Wi-fi works fine, I'm just worried. Should I be? And is there any way to stop the flashing? Thanks in advance.

---

### Post by tgalati4 on 2013-01-25
Electrical tape.

What module is loaded for wireless?

```
lsmod
modinfo wirelessmodulethatyoudiscoveredfromabovecommand
```

There may be a module switch to turn it off or change it's flashing behavior.

---

### Post by kronus980 on 2013-01-25
I don't know what that output means D: (Not so good with Linux yet..) But I ran the command, the only thing that was related to wifi was this:

```
mac80211              539958  1 iwlwifi
```

Is that of any use? Or do you want the entire output?

---

### Post by tgalati4 on 2013-01-25
Didn't find anything here:

tgalati4@Dell600m-mint14 ~ $ modinfo mac80211
filename:       /lib/modules/3.5.0-17-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     4E9B5E45BF1683A7E81BC0A
depends:        cfg80211
intree:         Y
vermagic:       3.5.0-17-generic SMP mod_unload modversions 686 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

Post the entire output of lsmod.

---

### Post by |{urse on 2013-01-25
Due to dyslexia I saw this post as "Wireless Flashlight" and I lol'd a bit.

---

### Post by fugue69 on 2013-02-20
Kronus,

I have an HDX 18 as well (although I'm running Ubuntu 12.04)... Have you tried editing the wlan.conf file?

Try this (it worked for me):

```
$ sudo -i
# echo 'options iwlwifi led_mode=1' >> /etc/modprobe.d/wlan.conf
# modprobe -r iwlwifi && modprobe iwlwifi
# exit

```

---

