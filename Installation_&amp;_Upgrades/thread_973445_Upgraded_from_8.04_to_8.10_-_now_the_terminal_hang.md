---
title: "Upgraded from 8.04 to 8.10 - now the terminal hangs and I cant use ctrl-alt-f1"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by clemme on 2008-11-06
Hi,

I just upgraded my Ubuntu install from 8.04 to 8.10. The upgrade went fine, but now I'm having some problems:

1) If I start a terminal and just write "exit" and press enter the terminal hangs, I can't kill it (not even kill -9 <PID> works) and I can't start a new one. If I look in the System Monitor I see the following: [http://jir.dk/Screenshot-3.png](http://jir.dk/Screenshot-3.png) (is the unix_stream_data_wait normal?)

2) If I press ctrl-alt-f1 in X, it does not go to a text terminal like it used to. I tried ctrl-alt-(f1 to f6), nothing works. The only way I can get out of X is by using ctrl-alt-backspace, which just gives me a blinking cursor.

3) When I login to X via GDM, there is a "pause" of about 4-5 seconds where the PC just seems to stall before it continues. Any idea what that might be? Is there any way to debug this? Maybe to see a list of the processes launched when logging into the computer?

Furthermore, when I use the "uptime" command I can see that the load is very high, but it's not CPU usage, usually it's around 3-5 constantly). What gives?

---

### Post by clemme on 2008-11-06
I just did so gdm does not start up upon boot, then I can use the text terminal, but as soon as I start gdm (and thereby X), I run into the same problems again. Could it be keyboard setup problems driver problems (I have an Nvidia8800GT card)?

---

### Post by clemme on 2008-12-02
After a long time of trying different things I stumbled upon the fact that running "lsusb" in a terminal (in X) would hang. I figured it might be something with the USB controller and/or driver, so I rebooted my PC and set the USB controller to USB 1.1 only and now my PC works fine.

The weird part is that this error only shows when X is running and the USB is set to 2.0 in the bios.

I'll try to look into which USB kernel module is used and if I can choose another one.

My hardware setup is as follows:
Shuttle SP35P2 Pro
Intel E8200 CPU
2GB DDR2 1066MHz RAM
Samsung 250GB SATA harddrive
Noname PATA CD/DVD recorder
Enermax USB keyboard & logitech USB mouse

---

### Post by clemme on 2008-12-02
Oddly enough, I'm still experiencing USB2.0 speeds, even if the bios is set to USB1.1.

And the output of lsusb still shows some USB2.0 stuff:

> 
Bus 008 Device 003: ID 1058:0910 Western Digital Technologies, Inc. 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 005: ID 0781:a7a8 SanDisk Corp. 
Bus 004 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 005: ID 0dc6:5300 Precision Squared Technology Corp. 
Bus 005 Device 004: ID 046d:c024 Logitech, Inc. MX300 Optical Mouse
Bus 005 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 005 Device 002: ID 0dc6:5000 Precision Squared Technology Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1307:1171 Transcend Information, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



---

### Post by bytecode on 2008-12-09
Hi clemme,
I'm relieved to find your post as it gives me something to try.

I would like to confirm that I am experiencing a similar issue with a particular desktop pc runing Ubuntu 8.10 Intrepid Ibex.

Symptoms:
*   Bash terminal becomes un responsive
*   System monitor shows:
    *   majority of processes listed with "do_poll", 
    *   2x gnome-pty-helper with "unix_streat_data_wait"
    *   wget "_mutex_lock" - I was trying to use wget to test for resolution and http file downloading as firefox stops connecting to new pages when these symptoms kick in...
    *   gvfs-fuse-daemon with "futex_wait"
    *   multiload-applet-2 with "_mutex_lock"
*   Sytem monitor system load continues to update showing 1,5,10 10.50, 9.95, 6.95 after many minutes.

*   I have the system monitor panel applet with the mini graphs - this seems to freeze when the problem starts.
*   Attempts to use sudo on the command line in a terminal are fruitless - I can type a command, but on pressing enter I have no response within the terminal other than a blinking cursor and any text that I type.

CTRL+C fails to make any impact.  It does not terminate the process.  The ^C character is drawn.

I'm running a dual-head system with nVidia, dual core AMD with an RT61 pci wireless card.
I haven't noticed any pertinent entries so far within the logs: daemon.log, auth.log, kern.log, messages or syslog.

I'll try the usb work around suggested above.

---

### Post by bytecode on 2008-12-09
Well, I changed my bios setting, disabled my USB2 support, but the symptoms represented themselves within 60 seconds of logging into the desktop.

I tried logging out and current have two blank monitors, except for that favourite little cursor pulsing rapidly in the top left corner.

I guess it's time to start unplugging all of the hardware until some clue presents itself.  Only it's 00:12 and I need to go to bed.

This box has run very happily for 6 months or so with Ubuntu 8.04 Hard Heron - I doubt that it's a hardware problem as such.  Plus the general gui remains active - it's more like there's some underlying service or process blocking everything else.

I can't even ping let alone ssh into the box from my laptop once the symptoms present themselves.

Only a hard reset reboots the box :(

If anyone has any suggestions I'd welcome them.  I'd file a bug report but I have insufficient information.

---

### Post by bytecode on 2008-12-10
After taking a look at my laptop also running Intrepid - it seems that the waiting channel status of my processes is nothing unusual..

So I'm guessing that the status of my processes, the load etc... is not directly related to the problem.

I do seem to be running ok so far today though on the desktop box that presented the problem - it's been up for 2 hours without any problems so far.

The only change that I have made, is that I have re-seated - more accurately, reconnected my DVI connector for mysecond screen - as I found that it was loose and although it was in contact enough for the display to work, was not connected very well.

I am unsure whether this is related.   But it is the only action that I have taken and time will tell.

I guess a poor connection could effect the machine as a whole, I'm familiar with short circuits affecting peripherals - I just would not expect it to affect performance, load averages and such. 

I wondered about trying to partially pull out the DVI connector, but I've got work to do...

---

### Post by clemme on 2008-12-10
Hi Bytecode,

The symptons I'm having are exactly the same as yours when I look in the system monitor.

I've been running with the USB setting on USB1.1 for some days now, I still see the problem once in a while, but all the time, as was the case when the BIOS setting was on USB2.

My box also ran for a long time with Ubuntu 8.04 with no problems whatsoever, so I'm ruling out hardware issues as well. The fact that both Windows XP and Vista 64-bit runs fine on the same box makes me certain that it is not a hardware issue.

I have a single-screen setup with an Nvidia (Asus branded) 8800GT graphics card, I'll make sure to check the DVI connector when I get home and post back here if it helps.

Kinda "glad" to see I'm not the only one with this rather weird issue :)

---

### Post by clemme on 2008-12-15
No loose DVI connector here, I'm still seeing the issue once in a while. I'm pretty sure it's USB related, once in a while when shutting down I see some error messages related to USB, something about "USB timing out" or something along those lines.

---

### Post by clemme on 2009-01-04
Just because I had some extra time to waste over the Christmas holidays, I installed Kubuntu 8.10 on an empty hard-drive I had lying around.

After the installation process finished, I saw the same problems as on Ubuntu 8.10, so it is not Gnome specific.

And as I (think) I've written before, there are no problems at all when not running X (not starting gdm at startup). But it is a bit boring only having a commandline to play with :P

---

