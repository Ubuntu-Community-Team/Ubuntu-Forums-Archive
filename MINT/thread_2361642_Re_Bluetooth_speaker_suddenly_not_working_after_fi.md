---
title: "Re: Bluetooth speaker suddenly not working after firmware update"
date: 2017-05-18
forum: MINT
---

### Post by jamesleesmith on 2017-05-18
I should first of all mention that my OS is Linux Mint 18.1 and I have  the Cinnamon desktop environment and that the Bluetooth speaker I'm  having an issue with is the UE Boom 2.

Here's what I'm dealing with.

1. First of all, let me say that I haven't tried it with my Windoze computer yet (because I rarely use my Windows computer), but it does work with my cell phone, so I'm going to make the reasonable presumption that something about the new firmware is incompatible with something in LM 18.1

2. Here's my computer's information...

```
mac@mac-Lenovo-Y50-70-Touch ~ $ inxi -Fxzd
System:    Host: mac-Lenovo-Y50-70-Touch Kernel: 4.4.0-77-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Cinnamon 3.2.7 (Gtk 3.18.9) Distro: Linux Mint 18.1 Serena
Machine:   System: LENOVO product: 20349 v: Lenovo Y50-70 Touch
           Mobo: LENOVO model: Lenovo Y50-70 Touch v: 31900058Std
           Bios: LENOVO v: 9ECN43WW(V3.03) date: 08/12/2015
CPU:       Quad core Intel Core i7-4700HQ (-HT-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 19155
           clock speeds: max: 3400 MHz 1: 2727 MHz 2: 2939 MHz 3: 2668 MHz
           4: 2429 MHz 5: 3268 MHz 6: 2926 MHz 7: 2997 MHz 8: 2729 MHz
Graphics:  Card-1: Intel 4th Gen Core Processor Integrated Graphics Controller
           bus-ID: 00:02.0
           Card-2: NVIDIA GM107M [GeForce GTX 860M] bus-ID: 01:00.0
           Display Server: X.Org 1.18.4 driver: nvidia
           Resolution: 3840x2160@48.00hz
           GLX Renderer: GeForce GTX 860M/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 375.39 Direct Rendering: Yes
Audio:     Card-1 Intel 8 Series/C220 Series High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:03.0
           Sound: Advanced Linux Sound Architecture v: k4.4.0-77-generic
Network:   Card-1: Intel Wireless 7260 driver: iwlwifi bus-ID: 08:00.0
           IF: wlp8s0 state: up mac: <filter>
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: 3000 bus-ID: 09:00.0
           IF: enp9s0 state: down mac: <filter>
           Card-3: Atmel usb-ID: 003-002
           IF: null-if-id state: N/A speed: N/A duplex: N/A mac: N/A
Drives:    HDD Total Size: 2000.4GB (64.1% used)
           ID-1: USB /dev/sda model: TOURO_S size: 1000.2GB
           ID-2: /dev/sdb model: Crucial_CT1024MX size: 1000.2GB
           ID-3: /dev/mmcblk0 model: N/A size: 63.9GB
           Optical: No optical drives detected.
Partition: ID-1: / size: 442G used: 338G (81%) fs: ext4 dev: /dev/sdb5
           ID-2: swap-1 size: 17.09GB used: 0.00GB (0%) fs: swap dev: /dev/sdb6
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 59.0C mobo: N/A gpu: 0.0:51C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 255 Uptime: 3:41 Memory: 4570.6/15963.7MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.461) inxi: 2.2.35 

```

Ok, now let me explain (though you've no doubt guessed the problem):

I have this UE Boom 2 speaker that is great. I'd never done a firmware update to it, so I decided to do it the other day. The next time I used it with my laptop, the sound was really tinny. Very thin sound. No bass. Nothing but mid-range and highs. I was listening to a podcast, so I decided to not mess with it at that time. I assumed it would be an easy fix. 

This morning I tried to sort it out and I'm stumped. Here's what I did:

1. I went into Blueman and removed it from the list of Bluetooth devices. Then I went through the steps of searching for it and pairing it. It paired up, but the speaker never gave an indication that it was paired and if I go into sound settings, I don't see the speaker listed under devices as I did before.

2. I've tried uninstalling everything, rebooting everything, turning it off and then back on, etc.

3. I found a post about a similar problem on an Ubuntu forum, but the solution that worked for that guy didn't work for me.

Any help is appreciated.

Thank you

After googling, I found a few threads on various forums that weren't helpful at all. One Linux forum, however, gives me a glimmer of hope. I found this post in which the moderator gives the following advice:

> Try this. It usually works for me.

```
pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` off; sleep 2 ; echo -e "disconnect 88:C6:26:81:D7:CA\n quit"|bluetoothctl;sleep 5; echo -e "connect 88:C6:26:81:D7:CA\n quit"|bluetoothctl; sleep 5; pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` a2dp_sink

```

The forum member whom he was advising responded with elation. It worked!

Noticing that my UE BOOM 2 is associated with a different uh... address(?), I amended his suggested terminal command and tried it. This was the result:

```
mac@mac-Lenovo-Y50-70-Touch ~ $ pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` off; sleep 2 ; echo -e "disconnect 88:C6:26:C2:89:A1\n quit"|bluetoothctl;sleep 5; echo -e "connect 88:C6:26:C2:89:A1\n quit"|bluetoothctl; sleep 5; pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` a2dp_sink
You need to specify a profile by its name.
[NEW] Controller E8:2A:EA:57:8F:B8 mac-Lenovo-Y50-70-Touch [default]
[NEW] Device 88:C6:26:C2:89:A1 UE BOOM 2
[NEW] Device 00:11:67:00:04:DF Bluetooth Optical Mouse
[NEW] Device 08:21:EF:6D:93:00 Samsung Galaxy S7
[NEW] Device A0:02:DC:E0:6E:50 McFire
[bluetooth]# disconnect 88:C6:26:C2:89:A1
Attempting to disconnect from 88:C6:26:C2:89:A1
[bluetooth]#  quit
[DEL] Controller E8:2A:EA:57:8F:B8 mac-Lenovo-Y50-70-Touch [default]
[NEW] Controller E8:2A:EA:57:8F:B8 mac-Lenovo-Y50-70-Touch [default]
[NEW] Device 88:C6:26:C2:89:A1 UE BOOM 2
[NEW] Device 00:11:67:00:04:DF Bluetooth Optical Mouse
[NEW] Device 08:21:EF:6D:93:00 Samsung Galaxy S7
[NEW] Device A0:02:DC:E0:6E:50 McFire
[bluetooth]# connect 88:C6:26:C2:89:A1
Attempting to connect to 88:C6:26:C2:89:A1
[bluetooth]#  quit
[DEL] Controller E8:2A:EA:57:8F:B8 mac-Lenovo-Y50-70-Touch [default]
You need to specify a profile by its name.

```

So, I think I'm close to a solution, but I'm missing something. What does it mean by "you need to specify a profile by its name"? 

Thanks in advance for your help.

---

### Post by howefield on 2017-05-19
Thread moved to the "*MINT*" forum.

---

### Post by jeremy31 on 2017-05-19
With the headset paired/connected, post results for ```
pacmd list-cards
```

---

### Post by jamesleesmith on 2017-05-19
> **jeremy31 said:**
> With the headset paired/connected, post results for ```
pacmd list-cards
```

Thanks for the reply. Here it is:

```
mac@mac-Lenovo-Y50-70-Touch ~ $ pacmd list-cards
2 card(s) available.
    index: 0
    name: <alsa_card.pci-0000_00_03.0>
    driver: <module-alsa-card.c>
    owner module: 6
    properties:
        alsa.card = "0"
        alsa.card_name = "HDA Intel HDMI"
        alsa.long_card_name = "HDA Intel HDMI at 0xd1710000 irq 35"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:03.0"
        sysfs.path = "/devices/pci0000:00/0000:00:03.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "0c0c"
        device.product.name = "Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller"
        device.form_factor = "internal"
        device.string = "0"
        device.description = "Built-in Audio"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    profiles:
        output:hdmi-stereo: Digital Stereo (HDMI) Output (priority 5400, available: unknown)
        output:hdmi-surround: Digital Surround 5.1 (HDMI) Output (priority 300, available: unknown)
        output:hdmi-surround71: Digital Surround 7.1 (HDMI) Output (priority 300, available: unknown)
        output:hdmi-stereo-extra1: Digital Stereo (HDMI 2) Output (priority 5200, available: unknown)
        output:hdmi-surround-extra1: Digital Surround 5.1 (HDMI 2) Output (priority 100, available: unknown)
        output:hdmi-surround71-extra1: Digital Surround 7.1 (HDMI 2) Output (priority 100, available: unknown)
        output:hdmi-stereo-extra2: Digital Stereo (HDMI 3) Output (priority 5200, available: unknown)
        output:hdmi-surround-extra2: Digital Surround 5.1 (HDMI 3) Output (priority 100, available: unknown)
        output:hdmi-surround71-extra2: Digital Surround 7.1 (HDMI 3) Output (priority 100, available: unknown)
        off: Off (priority 0, available: unknown)
    active profile: <output:hdmi-stereo>
    sinks:
        alsa_output.pci-0000_00_03.0.hdmi-stereo/#0: Built-in Audio Digital Stereo (HDMI)
    sources:
        alsa_output.pci-0000_00_03.0.hdmi-stereo.monitor/#0: Monitor of Built-in Audio Digital Stereo (HDMI)
    ports:
        hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-1: HDMI / DisplayPort 2 (priority 5800, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-2: HDMI / DisplayPort 3 (priority 5700, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
    index: 1
    name: <alsa_card.pci-0000_00_1b.0>
    driver: <module-alsa-card.c>
    owner module: 7
    properties:
        alsa.card = "1"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xd1714000 irq 34"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card1"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "8c20"
        device.product.name = "8 Series/C220 Series Chipset High Definition Audio Controller"
        device.form_factor = "internal"
        device.string = "1"
        device.description = "Built-in Audio"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    profiles:
        input:analog-stereo: Analog Stereo Input (priority 60, available: unknown)
        output:analog-stereo: Analog Stereo Output (priority 6000, available: unknown)
        output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (priority 6060, available: unknown)
        output:iec958-stereo: Digital Stereo (IEC958) Output (priority 5500, available: unknown)
        output:iec958-stereo+input:analog-stereo: Digital Stereo (IEC958) Output + Analog Stereo Input (priority 5560, available: unknown)
        off: Off (priority 0, available: unknown)
    active profile: <output:analog-stereo+input:analog-stereo>
    sinks:
        alsa_output.pci-0000_00_1b.0.analog-stereo/#1: Built-in Audio Analog Stereo
    sources:
        alsa_output.pci-0000_00_1b.0.analog-stereo.monitor/#1: Monitor of Built-in Audio Analog Stereo
        alsa_input.pci-0000_00_1b.0.analog-stereo/#2: Built-in Audio Analog Stereo
    ports:
        analog-input-internal-mic: Internal Microphone (priority 8900, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-input-mic: Microphone (priority 8700, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-output-speaker: Speakers (priority 10000, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-speakers"
        analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-headphones"
        iec958-stereo-output: Digital Output (S/PDIF) (priority 0, latency offset 0 usec, available: unknown)
            properties:


```

---

### Post by jeremy31 on 2017-05-20
The headset isn't found by Pulseaudio, post results for ```
pactl list short | grep blue
```

---

### Post by jamesleesmith on 2017-05-20
> **jeremy31 said:**
> The headset isn't found by Pulseaudio, post results for ```
pactl list short | grep blue
```

Again, thank you:
```
mac@mac-Lenovo-Y50-70-Touch ~ $ pactl list short | grep blue
8    module-bluetooth-policy        
9    module-bluetooth-discover        
10    module-bluez5-discover
```

---

### Post by jeremy31 on 2017-05-20
Have you tried the a2dp.py script that is mentioned in [https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1577197](https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1577197) in comment #25

---

### Post by jamesleesmith on 2017-05-20
> **jeremy31 said:**
> Have you tried the a2dp.py script that is mentioned in [https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1577197](https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1577197) in comment #25

No I haven't, mostly because I don't understand what action he's recommending.

---

### Post by jeremy31 on 2017-05-20
See [https://askubuntu.com/a/889765/300665](https://askubuntu.com/a/889765/300665) and see if it still works.  I still use the script with Ubuntu 16.04 and Linux Mint 18

---

### Post by jamesleesmith on 2017-05-20
> **jeremy31 said:**
> See [https://askubuntu.com/a/889765/300665](https://askubuntu.com/a/889765/300665) and see if it still works.  I still use the script with Ubuntu 16.04 and Linux Mint 18

Ok, I obviously am too ignorant of the finer points of Linux, because I don't even know how to follow the advise in the link you posted. Here's what happened:

```
mac@mac-Lenovo-Y50-70-Touch ~ $ wget https://gist.github.com/pylover/d68be364adac5f946887b85e6ed6e7ae/archive/d698974910bbb7d016ec0ad08c1bf41b4b524364.zip
--2017-05-20 16:54:13--  https://gist.github.com/pylover/d68be364adac5f946887b85e6ed6e7ae/archive/d698974910bbb7d016ec0ad08c1bf41b4b524364.zip
Resolving gist.github.com (gist.github.com)... 192.30.253.118, 192.30.253.119
Connecting to gist.github.com (gist.github.com)|192.30.253.118|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://codeload.github.com/gist/d68be364adac5f946887b85e6ed6e7ae/zip/d698974910bbb7d016ec0ad08c1bf41b4b524364 [following]
--2017-05-20 16:54:17--  https://codeload.github.com/gist/d68be364adac5f946887b85e6ed6e7ae/zip/d698974910bbb7d016ec0ad08c1bf41b4b524364
Resolving codeload.github.com (codeload.github.com)... 192.30.253.120, 192.30.253.121
Connecting to codeload.github.com (codeload.github.com)|192.30.253.120|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3960 (3.9K) [application/zip]
Saving to: ‘d698974910bbb7d016ec0ad08c1bf41b4b524364.zip.1’

d698974910bbb7d016e 100%[===================>]   3.87K  --.-KB/s    in 0.1s    

2017-05-20 16:54:20 (35.4 KB/s) - ‘d698974910bbb7d016ec0ad08c1bf41b4b524364.zip.1’ saved [3960/3960]
```

And then...

```
mac@mac-Lenovo-Y50-70-Touch ~ $ mv ~/d68be364adac5f946887b85e6ed6e7ae-d698974910bbb7d016ec0ad08c1bf41b4b524364/a2dp.py .a2dp.py
mv: cannot stat '/home/mac/d68be364adac5f946887b85e6ed6e7ae-d698974910bbb7d016ec0ad08c1bf41b4b524364/a2dp.py': No such file or directory
mac@mac-Lenovo-Y50-70-Touch ~ $
```

Finally...

```
mac@mac-Lenovo-Y50-70-Touch ~ $ ./a2dp.py
bash: ./a2dp.py: No such file or directory
mac@mac-Lenovo-Y50-70-Touch ~ $ 
```

If you can walk me through it as if I was a fairly bright 10 year old, that might help.

Thank you

---

### Post by jeremy31 on 2017-05-22
Try
```
unzip d698974910bbb7d016ec0ad08c1bf41b4b524364.zip
```
```
cp d68be364adac5f946887b85e6ed6e7ae-d698974910bbb7d016ec0ad08c1bf41b4b524364/a2dp.py a2dp.py
```
```
chmod +x a2dp.py
```
```
./a2dp.py
```

---

### Post by jamesleesmith on 2017-05-22
> **jeremy31 said:**
> Try
```
unzip d698974910bbb7d016ec0ad08c1bf41b4b524364.zip
```
```
cp d68be364adac5f946887b85e6ed6e7ae-d698974910bbb7d016ec0ad08c1bf41b4b524364/a2dp.py a2dp.py
```
```
chmod +x a2dp.py
```
```
./a2dp.py
```

Ok, I did all that. Here's the result of the last command:

```
mac@mac-Lenovo-Y50-70-Touch ~ $ ./a2dp.py
Connection MADE
Selecting device:
1. 88:C6:26:C2:89:A1 UE BOOM 2
2. 08:21:EF:6D:93:00 Samsung Galaxy S7
3. A0:02:DC:E0:6E:50 McFire
4. 00:11:67:00:04:DF Bluetooth Optical Mouse
Select device[1]:
1
Device MAC: 88:C6:26:C2:89:A1
Cannot find `bluez_card.88_C6_26_C2_89_A1` using `pactl list cards short`. Retrying 8 more times
Cannot find `bluez_card.88_C6_26_C2_89_A1` using `pactl list cards short`. Retrying 7 more times
Cannot find `bluez_card.88_C6_26_C2_89_A1` using `pactl list cards short`. Retrying 6 more times
Cannot find `bluez_card.88_C6_26_C2_89_A1` using `pactl list cards short`. Retrying 5 more times
Cannot find `bluez_card.88_C6_26_C2_89_A1` using `pactl list cards short`. Retrying 4 more times
Cannot find `bluez_card.88_C6_26_C2_89_A1` using `pactl list cards short`. Retrying 3 more times
Cannot find `bluez_card.88_C6_26_C2_89_A1` using `pactl list cards short`. Retrying 2 more times
Cannot find `bluez_card.88_C6_26_C2_89_A1` using `pactl list cards short`. Retrying 1 more times
It seems device: 88:C6:26:C2:89:A1 is not connected yet, trying to connect.
Expression "Failed to connect: org.bluez.Error.Failed" failed with fail pattern: "fail"
Exiting bluetoothctl
```

---

### Post by jeremy31 on 2017-05-22
I would use bluetoothctl to see what is going on
In terminal
```
bluetoothctl
remove 88:C6:26:C2:89:A1
```
Put the headphones in pairing mode and then back in terminal
```
pair 88:C6:26:C2:89:A1
trust 88:C6:26:C2:89:A1
connect 88:C6:26:C2:89:A1
exit
./a2dp.py
```

See if any errors appear or if it works now

---

### Post by jamesleesmith on 2017-05-22
> **jeremy31 said:**
> I would use bluetoothctl to see what is going on
In terminal
```
bluetoothctl
remove 88:C6:26:C2:89:A1
```
Put the headphones in pairing mode and then back in terminal
```
pair 88:C6:26:C2:89:A1
trust 88:C6:26:C2:89:A1
connect 88:C6:26:C2:89:A1
exit
./a2dp.py
```

See if any errors appear or if it works now

```
mac@mac-Lenovo-Y50-70-Touch ~ $ bluetoothctl
[NEW] Controller E8:2A:EA:57:8F:B8 mac-Lenovo-Y50-70-Touch [default]
[NEW] Device 88:C6:26:C2:89:A1 UE BOOM 2
[NEW] Device 00:11:67:00:04:DF Bluetooth Optical Mouse
[NEW] Device 08:21:EF:6D:93:00 Samsung Galaxy S7
[NEW] Device A0:02:DC:E0:6E:50 McFire
[bluetooth]# remove 88:C6:26:C2:89:A1
[DEL] Device 88:C6:26:C2:89:A1 UE BOOM 2
Device has been removed
[bluetooth]# pair 88:C6:26:C2:89:A1
Device 88:C6:26:C2:89:A1 not available
[bluetooth]# trust 88:C6:26:C2:89:A1
Device 88:C6:26:C2:89:A1 not available
[bluetooth]# connect 88:C6:26:C2:89:A1
Device 88:C6:26:C2:89:A1 not available
[bluetooth]# exit
[DEL] Controller E8:2A:EA:57:8F:B8 mac-Lenovo-Y50-70-Touch [default]
mac@mac-Lenovo-Y50-70-Touch ~ $ bluetoothctl
[NEW] Controller E8:2A:EA:57:8F:B8 mac-Lenovo-Y50-70-Touch [default]
[NEW] Device 00:11:67:00:04:DF Bluetooth Optical Mouse
[NEW] Device 08:21:EF:6D:93:00 Samsung Galaxy S7
[NEW] Device A0:02:DC:E0:6E:50 McFire
[bluetooth]# pair 88:C6:26:C2:89:A1
Device 88:C6:26:C2:89:A1 not available
```

No luck.

---

### Post by jeremy31 on 2017-05-23
Lets try
```
bluetoothctl
remove 88:C6:26:C2:89:A1
```
Put the headphones in pairing mode and then back in terminal
```
scan on
```
Wait for it to find the headset
```
pair 88:C6:26:C2:89:A1
trust 88:C6:26:C2:89:A1
connect 88:C6:26:C2:89:A1
exit
./a2dp.py
```

See if any errors appear or if it works now

---

### Post by kendrick.ong on 2018-04-26
I'm having the same problem I tried every code above nothing works, maybe I missed something or my peripherals is not known for [https://www.jbl.com](https://www.jbl.com) and [https://www.dossspeakerbluetooth.com](https://www.dossspeakerbluetooth.com) ? I'll try to double checked it again and comeback here If I got some good results.

---

### Post by spacey2 on 2018-05-12
The instructions from Jeremy31 did the trick for my JBL Charge 2+! Thank you!

---

