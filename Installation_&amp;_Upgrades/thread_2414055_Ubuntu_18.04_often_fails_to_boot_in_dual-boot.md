---
title: "Ubuntu 18.04 often fails to boot in dual-boot"
date: 2019-03-05
forum: Installation &amp; Upgrades
---

### Post by gipsyshadow on 2019-03-05
I've just built a PC with this cgf:
- amd ryzen 2200g with Vega 8 integrated graphics;
- msi b450-a pro and upgraded bios to its last release;
- 2x4gb hyperx predator @3200 cl16 (I let them work @2400 by default)
- no dedicated graph card

I've just installed windows 10 enterprise ltsc 2019 for 1st and ubuntu 18.04.2lts for 2nd and I could boot ubuntu with these 3 kernels: 4.15.0-29, 4.15.0-45, 4.18.0-15.
I knew I had to disable win fast boot and my bios secure boot to make ubuntu boots properly and those I did. In particular I did the following about my secure boot. This is the path to get secure boot within my MB's bios: settings - advanced - Windows OS Configuration - secure boot. The problem was that "Windows 10 WHQL Support" was disabled by default therefore I couldn't get/modify secure boot parameters, so I had to enable "Windows 10 WHQL Support" for 1st and then I could get secure boot parameters and they were set by deafult as:
secure boot control: disable
secure boot mode: standard
So I didn't modify them. Definetely I only enabled "Windows 10 WHQL Support" in my bios. I tried to disable "Windows 10 WHQL Support" but nothing changed, anyway I attach a pic with 2 photos taken from bios exiting message windows: one dealing with all disable->enable changes and the other one the opposite situation.

These are my problems.

- When I try to boot 4.18.0-15 kernel sometimes ubuntu session starts (like this time) and sometimes doesn't, I mean I can see the purple screen with kernel name but then black screen, I guess the PC reboots and monitor led gets yellow as there was no video signal and I have to reset.
When the 4.18.0-15 starts it freezes sometimes as soon as it starts and I open FF and I try to open a bookmark link.
I think amd drivers are loaded because of this:
```

$ sudo lshw -c display
  *-display                 
       description: VGA compatible controller
       product: Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:38:00.0
       version: c8
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix vga_controller bus_master cap_list
       configuration: driver=amdgpu latency=0
       resources: irq:53 memory:e0000000-efffffff memory:f0000000-f01fffff ioport:e000(size=256) memory:fe600000-fe67ffff

```
See driver=amdgpu.
I tried to get more infos and I booted 4.18.0-15 in recovery/emergency mode, I selected "root" from menu and run the shell. Then I gave "journalctl -xb" command to view system logs and I saw there were 3 lines of red colour:
line 498 - something related to "iommu..."
line 738 and 916 - same lines about "vgacon disables amdgpu..."

- Whenever I try to boot 4.15.0-29 kernel I get black screen and yellow monitor led and I've to reset manually. I added "nomodeset" parameter to boot options and the purple screen appeared with kernel name, then ubuntu loading logo appeared and then the emergency mode shell screen started though I booted the kernel in normal mode and not in recovery mode. Then I gave "journalctl -xb" command and I saw the same error lines like in 4.18.0-15 shell and other "interesting" errors like these 2 ones:
line 1223 - fat-fs (sda2): io charset iso8859-1 not found
line 1227 - failed to mount /boot/efi

So I guess there's a problem with sda2 efi partition. These outputs are got from this running 4.18.0-15 session:
```

$ sudo fdisk -l
[...]
Disk /dev/sda: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 80053721-D476-46FF-BDF8-55738A46C5DA

Dispositivo     Start       Fine    Settori   Size Tipo
/dev/sda1        2048    1023999    1021952   499M Windows recovery environment
/dev/sda2     1024000    1228799     204800   100M EFI System
/dev/sda3     1228800    1261567      32768    16M Microsoft reserved
/dev/sda4   103561216  266242047  162680832  77,6G Microsoft basic data
/dev/sda5     1261568  103561215  102299648  48,8G Linux filesystem
/dev/sda6   286722048 1953523711 1666801664 794,8G Microsoft basic data
/dev/sda7   266242048  286722047   20480000   9,8G Linux filesystem

Partition table entries are not in disk order.
[...]

```
```

$ efibootmgr -v
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001,0000
Boot0000* Windows Boot Manager    HD(2,GPT,55a5e162-f205-4baa-a392-b50d8540d604,0xfa000,0x32000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...I................
Boot0001* ubuntu    HD(2,GPT,55a5e162-f205-4baa-a392-b50d8540d604,0xfa000,0x32000)/File(\EFI\UBUNTU\SHIMX64.EFI)

```
In Gparted we can see the sda order is 1,2,3,5,4,7,6 (see attachment).

How can I solve my booting issues?

---

### Post by oldfred on 2019-03-05
While different brand, same chip.

       Gigabyte B450 Ryzen needs kernel & mesa drivers
[https://ubuntuforums.org/showthread.php?t=2408247](https://ubuntuforums.org/showthread.php?t=2408247)

---

### Post by gipsyshadow on 2019-03-05
So you think it's only a graphic drivers issue, nevermind the MB's WHQL matter nor sda order, don't you?
I followed the omgubuntu "solution" link [here](https://www.omgubuntu.co.uk/2018/06/mesa-18-1-1-ubuntu-18-04-ppa). Can you please confirm the following commands to get most recent mesa drivers?
```

sudo add-apt-repository ppa:ubuntu-x-swat/updates
sudo apt dist-upgrade
reboot
glxinfo | grep "OpenGL version"

```
and I'd get something like
```

OpenGL version string: X.X Mesa XX.X.X

```
Just a question. We can read this in omgubuntu page:
> 
You don&#8217;t need this PPA if you have patience
If you don&#8217;t want to install the update right now, you don&#8217;t have to. Ubuntu 18.04.1 LTS will ship with an updated graphics stack based on Mesa 18.1.x next month.

What's the meaning? I've got 18.04.2 so are the mesa drivers already present?

---

### Post by oldfred on 2019-03-05
Then they should already be present, unless further updates were released.

This shows what the ppa has:
[https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/updates](https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/updates)
It shows 18.3.3
So what version do you have?

The omgubuntu was about 18.1.1.

---

### Post by gipsyshadow on 2019-03-05
```

glxinfo | grep "OpenGL version"
OpenGL version string: 4.4 (Compatibility Profile) Mesa 18.2.2

```
So I'll try to install and run 18.3.3 by those commands above, ok?
A last question. I guess both drivers (universal & mesa) will be present, how to switch from universal ones to mesa ones?

Another matter of fact. Maybe it's a random phenomenon but 1 boot out of 2 attempts has success with 4.18.0-15 and that all the times.

---

### Post by oldfred on 2019-03-05
I really do not know AMD, but have these links also:

[https://ubuntuforums.org/showthread.php?t=2387396](https://ubuntuforums.org/showthread.php?t=2387396)
       Raven Ridge With The Ryzen 5 2400G On Mesa 18.2 + Linux 4.17 Is Finally Stable MSI B350M GAMING PRO
[https://www.phoronix.com/scan.php?page=article&item=ryzen-2400g-may&num=1](https://www.phoronix.com/scan.php?page=article&item=ryzen-2400g-may&num=1) 
   After adding "GRUB_GFXMODE=1920x1080x32" to the grub config the next reboot Ubuntu worked perfectly, both monitors fully functional and I could watch videos

---

### Post by gipsyshadow on 2019-03-06
Things are getting worse for me.
I was going to update to the latest mesa drivers as suggested but I could no more boot ubuntu! I tried with each one of the 3 kernels but I got the same result every time adding or not "nomodeset" parameter within boot options: purple display showing kernel name, ubuntu logo display and then emergency mode shell though I never chose recovery mode boot. I tried many times but I got only that, I guess ubuntu's definetely dead. Now I think the best way is to reinstall it.
It won't be my 2^ attempt to install ubuntu. Last time something strange happend: though I formatted both root and home partitions (I keep them separated) and their mount points were different home data were stored "somewhere" so I got the SAME desktop as the previous attempt and I refound my bookmarks in FF and I was already logged into my forums! I can't explain that because I'm sure I formatted both partitions. Can you give an explanation to that?

Now what about getting the latest 18.10 instead of 18.04lts? Will I get the latest mesa drivers with 18.10?
What about the "disordered" sda partitions? Could this be important in my booting issues and the impossibility to format home partition?
Is bios WQHL/secure boot option important to consider in this situation?

---

### Post by oldfred on 2019-03-06
Even if new system, have to checked that you have very latest UEFI from vendor. 
And if SSD, latest firmware for SSD?

I currently only boot with Secure Boot off. But may in future change and turn it on. 
In beginning it was often an issue particularly with some systems. 

I also only use the latest LTS version, currently 18.04, as main working install. But when I built this system, 16.04 was not yet released, but I needed latest kernel & Intel drivers, so installed 16.04 in late February or early March. I realized that system could crash at any time as I was then more a tester than a user. And it would get more than the usual amount of updates & logs would grow a lot.  Not sure if I totally reinstalled when released or not, but do try to houseclean. 
If willing to go thru that type of experiment, you can currently install 19.04. I do also have it installed and it has worked on my system. 
Issues have mostly been resolved, you now even can add a proprietary drive with UEFI Secure Boot on which previously you could not do.
If just wanting to test as install, use 25GB  as / (root) and install.

Partition order does not matter, Ubuntu uses UUID and and UEFI uses GUIDs with gpt for knowing what partition is what.

---

### Post by gipsyshadow on 2019-03-10
First of all sorry for my delay but I can't get email notifications. I just receive notifications of the first 3 replies for each one of my subscribed threads and then no more and I couldn't understand why. I asked to 2 moderators but I got no explanation of that and it's a real pain for me.

Anyway _I think I solved_ this booting issue and I'd like to share my solution with you both to contribute to this forum and to understand what I did because honestly I couldn't understand why it worked and I'd like to get a theoretic explanation.
During one of my installation attempts I tried to let ubuntu install its system automatically "near to" windows partition, I mean I let the system choose the root partition it preferred instead of me choosing root partition manually ("other" entry). What I saw was very weird because ubuntu showed the HDD as divided only into 2 partitions (see attachment) instead of the 7 partitions it's really divided into (see "fdisk -l" above). Though I'm very newbie I felt there was something wrong in the way ubuntu "saw" my HDD, something that relied before ubuntu live mounting therefore I supposed the problem was in the bios.

So I set the bios like that:
f6 (to reset) 
whql = enabled (and secure boot disabled)  -> therefore boot = uefi and couldn't be modified
secure boot mode = custom -> therefore the 2 following entries can be reset
delete all secure boot variables 
enroll all factory default keys 
boot order (I guess THIS was my lucky solution): #1 ubuntu live UEFI flash drive; **all the other devices set on disabled**
 
 In live environment I couldn't see the other partitions I'd always seen in the previous attempts (eg. storage).
During installation in this attempt there was no "install near to windows" option as 1st as in all the previous attempts but there was "erase ubuntu 18.04.2lts and reinstall" (ok, this is my personal english translation, don't take it literally). Anyway I chose to format manually root and home as usual and I let ubuntu chose boot loader partition.
After that I rebooted the bios and set it like this:
f6 
whql = disabled -> secure boot entry no more present  
boot = legacy+uefi 
boot order: #1 hdd ubuntu uefi, #2 hdd wd (I mean not-uefi hdd), other devices by default 
It worked until now, no more booting issues nor graphic ones.

I've only one note to show you but it could be not important because it's my first dual boot after many years so I don't remember if it's normal. After grub loading if I choose windows it just starts while if I choose ubuntu first I get black screen and yellow monitor led then I hear the usual PC/HDD booting/reloading noise and only then monitor led turns blue again. Then the mouse pointer appears on a black screen, I mean without showing ubuntu logo, and suddenly ubuntu desktop appears. When I close ubuntu session the ubuntu logo appears with the loading spots.
Is this normal? I'm afraid of that "double" like PC/HDD reloading every time I boot ubuntu because I'm afraid my HDD lifespan can be shortened by that in the long period.

So can you explain me why did this (lucky) attempt work? I do want to understand the reason because I think it's fundamental for my ubuntu learning.

---

### Post by oldfred on 2019-03-10
It now looks like you only have two partitions. Windows would then only work if MBR and booting in BIOS boot mode.
And then Ubuntu would install in BIOS boot mode.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 
    
Windows only boots in the now 35 year old BIOS mode from MBR partitioned drives.
And Windows only boots in the newer UEFI boot mode from gpt partitioned drives.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

### Post by gipsyshadow on 2019-03-10
I tried to get 2 boot-repair different reports because I'd like to understand if that "trick" had a sense or not, I mean setting only the uefi flash drive device for 1st and all the other devices not enabled. Therefore for first I set the bios under the conditions that leaded to the successful installation with that trick and I got [this 1st report](http://paste.ubuntu.com/p/2QK8DXnfBK/) and for second I re-enabled all the other devices in booting order list and got [this 2nd report](http://paste.ubuntu.com/p/JG7V49mC7B/).
Anyway I think I didn't recreate the same conditions I got for the successful installation because, as I said, in that live session I couldn't see any sda partition in "file" manager while this time all my partition were present there, moreover that time I had tried to insert another flash drive and it was not recognized while this time it was. Due to that I guess the 2 reports are the same. Now I really don't know how to recreate those conditions and it could be a trouble if they'll be necessary for another successful installation.

---

### Post by oldfred on 2019-03-10
You are showing all the standard partitions that a dual boot Windows & Ubuntu in UEFI boot mode would have.

Issue could have been that Windows fast start up was on? And note that Windows updates will turn it back on. Then grub will not boot Windows as grub only boots working Windows. If that happens just directly boot Windows from UEFI boot menu.

Your UEFI boot order still shows flash drive as first in boot order?
sudo efibootmgr -v

---

### Post by gipsyshadow on 2019-03-12
Now email notifications seem to work regularly. Have I to thank you? :)

Solved the strange ubuntu booting behavior (aka "double" booting). I checked my hdd booting counter with crystaldiskinfo in win10 and verified ubuntu boots only once. The thing that appeared strange to me was the difference between windows and ubuntu booting: the 1st one boot "directly" while the 2nd "indirectly" I mean first I got black screen, led yellow monitor and "no signal" message appears to my monitor, then led turns blue and ubuntu session starts. It could be interesting to understand why this difference even if not important, just to learn something :)

> 
Issue could have been that Windows fast start up was on?

I'm sure it was almost impossible win fast boot was enabled because I disable it as soon as I red my first guide to ubuntu dual boot.
By the way there's something I want to show you about 2 boot-repair reports, maybe it's important. As far as I could see there's only the following difference between the 2 reports:
```

Windows is hibernated, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.)

```
starting from line 530 within 2QK8DXnfBK report, I mean the 1st one so the one with only ubuntu uefi flash drive enabled as #1 booting device and all the other devices disabled. What do these lines mean? Could it be important in ubuntu installation?
I'm running win10 enterprise and updates are not so frequent as the other editions (home, pro) moreover I use anti-spy sw (eg. windows firewall control) to minimize the in/outgoing data.

As I said in my previous post I'm no more able to recreate those particular/strange conditions of the successful installation and now I'm afraid that if I'll install ubuntu again I'll get the same old troubles. What is most difficult to believe for myself too is that I couldn't see my storage partition in file manager during that live session moreover the second flash drive I inserted in usb port wasn't seen, it was as I inserted nothing. Therefore I'm afraid I forgot to note some parameters I set bios with that leaded to that "strange" but successful live session. So I'd want to ask you: what kind of "factors" can lead to that kind of live session?

> 
Partition order does not matter, Ubuntu uses UUID and and UEFI uses GUIDs with gpt for knowing what partition is what.

So you're definitely sure disordered partition scheme couldn't ever have a role in these kind of issues, aren't you?

Now 1st booting device is uefi hdd with ubuntu:
```

~$ efibootmgr -v
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001,0000,0002
Boot0000* Windows Boot Manager    HD(2,GPT,55a5e162-f205-4baa-a392-b50d8540d604,0xfa000,0x32000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...I................
Boot0001* ubuntu    HD(2,GPT,55a5e162-f205-4baa-a392-b50d8540d604,0xfa000,0x32000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0002* Hard Drive    BBS(HD,,0x0)/VenHw(5ce8128b-2cec-40f0-8372-80640e3dc858,0200)..GO..NO..........W.D.C. .W.D.1.0.0.3.F.Z.E.X.-.0.0.K.3.C.A.0...................\.,.@.r.d.=.X..........A.................................>..Gd-.;.A..MQ..L. . . . .W. .-.D.C.W.6.C.4.Y.N.F.P.L.1.N........BO

```

Thanks for you help :)

---

### Post by oldfred on 2019-03-12
I do not know AMD graphics.
But have seen some reports where the video mode switching is a known issue and is being worked on. One of my systems had nVidia & the other just Intel's video. If I in grub remove the quiet splash on the Linux line, all the boot process is shown. And near beginning I even see font change as it switches graphic mode. But with my SSD, boot is normally so fast now, that I do not see graphic issues. When I boot full install from flash drive, then it is a lot more noticeable.

---

### Post by gipsyshadow on 2019-03-20
hi oldfred,
thanks for your suggestions, I think I've got some improvements on my desperate buntu-way.
1stly I've upgraded my bios to its latest release (march 7th) and booting issues are solved now.
I'm still trying 18.04.2lts and I experienced those freezes I talked above. system freezes sometimes both during FF and using kate text editor (just once) so I don't think it's an issus related only to FF. I'd want to ask you what you suggest between trying upgrading mesa drivers (from 18.2.2 to 18.3.3) right now and trying to understand the cause that generates these freezes with current graphic drivers. anyway I've experienced no freezes from bios upgrading (yesterday). do you think there could be a link between bios and freezes?

---

### Post by oldfred on 2019-03-20
If you see a freeze, quickly go to terminal (usually still works) and run top to see what process is consuming system resources. And/or start system monitor.

I use gnome-panel or fallback which is similar to the old gnome2 or maybe mate desktops. And then I was able to put system monitor in top panel so I could click on it and see what was going on.

With my old laptop which only had 1.5GB of RAM, it would go to swap if I tried to load two larger programs at once. I could run Firefox and terminal or LibreOffice and terminal, but not both Firefox & LibreOffice or other larger programs. When switching to using swap screen would turn gray and everything paused for several seconds as hard drive was also old slow drive.

Some systems have run-away log files and need boot parameter to prevent those.  Particularly some models of Asus.

---

### Post by gipsyshadow on 2019-03-20
unfortunately when system freezes nothing works and i've to reset my desktop pc manually.
anyway do you think it'd be better to open a new thread for these freezes? the booting issues are solved now.

---

### Post by oldfred on 2019-03-20
Probably better to have new thread.
Post brand model and as much info as you can on the issue.
Include model & issue in title to see if anyone with similar system may have had issue and will see thread.

---

