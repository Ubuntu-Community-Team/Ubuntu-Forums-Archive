---
title: "Ubuntu and Lenovo Yoga 500 Compatibility???"
date: 2015-12-11
forum: Installation &amp; Upgrades
---

### Post by jbrice on 2015-12-11
Am looking at obtaining a Lenovo Yoga 500 14" as the physical format suits my needs. Having looked around at the usual sources I have been unable to find any comprehensive information of the compatibility of current flavours of Ubuntu with this hardware. So I would be pleased to hear from anyone who has succeeded in installing Ubuntu. Equally useful to hear from anyone who has tried and found problems!

TIA

---

### Post by Robert_Kampas on 2015-12-16
I had purchased exactly same laptop few days ago. It looks nice, specs are good and price is low here in UK so I was happy to find it at Curry's PC World store. It came with Windows 10 pre-installed. I already have dedicated laptop with Windows for gaming and stuff so I made a backup image and formatted my HDD. Then I changed all UEFI settings back to Legacy and installed Ubuntu 15 from external CD. Installation went flawlessly, no issues. Then I restarted, updated and everything worked just fine. I was quite worried that some of the hardware will not work (as it happened many times before) but this time I was very impressed how everything worked straight out of the box. Wifi card, trackpad, sound and even touch screen worked without any additional drivers! I really did not expect touchsreen to work but after updating Ubuntu it did. I only had it for few days but very happy with my experience so far. I still have to install nVidia drivers and not sure what to do about Dolby Sound stuff but overall I'm pleased with how it works.

---

### Post by jbrice on 2015-12-16
Robert,
Many thanks for taking the time to write such a complete and helpful reply. Doubly helpful as I had one delivered from the same supplier yesterday - an act of faith in Ubuntu! First impressions - like yours - of a very nice piece of hardware. Pity the pre-installed software (spyware?!) does not live up to the hardware. 

Having had a quick first explore of possibilities, had look from within Win10 to see how much I could shrink the existing partitions to find room for a dual-boot Linux install. The maximum free disk offered by Windows disk manager was 450GB - on a 1TB hard disk!

As I have a nearly new SSD to hand I think I'll follow your lead and do a clean install on that. Then I can put the original SSHD to one side for a while so I can pop it back in should there be any any need for a guarantee claim etc.

Don't forget that Lenovo are doing a £100 cashback on that product. Note the "gotcha" is that you have to claim between 21 and 51 days after the invoice date.

Thanks again and enjoy your new Yoga.

JB

---

### Post by jbrice on 2016-01-19
Update for anyone interested...

Have now set up two Lenovo Yoga 500s - one for myself and one for a family member. Both installed with Linux Mint 17.3 and very pleased with the end result. There are a couple of things that do not work but these are minor or not deal-breakers for our particular use.

- Wifi only worked after bumping the Linux kernel up to 4.2 (easily done with the Linux Mint Update Manager).

- Touch screen is only "mouse-style" click and drag but that's fine as I need a laptop and not a tablet. Touch works really well with Kodi media player (see below).

-The 1920x1080 screen is very good but not quite up to using the Cinnamon HiDpi setting. Instead used Cinnamon standard resolution with up-scaling of font sizes and panel widths to suit.

- Set up a simple script (just search the web to find examples) to rotate screen by 180deg.  on pressing key combination so that the device can be used in "tent" mode as a very nice media player. Installed the current version (not the old version offered by Software Manager) of Kodi as media player app. and this works really well with the touch screen.

- All buttons work except for brightness up/down function keys. Have tried all the fixes I could find but to no avail. The Cinnamon screen brightness applet doesn't work either. BUT the brightness slider on the Cinnamon power/battery indicator works fine and suffices to control screen brightness. :)) 

- Swapping between Intel (low power) and Nvidia (high performance) video chips needs a log in/out, but as the Intel video plays 1080-line HDTV without breaking into a sweat so I don't see the Nvidia video being used too often. Having said that, pleased to find that the Nvidia graphics will play 4K UHDTV at what looks like full frame rate in Kodi (YMMV according to the chip set in your laptop).

---

### Post by Andre_Katov on 2016-01-22
[COLOR=#DD4814][COLOR=#000000][jbrice]("http://ubuntuforums.org/member.php?u=297940"),

Thanks for that information - you saved me a lot of time.
 I also couldn't find any solution for Brightness up/down via f11 f12 keys but as you've mentioned , 
it works great trough brightness settings so that (+-) fine untill someone finds a solution.

[/COLOR][/COLOR]

---

### Post by Fiorela_C on 2016-02-14
Hi jbrice and all,
I am new to Ubuntu, or I might say I am still a new Linux user. I have bought the same Lenovo yoga 500 because the hardware details appealed to me for the price, but I am having some problems to install Linux on it. I have not been able to find much about this lenovo yoga 500 machine and linux except for this thread. I am wondering whether you could explain more in detail how you did it or point me to some other link, and whether you are still satisfied with the end result (almost a month after your buy). Remaining with the machine with the default Windows 10 is not an option to me, so I have been also thinking about returning it or selling it if I do not succeed to install Linux on it. I have not used it much since I bought it since I am hating to start the machine every time just because windows 10 gets into my nerves. 
I will be very grateful for any reply or suggestions,
Thanks a lot,:D
Fiorela

---

### Post by Vidar30 on 2016-02-14
I recently bought a Lenovo Yoga 500 and its basically not compatible with Ubuntu/Linux. I've tried 15.10 but am now running Ubuntu 16.04 from USB and it's slow, so slow that its not usable. Can't see anything relevant in the log files either - help!

---

### Post by virgosun on 2016-04-09
Lenovo Yoga 500 have many different variation with different peripheral chips.
For mine, I have to say only Ubuntu Gnome 3.18 work with autorotation touch screen. Wifi/BT not work. See my specs [https://www.youtube.com/watch?v=lNFKSXUT7bk](https://www.youtube.com/watch?v=lNFKSXUT7bk)

---

### Post by xsobotkaj on 2016-04-24
I would like to contribute to by my experience with Ubuntu and **Lenovo YOGA 500-15IBD** (product number 80N600EQCK). Because I'm using Ubuntu GNOME 14.04 on two laptops and I read, that GNOME is one of the best choices for touch screen I decided to try Ubuntu GNOME 15.10 and 16.04. Everything I need seemed ok until I found out that WiFi don't work. I made some research, but it seems, that it will be big issue [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1432869](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1432869), because in this time there are **not drivers for BCM 43162 [14e4:43ae] rev 02**. My last try with ndiswrapper was not successful too, because there are no Windows XP drivers. Now I'm waiting for USB WiFi adapter and hope, that in near future driver will be available.** So be careful with Yoga spec - often they have Broadcom WiFi, which have to be very problematic**. Also I didn't test GeForce graphic as I don't care about graphical power.

---

### Post by xsobotkaj on 2016-06-06
Finally I solved lack of drivers for BCM 43162 [14e4:43ae] rev 02. by replacing WiFi card with Intel Dual band Wireless-AC 7260 7260NGW Bluetooth BT4.0 NGFF 867Mbps Wifi Card. Bought from [http://www.ebay.com/itm/171173641839](http://www.ebay.com/itm/171173641839) This card works fine in Ubuntu GNOME 16.04. If you plan change the card too, be careful, some cards might be blocked, but this one works in my laptop. More information here [https://www.bios-mods.com/forum/Thread-REQUEST-BDCN63WW-lenovo-yoga-500](https://www.bios-mods.com/forum/Thread-REQUEST-BDCN63WW-lenovo-yoga-500)

---

### Post by virgosun on 2016-08-19
I bought 2 Wifi USB : TP Link 727 for Ubuntu and Tenda W300 for macOS.
More over, my Bt4.0 low power seems odd, working very erratic so Lenovo replace it for me by a QCA61x4 combo.
Fortunately both wifi and BT now work OOB with Ubuntu Gnome 16.04 LTS
This mean they also work oob with Android x86 6.0 linux kernel, because I need androidx86 for DJI Go
I need IOS for yamaha page turner app, if anynone evrer know how to run it on intel cpu?

---

### Post by dr.anandravi on 2016-11-13
Hi!
I have also purchased the same machine and unable to install 16.04 in UEFI mode and in legacy mode installation it automatically boots in Windows. please help!

---

