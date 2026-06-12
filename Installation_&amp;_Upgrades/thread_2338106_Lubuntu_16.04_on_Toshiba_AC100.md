---
title: "Lubuntu 16.04 on Toshiba AC100"
date: 2016-09-24
forum: Installation &amp; Upgrades
---

### Post by asgard2 on 2016-09-24
Hi,

is someone still using this device?

Is it possible to install 16.04?
 I could not find a preinstalled image.

Best regards

---

### Post by QIII on 2016-09-24
Hello!

I'm not sure about 16.04, but I know that at one time the AC100 was the reference hardware for the Ubuntu ARM port.

You might be able to start [here]("https://wiki.ubuntu.com/ARM/TEGRA/AC100").

Cheers!

---

### Post by asgard2 on 2016-09-26
Hi QIII,

thanks, but this link only describes how to install 12.04.

---

### Post by manemis on 2016-10-06
check this out.

[http://ports.ubuntu.com/ubuntu-ports/dists/xenial-updates/main/installer-armhf/current/images/generic/netboot/](http://ports.ubuntu.com/ubuntu-ports/dists/xenial-updates/main/installer-armhf/current/images/generic/netboot/)

---

### Post by markteras on 2017-02-15
Hi. Just found your post about ac100 and 16.04. Wanted to ask if you got anywhere with installation of 16.04? Am running Lubuntu 14.04. Slight problems with nvidia tegra driver, menus missing, things flashing on/off, text invisible. On OSS driver everything is OK; 
did you run 14.04 by any chance?
BTW, there are OpenSuse Tumbleweed images for AC100/paz00 here:
[http://download.opensuse.org/ports/armv7hl/tumbleweed/images/](http://download.opensuse.org/ports/armv7hl/tumbleweed/images/)
XFCE, LXQT, etc.
Bootloader procedure here:
[https://en.opensuse.org/HCL:ToshibaAC100](https://en.opensuse.org/HCL:ToshibaAC100)
Haven't tried them, though. Would be nice to upgrade to 16.04.
Cheers!

---

### Post by RobGoss on 2017-02-15
> **asgard2 said:**
> Hi,

is someone still using this device?

Is it possible to install 16.04?
 I could not find a preinstalled image.

Best regards

I think the best way to find out if 16.04 will run on that machine is to just run the live installer if all works as it should it's more then likely it will be ok

---

### Post by asgard2 on 2018-02-13
@[**[COLOR=#000000]markteras[/COLOR]**]("https://ubuntuforums.org/member.php?u=2057659")
I didn't try. We can not use the nvidia bootloader, only uboot.
Without a recent guide I may break the device. Could you install opensuse?
I found a guide here, but links are broken: [https://en.opensuse.org/HCL:ToshibaAC100#Installing_the_openSUSE_Tumbleweed_image](https://en.opensuse.org/HCL:ToshibaAC100#Installing_the_openSUSE_Tumbleweed_image)



@[**[COLOR=#000000]RobGoss[/COLOR]**]("https://ubuntuforums.org/member.php?u=1971247") 
Without a regular bootloader, there is no way to boot a live system, but maybe we can install and boot from an sdcard. Can you provide a manual?

---

### Post by markteras on 2018-02-24
Haven't tried OpenSuse. I kept AC100 on 14.04 because it is stable, works and I use it as a typwriter, basically.
If you just search this directory  

[http://download.opensuse.org/ports/armv7hl/factory/repo/oss/suse/armv7hl/](http://download.opensuse.org/ports/armv7hl/factory/repo/oss/suse/armv7hl/)

[http://download.opensuse.org/ports/armv7hl/factory/repo/oss/suse/armv7hl/u-boot-paz00-2018.01-1.1.armv7hl.rpm](http://download.opensuse.org/ports/armv7hl/factory/repo/oss/suse/armv7hl/u-boot-paz00-2018.01-1.1.armv7hl.rpm)

[http://download.opensuse.org/ports/armv7hl/factory/repo/oss/suse/armv7hl/u-boot-paz00-doc-2018.01-1.1.armv7hl.rpm](http://download.opensuse.org/ports/armv7hl/factory/repo/oss/suse/armv7hl/u-boot-paz00-doc-2018.01-1.1.armv7hl.rpm)

for paz00, you'll find the files for AC100's Uboot bootloader from 2018; they update the files and build new OpenSuse images for 

AC100 all the time (all have paz00 designation), which is rather amazing to me. They will even have video decoding working based on this

[https://marc.info/?l=linux-tegra&m=150637806225024&w=2](https://marc.info/?l=linux-tegra&m=150637806225024&w=2)
   
New AC100/paz00 OpenSuse images appear all the time here

[http://download.opensuse.org/ports/armv7hl/tumbleweed/images/](http://download.opensuse.org/ports/armv7hl/tumbleweed/images/)

e.g.

[http://download.opensuse.org/ports/armv7hl/tumbleweed/images/openSUSE-Tumbleweed-ARM-XFCE-paz00.armv7l-Current.raw.xz](http://download.opensuse.org/ports/armv7hl/tumbleweed/images/openSUSE-Tumbleweed-ARM-XFCE-paz00.armv7l-Current.raw.xz)

I think I might try them sooner or later, just didn't have the time or need yet.

There are also guides for Arch Linux around, but OpenSuse has active support with full images. I think if you follow the bootloader 

procedure it should all work; I'd take full backup sector by sector with nvflash beforehand, no matter what.

---

### Post by asgard2 on 2018-02-28
Right, there was a 14.04 release with [EOL 2019 .]("https://wiki.ubuntu.com/Releases")
I searched but they are vanished from the ubuntu servers ([trusty-preinstalled-desktop-armhf+ac100.tar.gz ]("http://cdimage.ubuntu.com/lubuntu/daily-preinstalled/pending/trusty-preinstalled-desktop-armhf+ac100.tar.gz")[trusty-preinstalled-desktop-armhf+ac100.bootimg)]("http://cdimage.ubuntu.com/lubuntu/daily-preinstalled/pending/trusty-preinstalled-desktop-armhf+ac100.bootimg") . :(

---

### Post by markteras on 2018-03-02
I still have the images for Lubuntu 14.04 and 12.10, but the upload on my current connection would be a nightmare. Fortunately there are still images for 14.04 here: [http://mirrors.webair.com/ubuntu/ubuntu-cdimage/lubuntu/daily-preinstalled/20140204/](http://mirrors.webair.com/ubuntu/ubuntu-cdimage/lubuntu/daily-preinstalled/20140204/) if you want them. There are also files for 12.04 here [http://ftp.heanet.ie/mirrors/ubuntu-cdimage/releases](http://ftp.heanet.ie/mirrors/ubuntu-cdimage/releases) although there is no point installing that one now, I think, except for the fact that Nvidia graphics driver was working for me perfectly on 12.10 and it does not work on 14.04, even though it does exist in the repos. So, no games, etc. Screwed up colors and slow on Nvidia. No major problems on Nouveau. Videos work fine on normal players, never used it in browsers. Chromium fine, Firefox fine up to 52esr. Palemoon armhf doesn't go.
Audio fine, except to get mp3s to work I had to install various mp3 encoding/decoding libraries/debs and don't remember now which one did the trick. Other file formats - no problem.
Libre Office installed after some problems, clearing stuff out with aptitude etc. That was nasty.
The rest is OK, had no problems with installing the system itself and I did it twice. I installed from an sd card directly to filesystem.
Sound reset command is useful, sometimes stops playing after installing stuff or using Nvidia driver.

alsaucm -c tegraalc5632 reset

Backlight control is working after installing some xubuntu bars/controls. Then you get a slider for it, terminal commands didn't 
work for me.
And watch out with upgrading apparmor; screwed up wifi for me once until I froze it at some older version.

[https://wiki.ubuntu.com/ARM/TEGRA/AC100](https://wiki.ubuntu.com/ARM/TEGRA/AC100)  use the same procedure, might want to rename files to 1.bootimg and 1.tar.gz or similar to make it easier.

Good luck.

BTW, out of curiosity, what do you have installed right now?

---

### Post by asgard2 on 2018-03-02
@[**[COLOR=#000000]markteras[/COLOR]**]("https://ubuntuforums.org/member.php?u=2057659")
I had lubuntu 12.04 installed.
Thanks, but I already tried to install the opensuse image, after writing the new BCT, the ac100 is only black, it not booting from sd card or emmc.

Backup restore from 2nd partition fails ... 
```
./nvflash -r --download 2 part02.img 

 Nvflash started
 [resume mode]

 failed executing command 14 NvError 0x120002

 command failure: partition download failed (bad command)
```

not shure what went wrong ... :(

Any hints?

---

### Post by markteras on 2018-03-02
Shouldn't the command be nvflash -- r --download?

Or try

-- resume -- download

-resume --download

Or try without --r or -- resume

I seem to remember having a similar problem and I think one of those fixed it

Why partition 2: was BCT there?

Bootloader was on 6 wasn't it?

---

### Post by asgard2 on 2018-03-03
Should be correct.
```
 Write the image <filename> partition <N> of your AC100: 

 $ nvflash -r --download <N> <filename>   

Read the partition <N> from the AC100 to the file <filename>: 
 $ nvflash -r --read <N> <filename>
```
[https://ac100.grandou.net/nvflash](https://ac100.grandou.net/nvflash)

[https://ac100.grandou.net/backups](https://ac100.grandou.net/backups)

my partitiontable:
```
PartitionId=2
Name=BCT
DeviceId=18
StartSector=0
NumSectors=1536
BytesPerSector=2048


PartitionId=3
Name=PT
DeviceId=18
StartSector=1536
NumSectors=256
BytesPerSector=2048


PartitionId=4
Name=EBT
DeviceId=18
StartSector=1792
NumSectors=1024
BytesPerSector=2048


PartitionId=5
Name=SOS
DeviceId=18
StartSector=2816
NumSectors=2560
BytesPerSector=2048


PartitionId=6
Name=LNX
DeviceId=18
StartSector=5376
NumSectors=4096
BytesPerSector=2048


PartitionId=7
Name=MBR
DeviceId=18
StartSector=9472
NumSectors=512
BytesPerSector=2048


PartitionId=8
Name=APP
DeviceId=18
StartSector=9984
NumSectors=153600
BytesPerSector=2048


PartitionId=9
Name=CAC
DeviceId=18
StartSector=163584
NumSectors=204800
BytesPerSector=2048


PartitionId=10
Name=MSC
DeviceId=18
StartSector=368384
NumSectors=1024
BytesPerSector=2048


PartitionId=11
Name=EM1
DeviceId=18
StartSector=369408
NumSectors=256
BytesPerSector=2048


PartitionId=12
Name=UDA
DeviceId=18
StartSector=369664
NumSectors=632320
BytesPerSector=2048


PartitionId=13
Name=EM2
DeviceId=18
StartSector=1001984
NumSectors=256
BytesPerSector=2048


PartitionId=14
Name=UDB
DeviceId=18
StartSector=1002240
NumSectors=2905344
BytesPerSector=2048




```

---

### Post by markteras on 2018-03-03
I would run:

$ sudo ./nvflash --resume --download 2 part02.img

to fix your problem

(I was using Windows nvflash, but that doesn't matter; check below)


You've got exactly the same partition table as mine but for the last one. This is mine:

PartitionId=14
Name=UDB
DeviceId=18
StartSector=1002240
NumSectors=6774016
BytesPerSector=2048

Meaning you have got a smaller number of sectors on 14 (8gb version?) and mine is 16gb, but that doesn't matter, of course.

Look at this excerpt from ac100 chat log I have saved:

17:32 < nabhoth> any advice? I am trying to flash the partition 5 using the prepare-for-ubuntu but either it hangs or have a problem 

reported
17:34 < ogra_> nabhoth, either restart the ac100 between the two nvflash commands or use the --resume option for the 

second one
17:35 < ogra_> (instead of --bl fastboot.bin)
17:35 < nabhoth> thank you

And this log discusses --resume

[http://salaliitto.com/~gildean/ac100/ac100log.txt](http://salaliitto.com/~gildean/ac100/ac100log.txt)

I recall that I had the same problem when uploading Ubuntu bootimg bootloader and had found this site

[http://bis.org.pl/en:ac100](http://bis.org.pl/en:ac100)

with this:


Files can be downloaded from this site or copied from the device itself, using the following commands: 
nvflash --bl bootloader.bin --go
nvflash --resume --getpartitiontable partitiontable.txt
for i in 2 3 4 5 6 7 8 9 10 11 12 13; do
  sudo 

nvflash --resume --read $i part-$i.img
done
Sometimes nvflash &#8211;read hangs. If it happens, You should restart the machine again, load the bootloader again (first click) and then 

continue from the failed operation. 
  * The BCT is the first 4080 bytes of partition 2
  * The bootloader occupies 1066kB initial partition 4 (the data from my version).
After doing the backup, you can proceed to programming the device. 

Programming for the first time
$ sudo ./nvflash --bct ac100.bct --setbct --configfile linux.cfg --create --bl bootloader.bin --go
Nvflash started


Bootloader (runs in RAM and accepts commands): 
$ sudo ./nvflash --bl bootloader.bin --go
Nvflash started
rcm version 0X20001
System Information:
   chip name: t20
   chip id: 0x20 

major: 1 minor: 2
   chip sku: 0x8
   chip uid: 0x161c11034260e057
   macrovision: disabled
   hdcp: enabled
   sbk burned: false
   dk 

burned: false
   boot device: emmc
   operating mode: 3
   device config strap: 1
   device config fuse: 0
   sdram config strap: 1

downloading 

bootloader -- load address: 0x108000 entry point: 0x108000
sending file: bootloader.bin
/ 779268/779268 bytes sent
bootloader.bin 

sent successfully
waiting for bootloader to initialize
bootloader downloaded successfully
Kernel: 
$ sudo ./nvflash --resume --download 6 linux.img 
Nvflash started



I have used --resume --download and it had worked.

---

### Post by asgard2 on 2018-03-03
Yes it is the 8GB version ;)

I the used "-r" already, should be the same as "--resume" (see nvflash --help).

But I could now restore my 2nd partition with 
```
./nvflash -r --**rawdevicewrite    0    1536** part02.img
```


It seems that the opensuse u-boot binary is not working on ac100?

```
./nvflash --bl u-boot.bin --sync
```
is stuck on waiting to initialize ...

```
sudo tegrarcm --bct u-boot.bct --bootloader u-boot.bin --loadaddr=0x00108000 --entryaddr=0x00108000
...
tegrarcm: error downloading bct: u-boot.bct: Input/output error
```

---

### Post by markteras on 2018-03-06
Can't help you with BCT on OpenSuse. You have just reached the limit of my knowledge, I never tried it, but I know that guys on 
OpenSuse forum could help because they do that stuff. I suggest you post BCT code there. Here
[https://forums.opensuse.org/showthread.php/521283-Toshiba-AC100-ARMHF-Lubuntu-OpenSUSE-dual-boot-with-U-boot?](https://forums.opensuse.org/showthread.php/521283-Toshiba-AC100-ARMHF-Lubuntu-OpenSUSE-dual-boot-with-U-boot?)
I asked them if it would be possible to dual-boot Lubuntu with OpenSuse, but this developer called zombah 
[https://forums.opensuse.org/member.php/18826-zombah?](https://forums.opensuse.org/member.php/18826-zombah?)
said no because Ubuntu bootloader is closed and Uboot completely open-source, they don't play nice together.
OpenSuse installation defaults to external SD card.
I know he still deals with AC100 software, see here:
[https://plus.google.com/communities/118383678603263932646](https://plus.google.com/communities/118383678603263932646)
and here
[https://github.com/zombah/android_device_toshiba_ac100](https://github.com/zombah/android_device_toshiba_ac100)
If you try it again with OpenSuse, and succeed, or get some answers out of them, let me know, will you? I might want to try it sooner or later.

---

### Post by asgard2 on 2018-03-12
> **markteras said:**
> If you try it again with OpenSuse, and succeed, or get some answers out of them, let me know, will you? I might want to try it sooner or later.

There could be an incompatibility with newer version which maybe break it.

- [a full backup]("http://https://ac100.grandou.net/backups")

- the[ SOS boot image from his guide]("https://paz00.ru/index.php/Migrate_to_U-Boot") is working, you can write a new bct to the 2nd partition, with the scripts getbct.sh, mkbct.sh, uploadbct.sh .

Now we can boot Tumbleweed from sdcard, the other internal partitions should be untouched .

I tried LXQT, it seems buggy and I don't like yast :sad:
... and I need to figure out, how to move it to the internal emmc.

---

### Post by markteras on 2018-03-15
Thanks for that.
KDE on OpenSuse should be best, it's their default DE, but how the hell could this work in 512MB RAM? Could you install anything 

with YAST?

Wish we could put together 16.04, but I'm not up to it.

On the other hand Debian has armhf installation ISOs, so I don't know.

[https://cdimage.debian.org/debian-cd/current/armhf/iso-cd/](https://cdimage.debian.org/debian-cd/current/armhf/iso-cd/)

---

### Post by asgard2 on 2018-03-17
No, I didn't try ... but I used [zypper]("https://en.opensuse.org/SDB:Zypper_usage").

That should be something like[ this]("https://help.ubuntu.com/lts/installation-guide/armhf/index.html"), a debian/ubuntu armhf version with uboot.

---

