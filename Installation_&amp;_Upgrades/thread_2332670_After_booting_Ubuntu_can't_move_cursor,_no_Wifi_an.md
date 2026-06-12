---
title: "After booting Ubuntu: can't move cursor, no Wifi and can't shutdown."
date: 2016-08-02
forum: Installation &amp; Upgrades
---

### Post by gabrielbeauchemin on 2016-08-02
Hello everyone :),

So now I finally was able to install ubuntu (Mate) in EFI. My computer is Acer Aspire V15 V3-575T-51Q8.

The problem is that I can't move the cursor (with laptop touchpad). It was the same thing before when I tried in other LIVE Gnu/Linux Distro, but if I connect a mouse it was working with it. So now witht he mouse it's not working. I tried in all usb place on my laptop (2.0 and 3.0). I guess drivers doesn't work. When I did the installation I asked to install everything (I think they called take third party installation) and I chose to do the update while it was installing (the laptop didnt find the wifi, which work easly on widnows, so I put the wired directly in it).

 Also the wifi don't work, I think the driver for my wifi card doesn't work. The computer also can't shutdown. After a shutdown, the Ubuntu Mate is loading for ever and the computer never closes. The command shutdown -h now works to close my computer.

So I guess I will have to solve it on the console only (Im beginner on the console) I tried few things I found only but nothing worked. I found command that help few people that have the same problem that mine (No wifi and can't shutdown normally) but it doesnt work for my it says that the command can't be found or something similar. The command is the following:sudo apt-get remove --purge bcmwl -Kernel-source        then       sudo apt-get install linux -firmware -nonfree

Thanks Anyone for help...I tried a lot of thing but found problem after problem...Im trying to installed it for the past month. Thanks much

---

### Post by mörgæs on 2016-08-05
First let's see the hardware. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by gabrielbeauchemin on 2016-08-06
First, thanks for the willing to help :).

I run the command you ask me to and ''PCI Csysff'' appeared and disappear I guess its normal. Than I did cat on the file in question. I Have a problem at this point. Do you want to see what fully contains the file? Because it seems pretty long and I can't copy/paste, because I don't have wifi the computer. Also, even if I would have it, How can I copy it adn send it withtout any mouse? I took in note the end of the file I saw and I will copy it now.

description: data partition
vendor: windows
physical id:7
bus info: scsi@0:0.0.0,7
logical name: dev\sda7
capacity 40 gib
configuration: name=primary

x-Volume:7
description: EXT4 value
vendor:Linux
physicial id:8 
bus info: scsi @0:0.0.0,8
version 1.0
serial: REMOVED
size:422 gib 
capacities:formated extended_attributes large_file huge_file elis_nlink recover extends ext4 ext2 initialized
configuration created: 2016-07-27 21:20:37 filesystem=ext4 last mountpoint:/ modified=2016-08-06 00:52:29 mount.filetype=ext4 lastmtwe, errors: remount_ro, dates=ordered mounted=2016-08-06 00:52:24 state =mounted.

I will have to find a way to copy futher command you ask...becuase writing it on a paper and wrtiting it again of the forum is very long.

---

### Post by gabrielbeauchemin on 2016-08-06
I found on a the spec of my computer:

Built-in 802.11ac WiFi featuring MU-MIMO technology allows you to  seamlessly connect to your wireless home network or any WiFi hotspot,  and makes online gaming and streaming video faster and more reliable

May the 802.11ac be a problem with ubuntu?

---

### Post by mörgæs on 2016-08-08
Are you able to post the file using a wired internet connection?

---

### Post by gabrielbeauchemin on 2016-08-08
probably but I dont know how to do this via console

---

### Post by mörgæs on 2016-08-09
Keep trying. Live boot of something other than Mate? Live boot with and without mouse attached?

---

