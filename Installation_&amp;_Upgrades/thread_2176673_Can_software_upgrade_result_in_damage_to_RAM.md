---
title: "Can software upgrade result in damage to RAM?"
date: 2013-09-25
forum: Installation &amp; Upgrades
---

### Post by kinshuk2 on 2013-09-25
Weird but thats what i have witnessed..
Yesterday i upgraded ubuntu 12.04 to 12.10 and the upgrade seemed to have gone well and asked me to reboot it.
Once i rebooted it said unable to mount /tmp and just hung there. 
Then i reset the system and it wont boot up after passing bios. I did not even see grub screen :(

Finally, i took a bootable usb having ubuntu 12.04 to restore back the the working release and while installing it saw kernel panic.. 

Then i ran memory test available in the live bootable usb and was shovked to see so many memory errors. More than 5000 errors reported within a couple of minutes.

Can software upgrades result in damage memory? :(


System basic detail:
RAM 1024 DDR2
HDD 250GB
Intel GMA 3100 Graphics

----- /proc/cpuinfo -----
 processor    : 0
 vendor_id    : GenuineIntel
 cpu family    : 6
 model        : 15
 model name    : Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz
 stepping    : 13
 microcode    : 0xa3
 cpu MHz        : 1200.000
 cache size    : 1024 KB
 physical id    : 0
 siblings    : 2
 core id        : 0
 cpu cores    : 2
 apicid        : 0
 initial apicid    : 0
 fdiv_bug    : no
 hlt_bug        : no
 f00f_bug    : no
 coma_bug    : no
 fpu        : yes
 fpu_exception    : yes
 cpuid level    : 10
 wp        : yes
 flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm
 bogomips    : 4389.71
 clflush size    : 64
 cache_alignment    : 64
 address sizes    : 36 bits physical, 48 bits virtual
 power management:

 processor    : 1
 vendor_id    : GenuineIntel
 cpu family    : 6
 model        : 15
 model name    : Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz
 stepping    : 13
 microcode    : 0xa3
 cpu MHz        : 2200.000
 cache size    : 1024 KB
 physical id    : 0
 siblings    : 2
 core id        : 1
 cpu cores    : 2
 apicid        : 1
 initial apicid    : 1
 fdiv_bug    : no
 hlt_bug        : no
 f00f_bug    : no
 coma_bug    : no
 fpu        : yes
 fpu_exception    : yes
 cpuid level    : 10
 wp        : yes
 flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm
 bogomips    : 4389.71
 clflush size    : 64
 cache_alignment    : 64
 address sizes    : 36 bits physical, 48 bits virtual
 power management:

----- /proc/cpuinfo end -----

Why did i bother upgrading from LTS release to an unsupported release ?

Well check this out
[https://answers.launchpad.net/ubuntu/+question/234595](https://answers.launchpad.net/ubuntu/+question/234595)

I was not happy with stability of 12.04 nd decided to try latest releases ..

---

### Post by tgalati4 on 2013-09-25
Unfortunately, there is a bug in 12.04's memtest (in test 7 I believe).  Your booting problems are probably related to changes in 12.10.  Once you start adding updates, memtest will get fixed.  If the errors are at 129MB in test #7, don't worry about it.

---

### Post by kinshuk2 on 2013-09-25
[**[COLOR=#000000]tgalati4[/COLOR]**]("http://ubuntuforums.org/member.php?u=241895"),

Thanks for replying back :)
the error values looked too high to be real and i would be the happiest person if it turns out to be a memtest bug.
However, i have run the memtest86+ on 12.04 ubuntu for more than 7 hours in past and did not see a single error reported!
I wonder if the bug is intermmittent in nature ?

I will try installing 12.10 or a fresh 13.04 ubuntu tomorrow and update the thread.

Thanks again.

---

### Post by tgalati4 on 2013-09-25
Try reseating your RAM.  Use an eraser to gently clean the tabs on the RAM sticks.  Ground yourself to avoid electrostatic discharge.  I encountered the memtest bug in 12.10.  It has since been updated: (in /boot)

-rw-r--r--  1 root root   176764 Jan  3  2013 memtest86+.bin

tgalati4@Mint14-Extensa /boot $ apt-cache policy memtest86+
memtest86+:
  Installed: 4.20-1.1ubuntu2.1
  Candidate: 4.20-1.1ubuntu2.1
  Version table:
 *** 4.20-1.1ubuntu2.1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     4.20-1.1ubuntu2 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages

---

