---
title: "wireless &quot;disabled&quot;"
date: 2010-02-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by libihero on 2010-02-27
in lucid, my wireless wont work, stating "wireless disabled".  i think the problem is with the kernel, since when i tried to download the 2.6.32 kernel in karmic, i had the same problem

---

### Post by psyke83 on 2010-02-27
It could be a simple configuration issue.

Right-click on the NetworkManager applet icon, and make sure the checkmark is ticked beside "Enable Wireless".

---

### Post by libihero on 2010-02-28
it wont let me, it's completely grayed out

---

### Post by garvinrick4 on 2010-02-28
I would think to purge program then clean cache and reinstall from repository before doing anything major. Make sure you sudo apt-get clean before reinstall.

---

### Post by libihero on 2010-02-28
could u clarify?

---

### Post by ikt on 2010-02-28
give WICD a try.

---

### Post by slymi2005 on 2010-02-28
If I may butt in, what exactly is the difference between the default network manager and wicd? I had constant wireless issues with 9.10 so I upgraded on thursday and I just had my first issue again today. Ubuntu sees my wireless connection but it just won't connect.

---

### Post by ikt on 2010-02-28
> **slymi2005 said:**
> If I may butt in, what exactly is the difference between the default network manager and wicd?

[https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)

- Some of Wicd's features include:
- No Gnome dependencies (although it does require GTK), so it is easy to use in XFCE, Fluxbox, Openbox, Enlightenment, etc.
- Ability to connect to wired (Ethernet only, no PPPoE/DSL support yet) and wireless networks
- Profiles for each wireless network and wired network
- Many encryption schemes, some of which include WEP/WPA/WPA2 (and you can add your own)
- Remains compatible with wireless-tools
- Tray icon showing network activity and signal strength
- A full-featured console interface

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by bikeboy on 2010-02-28
Sounds like nothing WICD is likely to fix. I'd say it's a kernel issue, and Ubuntu isn't detecting the card correctly. I say this form experience.

Could you tell us what sort of chipset the card is (perhaps with the output of lspic) and provide the output of lsmod?

---

### Post by libihero on 2010-02-28
my lspci:
```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

```

and my lsmod
```
Module                  Size  Used by
binfmt_misc             8356  1 
joydev                 10240  0 
rndis_wlan             21476  0 
arc4                    1660  2 
ecb                     2524  2 
snd_hda_codec_atihdmi     3356  1 
rndis_host              7356  1 rndis_wlan
cdc_ether               4924  1 rndis_host
snd_seq_dummy           2656  0 
snd_hda_codec_idt      59844  1 
rtl8187                50624  0 
snd_seq_oss            28576  0 
mac80211              181140  1 rtl8187
led_class               4096  1 rtl8187
eeprom_93cx6            1916  1 rtl8187
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
usbnet                 17188  3 rndis_wlan,rndis_host,cdc_ether
iptable_filter          3100  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_hda_intel          26920  2 
snd_hda_codec          75708  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
cfg80211               93052  3 rndis_wlan,rtl8187,mac80211
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
psmouse                56500  0 
serio_raw               5280  0 
snd_timer              22276  2 snd_seq,snd_pcm
snd                    59204  16 snd_hda_codec_idt,snd_seq_oss,snd_rawmidi,snd_seq,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_seq_device,snd_pcm,snd_timer
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
k8temp                  4188  0 
shpchp                 32272  0 
i2c_piix4               9932  0 
lp                      8964  0 
parport                35340  1 lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usb_storage            52576  0 
video                  19380  0 
output                  2780  1 video
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
r8169                  32064  0 
mii                     5212  2 usbnet,r8169
ati_agp                 6760  0 
agpgart                34988  3 ttm,drm,ati_agp

```

---

### Post by libihero on 2010-02-28
btw i did this in my karmic... let me know if you need it in lucid also

---

### Post by ikt on 2010-02-28
> **bikeboy said:**
> Sounds like nothing WICD is likely to fix. I'd say it's a kernel issue, and Ubuntu isn't detecting the card correctly. I say this form experience.

Could you tell us what sort of chipset the card is (perhaps with the output of lspic) and provide the output of lsmod?

I had a similar issue in jaunty and switching to wicd worked until karmic where nm decided to play nice.

---

### Post by diebels on 2010-02-28
> **libihero said:**
> it wont let me, it's completely grayed out
Try ```
iwconfig
```

---

### Post by ikt on 2010-02-28
off topic but I had an annoying issue where network manager would say my wireless was disabled on boot, so I would have to right click and enable the wireless, then a pop up would come up asking for my system password, which I would then enter and then it would connect...

just installed wicd and it connects automatically on bootup without the pop up or having to 'enable wireless'.

+1 for wicd.

Though strange I had to remove network-manager, it wasn't done automatically when installing wicd.

---

### Post by diebels on 2010-02-28
> **ikt said:**
> off topic but I had an annoying issue where network manager would say my wireless was disabled on boot, so I would have to right click and enable the wireless, then a pop up would come up asking for my system password, which I would then enter and then it would connect...

just installed wicd and it connects automatically on bootup without the pop up or having to 'enable wireless'.

+1 for wicd.

Though strange I had to remove network-manager, it wasn't done automatically when installing wicd.

It's nice that people have good experiences with wicd.  But as NetworkManager is the default, we should try to get that working on all configurations.  Give it a try and ask for help if you're stuck.

I used to hate NetworkManager myself as it kept asking me for passwords since I've always used autologin.  Now we've had the nice "Available to all users" checkbox for a while to solve that problem.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=148598&stc=1&d=1267380353[/IMG]

---

### Post by libihero on 2010-02-28
iwconfig gives me:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth1      no wireless extensions.


```

in lucid of course ;)

---

### Post by xblong on 2010-02-28
I think the problem might be caused by the installed driver for your Realtek wireless adapter. If your adapter uses a Ralink device you might need the latest Ralink driver. I had a similar problem and was able to fix it:

Find out which Ralink device your Realtek adapter has.

Go to [www.ralink.com](www.ralink.com) and download the source code for the latest driver for that Ralink device. 

Extract the source code. Modify the config.mk file 

change two items from no to yes

1.change
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=n
to
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

2.and change
# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n
to
# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

3. Backup the original driver, Example: rename rtxxxsta.ko to rtxxxsta.ko.bk in directory
/lib/modules/2.6.32-14-generic/kernel/drivers/net/wireless

4. sudo make && make install

5. reboot

---

### Post by libihero on 2010-02-28
haha ok im a total noob with driver stuff, how do i figure out what driver i have?

---

### Post by xblong on 2010-02-28
Your Realtek adapter does NOT use a Ralink driver, so my previous post won't help. 

Here is a link to Realtek where you can download the correct driver for the RTL8101E/RTL8102E PCI Express Fast Ethernet controller.

[http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false)

Pick one of the download sites for
LINUX driver for kernel 2.6.X and 2.4.X (Support x86 and x64)

It comes with a readme file that has instructions. To simplify things you should disable any other built-in wireless or wired Ethernet devices. Usually the motherboard's BIOS Setup program has on option to enable/disable any built-in networking devices. Then follow the readme file's instructions up to the point where it tells you 

"You can check whether the driver is loaded by using following commands." 

Follow the commands and if the driver is loaded try rebooting then using Ubuntu's System->Preferences->Network Connections to connect.

---

### Post by bikeboy on 2010-02-28
> **libihero said:**
> btw i did this in my karmic... let me know if you need it in lucid also

Your lspci doesn't show the wireless card afaict. Are you using a USB wireless device? Nevertheless, the lsmod indicates you're using a Realtek device, as mentioned earlier. Not sure how up-to-date this is, but it should at least provide a little info - [http://linuxwireless.org/en/users/Drivers/rtl8187](http://linuxwireless.org/en/users/Drivers/rtl8187)

> **ikt said:**
> I had a similar issue in jaunty and switching to wicd worked until karmic where nm decided to play nice.

Don't get me wrong, I'm using WICD right now. However when NM has greyed out wireless it tends to mean the device isn't functioning properly at the hardware (kernel) level. I've had this issue coming out of suspend and the only way to fix it without rebooting was to remove then re-insert the module for my card (rt61pci in this case). I'm no debugger or expert though, so YMMV.

> **xblong said:**
> Your Realtek adapter does NOT use a Ralink driver, so my previous post won't help. 

Here is a link to Realtek where you can download the correct driver for the RTL8101E/RTL8102E PCI Express Fast Ethernet controller.



I think that's the *wired* LAN not the wireless.

---

### Post by KrazyPenguin on 2010-02-28
I had a problem connecting as well last week.

I dunno how I really fixed it, but I connected to a "wired" connection, and then entered in a new wireless connection, unplugged it and it worked.

Maybe the settings were screwed and somehow the became unscrewed????
:shock:

---

### Post by ikt on 2010-03-03
> **diebels said:**
> I used to hate NetworkManager myself as it kept asking me for passwords since I've always used autologin.  Now we've had the nice "Available to all users" checkbox for a while to solve that problem.

That didn't actually fix the issue in karmic, however lucky for me the issue is fixed in 10.04/nm 0.8+

> **bikeboy said:**
> I've had this issue coming out of suspend and the only way to fix it without rebooting was to remove then re-insert the module for my card (rt61pci in this case). I'm no debugger or expert though, so YMMV.

I don't have a module, it's inbuilt.

---

### Post by libihero on 2010-03-04
i'm too scared to download drivers unless i really have to.  is it possible that when the final version of lucid comes out, those drivers would be there?

---

### Post by QwUo173Hy on 2010-03-04
I experienced the same symptoms as the libihero, although not necessarily for the same reasons. Alpha 3 was fine until an update left me in the same situation as you.

But I just re-installed Alpha 3 and ran the update a few days later. The newer updates didn't have this problem (although as of yesterday, I can't connect to the wireless station that NM can see).

HTH

---

### Post by QwUo173Hy on 2010-03-05
And after another update today, it's all working again. I'll cancel that bug report.

---

### Post by Trinity33 on 2010-03-05
> **libihero said:**
> in lucid, my wireless wont work, stating "wireless disabled".  i think the problem is with the kernel, since when i tried to download the 2.6.32 kernel in karmic, i had the same problem

had the same problem with lucid and karmic card wasnt recognised by network manager so i used my IQ u should sometimes too. uninstall network manager and install wicd and see if u got everything working.

---

### Post by libihero on 2010-03-19
i tried it in the beta 1 and its still a regression, how do i file a bug report?

---

### Post by cariboo on 2010-03-19
Is your device USB? Can you also post the output of:

```
sudo lshw -C network
```

---

### Post by libihero on 2010-03-19
do u mean am i loading ubuntu from a usb? if thats the question then yes i am.  if your asking if my wireless is from a usb then no its not, its just on my laptop. 
here is the output i got
```
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 01
       serial: 00:e0:b8:f9:70:9c
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=141.217.223.150 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:29 ioport:a000(size=256) memory:f8200000-f8200fff memory:80000000-8001ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:44:c7:2f:50
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```
i know the problem has something to do with the kernel 2.6.32.  when i update the kernel on karmic its the same problem :(

---

### Post by andrek on 2010-03-21
And I have a bit different problem with network manager. It might sound silly, but what does an icon with a red exclamation mark mean (in the tray)? Does it indicate a low-signal connection? If so, something is wrong here - I've got 95%+ signal strength on Windows, also the quality of the connection is good here on linux, too. So.. is this somehow related to a wrong icon, or is this a bug?

---

### Post by jaoc223 on 2010-03-21
I have the same issue with the red exclamation mark, my signal is fine in mac osx, and seems to be fine on beta 1, I read somewhere on the forums yesterday that this is a bug in nm. My other issue was mentioned above. I have wireless working, but after turning off my box and coming back to it the next morning nm wireless shows I'm connected, but cannot resolve any hosts, I then connect wired, unplug and then wireless is ok. Anyone else having this issue? I'm using beta 1 with the 2.6.32-14 kernel. I installed from an alpha3 build from Mar.15th, and updated to beta 1, because the 2.6.32-20 kernel wouldn't allow me to work with wireless when I installed from the beta 1 release from Mar.17th. I'm really puzzled as to why my wireless works ok all day and then the next morning it seems to need a wired jump start to get it going. I should mention at night when I shutdown I power my router off by unplugging the A/C, and plug it back in the morning. 
after I posted this, I thought maybe unplugging my router is causing the problem with wireless needing a wired jump start, but I just tested this by shutting down my computer unplugging the A/C, then unplugging the A/C from the router, I waited about 10 minutes plugged comp and router back in, booted up and wireless is connecting, as I said I thought unplugging my router at night was maybe causing my issue. Any thoughts or ideas are greatly appreciated. Thanks in advance.

from lsmod i have this 

 *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 05
       serial: 00:1f:5b:d1:1b:b8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.7 latency=0 multicast=yes                     wireless=IEEE 802.11abgn
       resources: irq:16 memory:50200000-50203fff
  *-network
       description: Ethernet interface
       product: Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 13
       serial: 00:22:41:21:3b:e4
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0        link=no multicast=yes port=twisted pair
       resources: irq:29 memory:50100000-50103fff ioport:5000(size=256) memory:50d00000-50d1ffff(prefetchable)

under my hardware drivers STA Broadcom I see this

These package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware.

Is BCM4328 802.11a/b/g/n supported here?


from blacklist.conf i see this 

# replaced by b43 and ssb.
blacklist bcm43xx

Does that mean my BCM4328 802.11a/b/g/n is not being loaded when lucid boots?

---

### Post by libihero on 2010-03-21
can anyone just fill me in on how to fill a bug report for it
this no wifi is the make or break issue for me with lucid, kind of hard to use a laptop that has no wifi lol

---

### Post by libihero on 2010-03-22
bump :(

---

### Post by QwUo173Hy on 2010-03-22
I don't like seeing replies like the one I'm about to give, but it's the best I can offer.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

And make your report based on the outcome of those tests. I'm SURE there's a better way, but it's the best I know how.

---

### Post by andrek on 2010-03-22
Just want to say that I got rid of the 'red exclamation mark problem' with changing to opensource Broadcom B43 driver (from the proprietary STA).

---

### Post by jaoc223 on 2010-03-22
andrek how do you install the opensource Broadcom B43? through synaptic?
did you remove proprietary first?

Thanks

---

### Post by andrek on 2010-03-22
I used "Hardware Drivers" application (jockey-gtk) - I removed the proprietary Broadcom driver using this handy tool, rebooted and installed the free one.

---

### Post by jaoc223 on 2010-03-22
Can you provide me with a link to the drivers?
Thanks

---

### Post by andrek on 2010-03-22
What kind of a link do you mean? Just open System -> Administration -> Hardware Drivers and use this tool to install the Broadcom B43 Wireless Driver. ( first make sure the Broadcom STA Wireless Driver is uninstalled - can be checked and done in Hardware Drivers tool as well )

---

### Post by jaoc223 on 2010-03-22
I'm a noobie andrek, I mean where do yoou get the opensource driver? I know how to remove the STA Broadcom driver, I just don't see the opnsource driver. I checked synaptic in I see b43 fwcutter. I apologize for my lack of knowledge.
Thanks

---

### Post by andrek on 2010-03-22
The Hardware Drivers tool doesn't show you the open-source driver? That's weird. Let me find it how to install it manually.

Yup, looks like 'b43-fwcutter' is the way to go. I haven't installed it manually by Synaptic but you may try:

> sudo sh /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

to install the driver. (if Synaptic hasn't done it already when installing b43-fwcutter - just make sure to reboot after its installation's done)

---

### Post by jaoc223 on 2010-03-22
ok. I did sudo sh /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
looks like it installed ok, I uninstalled the Broadcom STA, rebooted, went back to Hardware Drivers, but I still don't see the b43 driver.

---

### Post by jaoc223 on 2010-03-22
andrek I appreciate your help, but I can't seem to find the b43 fwcutter broadcom driver, the only one showing in hardware drivers is the broadcom STA driver. I installed the bcmwl kernel source for broadcom.so i need to blacklist the broadcom driver to get the b43 loaded?

---

### Post by libihero on 2010-03-22
SOLVED
hahahahaaha
so apparently according to this

"4.2.5. Driver looks ok, device disabled
Newer laptops come with features to disable the wireless radio to save battery when not in use. Usually this is switched by a FN+Fx key combo or specific button for the purpose. It is possible driver and everything is ok but the wireless device is in the disabled state and can't be used. Using the designated key(s) in linux sometimes does not work.
Usually this is apparent by running the lshw command you see *-network:1 DISABLED or wireless=radio off, or if you run the iwconfig command you see eth1      NOT READY!. So how do you rectify this? It varies so much the exact solution can't be put here in this document for all the different models. So...
Look at the LaptopTestingTeam page on the team wiki to see if your laptop is listed with any information.
Do a google search using terms such as manufacture, model, linux, wireless, enable, button, radio....etc. When searching and finding similar pages that don't help, use words that are used in those pages to help you search.
Go to the ubuntu forums and ask, maybe someone else has the same laptop and knows the work around.
Some laptops have a controller chip on the motherboard that is only accessible through a different OS. If you have turned off your WiFi card in a different operating system, you may have to boot back into that OS and enable the card before it is accessible to Linux."

so i looked at the function key and i looked at the F buttons and i found one that had a wireless and i just did the key combo and it worked
SO THANKS FOR LEADING ME TO THAT SITE :)

---

