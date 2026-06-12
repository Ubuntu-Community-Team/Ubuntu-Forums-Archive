---
title: "Problem with install remove reinstall package!!!"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by MAO on 2007-03-28
Trying to install Conexant modem!!!

But make some mistakes by myself!!!

NOw have some strange error:

root@janka:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR="Red"][SIZE="5"]E: The package conexant needs to be reinstalled, but I can't find an archive for it.[/SIZE][/COLOR]
root@janka:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package conexant needs to be reinstalled, but I can't find an archive for it.
root@janka:~# sudo apt-get install --reinstall conexant
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package conexant needs to be reinstalled, but I can't find an archive for it.
root@janka:~# sudo dpkg -r --force-remove-reinstreq conexant
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 140983 files and directories currently installed.)
Removing conexant ...
ERROR: Module hsfserial does not exist in /proc/modules
ERROR: Module hsfengine does not exist in /proc/modules
ERROR: Module hsfbasic2 does not exist in /proc/modules
ERROR: Module hsfosspec does not exist in /proc/modules
dpkg: error processing conexant (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 conexant
root@janka:~# 

PLZ Help me with this may be it possible to remove Monualy!!!

---

### Post by mahy on 2007-03-28
do you have the connexant.deb file at hand?

---

### Post by zvacet on 2007-03-28
```
 sudo apt-get remove --purge program

```

---

### Post by MAO on 2007-03-28
> **mahy said:**
> do you have the connexant.deb file at hand?

yes !!! at hand

root@janka:~# **apt-get remove --purge conexant**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package conexant needs to be reinstalled, but I can't find an archive for it.
root@janka:~#

Someone PLZ heed quick help

---

### Post by MAO on 2007-03-28
PLZ Heeeeeeeelp !!!!

---

### Post by zvacet on 2007-03-28
Try to reinstall with synaptic.If that doesn´t work try (still in synaptic) go to edit and fix broken package.Last resort is to see (right click on program in synaptic) where program or program files is.After that remove it manualy.
```
cd /where_program_is
```
```
sudo rm -r program
```

---

### Post by MAO on 2007-03-29
> **zvacet said:**
> Try to reinstall with synaptic.If that doesn´t work try (still in synaptic) go to edit and fix broken package.Last resort is to see (right click on program in synaptic) where program or program files is.After that remove it manualy.
```
cd /where_program_is
```
```
sudo rm -r program
```

Synaptic ERROR:
E: The package conexant needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

when trying to  f**ix broken package** no action!!!
Synaptic BLANK SREEN

for 2 type can't find folder or files "Conexant"
root@janka:~/Desktop/Modem# whereis conexant
conexant:
root@janka:~/Desktop/Modem#

---

### Post by zvacet on 2007-03-29
```
find / -name 'ls'
```

---

### Post by MAO on 2007-03-30
root@janka:~# find / -name 'conexant'

blank (no action)

---

### Post by MAO on 2007-03-30
```

root@janka:~/Desktop# /usr/sbin/modem-hsf --install
Removing modules:
removed `/etc/hsf/KYRGYZSTAN'
removed `/etc/hsf/1002.4378'
removed directory: `/etc/hsf'
make clean -C inf
make[1]: Entering directory `/usr/share/conexant-192-1ubuntu/inf'
rm -rf *.o
rm -rf *.temp
rm -rf *.bin
rm -rf hsfinf2bin
make[1]: Leaving directory `/usr/share/conexant-192-1ubuntu/inf'
make clean -C modules
make[1]: Entering directory `/usr/share/conexant-192-1ubuntu/modules'
make -C /lib/modules/$(uname -r)/build M=/usr/share/conexant-192-1ubuntu/modules clean
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  CLEAN   /usr/share/conexant-192-1ubuntu/modules/.tmp_versions
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
rm -rf *.ko
rm -rf *.o
rm -rf *.O
make[1]: Leaving directory `/usr/share/conexant-192-1ubuntu/modules'

VendorID is 1002 DeviceID is 4378 Country is KYRGYZSTAN CountryCode is 

make clean -C inf
make[1]: Entering directory `/usr/share/conexant-192-1ubuntu/inf'
rm -rf *.o
rm -rf *.temp
rm -rf *.bin
rm -rf hsfinf2bin
make[1]: Leaving directory `/usr/share/conexant-192-1ubuntu/inf'
make clean -C modules
make[1]: Entering directory `/usr/share/conexant-192-1ubuntu/modules'
make -C /lib/modules/$(uname -r)/build M=/usr/share/conexant-192-1ubuntu/modules clean
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
rm -rf *.ko
rm -rf *.o
rm -rf *.O
make[1]: Leaving directory `/usr/share/conexant-192-1ubuntu/modules'
make -C inf
make[1]: Entering directory `/usr/share/conexant-192-1ubuntu/inf'
cc -I../modules/imported/include -I../modules/osspec/include -O2 -Wall   -c -o inf2bin.o inf2bin.c
inf2bin.c: In function &#8216;ProcessString&#8217;:
inf2bin.c:236: warning: pointer targets in assignment differ in signedness
inf2bin.c: In function &#8216;ProcessCtryStruct&#8217;:
inf2bin.c:393: warning: pointer targets in assignment differ in signedness
cc -o hsfinf2bin inf2bin.o
(./preprocess.sh linux_hsfi-1002-4378.bin > linux_hsfi-1002-4378.bin.temp; ./hsfinf2bin linux_hsfi-1002-4378.bin.temp linux_hsfi-1002-4378.bin)
make[1]: Leaving directory `/usr/share/conexant-192-1ubuntu/inf'
make -C modules 
make[1]: Entering directory `/usr/share/conexant-192-1ubuntu/modules'
make -C /lib/modules/$(uname -r)/build M=/usr/share/conexant-192-1ubuntu/modules modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  CC [M]  /usr/share/conexant-192-1ubuntu/modules/mod_basic2.o
ld -r -d -o /usr/share/conexant-192-1ubuntu/modules/hsfbasic2-nc.O /usr/share/conexant-192-1ubuntu/modules/imported/hsfbasic2.O
  CC [M]  /usr/share/conexant-192-1ubuntu/modules/mod_engine.o
ld -r -d -o /usr/share/conexant-192-1ubuntu/modules/hsfengine-nc.O /usr/share/conexant-192-1ubuntu/modules/imported/hsfengine.O
  CC [M]  /usr/share/conexant-192-1ubuntu/modules/mod_ich.o
ld -r -d -o /usr/share/conexant-192-1ubuntu/modules/hsfich-nc.O /usr/share/conexant-192-1ubuntu/modules/imported/hsfich.O
  CC [M]  /usr/share/conexant-192-1ubuntu/modules/mod_osspec.o
  CC [M]  /usr/share/conexant-192-1ubuntu/modules/osspec/osmemory.o
  CC [M]  /usr/share/conexant-192-1ubuntu/modules/osspec/osstring.o
  CC [M]  /usr/share/conexant-192-1ubuntu/modules/osspec/osdebug.o
  CC [M]  /usr/share/conexant-192-1ubuntu/modules/osspec/osfloat.o
  CC [M]  /usr/share/conexant-192-1ubuntu/modules/osspec/osstdio.o
  CC [M]  /usr/share/conexant-192-1ubuntu/modules/osspec/osmodule.o
  CC [M]  /usr/share/conexant-192-1ubuntu/modules/osspec/osnvm.o
  CC [M]  /usr/share/conexant-192-1ubuntu/modules/osspec/ostime.o
  CC [M]  /usr/share/conexant-192-1ubuntu/modules/osspec/linuxres.o
/usr/share/conexant-192-1ubuntu/modules/osspec/linuxres.c: In function &#8216;cnxthsf_LinuxInitPowerManagement&#8217;:
/usr/share/conexant-192-1ubuntu/modules/osspec/linuxres.c:131: warning: implicit declaration of function &#8216;pm_register&#8217;
/usr/share/conexant-192-1ubuntu/modules/osspec/linuxres.c:131: warning: assignment makes pointer from integer without a cast
/usr/share/conexant-192-1ubuntu/modules/osspec/linuxres.c: In function &#8216;cnxthsf_LinuxTermPowerManagement&#8217;:
/usr/share/conexant-192-1ubuntu/modules/osspec/linuxres.c:141: warning: implicit declaration of function &#8216;pm_unregister&#8217;
  CC [M]  /usr/share/conexant-192-1ubuntu/modules/serial_hsf.o
/usr/share/conexant-192-1ubuntu/modules/serial_hsf.c: In function &#8216;hsf_rx_chars&#8217;:
/usr/share/conexant-192-1ubuntu/modules/serial_hsf.c:183: error: &#8216;struct tty_struct&#8217; has no member named &#8216;flip&#8217;
/usr/share/conexant-192-1ubuntu/modules/serial_hsf.c:184: error: &#8216;struct tty_struct&#8217; has no member named &#8216;flip&#8217;
/usr/share/conexant-192-1ubuntu/modules/serial_hsf.c:185: error: &#8216;struct tty_struct&#8217; has no member named &#8216;flip&#8217;
/usr/share/conexant-192-1ubuntu/modules/serial_hsf.c:194: error: &#8216;struct tty_struct&#8217; has no member named &#8216;flip&#8217;
/usr/share/conexant-192-1ubuntu/modules/serial_hsf.c:195: error: &#8216;struct tty_struct&#8217; has no member named &#8216;flip&#8217;
/usr/share/conexant-192-1ubuntu/modules/serial_hsf.c:196: error: &#8216;struct tty_struct&#8217; has no member named &#8216;flip&#8217;
/usr/share/conexant-192-1ubuntu/modules/serial_hsf.c:206: error: &#8216;struct tty_struct&#8217; has no member named &#8216;flip&#8217;
/usr/share/conexant-192-1ubuntu/modules/serial_hsf.c:208: error: &#8216;struct tty_struct&#8217; has no member named &#8216;flip&#8217;
/usr/share/conexant-192-1ubuntu/modules/serial_hsf.c:210: error: &#8216;struct tty_struct&#8217; has no member named &#8216;flip&#8217;
/usr/share/conexant-192-1ubuntu/modules/serial_hsf.c:211: error: &#8216;struct tty_struct&#8217; has no member named &#8216;flip&#8217;
/usr/share/conexant-192-1ubuntu/modules/serial_hsf.c: At top level:
/usr/share/conexant-192-1ubuntu/modules/serial_hsf.c:670: warning: initialization from incompatible pointer type
/usr/share/conexant-192-1ubuntu/modules/serial_hsf.c:671: warning: initialization from incompatible pointer type
/usr/share/conexant-192-1ubuntu/modules/serial_hsf.c:695: error: expected &#8216;)&#8217; before string constant
/usr/share/conexant-192-1ubuntu/modules/serial_hsf.c:699: error: expected &#8216;)&#8217; before string constant
make[3]: *** [/usr/share/conexant-192-1ubuntu/modules/serial_hsf.o] Error 1
make[2]: *** [_module_/usr/share/conexant-192-1ubuntu/modules] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/usr/share/conexant-192-1ubuntu/modules'
make: *** [all] Error 2
cp: cannot stat `modules/hsfbasic2.ko': No such file or directory
cp: cannot stat `modules/hsfengine.ko': No such file or directory
cp: cannot stat `modules/hsfich.ko': No such file or directory
cp: cannot stat `modules/hsfosspec.ko': No such file or directory
cp: cannot stat `modules/hsfserial.ko': No such file or directory
FATAL: Module hsfserial not found.

Modem driver should be installed and available on /dev/modem.
If not, your modem may not be supported.

root@janka:~/Desktop# whereis conexant
conexant:
root@janka:~/Desktop# find / -name 'conexant'

root@janka:~/Desktop# 

```

Someone  how to fix this problems !!!

---

### Post by MAO on 2007-03-30
If this Help
```

root@janka:~# sudo dpkg -r --force-remove-reinstreq conexant
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 141015 files and directories currently installed.)
Removing conexant ...
ERROR: Module hsfserial does not exist in /proc/modules
ERROR: Module hsfengine does not exist in /proc/modules
ERROR: Module hsfbasic2 does not exist in /proc/modules
ERROR: Module hsfosspec does not exist in /proc/modules
dpkg: error processing conexant (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 conexant
root@janka:~# 

```

** /proc/modules**
```

root@janka:~# cat /proc/modules 
binfmt_misc 13448 1 - Live 0xf8df7000
rfcomm 42260 0 - Live 0xf8e32000
l2cap 27136 5 rfcomm, Live 0xf8dd8000
ipv6 272288 8 - Live 0xf9475000
fglrx 406988 8 - Live 0xf8e51000
powernow_k8 15008 0 - Live 0xf8dd3000
cpufreq_powersave 2944 0 - Live 0xf8bde000
cpufreq_stats 7744 0 - Live 0xf8dca000
cpufreq_userspace 5408 0 - Live 0xf8dc7000
cpufreq_ondemand 8876 1 - Live 0xf8dc3000
cpufreq_conservative 8712 0 - Live 0xf8d6a000
freq_table 6048 2 powernow_k8,cpufreq_stats, Live 0xf8db6000
tc1100_wmi 8324 0 - Live 0xf8d74000
video 17540 0 - Live 0xf8dbd000
battery 11652 0 - Live 0xf8c19000
container 5632 0 - Live 0xf8d67000
sbs 16804 0 - Live 0xf8d6e000
button 7952 0 - Live 0xf8c3f000
pcc_acpi 14080 0 - Live 0xf8bd1000
sony_acpi 6412 0 - Live 0xf8bf7000
i2c_ec 6272 1 sbs, Live 0xf8bed000
i2c_core 23424 1 i2c_ec, Live 0xf8c2b000
ac 6788 0 - Live 0xf8a53000
dev_acpi 12292 0 - Live 0xf8c14000
asus_acpi 17688 0 - Live 0xf8c25000
hotkey 11556 0 - Live 0xf8bbc000
nls_utf8 3200 1 - Live 0xf8b52000
ntfs 112116 1 - Live 0xf8d78000
fuse 43912 0 - Live 0xf8c33000
sbp2 24584 0 - Live 0xf8c1d000
scsi_mod 144648 1 sbp2, Live 0xf8c42000
lp 12964 0 - Live 0xf8a9f000
tsdev 9152 0 - Live 0xf8c00000
joydev 11200 0 - Live 0xf8bf3000
hci_usb 18068 2 - Live 0xf8bfa000
bluetooth 53476 7 rfcomm,l2cap,hci_usb, Live 0xf8c05000
tifm_7xx1 9472 0 - Live 0xf8bda000
tifm_core 10496 1 tifm_7xx1, Live 0xf8bd6000
usbhid 45152 0 - Live 0xf8be0000
pcmcia 40380 0 - Live 0xf8b80000
sdhci 20108 0 - Live 0xf8b73000
mmc_core 32136 1 sdhci, Live 0xf8b8b000
snd_atiixp_modem 17800 0 - Live 0xf8b7a000
bcm43xx 127252 0 - Live 0xf8b9b000
ieee80211softmac 33792 1 bcm43xx, Live 0xf8b5e000
ieee80211 35272 2 bcm43xx,ieee80211softmac, Live 0xf8b69000
ieee80211_crypt 7552 1 ieee80211, Live 0xf8b4f000
snd_atiixp 21388 1 - Live 0xf8b57000
snd_ac97_codec 97696 2 snd_atiixp_modem,snd_atiixp, Live 0xf8af7000
snd_ac97_bus 3456 1 snd_ac97_codec, Live 0xf8a9d000
snd_pcm_oss 47360 0 - Live 0xf8b42000
snd_mixer_oss 19584 1 snd_pcm_oss, Live 0xf8af1000
snd_pcm 84612 4 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss, Live 0xf8b2c000
tg3 107652 0 - Live 0xf8b10000
yenta_socket 28812 1 - Live 0xf8ae8000
rsrc_nonstatic 15360 1 yenta_socket, Live 0xf8a61000
pcmcia_core 43924 3 pcmcia,yenta_socket,rsrc_nonstatic, Live 0xf8adc000
snd_timer 25348 1 snd_pcm, Live 0xf8ad4000
ati_agp 10636 0 - Live 0xf8a91000
agpgart 34888 2 fglrx,ati_agp, Live 0xf8aca000
shpchp 42144 0 - Live 0xf8abe000
pci_hotplug 32828 1 shpchp, Live 0xf8ab4000
evdev 11392 2 - Live 0xf8a6a000
snd 58372 9 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer, Live 0xf8aa4000
soundcore 11232 1 snd, Live 0xf8a66000
parport_pc 37796 1 - Live 0xf8a86000
snd_page_alloc 11400 3 snd_atiixp_modem,snd_atiixp,snd_pcm, Live 0xf8a59000
parport 39496 2 lp,parport_pc, Live 0xf8a7b000
psmouse 41352 0 - Live 0xf8a6f000
serio_raw 8452 0 - Live 0xf8a5d000
pcspkr 4352 0 - Live 0xf8a56000
reiserfs 263936 1 - Live 0xf88e7000
ehci_hcd 34696 0 - Live 0xf88d1000
ohci1394 37040 0 - Live 0xf88a3000
ieee1394 306104 2 sbp2,ohci1394, Live 0xf8930000
ohci_hcd 22532 0 - Live 0xf8886000
usbcore 134912 5 hci_usb,usbhid,ehci_hcd,ohci_hcd, Live 0xf88af000
ide_generic 2432 0 - Live 0xf8831000
ide_cd 33696 0 - Live 0xf887c000
cdrom 38944 1 ide_cd, Live 0xf8871000
ide_disk 18560 4 - Live 0xf8855000
generic 6276 0 - Live 0xf883f000
atiixp 7824 1 - Live 0xf883c000
thermal 15624 3 - Live 0xf8850000
processor 31560 2 powernow_k8,thermal, Live 0xf885b000
fan 6020 0 - Live 0xf8839000
fbcon 41504 0 - Live 0xf8844000
tileblit 3840 1 fbcon, Live 0xf8837000
font 9344 1 fbcon, Live 0xf8833000
bitblit 7168 1 fbcon, Live 0xf882a000
softcursor 3328 1 bitblit, Live 0xf882d000
vesafb 9244 0 - Live 0xf8808000
capability 5896 0 - Live 0xf8827000
commoncap 8704 1 capability, Live 0xf880c000


```


```

root@janka:~# sudo dpkg --get-selections | grep conexant
conexant                                        deinstall
root@janka:~# 

```

---

### Post by zvacet on 2007-03-31
```
whereis conexant ls 
```

This comman will find conexant and after you know where is you can remove it manualy.For example lat as say it is in usr/bin directory.
```
cd /usr/bin
```
now you are in directory and you want to remove file
```
sudo rm -r conexant
```

This is just xample and with first command you will know exactly where your file is.

---

### Post by MAO on 2007-04-02
root@janka:~# whereis conexant ls
conexant:
ls: /bin/ls /usr/share/man/man1/ls.1.gz
root@janka:~# 
 ???

Any ideas !!! PLZ Heeelp !!!

Can't upgrade, install some soft !!!everything works fine, but I need new packeges to install!!!

---

### Post by pradeepadapa on 2007-04-02
why dont u manually remove the file ls.l.gz in /bin/ls /usr/share/man/man1/ nd then reinstall it.

---

### Post by flyck on 2007-04-21
I had the very same problem!

Did someone resolved?

---

### Post by Ranzas on 2007-05-02
Hi everybody!
This is my first post on this forum and I've had the same problem with Conexant drivers.
I have an easy workaround that worked fine for me:

cd /var/lib/dpkg/info
rm -rf conexant*

Then, the conexant drivers are not seen anymore as partially installed, and you shouldn't see any more message about missing modules while installing/removing other packages.
Hope it helps!
Ciao!

---

