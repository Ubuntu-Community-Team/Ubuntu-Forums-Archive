---
title: "Help Needed With Install of 13.04 on AMD Architecture"
date: 2013-06-30
forum: Installation &amp; Upgrades
---

### Post by jakacitizenoftheearth on 2013-06-30
I have been having a horrible time trying to install a linux distro.  I just can't seem to get it up and running.  I was having trouble with Ubuntu 12.04 ( [http://ubuntuforums.org/showthread.php?t=2154486](http://ubuntuforums.org/showthread.php?t=2154486) ), and decided to do a slow write over both my hdd and my ssd,  I then just installed 13.04 on the ssd.  I was unable to get online during install, so I only have whatever came with the install .iso (from bootable USB created on another Linux computer.)  At the moment I have a black screen with a login prompt.  I do not know how to go about setting up my Internet/ finishing the install/ and then installing wireless/ graphic drivers.  I figured I would use this as a starting point, since there is literally no other files that can be causing issues, and it it should be easier for someone to walk me through step by step.  I am new to Linux, and to the terminal, so please be detailed.  I have done over 200 hours or research, and I am learning as I go, but by no means do I know what I am doing.  I am grateful for any help. 

My system:
[IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG]

Hardware:  
VGA ASUS HD 7770-2GD5  2Gb Ram
8Gbx2-GSkill F3-1866c10D-16Gb Ram

128 GB Samsung SSD
HDD 3Tb Toshiba DT01ACA300
CPU-AMD-8Core-FX-8320-3.5G-8M-R
Gigabyte GA-990FXA-UD3 AM3+ AMD 990FX SATA 6Gb/s USB 3.0 ATX AMD Motherboard
 Asus PCE-N10 Wireless-N Network Adapter (150 Mbs Transmit/Recieve) PCI-E interface-WPS
ASUS Vs228-H-P 22-Inch Full-HD 2ms LED-Lit LCD Monitor



My OS:

Ubuntu 13.04 installed from bootable USB, offline during install, checked "install third party software box," installed on entire 120GB SSD using automatic install (vs. advanced).


*Update: July-18-2013   With lots of help I have a wired connection up.   See the last few threads for details.  Here is the link that Bashing-om found that worked for me: 
"Re: Unable to get the RTL8111E working
I manage to get it working!!!! It was a BIOS level problem, there is a  setting in the Gigabyte BIOS called IOMMU (which comes disabled by  default), that must be enabled for get it working, no idea of what is  that option for, but it works!"

---

### Post by Bashing-om on 2013-06-30
cmcg513; Hi !

Let's back up and regroup...
Boot up the liveUSB and see if you can boot "try ubuntu" mode... What ever it takes to boot the "try ubuntu" mode will direct our attention to what must be done in the real install.

Be advised I am slow ..one step at a time kinda guy... I do anticipate having a graphics issue at this time... 

In the event you cannot boot up to a GUI in the liveUSB : Try to boot to the USB's boot options menu ->
What results at the purple splash screen when you press the tab key ? .. have not used a USB device to install from and best I recall the procedure differs from the CD/DVD method in that the tab key functions in place of the shift key. When you get to the boot menu screen ... f6 key for the preset boot options; try "nomodeset" ; space to accept, escape to exit back and enter to continue the boot process with the "nomodeset" parameter.

[INDENT][INDENT]where there is a will there is a way[/INDENT][/INDENT]

---

### Post by jakacitizenoftheearth on 2013-06-30
I have always been able to run the live session.  I will confirm when I have a chance.  Over the next 4 days I will only be able to pop into the forums a few hours a day, since I have summer finals coming up Wednesday.  Please know that this is not a lack of interest.  Do you mean there is a different boot screen than the BIOS boot options screen? (hitting F-12 on restart gives me the option to run Ubuntu, run the usb as UEF (which rarely works)I, run the USB normally (which gives me the option to install Ubuntu alongside, new, or try it from USB), or start up options (which is the BIOS menu).  I get home in about 8 hours.  I am usually available to chat from 1600-0200 Pacific time, but this week will be a bit more sporadic. Also, could you please explain the 'nomodset' thing a bit more?  Where am I entering this command?

---

### Post by Bashing-om on 2013-06-30
jakacitizenoftheearth; Hey ...

ubuntu boot screen ... yes entirely different than that of the bios boot screen... but as you advise there is no problem booting the live mode .. then let us see about booting into the install ... and rather then booting to a GUI ... try and boot to a test login. From there we can run a few commands and find out what is happening or not happening.
Nope, change of mind set -> First let's see if we can get a GUI up ... and then resort to the CLI if needed.

Boot the install ...at the install's boot menu hightlight the latest kernel of ubuntu ... and press the "e" key to enter edit mode: ->kernel parameters screen; arrow down to the line similar to this " linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff" ; arrow across to the term "quiet splash" and enter the term nomodeset just after "quiet splash" -within the quotes- ; key combo ctl+x to continue the boot process. Do you now boot to the GUI login ? degraded graphics is ok at this point ... fixable !

Understood about time constraints ! Exams and finals should take priority and precedence over all else at this time. I await you advisement. 

[INDENT][INDENT][INDENT]we be step'n[/INDENT][/INDENT][/INDENT]

---

### Post by ausyjedi on 2013-06-30
Hi, I am having a similar problem. I will try to be as detailed as possible. Created a Ubuntu live USB drive from both ubuntu-13.04-desktop-i386.iso and ubuntu-13.04-desktop-amd64.iso. When installing Ubuntu to a second 32Gb USB drive the i386 works an boots correctly to the Ubuntu desktop but the amd64 version will not boot. I have used universal installer to create the live USB drives as instructed for both systems on a windows 7 platform. any suggestions

---

### Post by Bashing-om on 2013-06-30
ausyjedi; Hi !

Too soon to say .. but let's cover the basic bases:

1. Is the machine 64 bit ? One may run 32 bit on 64 bit but not the reverse, no can do 64 bit on 32 bit machine.
2. Did you verify the md5sum (checksum) of the downloaded .iso image ?
3. Did you burn as an image at a slow burn rate ?
4. Check the USB file's integrity .. boot the usb (bios 1st priority) at the purple splash screen immediately press the tab or maybe shift key ... ->language screen (?) escape key to accept defaults -> boot options screen -> check disk.

At this boot menu screen are a number of options available with the use of the f function keys... f6 key yields a submenu of preset boot parameters... the one most used is "nomodeset" when a graphics problem is suspected. Arrow down to "nomodset" space accepts, escape exits back and key combo ctl+x continues the boot process.  

As you boot the 32 bit install amd cannot boot the 64 bit install ...and there are no problems encountered on the above ... I do not know what differences in drivers there may be between the two versions ...all we can do is try and see what haps.

[INDENT][INDENT][INDENT]hope this helps[/INDENT][/INDENT][/INDENT]

---

### Post by jakacitizenoftheearth on 2013-07-01
" /boot/vmlinuz-3.8.0-19-generic root=UUID+7f176015-596c-46dc-a66a-6dc6bc04a0ca ro  quiet splash **nomodset** $vt_handoff "    
Is what I typed, then I did CTRL + X and I booted to the same black screen.  
"your screen, graphics card, and input device settings could not be detected correctly.  You will need to configure these yourself."   
I hit ok and  am asked: 
"What would you like to do? Run in low graphics mode for just one session, reconfigure graphics, troubleshoot the error, exit to console login"    
Selecting "run in..."  results in: 
"Standby while the display restarts..."  
to wit, my computer freezes...


*However, Upon a manual reboot:  GUI  !!!  woot!  I can log in to my desktop! what's next?

**I tried my internet connections:  My wireless card did not automatically detect my home network.  I selected: connect to hidden wireless network> Name of network, security WPA2 personal > correct password.  It attempted to login, and disconnected.    
I plugged in the ethernet cable, it attempted to auto-configure the Ethernet "wired connection 1,"  it did not successfully connect, and every 25 seconds it give me a message "you are now disconnected."  (this is similar to the problem I was having before.)

*** Also, recieved an internal system error message but it disappeared before I could read it.  I caught "/Xorg" and "...3D Graphics"  The desktop appears to work fine, just no internet, and the front USB ports have power, but will not recognize devices, only the rear USB 3.0 will.

****Also, just to see where this was at:
USER@BOX:~$ sudo ifconfig
[sudo] password for USER: 
eth0      Link encap:Ethernet  HWaddr some colon stuff  
          inet6 addr: some more colon stuff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:1927 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:150 (150.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:numbers.and.dots  Mask:dots.and.numbers
          inet6 addr: ::number/number Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1208 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:98816 (98.8 KB)  TX bytes:98816 (98.8 KB)

wlan0     Link encap:Ethernet  HWaddr num:num:num:num 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

USER@BOX:~$ sudo ifconfig wlan0 up  (THIS DID NOTHING)
USER@BOX:~$ sudo iwconfig #
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          
USER@BOX:~$ sudo iwlist wlan0 s #
wlan0     No scan results

USER@BOX:~$ sudo iwconfig wlan0 essid NetworkNAME key PASSWORDENDINGINNUMBERS
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "NetworkNAME".

---

### Post by ausyjedi on 2013-07-01
> **Bashing-om said:**
> ausyjedi; Hi !  Too soon to say .. but let's cover the basic bases:  1. Is the machine 64 bit ? One may run 32 bit on 64 bit but not the reverse, no can do 64 bit on 32 bit machine. 2. Did you verify the md5sum (checksum) of the downloaded .iso image ? 3. Did you burn as an image at a slow burn rate ? 4. Check the USB file's integrity .. boot the usb (bios 1st priority) at the purple splash screen immediately press the tab or maybe shift key ... ->language screen (?) escape key to accept defaults -> boot options screen -> check disk.  At this boot menu screen are a number of options available with the use of the f function keys... f6 key yields a submenu of preset boot parameters... the one most used is "nomodeset" when a graphics problem is suspected. Arrow down to "nomodset" space accepts, escape exits back and key combo ctl+x continues the boot process.    As you boot the 32 bit install amd cannot boot the 64 bit install ...and there are no problems encountered on the above ... I do not know what differences in drivers there may be between the two versions ...all we can do is try and see what haps.  [INDENT][INDENT][INDENT]hope this helps[/INDENT][/INDENT][/INDENT]  Bashing-om; hey  Thanks for the quick response - wasn't expecting it that soon 1. Machine is an Asus i7 laptop running Windows 7 64 with 16G ram 2. Not sure on the checksum. did run a disk check on the Live USB - no errors reported. Have download the iso again in case of a download error. 3. Am able to run previous versions (12.04) amd64 without problems from an 8G USB drive on the same laptop.  I haven't en-counted this type of problem in the past so I'm a little perplexed. Will try the second download and let you know.

---

### Post by Bashing-om on 2013-07-01
jakacitizenoftheearth; Hey ..//


One thing at a time... until we have a solid GUI ... nothing else is important...
To that GUI situation ->
Ok boot up to the degraded graphics state -> Software Sources -> Additional Drivers ( I do not run the traditional desktop so not sure of the location of Additional Drivers) ... but anyway ... Find Additional Drivers .... and install all the recommended drivers... I am "hopeful" that the internet connection will make at this point (wired and connected, direct,  no router at this point)..... IF not ... all I can think of is to (re-) install with the check box checked at the initial screen to "install updates" ... it is a MUST to have that internet to do anything else,
Else: Boot up the liveDVD and insure the wired connection works in that live environment from the "try ubuntu" mode.

In order to get the wireless up we have to get the drivers ... to get the drivers we have to use the wired connection... nearly all wired drivers are in the kernel ... to initially establish a wired connection.

Get wired connection up and running;
Get the GUI up and functioning -> perhaps then with Additional Drivers all else will fall into place. 

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-07-01
@ ausyjedi .,...
I have not looked up the specs on your machine ,,, but let us for now pre-suppose that you are running with "hybrid" graphics. In that circumstance let us suppose that ubuntu (installed) is confused and does not know which driver to load...
Let us look directly and see what we have to work with;
Boot up the liveUSB -> desk top -> key combo ctl+alt+t yields a terminal interface... post back the outputs of:
So we can see your graphics card(s) and info:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga
lspci -vnn | grep -i VGA

```

[INDENT][INDENT]we will see what is to be seen[/INDENT][/INDENT]

---

### Post by jakacitizenoftheearth on 2013-07-01
So... I tried the nomodset thing again, and it did not work.  But I rebooted a few times, and the normal boot process, miraculously, took me to the GUI. I looked for additional drivers and none are present.  I still have no wired or wireless connection, but perhaps I just have to play with the wired network settings?  I have the ethernet cable coming from the wireless router.  This is the only way I can do it, since my whole house is set up on this internet.  I can get a connection through the cable via "auto Ethernet' on my Ubuntu laptop.  Anyway, I have a desktop, I have no proprietary drivers installed.  I can try to shuffle them over via usb.
Router is linksys WNR1000v2

---

### Post by Bashing-om on 2013-07-01
jakacitizenoftheearth; some good news that ..
Still got to get a wired connection up... so let us see if you are even getting out .. no point so far as I know even looking at configs at this time.. the kernel should have set all that up at install .. perhaps not working because you were not connected at install ?? Just not sure ..

Let's see if you are even getting out of house:
get to the desk top ... key combo ctl+alt+t gives a terminal interface:
Terminal codes:
```
ping -c3 74.125.227.160
dig

```
pings google and "dig" looks to see if the ISP server is found.
Any response at all ?

[INDENT][INDENT]we be try'n
[/INDENT][/INDENT]

---

### Post by jakacitizenoftheearth on 2013-07-01
Connect: Network is unreachable

; <<>> DiG 9.9.2-P1 <<>>
;; global options: +cmd
;; connection timed out; no servers could be reached

---

### Post by Bashing-om on 2013-07-01
jakacitizenoftheearth; ungood !

Not getting out..
What have you got for networking cards ?
```
lspci -v | grep -iE 'Wire|Ether'
```
and do we see your router ?
```
route
ip route
ping -c3 192.168.0.1 ##a common router IP .. yours may be different

```

[INDENT][INDENT]is baby even talking[/INDENT][/INDENT]

---

### Post by ausyjedi on 2013-07-01
Bashing-om, your right the graphics is a hybrid - intel and NVidia following is the info you requested.
 ubuntu@ubuntu:~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: GF108M [GeForce GT 630M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
  *-display
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)

ubuntu@ubuntu:~$ lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1477]
    Kernel driver in use: i915
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108M [GeForce GT 630M] [10de:0de9] (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1477]
    Kernel driver in use: nouveau
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)

ubuntu@ubuntu:~$ lspci -vnn | grep -i VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108M [GeForce GT 630M] [10de:0de9] (rev a1) (prog-if 00 [VGA controller])
ubuntu@ubuntu:~$ 


Another piece of info that might help, GParted reports that the install on the second USB drive doesn't have a bootable partition. 
I don't understand why the video driver would prevent the system from creating a bootable partition. 
Shouldn't the scripting revert to a generic driver? like the LiveUSB does? Just a thought. 
Will let you know shortly on the second download.

---

### Post by jakacitizenoftheearth on 2013-07-01
To the first command:   
04:0e.0 Firewire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI controller (rev c0) (prog-if 10 [OHCI])
Kernel driver in use: firewire_ohci
05:00.0 Ethernet controller (rev 06)


To the second:
Network is unreachable

(mine is 192.168.1.1)  the exact code I used was:  ```
ping -c3 192.168.1.1
```

---

### Post by Bashing-om on 2013-07-01
jakacitizenoftheearth;

OK.. Seems the card is not turned on .. try this:
in the top task bar is an indicator for networking. -> right click and choose "enable networking" and try and ping your router again.

There have been some changes in "networking" within the recent kernels... I will have to do some research to get back up to date with trouble shooting a network issue... what used to be - no longer applies as the files have been changed/moved.

If you bear with me ... and none others pop in here to assist .. we will work it out....

But for a quick check: boot up the liveDVD in "try ubuntu" mode and insure networking works in that environment.

[INDENT][INDENT]where there is a will there is a way[/INDENT][/INDENT]

---

### Post by jakacitizenoftheearth on 2013-07-01
There is no right click function.  But there is a dropdown menu and a checkbox.  It has been checked this whole time.  I unchecked it and rechecked it, upon the second ping I have received the same response.  The live enviornment is like a mirror of my desktop.  It has the same internet issues, and networking is checked by default.   So, Why does the terminal say that networking is not enabled while the icon says it is?

---

### Post by Bashing-om on 2013-07-01
ausyjedi...
Here is the situation:
Nvidia does not support hybrid graphics and therefore ubuntu does not cope well with hybrid graphics.
There are work-a-rounds entailing disabling one or the other of the graphic components .. there are pros and cons for either ... and the experience will not be good and/or hard on the hardware:
see:
  [http://ubuntuforums.org/showthread.php?t=1743535&highlight=i915&page=80](http://ubuntuforums.org/showthread.php?t=1743535&highlight=i915&page=80) A very long thread .. within which is a good discussion of your issue and suggested options.

And then there is the best solution: Intel/Nvidia ->optimus == BumbleBee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
Many have had success with it .. and I have seen good report - but it does take learning how to cope with switching graphics.

There are numerous threads on the forum in respect to BumbleBee and lots of info on the net ... Google search "bumblebee ubuntu" to guide you in making an informed decision.

[INDENT][INDENT]again, where there is a will a way can be made[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-07-02
jakacitizenoftheearth; Hey ..
sorry for the delay .. what I do not know is presently biting me in the rear. I knew there were some changes made to how networking performed,,, I am having to get up to speed on this ... and may take a bit of time for me to comprehend.

It is rare that the kernel can not build a driver ... but it does happen. I am concerned that the liveDVD cannot establish a connection, Indicative that a driver can not be built and we may have to provide some help in finding and loading a driver. 
Try and see what is not going on ->
For now.
I am old school thought patterns and my first approach to any trouble shooting is to verify the hardware, so if at all possible:
unplug the wired cable from the present install and plug it into another computer that is working wired. We want to verify that the router port is good and the cable is good... bent pins happen and loose connections happen.
All good ? plug back up to the computer we are working to get ubuntu installed onto, boot up the install to a terminal:
1. let's see what card is installed and driver in use:
```
lshw -C network
lspci -nn | grep Ethernet
lspci -nn | grep 0200 ##to get the bus number ID

```
2. And here is where I can not follow, perhaps because I am on a desk top and the reference is for a lap top ? What is your result?
```

cat /sys/devices/pci0000:00/0000:00:19.0/power/control

``` where "00:19.0" the bus # ID is to be replaced by what is the first numbers of "lspci -nn | grep 0200"
My Example output:
> sysop@1304mini:~$ lspci -nn | grep 0200
01:09.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
sysop@1304mini:~$
 -> MY bus ID in this instance being "01:09.0"


As to why Network Manager icon says connection is enabled... well that is just the front end for NM and only directs that the connection is to be established ... not that it is or can be made.

[INDENT][INDENT]best regards[/INDENT][/INDENT]

---

### Post by ausyjedi on 2013-07-02
Bashing-om

Thanks for your assistance to date, however I am still at a loss to see how the video driver would prevent the system from creating a bootable drive.
To verify what I stated before I downloaded a fresh copy of Ubuntu-desktop-12.10-amd64.iso.
Created a live USB drive using Universal-USB-Installer-1.9.3.6, and installed it to the same USB drive I have been testing.
Ubuntu 12.10 booted correctly. I then ran the required updates without problems(330Mb) vie wireless network.
Under 12.10 I have a full working system. The video driver may need customizing to get full functionality but everything else works fine.
I also downloaded a fresh copy of Ubuntu-desktop-13.04-amd64.iso - same result.
I can create a live USB drive using Universal-USB-Installer-1.9.3.6.
Booting from the Live USB drive I then install 13.04 to the same 32G USB drive. The install procedure works with errors but the drive will not boot!

Shouldn't 13.04 revert to the same generic video setup as 12.10 if the drivers are not available?
I suspect that there is some other issue that is preventing 13.04 from booting correctly.

Again 12.10 works perfectly with the same hardware.

---

### Post by jakacitizenoftheearth on 2013-07-02
I tested the ethernet cable on my laptop.  It works, I loaded webpages.  

When I entered the first command it recommended using SU, so I did.  Here is a copy/paste of the terminal, with commands included.


WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
USER@BOXNAME:~$ sudo su
[sudo] password for USER: 
root@BOXNAME:/home/searching# lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168 PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 06
       serial: 94:de:80:74:f8:de
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:75 ioport:b000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 10:bf:48:4a:84:ab
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.8.0-19-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 ioport:a000(size=256) memory:fe500000-fe503fff
root@BOXNAME:/home/searching# lspci -nn | grep Ethernet
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
root@BOXNAME:/home/searching# lspci -nn | grep 0200
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
root@BOXNAME:/home/searching# cat /sys/devices/pci0000:00/0000:05:00.0/power/control
cat: /sys/devices/pci0000:00/0000:05:00.0/power/control: No such file or directory

---

### Post by Bashing-om on 2013-07-02
jakacitizenoftheearth; Ok ..That rings a bell ... Seems I recall that with that card/driver combination.. we have to obtain the driver and install it ... It is going to be trying as we will have to transfer the driver files from another machine via a usb thumb drive (??)

Let me go and get my facts straight ... and all the ducks in a row .. and locate the method to get this accomplished. May take me more than a bit.

[INDENT][INDENT]I'll be Baackkk[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-07-02
ausyjedi; Hey,
I do appreciate the fact that you have a problem that you seek to solve.
However, your problem has nothing to do with this thread and only serves to dilute and pollute this thread.
I ask that you start your own thread - in which you have the control. I will meet you in that new post and do all that is in my power to resolve your situation.
Forum policy -> one problem, one thread.

[INDENT][INDENT]cheers and I will meet you
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-07-03
jakacitizenoftheearth; Hello !
Look what I ran across .. check your bios and see !


> Re: Unable to get the RTL8111E working
I manage to get it working!!!! It was a BIOS level problem, there is a setting in the Gigabyte BIOS called IOMMU (which comes disabled by default), that must be enabled for get it working, no idea of what is that option for, but it works!

It could be ->

[INDENT][INDENT]my fingers are crossed[/INDENT][/INDENT]

---

### Post by ausyjedi on 2013-07-03
My sincere apologies for the disturbance I have caused. I was unaware of the inconvenience it was causing.
As this is my first time using the Ubuntu community forum for assistance I am still learning the ropes.
I think I may have found the answer I need to solve the current problem.
Whether the solution works or not, do not worry yourself I will not be bothering you again !.

Good Luck!!!!

---

### Post by Bashing-om on 2013-07-03
ausyjedi;
Please, I do not mean to offend ..nor to detract from your solving your situation. We are all here to help and better assistance will be within your own thread... it is not a bother to assist in the least, merely greater focus on you in that separate thread, and that permits greater focus in this demanding thread. Again I assure you I will do all that I can to attain a solution.

[INDENT][INDENT]my regards[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-07-04
@ausyjedi... Hey 

I keep looking for the new post ... We are here to help.

@jakacitizenoftheearth; Anything new to this time ... are we looking at needing to install the drivers from the manufacturer ?

[INDENT][INDENT]just try'n to keep up
[/INDENT][/INDENT]

---

### Post by jakacitizenoftheearth on 2013-07-17
I just checked in. I will try the BIOS thing. I was also looking at flashing the BIOS as an option.  For some reason I wasn't getting any forum notifications.  I will let you know in the next day or two if the setting change worked.

---

### Post by Bashing-om on 2013-07-17
jakacitizenoftheearth; Hi !

I was in doubt that you had a continued interest ... or maybe exams were that bad !

Else: I have it on good authority to install a different driver from the manufacturer. (linux friendly)

[INDENT][INDENT]still learning even after all these years[/INDENT][/INDENT]

---

### Post by jakacitizenoftheearth on 2013-07-19
IT WORKED!!!!!! IT WORKED!!!!! IT WORKED!!!!!!!!!!!!!!!!!

I still have a ton of set up issues, I need to complete the installation, get my wireless drivers, etc.  But I have a wired connection!!!   Should I start a new thread for help getting the missing install packages?   Thank you soooooo much!

---

