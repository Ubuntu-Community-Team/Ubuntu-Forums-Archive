---
title: "How to install ZTE MF193E 3G modem"
date: 2013-12-04
forum: Installation &amp; Upgrades
---

### Post by rajib2ruet on 2013-12-04
Hi,
Having problem installing ZTE MF193E modem in ubuntu 13.04 64bit modem. I am using #lsusb command, then i trying the with #wvdialconf command but show no modem found. It cant create any wvdialconf file in /etc/wvdial.conf file.
what should be done for working this modem in ubuntu OS?
Modem v= 19d2 & p= 1232

Masud

---

### Post by fantab on 2013-12-04
Have tried to get the modem to work with 'network-manager'?

You can read over the following wikipage to see what you are missing:
[URL="https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer"]https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer
[/URL]

---

### Post by rajib2ruet on 2013-12-04
what do you mean by work with 'network-manager' ....will you elaborate that configuration steps?
I have another modem Huawei EG162G that I can configure with 'wvdialconf' configuration as i want to use that modem for SMSServer (using kannel).

---

### Post by fantab on 2013-12-04
> **rajib2ruet said:**
> what do you mean by work with 'network-manager' ....will you elaborate that configuration steps?


Plug in your Modem, on the top-bar click on the Network icon ->Edit Connections->Add->'your modem will be detected->then follow the instructions from the wizard.

Post the output of:
```
lsusb
```

---

### Post by rajib2ruet on 2013-12-04
Follow your steps but modem cannot be detected automatically.
lsusb::
root@masudul-Inspiron-5520:~# lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 004: ID 19d2:2003 ZTE WCDMA Technologies MSM
Bus 003 Device 002: ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp.
Bus 001 Device 004: ID 0c45:644a Microdia
Bus 002 Device 004: ID 0cf3:e004 Atheros Communications, Inc.

---

### Post by fantab on 2013-12-04
Not sure what the problem is. I suggest you wait for someone with a solution to post.
Who is the 'Service Provider'?

Ubuntu uses 'usb-modeswitch' package to manage USB Modems, if the issue is related to 'modeswitch' then following might help:
[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?f=6&t=1201&start=15](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?f=6&t=1201&start=15)
[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=574](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=574)

A good wiki on wvdial:
[https://wiki.archlinux.org/index.php/Wvdial](https://wiki.archlinux.org/index.php/Wvdial)

---

### Post by rajib2ruet on 2013-12-05
Please see the log when i want to install driver software from Telco (Teletalk)::
root@masudul-HP-ProBook-450-G0: /Teletalk/Linuxroot@masudul-HP-ProBook-450-G0:/Teletalk/Linux# ./install.sh 
..................start install.................
*** Check for root...ok...
./zr: error while loading shared libraries: libxml2.so.2: cannot open shared object file: No such file or directory
Get resouse file successfully.
..........delete /etc/udev/rules.d/7-zte-mutil_port_device.rules ok...........
Teletalk_3G/usr/share/applications/Teletalk_3G.desktop
Teletalk_3G/usr/share/pixmaps/Teletalk_3G.png
Teletalk_3G/usr/lib/libphonon.so.4.4.0
Teletalk_3G/usr/lib/libpng12.so.0.49.0
Teletalk_3G/usr/lib/libQtCore.so.4.7.3
Teletalk_3G/usr/lib/libQtGui.so.4.7.3
Teletalk_3G/usr/lib/libpng.so.3.49.0
Teletalk_3G/usr/lib/libQtSql.so.4.7.3
Teletalk_3G/usr/lib/libQtXml.so.4.7.3
Teletalk_3G/usr/lib/libQtDBus.so.4.7.3
Teletalk_3G/usr/lib/libQtNetwork.so.4.7.3
Teletalk_3G/usr/lib/UniSdk.so
Teletalk_3G/usr/lib/MMS_Stack.so
Teletalk_3G/usr/lib/UniDevManager.so
Teletalk_3G/usr/lib/UniVousb.so
Teletalk_3G/usr/lib/UniCodec.so
Teletalk_3G/usr/lib/UniSdk.lib
Teletalk_3G/usr/lib/CoreSDK.so
Teletalk_3G/plugins/imageformats/libqtiff.so
Teletalk_3G/plugins/imageformats/libqgif.so
Teletalk_3G/plugins/imageformats/libqmng.so
Teletalk_3G/plugins/imageformats/libqico.so
Teletalk_3G/plugins/imageformats/libqsvg.so
Teletalk_3G/plugins/imageformats/libqjpeg.so
Teletalk_3G/plugins/codecs/libqcncodecs.so
Teletalk_3G/plugins/codecs/libqkrcodecs.so
Teletalk_3G/plugins/codecs/libqtwcodecs.so
Teletalk_3G/plugins/codecs/libqjpcodecs.so
Teletalk_3G/Help/English/help.html
Teletalk_3G/Data/aplay.sh
Teletalk_3G/Data/launchFirefox.sh
Teletalk_3G/sqldrivers/libqsqlite.so
Teletalk_3G/wirelessconfig/options
Teletalk_3G/wirelessconfig/chat-ztisp
Teletalk_3G/bin/aplay
Teletalk_3G/bin/SameNameSh
Teletalk_3G/bin/Teletalk_3G.conf
Teletalk_3G/bin/7-zte-mutil_port_device.rules
Teletalk_3G/bin/9-cdrom.rules
Teletalk_3G/driver/nm.pp
Teletalk_3G/driver/se
Teletalk_3G/driver/driver_install.run
Teletalk_3G/driver/disselfirefox.pp
Teletalk_3G/pppd/ip-up.local
Teletalk_3G/pppd/ip-down.local
Teletalk_3G/pppd/get_route_info
Teletalk_3G/scripts/delete_username_option.sh
Teletalk_3G/scripts/delete_apn_in_chatscipt.sh
Teletalk_3G/scripts/modify_modem_port.sh
Teletalk_3G/scripts/replace_dial_in_chatscipt.sh
Teletalk_3G/scripts/smart_insert_line_into_file.sh
Teletalk_3G/scripts/add_usepeerdns.sh
Teletalk_3G/scripts/modify_username_option.sh
Teletalk_3G/scripts/copy_file.sh
Teletalk_3G/scripts/delete_usepeerdns.sh
Teletalk_3G/scripts/replace_apn_in_chatscipt.sh
Teletalk_3G/scripts/modify_authrization_option.sh
Teletalk_3G/Sound/call.wav
Teletalk_3G/Sound/offline.wav
Teletalk_3G/Sound/online.wav
Teletalk_3G/Sound/sms.wav
Teletalk_3G/UiFile/MainWindow.ui
Teletalk_3G/UiFile/VoiceRecord.ui
Teletalk_3G/UiFile/Welcome.ui
Teletalk_3G/Config/UUConfig.xml
Teletalk_3G/Config/UUGlobalApn.xml
Teletalk_3G/Config/UULanguageMap.xml
Teletalk_3G/Skin/icon_message_forward_Enable.png
Teletalk_3G/Skin/icon_message_forward_Hover.png
Teletalk_3G/sdk.config.ini
Teletalk_3G/launch-gui.sh
Teletalk_3G/version.ini
Teletalk_3G/config_Icera.ini
Teletalk_3G/UUDb
Teletalk_3G/config.ini
Teletalk_3G/Teletalk_3G
Teletalk_3G/Service.ini
Teletalk_3G/uninstall.sh
Teletalk_3G/UpdateCfg.ini
Teletalk_3G/UpdateInfo.xml
Teletalk_3G/UniSdk.db
Teletalk_3G/Thumbs.db
Teletalk_3G/App.Config.ini
Teletalk_3G/APP_ICON.ico
Teletalk_3G/usr/share/applications/
Teletalk_3G/usr/share/pixmaps/
Teletalk_3G/usr/share/
Teletalk_3G/usr/lib/
Teletalk_3G/plugins/imageformats/
Teletalk_3G/plugins/codecs/
Teletalk_3G/Help/English/
Teletalk_3G/usr/
Teletalk_3G/plugins/
Teletalk_3G/Data/
Teletalk_3G/sqldrivers/
Teletalk_3G/wirelessconfig/
Teletalk_3G/bin/
Teletalk_3G/driver/
Teletalk_3G/pppd/
Teletalk_3G/scripts/
Teletalk_3G/download/
Teletalk_3G/Sound/
Teletalk_3G/UiFile/
Teletalk_3G/userdata/
Teletalk_3G/Config/
Teletalk_3G/Help/
Teletalk_3G/Image/
Teletalk_3G/Language/
Teletalk_3G/qss/
Teletalk_3G/Skin/
Teletalk_3G/
ls: cannot access /usr/share/applications/desktop.*.cache: No such file or directory
******Begin to /opt/Teletalk_3G/driver
this is linux driver installtion
make -C /lib/modules/3.8.0-19-generic/build M=/tmp/ONDA_driver_install_V3.42 modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-19-generic'
  CC [M]  /tmp/ONDA_driver_install_V3.42/onda.o
/tmp/ONDA_driver_install_V3.42/onda.c:21354:16: error: ‘usb_serial_probe’ undeclared here (not in a function)
/tmp/ONDA_driver_install_V3.42/onda.c:21355:16: error: ‘usb_serial_disconnect’ undeclared here (not in a function)
/tmp/ONDA_driver_install_V3.42/onda.c: In function ‘onda_init’:
/tmp/ONDA_driver_install_V3.42/onda.c:21433:2: error: implicit declaration of function ‘usb_serial_register’ [-Werror=implicit-function-declaration]
/tmp/ONDA_driver_install_V3.42/onda.c:21446:2: error: implicit declaration of function ‘usb_serial_deregister’ [-Werror=implicit-function-declaration]
/tmp/ONDA_driver_install_V3.42/onda.c: In function ‘onda_instat_callback’:
/tmp/ONDA_driver_install_V3.42/onda.c:21510:2: error: implicit declaration of function ‘dbg’ [-Werror=implicit-function-declaration]
/tmp/ONDA_driver_install_V3.42/onda.c:21548:6: error: called object ‘err’ is not a function
/tmp/ONDA_driver_install_V3.42/onda.c: In function ‘__check_debug’:
/tmp/ONDA_driver_install_V3.42/onda.c:21598:1: warning: return from incompatible pointer type [enabled by default]
cc1: some warnings being treated as errors
make[2]: *** [/tmp/ONDA_driver_install_V3.42/onda.o] Error 1
make[1]: *** [_module_/tmp/ONDA_driver_install_V3.42] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-19-generic'
make: *** [modules] Error 2
this  is customized kernel ,kernel version is: 3.8.0-19-generic
enter customize_driver_install function
cp: cannot stat ‘onda.ko’: No such file or directory
FATAL: Module onda not found.
disselfirefox.pp driver_install.run nm.pp se End to /opt/Teletalk_3G/driver
udevadm is exist!
install completed!!!
....After setup, you will find the Teletalk 3G in "Applications->Internet->Teletalk 3G". Click the Teletalk 3G and the application will run
press any key to continue.... 
./Teletalk_3G: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory
]0;root@masudul-HP-ProBook-450-G0: /Teletalk/Linuxroot@masudul-HP-ProBook-450-G0:/Teletalk/Linux# 
]0;

---

### Post by kane88 on 2014-02-13
rajib,

did u get it working.
i have a **MF8250 **modem from zte with pid:19d2 and vid:0017.
zte had onda driver for 3.2 not for 3.8 kernel.

let me know if u found a soluton.

---

