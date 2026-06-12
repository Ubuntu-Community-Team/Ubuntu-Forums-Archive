---
title: "Installer not working + serious hard drive problems"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by mike_e on 2008-05-03
I switched a while ago from Mac OS X (Leopard) to Ubuntu (Gutsy) and didn't encounter any serious problems until about a month ago when Ubuntu crashed for seemingly no reason. I tried to boot my computer and for a while nothing happened, then an image came up of a folder with a question mark on it.

So, I've been using the ubuntu liveCD for about a month tinkering around and trying to install...but the installer gets to about 48% and then freezes.

Throughout this process, I lost all of the files in my /home folder and seemingly all of my hard drive partitions. This is interesting, because at first I still had my files and the installer detected my existing partitions, but now it doesn't do it at all.

Here are some notable command line outputs:

ls /dev:
> 1-2        ptyc0  ptyqf  ptyve  ram7        tty7   ttyec  ttyt7  ttyy6
3-2        ptyc1  ptyr0  ptyvf  ram8        tty8   ttyed  ttyt8  ttyy7
4-1        ptyc2  ptyr1  ptyw0  ram9        tty9   ttyee  ttyt9  ttyy8
5-4        ptyc3  ptyr2  ptyw1  random      ttya0  ttyef  ttyta  ttyy9
adsp       ptyc4  ptyr3  ptyw2  rtc         ttya1  ttyp0  ttytb  ttyya
agpgart    ptyc5  ptyr4  ptyw3  scd0        ttya2  ttyp1  ttytc  ttyyb
audio      ptyc6  ptyr5  ptyw4  sequencer   ttya3  ttyp2  ttytd  ttyyc
bus        ptyc7  ptyr6  ptyw5  sequencer2  ttya4  ttyp3  ttyte  ttyyd
cdrom      ptyc8  ptyr7  ptyw6  sg0         ttya5  ttyp4  ttytf  ttyye
cdrw       ptyc9  ptyr8  ptyw7  shm         ttya6  ttyp5  ttyu0  ttyyf
console    ptyca  ptyr9  ptyw8  snapshot    ttya7  ttyp6  ttyu1  ttyz0
core       ptycb  ptyra  ptyw9  snd         ttya8  ttyp7  ttyu2  ttyz1
disk       ptycc  ptyrb  ptywa  sndstat     ttya9  ttyp8  ttyu3  ttyz2
dri        ptycd  ptyrc  ptywb  sr0         ttyaa  ttyp9  ttyu4  ttyz3
dsp        ptyce  ptyrd  ptywc  stderr      ttyab  ttypa  ttyu5  ttyz4
dvd        ptycf  ptyre  ptywd  stdin       ttyac  ttypb  ttyu6  ttyz5
dvdrw      ptyd0  ptyrf  ptywe  stdout      ttyad  ttypc  ttyu7  ttyz6
fd         ptyd1  ptys0  ptywf  tty         ttyae  ttypd  ttyu8  ttyz7
full       ptyd2  ptys1  ptyx0  tty0        ttyaf  ttype  ttyu9  ttyz8
fuse       ptyd3  ptys2  ptyx1  tty1        ttyb0  ttypf  ttyua  ttyz9
hpet       ptyd4  ptys3  ptyx2  tty10       ttyb1  ttyq0  ttyub  ttyza
initctl    ptyd5  ptys4  ptyx3  tty11       ttyb2  ttyq1  ttyuc  ttyzb
input      ptyd6  ptys5  ptyx4  tty12       ttyb3  ttyq2  ttyud  ttyzc
kmem       ptyd7  ptys6  ptyx5  tty13       ttyb4  ttyq3  ttyue  ttyzd
kmsg       ptyd8  ptys7  ptyx6  tty14       ttyb5  ttyq4  ttyuf  ttyze
log        ptyd9  ptys8  ptyx7  tty15       ttyb6  ttyq5  ttyv0  ttyzf
loop0      ptyda  ptys9  ptyx8  tty16       ttyb7  ttyq6  ttyv1  urandom
loop1      ptydb  ptysa  ptyx9  tty17       ttyb8  ttyq7  ttyv2  usb1
loop2      ptydc  ptysb  ptyxa  tty18       ttyb9  ttyq8  ttyv3  usb2
loop3      ptydd  ptysc  ptyxb  tty19       ttyba  ttyq9  ttyv4  usb3
loop4      ptyde  ptysd  ptyxc  tty2        ttybb  ttyqa  ttyv5  usb4
loop5      ptydf  ptyse  ptyxd  tty20       ttybc  ttyqb  ttyv6  usb5
loop6      ptye0  ptysf  ptyxe  tty21       ttybd  ttyqc  ttyv7  usbdev1.1_ep00
loop7      ptye1  ptyt0  ptyxf  tty22       ttybe  ttyqd  ttyv8  usbdev1.1_ep81
MAKEDEV    ptye2  ptyt1  ptyy0  tty23       ttybf  ttyqe  ttyv9  usbdev1.4_ep00
mem        ptye3  ptyt2  ptyy1  tty24       ttyc0  ttyqf  ttyva  usbdev1.4_ep81
mixer      ptye4  ptyt3  ptyy2  tty25       ttyc1  ttyr0  ttyvb  usbdev1.4_ep83
net        ptye5  ptyt4  ptyy3  tty26       ttyc2  ttyr1  ttyvc  usbdev1.4_ep84
null       ptye6  ptyt5  ptyy4  tty27       ttyc3  ttyr2  ttyvd  usbdev2.1_ep00
nvidia0    ptye7  ptyt6  ptyy5  tty28       ttyc4  ttyr3  ttyve  usbdev2.1_ep81
nvidiactl  ptye8  ptyt7  ptyy6  tty29       ttyc5  ttyr4  ttyvf  usbdev3.1_ep00
oldmem     ptye9  ptyt8  ptyy7  tty3        ttyc6  ttyr5  ttyw0  usbdev3.1_ep81
port       ptyea  ptyt9  ptyy8  tty30       ttyc7  ttyr6  ttyw1  usbdev3.2_ep00
ppp        ptyeb  ptyta  ptyy9  tty31       ttyc8  ttyr7  ttyw2  usbdev3.2_ep83
psaux      ptyec  ptytb  ptyya  tty32       ttyc9  ttyr8  ttyw3  usbdev4.1_ep00
ptmx       ptyed  ptytc  ptyyb  tty33       ttyca  ttyr9  ttyw4  usbdev4.1_ep81
pts        ptyee  ptytd  ptyyc  tty34       ttycb  ttyra  ttyw5  usbdev4.3_ep00
ptya0      ptyef  ptyte  ptyyd  tty35       ttycc  ttyrb  ttyw6  usbdev4.3_ep02
ptya1      ptyp0  ptytf  ptyye  tty36       ttycd  ttyrc  ttyw7  usbdev4.3_ep03
ptya2      ptyp1  ptyu0  ptyyf  tty37       ttyce  ttyrd  ttyw8  usbdev4.3_ep81
ptya3      ptyp2  ptyu1  ptyz0  tty38       ttycf  ttyre  ttyw9  usbdev4.3_ep82
ptya4      ptyp3  ptyu2  ptyz1  tty39       ttyd0  ttyrf  ttywa  usbdev4.3_ep83
ptya5      ptyp4  ptyu3  ptyz2  tty4        ttyd1  ttys0  ttywb  usbdev5.1_ep00
ptya6      ptyp5  ptyu4  ptyz3  tty40       ttyd2  ttyS0  ttywc  usbdev5.1_ep81
ptya7      ptyp6  ptyu5  ptyz4  tty41       ttyd3  ttys1  ttywd  usbdev5.3_ep00
ptya8      ptyp7  ptyu6  ptyz5  tty42       ttyd4  ttyS1  ttywe  vcs
ptya9      ptyp8  ptyu7  ptyz6  tty43       ttyd5  ttys2  ttywf  vcs1
ptyaa      ptyp9  ptyu8  ptyz7  tty44       ttyd6  ttyS2  ttyx0  vcs2
ptyab      ptypa  ptyu9  ptyz8  tty45       ttyd7  ttys3  ttyx1  vcs3
ptyac      ptypb  ptyua  ptyz9  tty46       ttyd8  ttyS3  ttyx2  vcs4
ptyad      ptypc  ptyub  ptyza  tty47       ttyd9  ttys4  ttyx3  vcs5
ptyae      ptypd  ptyuc  ptyzb  tty48       ttyda  ttys5  ttyx4  vcs6
ptyaf      ptype  ptyud  ptyzc  tty49       ttydb  ttys6  ttyx5  vcs7
ptyb0      ptypf  ptyue  ptyzd  tty5        ttydc  ttys7  ttyx6  vcs8
ptyb1      ptyq0  ptyuf  ptyze  tty50       ttydd  ttys8  ttyx7  vcsa
ptyb2      ptyq1  ptyv0  ptyzf  tty51       ttyde  ttys9  ttyx8  vcsa1
ptyb3      ptyq2  ptyv1  ram0   tty52       ttydf  ttysa  ttyx9  vcsa2
ptyb4      ptyq3  ptyv2  ram1   tty53       ttye0  ttysb  ttyxa  vcsa3
ptyb5      ptyq4  ptyv3  ram10  tty54       ttye1  ttysc  ttyxb  vcsa4
ptyb6      ptyq5  ptyv4  ram11  tty55       ttye2  ttysd  ttyxc  vcsa5
ptyb7      ptyq6  ptyv5  ram12  tty56       ttye3  ttyse  ttyxd  vcsa6
ptyb8      ptyq7  ptyv6  ram13  tty57       ttye4  ttysf  ttyxe  vcsa7
ptyb9      ptyq8  ptyv7  ram14  tty58       ttye5  ttyt0  ttyxf  vcsa8
ptyba      ptyq9  ptyv8  ram15  tty59       ttye6  ttyt1  ttyy0  watchdog
ptybb      ptyqa  ptyv9  ram2   tty6        ttye7  ttyt2  ttyy1  xconsole
ptybc      ptyqb  ptyva  ram3   tty60       ttye8  ttyt3  ttyy2  zero
ptybd      ptyqc  ptyvb  ram4   tty61       ttye9  ttyt4  ttyy3
ptybe      ptyqd  ptyvc  ram5   tty62       ttyea  ttyt5  ttyy4
ptybf      ptyqe  ptyvd  ram6   tty63       ttyeb  ttyt6  ttyy5

[note no sda]

> ubuntu@ubuntu:~$ ls /dev | grep sda
[no output]

> ubuntu@ubuntu:~$ sudo fdisk /dev/sda

Unable to open /dev/sda

> ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda /mnt/temp
mount: special device /dev/sda does not exist


> ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$

[no output]

Everyone I have talked to about this has been thoroughly baffled. Any help would be immensely appreciated.

---

