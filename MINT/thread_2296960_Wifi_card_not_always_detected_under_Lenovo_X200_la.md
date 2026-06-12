---
title: "Wifi card not always detected under Lenovo X200 laptop"
date: 2015-09-30
forum: MINT
---

### Post by stepnjump1 on 2015-09-30
Hi,

I'm using Linux Mint Cinnamon 64bits. Mostly it works flawlessly but there is something really weird that happens.
This happened with previous versions of Linux Mint as well.
I post here because Linux Mint is a subset of Ubuntu so I thought someone might be able to help.

When the Wifi light doesn,t turn on after booting up, I often times check the ifconfig. The wlan0 is not showing at all. It's not due to rfkill.
When that happens, I reboot in windows7 (dual boot), then wifi comes on so I will reboot again and lo and behold, it will finally come up under Linux Mint.

An other way to bring it back up is by booting up with a wifi dongle. Whatever it does, it revives wifi card. Ifconfig shows now both wlan0 and wlan1.
Then I disconnect the Wifi dongle and wlan0 takes over the connection.

Go figure!

Maybe you guys programmers might look into this for future releases?
If you require more information, please kindly ask and I shall provide it to you.

Thanks for your help

Step

---

### Post by howefield on 2015-09-30
Thread moved to the "*MINT*" forum.

---

### Post by jeremy31 on 2015-10-01
What does this command in terminal return ```
lspci -nnk | grep -iA2 net
```

---

### Post by stepnjump1 on 2015-10-04
Hi Jeremy,

Sorry for not responding to you before. But finally, here it is. Thanks for your help.

00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
    Subsystem: Lenovo Device [17aa:20ee]
    Kernel driver in use: e1000e

---

### Post by jeremy31 on 2015-10-04
Is WLAN enabled in BIOS?  It wasn't detected when you ran the lspci command

---

### Post by stepnjump1 on 2015-10-05
Jeremy, I just checked in the BIOS and yes, it's ON

---

### Post by jeremy31 on 2015-10-07
I would remove the wifi card from the computer and reinstall to see if it solves the issue

---

### Post by stepnjump1 on 2015-10-13
Hi Jeremy,

Ok, I will try it in a few days because it requires to loosen a lot of screws. I will report back once I find out.

thank you.

---

