---
title: "No wired internet connection after first installation on new computer"
date: 2012-04-22
forum: Installation &amp; Upgrades
---

### Post by uubunti on 2012-04-22
**[FONT=DejaVu Sans, sans-serif][SIZE=3]1) I installed Ubuntu from a CD-[/SIZE][/FONT]****[FONT=DejaVu Sans, sans-serif][SIZE=3]ROM[/SIZE][/FONT]****[FONT=DejaVu Sans, sans-serif][SIZE=3] on a new computer. [/SIZE][/FONT]** 
         **         [FONT=DejaVu Sans, sans-serif][SIZE=3]The first run of this computer was with Ubuntu[/SIZE][/FONT]****[FONT=DejaVu Sans, sans-serif][SIZE=3].[/SIZE][/FONT]**
        **[FONT=DejaVu Sans, sans-serif][SIZE=3]There is no second operating system on the [/SIZE][/FONT]**       [B][FONT=DejaVu Sans, sans-serif][SIZE=3]
[/SIZE][/FONT][/B]       **[FONT=DejaVu Sans, sans-serif][SIZE=3]computer.[/SIZE][/FONT]**
        **[FONT=DejaVu Sans, sans-serif][SIZE=3]Now, a word processing program works.[/SIZE][/FONT]** 
        **[FONT=DejaVu Sans, sans-serif][SIZE=3]The i[/SIZE][/FONT]****[FONT=DejaVu Sans, sans-serif][SIZE=3]nternet connection of the computer [/SIZE][/FONT]****[FONT=DejaVu Sans, sans-serif][SIZE=3]is [/SIZE][/FONT]**[B][FONT=DejaVu Sans, sans-serif][SIZE=3]not 
[/SIZE][/FONT][/B]       **[FONT=DejaVu Sans, sans-serif][SIZE=3]working[/SIZE][/FONT]****[FONT=DejaVu Sans, sans-serif][SIZE=3].[/SIZE][/FONT]**
 **[FONT=DejaVu Sans, sans-serif][SIZE=3]2) Favorites _ System Settings _ Network [/SIZE][/FONT]**[B][FONT=DejaVu Sans, sans-serif][SIZE=3]and 
[/SIZE][/FONT][/B]       **[FONT=DejaVu Sans, sans-serif][SIZE=3]Connectivity _   [/SIZE][/FONT]**[B][FONT=DejaVu Sans, sans-serif][SIZE=3]Network Settings _ Network 
[/SIZE][/FONT][/B]       **[FONT=DejaVu Sans, sans-serif][SIZE=3]Connections[/SIZE][/FONT]**
        **[FONT=DejaVu Sans, sans-serif][SIZE=3]shows      Wired (not active, cannot be activated)[/SIZE][/FONT]**
                             **[FONT=DejaVu Sans, sans-serif][SIZE=3]Wire[/SIZE][/FONT]****[FONT=DejaVu Sans, sans-serif][SIZE=3]le[/SIZE][/FONT]****[FONT=DejaVu Sans, sans-serif][SIZE=3]ss (active) [/SIZE][/FONT]** 
                             [B][FONT=DejaVu Sans, sans-serif][SIZE=3]Mobile Broadband (not active, cannot be 
[/SIZE][/FONT][/B]                                                                                    **[FONT=DejaVu Sans, sans-serif][SIZE=3]activated)[/SIZE][/FONT]**
                             **[FONT=DejaVu Sans, sans-serif][SIZE=3]VPN (active) [/SIZE][/FONT]** 
                             **[FONT=DejaVu Sans, sans-serif][SIZE=3]DSL  (not active, cannot be activated)[/SIZE][/FONT]**
           **[FONT=DejaVu Sans, sans-serif][SIZE=3]all [/SIZE][/FONT]****[FONT=DejaVu Sans, sans-serif][SIZE=3]active [/SIZE][/FONT]****[FONT=DejaVu Sans, sans-serif][SIZE=3]windows are empty[/SIZE][/FONT]**
 [B][FONT=DejaVu Sans, sans-serif][SIZE=3]3) Terminal _ sudo dhclient eth0 
[/SIZE][/FONT][/B]              **[FONT=DejaVu Sans, sans-serif][SIZE=3]Shows following text:[/SIZE][/FONT]**
               **[FONT=DejaVu Sans, sans-serif][SIZE=3]SIOCSIFADDR: No such device[/SIZE][/FONT]**
               **[FONT=DejaVu Sans, sans-serif][SIZE=3]eth0: ERROR while getting interface flags: No such [/SIZE][/FONT]**              **[FONT=DejaVu Sans, sans-serif][SIZE=3]device[/SIZE][/FONT]**
               [B][FONT=DejaVu Sans, sans-serif][SIZE=3]eth0: ERROR while getting interface flags: No such 
[/SIZE][/FONT][/B]                                  **[FONT=DejaVu Sans, sans-serif][SIZE=3]device[/SIZE][/FONT]**
               **[FONT=DejaVu Sans, sans-serif][SIZE=3]Bind socket to interface: No such device[/SIZE][/FONT]**
 **[FONT=DejaVu Sans, sans-serif][SIZE=3]4) [/SIZE][/FONT]****[FONT=DejaVu Sans, sans-serif][SIZE=3]Konqueror:  192.168.1.1 [/SIZE][/FONT]** 
        **[FONT=DejaVu Sans, sans-serif][SIZE=3]shows: connection to server refused[/SIZE][/FONT]**
 [B][FONT=DejaVu Sans, sans-serif][SIZE=3]5) Ethernet controller Broadcom Corporation 
[/SIZE][/FONT][/B]       **[FONT=DejaVu Sans, sans-serif][SIZE=3]NetLink BCM57785 Gigabit[/SIZE][/FONT]****[FONT=DejaVu Sans, sans-serif][SIZE=3] Ethernet PCIe[/SIZE][/FONT]**       
**[FONT=DejaVu Sans, sans-serif][SIZE=3]6[/SIZE][/FONT]****[FONT=DejaVu Sans, sans-serif][SIZE=3]) [/SIZE][/FONT]****[FONT=DejaVu Sans, sans-serif][SIZE=3]I do not have wireless connection.[/SIZE][/FONT]**
 **[FONT=DejaVu Sans, sans-serif][SIZE=3]7[/SIZE][/FONT]****[FONT=DejaVu Sans, sans-serif][SIZE=3]) Another computer [/SIZE][/FONT]****[FONT=DejaVu Sans, sans-serif][SIZE=3]works with [/SIZE][/FONT]**[B][FONT=DejaVu Sans, sans-serif][SIZE=3]the 
[/SIZE][/FONT][/B]       **[FONT=DejaVu Sans, sans-serif][SIZE=3]same [/SIZE][/FONT]****[FONT=DejaVu Sans, sans-serif][SIZE=3]wired connection[/SIZE][/FONT]****[FONT=DejaVu Sans, sans-serif][SIZE=3].[/SIZE][/FONT]**
 **[FONT=DejaVu Sans, sans-serif][SIZE=3]8[/SIZE][/FONT]****[FONT=DejaVu Sans, sans-serif][SIZE=3]) How can I get access to the internet?[/SIZE][/FONT]**

---

### Post by SeijiSensei on 2012-04-22
Apparently it's not loading the appropriate Broadcom driver.  Try this:

```
sudo modprobe -v tg3
```

Support for the BCM57785 is in the tg3 module. I can see it if I grep for BCM57785 in the tg3.ko module.

If that works, edit the file /etc/modules by using "sudo nano /etc/modules" and add the line "tg3" to the bottom of the file.  If you reboot, does the computer then connect to the network?

---

### Post by uubunti on 2012-04-22
[SIZE=4]Problem is not fixed.

a) I tried this:
[/SIZE][SIZE=4]sudo modprobe -v tg3[/SIZE][SIZE=4]then I started the internet browser. No internet, no access to the router.
I do not understand the purpose to this command. So I am not sure if I made it right.

b) I do not know how I can make this:
    "[/SIZE]Support for the BCM57785 is in the tg3 module. I can see it if I grep for BCM57785 in the tg3.ko module."

[SIZE=4]c) Without doing b), I edited the file /etc/modules by using "sudo nano /etc/modules" and added the line "tg3" to the bottom of the file. I rebooted, the computer did then not connect to the network.[/SIZE]
[SIZE=4]
[/SIZE]

---

### Post by SeijiSensei on 2012-04-22
According to your first post, you have a NetLink BCM57785 Gigabit Ethernet PCIe ethernet adapter.  On my machine running Ubuntu 12.04b2, the tg3 kernel module provides support for the BCM57785 device.  The command "sudo modprobe -v tg3" should have forced your kernel to try and load that module even though it wasn't detected when Linux was installed.  Apparently that doesn't work.  It's possible that the version of Ubuntu you're running doesn't include support for your network adapter.

Here's a quick way to see if using a more recent version helps.  I suggest you boot from the [current beta version of 12.04]("http://releases.ubuntu.com/precise/") and choose "Try Ubuntu".  See if you can get your adapter to work with that version.

---

### Post by uubunti on 2012-04-24
p { margin-bottom: 0.21cm; }  **Summary:**

The Kubuntu version was 10.04.
Maybe it is too old for the new computer.
I tried newer linux distributions, especially Ubuntu 11.10
I tried to reboot with a USB and a DVD with the iso file on it.
I did not get to the point where I could check the internet connection.



**Details:**

USB starter stick with Ubuntu 11.10  made with Universal-USB-Installer-1.8.9.2.exe
 Menue
 1. Run on usb (after 8 sec automatic start)
 2.Install Ubuntu on HDD
 ...
 

 Automatikc start without selection of one menue point: After 15 minutes screen gets black
 Start mit 2. Installation on HDD endless repetition of USB mouse
 Start with 1 endless repetition of USB mouse
 Start with 2 without mouse:  
 .... [sdb] No Caching mode page present
 .... [sdb] Assuming drive chache: write through
 3 times repeated then showing  
  .... [sdb] Attached SCSI removable disk
  

 Start with USB Ubuntu 11.10 error message:
 udev[109]: '/sbin/modprobe -bv pci:v000010DEd00000DF7sv00001025sd00000512bc03sc00i00'
 [199] terminated by signal 9 (Killed)
 

 then repeating 3 lines about 20 times
 input: xxx USB yyy Mouse as /device/pci.../usb2/2-1/2-1-1/2-1-1
 generic-usb ... : input,hidraw0: USB HID v1.11 Mouse [...] on usb-0000...
 usb 2-1.1: USB disconnect, device number Z
 These 3 lines are repeated about 20 times counting Z from 1 to 21  
 

 At start from menue 2 Installation on HDD
 endless repetition Mouse problem with 3 lines

start DVD Ubuntu 11.10
k3b  _ data project _ writing _ create image DVD written
 or should it be
 k3b  _ data project _ image _ write image file to:
 ?
 

 k3b  _ data project _ writing _ create image DVD written
 Reboot computer with this DVD:
 Computer does not boot with this DVD, but boots with Kubuntu 10.04 which is already on HDD
 

 k3b detects iso file as iso file and suggests to burn it as iso file on DVD.
 Reboot with usb mouse and with this DVD: Screen shows "ubuntu with 5 red dots below the text" for 1 hour, no menue
 Reboot without usb mouse and with this DVD: Screen shows repeated ... /sbin/modprobe -v pci:v00...
 udevadm settele - timeout of 120 seconds readched, the event queue contains:
 /sys/devices/pci0000:00/0000:00:02.2 (1082)


What do you recommend?

---

### Post by uubunti on 2012-04-24
[SIZE=4]**Summary:**
[/SIZE]
[SIZE=4]The Kubuntu version was 10.04.[/SIZE]
[SIZE=4]Maybe it is too old for the new computer.[/SIZE]
[SIZE=4]I tried newer linux distributions, especially Ubuntu 11.10[/SIZE]
[SIZE=4]I tried to reboot with a USB and a DVD with the iso file on it.[/SIZE]
[SIZE=4]I did not get to the point where I could check the internet connection.
[/SIZE]
[SIZE=4]
[/SIZE]
[SIZE=4]**Details:**
[/SIZE]
[SIZE=4]USB starter stick with Ubuntu 11.10  made with Universal-USB-Installer-1.8.9.2.exe[/SIZE]
 [SIZE=4]Menue[/SIZE]
 [SIZE=4]1. Run on usb (nach 8 sec automatischer Start)[/SIZE]
 [SIZE=4]2.Install Ubuntu on HDD[/SIZE]
 [SIZE=4]...[/SIZE]
 [SIZE=4]
[/SIZE] 
 [SIZE=4]Automatic start without selection of one menue point: After 15 minutes screen gets black[/SIZE]
 [SIZE=4]Start mit 2. Installation on HDD endless repetition of USB mouse[/SIZE]
 [SIZE=4]Start with 1 endless repetition of USB mouse[/SIZE]
 [SIZE=4]Start with 2 without mouse:  [/SIZE]
 [SIZE=4].... [sdb] No Caching mode page present[/SIZE]
 [SIZE=4].... [sdb] Assuming drive chache: write through[/SIZE]
 [SIZE=4]3 times repeated then showing  [/SIZE]
 [SIZE=4] .... [sdb] Attached SCSI removable disk[/SIZE]
  [SIZE=4]
[/SIZE] 
 [SIZE=4]Start with USB Ubuntu 11.10 error message:[/SIZE]
 [SIZE=4]udev[109]: '/sbin/modprobe -bv pci:v000010DEd00000DF7sv00001025sd00000512bc03sc00i00'[/SIZE]
 [SIZE=4][199] terminated by signal 9 (Killed)[/SIZE]
 [SIZE=4]
[/SIZE] 
 [SIZE=4]then repeating 3 lines about 20 times[/SIZE]
 [SIZE=4]input: xxx USB yyy Mouse as /device/pci.../usb2/2-1/2-1-1/2-1-1[/SIZE]
 [SIZE=4]generic-usb ... : input,hidraw0: USB HID v1.11 Mouse [...] on usb-0000...[/SIZE]
 [SIZE=4]usb 2-1.1: USB disconnect, device number Z[/SIZE]
 [SIZE=4]These 3 lines are repeated about 20 times counting Z from 1 to 21  [/SIZE]
 [SIZE=4]
[/SIZE] 
 [SIZE=4]At start from menue 2 Installation on HDD[/SIZE]
 [SIZE=4]endless repetition Mouse problem with 3 lines[/SIZE]
[SIZE=4]
start DVD Ubuntu 11.10
[/SIZE] [SIZE=4]k3b  _ data project _ writing _ create image DVD written[/SIZE]
 [SIZE=4]or should it be[/SIZE]
 [SIZE=4]k3b  _ data project _ image _ write image file to:[/SIZE]
 [SIZE=4]?[/SIZE]
 [SIZE=4]
[/SIZE] 
 [SIZE=4]k3b  _ data project _ writing _ create image DVD written[/SIZE]
 [SIZE=4]Reboot computer with this DVD:[/SIZE]
 [SIZE=4]Computer does not boot with this DVD, but boots with Kubuntu 10.04 which is already on HDD[/SIZE]
 [SIZE=4]
[/SIZE] 
 [SIZE=4]k3b detects iso file as iso file and suggests to burn it as iso file on DVD.[/SIZE]
 [SIZE=4]Reboot with usb mouse and with this DVD: Screen shows "ubuntu with 5 red dots below the text" for 1 hour, no menue[/SIZE]
 [SIZE=4]Reboot without usb mouse and with this DVD: Screen shows repeated ... /sbin/modprobe -v pci:v00...[/SIZE]
 [SIZE=4]udevadm settele - timeout of 120 seconds readched, the event queue contains:[/SIZE]
 [SIZE=4]/sys/devices/pci0000:00/0000:00:02.2 (1082)[/SIZE]
[SIZE=4]
[/SIZE]
[SIZE=4]What do you recommend?
[/SIZE]

---

