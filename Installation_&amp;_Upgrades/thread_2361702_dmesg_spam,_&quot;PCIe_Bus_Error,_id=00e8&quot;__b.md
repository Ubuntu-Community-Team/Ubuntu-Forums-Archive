---
title: "dmesg spam, &quot;PCIe Bus Error, id=00e8&quot;  both 16.04 and 17.04, (workaround OK)"
date: 2017-05-19
forum: Installation &amp; Upgrades
---

### Post by jbeale2 on 2017-05-19
I have an i7-6700TE @ 2.4GHz, 32 GB RAM, 500 GB SSD with Nvidia GeForce GT710 video card and Realtek 8821AE PCI-E wireless adaptor. It came with Windows 10 installed, and that works fine. I then installed Ubuntu Desktop 16.04 from a bootable USB stick, and it installed, rebooted, and runs, but 'dmesg' showed a continual stream of error messages every few microseconds (! yes, some serious spammage) about a PCIe bus error with Receiver ID 00e8. I then tried installing Ubuntu 17.04 with exactly the same result. Any ideas? 

With this error rate, I see /var/log/kern.log is over 10 GB in size only a few minutes after login. This may be related to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1521173](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1521173) allegedly related to "Realtek, RLT8723BE PCIe Wireless Network Adapter".  I followed the workaround on that bug changing the grub file, and it works for me (no more PCIe errors reported). However, it also caused the internal PCIe wifi to stop working (it had worked before in Ubuntu, despite all the errors logged). I am still able to use a separate TP-Link TL-WN822N v3 USB wifi device.

> [COLOR=#333333][FONT=monospace]Note: Current workaround is to add pci=noaer to your kernel command line:
1) edit /etc/default/grub and and add pci=noaer to the line starting with GRUB_CMDLINE_LINUX_DEFAULT. It will look like this:[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=noaer"
2) run "sudo update-grub"
3) reboot[/FONT][/COLOR]

```
$ ls -al /var/log/kern.log
-rw-r-----  1 syslog            adm    10208816070 May 19 15:45 kern.log


$ uname -a
Linux linux-desktop 4.10.0-19-generic #21-Ubuntu SMP Thu Apr 6 17:04:57 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```


sample from 'dmesg' : 


```
[  283.805239] pcieport 0000:00:1d.0: AER: Corrected error received: id=00e8
[  283.805243] pcieport 0000:00:1d.0: can't find device of ID00e8
[  283.805256] pcieport 0000:00:1d.0: AER: Corrected error received: id=00e8
[  283.805260] pcieport 0000:00:1d.0: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e8(Receiver ID)
[  283.805262] pcieport 0000:00:1d.0:   device [8086:a119] error status/mask=00000001/00002000
[  283.805263] pcieport 0000:00:1d.0:    [ 0] Receiver Error         (First)
[  283.805281] pcieport 0000:00:1d.0: AER: Corrected error received: id=00e8
[  283.805287] pcieport 0000:00:1d.0: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e8(Receiver ID)
[  283.805288] pcieport 0000:00:1d.0:   device [8086:a119] error status/mask=00000001/00002000
[  283.805290] pcieport 0000:00:1d.0:    [ 0] Receiver Error         (First)
[  283.805296] pcieport 0000:00:1d.0: AER: Corrected error received: id=00e8
[  283.805300] pcieport 0000:00:1d.0: can't find device of ID00e8
[  283.805321] pcieport 0000:00:1d.0: AER: Corrected error received: id=00e8
[  283.805325] pcieport 0000:00:1d.0: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e8(Receiver ID)
[  283.805326] pcieport 0000:00:1d.0:   device [8086:a119] error status/mask=00000001/00002000
[  283.805327] pcieport 0000:00:1d.0:    [ 0] Receiver Error         (First)

```

---

