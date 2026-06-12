---
title: "grub2 load ubuntu fails"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Astenorh on 2009-10-04
In Karmic I am unable to boot to ubuntu unless, I edit myself the entry (while having grub2 loaded) and remove these lines :

```
recordfail=1
save_env recordfail
```

Does anybody have this problem as well?
And which file to edit to configure GRUB 2 by hand.

Here is /proc/cpuinfo :

```
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 104
model name	: AMD Turion(tm) 64 X2 Mobile Technology TL-62
stepping	: 2
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 1600.25
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 104
model name	: AMD Turion(tm) 64 X2 Mobile Technology TL-62
stepping	: 2
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 1600.25
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

```

lspci :

```
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:04.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:04.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
02:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 9300M G] (rev a1)
05:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```

Here is the kernel version : 2.6.31-10-generic

It fails to load any kernel (because of those lines)
Ubuntu works fine if I edit grub.

---

### Post by dino99 on 2009-10-04
hi,

i never had this problem, but have already read on that forum the same issue many times.
You can edit /etc/default/grub

actual kernel is 31-11, so update it & the others packages

you said editing grub, that's not a good idea. (I suppose you're talking about grub.conf)

If you have dist-upgrade a Jaunty system, you need to install os-prober & grub-pc.

anyway, do the following:

 - sudo aptitude clean
 - sudo aptitude autoclean
 - sudo apt-get autoremove
 - sudo aptitude install -f
 - sudo aptitude update
 - sudo aptitude safe-upgrade

Then, sudo os-prober
      sudo update-grub2
      sudo grub-mkconfig

Good evening.

---

### Post by ajgreeny on 2009-10-04
Grub 2 is very different, and editing the configuration is also different, so have a look at the info here:-
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by drs305 on 2009-10-04
I wrote the guide referenced in the previous post. It's a good idea to become familiar with the Grub 2 files.

I too have seen the problems related to the "recordfail=1 save_env recordfail" difficulties. I don't address this specifically in the guide but I will find out which script places those lines into grub.cfg and report back if nodoby else responds sooner.

---

### Post by drs305 on 2009-10-04
Well, that didn't take too long.

It appears those entries are entered by the script /etc/grub.d/10_linux.
Open the file with admin rights:
```
gksu gedit /etc/grub.d/10_linux
```
Look for this section and comment the lines in **bold**; 
> 
linux_entry ()
{
  cat << EOF
menuentry "$1" {
[B]        recordfail=1
        save_env recordfail[/B]

Change it to:
> linux_entry ()
{
  cat << EOF
menuentry "$1" {
[B]#        recordfail=1
#        save_env recordfail[/B]

Save the file, then run
```
sudo update-grub
```

The two lines should no longer appear when you press E to view the selection in the Grub 2 menu. You will see a "save_env save_entry" line but this should not cause the failure if you successfully booted the previous time.

---

