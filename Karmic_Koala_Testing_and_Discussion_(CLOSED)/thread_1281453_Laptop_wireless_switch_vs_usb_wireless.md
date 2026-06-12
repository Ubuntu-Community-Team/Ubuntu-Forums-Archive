---
title: "Laptop wireless switch vs usb wireless"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kaar3l on 2009-10-03
I noticed a weird thing today. I have laptop with intel wifi 5100 and i have a rt73 usb wireless reciever. I was inside wifi with 5100 and then plugged in rt73. Then rt73 connected to that same wifi ap. Then I thought that I'll test my rt73, because i modded it's antenna little bit and switched wireless off from laptop wireless hardware switch. 5100 was off and so did go off the rt73. :/
Weird a bit :)
Here is a bit of dmesg:
I plugged in the rt73 stick:
```
[ 1502.040535] udev: renamed network interface wlan1 to wlan2
[ 1502.044503] rt73usb 2-1:1.0: firmware: requesting rt73.bin
[ 1502.163517] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 1510.048187] wlan2: authenticate with AP 02:22:6b:95:7d:ab
[ 1510.049892] wlan2: authenticated
[ 1510.049901] wlan2: associate with AP 02:22:6b:95:7d:ab
[ 1510.052485] wlan2: RX AssocResp from 02:22:6b:95:7d:ab (capab=0x411 status=0 aid=2)
[ 1510.052493] wlan2: associated
[ 1510.071775] ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready
[ 1520.941054] wlan2: no IPv6 routers present
[ 1525.256616] atkbd.c: Unknown key pressed (translated set 2, code 0xf1 on isa0060/serio0).
[ 1525.256625] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known.
[ 1525.264062] atkbd.c: Unknown key released (translated set 2, code 0xf1 on isa0060/serio0).
[ 1525.264071] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known.

```
I switched the wireless switch
```

[ 1525.273182] wlan0: deauthenticating by local choice (reason=3)
[ 1525.708104] wlan2: deauthenticating by local choice (reason=3)
[ 1525.808205] wlan2: disassociating by local choice (reason=3)

```
Now i wanted to do sudo ifconfig wlan2 up, but it doesn't wanna come up.
```

[ 1539.778011] ADDRCONF(NETDEV_UP): wlan2: link is not ready

```

Not a big bug but sometimes can be not peasant. :)

---

### Post by Gourgi on 2009-10-03
sorry for being off-topic but how you modded the antenna and for what purpose you did it? increase signal strength?
i own the same usb adapter and i'd like to know.
thanks in advance :)

---

