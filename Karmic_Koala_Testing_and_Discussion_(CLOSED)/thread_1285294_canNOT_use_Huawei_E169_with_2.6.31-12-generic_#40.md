---
title: "canNOT use Huawei E169 with 2.6.31-12-generic #40"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by GeorgeVita on 2009-10-07
**[SIZE="3"]Update:[/SIZE]**
This bug still exists on 9.10rc kernel ( 2.6.31-14-generic #48 )
Some workarounds:
a. boot a previous kernel (if you have)
b. use other internet connection (wifi, eth or via a previous Ubuntu version (LiveCD etc.) to get the [patched kernel]("http://people.canonical.com/~apw/lp446146-karmic/")
c. try '[old-method]("http://ubuntuforums.org/showpost.php?p=8128534&postcount=13")' (may work on **E220**): ```
sudo rmmod usb-storage
sudo modprobe usbserial vendor=0x12d1 product=0x1003
```

Relative Bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)

------------------- 

Hi,
after recent updated ubuntu 9.10 with kernel **2.6.31-12-generic #40**, I cannot use my Huawei E169 3G modem.

System (dmesg) is looping creating/disconnecting ttyUSBx and the virtual CDROM appeared on desktop (1st time till 8.10).

Anybody else facing the same problem?

Thanks in advance,
George

---

### Post by jontxo on 2009-10-07
I have the same problem.

Ubuntu amd64.

Now I am downloading the daily build to see if it is solved with a new install.

---

### Post by lancest on 2009-10-07
Karmic 64- updated to latest
Huawei E620 working excellent here.

---

### Post by GeorgeVita on 2009-10-08
> **jontxo said:**
> I have the same problem.
Ubuntu amd64.
Now I am downloading the daily build to see if it is solved with a new install.

I am using **32bit** on EeePC 1000H. I can connect booting a previous kernel (hold shift while booting to see menu). Probably a new kernel update can solve it and not the current daily-build.

**EDIT**: system frozen trying to use E169 with kernel **2.6.31-12-generic #41**

G

---

### Post by dom-eckert on 2009-10-08
Same problem here, using Kubuntu Karmic 32-bit. Time for a bug report?

---

### Post by dom-eckert on 2009-10-08
Bug report filed to Launchpad.

---

### Post by GeorgeVita on 2009-10-08
Hi **dom-eckert**,
post here the bug# to be informed!

**EDIT: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146) **

>>> WORKAROUND: press Shift keys at boot to get Grub menu and then boot from a previous kernel

---

### Post by GeorgeVita on 2009-10-09
problem exists on **2.6.31-13-generic #42**

AND on Ubuntu Netbook Remix daily live (.iso) of 9-Oct-09 where Huawei E169 cannot be used at all as there is no previous kernel to boot!

**EDIT:** problem exists on **2.6.31-13-generic #43**
```
g@KKsep22:~$ dmesg
[ 1261.396207] usb 2-2: new full speed USB device using uhci_hcd and address 4
[ 1261.616651] usb 2-2: configuration #1 chosen from 1 choice
[ 1261.634400] scsi86 : SCSI emulation for USB Mass Storage devices
[ 1261.637423] usb-storage: device found at 4
[ 1261.637438] usb-storage: waiting for device to settle before scanning
[ 1261.744264] usb 2-2: USB disconnect, address 4
[ 1262.480201] usb 2-2: new full speed USB device using uhci_hcd and address 5
[ 1262.645650] usb 2-2: configuration #1 chosen from 1 choice
[ 1262.653302] option 2-2:1.0: GSM modem (1-port) converter detected
[ 1262.653695] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[ 1262.656890] option 2-2:1.1: GSM modem (1-port) converter detected
[ 1262.657342] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[ 1262.666827] option 2-2:1.2: GSM modem (1-port) converter detected
[ 1262.667166] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[ 1262.672207] scsi90 : SCSI emulation for USB Mass Storage devices
[ 1262.678576] usb-storage: device found at 5
[ 1262.678585] usb-storage: waiting for device to settle before scanning
[ 1267.678453] usb-storage: device scan complete
[ 1267.681422] scsi 90:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 1267.684423] scsi 90:0:0:1: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[ 1267.715350] sr0: scsi-1 drive
[ 1267.715798] sr 90:0:0:0: Attached scsi CD-ROM sr0
[ 1267.716193] sr 90:0:0:0: Attached scsi generic sg2 type 5
[ 1267.716944] sd 90:0:0:1: Attached scsi generic sg3 type 0
[ 1267.749246] option: option_instat_callback: error -108
[ 1267.749530] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 1267.749596] option 2-2:1.0: device disconnected
[ 1267.752224] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 1267.752271] option 2-2:1.1: device disconnected
[ 1267.755231] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[ 1267.755279] option 2-2:1.2: device disconnected
[ 1267.864140] usb 2-2: reset full speed USB device using uhci_hcd and address 5
[ 1268.011659] option 2-2:1.2: GSM modem (1-port) converter detected
[ 1268.011950] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[ 1268.012354] option 2-2:1.1: GSM modem (1-port) converter detected
[ 1268.012698] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[ 1268.013127] option 2-2:1.0: GSM modem (1-port) converter detected
[ 1268.013513] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[ 1268.091233] option: option_instat_callback: error -108
[ 1268.099009] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[ 1268.099071] option 2-2:1.0: device disconnected
[ 1268.099265] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 1268.099322] option 2-2:1.1: device disconnected
[ 1268.099495] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 1268.099547] option 2-2:1.2: device disconnected
[ 1268.212136] usb 2-2: reset full speed USB device using uhci_hcd and address 5
[ 1268.363660] option 2-2:1.2: GSM modem (1-port) converter detected
[ 1268.363949] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[ 1268.368194] option 2-2:1.1: GSM modem (1-port) converter detected
[ 1268.368600] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[ 1268.377822] option 2-2:1.0: GSM modem (1-port) converter detected
[ 1268.378069] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[ 1268.420234] option: option_instat_callback: error -108
[ 1268.437314] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[ 1268.437373] option 2-2:1.0: device disconnected
[ 1268.437538] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 1268.437591] option 2-2:1.1: device disconnected
[ 1268.437757] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 1268.437809] option 2-2:1.2: device disconnected
[ 1268.549191] usb 2-2: reset full speed USB device using uhci_hcd and address 5
[ 1268.699661] option 2-2:1.2: GSM modem (1-port) converter detected
[ 1268.699950] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[ 1268.700381] option 2-2:1.1: GSM modem (1-port) converter detected
[ 1268.700738] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[ 1268.704079] option 2-2:1.0: GSM modem (1-port) converter detected
[ 1268.704464] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[ 1268.764235] option: option_instat_callback: error -108
[ 1268.764481] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[ 1268.764540] option 2-2:1.0: device disconnected
[ 1268.764733] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 1268.764785] option 2-2:1.1: device disconnected

```
G

---

### Post by GeorgeVita on 2009-10-17
Just in case anybody can **HELP**:

[B]the patch of this bug MUST be included into final .iso
and NOT AFTER release of Ubuntu 9.10[/B]

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)

Informed that: > Andy Whitcroft  wrote 19 hours ago:  	  #39
The patch is now pulled into our tree. It is most likely to release as an SRU immediatly after release.
Changed in linux (Ubuntu):
status: 	Incomplete &#8594; Fix Committed 

Trying to prevent SRU:

> Russell Faull  wrote 25 minutes ago:  	  #40
Andy, do I understand you correctly that the fix for this problem will only be available in a kernel upgrade sometime after Karmic is available to the general public as a final release on 27 October?

If so, there will be many disappointed users of e169 modems. I expected the Ubuntu will also suffer pretty negative publicity. I hope I am misunderstanding your post..

BTW I am using the kernel with Ben's 'hack' patch you posted at #15. It works fine. Is there a chance of a new kernel complied with the final patch for testing through this forum?

Regards and thanks
> GeorgeVita wrote 5 seconds ago: 	#41
SRU ([https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)) is unacceptable!

This must be fixed BEFORE final release. Imagine a new user (Ubuntu/linux 'newbie') without any other Internet access:

Get Ubuntu 9.10, install it, use windows to get a new .deb, copy it to your Ubuntu 9.10 Desktop and double click it to install. 'Ubuntu via windows'...

We 'throw away' dial up (no wvdial), we do not want ZTE MF636 (ok this is a minority) now we need to patch LiveCDs for a Huawei 3G modem (very popular worldwide)?
... and I think you understand that this is not OUR problem as we are involved in testing (development phase) and we gain a lot of knowledge (Thanks!). Now we can use over 5 methods to connect with our 3G modems.
What about a newcomer?


---

### Post by CbrPad on 2009-10-18
+1 on that.  I've just installed todays daily image on my test partition only to find my Huawei E220 modem is comletely unusable.  

I've just tried the 2.6.31-13.44lp446146apw1 kernel that was linked from Launchpad 446146 and that doesn't work either.  

I'm in Ireland and there are LOTS of people who depend soley upon 3g modems, including myself.  To release Karmic like this would be horrendous.

---

### Post by finesse on 2009-10-19
This would be a big mistake to not include it in the released ISO, a problem like this will effect a lot of people.

What can we do about it now though? With the kernel freeze and all?

---

### Post by redbook4574 on 2009-10-19
> **CbrPad said:**
> +1 on that.  I've just installed todays daily image on my test partition only to find my Huawei E220 modem is comletely unusable.  

I've just tried the 2.6.31-13.44lp446146apw1 kernel that was linked from Launchpad 446146 and that doesn't work either.  

I'm in Ireland and there are LOTS of people who depend soley upon 3g modems, including myself.  To release Karmic like this would be horrendous.

Use Kernel 2.6.31-11 it works in this kernel

---

### Post by CbrPad on 2009-10-19
> **redbook4574 said:**
> Use Kernel 2.6.31-11 it works in this kernel

Bit of a chicken and egg situation though, how can I download it if I can't access the internet ?  Fair enough, I myself can probably download it in work, but for the average user this isn't a viable option, they just won't be able to connect and that's it, major fail.

I've found out I can eventually get my particular modem to work but it's incredibly fiddly..

sudo rmmod usb-storage
sudo modprobe usbserial vendor=0x12d1 product=0x1003

---

### Post by Rorohiko on 2009-10-19
Hi **CbrPad**!:)

> CbrPad  	
Re: canNOT use Huawei E169 with 2.6.31-12-generic #40
... I've just installed todays daily image on my test partition only to find my Huawei E220 modem is comletely unusable.

I've just tried the 2.6.31-13.44lp446146apw1 kernel that was linked from Launchpad 446146 and that doesn't work either.

I'm in Ireland and there are LOTS of people who depend soley upon 3g modems, including myself. ...
I'm a bit surprise, because I'm using meanwihle the kernel: '2.6.31-14' - it came with the normal update - and, because my E169 didn't work with this kernel ootb, I put the fixis (2.6.31-13.44lp446146apw1) on top of it and it works.

So I'm very happy with this solution (as long as it is not in the release).

Rorohiko

---

### Post by GeorgeVita on 2009-10-23
... waiting for the [patch]("http://launchpadlibrarian.net/33442788/patch0") to be included into final release of 9.10 ([problem]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146") exists on KK**rc**+updates), I got an 'all time classic' **[6.06.2]("http://releases.ubuntu.com/releases/6.06.2/")** server (equipped with kernel **2.6.15.51**), installed it to an old desktop and tried the **Huawei E169**

Result: it works!

I used: ```
sudo modprobe -r option
sudo modprobe -r usbserial
sudo modprobe usbserial vendor=0x12d1 product=0x1001
sudo pppd ttyUSB0 ...
```

Regards,
George

---

### Post by agurk on 2009-10-23
Yeah, releasing Karmic with a known (and patched) regression like this just isn't nice. Upgrade and BAM - you're offline.

I am not affected by this bug myself, but it will be sort of awkward promoting this release to dongle-toting friends and family.

---

### Post by GeorgeVita on 2009-10-24
... a 'desperate' **bump**

just in case

an authorized person will see this thread

and could 'try/reach/force' the released patch of this [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146") to be INTO final .iso

---

### Post by tiagoantao on 2009-10-25
Yet another desperate bump attempt.
This modem/dongle is USED MASSIVELY IN WESTERN EUROPE.
Vodafone, a big pan-European provider, sells their mobile net access with these dongles and they sell a lot.
For many people, this is the only kind of net access that they have. This not working equals NO INTERNET FOR MANY PEOPLE.

This is not "Medium", this is "Critical".

Wake up!

---

### Post by rfaull on 2009-10-25
But I think no-one is listening to users/power users. The release page for Karmic RC lists the kernel as 2.6.31-14.48. And this problem is not listed with the critical bug fixes, even though it has been committed as a fix for 10 days!

---

### Post by shereda on 2009-10-25
I have same problem and hope fix in Final Release.

---

