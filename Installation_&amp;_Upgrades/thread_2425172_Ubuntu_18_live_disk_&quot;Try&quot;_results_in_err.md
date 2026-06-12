---
title: "Ubuntu 18 live disk &quot;Try&quot; results in errors"
date: 2019-08-21
forum: Installation &amp; Upgrades
---

### Post by alfonso5 on 2019-08-21
I have a new computer and wanted to install Ubuntu. I put it on a flash drive:
1/ flash drive works OK on my old computer - nothing wrong there.
2/ New computer - it gets to "Try Ubuntu" "Install"
3/ If I select "Try" I get error messages continuously scrolling down the screen too quickly to read.
4/ I tried a couple of other Ubuntu derived operating systems which I had to hand - same result.
5 Tried Manjaro that worked both on "try without installing" and it installed - apparently nothing wrong with the computer.

Obviously it would help if I knew what the error message(s) say(s) but I don't know a way of stopping it scrolling. 

Help would be appreciated

---

### Post by TheFu on 2019-08-21
Does any other TTY work? 
Change to different TTYs using <cntl><alt>-F1,  <cntl><alt>-F2,  <cntl><alt>-F3, .... get back to the default using  <cntl><alt>-F7

---

### Post by alfonso5 on 2019-08-21
Don't understand the answer. What is TTY? 
at what point in the sequence would I use the key combinations you mention?

---

### Post by oldfred on 2019-08-21
Teleprinter, also called a teletypewriter (*TTY*) back in history when Unix was created, long before Linux emulated most of Unix. Now just the terminal mode.

What brand/model system?
What video card chip?

Old computer probably was BIOS, but new computer is UEFI and you need to be sure to boot in UEFI mode.
        Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by crip720 on 2019-08-21
Ubuntu seems to not like your computer as is.  If you can give make/model and cpu/gpu, hopefully someone here might know the fix.

---

### Post by alfonso5 on 2019-08-21
The computer is custom built by a company called CCL who sell computers without windows installed for £100 less than the same thing with Windows 10. At the moment I have Manjaro loaded and got this information from the teminal cammand: I don't know if that tells you anything. 
```
$ inxi -Fxxxza
System:
  Host: john-ccl Kernel: 4.19.66-1-MANJARO x86_64 bits: 64 compiler: gcc 
  v: 9.1.0 
  parameters: BOOT_IMAGE=/boot/vmlinuz-4.19-x86_64 
  root=UUID=67930aa8-3bf0-4dee-9d80-09de0ba2d45d rw quiet 
  Desktop: Gnome 3.32.2 wm: gnome-shell dm: GDM 3.32.0 Distro: Manjaro Linux 
Machine:
  Type: Desktop Mobo: Gigabyte model: B360M H v: x.x serial: <filter> 
  UEFI [Legacy]: American Megatrends v: F12 date: 03/14/2019 
CPU:
  Topology: Dual Core model: Intel Pentium Gold G5400 bits: 64 type: MT MCP 
  arch: Kaby Lake family: 6 model-id: 9E (158) stepping: A (10) 
  microcode: B4 L2 cache: 4096 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 29576 
  Speed: 3700 MHz min/max: 800/3700 MHz Core speeds (MHz): 1: 3700 2: 3700 
  3: 3700 4: 3700 
  Vulnerabilities: Type: l1tf 
  mitigation: PTE Inversion; VMX: conditional cache flushes, SMT vulnerable 
  Type: mds mitigation: Clear CPU buffers; SMT vulnerable 
  Type: meltdown mitigation: PTI 
  Type: spec_store_bypass 
  mitigation: Speculative Store Bypass disabled via prctl and seccomp 
  Type: spectre_v1 
  mitigation: usercopy/swapgs barriers and __user pointer sanitization 
  Type: spectre_v2 mitigation: Full generic retpoline, IBPB: conditional, 
  IBRS_FW, STIBP: conditional, RSB filling 
Graphics:
  Device-1: Intel vendor: Gigabyte driver: i915 v: kernel bus ID: 00:02.0 
  chip ID: 8086:3e90 
  Display: x11 server: X.org 1.20.5 driver: intel unloaded: modesetting 
  alternate: fbdev,vesa compositor: gnome-shell 
  resolution: <xdpyinfo missing> 
  OpenGL: renderer: Mesa DRI Intel UHD Graphics 610 (Coffeelake 2x6 GT1) 
  v: 4.5 Mesa 19.1.4 compat-v: 3.0 direct render: Yes 
Audio:
  Device-1: Intel Cannon Lake PCH cAVS vendor: Gigabyte 
  driver: snd_hda_intel v: kernel bus ID: 00:1f.3 chip ID: 8086:a348 
  Sound Server: ALSA v: k4.19.66-1-MANJARO 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Gigabyte driver: r8168 v: 8.047.02-NAPI port: 4000 bus ID: 01:00.0 
  chip ID: 10ec:8168 
  IF: enp1s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
  Device-2: Realtek RTL8192EE PCIe Wireless Network Adapter 
  driver: rtl8192ee v: kernel port: 3000 bus ID: 02:00.0 chip ID: 10ec:818b 
  IF: wlp2s0 state: up mac: <filter> 
Drives:
  Local Storage: total: 1.35 TiB used: 27.57 GiB (2.0%) 
  ID-1: /dev/sda vendor: Gigabyte model: GP-GSTFS31480GNTD size: 447.13 GiB 
  block size: physical: 512 B logical: 512 B speed: 6.0 Gb/s 
  serial: <filter> rev: 61.3 scheme: MBR 
  ID-2: /dev/sdb vendor: Seagate model: ST1000DM010-2EP102 size: 931.51 GiB 
  block size: physical: 4096 B logical: 512 B speed: 6.0 Gb/s 
  rotation: 7200 rpm serial: <filter> rev: CC43 scheme: GPT 
Partition:
  ID-1: / raw size: 447.13 GiB size: 439.11 GiB (98.21%) 
  used: 27.57 GiB (6.3%) fs: ext4 dev: /dev/sda1 
Sensors:
  System Temperatures: cpu: 42.0 C mobo: 27.8 C 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 198 Uptime: 1h 14m Memory: 3.72 GiB used: 1.21 GiB (32.6%) 
  Init: systemd v: 242 Compilers: gcc: N/A Shell: bash v: 5.0.7 
  running in: gnome-terminal inxi: 3.0.35
```

---

### Post by oldfred on 2019-08-21
It shows you have f12 UEFI, and an update to f15 is available. I would update that first.
[https://www.gigabyte.com/us/Motherboard/B360M-DS3H-rev-10/support#support-dl-bios](https://www.gigabyte.com/us/Motherboard/B360M-DS3H-rev-10/support#support-dl-bios)

You may need some settings in UEFI. Note that UEFI update, may restore defaults.
Turn off UEFI secure boot, may be called "Windows" or "Other" where "Other" is for Windows 7 as it does not support UEFI Secure Boot.
Drives need to be AHCI, not Intel SRT nor RAID.
You should have UEFI fast start up off, at least until system fully configured.
You may have to turn on allow USB boot, but if able to boot Manjaro then that may already be allowed.
Some Gigabyte boards need grub boot parameters, but most of those are AMD chip based, not Intel.

---

### Post by alfonso5 on 2019-08-22
I have photographed the screen with the errors and while I can't read the start of the line it says
.................. PCIe Bus Error : severity = Corrected, type physical layer, id=00e7(Receiver ID)
With the occasional line
.................. ^^device [8086:a33f],,error status/mask=00000001/00002000 
I found this on line
[https://askubuntu.com/questions/771899/pcie-bus-error-severity-corrected](https://askubuntu.com/questions/771899/pcie-bus-error-severity-corrected)
which seems to be a similar problem but I don't see how I can make the changes to Grub suggested when booting from a "live disk" (flash memory) when I can't get past "Try Ubuntu".
Suggestions would be welcome.

---

### Post by CatKiller on 2019-08-22
> **alfonso5 said:**
> I don't see how I can make the changes to Grub suggested when booting from a "live disk" (flash memory) when I can't get past "Try Ubuntu".
Pressing E at the Try Ubuntu screen will let you edit the startup options.

---

### Post by oldfred on 2019-08-22
My PCI errors go by so fast I cannot see them, but they are there. 
I have not had any issues because of PCI issues.

---

### Post by alfonso5 on 2019-08-25
> **oldfred said:**
> It shows you have f12 UEFI, and an update to f15 is available. I would update that first.
[https://www.gigabyte.com/us/Motherboard/B360M-DS3H-rev-10/support#support-dl-bios](https://www.gigabyte.com/us/Motherboard/B360M-DS3H-rev-10/support#support-dl-bios)

You may need some settings in UEFI. Note that UEFI update, may restore defaults.
Turn off UEFI secure boot, may be called "Windows" or "Other" where "Other" is for Windows 7 as it does not support UEFI Secure Boot.
Drives need to be AHCI, not Intel SRT nor RAID.
You should have UEFI fast start up off, at least until system fully configured.
You may have to turn on allow USB boot, but if able to boot Manjaro then that may already be allowed.
Some Gigabyte boards need grub boot parameters, but most of those are AMD chip based, not Intel.

I'm sure that is excellent advice and I intend to follow it up but having photoed the screen and read the error message PCLe Bus error and found a suggested means of overcoming the problem in askubuntu I was already pursuing that route. The suggestion was to add pci=nomsi to the command text on the line with " quiet splash ..." or something similar. I did this and it booted OK. I Installed rebooted again having adding pci=nomsi and got to the newly installed Ubuntu. There I edited grub adding the fix and ran update-grub. I ended up with a stable Ubuntu 18. When I tried to install programs I got a message "incorrect permissions" which I googled and found an instruction to run something or other which cured that. I now have a working Operating system.  Only one snag my computer has an SSD and a conventional HDD and I wanted the operating system on the SSD. The install did not give me that option so it has ended up on the HDD. Duel boot doesn't work so I cannot access Manjaro from the boot menu - I can if I select Boot the SSD.  I am going to have to leave it for a week - other commitments - and start again. I will look into the above advice. Physically disconnect the HDD reformat the SSD and start again. 

I am a retired electronics design engineer - latterly designing and programming micro-controller based systems.  I have been using Ubuntu for 10 years now and I have seen a lot of new releases most of which seemed to be change for the sake of change and in some cases not for the better. Essentially whoever is running the show has taken his eye off the ball. No 1 priority is to provide something people can try and install without hassle. **Without that no one is going to**. This would be one heck of a waste of an awful lot of people's effort. If you take the PCLe bus error fix I found - that was posted 3 years ago. The idea that some thing can get stuck in a loop churning out error messages which you can't read is pretty basic. If an error occurs the program should either stop and produce an error message or try a fixed number of times and produce an error message. As it implies that the error is predictable there is no reason why the error message couldn't suggest a solution or provide a link to somewhere where a newbe could be talked through it. !0 years ago I wouldn't have hesitated in recommending Ubuntu. At the moment I wouldn't recommend ubuntu to anyone.

---

### Post by oldfred on 2019-08-25
Grub will offer to boot other systems, but only if installed in same boot mode. Or all systems must be UEFI or all must be BIOS.
This updates menu, but install should add it. A few systems with LVM or other special types have to be first mounted so the grub update can find the system. And if LVM, you may need to add LVM drivers, first to be able to mount it.

sudo update-grub

You can look at your log files for errors or warnings. Files are long as they post all the details.
/var/log. Some need log file viewer to see them others are just text.

If you use the Something Else install option, you get choices. You can create partitions, reuse partitions, change drives and various other options.
       [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)  
            [https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

---

### Post by gin-cognac on 2019-08-26
OK Thank you for your help. 
The "try something else" only listed the HDD. I solved the problem by partitioned the SSD first and trying again and have now got a stable install where I want it.
Idiots guide to the fix 
1/ At boot menu highlight "Try Ubuntu" - press [e] to edit
2/ add pci=nomsi to the command text on the line with " quiet splash ..."  
3/ F10 to boot. - if the problem is the same as mine it will boot OK. Try a few things to see if its working and select install
4/ When install is complete reboot.
5/ again add pci=nomsi to the command text on the line with " quiet splash ..." 
6/ It should boot to the installed OS
7/ In the terminal type "cd /etc/default" [enter]
   type  "sudo gedit grub"  type in your password and press [enter]. 
add pci=nomsi to the line "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=nomsi" save and close.
then "sudo update-grub"
Next time you log in it should work

Now I am trying to find how to mark it as "solved".  Thread tools gives me 3 options "Show printable Option" "email this page" "subscribe to this thread"

---

