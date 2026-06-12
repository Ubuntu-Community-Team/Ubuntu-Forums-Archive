---
title: "Raspberry Pi Ubuntu: Wifi don't work"
date: 2022-09-01
forum: Installation &amp; Upgrades
---

### Post by waffen on 2022-09-01
Hello,
I just installed Ubuntu 22.04 in a Raspberry Pi4 64 bits, the wifi is not working, I can see the service active but in the Settings screen the gui keep in the searching mode and don't detect any network, the Rpi is located 40 cm from my router. Wired connection works fine.

The Rpi loading Raspbian works with no problem with my Wifi. 

Any ideas?

---

### Post by waffen on 2022-09-02
Hello,
Any ideas why the Wifi is not working?

---

### Post by MAFoElffen on 2022-09-03
I am surprised that no one has jumped in to help you... People are usually more responsive. I am posting this from my Raspberry PI 4 running 22.04.1 Server, with Ubuntu Desktop, usually connected via  Wifi... I am an IT Professional, and have a few skills. LOL

You did not explicitly say whether you were running Desktop or Server, but you did say a few things that implies that you are running Desktop Edition...
> 
"...in the Settings screen the gui keep in the searching mode and don't detect any network, "

There is a few things to look at first. For your router, is it setup with the SSID (Wifi Network Name) as discoverable or hidden? Usually by default, they are setup as discoverable, but just want to confirm that.

Next, ensure that your board firmware is up to date.
```

sudo apt update
sudo apt full-upgrade
sudo apt install rpi-eeprom
reboot

```
Then 
```

mafoelffen@ubuntu:~$ sudo rpi-eeprom-update
[sudo] password for mafoelffen: 
BOOTLOADER: up to date
   CURRENT: Thu Mar 10 11:57:12 UTC 2022 (1646913432)
    LATEST: Thu Mar 10 11:57:12 UTC 2022 (1646913432)
   RELEASE: stable (/lib/firmware/raspberrypi/bootloader/stable)
            Use raspi-config to change the release.

  VL805_FW: Using bootloader EEPROM
     VL805: up to date
   CURRENT: 000138a1
    LATEST: 000138a1

```
If it isn't up to date, then do this
```

sudo rpi-eeprom-update -a

```
If you look at the EEPROM update [Release notes]("https://github.com/raspberrypi/rpi-eeprom/blob/master/firmware/release-notes.md"), there were quite a few network fixes in the firmware this year...

Next, open a terminal session and do this:
```

awk '{print $0}' /proc/net/dev

```
The output should look somewhat like this:
```

Inter-|   Receive                                                |  Transmit
 face |bytes    packets errs drop fifo frame compressed multicast|bytes    packets errs drop fifo colls carrier compressed
    lo:  182950    1853    0    0    0     0          0         0   182950    1853    0    0    0     0       0          0
  eth0:       0       0    0    0    0     0          0         0        0       0    0    0    0     0       0          0
 wlan0: 15724446   38108    0    0    0     0          0     11867  6643028   35953    0    0    0     0       0          0
virbr0:       0       0    0    0    0     0          0         0        0       0    0    0    0     0       0          0

```
Next, run the [UbuntuForums 'system-info']("https://github.com/UbuntuForums/system-info") script and select upload to pastebin, then post the URL to the report here in a post.

---

