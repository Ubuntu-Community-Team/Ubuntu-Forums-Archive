---
title: "I want to Install Ubuntu Server 21.10 as dual boot system of"
date: 2022-01-30
forum: Installation &amp; Upgrades
---

### Post by lsepolis123 on 2022-01-30
[FONT=Calibri]I want to **Install **UbuntuServer 21.10 as dual boot system of 

[/FONT]
[COLOR=black][FONT=HPSimplifiedLight]**Product: **HP Pavilion Elite M9372.GrDesktop PC 2008-2009[/FONT][/COLOR]
[COLOR=black][FONT=HPSimplifiedLight]**Operating System: **Microsoft Windows 10(64-Bit) Home[/FONT][/COLOR]
[FONT=Calibri]PC is Intel Core 2Quad / RAM 8GB DDR2  [/FONT]
[FONT=Calibri]**can I without problems...?**

**Can I easily** >>upgrade-to>> Ubuntu Server 22.04 LTS # April 2022, **via CMD line when time comes???**

I will use it **as ****Always ON as LocalLAN File/Media Server,** is any limit required for staying always ON... eg Operate max of 3-days always ON...??
Alternatively, 
What about **using **[/FONT]
[FONT=Calibri]**Wake-On-LAN**, with an ETHERNET **USB-2-Ethernet** **adapter **for connecting to this desktop PC...? Ubuntu Server 22.04 LTS supports **Wake-On-LAN **or this is hardware only compatibility???[/FONT]

---

### Post by MAFoElffen on 2022-01-31
On WOL: [https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan)

On installing 21.10 as a server... 21.10 is an interim build support wise. LTS version are support better for security updates and stability. In Server Editions, that is usually what you want and depend on. 'Stabilty." Whether you install 21.10 or 20.04.3 LTS, come late April, you can update to 22.04. Even if you do decide to install Server 21.10, wiht the intention of updating to 22.04 LTS come April, on that release Upgrade, I would change the APT option to upgrade on LTS, instead of interim test versions. 

On dual-boot server intended to be as a dual-boot with Windows... ??? Why??? Those two functions sort of conflict with what you have said you want. Just saying that the logic of what you said is not there.

If 24x7x365 uptime for Server Sercies then what instances do you see yourself bring it down, for use as Windows 10? To make the Ubuntu Server Services available when you use Windows 10, you know that if you ran Ubuntu Server as a VM on Hyper-V, with boot VM on boot, you know you would have what you said you want as a goal, right? Just going off what you said you want...

Even for setting up a Hyper-V guest as WOL, if you have more than 2 NIC's that support WOL. Because Hyper-V is going to need the NIC with WOL capabilities, physically passed through to the specific VM that is going to use that...

---

### Post by TheFu on 2022-01-31
+1 on not installing a non-LTS release.  Start with 20.04 then wait until late-June, early July, at the earliest to upgrade/install 22.04.  Give it a few months to settle and for some early issues to be resolved.

I wouldn't deal with the complexities of a dual-boot setup especially if the system is going to be always on as a media server.
There aren't any arbitrary time limits for being powered on with Linux systems that I'm aware.
```
$ uptime
 20:19:08 up 9 days
```
is my media server (Plex, Jellyfin, MPD and some custom music tools), NFS, calibre and TV recording box. It also runs a Nextcloud virtual machine.  
```
$ virsh list
 Id    Name                           State
----------------------------------------------------
 1     nextcloud                      running
```

9 days ago, I happened to patch and the patching needed a reboot due to a new kernel, so I rebooted it. It is always on. It doesn't sleep or WoL.  Always on and I prevent the HDDs from spinning down too. Lots of processing happens overnight on that box. I never know when it will be recording some TV show. I tend to get PBS shows after midnight to avoid having too many concurrent recordings during prime time. 

Also, it 'pulls' backups for a few systems overnight here. It isn't my main backup server, but I'm moving more and more over to a dedicated disk inside it for some not-so-simple reasons.  I really need to move it from 18.04 to 20.04, but because it is needed to keep the "one who shall be obeyed" happy, I need to schedule it being down MONTHS in advance if I want to wake up ... ever. ;)  Mujer feliz, vida feliz.

---

### Post by lsepolis123 on 2022-02-01
This is very old PC(BIOS Firmware), 2008-2009, after dual boot Windows 10 Home + Linux Server 21.10/22.04, can I set the default boot OS…?

WOL
May Not supported…? If in this PC wake on LAN - request wake up eg from my laptop - should boot the default OS, if dual boot system, correct?

Because this PC is very old, and Windows 10 Home, I think Hyper-V Not supported, but ONLY VirtualBox is supported as of running VMs…

With this in mind,
Can you reply with less words, what you wanted to say…?

---

### Post by TheFu on 2022-02-01
Yes, you can have grub boot whatever OS you prefer as the default.

Win10 wasn't released in 2010.  Do you mean Win7?  I'm always amazed when people read MSFT EULA and agree with the updates/changes forced in Win10.  I didn't accept it, don't have Win10 for that reason. It was some nasty legal terms, IMHO. Completely 1-sided. Anti-consumer. Anti-privacy.

All Core2 Duo systems are 64-bit and the CPUs support VT-x - which is the hardware support needed for running any of the modern virtualization hardware.  However, sometimes "bad" companies like HP and Acer removed from the BIOS the ability to enable VT-x support even when everything else in the system supported it. I've seen this on laptops from both those companies. In fact, some Celeron CPUs have VT-x too.  The first Chromebook I owned did while Intel was trying to figure out what to charge for fast, cheap, CPUs across their line of CPUs. Also had a $50 Pentium from 2015-ish which was faster than all the Core2Duos, supports VT-x and happily ran 3 virtual machines for a very long time here. These days, I can't give that Pentium away because a used system for $75 is much faster and more capable.

I ran multiple Core2 Duo computers with VT-x and has 20 VMs running one at least one of them for years.  I was using Xen initially, then moved to KVM/QEMU.  Worked great for the time, though faster CPUs with lower power needs is always better.  I had an E6600 C2D eating 125W for years here.  Added an E8400, then an X8600 ... all C2D systems, before I started moving in Core i5/i7 boxes. They made a bunch of heat, so I started getting newer CPUs which used 50% less power. The savings in my power bill usually paid for the cooler, faster, newer, CPUs in about 2 yrs.  I have 1 CPU left using 125W - all the others are 65W or less and over 5x faster.  

Just something to consider.

---

### Post by MAFoElffen on 2022-02-01
Since "Windows 10 Home", I am assuming it's at least 64bit... How much memory and what CPU?

Because there is another way also... You could do Ubuntu Server, Primary, running 24x7, with KVM, with on-demand minimal Desktop...With your Windows 10 Home migrated to KVM VM Guest.. That way your Server Services are not interrupted by your intermittent use of that.

Just another option..

But what you describe, is not what you said. If the PC is down, powered off, and woke up by WOL... That is not 24x7x365 service. Just saying. (Are you trying to save money on your electrical bill from that?)

---

### Post by MAFoElffen on 2022-02-01
If you 'Try' an lightweight Ubuntu Flavor... and have your Windows as a VM Guest of that host, it's still there. You could always keep a backup to revert back.

Who knows. You might find that you use that VM less and less as you familiarize yourself with Linux Desktops... and later find that you might not use that VM enough to keep it going. Microsoft is abandoning users of older hardware for any release upgrade path to Windows 11. This will be a personal consideration to you eventually.

---

### Post by lsepolis123 on 2022-02-01
2008-2009
I mean year purchased and probably manufactured 

Because this PC is very old, and Windows 10 Home 64-bit, I think Hyper-V Not supported, but ONLY VirtualBox is supported as of running VMs…

This is intel core 2 quad 64-bit, DDR2 8GB RAM, HDD Windows 10 Home 64-bit

BIOS And Not UEFI 
MBR and Not GPT

Default boot OS can be configured...? If yes, this depends on OS installed lastly...?

---

### Post by SeijiSensei on 2022-02-02
I'd just install the advance version of 22.04. Server distros are quite stable. 

[http://cdimage.ubuntu.com/ubuntu-server/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-server/daily-live/current/)

---

### Post by oldfred on 2022-02-02
You can use gpt with old BIOS. Its just you need a bios_grub partition of 1 or 2MB unformatted with bios_grub flag.
I started converting to gpt back in 2010 with old BIOS system. Now all drives are gpt and only one retired laptop is BIOS, but also gpt.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR](https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

If you convert from MBR to gpt it will totally erase drive, so have good backups.
And if you want to keep Windows, you have to stay with MBR as Windows only boots from gpt with UEFI.

---

### Post by TheFu on 2022-02-02
> **lsepolis123 said:**
>  
Because this PC is very old, and Windows 10 Home 64-bit, I think Hyper-V Not supported, but ONLY VirtualBox is supported as of running VMs…

This is intel core 2 quad 64-bit, DDR2 8GB RAM, HDD Windows 10 Home 64-bit

BIOS And Not UEFI 
MBR and Not GPT

Default boot OS can be configured...? If yes, this depends on OS installed lastly...?

Windows has to be installed first, if you insist on dual boot. I think dual boot is an abomination. Use virtual machines. Your CPU and RAM will easily support multiple VMs. Easily.  Linux-based VMs can boot with either UEFI or legacy BIOS emulated. I'd bet that whatever hypervisor Win10 provides (or vbox or VMware $$$ Workstation) can as well. I haven't kept up with Windows hypervisors since about 2011 when I stopped putting Windows on physical systems.

Linux doesn't have artificial limits on using GPT only with UEFI.  32-bit, 64-bit, BIOS/UEFI, MBR/GPT ... doesn't matter. Any combination should work fine. I've BIOS booted an AMD E-350 APU from a GPT 4TB drive long, long, ago with no problems.  
MSFT added arbitrary limitations to force new hardware, EFI deployment, secure boot, and a few other things that were issues for Windows, but not Linux.  EFI booting is recommended by the Linux Foundation, as is using Secure Boot, for the most secure Linux system.  Read more here: [https://www.linuxfoundation.org/blog/how-lf-communities-enable-security-measures-required-by-the-us-executive-order-on-cybersecurity/](https://www.linuxfoundation.org/blog/how-lf-communities-enable-security-measures-required-by-the-us-executive-order-on-cybersecurity/)  But by dual booting, all the systems on that hardware are just a little less secure because the entire device cannot be encrypted.
I'm bad and don't use UEFI or Secure Boot on my systems, except for 1 laptop. Many of my systems don't have GPT boot devices, but if they have more than 1 storage device connected and that device was added since around 2012, then it has a GPT partition table. This is regardless of size.  32GB or 8TB ... they are GPT.  That 4TB HDD from the E-350 has been moved forward to 2 newer systems and 3 replacement HDDs, but I've never changed the partition table to GPT over all these years. The OS has been upgrades, not installed fresh all these times.

Core2 Quad supports VT-x, period. [https://ark.intel.com/content/www/us/en/ark/products/40480/intel-core2-quad-processor-q9000-6m-cache-2-00-ghz-1066-mhz-fsb.html](https://ark.intel.com/content/www/us/en/ark/products/40480/intel-core2-quad-processor-q9000-6m-cache-2-00-ghz-1066-mhz-fsb.html) All Intel Core2 CPUs support VT-x.  It is more than sufficient to run multiple virtual machines with hardware acceleration. The hostOS can be Windows OR Linux. Generally, people choose the OS where they want the best GPU performance as the hostOS.  Then there are people like me who always choose Linux. Always.  That completely removes hardware compatibility issues from Windows - so my really old printers and scanners which haven't been supported by Windows since before Vista can still be used.

Think I've posted most of this earlier in this thread.  Everything the other posters here are saying is all true too. This is the superstar team trying to help.

---

### Post by lsepolis123 on 2022-02-03
Can you reply this: Can practice in a UEFI/GPT hp Z440 Workstation system, but inside VM in Vmware Workstation pro 15.x setup And the VM be as BIOS/MBR OS...? This because after Testing i will try in an old system BIOS/MBR this... process... can I make this testing...?

---

### Post by lsepolis123 on 2022-02-03
So, the answer is 
YES I, CAN TEST BIOS/MBR FROM UEFI/GPT Host:/VM:BIOS/MBR...
So review, Vmware docs or search Google or Vmware forums...correct?

---

### Post by MAFoElffen on 2022-02-04
Yes. For many VM Hosts, when you create the VM Guest, you can choose with BIOS firmware type you want to simulate.

---

