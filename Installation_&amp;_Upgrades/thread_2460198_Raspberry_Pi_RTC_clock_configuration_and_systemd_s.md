---
title: "Raspberry Pi RTC clock configuration and systemd service"
date: 2021-04-04
forum: Installation &amp; Upgrades
---

### Post by paul-onolan on 2021-04-04
I'm trying to get Ubuntu Core 20.04 working with a DS3132 RTC on a Raspberry Pi 3/4. Have done this without difficulty using RaspiOS in the past. I've got it detecting the hardware but systemd service is not working as expected. So far the most useful things I've found are:

[LIST]
[*][https://spellfoundry.com/docs/setting-up-the-real-time-clock-on-raspbian-jessie-or-stretch/](https://spellfoundry.com/docs/setting-up-the-real-time-clock-on-raspbian-jessie-or-stretch/) 
[*][https://www.raspberrypi.org/forums/viewtopic.php?p=1320052](https://www.raspberrypi.org/forums/viewtopic.php?p=1320052) 
[*][https://www.willhughes.name/post/ds3231_raspi3/#an-2](https://www.willhughes.name/post/ds3231_raspi3/#an-2) 
[/LIST]
 First contains instructions on installing i2c-tools, which are not included in Ubuntu, and on editing /lib/udev/hwclock-set. The systemd unit in the second link doesn't work (and the hardware isn't detected). With that in the 3rd link the hardware is detected and readable but the systemd service doesn't work. Pointers / advice welcome. Thanks.

My /boot/config.sys
```

dtparam=i2c_arm=on
dtoverlay=i2c-rtc,ds3231

```

Modprobe results
```
ubuntu@pi4:~$ sudo modprobe rtc-ds1307
ubuntu@pi4:~$ sudo modprobe rtc-ds3231
modprobe: FATAL: Module rtc-ds3231 not found in directory /lib/modules/5.4.0-1032-rasp

```

Not sure how to interpret this. There's a **ds3232** driver in both /lib/modules/5.4.0-1028-raspi/kernel/drivers/rtc and /lib/modules/5.4.0-1032-raspi/kernel/drivers/rtc :confused:

---

### Post by ActionParsnip on 2021-04-05
Use TAB to autocomplete the module names. Stop after 'rtc' and press TAB to see what is available

---

### Post by paul-onolan on 2021-04-05
```
ubuntu@ubuntu:/lib/modules/5.4.0-1032-raspi/kernel/drivers/rtc$ sudo modprobe rtc-
rtc-88pm80x          rtc-cadence          rtc-ds1307           rtc-ds1742           rtc-isl12022         rtc-max6900          rtc-mcp795           rtc-pcf8523          rtc-rp5c01           rtc-rx8025           rtc-tps80031
rtc-88pm860x         rtc-cpcap            rtc-ds1343           rtc-ds2404           rtc-isl1208          rtc-max6902          rtc-msm6242          rtc-pcf85363         rtc-rs5c348          rtc-rx8581           rtc-v3020
rtc-ab3100           rtc-cros-ec          rtc-ds1347           rtc-ds3232           rtc-lp8788           rtc-max6916          rtc-mt6397           rtc-pcf8563          rtc-rs5c372          rtc-s35390a          rtc-wm831x
rtc-ab-b5ze-s3       rtc-da9052           rtc-ds1374           rtc-efi              rtc-m41t80           rtc-max77686         rtc-palmas           rtc-pcf8583          rtc-rv3028           rtc-s5m              rtc-wm8350
rtc-ab-eoz9          rtc-da9055           rtc-ds1390           rtc-em3027           rtc-m41t93           rtc-max8907          rtc-pcap             rtc-pl030            rtc-rv3029c2         rtc-sd3078           rtc-x1205
rtc-abx80x           rtc-da9063           rtc-ds1511           rtc-fm3130           rtc-m41t94           rtc-max8925          rtc-pcf2123          rtc-r7301            rtc-rv8803           rtc-snvs             rtc-zynqmp
rtc-as3722           rtc-ds1286           rtc-ds1553           rtc-ftrtc010         rtc-m48t35           rtc-max8997          rtc-pcf2127          rtc-r9701            rtc-rx4581           rtc-stk17ta8         
rtc-bq32k            rtc-ds1302           rtc-ds1672           rtc-hid-sensor-time  rtc-m48t59           rtc-max8998          rtc-pcf50633         rtc-rc5t583          rtc-rx6110           rtc-tps6586x         
rtc-bq4802           rtc-ds1305           rtc-ds1685           rtc-hym8563          rtc-m48t86           rtc-mc13xxx          rtc-pcf85063         rtc-rk808            rtc-rx8010           rtc-tps65910 

```

I've already looked at this. Not clear what you're suggesting. That I should use rtc-ds3232? As far as I can [ascertain]("https://www.maximintegrated.com/en/design/technical-documents/app-notes/5/5143.html") it's "similar" to the ds3132.

---

### Post by paul-onolan on 2021-04-05
I checked a raspbian installation and found it also had a ds3232 driver, not a ds3132. Strange to find almost no references online to the ds3232 -- just this [one]("https://www.raspberrypi.org/forums/viewtopic.php?t=16218&start=100") from someone else having systemd issues. And [this]("https://www.raspberrypi.org/forums/viewtopic.php?f=131&t=285762&p=1729223&hilit=ubuntu+rtc#p1729223") from someone else unable to get things working with Ubuntu 20.04.

It doesn't seem to matter whether the device is identified in /boot/config.sys as a ds3132 or ds3232. The hwclock-start.service with > ExecStartPre=/bin/bash -c "echo ds1307 0x68 | tee /sys/class/i2c-adapter/i2c-1/new_device" seems to cause it to be recognized as a ds1307. I'm not clear whether I need to have something loaded in /etc/modules or not. Currently I don't and > sudo timedatectl status shows that the system clock is synchronized.

I'd still like to find clear and current instructions on getting things working, with explanations. For Ubuntu. With SystemD. A lot of what's findable online seems raspbian-specific and out of date. I'm not even sure I need to run hwclock-start at all (I've read that systemd-timesyncd service, which is running, will update the RTC automatically); still poking at this.

---

