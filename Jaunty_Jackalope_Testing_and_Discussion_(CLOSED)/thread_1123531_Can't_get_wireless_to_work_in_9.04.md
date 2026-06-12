---
title: "Can't get wireless to work in 9.04"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tati on 2009-04-12
Just did a clean install of Ubuntu 9.04 and I can't get the wireless to work. I have a Dell Studio Hybrid with a Broadcom 4328 wireless card. Multiverse is enabled; ndiswrapper is installed; tried the instructions [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver").

No wireless networks appear in the networks menu on the panel. How do I get wireless to work in Jaunty? Isn't this supposed to work out of the gate now for most drivers?

(Reposted from the Jaunty Jackalope testing forum.)

---

### Post by hyper_ch on 2009-04-12
do you even need ndiswrapper for that card on Jaunty?

---

### Post by tati on 2009-04-12
Didn't think I did either but no wireless networks appear on my network panel. Do I need to enable that separately now?

---

### Post by Ayuthia on 2009-04-13
Have you checked System->Administration->Hardware Drivers for the Broadcom STA (wl) driver?  As far as I know, that and ndiswrapper are your only choices.  The Broadcom STA driver seems to work with some 4328 cards. Here is the link to the driver from Broadcom:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

It does not say that your card is supported, but there have been people that have reported that it works and it does show up as one of the alias chipsets in the wl.ko file.

---

### Post by BillyPrefect on 2009-04-13
Try running a couple of system updates.  Mine kicked in after I think 2 updates... first it pointed to the updated wireless driver, then picked a specific broadcom driver.  I am at work right now so can not be more specific.  I have installed on my Dell 1720, which uses the Broadcom 4328 card.

---

### Post by tati on 2009-04-13
System update = [FONT="Courier New"]sudo apt-get update[/FONT]?

Tried that a number of times to no avail. Have I missed a step? All I've done is a clean install of 9.04 and the above command. Did I neglect to turn something on?

---

### Post by Ayuthia on 2009-04-13
> **tati said:**
> System update = [FONT="Courier New"]sudo apt-get update[/FONT]?

Tried that a number of times to no avail. Have I missed a step? All I've done is a clean install of 9.04 and the above command. Did I neglect to turn something on?

Can you post the results of lshw -C network?  My guess is that you might have a Broadcom wired ethernet card and that might be what is causing the problem.

---

### Post by tati on 2009-04-13
[B]Ignore this -- wrong paste.
[/B]
```
Hardware Lister (lshw) - B.02.13
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.13)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-c CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
	-numeric        output numeric IDs (for PCI, USB, etc.)
```

---

### Post by tati on 2009-04-13
```
 *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:1c:b1:e4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.104 latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 5a:6c:27:f9:1d:9e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

---

### Post by Ayuthia on 2009-04-13
> **tati said:**
> ```
 *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:1c:b1:e4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.104 latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 5a:6c:27:f9:1d:9e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```
It looks like it is trying to use the b43 module.  Can you try the following:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan
```
It will remove the b43, ssb, and wl modules and then load the wl module.  It will then try to start up the wireless card and search for wireless sites.

---

### Post by tati on 2009-04-13
Worked, thanks!

---

### Post by tati on 2009-04-14
**Update**: Spoke too soon. I lose these changes on restart. How do I make them permanent?

---

### Post by ScoobyDan on 2009-04-16
> **tati said:**
> **Update**: Spoke too soon. I lose these changes on restart. How do I make them permanent?

+1 on this

---

### Post by qinyian on 2009-04-17
I just put the command into /etc/rc.local, which will be executed every time when your computer start up. Now, my Broadcom works perfectly. I'm beginner of Ubuntu. It's the first time for me to offer a solution on this forum. I'm not sure whether it has any side effect or not.

---

### Post by M42 on 2009-04-18
Hello qinyian,

Your solution worked for me.  I just put the first two command in the rc.local file and it works fine.  Not a long term solution maybe but a good workaround until a better fix is implemented.

Thanks.

---

### Post by tati on 2009-04-19
Could you post the complete code of your /etc/rc.local file? This noob doesn't understand shell scripts.

---

### Post by psyke83 on 2009-04-20
Although the solution mentioned here works, it's better to use the standardized (Debian/Ubuntu) way to resolve module conflicts.

You want to blacklist the b43 module, and ensure the wl module loads properly, correct? So instead of using that script...

a) Edit /etc/modprobe.d/blacklist.conf:
```
$ gksudo gedit /etc/modprobe.d/blacklist.conf
```
Append to the end of this file, then save:
```
blacklist b43
```

b) Edit /etc/modules:
```
$ gksudo gedit /etc/modules
```
Append to the end of this file, then save:
```
wl
```

c) Remove your customizations from the /etc/rc.local file.

Step A will add the b43 module to the blacklist, preventing it from loading. Step B will add the wl module to the list of modules to be loaded (even if the system thinks that it's not necessary, as is the case for you). Step C will remove the non-standard customization you made. 

After a reboot, wireless should work automatically.

Providing this solution works, I recommend that you file a bug on your issue to ensure it gets fixed automatically in the future.

---

### Post by tati on 2009-04-21
Didn't work for me. No wireless networks are available after restart.

---

### Post by artjermyn on 2009-04-21
I had a similiar problem.  I had to blacklist b44 *and* ssb.  I added both of them to my blacklist file, saved it and ran the command: **sudo update-initramfs**.

Do this and reboot and see if it helps.

-- 
art

---

### Post by tati on 2009-04-21
Here's the output of **sudo update-initramfs**:

```
You must specify at least one of -c, -u, or -d.

Usage: /usr/sbin/update-initramfs [OPTION]...

Options:
 -k [version]	Specify kernel version or 'all'
 -c		Create a new initramfs
 -u		Update an existing initramfs
 -d		Remove an existing initramfs
 -t		Take over a custom initramfs with this one
 -b		Set alternate boot directory
 -v		Be verbose
 -h		This message
```

---

### Post by homerhomer on 2009-04-22
Wow, what a cluster!

Anyway I had an issue with my broadcom wireless card and had to use an older firmware to get it to work properly. 

[http://launchpadlibrarian.net/19141977/b43-all-fw.tar.gz](http://launchpadlibrarian.net/19141977/b43-all-fw.tar.gz)

Try this firmware, you'll have to copy the files to /lib/firmware/b43

hope it works

---

