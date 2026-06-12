---
title: "Minimal install - mini.iso - No Network Interfaces Detected"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by Muskoka on 2010-05-09
Hello,

Trying a minimal install with the mini.iso. I don't have a wired internet connection, only wireless from my iPhone which works fine with my full install of Ubuntu. The installer is not able to find my wireless connection stating "No Network Interfaces Detected". I did try to install yesterday in town with a friends wired internet connection and I got the same result. I'm able to get to the command line in the installer but have no idea how to start my wireless connection so the install can continue. I have searched here, and elsewhere on the net to the point of giving up. Any ideas/help would be great.

Thanks Glen

---

### Post by mörgæs on 2010-05-10
+1 for the minimal. All my future installs will be minimal, though the machine can support a full Ubuntu.

You will need a good and cheap (that is, wired) internet connection if you do a minimal install. Probably there are hundreds of MB to be downloaded. 

If you boot a full live CD with a wired connection, do you get access?

---

### Post by Muskoka on 2010-05-10
Hello,

Thanks for taking the time to respond. Yes to the question. No problems with wired or wireless with a live cd. I haven't had any problems with my network devices being detected until the minimal install with the mini.iso. I have had Ubuntu, Xubuntu, Lubuntu, Fedora, and Mint installed at various times and even as a quad boot with Windows 7 and everything installed just fine.

from sudo lspci -v

01:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
	Subsystem: Acer Incorporated [ALI] Device 029b
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at d3500000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at 2000 [size=128]
	Capabilities: [40] Power Management version 3
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [58] Express Endpoint, MSI 00
	Capabilities: [6c] Vital Product Data <?>
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [180] Device Serial Number ff-9e-26-00-a8-b2-b3-ff
	Kernel driver in use: atl1c
	Kernel modules: atl1c

02:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
	Subsystem: Intel Corporation Device 1301
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at d2500000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number 30-16-0d-ff-ff-d6-24-00
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

Any further help would be greatly appreciated. Thanks

Glen

---

### Post by mörgæs on 2010-05-11
There is a bug regarding drivers for this internet card:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/386468](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/386468)

Would be good if you could add your findings to the bug report. 


If an older minimal works then you could maybe try installing that and then upgrade to 10.04. I normally don't recommend upgrades, but in this case it could be worth a try.

---

### Post by Muskoka on 2010-05-11
Had a look at the bug report, thanks. 

My network devices work just fine. The only issue I've ever had is with the Ubuntu mini.iso, when I try to install. Neither the ethernet or wireless are detected. No list is presented to pick them from, nothing. I can get to a command-line but don't know what to do from there, still researching.  Perhaps I'll look for another distro's minimal install that's a little more accommodating with the network interfaces.

Glen

---

### Post by mikewhatever on 2010-05-11
Just a guess, but it could be that not all network cards are supported by the mini.iso. Trying another distro would be a good way to check. You can still get the Ubuntu minimal installation by using the Alternate iso. If that's an option, boot from the Alternate cd, hit f4 and select 'command line installation'.

---

### Post by btindie on 2010-06-25
The minimal install iso is missing a lot of the firmware required for wireless devices. If you take a look at the output from dmesg you see what file it's requesting, probably something like iwlwifi-5150-2.ucode.
 
I've done quite a few installs using a customised initrd from the mini.iso. You can remove all the unneeded firmware from /lib/firmware/ to save space and add in the required firmware file.

---

### Post by s990we on 2010-07-02
> **btindie said:**
> The minimal install iso is missing a lot of the firmware required for wireless devices. If you take a look at the output from dmesg you see what file it's requesting, probably something like iwlwifi-5150-2.ucode.
 
I've done quite a few installs using a customised initrd from the mini.iso. You can remove all the unneeded firmware from /lib/firmware/ to save space and add in the required firmware file.

Could you explain how I could do the opposite(add more network drivers) to the mini iso?

When I try to boot my netbook it says "No Network Interfaces Detected".

---

