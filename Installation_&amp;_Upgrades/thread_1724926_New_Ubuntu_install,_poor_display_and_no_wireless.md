---
title: "New Ubuntu install, poor display and no wireless"
date: 2011-04-09
forum: Installation &amp; Upgrades
---

### Post by EriktheAwful on 2011-04-09
I'm almost a complete noob when it comes to Linux. All my computers 'til now  have been Windows boxes (3.1 on up to XP). I do know a little, I've  tried to switch to Linux since RedHat 7.2 but never got this far (I can  connect to the Internet!). I currently have two issues I really need to  get past this weekend, or I'll be forced to spend $110 on Windows 7 -  which I REALLY don't want to do. I can't get the display right, and I  can't get the wireless working.

My computer is an AMD Zacate on  an ASUS motherboard with integrated graphics (ATI Raedon 6380, if I  remember correctly from this afternoon). I'm using an Insignia 1080p TV  as my sole monitor. The wireless card is a  Zonet ZEW1642S which uses  the Ralink RT3062 chipset.

Today I finally got the monitor to  display in 1920x1080. I updated the ATI drivers (HDMI sound started  working after I installed them) and downloaded Catalyst. I've been  trying to get through the xrandr instructions to get the screen to fit,  as I can't see the top and bottom bars. Also, I think it's displaying in  1080i instead of 1080p. Text quality is atrocious compared to the  1024x768 resolution it had earlier. The screen refresh is terrible.

I opened terminal, inputted "xrandr" and got:```
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 1920 x 1920
DFP1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 698mm x 392mm
   1920x1080      30.0*+   30.0  
   1776x1000      30.0  
   1680x1050      30.0     30.0  
   1400x1050      30.0     30.0  
   1600x900       30.0  
   1280x1024      30.0     30.0  
   1440x900       30.0  
   1280x960       30.0  
   1280x768       59.9  
   1280x720       60.0     59.9  
   1024x768       75.0     70.1     60.0  
   1152x648       60.0  
   1024x600       75.0     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   800x480        72.2     75.0     60.3     56.2  
   720x480        30.0     60.0     30.0     59.9  
   640x480        75.0     72.8     60.0     59.9  
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 disconnected (normal left inverted right x axis y axis)

```"cvt 1920 1080" gave me```
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline  "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120  -hsync +vsync
```I inputted "xrandr --newmode "1920x1080_60.00"   173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync" with no  problem, xrandr now gives```
Screen 0: minimum 320 x 200, current 1920  x 1080, maximum 1920 x 1920
DFP1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 698mm x 392mm
   1920x1080      30.0*+   30.0  
   1776x1000      30.0  
   1680x1050      30.0     30.0  
   1400x1050      30.0     30.0  
   1600x900       30.0  
   1280x1024      30.0     30.0  
   1440x900       30.0  
   1280x960       30.0  
   1280x768       59.9  
   1280x720       60.0     59.9  
   1024x768       75.0     70.1     60.0  
   1152x648       60.0  
   1024x600       75.0     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   800x480        72.2     75.0     60.3     56.2  
   720x480        30.0     60.0     30.0     59.9  
   640x480        75.0     72.8     60.0     59.9  
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 disconnected (normal left inverted right x axis y axis)
  1920x1080_60.00 (0x8f)  173.0MHz
        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock   67.2KHz
        v: height 1080 start 1083 end 1088 total 1120           clock   60.0Hz

```I  inputted "xrandr --addmode DFP1 1920x1080_60.00" and got this error  message:```
X Error of failed request:  BadMatch (invalid parameter  attributes)
  Major opcode of failed request:  155 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  27
   Current serial number in output stream:  28
```So I tried "xrandr  --output 1680x1000_30.00" and "xrandr -output 1680x1000" and  got```
warning: output 1680x1050 not found; ignoring
```I  tried using Catalyst, but it shows a preferred resolution of 4000x4000  and preferred refresh rate of 160hz (TV is supposed to be 60hz). It  gives me an option of 2560x1280, 70hz, and 120hz, but I can't make  changes.

My second issue is that I can't get the wireless network  up and running. Right now I have a CAT10 strung along the floor, and  the kids and dog keep kicking it free. If I get the wireless fixed I can  probably avoid buying Windows 7 - the wife's not a fan of the cable  duct-taped to our floor. It's a  Zonet ZEW1642S which uses the Ralink  RT3062 chipset. I used gedit to add several items to the blacklist. 

"lspci -nn" gives```
06:00.0 Network controller [0280]: RaLink Device [1814:3062]
```Earlier today I added ```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb
``` to the blacklist, but I'm not sure that it did anything.

I installed wicd, but it doesn't show a wireless connection.

I feel so clueless...

---

### Post by BicyclerBoy on 2011-04-09
Did you see this thread..

[http://ubuntuforums.org/showthread.php?p=10054976A](http://ubuntuforums.org/showthread.php?p=10054976A)
They were blacklisting in another file as well..

lsmod  or dmesg
will (help) reveal what module is load for the h/w..

I not sure about the exact mode name to use with --addmode "mode" but AFAIK you do not add the refresh rate to the end of internal mode names...

i.e. "1680x1050"  is good  "1680x1050_60" is bad unless you have defined that as new mode..

Try reduced vertical blanking modeline as most digital connections prefer it..
cvt -r 1920 1080 60

Search in 
/var/log/Xorg.0.log    for X server stuff.

Sorry not used xrandr seriously before & wifi on my netbook was an easy fix..

---

### Post by EriktheAwful on 2011-04-09
For some reason this morning System/Preferences/Monitors decided to start showing more options. I set my screen to 1776x1000 and it fits nicely with a little unused border. Text still looks crappy, and the refresh rate is running at 30hz, but it's definitely liveable.

I ran lsmod and got the following:```
Module                  Size  Used by
binfmt_misc             7984  1 
snd_hda_codec_realtek   300173  1 
fglrx                2730709  3 
snd_hda_codec_atihdmi     3079  1 
snd_hda_intel          26147  2 
snd_hda_codec         100951  3 snd_hda_codec_realtek,snd_hda_codec_atihdmi,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_seq_midi            5932  0 
eeepc_wmi               3571  0 
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
ppdev                   6804  0 
lp                     10201  0 
sparse_keymap           3837  1 eeepc_wmi
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             30086  1 
snd                    64181  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
i2c_piix4              10047  0 
parport                37032  3 ppdev,lp,parport_pc
xhci_hcd               60496  0 
usbhid                 42030  0 
firewire_ohci          24839  0 
hid                    84710  1 usbhid
ahci                   22210  2 
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  1 firewire_core
pata_atiixp             4405  0 
r8169                  42254  0 
mii                     5261  1 r8169
libahci                26148  1 ahci

```It looks like r8169 is the motherboard-integrated wired connection, and the wireless card isn't showing at all. I'm still waking up, so I'll fart around with it some more and post. What's the Ubuntu equivalent of "hardware manager"?

---

### Post by EriktheAwful on 2011-04-09
The TV is definitely running interlaced. When I leave the computer and come back to it, the TV wakes up showing "1080i". Not sure why or how to fix that.

I've tried getting to Ralink's website for drivers, but apparently it's down. Is there an alternate source for their drivers?

Edit:
Found a setting in the TV's menu for "Overscan". It says to turn it off when using the TV as a monitor. I turned it off and I'm running 1920x1080 right to the edges of the screen. I guess not getting a manual is the big downside to buying a discontinued store-display monitor cheap.

I I got to [http://web.ralinktech.com/ralink/Home/Support/Linux.html](http://web.ralinktech.com/ralink/Home/Support/Linux.html). The connection is really wonky. They don't list a driver for RT306x hardware. I'll peruse some more.

---

### Post by BicyclerBoy on 2011-04-09
Your wifi card needs firmware package..
The driver reloads the firmware at every cold boot.

Do you have the non-free firmware package installed (synaptic - linux firmware) ?

You need to search thru 
**dmesg**
look in  std output for firmware loaded cold start etc.. 

Overscan off is correct with PC video use..

Did you try the reduced vertical blanking CVT timing formula ?

You would be well advised to **not do** the windows thing .. grabbing software/firmware/drivers from anywhere (inc vendors).
It can all go badly wrong..
You would need to compile a kernel module against your current kernel version etc etc..

---

### Post by EriktheAwful on 2011-04-09
>  Did you try the reduced vertical blanking CVT timing formula ?Sorry, I forgot to tell the outcome of that. I tried "cvt -r 1920 1080 60" and got```
# 1920x1080 59.93 Hz (CVT 2.07M9-R) hsync: 66.59 kHz; pclk: 138.50 MHz
Modeline "1920x1080R"  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync
```I inputted "xrandr --newmode "1920x1080R"  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync",

then "xrandr --addmode DFP1 1920x1080",

and finally "xrandr --output 1920x1080_60.00"

and got "warning: output 1920x1080_60.00 not found; ignoring",

so I inputted "xrandr --output 1920x1080"

and got "warning: output 1920x1080 not found; ignoring"

"xrandr" now gives me```
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 1920 x 1920
DFP1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 698mm x 392mm
   1920x1080      30.0*+   30.0  
   1776x1000      30.0  
   1680x1050      30.0     30.0  
   1400x1050      30.0     30.0  
   1600x900       30.0  
   1280x1024      30.0     30.0  
   1440x900       30.0  
   1280x960       30.0  
   1280x768       59.9  
   1280x720       60.0     59.9  
   1024x768       75.0     70.1     60.0  
   1152x648       60.0  
   1024x600       75.0     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   800x480        72.2     75.0     60.3     56.2  
   720x480        30.0     60.0     30.0     59.9  
   640x480        75.0     72.8     60.0     59.9  
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 disconnected (normal left inverted right x axis y axis)
  1920x1080R (0x8f)  138.5MHz
        h: width  1920 start 1968 end 2000 total 2080 skew    0 clock   66.6KHz
        v: height 1080 start 1083 end 1088 total 1111           clock   59.9Hz
```How do I switch the output to the new setting?
> Your wifi card needs firmware package..
The driver reloads the firmware at every cold boot.

Do you have the non-free firmware package installed?

You need to search thru 
**dmesg**
look in  std output for firmware loaded cold start etc..I ran dmesg and got more info than can fit in the terminal window. I have no idea what I'm looking for in dmesg that relates to the firmware. I searched for "firmware" and "cold start" and it didn't return any hits, so what should I be looking for? Non-free firmware package? I take it that's the "linux-firmware-nonfree" v1.9 in the Synaptic Package Manager? I haven't installed it yet, is that the one I need?

---

### Post by BicyclerBoy on 2011-04-10
Yep.
linux firmware nonfree is the one..

your xrandr --output is wrong
try

xrandr --newmode "1920x1080R"  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync
xrandr --addmode DFP1 1920x1080R
xrandr --output DFP1 --mode 1920x1080R

new mode: defines the timing formula..
addmode: adds it to the mode pool for that wired port (& validates/checks its possible)
output mode: sets it to that wired port now.


You can search dmesg stdout (or any cmd output) with
dmseg | grep firmware

---

### Post by EriktheAwful on 2011-04-10
I installed the linux firmware non-free package. I tinkered around with System/Preferences/Network Connections, but it's still not using the wireless card. "dmesg | grep firmware" returns nothing.

I tried xrandr again, and:
xrandr --newmode "1920x1080R"  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync
xrandr --addmode DFP1 1920x1080R

gives me```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  155 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  27
  Current serial number in output stream:  28

```The following goes through just fine but accomplishes nothing.
xrandr --addmode DFP1 1920x1080
xrandr --output DFP1 --mode 1920x1080

> new mode: defines the timing formula..
addmode: adds it to the mode pool for that wired port (& validates/checks its possible)
output mode: sets it to that wired port now.Thanks! I learn a lot better when I understand what it's doing. That was pretty much what I had figured was going on, and it's good to have some verification.

---

### Post by BicyclerBoy on 2011-04-10
I think you will need to reboot to get the firmware loading to happen (if it will)..
Else you have to modprobe the driver..
look for clues in ..
lspci
lspci | grep wifi
lsmod
dmesg | grep wifi
dmesg | grep firmware

Don't know what the problem is with xrandr..truely horrible program with meaningless error messages (except to the programmer)..may have to do it the better old way via xorg.conf file.

---

### Post by EriktheAwful on 2011-04-10
Rebooting didn't make any difference. What is modprobe?

"lspci | grep wifi", "dmesg | grep wifi", and "dmesg | grep firmware" all return nothing.

lspci returns:```
00:00.0 Host bridge: Advanced Micro Devices [AMD] Device 1510
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9802
00:01.1 Audio device: ATI Technologies Inc Device 1314
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Device 1512
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (rev 40)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
00:15.1 PCI bridge: ATI Technologies Inc Device 43a1
00:15.2 PCI bridge: ATI Technologies Inc Device 43a2
00:15.3 PCI bridge: ATI Technologies Inc Device 43a3
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Device 1700 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Device 1701
00:18.2 Host bridge: Advanced Micro Devices [AMD] Device 1702
00:18.3 Host bridge: Advanced Micro Devices [AMD] Device 1703
00:18.4 Host bridge: Advanced Micro Devices [AMD] Device 1704
00:18.5 Host bridge: Advanced Micro Devices [AMD] Device 1718
00:18.6 Host bridge: Advanced Micro Devices [AMD] Device 1716
00:18.7 Host bridge: Advanced Micro Devices [AMD] Device 1719
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
05:00.0 PCI bridge: Device 1b21:1080 (rev 01)
06:00.0 Network controller: RaLink Device 3062
06:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
07:00.0 USB Controller: Device 1b21:1042
```So the computer does recognize that it has a RaLink 3062 card.

lsmod returns:```
Module                  Size  Used by
nls_iso8859_1           4657  1 
nls_cp437               6375  1 
vfat                   10954  1 
fat                    56244  1 vfat
usb_storage            50436  1 
binfmt_misc             7984  1 
snd_hda_codec_realtek   300173  1 
snd_hda_codec_atihdmi     3079  1 
snd_hda_intel          26147  2 
snd_hda_codec         100951  3 snd_hda_codec_realtek,snd_hda_codec_atihdmi,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
eeepc_wmi               3571  0 
ppdev                   6804  0 
sparse_keymap           3837  1 eeepc_wmi
fglrx                2730709  3 
snd                    64181  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
xhci_hcd               60496  0 
parport_pc             30086  1 
soundcore               1240  1 snd
i2c_piix4              10047  0 
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
lp                     10201  0 
parport                37032  3 ppdev,parport_pc,lp
firewire_ohci          24839  0 
firewire_core          54327  1 firewire_ohci
usbhid                 42030  0 
hid                    84710  1 usbhid
ahci                   22210  2 
crc_itu_t               1739  1 firewire_core
r8169                  42254  0 
mii                     5261  1 r8169
pata_atiixp             4405  0 
libahci                26148  1 ahci
```

Should I re-ask my questions in the "Multimedia & Video" and "Networking & Wireless" forums?

---

### Post by EriktheAwful on 2011-04-11
BicyclerBoy, thanks for your help. I've re-asked my questions in the  "Multimedia & Video" and "Networking & Wireless" forums. I'm already feeling a lot more comfortable with Ubuntu, but I know I still have a lot to learn.

---

### Post by BicyclerBoy on 2011-04-13
Divide & conquer..

Should find someone who uses xrandr with ati...

I have found it useless with nvidia h/w.

---

