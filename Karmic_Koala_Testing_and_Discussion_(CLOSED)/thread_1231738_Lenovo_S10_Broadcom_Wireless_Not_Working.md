---
title: "Lenovo S10 Broadcom Wireless Not Working ??"
date: 2009-08-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by fiddler59 on 2009-08-04
I can not seem to get the wireless working on my Lenovo S10 netbook. It has the dreaded Broadcom 4312 wireless in it. I try and enable it under system->hardware drivers and it crashes out. I tried installing the b43 driver and under hardware drivers it shows b43 drivers as being enabled but still no wireless. I tried installin the bcmwl kernel source and still no go....any help would be much appreciated. This is all with Ubuntu 9.10 with the latest updated and kernel.

David Blackmon

---

### Post by fiddler59 on 2009-08-05
Any help on this ?? Just for the record, wireless works fine with Ubuntu 8.10.

David Blackmon

---

### Post by fiddler59 on 2009-08-05
Any help at all ??

David Blackmon

---

### Post by taavikko on 2009-08-05
Stop bumping posts after few hours, somebody will reply if they are up to it.

for some extra-info
```
lspci; nm-tool; dkms status
```

---

### Post by fiddler59 on 2009-08-05
Sorry about that.....I guess I am just eager to get this thing somewhat working under 9.10. I'll post what I get when I am back at my netbook...I like the fact that the Intel video works much better under 9.10 as opposed to 9.04.

DB

---

### Post by caecusum on 2009-08-05
I'm not sure if it's related but I am also having wireless issues with my Intel 3945 wireless.

It works fine when I boot into the 2.6.31-4 kernel, but not *.31-5 and is also not due to the apparmor issues discussed in the other thread.

---

### Post by superhick on 2009-08-05
same iisues here, lenovo w500 series laptop. booting *3 kernel

 *-network
                description: Wireless interface
                product: Wireless WiFi Link 5300
                vendor: Intel Corporation

---

### Post by Nburnes on 2009-08-05
I have a BCM4312 wireless in my Acer Extensa that I am using right now and the wireless seems to be working fine, even turning on a boot up now.

I had to go under the hardware drivers and choose the BCMFwcutter and turn that on, then turn it off, just to be able to turn on the BCM4312 driver.

If that makes any sense?

---

### Post by superhick on 2009-08-05
here's log output, first one from *5 kernel, below is *3 one. 
ipv6 message is strange one, I'll try disabling ipv6 and check again

[   22.193676] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   25.423113] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12
[   25.601570] Registered led device: iwl-phy0::radio
[   25.601593] Registered led device: iwl-phy0::assoc
[   25.601612] Registered led device: iwl-phy0::RX
[   25.601632] Registered led device: iwl-phy0::TX
[   25.621069] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.862354] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   50.386324] wlan0: authenticate with AP 00:18:39:c9:7d:f0
[   50.388250] wlan0: authenticated
[   50.388253] wlan0: associate with AP 00:18:39:c9:7d:f0
[   50.390616] wlan0: RX AssocResp from 00:18:39:c9:7d:f0 (capab=0x411 status=0 aid=1)
[   50.390619] wlan0: associated
[   50.404950] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   50.586720] __ratelimit: 9 callbacks suppressed
[   50.586723] type=1503 audit(1249511981.463:15): operation="capable" pid=4696 parent=3231 profile="/sbin/dhclient3" name="net_raw"
[   60.564107] wlan0: no IPv6 routers present





[   21.201340] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   21.720112] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12
[   21.901035] Registered led device: iwl-phy0::radio
[   21.901057] Registered led device: iwl-phy0::assoc
[   21.901076] Registered led device: iwl-phy0::RX
[   21.901101] Registered led device: iwl-phy0::TX
[   21.917610] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.002089] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   45.583925] wlan0: authenticate with AP 00:18:39:c9:7d:f0
[   45.585957] wlan0: authenticated
[   45.585958] wlan0: associate with AP 00:18:39:c9:7d:f0
[   45.588031] wlan0: RX AssocResp from 00:18:39:c9:7d:f0 (capab=0x411 status=0 aid=1)
[   45.588034] wlan0: associated
[   45.589564] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

---

### Post by tekstr1der on 2009-08-05
> **fiddler59 said:**
> I can not seem to get the wireless working on my Lenovo S10 netbook. It has the dreaded Broadcom 4312 wireless in it. I try and enable it under system->hardware drivers and it crashes out. I tried installing the b43 driver... 
David Blackmon

Been running karmic on Lenovo S10 without issue since bcmwl-kernel-source became available. b43 module is blacklisted so that's not going to help you. Like taavikko stated, need to see output from 
```

dkms status
```

Did you build the module against the 31-5 kernel? It has worked flawlessly since 2.6.30 series kernels on up in karmic on S10.
```

$ apt-cache policy bcmwl-kernel-source
bcmwl-kernel-source:
  Installed: 5.10.91.9+bdcom-0ubuntu4
  Candidate: 5.10.91.9+bdcom-0ubuntu4
  Version table:
 *** 5.10.91.9+bdcom-0ubuntu4 0
        500 http://us.archive.ubuntu.com karmic/restricted Packages
        100 /var/lib/dpkg/status

$ dkms status
bcmwl, 5.10.91.9+bdcom, 2.6.31-3-generic-pae, i686: installed  (WARNING! Diff between built and installed module!)
bcmwl, 5.10.91.9+bdcom, 2.6.31-4-generic, i686: installed 
bcmwl, 5.10.91.9+bdcom, 2.6.31-1-generic, i686: built 
bcmwl, 5.10.91.9+bdcom, 2.6.31-2-generic, i686: built 
bcmwl, 5.10.91.9+bdcom, 2.6.31-3-generic, i686: built 
bcmwl, 5.10.91.9+bdcom, 2.6.31-5-generic, i686: installed 
```

---

### Post by fiddler59 on 2009-08-06
On a whim I decided to do a complete reinstall....I then updated (through wired lan) to the current state of available updates. I then rebooted with the new kernel and installed bcmwl-kernel-source
and rebooted and all is well and my wireless is working fine now. I know 9.10 is still in Alpha and things are routinely broken through updates, but I have a feeling I may have borked my system through careless installs and uninstalls of related and unrelated software trying to fix the issue. Thanx for all who helped and sorry for being a little over the top with the bumps earlier. I guess I am a little OCD !!

David B

---

