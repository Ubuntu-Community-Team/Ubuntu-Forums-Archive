---
title: "Ubuntu 18.04 HDMI not working"
date: 2018-07-19
forum: Installation &amp; Upgrades
---

### Post by sduverge on 2018-07-19
In the past this was the least of my worries, but here we are. I just moved from one LTS to another and made a sort of fresh install (only / partition).
Now I have this black screen with a blinking pointer whenever I plug in my HDMI cable.
I have revised previous posts and seems this problem is a year old, yet all the solutions out there doesn't seem to work. 
I'll display all the basics you might ask, and help me find a solution.

[HTML]~$ lspci -vk | grep -iA20 vga
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Mobile 4 Series Chipset Integrated Graphics Controller
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d3c00000 (64-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at d120 [size=8]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Lenovo Mobile 4 Series Chipset Integrated Graphics Controller
    Flags: bus master, fast devsel, latency 0
    Memory at d4100000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Lenovo 82801I (ICH9 Family) USB UHCI Controller
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at d0c0 [size=32][/HTML]

[HTML]~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

[/HTML]

HDMI is not connected.
[HTML]~$ sudo apt install read-edid && sudo get-edid | parse-edid
[sudo] password for arashiko: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
read-edid is already the newest version (3.0.2-1build1).
0 upgraded, 0 newly installed, 0 to remove and 278 not upgraded.
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 0
No EDID on bus 1
No EDID on bus 3
No EDID on bus 4
No EDID on bus 5
No EDID on bus 6
No EDID on bus 7
1 potential busses found: 2
128-byte EDID successfully retrieved from i2c bus 2
Looks like i2c was successful. Have a good day.
Checksum Correct

Section "Monitor"
    Identifier "&#65533;&#65533;"
    ModelName "&#65533;&#65533;"
    VendorName "AUO"
    # Monitor Manufactured week 1 of 2008
    # EDID version 1.3
    # Digital Display
    DisplaySize 330 210
    Gamma 2.20
    Option "DPMS" "false"
    Modeline     "Mode 0" 71.11 1280 1328 1360 1438 800 803 809 824 -hsync -vsync 
EndSection

[/HTML]

HDMI is connected. Black screen, blinking pointer. I just waited for it to go blank, then press enter.
[HTML]~$ sudo apt install read-edid && sudo get-edid | parse-edid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
read-edid is already the newest version (3.0.2-1build1).
0 upgraded, 0 newly installed, 0 to remove and 278 not upgraded.
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 0
No EDID on bus 1
No EDID on bus 3
No EDID on bus 5
No EDID on bus 6
No EDID on bus 7
2 potential busses found: 2 4
Will scan through until the first EDID is found.
Pass a bus number as an option to this program to go only for that one.
128-byte EDID successfully retrieved from i2c bus 2
Looks like i2c was successful. Have a good day.
Checksum Correct

Section "Monitor"
    Identifier "&#65533;&#65533;"
    ModelName "&#65533;&#65533;"
    VendorName "AUO"
    # Monitor Manufactured week 1 of 2008
    # EDID version 1.3
    # Digital Display
    DisplaySize 330 210
    Gamma 2.20
    Option "DPMS" "false"
    Modeline     "Mode 0" 71.11 1280 1328 1360 1438 800 803 809 824 -hsync -vsync 
EndSection[/HTML]

Please help!

---

