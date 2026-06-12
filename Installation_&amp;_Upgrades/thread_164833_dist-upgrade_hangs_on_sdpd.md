---
title: "dist-upgrade hangs on sdpd"
date: 2006-04-23
forum: Installation &amp; Upgrades
---

### Post by Reggie on 2006-04-23
Hi,

I'm trying to upgrade my breezy to dapper. I did apt-get dist-upgrade and now it hangs on:

```
* Starting Bluetooth services...
hcid sdpd
```

I tried to kill /etc/bin/sdpd but no response.
What's the safest way to step over this ? I really don't want my computer to crash because of this ..

---

### Post by christhemonkey on 2006-04-23
```
sudo /etc/init.d/sdpd stop
```
will stop stop it running
You could just remove it from your init scripts:
```
sudo update-rc.d -f sdpd
```

---

### Post by Reggie on 2006-04-23
Ok got past it.
But now apt ends with the following message:

```
Errors were encountered while processing:
  bluez-utils
  bluez-pcmcia-support
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@KLUS:/home/reggie#
```

Is it safe to reboot ? How can I make sure the upgrade is really really finished ?

---

### Post by christhemonkey on 2006-04-23
Try running
```
sudo apt-get -f install
```
(i think its that...)

---

### Post by Reggie on 2006-04-23
The he tries to start the bluetooth service again. Is there any way to skip this service ?

---

### Post by codypumper on 2006-04-23
You can un-select it in synaptic

---

### Post by caesar424 on 2006-05-05
[QUOTE=Reggie]Hi,

I'm trying to upgrade my breezy to dapper. I did apt-get dist-upgrade and now it hangs on:

```
* Starting Bluetooth services...
hcid sdpd
```

I tried to kill /etc/bin/sdpd but no response.
What's the safest way to step over this ? I really don't want my computer to crash because of this ..[/QUOTE]

After trying all the suggestions here, nothing worked. What did I do?

Rebooted to safe mode by pressing Esc when prompted during Grub bootup. I chose an "old" kernel file to start in safe mode. After entering the root pw, I exeuted the dpkg --configure -a command to re"configure" the installation. After about 10 or 15 minutes, I had completed the dapper upgrade.

I also took time to correct my ndiswrapper error and subsequent hang while in safe mode. If anyone's interested or searching the forum, ndiswrapper hung on the -l parameter for me while in the GNOME. In safe mode, it worked fine and I was able to sort out my driver conflict. Rebooting into dapper I found my wireless to be working and configured correctly. Previously, I used the tutorial found [here]("http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux"). I do not know if upgrading to dapper beta delived more wifi support, so that is possible as well.

---

