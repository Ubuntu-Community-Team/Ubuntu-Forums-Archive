---
title: "Intel 4965 AGN Completely Defunct from Beta Testing"
date: 2009-04-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Melk79 on 2009-04-02
I am not a programmer.  I've been using Ubuntu and a few other distros for about a year now and decided I want to be a part of the solution.

I upgraded from Intrepid to Jaunty Beta to help support the suspend/resume testing and kerneloops testing.  The first day went OK, though the suspend/resume test failed.  Second day, I tried to do that test again and it failed again (during interative step 7 at 50 seconds: resulted in black screen with no x session, no mouse control).  Since that last failure, my Intel 4965 AGN wireless card is almost entirely non-functional, both in Ubuntu and on my Vista partition.  My old laptop's wireless is working fine as well as my desktop's ethernet connection.

I tried restarting, suspending, shutting down, taking battery out, etc. and last night it actually woke up for a while and I was able to update through the terminal thinking this might help.

Today, I have the same problem.  Absolutely no wireless connection from Vista, Ubuntu and even a Hardy LiveCD.  I understand Beta's aren't ready for primetime, but didn't think it could actually take out hardware.  Running sudo lshw - C network does output the Intel's details, so it is seemingly still alive.

At startup I received this message (not sure of any correlation): User's $HOME/.drmc file is being ignored.  This prevents the default session and language from being saved. File should be owned by user and have 644 permissions.  User's $HOME directory must be owned by user and not writable by other users.

Can anyone help out?  I like to help testing, but losing wireless might as well be taking out the computer all together.

Thanks!

---

### Post by caryb on 2009-04-02
Melk79 I had the same problem with my wireless (previous model to you) what I did was boot into windows go into the wireless property's in network neighbourhood & right click & enable the device. For some reason it gets turned off at the bios level & needs to be forced back on. If you have a wireless switch on your pc you could try tuning it off & back on. I did this on a friends laptop but as mine doesn't have a switch I had to do it at the software level. There might be a way to do this in Gnome but I was unable to find a way in KDE/Kubuntu.


Cary

---

### Post by psyke83 on 2009-04-02
> **Melk79 said:**
> I am not a programmer.  I've been using Ubuntu and a few other distros for about a year now and decided I want to be a part of the solution.

I upgraded from Intrepid to Jaunty Beta to help support the suspend/resume testing and kerneloops testing.  The first day went OK, though the suspend/resume test failed.  Second day, I tried to do that test again and it failed again (during interative step 7 at 50 seconds: resulted in black screen with no x session, no mouse control).  Since that last failure, my Intel 4965 AGN wireless card is almost entirely non-functional, both in Ubuntu and on my Vista partition.  My old laptop's wireless is working fine as well as my desktop's ethernet connection.

I tried restarting, suspending, shutting down, taking battery out, etc. and last night it actually woke up for a while and I was able to update through the terminal thinking this might help.

Today, I have the same problem.  Absolutely no wireless connection from Vista, Ubuntu and even a Hardy LiveCD.  I understand Beta's aren't ready for primetime, but didn't think it could actually take out hardware.  Running sudo lshw - C network does output the Intel's details, so it is seemingly still alive.

At startup I received this message (not sure of any correlation): User's $HOME/.drmc file is being ignored.  This prevents the default session and language from being saved. File should be owned by user and have 644 permissions.  User's $HOME directory must be owned by user and not writable by other users.

Can anyone help out?  I like to help testing, but losing wireless might as well be taking out the computer all together.

Thanks!

Some ideas:
[LIST]
[*]Make sure your wireless switch is turned on! On some laptops it's a physical switch, on others it's a special keypress.
[*]Check your dmesg log for any indications of problems with your wireless card. I'm not sure what's the name of the kernel module for your wireless chipset, so check the whole log for relevant messages.
[*]Ensure you didn't remove important packages from your system such as "linux-restricted-modules-generic", etc.
[*]Check your wireless _router_.
[*]Try to update your BIOS to a newer version, if available.
[/LIST]

AFAIK, there are no hardware killing bugs for any of the Intel wireless modules (although there was a recent problem with wired ethernet cards getting bricked), so it's highly unlikely that your card was killed by software.

---

### Post by Melk79 on 2009-04-02
caryb, thanks for your advice.  It doesn't seem to be doing the trick for me at the moment, but I think the chip is turned off as you said.

psyke83, switch is on and has been toggled many times now (not in the crazy back in forth way, just nice cross your fingers way.)

In the logs I see nvidia and intel both setting their latency timer to 64.  Then wlan0 goes through a bunch of authentication messages and shortly therefter deauthenticates.  Last two messages before deauthentication are: wlan0 no IPv6 routers present, wlem0: disassociating by local choice (reason=3)

linux-restricted-modules is not installed, but l-r-m-common and l-r-m-generic are installed.

The router is D-Link DIR-615, seems to be OK considering my old lappy connects (but on 11g not 11n).  Does that IPv6 message mean I should change a setting.  Not sure why Vista would care though.

Also not sure if it is just coincidence, but as NM is trying to connect I seem to get a serious crash message about the kernel and compiz.real craps out.  Didn't get the kernel message just now, so I'm not sure what it is.

Also, BIOS is current

---

### Post by Melk79 on 2009-04-02
Great.  iwlagn MAC is in deep sleep!  Looks like a bug [http://www.gossamer-threads.com/lists/linux/kernel/1046835](http://www.gossamer-threads.com/lists/linux/kernel/1046835)

Anyone know how to wake up?

---

### Post by SyberKowboy on 2009-04-14
Toggling switch on then off seems to get the wifi back on for me but the issue I've been having lately with the new kernels is that both the iwlagn and Broadcomm STA drivers connect and work fine for some random period of time then drop to a 1 Mb/s connection. Can't figure it out. Last build (same hardware) I threw some commands at it and go another driver install (don't recall the name) but it was sort of stable.


```
 18.558733] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   18.558736] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   18.558873] iwlagn 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.558907] iwlagn 0000:0c:00.0: setting latency timer to 64
[   18.558989] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   18.597128] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   18.601652] iwlagn: Tunable channels: 11 802.11bg, 13 802.11a channels
[   18.601749] iwlagn 0000:0c:00.0: irq 2295 for MSI/MSI-X
[   18.602454] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   18.611604] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   18.611676] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.656247] udev: renamed network interface wlan0 to wlan1
[   18.884261] lp: driver loaded but no devices found
[   18.992705] Adding 2088440k swap on /dev/sda3.  Priority:-1 extents:1 across:2088440k
[   19.402734] elantech.c: assuming hardware version 1, firmware version 2.4
[   19.498916] elantech.c: Synaptics capabilities query result 0x10, 0x02, 0x64.
[   19.529070] EXT3 FS on sda4, internal journal
[   20.028214] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input8
[   21.806755] type=1505 audit(1239676910.918:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2174
[   21.846033] type=1505 audit(1239676910.958:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2178
[   21.846122] type=1505 audit(1239676910.958:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2178
[   21.846152] type=1505 audit(1239676910.958:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2178
[   21.846179] type=1505 audit(1239676910.958:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2178
[   21.925024] type=1505 audit(1239676911.038:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2183
[   21.925157] type=1505 audit(1239676911.038:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2183
[   21.958906] type=1505 audit(1239676911.070:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2187
[   32.494081] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   32.494084] vboxdrv: Successfully done.
[   32.494085] vboxdrv: Found 2 processor cores.
[   32.494958] VBoxDrv: dbg - g_abExecMemory=ffffffffa0b15aa0
[   32.495020] vboxdrv: fAsync=0 offMin=0x198 offMax=0xf948
[   32.495056] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   32.495058] vboxdrv: Successfully loaded version 2.1.4_OSE (interface 0x000a0009).
[   32.700192] VBoxNetFlt: dbg - g_abExecMemory=ffffffffa0cb4940
[   35.757552] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   35.757554] Bluetooth: BNEP filters: protocol multicast
[   35.771076] Bridge firewalling registered
[   39.115325] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   39.116202] input: MoGo Mouse X54 as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/bluetooth/hci0/hci0:11/input9
[   39.156182] generic-bluetooth 0005:0A5C:0001.0001: input,hidraw0: BLUETOOTH HID v1.29 Mouse [MoGo Mouse X54] on 00:22:69:CF:49:75
[   41.323396] ppdev: user-space parallel port driver
[   44.887789] tg3 0000:04:00.0: irq 2294 for MSI/MSI-X
[   44.952420] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   45.030303] iwlagn 0000:0c:00.0: firmware: requesting iwlwifi-4965-2.ucode
[   46.187027] Registered led device: iwl-phy0:radio
[   46.187049] Registered led device: iwl-phy0:assoc
[   46.187060] Registered led device: iwl-phy0:RX
[   46.187072] Registered led device: iwl-phy0:TX
[   46.555374] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   48.176272] wlan1: authenticate with AP 00:0f:3d:3b:22:a4
[   48.376274] wlan1: authenticate with AP 00:0f:3d:3b:22:a4
[   48.517741] wlan1: authenticated
[   48.517746] wlan1: associate with AP 00:0f:3d:3b:22:a4
[   48.524094] wlan1: RX AssocResp from 00:0f:3d:3b:22:a4 (capab=0x421 status=0 aid=1)
[   48.524098] wlan1: associated
[   48.567082] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   48.568173] wlan1: disassociating by local choice (reason=3)
[   59.208248] wlan1: no IPv6 routers present
[  196.524782] input: MoGo Mouse X54 as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/bluetooth/hci0/hci0:12/input10
[  196.568194] generic-bluetooth 0005:0A5C:0001.0002: input,hidraw1: BLUETOOTH HID v1.29 Mouse [MoGo Mouse X54] on 00:22:69:CF:49:75
[  218.889209] wlan1: authenticate with AP 00:1d:7e:d5:1e:d8
[  218.892341] wlan1: authenticated
[  218.892350] wlan1: associate with AP 00:1d:7e:d5:1e:d8
[  218.896435] wlan1: RX AssocResp from 00:1d:7e:d5:1e:d8 (capab=0x411 status=0 aid=1)
[  218.896441] wlan1: associated
[ 1063.945732] CE: hpet increasing min_delta_ns to 15000 nsec
[ 1065.721299] CE: hpet increasing min_delta_ns to 22500 nsec
[ 1066.637414] CE: hpet increasing min_delta_ns to 33750 nsec
[ 1548.826713] wlan1: disassociating by local choice (reason=3)
[ 1624.653342] input: MoGo Mouse X54 as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/bluetooth/hci0/hci0:11/input11
[ 1624.693179] generic-bluetooth 0005:0A5C:0001.0003: input,hidraw2: BLUETOOTH HID v1.29 Mouse [MoGo Mouse X54] on 00:22:69:CF:49:75
[ 1628.334248] wlan1: deauthenticated
[ 1723.103254] iwlagn: MAC is in deep sleep!
[ 1734.373697] Registered led device: iwl-phy0:radio
[ 1734.373734] Registered led device: iwl-phy0:assoc
[ 1734.373771] Registered led device: iwl-phy0:RX
[ 1734.373805] Registered led device: iwl-phy0:TX
[ 1734.419659] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1734.484964] wlan1: direct probe to AP 00:11:24:5c:12:c3 try 1
[ 1734.684380] wlan1: direct probe to AP 00:11:24:5c:12:c3 try 2
[ 1734.873069] wlan1 direct probe responded
[ 1734.873079] wlan1: authenticate with AP 00:11:24:5c:12:c3
[ 1734.874843] wlan1: authenticated
[ 1734.874851] wlan1: associate with AP 00:11:24:5c:12:c3
[ 1734.876967] wlan1: RX AssocResp from 00:11:24:5c:12:c3 (capab=0x401 status=0 aid=2)
[ 1734.876973] wlan1: associated
[ 1734.898922] phy0: failed to restore operational channel after scan
[ 1734.901359] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 1734.901650] wlan1: disassociating by local choice (reason=3)
[ 1745.800182] wlan1: no IPv6 routers present
[ 1788.921683] wlan1: authenticate with AP 00:1d:7e:d5:1e:d8
[ 1788.924510] wlan1: authenticated
[ 1788.924520] wlan1: associate with AP 00:1d:7e:d5:1e:d8
[ 1788.928628] wlan1: RX AssocResp from 00:1d:7e:d5:1e:d8 (capab=0x411 status=0 aid=1)
[ 1788.928636] wlan1: associated
[ 2423.820372] CE: hpet increasing min_delta_ns to 50624 nsec
[ 2696.309438] CE: hpet increasing min_delta_ns to 75936 nsec
[ 2699.921515] CE: hpet increasing min_delta_ns to 113904 nsec
[ 2700.249289] CE: hpet increasing min_delta_ns to 170856 nsec
[ 2700.978699] CE: hpet increasing min_delta_ns to 256284 nsec
[ 3288.168902] input: MoGo Mouse X54 as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/bluetooth/hci0/hci0:12/input12
[ 3288.216327] generic-bluetooth 0005:0A5C:0001.0004: input,hidraw3: BLUETOOTH HID v1.29 Mouse [MoGo Mouse X54] on 00:22:69:CF:49:75
[ 4220.710715] tg3: eth0: Link is up at 1000 Mbps, full duplex.
[ 4220.710721] tg3: eth0: Flow control is on for TX and on for RX.
[ 4220.712663] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 4230.722089] eth0: no IPv6 routers present
[ 4421.205811] input: MoGo Mouse X54 as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/bluetooth/hci0/hci0:11/input13
[ 4421.249256] generic-bluetooth 0005:0A5C:0001.0005: input,hidraw4: BLUETOOTH HID v1.29 Mouse [MoGo Mouse X54] on 00:22:69:CF:49:75
[ 4885.523598] iwlagn: Radio Frequency Kill Switch is On:
[ 4885.523603] Kill switch must be turned off for wireless networking to work.
[ 4885.526328] atkbd.c: Unknown key pressed (translated set 2, code 0xf1 on isa0060/serio0).
[ 4885.526334] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known.
[ 4885.539646] atkbd.c: Unknown key released (translated set 2, code 0xf1 on isa0060/serio0).
[ 4885.539654] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known.
[ 4885.753114] usb 4-1: USB disconnect, address 2
[ 4885.753762] btusb_intr_complete: hci0 urb ffff88013e405d80 failed to resubmit (19)
[ 4885.753780] btusb_bulk_complete: hci0 urb ffff88013e405540 failed to resubmit (19)
[ 4885.754787] btusb_bulk_complete: hci0 urb ffff88013e405000 failed to resubmit (19)
[ 4885.759471] btusb_send_frame: hci0 urb ffff88011e0a1540 submission failed
[ 4889.620409] wlan1: No ProbeResp from current AP 00:1d:7e:d5:1e:d8 - assume out of range
[ 4889.633417] iwlagn: Error sending REPLY_ADD_STA: enqueue_hcmd failed: -5
[ 4889.633430] mac80211-phy0: failed to remove key (0, 00:1d:7e:d5:1e:d8) from hardware (-5)
[ 4889.633490] iwlagn: Error sending REPLY_ADD_STA: enqueue_hcmd failed: -5
[ 4889.633497] mac80211-phy0: failed to remove key (1, ff:ff:ff:ff:ff:ff) from hardware (-5)
[ 4891.164280] iwlagn: MAC is in deep sleep!
[ 4891.164457] iwlagn: MAC is in deep sleep!
[ 4891.164632] iwlagn: MAC is in deep sleep!
[ 4891.164890] iwlagn: MAC is in deep sleep!
[ 4974.491753] atkbd.c: Unknown key pressed (translated set 2, code 0xf1 on isa0060/serio0).
[ 4974.491759] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known.
[ 4974.501600] atkbd.c: Unknown key released (translated set 2, code 0xf1 on isa0060/serio0).
[ 4974.501607] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known.
[ 4975.273390] usb 4-1: new full speed USB device using uhci_hcd and address 4
[ 4975.448591] usb 4-1: configuration #1 chosen from 1 choice
[ 4976.103820] Registered led device: iwl-phy0:radio
[ 4976.103858] Registered led device: iwl-phy0:assoc
[ 4976.103893] Registered led device: iwl-phy0:RX
[ 4976.103927] Registered led device: iwl-phy0:TX
[ 4976.149958] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 4976.200002] wlan1: direct probe to AP 00:0f:3d:3b:22:a4 try 1
[ 4976.396223] wlan1: direct probe to AP 00:0f:3d:3b:22:a4 try 2
[ 4976.596205] wlan1: direct probe to AP 00:0f:3d:3b:22:a4 try 3
[ 4976.800055] wlan1: direct probe to AP 00:0f:3d:3b:22:a4 timed out
[ 5004.408469] input: MoGo Mouse X54 as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/bluetooth/hci0/hci0:11/input14
[ 5004.452232] generic-bluetooth 0005:0A5C:0001.0006: input,hidraw5: BLUETOOTH HID v1.29 Mouse [MoGo Mouse X54] on 00:22:69:CF:49:75
[ 5006.759919] wlan1: authenticate with AP 00:1d:7e:d5:1e:d8
[ 5006.764165] wlan1: authenticated
[ 5006.764174] wlan1: associate with AP 00:1d:7e:d5:1e:d8
[ 5006.768160] wlan1: RX AssocResp from 00:1d:7e:d5:1e:d8 (capab=0x411 status=0 aid=1)
[ 5006.768168] wlan1: associated
[ 5006.801813] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 5017.304285] wlan1: no IPv6 routers present
[ 5032.186459] wlan1 direct probe responded
[ 5032.186469] wlan1: authenticate with AP 00:1d:7e:d5:1e:d8
[ 5032.188437] wlan1: authenticated
[ 5032.188443] wlan1: associate with AP 00:1d:7e:d5:1e:d8
[ 5032.196170] wlan1: RX ReassocResp from 00:1d:7e:d5:1e:d8 (capab=0x411 status=0 aid=1)
[ 5032.196176] wlan1: associated
[ 5040.177266] wlan1: deauthenticated
[ 5040.190183] iwlagn: index 0 not used in uCode key table.
[ 5041.176068] wlan1: direct probe to AP 00:1d:7e:d5:1e:d8 try 1
[ 5041.377092] wlan1: direct probe to AP 00:1d:7e:d5:1e:d8 try 2
[ 5041.577553] wlan1: direct probe to AP 00:1d:7e:d5:1e:d8 try 3
[ 5041.612210] wlan1 direct probe responded
[ 5041.612221] wlan1: authenticate with AP 00:1d:7e:d5:1e:d8
[ 5041.614185] wlan1: authenticated
[ 5041.614192] wlan1: associate with AP 00:1d:7e:d5:1e:d8
[ 5041.617980] wlan1: RX ReassocResp from 00:1d:7e:d5:1e:d8 (capab=0x411 status=0 aid=1)
[ 5041.617987] wlan1: associated

```

---

### Post by raphoun on 2009-04-14
> **SyberKowboy said:**
> Toggling switch on then off seems to get the wifi back on for me but the issue I've been having lately with the new kernels is that both the iwlagn and Broadcomm STA drivers connect and work fine for some random period of time then drop to a 1 Mb/s connection. Can't figure it out. Last build (same hardware) I threw some commands at it and go another driver install (don't recall the name) but it was sort of stable.



Yes for me too,  my 4965 agn works bad on jaunty, there are a lot of latence time on firefox that I don't have with ethernet.
And some time my connection drop to 1mb/s (and my 1080p stream freeze...)
It's very disturbing

---

### Post by SyberKowboy on 2009-04-14
I was doing a little more testing last night and I found something very odd. I use an external BT mouse that fits in my PCMCIA slot. It's a slick little devices, anyway the 4965 will only connect to my router (or any router) if the mouse is connected. It's wierd I know but for some reason the wifi only works when the bluetooth is connected. If I stop using the mouse the wifi stalls when the mouse times out. If I re-establish the connection with the mouse the wifi starts working again. I hope this helps someone figure out how to fix it.

---

### Post by Reiger on 2009-04-14
A random thought: you wouldn't happen to have Intrepid backports installed on your system? Try removing those in favour of:
[list]
[*]linux-backports-modules-jaunty
[*]linux-backports-modules-jaunty-generic
[/list]

---

### Post by SyberKowboy on 2009-04-14
I am using all the Jaunty package sources and this was a brand new install. I'm very confused by the issue. I might try a different BroadComm chipset and see if I have better luck with it.

---

### Post by jblackhall on 2009-04-14
> **Melk79 said:**
> At startup I received this message (not sure of any correlation): User's $HOME/.drmc file is being ignored.  This prevents the default session and language from being saved. File should be owned by user and have 644 permissions.  User's $HOME directory must be owned by user and not writable by other users.

sudo chmod 700 /home/steve

(assuming your user is "steve").

(via Alan Pope: [https://answers.launchpad.net/ubuntu/+question/7296](https://answers.launchpad.net/ubuntu/+question/7296) )

This happened to me last week.  It happened to me when I attempted to copy my entire home folder to another location for backup (external hard drive), but I think there's multiple reasons it could happen.

Also, in regards to your original problem, I see you have Vista installed.  Does hibernating/suspending and then waking in Vista fix anything?  If there's a bug in the kernel, perhaps Vista can "wake" your card?

---

### Post by jblackhall on 2009-04-14
> **jblackhall said:**
> sudo chmod 700 /home/steve

(assuming your user is "steve").

(via Alan Pope: [https://answers.launchpad.net/ubuntu/+question/7296](https://answers.launchpad.net/ubuntu/+question/7296) )

This happened to me last week.  It happened to me when I attempted to copy my entire home folder to another location for backup (external hard drive), but I think there's multiple reasons it could happen.

Also, in regards to your original problem, I see you have Vista installed.  Does hibernating/suspending and then waking in Vista fix anything?  If there's a bug in the kernel, perhaps Vista can "wake" your card?

Actually I think by default, Ubuntu uses 755 permissions for the home dir, not 700.  so you might want to do:
sudo chmod 755 /home/steve
(assuming your username is steve)

---

