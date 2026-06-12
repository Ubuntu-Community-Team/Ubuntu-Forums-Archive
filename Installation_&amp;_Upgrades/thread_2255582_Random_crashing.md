---
title: "Random crashing"
date: 2014-12-06
forum: Installation &amp; Upgrades
---

### Post by cov on 2014-12-06
I've been having an issue recently where my machine suddenly locks up with excessive fan noise.

On two occasions I logged in immediately afterward to check the log files and these are the 'tail' output of the ones written to just before the crash.

/var/www/kern.log:
```
Dec  2 05:01:31 Threepwood kernel: [393278.788682] wlan0: authenticate with 6c:b0:ce:37:4d:08
Dec  2 05:01:31 Threepwood kernel: [393278.799049] wlan0: send auth to 6c:b0:ce:37:4d:08 (try 1/3)
Dec  2 05:01:31 Threepwood kernel: [393278.801800] wlan0: authenticated
Dec  2 05:01:31 Threepwood kernel: [393278.801943] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
Dec  2 05:01:31 Threepwood kernel: [393278.801948] wlan0: waiting for beacon from 6c:b0:ce:37:4d:08
Dec  2 05:01:31 Threepwood kernel: [393278.858222] wlan0: associate with 6c:b0:ce:37:4d:08 (try 1/3)
Dec  2 05:01:31 Threepwood kernel: [393278.861109] wlan0: RX AssocResp from 6c:b0:ce:37:4d:08 (capab=0x411 status=0 aid=1)
Dec  2 05:01:31 Threepwood kernel: [393278.864246] wlan0: associated
Dec  2 05:01:31 Threepwood kernel: [393278.864309] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

Dec  6 08:24:54 Threepwood kernel: [22825.630427] HDMI: invalid ELD buf size -1
Dec  6 08:24:54 Threepwood kernel: [22825.930729] HDMI: invalid ELD buf size -1
Dec  6 08:24:54 Threepwood kernel: [22825.930746] HDMI: invalid ELD buf size -1
Dec  6 08:24:54 Threepwood kernel: [22825.930751] HDMI: invalid ELD buf size -1
Dec  6 08:24:54 Threepwood kernel: [22825.930755] HDMI: invalid ELD buf size -1
Dec  6 08:24:55 Threepwood kernel: [22826.231063] HDMI: invalid ELD buf size -1
Dec  6 08:24:55 Threepwood kernel: [22826.231080] HDMI: invalid ELD buf size -1
Dec  6 08:24:55 Threepwood kernel: [22826.231086] HDMI: invalid ELD buf size -1
Dec  6 08:24:55 Threepwood kernel: [22826.231090] HDMI: invalid ELD buf size -1

```

/var/log/syslog:
```
Dec  2 07:20:01 Threepwood CRON[17900]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec  2 07:30:01 Threepwood CRON[18060]: (root) CMD (start -q anacron || :)
Dec  2 07:30:01 Threepwood anacron[18063]: Anacron 2.3 started on 2014-12-02
Dec  2 07:30:01 Threepwood anacron[18063]: Will run job `cron.daily' in 5 min.
Dec  2 07:30:01 Threepwood anacron[18063]: Jobs will be executed sequentially
Dec  2 07:35:01 Threepwood anacron[18063]: Job `cron.daily' started
Dec  2 07:35:01 Threepwood anacron[18125]: Updated timestamp for job `cron.daily' to 2014-12-02
Dec  2 07:39:01 Threepwood CRON[18211]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Dec  2 07:40:01 Threepwood CRON[18226]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)

Dec  6 08:24:54 Threepwood kernel: [22825.630427] HDMI: invalid ELD buf size -1
Dec  6 08:24:54 Threepwood kernel: [22825.930729] HDMI: invalid ELD buf size -1
Dec  6 08:24:54 Threepwood kernel: [22825.930746] HDMI: invalid ELD buf size -1
Dec  6 08:24:54 Threepwood kernel: [22825.930751] HDMI: invalid ELD buf size -1
Dec  6 08:24:54 Threepwood kernel: [22825.930755] HDMI: invalid ELD buf size -1
Dec  6 08:24:55 Threepwood kernel: [22826.231063] HDMI: invalid ELD buf size -1
Dec  6 08:24:55 Threepwood kernel: [22826.231080] HDMI: invalid ELD buf size -1
Dec  6 08:24:55 Threepwood kernel: [22826.231086] HDMI: invalid ELD buf size -1
Dec  6 08:24:55 Threepwood kernel: [22826.231090] HDMI: invalid ELD buf size -1

```

/var/log/Xorg.0.log:
```
[346431.991] reporting 5 6 12 89
[346432.048] reporting 5 6 12 89
[346432.111] reporting 5 6 12 89
[348906.863] reporting 5 6 12 89
[350622.427] reporting 5 6 12 89
[367349.512] (II) intel(0): switch to mode 1366x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[368375.098] (II) intel(0): switch to mode 1366x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[392466.720] reporting 5 6 12 89
[400598.669] (II) intel(0): switch to mode 1366x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none

[ 22797.062] reporting 5 6 12 89
[ 22797.062] reporting 5 6 12 89
[ 22797.063] reporting 5 6 12 89
[ 22797.063] reporting 5 6 12 89
[ 22797.063] reporting 5 6 12 89
[ 22797.064] reporting 5 6 12 89
[ 22797.065] reporting 5 6 12 89
[ 22799.024] reporting 5 6 12 89
[ 22799.042] (II) intel(0): switch to mode 1366x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
```

Obviously there was a crash on the second of December and one this morning, but I can't see too much in common.

I'm using XUbuntu, 14.04 upgrade, AMD64.

---

### Post by veddox on 2014-12-06
If you say excessive fan noises, I would rather guess at a hardware than a software problem (broken cooling system, dust clog-up, ...). Although having said that, were you running any heavy programs just before the crashes?

And could you give us your machine's specs?

---

### Post by cov on 2014-12-07
Thanks for the response.

I would say that the excessive fan noise is symptomatic of the demands being made of the hardware, than the hardware itself.

Specs:

```
dave@Threepwood:~$ sudo lshw -short
H/W path        Device      Class          Description
======================================================
                            system         HuronRiver Platform (System SKUNumber)
/0                          bus            Emerald Lake
/0/0                        memory         128KiB BIOS
/0/30                       processor      Intel(R) Core(TM) i5-2450M CPU @ 2.50GHz
/0/30/31                    memory         64KiB L1 cache
/0/30/32                    memory         256KiB L2 cache
/0/30/33                    memory         3MiB L3 cache
/0/34                       memory         8GiB System Memory
/0/34/0                     memory         4GiB SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
/0/34/1                     memory         DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Dat
/0/34/2                     memory         4GiB SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
/0/34/3                     memory         DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Dat
/0/100                      bridge         2nd Generation Core Processor Family DRAM Controller
/0/100/1                    bridge         Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
/0/100/1/0                  display        GF108M [GeForce GT 540M]
/0/100/1/0.1                multimedia     GF108 High Definition Audio Controller
/0/100/2                    display        2nd Generation Core Processor Family Integrated Graphics Controller
/0/100/16                   communication  6 Series/C200 Series Chipset Family MEI Controller #1
/0/100/1a                   bus            6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
/0/100/1b                   multimedia     6 Series/C200 Series Chipset Family High Definition Audio Controller
/0/100/1c                   bridge         6 Series/C200 Series Chipset Family PCI Express Root Port 1
/0/100/1c.1                 bridge         6 Series/C200 Series Chipset Family PCI Express Root Port 2
/0/100/1c.1/0   wlan0       network        Centrino Wireless-N 1000 [Condor Peak]
/0/100/1c.3                 bridge         6 Series/C200 Series Chipset Family PCI Express Root Port 4
/0/100/1c.3/0   eth0        network        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
/0/100/1d                   bus            6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
/0/100/1f                   bridge         HM65 Express Chipset Family LPC Controller
/0/100/1f.2                 storage        6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller
/0/100/1f.3                 bus            6 Series/C200 Series Chipset Family SMBus Controller
/0/1            scsi0       storage        
/0/1/0.0.0      /dev/sda    disk           500GB HITACHI HTS54505
/0/1/0.0.0/1    /dev/sda1   volume         200MiB Windows NTFS volume
/0/1/0.0.0/2    /dev/sda2   volume         40GiB Windows NTFS volume
/0/1/0.0.0/3    /dev/sda3   volume         410GiB Extended partition
/0/1/0.0.0/3/5  /dev/sda5   volume         28GiB HPFS/NTFS partition
/0/1/0.0.0/3/6  /dev/sda6   volume         39GiB Linux filesystem partition
/0/1/0.0.0/3/7  /dev/sda7   volume         47GiB Linux filesystem partition
/0/1/0.0.0/3/8  /dev/sda8   volume         200MiB Linux filesystem partition
/0/1/0.0.0/3/9  /dev/sda9   volume         260GiB Linux filesystem partition
/0/1/0.0.0/3/a  /dev/sda10  volume         9537MiB Linux swap / Solaris partition
/0/1/0.0.0/4    /dev/sda4   volume         14GiB Windows NTFS volume
/0/2            scsi4       storage        
/0/2/0.0.0      /dev/cdrom  disk           DVD RW AD-7710H
/0/3            scsi6       storage        
/0/3/0.0.0      /dev/sdb    disk           xD/SD/M.S.
/0/3/0.0.0/0    /dev/sdb    disk           
/1                          power          Smart Battery
/2                          power          TBD by ODM

```

I wasn't running anything particularly onerous before the crash, but I generally have a lot open at any one time.

---

### Post by veddox on 2014-12-10
Hm, your specs should be good enough for just about any job short of heavy-duty rendering...

I'm afraid I don't have much of an idea what could have caused those crashes :-( Maybe somebody else could help?

The only thing I'd suggest again is to check your machine for dust build-up, seeing as you're also in Africa (although the problem might not be quite as severe in SA as it is further north).

---

