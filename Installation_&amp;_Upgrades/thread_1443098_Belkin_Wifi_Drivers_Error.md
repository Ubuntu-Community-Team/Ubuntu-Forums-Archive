---
title: "Belkin Wifi Drivers Error"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by skorea2131 on 2010-03-30
This is the entire terminal log of what i did...

[SIZE="1"]
andrewo@andrewo-laptop:~$ sudo cd
[sudo] password for andrewo: 
sudo: cd: command not found

andrewo@andrewo-laptop:~$ cd /home/andrewo/Desktop/Storage/Downloads/Wifi_USB

andrewo@andrewo-laptop:~/Desktop/Storage/Downloads/Wifi_USB$ sudo make
make -C tools
make[1]: Entering directory `/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/tools'
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/tools/bin2h
cp -f os/linux/Makefile.6 /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/Makefile
make  -C  /lib/modules/2.6.31-20-generic/build SUBDIRS=/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../common/crypt_md5.o
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../common/mlme.o
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../common/mlme.c: In function &#8216;BssTableSortByRssi&#8217;:
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../common/mlme.c:4255: warning: the frame size of 1572 bytes is larger than 1024 bytes
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../common/cmm_wep.o
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../common/action.o
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../common/cmm_data.o
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../common/rtmp_init.o
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../common/cmm_aes.o
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../common/cmm_aes.c: In function &#8216;AES_GTK_KEY_WRAP&#8217;:
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../common/cmm_aes.c:1338: warning: the frame size of 1092 bytes is larger than 1024 bytes
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../common/cmm_sync.o
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../common/eeprom.o
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../common/cmm_info.o
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../common/dfs.o
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../common/spectrum.o
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../common/rt_channel.o
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../common/cmm_profile.o
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../common/cmm_asic.o
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../sta/assoc.o
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../sta/auth.o
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../sta/sync.o
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../sta/sync.c: In function &#8216;PeerBeaconAtScanAction&#8217;:
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../sta/sync.c:649: warning: the frame size of 1252 bytes is larger than 1024 bytes
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../sta/sync.c: In function &#8216;PeerBeacon&#8217;:
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../sta/sync.c:1423: warning: the frame size of 1312 bytes is larger than 1024 bytes
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../sta/sync.c: In function &#8216;PeerBeaconAtJoinAction&#8217;:
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../sta/sync.c:927: warning: the frame size of 1260 bytes is larger than 1024 bytes
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../sta/sync.c: In function &#8216;MlmeStartReqAction&#8217;:
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../sta/sync.c:523: warning: the frame size of 1064 bytes is larger than 1024 bytes
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../sta/sanity.o
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../sta/connect.o
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../sta/connect.c: In function &#8216;CntlOidScanProc&#8217;:
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../sta/connect.c:341: warning: the frame size of 1600 bytes is larger than 1024 bytes
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../sta/wpa.o
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.o
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSTaskAttach&#8217;:
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.c:1169: warning: unused variable &#8216;pid_number&#8217;
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSNetDevAttach&#8217;:
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.c:1508: error: &#8216;struct net_device&#8217; has no member named &#8216;open&#8217;
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.c:1509: error: &#8216;struct net_device&#8217; has no member named &#8216;stop&#8217;
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.c:1510: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.c:1511: error: &#8216;struct net_device&#8217; has no member named &#8216;do_ioctl&#8217;
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.c:1517: error: &#8216;struct net_device&#8217; has no member named &#8216;get_stats&#8217;
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.c:1551: error: &#8216;struct net_device&#8217; has no member named &#8216;validate_addr&#8217;
make[2]: *** [/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make: *** [LINUX] Error 2

andrewo@andrewo-laptop:~/Desktop/Storage/Downloads/Wifi_USB$ sudo make install
make -C /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux -f Makefile.6 install
make[1]: Entering directory `/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.31-20-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2870sta.ko /lib/modules/2.6.31-20-generic/kernel/drivers/net/wireless/
install: cannot stat `rt2870sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux'
make: *** [install] Error 2

andrewo@andrewo-laptop:~/Desktop/Storage/Downloads/Wifi_USB$ sudo make
make -C tools
make[1]: Entering directory `/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/tools'
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/tools/bin2h
cp -f os/linux/Makefile.6 /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/Makefile
make  -C  /lib/modules/2.6.31-20-generic/build SUBDIRS=/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.o
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSTaskAttach&#8217;:
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.c:1169: warning: unused variable &#8216;pid_number&#8217;
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSNetDevAttach&#8217;:
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.c:1508: error: &#8216;struct net_device&#8217; has no member named &#8216;open&#8217;
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.c:1509: error: &#8216;struct net_device&#8217; has no member named &#8216;stop&#8217;
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.c:1510: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.c:1511: error: &#8216;struct net_device&#8217; has no member named &#8216;do_ioctl&#8217;
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.c:1517: error: &#8216;struct net_device&#8217; has no member named &#8216;get_stats&#8217;
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.c:1551: error: &#8216;struct net_device&#8217; has no member named &#8216;validate_addr&#8217;
make[2]: *** [/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make: *** [LINUX] Error 2

andrewo@andrewo-laptop:~/Desktop/Storage/Downloads/Wifi_USB$ sudo make
make -C tools
make[1]: Entering directory `/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/tools'
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/tools/bin2h
cp -f os/linux/Makefile.6 /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/Makefile
make  -C  /lib/modules/2.6.31-20-generic/build SUBDIRS=/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  CC [M]  /home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.o
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSTaskAttach&#8217;:
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.c:1169: warning: unused variable &#8216;pid_number&#8217;
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSNetDevAttach&#8217;:
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.c:1508: error: &#8216;struct net_device&#8217; has no member named &#8216;open&#8217;
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.c:1509: error: &#8216;struct net_device&#8217; has no member named &#8216;stop&#8217;
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.c:1510: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.c:1511: error: &#8216;struct net_device&#8217; has no member named &#8216;do_ioctl&#8217;
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.c:1517: error: &#8216;struct net_device&#8217; has no member named &#8216;get_stats&#8217;
/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.c:1551: error: &#8216;struct net_device&#8217; has no member named &#8216;validate_addr&#8217;
make[2]: *** [/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/andrewo/Desktop/Storage/Downloads/Wifi_USB/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make: *** [LINUX] Error 2
[/SIZE]

PLEASE HELP ME!!! :sad:](*,)[-o<

---

