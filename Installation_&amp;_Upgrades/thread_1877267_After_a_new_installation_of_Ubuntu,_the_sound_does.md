---
title: "After a new installation of Ubuntu, the sound does not work"
date: 2011-11-07
forum: Installation &amp; Upgrades
---

### Post by *Chris* on 2011-11-07
Hi All,

Laptop - HP 2000-129CA Notebook PC
OS - Ubuntu 10.4.3

After installing Ubuntu I am unable to get the sound card to work.

From searching for previous sound related issues, the different commands people have asked others to complete are below including there outputs.  Any Ideas?

lspci -v
lsmod
pactl list
alsamixer

Thanks

------------------------------
pactl list

chris@commandcentral:~$ pactl list
Module #0
    Name: module-device-restore
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore the volume/mute state of devices"
        module.version = "0.9.21-63-gd3efa-dirty"

Module #1
    Name: module-stream-restore
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore the volume/mute/device state of streams"
        module.version = "0.9.21-63-gd3efa-dirty"

Module #2
    Name: module-card-restore
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore profile of cards"
        module.version = "0.9.21-63-gd3efa-dirty"

Module #3
    Name: module-augment-properties
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Augment the property sets of streams with additional static information"
        module.version = "0.9.21-63-gd3efa-dirty"

Module #4
    Name: module-alsa-card
    Argument: device_id="0" name="pci-0000_00_14.2" card_name="alsa_card.pci-0000_00_14.2" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"
    Usage counter: 0
    Properties:
        module.author = "Lennart Poettering"
        module.description = "ALSA Card"
        module.version = "0.9.21-63-gd3efa-dirty"

Module #5
    Name: module-udev-detect
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Detect available audio hardware and load matching drivers"
        module.version = "0.9.21-63-gd3efa-dirty"

Module #6
    Name: module-bluetooth-discover
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Joao Paulo Rechi Vita"
        module.description = "Detect available bluetooth audio devices and load bluetooth audio drivers"
        module.version = "0.9.21-63-gd3efa-dirty"

Module #7
    Name: module-esound-protocol-unix
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "ESOUND protocol (UNIX sockets)"
        module.version = "0.9.21-63-gd3efa-dirty"

Module #8
    Name: module-native-protocol-unix
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Native protocol (UNIX sockets)"
        module.version = "0.9.21-63-gd3efa-dirty"

Module #9
    Name: module-gconf
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "GConf Adapter"
        module.version = "0.9.21-63-gd3efa-dirty"

Module #10
    Name: module-default-device-restore
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore the default sink and source"
        module.version = "0.9.21-63-gd3efa-dirty"

Module #11
    Name: module-rescue-streams
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "When a sink/source is removed, try to move their streams to the default sink/source"
        module.version = "0.9.21-63-gd3efa-dirty"

Module #12
    Name: module-always-sink
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Colin Guthrie"
        module.description = "Always keeps at least one sink loaded even if it's a null one"
        module.version = "0.9.21-63-gd3efa-dirty"

Module #13
    Name: module-intended-roles
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically set device of streams based of intended roles of devices"
        module.version = "0.9.21-63-gd3efa-dirty"

Module #14
    Name: module-suspend-on-idle
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "When a sink/source is idle for too long, suspend it"
        module.version = "0.9.21-63-gd3efa-dirty"

Module #15
    Name: module-console-kit
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Create a client for each ConsoleKit session of this user"
        module.version = "0.9.21-63-gd3efa-dirty"

Module #16
    Name: module-position-event-sounds
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Position event sounds between L and R depending on the position on screen of the widget triggering them."
        module.version = "0.9.21-63-gd3efa-dirty"

Module #17
    Name: module-x11-publish
    Argument: display=:0.0
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "X11 credential publisher"
        module.version = "0.9.21-63-gd3efa-dirty"

Module #18
    Name: module-x11-bell
    Argument: display=:0.0 sample=bell.ogg
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "X11 bell interceptor"
        module.version = "0.9.21-63-gd3efa-dirty"

Module #19
    Name: module-x11-cork-request
    Argument: display=:0.0
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Synthesize X11 media key events when cork/uncork is requested"
        module.version = "0.9.21-63-gd3efa-dirty"

Module #20
    Name: module-x11-xsmp
    Argument: display=:0.0 session_manager=local/commandcentral:@/tmp/.ICE-unix/1292,unix/commandcentral:/tmp/.ICE-unix/1292
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "X11 session management"
        module.version = "0.9.21-63-gd3efa-dirty"

Sink #0
    State: SUSPENDED
    Name: alsa_output.pci-0000_00_14.2.analog-stereo
    Description: Internal Audio Analog Stereo
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 4
    Mute: no
    Volume: 0: 150% 1: 150%
            0: 10.57 dB 1: 10.57 dB
            balance 0.00
    Base Volume: 100%
                 0.00 dB
    Monitor Source: alsa_output.pci-0000_00_14.2.analog-stereo.monitor
    Latency: 0 usec, configured 0 usec
    Flags: HARDWARE HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
    Properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "HDA Generic"
        alsa.id = "HDA Generic"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "0"
        alsa.card_name = "HDA ATI SB"
        alsa.long_card_name = "HDA ATI SB at 0xd0440000 irq 16"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:14.2"
        sysfs.path = "/devices/pci0000:00/0000:00:14.2/sound/card0"
        device.bus = "pci"
        device.vendor.id = "1002"
        device.vendor.name = "ATI Technologies Inc"
        device.product.id = "4383"
        device.product.name = "SBx00 Azalia (Intel HDA)"
        device.form_factor = "internal"
        device.string = "front:0"
        device.buffering.buffer_size = "352768"
        device.buffering.fragment_size = "176384"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analog Stereo"
        device.description = "Internal Audio Analog Stereo"
        alsa.mixer_name = "Realtek ID 270"
        alsa.components = "HDA:10ec0270,103c3577,00100100"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"

Source #0
    State: SUSPENDED
    Name: alsa_output.pci-0000_00_14.2.analog-stereo.monitor
    Description: Monitor of Internal Audio Analog Stereo
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 4
    Mute: no
    Volume: 0: 100% 1: 100%
            0: 0.00 dB 1: 0.00 dB
            balance 0.00
    Base Volume: 100%
                 0.00 dB
    Monitor of Sink: alsa_output.pci-0000_00_14.2.analog-stereo
    Latency: 0 usec, configured 0 usec
    Flags: DECIBEL_VOLUME LATENCY 
    Properties:
        device.description = "Monitor of Internal Audio Analog Stereo"
        device.class = "monitor"
        alsa.card = "0"
        alsa.card_name = "HDA ATI SB"
        alsa.long_card_name = "HDA ATI SB at 0xd0440000 irq 16"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:14.2"
        sysfs.path = "/devices/pci0000:00/0000:00:14.2/sound/card0"
        device.bus = "pci"
        device.vendor.id = "1002"
        device.vendor.name = "ATI Technologies Inc"
        device.product.id = "4383"
        device.product.name = "SBx00 Azalia (Intel HDA)"
        device.form_factor = "internal"
        device.string = "0"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"

Source #2
    State: SUSPENDED
    Name: alsa_input.pci-0000_00_14.2.analog-stereo
    Description: Internal Audio Analog Stereo
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 4
    Mute: no
    Volume: 0: 149% 1: 149%
            0: 10.35 dB 1: 10.35 dB
            balance 0.00
    Base Volume:  32%
                 -30.00 dB
    Monitor of Sink: n/a
    Latency: 0 usec, configured 0 usec
    Flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
    Properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "HDA Generic"
        alsa.id = "HDA Generic"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "0"
        alsa.card_name = "HDA ATI SB"
        alsa.long_card_name = "HDA ATI SB at 0xd0440000 irq 16"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:14.2"
        sysfs.path = "/devices/pci0000:00/0000:00:14.2/sound/card0"
        device.bus = "pci"
        device.vendor.id = "1002"
        device.vendor.name = "ATI Technologies Inc"
        device.product.id = "4383"
        device.product.name = "SBx00 Azalia (Intel HDA)"
        device.form_factor = "internal"
        device.string = "front:0"
        device.buffering.buffer_size = "352768"
        device.buffering.fragment_size = "176384"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analog Stereo"
        device.description = "Internal Audio Analog Stereo"
        alsa.mixer_name = "Realtek ID 270"
        alsa.components = "HDA:10ec0270,103c3577,00100100"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"

Client #0
    Driver: module-console-kit.c
    Owner Module: 15
    Properties:
        application.name = "ConsoleKit Session /org/freedesktop/ConsoleKit/Session2"
        console-kit.session = "/org/freedesktop/ConsoleKit/Session2"

Client #1
    Driver: protocol-native.c
    Owner Module: 8
    Properties:
        application.name = "GNOME Volume Control Media Keys"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "16"
        application.id = "org.gnome.VolumeControl"
        application.icon_name = "multimedia-volume-control"
        application.version = "2.30.1"
        application.process.id = "1342"
        application.process.user = "chris"
        application.process.host = "commandcentral"
        application.process.binary = "gnome-settings-daemon"
        window.x11.display = ":0.0"
        application.language = "en_CA.utf8"
        application.process.machine_id = "03339f8842af067d4a330a304eb5f058"
        application.process.session_id = "03339f8842af067d4a330a304eb5f058-1320615669.628701-214767363"

Client #7
    Driver: module-x11-xsmp.c
    Owner Module: 20
    Properties:
        application.name = "XSMP Session on gnome-session as 1047224d3efe884d60132061567945997700000012920029"
        xsmp.vendor = "gnome-session"
        xsmp.client.id = "1047224d3efe884d60132061567945997700000012920029"

Client #8
    Driver: protocol-esound.c
    Owner Module: 7
    Properties:
        application.name = "EsounD client (UNIX socket client)"
        esound-protocol.peer = "UNIX socket client"
        esound.byte_order = "native"

Client #9
    Driver: protocol-native.c
    Owner Module: 8
    Properties:
        application.name = "libcanberra"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "16"
        application.process.id = "1484"
        application.process.user = "chris"
        application.process.host = "commandcentral"
        application.process.binary = "thunderbird-bin"
        window.x11.display = ":0.0"
        application.language = "en_CA.utf8"
        application.process.machine_id = "03339f8842af067d4a330a304eb5f058"
        application.process.session_id = "03339f8842af067d4a330a304eb5f058-1320615669.628701-214767363"

Client #10
    Driver: protocol-native.c
    Owner Module: 8
    Properties:
        application.name = "libcanberra"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "16"
        window.x11.display = ":0.0"
        window.x11.screen = "0"
        application.process.id = "1354"
        application.process.user = "chris"
        application.process.host = "commandcentral"
        application.process.binary = "metacity"
        application.language = "en_CA.utf8"
        application.process.machine_id = "03339f8842af067d4a330a304eb5f058"
        application.process.session_id = "03339f8842af067d4a330a304eb5f058-1320615669.628701-214767363"

Client #16
    Driver: protocol-esound.c
    Owner Module: 7
    Properties:
        application.name = "EsounD client (UNIX socket client)"
        esound-protocol.peer = "UNIX socket client"
        esound.byte_order = "native"

Client #17
    Driver: protocol-native.c
    Owner Module: 8
    Properties:
        application.name = "libcanberra"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "16"
        application.process.id = "3919"
        application.process.user = "chris"
        application.process.host = "commandcentral"
        application.process.binary = "firefox-bin"
        window.x11.display = ":0.0"
        application.language = "en_CA.utf8"
        application.process.machine_id = "03339f8842af067d4a330a304eb5f058"
        application.process.session_id = "03339f8842af067d4a330a304eb5f058-1320615669.628701-214767363"

Client #26
    Driver: protocol-native.c
    Owner Module: 8
    Properties:
        application.name = "pactl"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "16"
        application.process.id = "14865"
        application.process.user = "chris"
        application.process.host = "commandcentral"
        application.process.binary = "pactl"
        application.language = "en_CA.utf8"
        window.x11.display = ":0.0"
        application.process.machine_id = "03339f8842af067d4a330a304eb5f058"
        application.process.session_id = "03339f8842af067d4a330a304eb5f058-1320615669.628701-214767363"

Card #0
    Name: alsa_card.pci-0000_00_14.2
    Driver: module-alsa-card.c
    Owner Module: 4
    Properties:
        alsa.card = "0"
        alsa.card_name = "HDA ATI SB"
        alsa.long_card_name = "HDA ATI SB at 0xd0440000 irq 16"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:14.2"
        sysfs.path = "/devices/pci0000:00/0000:00:14.2/sound/card0"
        device.bus = "pci"
        device.vendor.id = "1002"
        device.vendor.name = "ATI Technologies Inc"
        device.product.id = "4383"
        device.product.name = "SBx00 Azalia (Intel HDA)"
        device.form_factor = "internal"
        device.string = "0"
        device.description = "Internal Audio"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Profiles:
        output:analog-stereo: Analog Stereo Output (sinks: 1, sources: 0, priority. 6000)
        output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (sinks: 1, sources: 1, priority. 6060)
        input:analog-stereo: Analog Stereo Input (sinks: 0, sources: 1, priority. 60)
        off: Off (sinks: 0, sources: 0, priority. 0)
    Active Profile: output:analog-stereo+input:analog-stereo

------------------------------
lspci -v

chris@commandcentral:~$ lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] Device 1510
    Subsystem: Advanced Micro Devices [AMD] Device 1510
    Flags: bus master, 66MHz, medium devsel, latency 32

00:01.0 VGA compatible controller: ATI Technologies Inc Device 9802
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 5000 [size=256]
    Memory at d0400000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    I/O ports at 5118 [size=8]
    I/O ports at 5124 [size=4]
    I/O ports at 5110 [size=8]
    I/O ports at 5120 [size=4]
    I/O ports at 5100 [size=16]
    Memory at d0449000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at d0448000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at d0447000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: 66MHz, medium devsel
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at d0440000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40) (prog-if 01)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at d0446000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=05, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: d0300000-d03fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d00fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:15.1 PCI bridge: ATI Technologies Inc Device 43a1
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Prefetchable memory behind bridge: 00000000d0100000-00000000d01fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:15.3 PCI bridge: ATI Technologies Inc Device 43a3
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d0200000-d02fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at d0445000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at d0444000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] Device 1700 (rev 43)
    Flags: fast devsel

00:18.1 Host bridge: Advanced Micro Devices [AMD] Device 1701
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Device 1702
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Device 1703
    Flags: fast devsel
    Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] Device 1704
    Flags: fast devsel

00:18.5 Host bridge: Advanced Micro Devices [AMD] Device 1718
    Flags: fast devsel

00:18.6 Host bridge: Advanced Micro Devices [AMD] Device 1716
    Flags: fast devsel

00:18.7 Host bridge: Advanced Micro Devices [AMD] Device 1719
    Flags: fast devsel

02:00.0 Class ff00: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, fast devsel, latency 0, IRQ 5
    Memory at d0300000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, fast devsel, latency 0, IRQ 27
    I/O ports at 3000 [size=256]
    Memory at d0104000 (64-bit, prefetchable) [size=4K]
    Memory at d0100000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

07:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
    Subsystem: Hewlett-Packard Company Device 1629
    Flags: bus master, fast devsel, latency 0, IRQ 23
    I/O ports at 2000 [size=256]
    Memory at d0200000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: rtl8192CE
    Kernel modules: r8192ce_pci

------------------------------
lsmod

chris@commandcentral:~$ lsmod
Module                  Size  Used by
michael_mic             1732  8 
arc4                    1153  4 
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203408  0 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               57406  0 
videodev               34425  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                  8740  0 
psmouse                63677  0 
serio_raw               3978  0 
video                  17375  0 
output                  1871  1 video
r8192ce_pci           455071  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_piix4               8335  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
r8169                  34140  0 
mii                     4381  1 r8169
ahci                   32360  2 

------------------------------

alsamixer

Card: HDA ATI SB                                     F1:  Help               &#9474;
&#9474; Chip: Realtek ID 270                                 F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All             F6:  Select sound card  &#9474;
&#9474; Item: Master [dB gain: 0.00, 0.00]                   Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;                                &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;                                 &#9474;
&#9474;                                &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                 &#9474;
&#9474;                                &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                 &#9474;
&#9474;                                &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                 &#9474;
&#9474;                                &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                 &#9474;
&#9474;                                &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                 &#9474;
&#9474;                                &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                 &#9474;
&#9474;                                &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                 &#9474;
&#9474;                                &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                 &#9474;
&#9474;                                &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                 &#9474;
&#9474;                                &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                 &#9474;
&#9474;                                &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                 &#9474;
&#9474;                                &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                 &#9474;
&#9474;                                &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;                                 &#9474;
&#9474;                              100<>100 100<>100                               &#9474;
&#9474;                             < Master >  PCM                                  &#9474;
&#9474;                                                                       
------------------------------

---

### Post by MAFoElffen on 2011-11-07
> ***Chris* said:**
> Hi All,

Laptop - HP 2000-129CA Notebook PC
OS - Ubuntu 10.4.3

After installing Ubuntu I am unable to get the sound card to work.

From searching for previous sound related issues, the different commands people have asked others to complete are below including there outputs.  Any Ideas?

lspci -v
lsmod
pactl list
alsamixer

Thanks
Looks like everything is loaded for what you have... As I remember about 10.04 and ALSA sound, the Alsa was installed with it "MUTED" as a default when installed. A lot of people didn't know this and thought they had sound issues, hwen all they had to do was unmute it.  Have you checked that in your sound settings/preferences?

---

### Post by Mikeb85 on 2011-11-07
Yes, the sound is muted as default.  You just need to move the slider to enable sound.

---

### Post by *Chris* on 2011-11-07
> **MAFoElffen said:**
> Looks like everything is loaded for what you have... As I remember about 10.04 and ALSA sound, the Alsa was installed with it "MUTED" as a default when installed. A lot of people didn't know this and thought they had sound issues, hwen all they had to do was unmute it.  Have you checked that in your sound settings/preferences?

I have checked this and yes by default it was muted however I unmuted  and ensured the volume was turned up.  Please see the attached pic.

---

### Post by *Chris* on 2011-11-12
Steps taken less a couple from [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

1)  Opened Terminal
2)  sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source
3)  sudo dpkg-reconfigure alsa-source
4)  Choose "Yes" and click enter
5)  Answer "Yes" for "ISA-PNP - recommended by package maintainers"
6)  Answer "Yes" for "for debugging - recommended by package maintainers"
7)  Choose your driver and ensure all other selections are unchecked (Space bar will select and deselect)
8)  If the progress bar reaches 100% with no errors, you will have installed the drivers successfully
9)  No errors and restarted the computer and the sound started working

---

