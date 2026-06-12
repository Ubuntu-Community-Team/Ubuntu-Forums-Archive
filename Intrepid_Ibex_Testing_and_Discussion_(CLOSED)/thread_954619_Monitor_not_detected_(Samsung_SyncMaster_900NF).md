---
title: "Monitor not detected (Samsung SyncMaster 900NF)"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by stbub on 2008-10-21
I've installed fglrx with intrepid, and my monitor isn't detected which means I can't set a high refresh rate - I'm limited to 60Hz.

Is there any way to force the monitor selection? ... or maybe edid can be fixed?

Here's the system information along with ddcprobe and get-edid output:

mino:/media/disk$ uname -a
Linux mino 2.6.27-7-generic #1 SMP Fri Oct 17 22:24:21 UTC 2008 i686 GNU/Linux
mino:/media/disk$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3600 Series
OpenGL version string: 2.1.8087 Release

mino:/media/disk$ sudo ddcprobe
vbe: VESA 3.0 detected.
oem: ATI ATOMBIOS
vendor: (C) 1988-2005, ATI Technologies Inc.
product: RV635 01.00
memory: 16384kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x256
mode: 1024x768x256
mode: 1280x1024x256
mode: 640x480x64k
mode: 800x600x64k
mode: 1024x768x64k
mode: 1280x1024x64k
mode: 320x200x64k
mode: 1600x1200x256
mode: 1600x1200x32k
mode: 1600x1200x64k
edid: 
edid: 1 3
id: 002f
eisa: SAM002f
serial: 41513139
manufacture: 12 2002
input: separate sync, composite sync, sync on green, digital signal.
screensize: 36 27
gamma: 1.940000
dpms: RGB, active off, no suspend, no standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 720x400@88 Hz (XGA2)
timing: 640x480@60 Hz (VGA)
timing: 640x480@67 Hz (Mac II, Apple)
timing: 640x480@72 Hz (VESA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@56 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@72 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 832x624@75 Hz (Mac II)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@60 Hz (VESA)
timing: 1024x768@70 Hz (VESA)
timing: 1024x768@75 Hz (VESA)
timing: 1280x1024@75 (VESA)
ctiming: 640x480@60
ctiming: 800x600@85
ctiming: 1024x768@85
ctiming: 1280x1024@85
ctiming: 1600x1200@75
ctiming: 1600x1200@85
ctiming: 1920x1440@60
ctiming: 2048x1536@65
dtiming: 1280x1024@99
monitorrange: 30-110, 50-160
monitorname: SyncMaster
monitorserial: H2QT300766
mino:/media/disk$ sudo get-edid | parse-edid
parse-edid: parse-edid version 1.4.1
get-edid: get-edid version 1.4.1

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
        Function supported
        Call successful

        VBE version 300
        VBE string at 0xc01d8 "ATI ATOMBIOS"

VBE/DDC service about to be called
        Report DDC capabilities

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
        Function supported
        Call successful

        Monitor and video card combination does not support DDC1 transfers
        Monitor and video card combination supports DDC2 transfers
        0 seconds per 128 byte EDID block transfer
        Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
        Read EDID

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
        Function supported
        Call successful

parse-edid: EDID checksum passed.

        # EDID version 1 revision 3
Section "Monitor"
        # Block type: 2:0 3:fd
        # Block type: 2:0 3:fc
        Identifier "SyncMaster"
        VendorName "SAM"
        ModelName "SyncMaster"
        # Block type: 2:0 3:fd
        HorizSync 30-110
        VertRefresh 50-160
        # Max dot clock (video bandwidth) 290 MHz
        # Block type: 2:0 3:fc
        # Block type: 2:0 3:ff
        # DPMS capabilities: Active off:yes  Suspend:no  Standby:no

        Mode    "1280x1024"     # vfreq 85.024Hz, hfreq 91.146kHz
                DotClock        157.500000
                HTimings        1280 1344 1504 1728
                VTimings        1024 1025 1028 1072
                Flags   "+HSync" "+VSync"
        EndMode
        # Block type: 2:0 3:fd
        # Block type: 2:0 3:fc
        # Block type: 2:0 3:ff
EndSection

---

### Post by marttali on 2008-10-22
Write into the xorg.conf file the resolution it should use.

---

### Post by stbub on 2008-10-22
> **marttali said:**
> Write into the xorg.conf file the resolution it should use.

That's what I ended up doing.

But that's not a very ubuntuish "for humans" kinda way to solve this :-)

Dunno who decided to remove the option to manually select the monitor (I think this is also missing in Hardy).

I would imagine there are still a lot of people with an aging but perfectly fine crt monitor.  Oh well...

---

