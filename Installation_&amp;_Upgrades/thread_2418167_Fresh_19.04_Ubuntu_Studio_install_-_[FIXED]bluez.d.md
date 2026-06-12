---
title: "Fresh 19.04 Ubuntu Studio install - [FIXED]bluez.dbus.error &amp; [FIXED]Volume Key broke"
date: 2019-05-02
forum: Installation &amp; Upgrades
---

### Post by joebuntu99 on 2019-05-02
After a fresh install of 19.04 I find two issues which were not present on my 18.04 install of Ubuntu Studio.

Firstly the Volume Keys (Mute, Up, Down - Fn+F1,2,3) on my Thinkpad X250 no longer control the audio volume. (Other keys such kill-networking & brightness keys work fine). After much searching I found a workaround involving xfce4-volumed. If I kill xfce4-volumed and then start it up again my keys are working. Perhaps somebody can offer a better solution so I can fix the problem? I am not sure why the initial auto-started instance fails to map the keys and the second manually started instance is successful - both are owned by my user.

note: On 18.04 I added the ubuntu-studio 18.04 backports ppa and the software updater install packages that were being held back by apt-get. This broke the volume controls on 18.04. I just did a ppa-purge and it reverted to working condition. This might be relevant?

The second issue is when I attempt to connect to my Denon Bluetooth Speaker I get the error 
Connection Failed blueman.bluez.errors.DBusFailedError:Host is down.
or (more commonly I think)
Connection Failed blueman.bluez.errors.DBusFailedError:Resource Temporarily Unavailable


The speaker does appear to connect briefly then lose the connection as if it fails to be connected to pulse audio after connecting to the adapter.
This is shown when using bluetoothctl

```
[bluetooth]# scan on
Discovery started
...
[bluetooth]# pairXX:XX:XX:XX:XX:XX
Attempting to pair with XX:XX:XX:XX:XX:XX
[CHG] Device XX:XX:XX:XX:XX:XX Connected: yes
[CHG] Device XX:XX:XX:XX:XX:XX ServicesResolved: yes
[CHG] Device XX:XX:XX:XX:XX:XX Paired: yes
Pairing successful
[CHG] Device XX:XX:XX:XX:XX:XX ServicesResolved: no
[CHG] Device XX:XX:XX:XX:XX:XX Connected: no
```


The issue of DBusFailedError seems from searches to be ongoing and unsolved. I can only get connected if I delete the device from the bluetooth manager and sudo service bluetooth restart and then pair the speaker and connect. This usually works (not always) but is not a sustainable workaround since my speaker powers off after about 10 minutes silence and then I cant reconnect!

For reference
[https://github.com/blueman-project/blueman/issues/547](https://github.com/blueman-project/blueman/issues/547)
[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1660277](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1660277)

Any advice on fixes or avenues of investigation appreciated.

---

### Post by joebuntu99 on 2019-05-02
I have the same two issues when I boot ubuntu studio live from the install usb stick

The volume issue seems to have cleared up and the volume keys are being correctly mapped at login.

---

### Post by joebuntu99 on 2019-05-06
I solved my bluetooth issue by copying the /var/lib/bluetooth directory from my old install to my new one. It appears to behave as before now.

---

### Post by Nosphky on 2019-05-24
I just discovered the ppa-ubuntustudio and applied it to my installation of 18.04. The most noticeable effect (apart from the whole new set of icons) was that my logitech keyboard's volume buttons (mute, up and down) were killed.

I tried your workaround of killing 'xfce4-volumed' and restarting it. This works for me, thanks.

I'll live with that until something better comes up.

---

