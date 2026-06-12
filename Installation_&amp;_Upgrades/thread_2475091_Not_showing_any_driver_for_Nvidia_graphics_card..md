---
title: "Not showing any driver for Nvidia graphics card."
date: 2022-05-16
forum: Installation &amp; Upgrades
---

### Post by akashsinhaha on 2022-05-16
After upgrading to 22.04 from 20.04 in the Software and Updates > Additional Drivers
it says "No additional drivers available".

here is the lspci results

```
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 1 (rev e4)
00:1c.1 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 2 (rev e4)
00:1c.2 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 3 (rev e4)
00:1c.4 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 5 (rev e4)
00:1c.5 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 6 (rev e4)
00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller (rev 07)
09:00.0 3D controller: NVIDIA Corporation GF117M [GeForce 610M/710M/810M/820M / GT 620M/625M/630M/720M] (rev a1)
0a:00.0 Network controller: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe
0a:00.1 Bluetooth: Ralink corp. RT3290 Bluetooth



```

---

### Post by #&amp;thj^% on 2022-05-16
> 02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)

There is no special class for these devices in PCI, so it is shown as Unassigned class
EDIT: I guess i should ask if it works?

---

### Post by akashsinhaha on 2022-05-16
what should be the solution then?

---

### Post by #&amp;thj^% on 2022-05-16
dose it not work?
EDIT: You can also update the PCI IDs, just in case:
```
 sudo update-pciids && lspci -nn | grep "Card Reader"
```
EDIT: I see you updated your thread title, so follow post #5

---

### Post by grahammechanical on 2022-05-16
Ubuntu 22.04 was supposed to default to using Wayland. But when it was released it was defaulting to X,Org. This was because the Nvidia driver had problems working on Wayland. I do not know if Nvidia fixed this issue but it may be that Canonical has decided not to offer an Nvidia driver in Software & Updates so that installs of 22.04 can default to Wayland as intended.

[https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-22.04-NVIDIA-XOrg-Back](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-22.04-NVIDIA-XOrg-Back)

> The default session for most systems that don&#8217;t have an Nvidia graphics  card is now Wayland. If you need a non-Wayland session, you can choose  the *Ubuntu on Xorg* session by clicking the gear button after selecting your name on the login screen.

[https://discourse.ubuntu.com/t/jammy-jellyfish-release-notes/24668](https://discourse.ubuntu.com/t/jammy-jellyfish-release-notes/24668)

Regards

---

### Post by akashsinhaha on 2022-05-17
> **1fallen said:**
> dose it not work?
EDIT: You can also update the PCI IDs, just in case:
```
 sudo update-pciids && lspci -nn | grep "Card Reader"
```
EDIT: I see you updated your thread title, so follow post #5


How can i check if it works or not?
also i updated the PCI IDs and it still shows the same.

---

### Post by #&amp;thj^% on 2022-05-17
> **akashsinhaha said:**
> How can i check if it works or not?
also i updated the PCI IDs and it still shows the same.

Before you changed your title from lspci to "Not showing any driver for Nvidia graphics card." my post in #4 is non relevant now.

I have no defined solution for you: [https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1969566](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1969566)
along with the links grahammechanical provided.

Have you tried to login a X11 session and from there will the driver show up under 
```
sudo ubuntu-drivers devices
```
Your card will probably use the nvidia 390 or nvidia 470

---

### Post by cigtoxdoc on 2022-05-19
But then, how does one deal with:
$ sudo ubuntu-drivers devices
[sudo] password for john: 
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00000A75sv00001028sd00000441bc03sc00i00
vendor   : NVIDIA Corporation
model    : GT218M [GeForce 310M]
driver   : nvidia-340 - third-party non-free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin

---

### Post by #&amp;thj^% on 2022-05-19
by running:
```
sudo ubuntu-drivers autoinstall
```
or:
```
sudo apt install nvidia-340
```

---

### Post by cigtoxdoc on 2022-05-19
Thank you for your suggestion.  Results below:

sudo apt install nvidia-340
[sudo] password for john: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
nvidia-340 is already the newest version (340.108-4ppajammy5).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

AND

sudo ubuntu-drivers autoinstall
[sudo] password for john: 
All the available drivers are already installed.

---

### Post by deadflowr on 2022-05-19
On 22.04 the nvidia-340 package is a transitional package which simply installs the nouveau driver.
The nvidia driver itself is no longer supported for the kernel used in 22.04.
A workaround is to grab it from this PPA:[https://launchpad.net/~kelebek333/+archive/ubuntu/nvidia-legacy?field.series_filter=jammy]("https://launchpad.net/~kelebek333/+archive/ubuntu/nvidia-legacy?field.series_filter=jammy")
The driver from there is patched to run on 22.04's current kernel.

---

### Post by #&amp;thj^% on 2022-05-19
Sniped
see below

---

### Post by #&amp;thj^% on 2022-05-19
what is the return for this;
```
nvidia-smi
```
Plus i forgot about the below:
> **deadflowr said:**
> On 22.04 the nvidia-340 package is a transitional package which simply installs the nouveau driver.
The nvidia driver itself is no longer supported for the kernel used in 22.04.
A workaround is to grab it from this PPA:[https://launchpad.net/~kelebek333/+archive/ubuntu/nvidia-legacy?field.series_filter=jammy]("https://launchpad.net/~kelebek333/+archive/ubuntu/nvidia-legacy?field.series_filter=jammy")
The driver from there is patched to run on 22.04's current kernel.
Thanks to deadflowr for the reminder. :)

---

### Post by cigtoxdoc on 2022-05-19
Thank you for your suggestion.

Below is output of nvidia-smi
| Compute processes:                                               GPU Memory |
|  GPU       PID  Process name                                     Usage      |
|=============================================================================|
|    0            Not Supported                                               |
+-----------------------------------------------------------------------------+
john@john-Vostro-3500:~$ nvidia-smi
Thu May 19 19:00:26 2022       
+------------------------------------------------------+                       
| NVIDIA-SMI 340.108    Driver Version: 340.108        |                       
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce 310M        Off  | 0000:01:00.0     N/A |                  N/A |
| N/A   53C   P12    N/A /  N/A |    347MiB /   511MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Compute processes:                                               GPU Memory |
|  GPU       PID  Process name                                     Usage      |
|=============================================================================|
|    0            Not Supported                                               |
+-----------------------------------------------------------------------------+
john@john-Vostro-3500:~$ 

I have [https://launchpad.net/~kelebek333/+archive/ubuntu/nvidia-legacy?field.series_filter=jammy](https://launchpad.net/~kelebek333/+archive/ubuntu/nvidia-legacy?field.series_filter=jammy) ppa installed and it shows in synaptic.  I have done the sudo update all.  PC definetely is using part of the nVidia system as display is much faster than before I installed the kelebex333 ppa and did the update all.

John

---

### Post by #&amp;thj^% on 2022-05-19
Good News, make use of "nvidia-prime" to switch between cards as needed.
> nvidia-prime/jammy,jammy 0.8.17.1 all
  Tools to enable NVIDIA's Prime


---

### Post by cigtoxdoc on 2022-05-19
Thank you.  So is this the same as NVIDIA X Server Settings?  Nothing else shows up as a program.  Yes, have it set for maximum performance.

John

---

### Post by #&amp;thj^% on 2022-05-20
> **cigtoxdoc said:**
>  So is this the same as NVIDIA X Server Settings?  Nothing else shows up as a program. 
John
Yes but you should see a very limited window in settings.
IE:```
nvidia-settings
```
I can only imagine how that driver performs now, due to age of the driver.
Are you able to use nvidia-prime with it?
```
sudo prime-select intel
```
or:
```
sudo prime-select nvidia
```

---

