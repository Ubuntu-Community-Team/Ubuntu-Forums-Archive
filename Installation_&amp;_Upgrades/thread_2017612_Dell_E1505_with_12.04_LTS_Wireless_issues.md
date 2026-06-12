---
title: "Dell E1505 with 12.04 LTS Wireless issues"
date: 2012-07-05
forum: Installation &amp; Upgrades
---

### Post by SimpsonTruckDriver on 2012-07-05
Using another post, I am going to show what the system gives me. It's a Dell Inspiron E1505, 2Gb RAM. I'm using the Verizon MiFi 2200 hooked to USB to connect right now. If I go to Windows Vista, I get into my home wireless network fine, but coming over to Ubuntu, not so much. So, here's what I did...
[INDENT]lspci -nn | grep 0280
[/INDENT]shows:
[INDENT]0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
[/INDENT]And...
[INDENT]lsmod | grep -e wl -e b43
[/INDENT]
shows:
[INDENT]wl                   2646601  0
lib80211           14040  1 wl
[/INDENT]And...
[INDENT]rfkill list all
[/INDENT]
shows:
[INDENT]0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
[/INDENT]In Windows Vista, Fn-F2 turns on the Wireless (light). But, the light won't turn on, wireless won't work, etc. It looks like the driver is ok. So, is there anything additional I need to try/do?

Thanks!
TS

---

### Post by O2Blevel on 2012-07-05
Fn+F2 will turn on/off the wireless but there is no indicator to tell you whether it's on or off.

Did you do this process yet?

  sudo apt-get update
  sudo apt-get install b43-fwcutter
  sudo apt-get install firmware-b43-installer

---

### Post by SimpsonTruckDriver on 2012-07-05
I did those steps, wireless card still won't start. 

TS

---

### Post by O2Blevel on 2012-07-05
I saw the b43 reference in your first post and I thought you were using the same driver as I do, I also have a Dell E1505, but now I see you're using the Broadcom STA driver from the 'additional drivers'.

Here's a thread that should get it working:

[http://ubuntuforums.org/showthread.php?t=1967515&highlight=jockey]("http://ubuntuforums.org/showthread.php?t=1967515&highlight=jockey")

You may also want to check the 'known issues' in this link:

[http://wiki.debian.org/wl/#Known_Issues]("http://wiki.debian.org/wl/#Known_Issues")

---

### Post by SimpsonTruckDriver on 2012-07-07
Typing:

sudo apt-get install --reinstall bcmwl-kernel-source

gives **Reinstallation of bcmwl-kernel-source is not possible, it cannot be downloaded**

Typing

sudo modprobe wl

gives no answer.

Typing

sudo modprobe -r wl
sudo modprobe -r bcma
sudo modprobe brcmsmac

gives no answer.

Typing

sudo su
echo "blacklist wl" >> /etc/modprobe.d/blacklist.conf
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
echo brcmsmac >> /etc/modules
exit

And rebooting gives NO wireless.

lsmod | grep -e wl -e bcma -e brcmsmac

gives

[B]brcmsmac              540875  0 
mac80211              436455  1 brcmsmac
brcmutil                    14675  1 brcmsmac
cfg80211                 178679  2 brcmsmac,mac80211
crc8                             12781  1 brcmsmac
cordic                         12487  1 brcmsmac
wl                             2646601  0 
lib80211                      14040  1 wl[/B]

Typing

dmesg | grep -e brcm -e wlan
iwconfig

Gives
[B]ppp0      no wireless extensions.
lo            no wireless extensions.
eth1      no wireless extensions.[/B]

Typing

rfkill list all

Shows

[B]0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no[/B]

Going into "Additional Drivers", the Broadcom one is listed, un-activated, but refuses to activate (I'm guessing that's the point). But, still no wireless (Fn-F2 will not turn on the wireless). Interestingly , 10.04 LTS worked fine with the wireless, did a full removal of the old one and installed 12.04 LTS on a cleaned partition.

Any other ideas?

TS

---

### Post by SimpsonTruckDriver on 2012-08-01
Any ideas?

TS

---

### Post by dwhitney67 on 2012-08-11
> **SimpsonTruckDriver said:**
> Any ideas?

TS

I just spent the afternoon trying to resurrect an old E1505 that I have with Kubuntu 12.04.  I had the same issues you described.  After Googling a bit, I came up with something that worked -- hopefully it will work for you too.

```

sudo apt-get update

sudo apt-get remove bcmwl-kernel-source

# If the following file does not exist, don't sweat it.
# However, you may need to comment out bcm43xx in /etc/modprobe.d/blacklist.conf
sudo rm /etc/modprobe.d/blacklist-bcm43.conf

sudo apt-get install b43-fwcutter

After installing b43-fwcutter, make sure to REBOOT your PC!!

Then run the following Terminal commands:

sudo modprobe -r b43 b44 b43legacy ssb

sudo modprobe b43

Then RETEST wireless.

```
Sure enough, when pressing Fn-F2, the WiFi LED lit up.  All I had to do then was setup a connection to my router.

But, I noticed that my wired-interface was no longer running; so I ran the following (note, I'm not certain whether the removal of b44 could have been deleted from the step performed earlier):
```

sudo modprobe b44

```
To complete the exercise, reboot your system.  Verify whether the wireless and the wired interfaces are both up/running.
```

/sbin/ifconfig

```
If all is well, then disconnect your LAN cable and go wireless!

---

### Post by SimpsonTruckDriver on 2012-08-24
Yep, that worked!

TS

---

