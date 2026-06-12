---
title: "bsnl 3g"
date: 2010-08-07
forum: Installation &amp; Upgrades
---

### Post by aashleshc on 2010-08-07
i have recently bought a bsnl 3g data card (usb port), and i followed this post for installing it,
[http://duopetalflower.blogspot.com/2010/05/configuring-bsnl-evdo-capitel-3g-usb.html#comment-form](http://duopetalflower.blogspot.com/2010/05/configuring-bsnl-evdo-capitel-3g-usb.html#comment-form)

i was first stuck at the fact that i already had a file in usb_modeswitch with 1c9e:f000 as header! the i deleted that file and changed it to what i need. 

now in dmesg | -20 i get the following error

[   17.397256] CPU2 attaching sched-domain:
[   17.397257]  domain 0: span 0,2 level SIBLING
[   17.397258]   groups: 2 (cpu_power = 589) 0 (cpu_power = 589)
[   17.397262]   domain 1: span 0-3 level MC
[   17.397263]    groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[   17.397267] CPU3 attaching sched-domain:
[   17.397268]  domain 0: span 1,3 level SIBLING
[   17.397270]   groups: 3 (cpu_power = 589) 1 (cpu_power = 589)
[   17.397273]   domain 1: span 0-3 level MC
[   17.397275]    groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[   17.449160] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   23.632493] eth1: no IPv6 routers present
[   24.483977] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[  209.916396] input: Dell BT Travel Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4.3/2-1.4.3:1.0/bluetooth/hci0/hci0:11/input12
[  209.916529] generic-bluetooth 0005:046D:B006.0003: input,hidraw1: BLUETOOTH HID v1.24 Mouse [Dell BT Travel Mouse] on C4:46:19:EA:B9:3A
[  255.436749] usb 2-1.2: new high speed USB device using ehci_hcd and address 7
[  255.549550] usb 2-1.2: configuration #1 chosen from 1 choice
[  255.553814] usbserial_generic 2-1.2:1.0: generic converter detected
[  255.553920] usb 2-1.2: generic converter now attached to ttyUSB0
[ 1111.515846] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.



i really want this little guy to work..

anyone out there with a solutioin??

---

