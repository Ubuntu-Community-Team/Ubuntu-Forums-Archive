---
title: "Delay in startup / ffy1 login to start GUI"
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by Dondorp on 2010-12-29
Hi,

I've recently installed ubuntu 10.10 again and when I boot it starts in ffy1 console, in which I need to login.
After the login in console version it will display the error
> Dec 29 13:31:41 Highland-Laptop kernel: [  138.182540] tpm_tis 00:0a: tpm_transmit: tpm_send: error -62
after this it takes ~30 seconds till the normal graphical login screen displays.
I've searching the forum about this problem but haven't encountered the solution anywhere nor the problem itself.
And yes I do see the disk errors but that would be during the login on the graphical screen so I'm just going to ignore that till I found the solution for this first.

So, if anyone could help me with this I'd be very happy.
Also if more information should be supplied I'd be happy to provide it. 

> Edit 1:
using "startx" will start the GUI but will relogin after the same period as without using the command (so logs out this session)
using "sudo service gdm start" does the same.

Both though work, but it isn't a proper workaround, there might be a delay somewhere in the gdm service.
Any logs on this one?

Linux kernell version:
> 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux

syslog (till startup, "grep error syslog.1"):
> Dec 29 13:29:40 Highland-Laptop kernel: [   16.226805] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
Dec 29 13:29:40 Highland-Laptop NetworkManager[617]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Dec 29 13:29:42 Highland-Laptop kernel: [   18.475958] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
Dec 29 13:31:41 Highland-Laptop kernel: [  138.182540] tpm_tis 00:0a: tpm_transmit: tpm_send: error -62
Dec 29 13:32:53 Highland-Laptop kernel: [  209.874492] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
Dec 29 13:32:58 Highland-Laptop NetworkManager[617]: <error> [1293625978.790767] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Dec 29 13:32:58 Highland-Laptop NetworkManager[617]: <error> [1293625978.881436] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Dec 29 13:33:17 Highland-Laptop kernel: [  233.288470] end_request: I/O error, dev sr0, sector 64
Dec 29 13:33:17 Highland-Laptop kernel: [  233.399663] end_request: I/O error, dev sr0, sector 1024
Dec 29 13:33:17 Highland-Laptop kernel: [  233.442143] end_request: I/O error, dev sr0, sector 646012
Dec 29 13:33:17 Highland-Laptop kernel: [  233.484624] end_request: I/O error, dev sr0, sector 644988
Dec 29 13:33:17 Highland-Laptop kernel: [  233.527117] end_request: I/O error, dev sr0, sector 646008
Dec 29 13:33:17 Highland-Laptop kernel: [  233.569594] end_request: I/O error, dev sr0, sector 644984
Dec 29 13:33:17 Highland-Laptop kernel: [  233.612118] end_request: I/O error, dev sr0, sector 646004
Dec 29 13:33:17 Highland-Laptop kernel: [  233.654600] end_request: I/O error, dev sr0, sector 644980
Dec 29 13:33:17 Highland-Laptop kernel: [  233.697064] end_request: I/O error, dev sr0, sector 645412
Dec 29 13:33:17 Highland-Laptop kernel: [  233.739552] end_request: I/O error, dev sr0, sector 644388
Dec 29 13:33:17 Highland-Laptop kernel: [  233.782048] end_request: I/O error, dev sr0, sector 645404
Dec 29 13:33:17 Highland-Laptop kernel: [  233.824531] end_request: I/O error, dev sr0, sector 644380
Dec 29 13:33:17 Highland-Laptop kernel: [  233.867046] end_request: I/O error, dev sr0, sector 2048
Dec 29 13:33:17 Highland-Laptop kernel: [  233.909498] end_request: I/O error, dev sr0, sector 1248
Dec 29 13:33:17 Highland-Laptop kernel: [  233.952005] end_request: I/O error, dev sr0, sector 646012
Dec 29 13:33:17 Highland-Laptop kernel: [  233.994485] end_request: I/O error, dev sr0, sector 644764
Dec 29 13:33:17 Highland-Laptop kernel: [  234.036984] end_request: I/O error, dev sr0, sector 646008
Dec 29 13:33:17 Highland-Laptop kernel: [  234.079463] end_request: I/O error, dev sr0, sector 644760
Dec 29 13:33:17 Highland-Laptop kernel: [  234.121963] end_request: I/O error, dev sr0, sector 644768
Dec 29 13:33:17 Highland-Laptop kernel: [  234.164441] end_request: I/O error, dev sr0, sector 646004
Dec 29 13:33:17 Highland-Laptop kernel: [  234.206964] end_request: I/O error, dev sr0, sector 644756
Dec 29 13:33:18 Highland-Laptop kernel: [  234.249409] end_request: I/O error, dev sr0, sector 645272
Dec 29 13:33:18 Highland-Laptop kernel: [  234.291933] end_request: I/O error, dev sr0, sector 644024
Dec 29 13:33:18 Highland-Laptop kernel: [  234.334379] end_request: I/O error, dev sr0, sector 645264
Dec 29 13:33:18 Highland-Laptop kernel: [  234.376863] end_request: I/O error, dev sr0, sector 644016
Dec 29 13:33:18 Highland-Laptop kernel: [  234.419356] end_request: I/O error, dev sr0, sector 2496
Dec 29 13:33:18 Highland-Laptop kernel: [  234.461842] end_request: I/O error, dev sr0, sector 1248
Dec 29 13:33:18 Highland-Laptop kernel: [  234.504331] end_request: I/O error, dev sr0, sector 2496
Dec 29 13:33:44 Highland-Laptop kernel: [  260.430038] tpm_tis 00:0a: tpm_transmit: tpm_send: error -62
Dec 29 13:35:44 Highland-Laptop kernel: [  381.180049] tpm_tis 00:0a: tpm_transmit: tpm_send: error -62


Hardware specs:
> Zepto Znote 6625WD
Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz 64 bits
G84 [GeForce 8600M GT]
2GB Internal memory: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
NetLink BCM5787M Gigabit Ethernet PCI Express
82801H (ICH8 Family) HD Audio Controller

---

### Post by Dondorp on 2010-12-30
Shameless bump, problem still here.

---

### Post by risto.pekkala on 2011-01-16
Same thing here. Same hardware (Zepto 6224w). 
Being lazy I only do "sudo kdm". Works until a solution is found.
This is the first time I found a report on this.

I also have problem with the Intel soundchip 82801H (ICH8-family).
Only speakers work. Only "Internal sound analog stereo" in Kmix.
I have no idea what to use for "snd-hda-intel model=" in alsa-base.conf.

---

### Post by risto.pekkala on 2011-01-16
Same thing here. Same hardware (Zepto 6224w). 
Being lazy I only do "sudo kdm". Works until a solution is found.
This is the first time I found a report on this.

I also have problem with the Intel soundchip 82801H (ICH8-family).
Only speakers work. Only "Internal sound analog stereo" in Kmix.
I have no idea what to use for "snd-hda-intel model=" in alsa-base.conf.

---

