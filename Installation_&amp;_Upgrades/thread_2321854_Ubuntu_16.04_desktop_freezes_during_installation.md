---
title: "Ubuntu 16.04 desktop freezes during installation"
date: 2016-04-24
forum: Installation &amp; Upgrades
---

### Post by skanger on 2016-04-24
I have n older HP DV8100 series laptop that has been used with previous versions of Ubuntu 64 bit (14.04, 13) and those installations have worked well.

However the installation of 16.04 freezes during the installation. At first I thought it was occurring only during the final hardware configuration part of the installation but it has happened earlier during the file copy section.

I know the cause could be related to many things, though I am certain that 64 bit 16.04 can run on this laptop (AMD ML-40 processor, 2GB ram, 240GB SSD in adapter tray). About the SSD, it functioned perfectly under Windows XP. Its new and was tested several times. Ubuntu should be able to install properly on an SSD. The drive shows up accurately in the BIOS boot selector. I tried disconnecting every external piece of hardware (USB express card, cardbus, etc). The install does start with a message about the synaptic touch pad not having a driver (or something similar) so I'm using a mouse which it recognized perfectly. Running the live DVD shows that the machine can handle the load, as the graphics are fairly smooth.

About the DVD, I have burned a second one (the first was 16.04 beta). though I know its possible the 2nd one could be bad.. The Md5sum was correct and the DVD was checked with the installer menu choice for analyzing the DVD  contents. It also checked out. 

The laptop is old and I wonder if the motherboard may have bad caps or some other low level problem, though the old Windows HDD never freezes. I wonder also if the DVD RW in the machine could be tired out during install. This machine can't boot from a USB DVD RW and if it did I would be using it, since the internal DVD RW is a replacement for the original which was failing, and now the replacement is old too. Maybe it has some intermittent problem and can't carry the install to completion. I have an external USB DVD RW abd would use it if I could. 

So this is my problem. I installed 16.04 on a new machine and its great. This old laptop still has life in it (XP works perfectly) so I want to put it to use. Its almost there and handles Ubuntu well. It just needs to get over this one hurdle.

Thanks for any help or suggestions. 
Sk.

---

### Post by DuckHook on 2016-04-24
There is probably nothing "wrong" with your HW except that you are trying to install too much of a resource hog onto it. Ubuntu proper takes a lot of resources, especially graphics, and your old laptop probably can't handle it. I would recommend installing Lubuntu, Xubuntu or Ubuntu-Mate. All three are less resource-heavy and should run on your machine. Try them out as LiveDVD/USB first and if they run, you should be good to go.

---

### Post by sammiev on 2016-04-25
Hi,

How much ram do you have?

It seems it comes with 256-MB DDR1 synchronous DRAM (SDRAM) at 333 MHz, expandable to 2.0 GB.

Do you have all the specs for this computer? 

If so, can you post them.

Thanks

---

### Post by Skaperen on 2016-04-25
does "Try Ubuntu" work?

---

### Post by skanger on 2016-04-25
> **Skaperen said:**
> does "Try Ubuntu" work?

"Try Ubuntu" works great. I was running it earlier with every program on the menu bar (8 Firefox tabs, all 3 Libre Office programs, the software center open, multiple folders open, the settings window open, etc.) all at once with no issues. The system was still responsive despite the relative sluggishness of the DVD RW. Windows were dragged with no lag or visible redraw time. Every feature was available and working well. In fact I would say that 16.04 is by far the fastest Ubuntu of the last 3 or 4 years - on this machine at least.

Clearly the problem is not with the specs of the machine, but some hangup or glitch due to a minor conflict. Hopefully its not hardware-based, though it would not seem to be as the DVD RW did not cause any problems working with the live DVD.

---

### Post by skanger on 2016-04-25
> **sammiev said:**
> Hi,

How much ram do you have?

It seems it comes with 256-MB DDR1 synchronous DRAM (SDRAM) at 333 MHz, expandable to 2.0 GB.

Do you have all the specs for this computer? 

If so, can you post them.

Thanks

No problem. As I mentioned in the original post, this machine has the maximum 2GB of RAM. The processor is an AMD Turion ML-40. It has an ATI Radeon Xpress Zoom graphics system with a maximum of 256MB memory. It can be run with as low as 128GB graphics memory. Also as mentioned in the original post, it has a 250GB SSD mounted in an mSATA to 44-pin ATA IDE adapter. That combination works well in Windows XP despite not having TRIM or other SSD utilities.

I don't have all the specs at the moment and HP has moved (retired as they say) most info on 10+ year old products. However if you have any questions about specific specs please ask. I never had an issue with any of the last 3 Ubuntu versions running on this machine. 

This machine does have WIFI, DVD RW, a touch pad, USB 2 and 1 ports, VGA out and most of the usual stuff 10 year old laptops had and new ones continue to have. I find it to be a very stable machine and have run a number of non-Linux and non-Windows operating systems on it. Again, let me know about any other specs you might need information about.

---

### Post by skanger on 2016-04-25
> **DuckHook said:**
> There is probably nothing "wrong" with your HW except that you are trying to install too much of a resource hog onto it. Ubuntu proper takes a lot of resources, especially graphics, and your old laptop probably can't handle it. I would recommend installing Lubuntu, Xubuntu or Ubuntu-Mate. All three are less resource-heavy and should run on your machine. Try them out as LiveDVD/USB first and if they run, you should be good to go.

I appreciate your suggestion. Apparently there is some minor installation hangup between 16.04 and this machine. 
I don't mind taking some time to get this problem sorted out.

---

### Post by DuckHook on 2016-04-25
> **skanger said:**
> ...I don't mind taking some time to get this problem sorted out.Your tenacity is admirable and exemplary. Have a cookie. ):P

---

### Post by sammiev on 2016-04-25
Hi,

With the ATI Radeon Xpress Zoom graphics you may need to run with 14.04 Lubuntu or Xubuntu. Not sure if the graphics card will work with 16.04 Lubuntu, Xubuntu or Ubuntu-Mate.

You can always try to run from a live USB/DVD

---

### Post by grahammechanical on 2016-04-25
It is a small point but I think it is relevant. If not to this particular problem but to the situation during the first restart after installation has finished. Do not tick the box Install third party software. That will set up a proprietary video driver. Each new version of Ubuntu comes with newer proprietary video drivers. And the proprietors of the drivers often drop support for what they consider to be obsolete video adapters. My video adapter is obsolete by Nvidia standards & is not supported by the latest proprietary video drivers in 16.04.

Another thing, make sure the DVD disc is clean & free from scratches & finger grease. You are at the point where wild guesses might be the solution. Most likely not but you never know.

There are three ways we can start a Ubuntu install session. It should not matter which way we choose but in the past I have found that on occasion it did make a difference. The three ways.

1) Allow the live session to load to a GUI Try/Install dialog. Select Install.
2) Allow the live session to load to a GUI Try/Install dialog. Select Try Ubuntu and then select Install Ubuntu from the icon on the live session desktop.
3) At the first purple screen with the icons of a human and a key board press enter. Then select an install language (default English ) and press enter. At the underlying screen with a text type menu select Install Ubuntu.

Regards & good luck.

---

### Post by skanger on 2016-04-25
> **grahammechanical said:**
> It is a small point but I think it is relevant. If not to this particular problem but to the situation during the first restart after installation has finished. Do not tick the box Install third party software. That will set up a proprietary video driver. Each new version of Ubuntu comes with newer proprietary video drivers. And the proprietors of the drivers often drop support for what they consider to be obsolete video adapters. My video adapter is obsolete by Nvidia standards & is not supported by the latest proprietary video drivers in 16.04.

Another thing, make sure the DVD disc is clean & free from scratches & finger grease. You are at the point where wild guesses might be the solution. Most likely not but you never know.

There are three ways we can start a Ubuntu install session. It should not matter which way we choose but in the past I have found that on occasion it did make a difference. The three ways.

1) Allow the live session to load to a GUI Try/Install dialog. Select Install.
2) Allow the live session to load to a GUI Try/Install dialog. Select Try Ubuntu and then select Install Ubuntu from the icon on the live session desktop.
3) At the first purple screen with the icons of a human and a key board press enter. Then select an install language (default English ) and press enter. At the underlying screen with a text type menu select Install Ubuntu.

Regards & good luck.

Thank you for the suggestions. The first two jogged my memory and I recall burning and cleaning a bunch of discs before getting a good install. That may also have been when I replaced the internal DVD RW. These are the kinds of minor issues that are behind many problems that appear to be difficult to solve.

About the video driver, I can recall this happening before with 13 or 14 on another older desktop. About support, they have been dropping a lot of support for "older" hardware in the past few years. I think someone advised me to do the same with those previous installations that were difficult: deselect the 3rd party support box. 

I haven't yet found an old machine (back to the SATA I days) that couldn't handle Ubuntu.

---

### Post by skanger on 2016-04-25
> **sammiev said:**
> Hi,

With the ATI Radeon Xpress Zoom graphics you may need to run with 14.04 Lubuntu or Xubuntu. Not sure if the graphics card will work with 16.04 Lubuntu, Xubuntu or Ubuntu-Mate.

You can always try to run from a live USB/DVD

I did try the live DVD and it worked very well. Graphics performance was more than adequate. 

I had a lot more problems trying to get 14.04 to run correctly on this machine and when it finally did work it was not as responsive as 16.04. Apparently they have cleaned and streamlined the installation and some of its components. 

I'm going to try skipping 3rd party drivers and see what happens. People with much better graphics systems have had far more difficulty than I with this "old" hardware.

Thank you.

---

### Post by skanger on 2016-04-25
> **DuckHook said:**
> Your tenacity is admirable and exemplary. Have a cookie. ):P

:lolflag:

---

### Post by skanger on 2016-04-29
> **grahammechanical said:**
> It is a small point but I think it is relevant. If not to this particular problem but to the situation during the first restart after installation has finished. Do not tick the box Install third party software. That will set up a proprietary video driver. Each new version of Ubuntu comes with newer proprietary video drivers. And the proprietors of the drivers often drop support for what they consider to be obsolete video adapters. My video adapter is obsolete by Nvidia standards & is not supported by the latest proprietary video drivers in 16.04.

Another thing, make sure the DVD disc is clean & free from scratches & finger grease. You are at the point where wild guesses might be the solution. Most likely not but you never know.

There are three ways we can start a Ubuntu install session. It should not matter which way we choose but in the past I have found that on occasion it did make a difference. The three ways.

1) Allow the live session to load to a GUI Try/Install dialog. Select Install.
2) Allow the live session to load to a GUI Try/Install dialog. Select Try Ubuntu and then select Install Ubuntu from the icon on the live session desktop.
3) At the first purple screen with the icons of a human and a key board press enter. Then select an install language (default English ) and press enter. At the underlying screen with a text type menu select Install Ubuntu.

Regards & good luck.

So far no luck with the above. I don't think the video driver is an issue since the live session works so well.

Is there any way of generating an installation log file?

I'm going to look at the SSD in windows and see what was installed. I noticed that rebooting the install SSD got the number lock and caps lock lights to be functional so I think the install progressed almost to completion.

---

### Post by skanger on 2016-04-30
> **skanger said:**
> No problem. As I mentioned in the original post, this machine has the maximum 2GB of RAM. The processor is an AMD Turion ML-40. It has an ATI Radeon Xpress Zoom graphics system with a maximum of 256MB memory. It can be run with as low as 128GB graphics memory. Also as mentioned in the original post, it has a 250GB SSD mounted in an mSATA to 44-pin ATA IDE adapter. That combination works well in Windows XP despite not having TRIM or other SSD utilities.

I don't have all the specs at the moment and HP has moved (retired as they say) most info on 10+ year old products. However if you have any questions about specific specs please ask. I never had an issue with any of the last 3 Ubuntu versions running on this machine. 

This machine does have WIFI, DVD RW, a touch pad, USB 2 and 1 ports, VGA out and most of the usual stuff 10 year old laptops had and new ones continue to have. I find it to be a very stable machine and have run a number of non-Linux and non-Windows operating systems on it. Again, let me know about any other specs you might need information about.

Here are the full specs:
[http://www.cnet.com/products/hp-pavilion-media-center-dv8125nr-17-turion-64-ml-32-win-xp-mce-2005-512-mb-ram-80-gb-hdd-plus-80-gb/specs/](http://www.cnet.com/products/hp-pavilion-media-center-dv8125nr-17-turion-64-ml-32-win-xp-mce-2005-512-mb-ram-80-gb-hdd-plus-80-gb/specs/)

Mine is a little different. It has an ML-40 and 2gb ram.

---

### Post by skanger on 2016-04-30
i was able to run the msata 250gb drive as a secondary drive under win xp 32 and its working very well. 

the 250gb drive is in a msata to pata 44 pin ide tray and shows up perfectly in the bios, win xp and ubuntu, though i wonder if the extra circuitry might be inducing some kind of problem. there are pins on this adapter for selecting master/slave settings, but none are marked, which i assume might mean that those settings might depend on the drive.

here is the adapter i'm using:

[http://www.ebay.com/itm/MSATA-mini-PCI-E-SATA-SSD-to-2-5-IDE-44-Pin-Adapter-Converter-Card-Portable-Kit-/331812974224?_trksid=p2141725.m3641.l6368](http://www.ebay.com/itm/MSATA-mini-PCI-E-SATA-SSD-to-2-5-IDE-44-Pin-Adapter-Converter-Card-Portable-Kit-/331812974224?_trksid=p2141725.m3641.l6368)

as i understand it, more recent ubuntu versions are programmed to perform trim and proper formatting for SSDs. windows xp doesn't have these functions and i didn't bother with finding utilities to attend to those functions, but the drive is extremely fast with no issues nevertheless. 

the bios sees the msata drive in its container perfectly, howsomever, there is always the possibility of a technical hangup with this arrangement.

any input is greatly appreciated.

---

### Post by skanger on 2016-05-01
the live session works very well - so well in fact i could just keep using it if i didn't need to customize things so much.

what doesn't work well, apparently, is power management. i found that the system freezes after the screen blanks for power saving (or maybe just for screen saver). it can't come out out of the lower power state for some reason. its either connected to video or power management. 

i'm sure i'll track this down after some experimenting though any suggestions or recommendations would be greatly appreciated. i had problems like this with other older machines that took a little extra effort but they've been running for years once those problems were corrected.

---

### Post by skanger on 2016-05-01
i turned off screen lock, but forgot to turn off screen dim. it was the screen dimming that froze the system. maybe this points to a video driver issue. i don't think the problem is the 3rd party driver. i think its the built-in driver that causes the problem since that driver is not installed until later in the installation. since the system can freeze during a live session without the 3rd party driver, it may be that the 3rd party driver can properly communicate with ubuntu whereas the built-in driver might be too generalized.

again, any suggestions greatly appreciated.

---

### Post by skanger on 2016-05-01
after turning off screen dim system continues without freeze.

---

### Post by skanger on 2016-05-07
have been getting very close to a full install, but haven't been able to get past hardware configuration at about 85% completion (according to the orange progress bar).

whatever it is that is freezing the system takes place there and must be the cause. is there any log file that can be accessed after the fact? 

16.04 is very responsive when running as a live session and functions well as a general purpose machine so i am sure it will work as a full install.

any wild guesses or specific suggestions will be greatly appreciated. i noticed the high view count for this thread. please jump in and write something even if it seems unlikely to help. thanks.

---

### Post by DuckHook on 2016-05-08
:shock:

skanger, I had unsubscribed from this thread some days ago and only just came across it again. During this time, you have continued to patiently bang your head against this particular wall. ](*,) Such perseverance surely deserves a response...

You've tried a lot of tricks on this old thing, but I believe that, throughout, you've been trying to install to an SSD hooked up by an adapter. I would suggest that you nix the adapter. Swap your XP HDD with the SSD and install directly through the motherboard's SATA port. See if that works.

Ubuntu keeps its installation logs in */var/log/installer/*. However, they can be massive. You'll have to use grep to whittle them down to size. Use the form:```
egrep -i 'warning|error|fatal' /var/log/installer/name_of_log
```...should save you some dreary scrolling.

---

### Post by skanger on 2016-05-08
> **DuckHook said:**
> :shock:

skanger, I had unsubscribed from this thread some days ago and only just came across it again. During this time, you have continued to patiently bang your head against this particular wall. ](*,) Such perseverance surely deserves a response...

You've tried a lot of tricks on this old thing, but I believe that, throughout, you've been trying to install to an SSD hooked up by an adapter. I would suggest that you nix the adapter. Swap your XP HDD with the SSD and install directly through the motherboard's SATA port. See if that works.

Ubuntu keeps its installation logs in */var/log/installer/*. However, they can be massive. You'll have to use grep to whittle them down to size. Use the form:```
egrep -i 'warning|error|fatal' /var/log/installer/name_of_log
```...should save you some dreary scrolling.

thanks for the reply and suggestions.

i have an extremely hard head and enjoy some good head banging.

about the system in question, its a laptop with no sata ports. it has two 44 pin pata ide channels and that's it, so its either the adapter with msata ssd or 2.5" hdd. right now all of hdds are tied up in file recovery so i have none to spare to test with this installation. besides, i expect to put the ssd to good use on this machine. its 250gb. apparently this laptop was of the last bunch before they started making them with sata ports, though its recognized and been used with all types of ssds (with pata or usb adapters)..  

can you suggest any particular logs to start with? i will put the ssd and its adapter in an external usb case and do the search on a properly working 16.04 machine (another piece of vintage hardware).

what do you think about this:
[h=4]5.4.4.1. System Freeze During the PCMCIA Configuration Phase[/h]   Some very old laptop models produced by Dell are known to crash when PCMCIA device detection tries to access some hardware addresses. Other laptops may display similar problems. If you experience such a problem and you don't need PCMCIA support during the installation, you can disable PCMCIA using the **hw-detect/start_pcmcia=false** boot parameter. You can then configure PCMCIA after the installation is completed and exclude the resource range causing the problems.  
   Alternatively, you can boot the installer in expert mode. You will then be asked to enter the resource range options your hardware needs. For example, if you have one of the Dell laptops mentioned above, you should enter **exclude port 0x800-0x8ff** here. There is also a list of some common resource range options in the [System resource settings section of the PCMCIA HOWTO]("http://pcmcia-cs.sourceforge.net/ftp/doc/PCMCIA-HOWTO-1.html#ss1.12"). Note that you have to omit the commas, if any, when you enter this value in the installer.  

makes a lot of sense to me and i'll try it. 16.04 is working so well on this machine that i'm convinced the problem is some minor hangup like this. with my rock hard head i expect to use this laptop as my main travel machine. wine runs almost all of the windows crap i use so i will be set for another ten years with this thing.

---

### Post by DuckHook on 2016-05-08
Since you are treating this as an intellectual exercise and an educational challenge that is rewarding in its own right, then by all means, try each fix you can. Just be sure to back out your previous fix before applying the next one. That way, you can track what is working and what is not. You might also find the *Old HW* link in my signature useful.

I'm frankly surprised that you are happy with the performance of Ubuntu proper on a laptop so old that it doesn't even have SATA. I've got a few of those that run Lubuntu acceptably, but that's about all the OS that those baby's can handle.

Keep swinging for the fences. We're all cheering for you from here in the peanut gallery. ;)

---

### Post by DuckHook on 2016-05-08
FWIW, since you can boot into a Live session, please do the following and post back to this thread:```
sudo lshw -numeric -sanitize
``````
lspci -vvnn
``````
lsusb -v
```The above will generate significant output, so please wrap in *CODE* brackets before posting.

It occurred to me only now that I didn't answer your question re: logs. It doesn't hurt to go through them all, but especially *syslog* and *debug*. Note, the installer syslog is different from your everyday one. Hopefully, the installation progresses far enough that logs are generated. The last entries would likely be the important ones anyway.

---

### Post by skanger on 2016-05-14
> **DuckHook said:**
> FWIW, since you can boot into a Live session, please do the following and post back to this thread:```
sudo lshw -numeric -sanitize
``````
lspci -vvnn
``````
lsusb -v
```The above will generate significant output, so please wrap in *CODE* brackets before posting.

It occurred to me only now that I didn't answer your question re: logs. It doesn't hurt to go through them all, but especially *syslog* and *debug*. Note, the installer syslog is different from your everyday one. Hopefully, the installation progresses far enough that logs are generated. The last entries would likely be the important ones anyway.

here they are:

```

ubuntu@ubuntu:~$ sudo lshw -numeric -sanitize
computer                  
    description: Computer
    width: 64 bits
    capabilities: smbios-2.31 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1873MiB
     *-cpu
          product: AMD Turion(tm) 64 Mobile Technology ML-40
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          size: 1600MHz
          capacity: 2200MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow rep_good nopl pni lahf_lm 3dnowprefetch vmmcall cpufreq
     *-pci:0
          description: Host bridge
          product: RS480/RS482/RS485 Host Bridge [1002:5950]
          vendor: Advanced Micro Devices, Inc. [AMD/ATI] [1002]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RC4xx/RS4xx PCI Bridge [int gfx] [1002:5A3F]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI] [1002]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:9000(size=4096) memory:b0100000-b01fffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS480M [Mobility Radeon Xpress 200] [1002:5955]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI] [1002]
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=66 mingnt=8
                resources: irq:17 memory:c0000000-cfffffff ioport:9000(size=256) memory:b0100000-b010ffff memory:b0120000-b013ffff
        *-pci:1
             description: PCI bridge
             product: RC4xx/RS4xx PCI Express Port 1 [1002:5A36]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI] [1002]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode cap_list
             configuration: driver=pcieport
             resources: irq:0
        *-usb:0
             description: USB controller
             product: IXP SB4x0 USB Host Controller [1002:4374]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI] [1002]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci-pci latency=64
             resources: irq:19 memory:b0000000-b0000fff
           *-usbhost
                product: OHCI PCI host controller [1D6B:1]
                vendor: Linux 4.4.0-21-generic ohci_hcd [1D6B]
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=4 speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: IXP SB4x0 USB Host Controller [1002:4375]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI] [1002]
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci-pci latency=64
             resources: irq:19 memory:b0001000-b0001fff
           *-usbhost
                product: OHCI PCI host controller [1D6B:1]
                vendor: Linux 4.4.0-21-generic ohci_hcd [1D6B]
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=4 speed=12Mbit/s
              *-usb
                   description: Mouse
                   product: USB Trackball [46D:C408]
                   vendor: Logitech [46D]
                   physical id: 3
                   bus info: usb@3:3
                   version: 14.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=50mA speed=2Mbit/s
        *-usb:2
             description: USB controller
             product: IXP SB4x0 USB2 Host Controller [1002:4373]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI] [1002]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:19 memory:b0002000-b0002fff
           *-usbhost
                product: EHCI Host Controller [1D6B:2]
                vendor: Linux 4.4.0-21-generic ehci_hcd [1D6B]
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=8 speed=480Mbit/s
              *-usb:0
                   description: Mass storage device
                   product: 816820090226 [3207:300]
                   vendor: 816820090226 [3207]
                   physical id: 4
                   bus info: usb@1:4
                   logical name: scsi2
                   version: 1.00
                   serial: [REMOVED]
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=500mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      physical id: 0.0.0
                      bus info: scsi@2:0.0.0
                      logical name: /dev/sdc
                      size: 29GiB (31GB)
                      capabilities: partitioned partitioned:dos
                      configuration: logicalsectorsize=512 sectorsize=512
                    *-volume
                         description: Windows FAT volume
                         physical id: 1
                         bus info: scsi@2:0.0.0,1
                         logical name: /dev/sdc1
                         logical name: /media/ubuntu/disk
                         version: FAT32
                         serial: [REMOVED]
                         size: 29GiB
                         capacity: 29GiB
                         capabilities: primary fat initialized
                         configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=999,gid=999,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
              *-usb:1
                   description: Printer
                   product: Deskjet 1050 J410 series [3F0:8911]
                   vendor: HP [3F0]
                   physical id: 5
                   bus info: usb@1:5
                   version: 1.00
                   serial: [REMOVED]
                   capabilities: usb-2.00 bidirectional
                   configuration: driver=usblp maxpower=2mA speed=480Mbit/s
        *-serial
             description: SMBus
             product: IXP SB4x0 SMBus Controller [1002:4372]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI] [1002]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:8400(size=16) memory:b0003000-b00033ff
        *-ide
             description: IDE interface
             product: IXP SB4x0 IDE Controller [1002:4376]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI] [1002]
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:8410(size=16)
        *-isa
             description: ISA bridge
             product: IXP SB4x0 PCI-ISA Bridge [1002:4377]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI] [1002]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: IXP SB4x0 PCI-PCI Bridge [1002:4371]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI] [1002]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:a000(size=4096) memory:b0200000-b02fffff memory:80000000-83ffffff
           *-network:0
                description: Network controller
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14E4:4318]
                vendor: Broadcom Corporation [14E4]
                physical id: 2
                bus info: pci@0000:06:02.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=b43-pci-bridge latency=64
                resources: irq:21 memory:b0204000-b0205fff
           *-pcmcia
                description: CardBus bridge
                product: PCIxx21/x515 Cardbus Controller [104C:8031]
                vendor: Texas Instruments [104C]
                physical id: 4
                bus info: pci@0000:06:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:20 memory:b0208000-b0208fff ioport:a400(size=256) ioport:a800(size=256) memory:80000000-83ffffff memory:84000000-87ffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: OHCI Compliant IEEE 1394 Host Controller [104C:8032]
                vendor: Texas Instruments [104C]
                physical id: 4.2
                bus info: pci@0000:06:04.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:23 memory:b0209000-b02097ff memory:b0200000-b0203fff
           *-storage
                description: Mass storage controller
                product: PCIxx21 Integrated FlashMedia Controller [104C:8033]
                vendor: Texas Instruments [104C]
                physical id: 4.3
                bus info: pci@0000:06:04.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=64 maxlatency=4 mingnt=7
                resources: irq:23 memory:b0206000-b0207fff
           *-generic
                description: SD Host controller
                product: PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [104C:8034]
                vendor: Texas Instruments [104C]
                physical id: 4.4
                bus info: pci@0000:06:04.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64 maxlatency=4 mingnt=7
                resources: irq:20 memory:b020a000-b020a0ff memory:b0209c00-b0209cff memory:b0209800-b02098ff
           *-network:1
                description: Ethernet interface
                product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10EC:8139]
                vendor: Realtek Semiconductor Co., Ltd. [10EC]
                physical id: 6
                bus info: pci@0000:06:06.0
                logical name: enp6s6
                version: 10
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half ip=[REMOVED] latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
                resources: irq:22 ioport:a000(size=256) memory:b020a400-b020a4ff
        *-multimedia
             description: Multimedia audio controller
             product: IXP SB400 AC'97 Audio Controller [1002:4370]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI] [1002]
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=snd_atiixp latency=64 mingnt=2
             resources: irq:17 memory:b0003400-b00034ff
        *-communication
             description: Modem
             product: IXP SB400 AC'97 Modem Controller [1002:4378]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI] [1002]
             physical id: 14.6
             bus info: pci@0000:00:14.6
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: msi generic bus_master cap_list
             configuration: driver=snd_atiixp_modem latency=64 mingnt=2
             resources: irq:17 memory:b0003800-b00038ff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
          vendor: Advanced Micro Devices, Inc. [AMD] [1022]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map [1022:1101]
          vendor: Advanced Micro Devices, Inc. [AMD] [1022]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
          vendor: Advanced Micro Devices, Inc. [AMD] [1022]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
          vendor: Advanced Micro Devices, Inc. [AMD] [1022]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk:0
             description: ATA Disk
             product: Samsung SSD 850
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1B6Q
             serial: [REMOVED]
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=c77b959b
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 1.0
                serial: [REMOVED]
                size: 231GiB
                capacity: 231GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2016-05-09 02:57:13 filesystem=ext4 lastmountpoint=/target modified=2016-05-09 02:57:16 mounted=2016-05-09 02:57:16 state=clean
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 1917MiB
                capacity: 1917MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1917MiB
                   capabilities: nofs
        *-disk:1
             description: ATA Disk
             product: SAMSUNG SSD UM41
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/sdb
             version: 2D1Q
             serial: [REMOVED]
             size: 14GiB (16GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=49a749a6
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.1.0,1
                logical name: /dev/sdb1
                version: 3.1
                serial: [REMOVED]
                size: 14GiB
                capacity: 14GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2016-05-11 04:31:55 filesystem=ntfs state=clean
     *-scsi:1
          physical id: 3
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD writer
             product: CD/DVDW TS-L532M
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             logical name: /cdrom
             version: HR08
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
                logical name: /cdrom
                capabilities: partitioned partitioned:dos
                configuration: mount.fstype=iso9660 mount.options=ro,noatime signature=0e0e8e70 state=mounted
              *-volume UNCLAIMED
                   description: Windows FAT volume
                   vendor: mkfs.fat
                   physical id: 2
                   version: FAT12
                   serial: [REMOVED]
                   size: 15EiB
                   capabilities: primary boot fat initialized
                   configuration: FATs=2 filesystem=fat
```

```
ubuntu@ubuntu:~$ lspci -vvnn
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD/ATI] RS480/RS482/RS485 Host Bridge [1002:5950] (rev 01)
    Subsystem: Hewlett-Packard Company RS480/RS482/RS485 Host Bridge [103c:309b]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 64

00:01.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Bridge [int gfx] [1002:5a3f] (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: b0100000-b01fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel modules: shpchp

00:04.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Express Port 1 [1002:5a36] (prog-if 00 [Normal decode])
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller [1002:4374] (prog-if 10 [OHCI])
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller [1002:4374]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at b0000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci-pci

00:13.1 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller [1002:4375] (prog-if 10 [OHCI])
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller [1002:4375]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at b0001000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci-pci

00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB2 Host Controller [1002:4373] (prog-if 20 [EHCI])
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB2 Host Controller [1002:4373]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at b0002000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 SMBus Controller [1002:4372] (rev 11)
    Subsystem: Hewlett-Packard Company IXP SB4x0 SMBus Controller [103c:309b]
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Region 0: I/O ports at 8400 [size=16]
    Region 1: Memory at b0003000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c_piix4

00:14.1 IDE interface [0101]: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 IDE Controller [1002:4376] (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company IXP SB4x0 IDE Controller [103c:309b]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin A routed to IRQ 16
    Region 0: I/O ports at 01f0 [size=8]
    Region 1: I/O ports at 03f4
    Region 2: I/O ports at 0170 [size=8]
    Region 3: I/O ports at 0374
    Region 4: I/O ports at 8410 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp, pata_acpi

00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-ISA Bridge [1002:4377]
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-PCI Bridge [1002:4371] (prog-if 01 [Subtractive decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Bus: primary=00, secondary=06, subordinate=08, sec-latency=64
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: b0200000-b02fffff
    Prefetchable memory behind bridge: 80000000-83ffffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-

00:14.5 Multimedia audio controller [0401]: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB400 AC'97 Audio Controller [1002:4370] (rev 02)
    Subsystem: Hewlett-Packard Company IXP SB400 AC'97 Audio Controller [103c:309b]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (500ns min), Cache Line Size: 32 bytes
    Interrupt: pin B routed to IRQ 17
    Region 0: Memory at b0003400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: snd_atiixp
    Kernel modules: snd_atiixp

00:14.6 Modem [0703]: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB400 AC'97 Modem Controller [1002:4378] (rev 02) (prog-if 00 [Generic])
    Subsystem: Hewlett-Packard Company IXP SB400 AC'97 Modem Controller [103c:309b]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (500ns min), Cache Line Size: 32 bytes
    Interrupt: pin B routed to IRQ 17
    Region 0: Memory at b0003800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: snd_atiixp_modem
    Kernel modules: snd_atiixp_modem

00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Capabilities: <access denied>

00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Kernel driver in use: k8temp
    Kernel modules: k8temp

01:05.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RS480M [Mobility Radeon Xpress 200] [1002:5955] (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company RS480M [Mobility Radeon Xpress 200] [103c:309b]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 66 (2000ns min), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Region 1: I/O ports at 9000 [size=256]
    Region 2: Memory at b0100000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at b0120000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeonfb, radeon

06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN [103c:1355]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin A routed to IRQ 21
    Region 0: Memory at b0204000 (32-bit, non-prefetchable) [size=8K]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

06:04.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
    Subsystem: Hewlett-Packard Company PCIxx21/x515 Cardbus Controller [103c:309b]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 168, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 20
    Region 0: Memory at b0208000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=06, secondary=07, subordinate=07, sec-latency=176
    Memory window 0: 80000000-83ffffff (prefetchable)
    Memory window 1: 84000000-87ffffff
    I/O window 0: 0000a400-0000a4ff
    I/O window 1: 0000a800-0000a8ff
    BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
    16-bit legacy interface ports at 0001
    Capabilities: <access denied>
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

06:04.2 FireWire (IEEE 1394) [0c00]: Texas Instruments OHCI Compliant IEEE 1394 Host Controller [104c:8032] (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company OHCI Compliant IEEE 1394 Host Controller [103c:309b]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (500ns min, 1000ns max), Cache Line Size: 32 bytes
    Interrupt: pin C routed to IRQ 23
    Region 0: Memory at b0209000 (32-bit, non-prefetchable) [size=2K]
    Region 1: Memory at b0200000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire_ohci

06:04.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
    Subsystem: Hewlett-Packard Company PCIxx21 Integrated FlashMedia Controller [103c:309b]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (1750ns min, 1000ns max), Cache Line Size: 32 bytes
    Interrupt: pin B routed to IRQ 23
    Region 0: Memory at b0206000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: tifm_7xx1
    Kernel modules: tifm_7xx1

06:04.4 SD Host controller [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [104c:8034]
    Subsystem: Hewlett-Packard Company PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [103c:309b]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (1750ns min, 1000ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 20
    Region 0: Memory at b020a000 (32-bit, non-prefetchable) [size=256]
    Region 1: Memory at b0209c00 (32-bit, non-prefetchable) [size=256]
    Region 2: Memory at b0209800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci_pci

06:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [103c:309b]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 128 (8000ns min, 16000ns max)
    Interrupt: pin A routed to IRQ 22
    Region 0: I/O ports at a000 [size=256]
    Region 1: Memory at b020a400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: 8139cp, 8139too

```


```
Bus 001 Device 003: ID 03f0:8911 Hewlett-Packard 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x03f0 Hewlett-Packard
  idProduct          0x8911 
  bcdDevice            1.00
  iManufacturer           1 HP
  iProduct                2 Deskjet 1050 J410 series
  iSerial                 3 CN18V1H0VD05QT
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           62
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    204 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               7
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x08  EP 8 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x89  EP 9 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            4.04
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12

Bus 003 Device 002: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc408 Marble Mouse (4-button)
  bcdDevice           14.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               50mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      66
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            4.04
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            4.04
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
```

---

### Post by DuckHook on 2016-05-15
skanger, even for you, surely there is a point of diminishing return.

I don't know if you've gone through your logs, but your output above confirms your observation that your machine *should* work with Xenial. Moreover, since it runs a LiveDVD, you know that it actually does. So here are my suggestions:

[LIST=1]
[*]You may have more luck with Lubuntu or Xubuntu 16.04. At least try installing them to see if they work. You may even like them enough to keep one of them instead of Ubuntu.
[*]Since it does install Trusty (14.04) and has run it in the past, do that install instead. Then, network upgrade from LTS to LTS. However, before doing so, install ssh-server so you can ssh into a black screen if such should occur. This is a way of working around your balky 16.04 install by leveraging an old 14.04 install first.
[*]A variation of the above strategy is to install Ubuntu Server 16.04 (with ssh). This only installs a command line environment which should be simpler and cleaner. Then, should it install without problem, pull in Ubuntu desktop by simply doing:```
sudo apt install ubuntu-desktop
```
[*]Install Lubuntu or Xubuntu 14.04. Frankly, your equipment calls for such lighter installs anyway, and you will have far better responsiveness with these than you did with Ubuntu 14.04. My old laptops that I use for travel purposes (just like you intend for this laptop) all have Xubuntu/Lubuntu; not Ubuntu.
[/LIST]
A final note: I usually unsubscribe from threads that haven't seen OP responses in three days. If you will be taking some days to respond, I may no longer by looking at this thread, in which case, I trust that others will jump in to help.

Good luck and, hopefully, Happy Ubuntuing!

---

### Post by skanger on 2016-05-15
> **DuckHook said:**
> skanger, even for you, surely there is a point of diminishing return.

I don't know if you've gone through your logs, but your output above confirms your observation that your machine *should* work with Xenial. Moreover, since it runs a LiveDVD, you know that it actually does. So here are my suggestions:

[LIST=1]
[*]You may have more luck with Lubuntu or Xubuntu 16.04. At least try installing them to see if they work. You may even like them enough to keep one of them instead of Ubuntu. 
[*]Since it does install Trusty (14.04) and has run it in the past, do that install instead. Then, network upgrade from LTS to LTS. However, before doing so, install ssh-server so you can ssh into a black screen if such should occur. This is a way of working around your balky 16.04 install by leveraging an old 14.04 install first. 
[*]A variation of the above strategy is to install Ubuntu Server 16.04 (with ssh). This only installs a command line environment which should be simpler and cleaner. Then, should it install without problem, pull in Ubuntu desktop by simply doing:```
sudo apt install ubuntu-desktop
``` 
[*]Install Lubuntu or Xubuntu 14.04. Frankly, your equipment calls for such lighter installs anyway, and you will have far better responsiveness with these than you did with Ubuntu 14.04. My old laptops that I use for travel purposes (just like you intend for this laptop) all have Xubuntu/Lubuntu; not Ubuntu. 
[/LIST]
A final note: I usually unsubscribe from threads that haven't seen OP responses in three days. If you will be taking some days to respond, I may no longer by looking at this thread, in which case, I trust that others will jump in to help.

Good luck and, hopefully, Happy Ubuntuing!

Thank you for your suggestions. The delay getting back to you couldn't be helped but I will try to respond in a more timely manner. About diminishing returns, its long past that point and has now entered a new phase: the point of unknown returns. With so much time and effort expended, something unknown and unexpected is bound to happen. 

About the logs, I hoped to put the msata SSD (in PATA adapter) in a PATA to USB/firewire carrier on this 16.04 machine to edit and post them here, but the carrier isn't seeing the SSD. I'll have to do that in WIndows instead.

I tried to install using the following boot parameter:

> Some very old laptop models produced by Dell are known to crash when  PCMCIA device detection tries to access some hardware addresses. Other  laptops may display similar problems. If you experience such a problem  and you don't need PCMCIA support during the installation, you can  disable PCMCIA using the **hw-detect/start_pcmcia=false** boot  parameter. You can then configure PCMCIA after the installation is  completed and exclude the resource range causing the problems.

The install ran as usual, right into hardware detection where it froze. I'm not sure if I inserted the boot parameter correctly. While booting from DVD, I pressed enter, selected English and the DVD menu appeared as usual. Selecting F6 brought up the list of boot modifiers. What I did was insert the above boot parameter for disabling PCMCIA after the boot parameters already present. There were three hyphens --- following the default boot parameters. I left them in place and typed in the PCMCIA disabling parameter. Pressing enter to begin the installation, I waited to see if any mention was made of PCMCIA being disabled but did not see any lines mentioning that. Therefore I wonder if I didn't do the insert according to proper syntax.

---

### Post by Skaperen on 2016-06-24
> **sammiev said:**
> Hi,

With the ATI Radeon Xpress Zoom graphics you may need to run with 14.04 Lubuntu or Xubuntu. Not sure if the graphics card will work with 16.04 Lubuntu, Xubuntu or Ubuntu-Mate.

You can always try to run from a live USB/DVD

if the live USB/DVD works, then there is some driver combination/configuration that can do it.  we want to get an installed system there.

---

