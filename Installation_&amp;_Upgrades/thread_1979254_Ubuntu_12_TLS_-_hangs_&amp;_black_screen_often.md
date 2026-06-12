---
title: "Ubuntu 12 TLS - hangs &amp; black screen often"
date: 2012-05-13
forum: Installation &amp; Upgrades
---

### Post by ganeshkondal on 2012-05-13
My Machine configuration:
# Linux MyMachine 3.2.0-24-generic-pae #37-Ubuntu SMP Wed Apr 25 10:47:59 UTC 2012 i686 i686 i386 GNU/Linux

me@MyMachine:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04 LTS
Release:	12.04
Codename:	precise

Memory: 8GB Ram
Processor: Intel Quadcore - i5-2500K CPU @3.30GHz

Relevant history:
Ugraded from Ubuntu 11.10 to 12.04 TLS.  Before or the upgrade itself was of no issues.

Problems facing:
1) Hangs
On no pattern the machine hangs. I have to do a restart. 
2) Frequent black screen:
Atleast once a hour, I get a black screen for a moment, before I see the screen.
3) No input to monitor (rarely)
Since upgrade, on few occurrences I have seen -loosing input to the monitor (as if the machine is off). But the machine is not off & the applications are running in the system.


I am really repenting on why I upgraded from a very stable version (11.10) to this OS version. 

Any thoughts or help is deeply appreciated. If you folks need more data - let me know - what / how to capture the data, so I can attach that as well (like syslogs or something).

Thanks,
Ganesh

---

### Post by bogan on 2012-05-13
Hi!, **ganeshkondal**,

What Video card do you have ? PCI or integrated, or both ??

Please Post output from lspci | grep -i VGA  That's a small 'L' in 'lspci'

Do you use Bumblebee ??

Chao!, **bogan**.

---

### Post by ganeshkondal on 2012-05-13
# lspci output

lspci | grep -i VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

# I don't have bumblebee in the system.

---

### Post by Kanna2412 on 2012-05-14
My details are also some as
:~$ lspci | grep -i VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)

:~$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 12
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:fe000000-fe3fffff memory:d0000000-dfffffff ioport:f160(size=8)

My desktop resolution was 1920x1080 pixels and changed to 1024x768 pixels when I upgraded from 11.10 to 12.04 LTS. It goes blank and black screen very often. I have tried almost every forum on internet and then contacted Intel support. They told me that I needed to have proper drivers installed for the new OS which  cannot be provided by Intel.

Can anybody suggest me to solve the problem so that I can work with 12.04 LTS.


Kanna.

---

### Post by bogan on 2012-05-14
Hi!, **Kanna241**2 & **ganeshkondal**,

I do not know much about the Intel integrated GPU or the i915 driver, hopefully someone who does will respond. Meantime try searching "Intel i915 + Solved" or similar, for example:

[https://bbs.archlinux.org/viewtopic.php?id=132172](https://bbs.archlinux.org/viewtopic.php?id=132172)

Chao!,** bogan**.

---

### Post by Kanna2412 on 2012-05-16
Guys, I ran an comment *xrandr* so my previous resolution 1920x1080 listed as result. Then I opened System Settings>>Displays and then selected 1920x1080 and applied. I got the resolution. 
But when I restart my computer. It goes back to smaller resolution again and got the error:
*Could not apply the stored configuration for monitors* followed by list of smaller resolutions.

I have to do the same again and again every time I login to my computer. Can anybody please give me permanent solution? Thank you in advance.

---

### Post by bogan on 2012-05-17
Hi!,** All**.

[COLOR=Blue]There is a new nvidia driver version 295.53 available [/COLOR]from nvidia downloads.  This Link is for the 32 bit version, check you get the correct one.
[http://www.nvidia.co.uk/object/linux-display-ia32-295.53-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-295.53-driver-uk.html)

[COLOR=RoyalBlue]**Edit: Updated Thursday May 17th; **[/COLOR]     

     ```
nvidia-installer --latest
``` now returns: v295.53 and the currently installed version, without altering anything.
     

     ```
nvidia-installer -f
``` will install 295.53 after un-installing the previous version.

NVNews says of version 295.53:
QUOTE:
**Please note:** This [NVIDIA]("http://www.nvidia.com/") Linux graphics driver release supports **GeForce 6xxx and newer [NVIDIA]("http://www.nvidia.com/") GPUs**,
 [GeForce4]("http://viglink.pgpartner.com/rd.php?r=10313&m=878281881&q=o&priceret=87.73&pg=%7E%7E3&k=2b6229593608c3c1fb499d0ca9880634&source=feed&url=http%3A%2F%2Fmicropartsusa%2Ecom%2F31p6953%2Dibm%2Dnvidia%2Dgeforce4%2Dmx440%2D64mb%2Dagp8x%2Datx%2Dgraphics%2Dcard%2Dw%2Do%2Dcable%2Dnew%2Dbulk%2Din%2Dstock%2Ehtml&st=feed&mt=%7E%7E%7E%7E%7E%7E%7E%7En%7E%7E%7E") and older GPUs are supported through the **96.43.xx** and **71.86.xx** [NVIDIA]("http://www.nvidia.com/") legacy graphics drivers.
 GeForce FX GPUs are supported through the **173.14.xx** NVIDIA legacy graphics drivers.

[B]
bogan.[/B]

---

### Post by ganeshkondal on 2012-08-22
After living with this issue for quite some time., based on few user suggestions I have un-installed compiz-fusion/compiz-core; since then, only once it hung (in a period of a week). Feeling far better now.

Thanks,
Ganesh

---

### Post by ganeshkondal on 2012-09-03
Compiz came in via unity update again; even after removing unity I had multiple crashes. 

Tried xubuntu install (apt-get xubuntu-desktop). Since then life has been very good. Very stable and faster too (with the xfce desktop). I don't think I will get to unity again anytime soon - even though lookwise I like unity more than the xubuntu.  But in xubuntu you can get the ambiance/rediance themes which are decent.

So solution that worked - xubuntu.

Ganesh Kondal
Sep 3, 2012.

---

