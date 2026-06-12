---
title: "Problem booting to bootable cds"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by Wicked_Sick on 2009-12-14
First off, I have ubuntu 9.10 x64 installed and working decently. Im trying to repartition my hdd to have Ubuntu, win xp(tuning software for my car and Zune), Solaris 10 and BackTrack 4. Right now my issue is that I cannot for the life of me get my laptop to boot to a cd. Ive tried 2 brands of dvds and 1 cd and none will boot on my laptop. They all boot fine in my wifes laptop, whether I burn the iso on my or her laptop. Ive tried burning with K3b, Wobim, and Brasero at max and 2x burn speed. I tried burning from a vmware windows server 2003 with InfraRecorder, and used InfraRecorder on my wifes Vista laptop. 

The dvds/cds wont boot at all, just sits there blinking the curser for a minute or two and then boots ubuntu like usual. The cds also do the same thing when trying to boot to cd with a physical cdd in vmware, but the iso's of the cds boot fine.

On another note, 1 time it did boot fine to one of the dvds burned on my wifes laptop. I tried to use gparted to partition the hdd and it fails when trying to make my /dev/sda1 partition smaller. The error is "e2fsck -f -y -v xxxx" something, I cant remember what the last part was. 

If anyone has any ideas or suggestions on how to get my laptop to boot to cd's I would be extremely grateful.


Also, how can I boot 4 os's with 3 primary partitions and 1 extended partition? Do I have 
[---p-------p------p-----------e-------]
[Ubuntu ][XP][Solaris][(BT4)(swap)]

---

### Post by phillw on 2009-12-14
> **Wicked_Sick said:**
> First off, I have ubuntu 9.10 x64 installed and working decently. Im trying to repartition my hdd to have Ubuntu, win xp(tuning software for my car and Zune), Solaris 10 and BackTrack 4. Right now my issue is that I cannot for the life of me get my laptop to boot to a cd. Ive tried 2 brands of dvds and 1 cd and none will boot on my laptop. They all boot fine in my wifes laptop, whether I burn the iso on my or her laptop. Ive tried burning with K3b, Wobim, and Brasero at max and 2x burn speed. I tried burning from a vmware windows server 2003 with InfraRecorder, and used InfraRecorder on my wifes Vista laptop. 

The dvds/cds wont boot at all, just sits there blinking the curser for a minute or two and then boots ubuntu like usual. The cds also do the same thing when trying to boot to cd with a physical cdd in vmware, but the iso's of the cds boot fine.

On another note, 1 time it did boot fine to one of the dvds burned on my wifes laptop. I tried to use gparted to partition the hdd and it fails when trying to make my /dev/sda1 partition smaller. The error is "e2fsck -f -y -v xxxx" something, I cant remember what the last part was. 

If anyone has any ideas or suggestions on how to get my laptop to boot to cd's I would be extremely grateful.


Also, how can I boot 4 os's with 3 primary partitions and 1 extended partition? Do I have 
[---p-------p------p-----------e-------]
[Ubuntu ][XP][Solaris][(BT4)(swap)]


CD issue is either a dirty lens (try one of cleaning cd/dvd disks), or your CD player is unhappy. This could be as simple as a loose lead (yeah, it does happen) to a dry solder joint (nasty) to a borked drive.

If it is trying to read the CD then I'm pretty sure your BIOS is set up okay.

As for partioning, I run 
sda1 Win
sda2 Extended
sda3 9.10

sda2 then holds...
sda5 /home
sda6 10.04
sda7 /swap

That leaves me one free primary block - the extended ones can hold quite a few partitions (can't remember how many).

something like that would be "good to go" and grub2 can happily find them all.

Regards,

phill.

---

### Post by presence1960 on 2009-12-14
> **Wicked_Sick said:**
> First off, I have ubuntu 9.10 x64 installed and working decently. Im trying to repartition my hdd to have Ubuntu, win xp(tuning software for my car and Zune), Solaris 10 and BackTrack 4. Right now my issue is that I cannot for the life of me get my laptop to boot to a cd. Ive tried 2 brands of dvds and 1 cd and none will boot on my laptop. They all boot fine in my wifes laptop, whether I burn the iso on my or her laptop. Ive tried burning with K3b, Wobim, and Brasero at max and 2x burn speed. I tried burning from a vmware windows server 2003 with InfraRecorder, and used InfraRecorder on my wifes Vista laptop. 

The dvds/cds wont boot at all, just sits there blinking the curser for a minute or two and then boots ubuntu like usual. The cds also do the same thing when trying to boot to cd with a physical cdd in vmware, but the iso's of the cds boot fine.

On another note, 1 time it did boot fine to one of the dvds burned on my wifes laptop. I tried to use gparted to partition the hdd and it fails when trying to make my /dev/sda1 partition smaller. The error is "e2fsck -f -y -v xxxx" something, I cant remember what the last part was. 

If anyone has any ideas or suggestions on how to get my laptop to boot to cd's I would be extremely grateful.


Also, how can I boot 4 os's with 3 primary partitions and 1 extended partition? Do I have 
[---p-------p------p-----------e-------]
[Ubuntu ][XP][Solaris][(BT4)(swap)]

Well if the CDs/DVDs boot fine on another machine that rules out the disks. Now the finger is pointing at your hardware or BIOS. Go into BIOS and make sure CD/DVD is set to boot first in the boot order. If it is so then you need to look into your optical drive as it may be faulty.

---

### Post by Wicked_Sick on 2009-12-14
The dvds I burn on my laptop boot fine on my wifes but not on mine. As soon as I burn the disc theres a popup asking if I want to search it for packages. I tried blowing out the drive but it didnt seem to make a difference. The BIOS is definately set to the right boot order, but I dont know if theres anything else in there to change. Its the least optioned BIOS Ive ever seen. Change the time, boot order, and whether or not bluray and wlan are on by default and whether lan wakes up the computer. Thats about all there is for options.

---

### Post by presence1960 on 2009-12-14
> **Wicked_Sick said:**
> The dvds I burn on my laptop boot fine on my wifes but not on mine. As soon as I burn the disc theres a popup asking if I want to search it for packages. I tried blowing out the drive but it didnt seem to make a difference. The BIOS is definately set to the right boot order, but I dont know if theres anything else in there to change. Its the least optioned BIOS Ive ever seen. Change the time, boot order, and whether or not bluray and wlan are on by default and whether lan wakes up the computer. Thats about all there is for options.

sounds like your optical drive and/or it's connections to it and motherboard.

If you can't fix/replace the optical drive hopefully your machine is capable of booting from usb. If so make bootable flash/usb disks.

---

### Post by phillw on 2009-12-14
> **Wicked_Sick said:**
> The dvds I burn on my laptop boot fine on my wifes but not on mine. As soon as I burn the disc theres a popup asking if I want to search it for packages. I tried blowing out the drive but it didnt seem to make a difference. The BIOS is definately set to the right boot order, but I dont know if theres anything else in there to change. Its the least optioned BIOS Ive ever seen. Change the time, boot order, and whether or not bluray and wlan are on by default and whether lan wakes up the computer. Thats about all there is for options.

There are two LEDS in a cd/dvd writer drive. It is usually the write one that dies 1st, but is possible the read one has died. - Blowing the drive wont help, you need to try a cleaning cd/dvd in it - preferrably a 'wet' one as they are better at removing any film build-up on the lenses.

Phill.

---

### Post by Wicked_Sick on 2009-12-14
> **presence1960 said:**
> sounds like your optical drive and/or it's connections to it and motherboard.

If you can't fix/replace the optical drive hopefully your machine is capable of booting from usb. If so make bootable flash/usb disks.


Is it possible to install from an external hdd? I dont have any flash drives :confused:


> **phillw said:**
> There are two LEDS in a cd/dvd writer drive. It is usually the write one that dies 1st, but is possible the read one has died. - Blowing the drive wont help, you need to try a cleaning cd/dvd in it - preferrably a 'wet' one as they are better at removing any film build-up on the lenses.

Phill.


I'll go shopping tomorrow and see what I can find. Ill let you know as soon as I find out if it worked or not. Thanks for the help.

---

### Post by presence1960 on 2009-12-14
> **Wicked_Sick said:**
> Is it possible to install from an external hdd? I dont have any flash drives :confused:


as long as your machine is capable of booting from USB you can use an external HDD. I always have my current version of Ubuntu Live CD on the first partition (primary) on my externall USB HDD. If I ever need the Live CD I just plug in the external USB HDD and reboot. Of course make sure you set USB/Removable in BIOS to boot before hard disk(s).

---

