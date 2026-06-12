---
title: "Mythtv upgrading from 26 I think to 29 duel tuners and other issues"
date: 2018-04-21
forum: Installation &amp; Upgrades
---

### Post by DeadEnd on 2018-04-21
Installing mythtv 0.26 I think was straight forward on ubuntu 14.04 but a clean install of 29.0 on ubuntu 16.04 has caused me many hours of frustration working out how to solve it and get it back up and running, 

This was mainly due to fact there have been changes to setup process that I was not aware of until I ran into a brick wall.

Also I noticed many threads where people gave up in frustration as there are very little or no error messages that point to the actual problem concerning duel tuners that I could see.

This worked for me hope it might help others who face the same issues.

0000 needs to set in myth-backend setup screen  or you will never get access to the database from other clients, this was not required previously .

Also storage groups now needs to be manually added whereas previous versions they were already set up and there are no error messages if you have failed to set location and or permissions wrong

My dibcom7000-PC duel tuner would be automatically recognised and set up correctly in previous versions, this is not the case any more, I now have to set both tuners up individually.

Everything seemed to check out just fine, all the permissions seemed to be correct and the dvb card was recognised and the drivers correctly installed.

```
ls -ld /dev/dvb/adapter*/frontend*
crw-rw----+ 1 root video 212, 3 Apr 21 23:31 /dev/dvb/adapter0/frontend0
crw-rw----+ 1 root video 212, 7 Apr 21 23:31 /dev/dvb/adapter1/frontend0
```

```
grep video /etc/group
video:x:44:mythtv
```



cat /var/log/mythtv/mythbackend.log No obvious errors in any logs that I could see .

```
dmesg
dvb-usb: found a 'Sony PlayTV' in warm state.
[   24.406903] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   24.407141] dvbdev: DVB: registering new adapter (Sony PlayTV)
[   24.522898] kvm: disabled by bios
[   24.967137] usb 1-2: DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[   25.223980] dib0070: DiB0070: successfully identified
[   25.224042] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   25.224760] dvbdev: DVB: registering new adapter (Sony PlayTV)
[   25.406174] usb 1-2: DVB: registering adapter 1 frontend 0 (DiBcom 7000PC)...
[   25.578652] rt2800pci 0000:07:00.0 wlo1: renamed from wlan0
[   25.703487] dib0070: DiB0070: successfully identified
[   25.740155] Registered IR keymap rc-dib0700-rc5
[   25.740732] rc rc0: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:12.2/usb1/1-2/rc/rc0
[   25.740825] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:12.2/usb1/1-2/rc/rc0/input15
[   25.740956] dvb-usb: schedule remote query interval to 50 msecs.
[   25.740961] dvb-usb: Sony PlayTV successfully initialized and connected.
```

This took the longest to solve eventually I had to add the first tuner/source /adapter0/frontend0 then scan for channels save then reboot then add the second tuner but this time not tuning for channels  just adding the source to /dev/dvb/adapter1/frontend0 then another reboot.

Adding the second card would always get a programming error in the main screen or card unavailable but nothing in any logs and without a reboot on each steps would not work at all.

I am sure there is a far more graceful way of proceeding without a reboot but my patience had worn thin at that point.

I do not think this is a ubuntu problem more a myth problem so apologies should have posted there .

---

### Post by DeadEnd on 2018-04-21
Wow just realised it has been 12 years since I  joined and probably 10 since last posted so forgive me if a little rusty.

I use ubuntu everyday as my main OS and my absence from this support forum is testament to the great work built by the community.

---

### Post by deadflowr on 2018-04-21
What Ubuntu releases are involved in all this?

---

### Post by DeadEnd on 2018-04-24
Apologies, hope I have made it more clear.

---

