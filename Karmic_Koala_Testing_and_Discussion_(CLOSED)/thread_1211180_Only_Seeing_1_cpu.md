---
title: "Only Seeing 1 cpu"
date: 2009-07-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rtalcott on 2009-07-12
upgraded 9.04 ->  9.10 Alpha2 a couple days ago....sound/pulseaudio now works!  But, the machine seems slow and the System Monitor shows only 1 cpu of the Athlon64 X2....when I was running 9.04 the machine was faster and System Monitor showed 2 cpu's....

Is anyone seeing anything like this?  Any suggestions?

thank you,
rt

---

### Post by taavikko on 2009-07-12
For the cpu, does "cat /proc/cpuinfo" display all the processors?
Is this also happening on a new user aswell? (Create a new user and login to that new account)

---

### Post by rtalcott on 2009-07-12
I will create a new user now...Thank You for the reply!
rt

rtalcott@ubuntuAMD:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping	: 2
cpu MHz		: 1800.000
cache size	: 512 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow up rep_good extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 3600.04
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

rtalcott@ubuntuAMD:~$

---

### Post by rtalcott on 2009-07-12
Looks the same....suppose I should look a bit more carefully!
rt

rmtalcott@ubuntuAMD:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping	: 2
cpu MHz		: 1000.000
cache size	: 512 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow up rep_good extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 2000.02
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

---

### Post by wayne_cat on 2009-07-12
True ... you have only on CPU (one core) at the moment

---

### Post by rtalcott on 2009-07-12
EVERYTHING else is GREAT!  Unfortunately, the machine is clearly slower than I had expected...I have no clue as to the cause or how to fix it...wondering if anyone else has seen this.
rt

---

### Post by wayne_cat on 2009-07-12
could you please post the result of "uname -a":

This is from my Intel system ... the important part .... **SMP**

```
root@macbook:~# uname -a
Linux macbook 2.6.31-2-generic #17-Ubuntu SMP Fri Jul 10 21:48:31 UTC 2009 i686 GNU/Linux
root@macbook:~# 
```edit:

and the result of "dmesg |grep Processor"

```
root@macbook:~# dmesg |grep Processor
[    0.002994] CPU: Physical Processor ID: 0
[    0.002995] CPU: Processor Core ID: 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.542168] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.543402] ACPI: Processor [CPU1] (supports 8 throttling states)
root@macbook:~#
```

---

### Post by rtalcott on 2009-07-12
Here it is....I appreciate the help....I'll try to learn something along the way
rt

rtalcott@ubuntuAMD:~$ uname -a
Linux ubuntuAMD 2.6.31-2-generic #17-Ubuntu SMP Fri Jul 10 21:48:17 UTC 2009 x86_64 GNU/Linux

AND:

rtalcott@ubuntuAMD:~$ dmesg |grep Processor
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.409208] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.735511] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ processors (1 cpu cores) (version 2.20.00)

---

### Post by rtalcott on 2009-07-14
I have updated and am still only seeing 1 core of two.....

Does anyone have any advice?  I had two cores under 8.10 & 9.04...with 9.10 my audio and usb hardware finally works but the machine is slow without that second core....
thanx
rt

---

### Post by alphacrucis2 on 2009-07-14
> **rtalcott said:**
> I have updated and am still only seeing 1 core of two.....

Does anyone have any advice?  I had two cores under 8.10 & 9.04...with 9.10 my audio and usb hardware finally works but the machine is slow without that second core....
thanx
rt

Sounds like a kernel bug.

---

### Post by wayne_cat on 2009-07-14
[COLOR=Black]sorry ... i did not see your response to my question. I also think you should create a launchpad bug report. 
[/COLOR]

---

### Post by alphacrucis2 on 2009-07-14
> **wayne_cat said:**
> [COLOR=Black]sorry ... i did not see your response to my question. I also think you should create a launchpad bug report. 
[/COLOR]

Before opening a launchpad bug report, OP should make sure they install the rc3 kernel, which is now in the repos. I don't have and AMD cpu to test myself.

---

### Post by rtalcott on 2009-07-14
wayne_cat...no problem!  I edited the post and added the response so I don't think it shows up as a new post...could be wrong though..

updated today:

rtalcott@ubuntuAMD4:~$ uname -a
Linux ubuntuAMD4 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 x86_64 GNU/Linux
rtalcott@ubuntuAMD4:~$ 

I believe this is the latest release...

rt

WRONG MACHINE!  IGNORE!
rt

---

### Post by wayne_cat on 2009-07-14
Is this an Ubuntu Karmic system ... you are using kernel version  2.6.28-13 ... but the latest version for Karmic is 2.6.31-3.

---

### Post by rtalcott on 2009-07-14
Opps...I posted that (above) from a 9.04 machine...not this one...

rtalcott@ubuntuAMD:~$ uname -a
Linux ubuntuAMD 2.6.31-3-generic #19-Ubuntu SMP Tue Jul 14 16:07:02 UTC 2009 x86_64 GNU/Linux
rtalcott@ubuntuAMD:~$ 

Just received this set of upgrades...sorry about that mispost..was NOT thinking!
rt

---

### Post by caryb on 2009-07-14
This must be a AMD thing I just checked mine & got this...

cary@stinkpad:~$ cat /proc/cpuinfo 
processor       : 0                
vendor_id       : GenuineIntel     
cpu family      : 6                
model           : 15               
model name      : Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz
stepping        : 10                                             
cpu MHz         : 800.000                                        
cache size      : 4096 KB                                        
physical id     : 0                                              
siblings        : 2                                              
core id         : 0                                              
cpu cores       : 2                                              
apicid          : 0                                              
initial apicid  : 0                                              
fpu             : yes                                            
fpu_exception   : yes                                            
cpuid level     : 10                                             
wp              : yes                                            
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida tpr_shadow vnmi flexpriority              
bogomips        : 3989.95                                                                              
clflush size    : 64                                                                                   
cache_alignment : 64                                                                                   
address sizes   : 36 bits physical, 48 bits virtual                                                    
power management:                                                                                      

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6           
model           : 15          
model name      : Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz
stepping        : 10
cpu MHz         : 800.000
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
apicid          : 1
initial apicid  : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida tpr_shadow vnmi flexpriority
bogomips        : 3989.97
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:


Cary

---

### Post by rtalcott on 2009-07-14
Hard to believe that I am the only one seeing this which makes me think there is either a simple fix or I have done something to have caused this problem....I'd like to un-cause" it now!

rt

---

### Post by wayne_cat on 2009-07-14
Could you pleas post the result from this command:

 **dmesg |grep CPU**


here is the result from my Intel CoreDuo system

```
root@macbook:~# dmesg |grep CPU
[    0.000000]   Transmeta TransmetaCPU
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c202f000, static data 35004 bytes
[    0.000000] Initializing CPU#0
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.002979] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.002982] CPU: L2 cache: 2048K
[    0.002984] CPU: Physical Processor ID: 0
[    0.002986] CPU: Processor Core ID: 0
[    0.076658] CPU0: Genuine Intel(R) CPU           T2500  @ 2.00GHz stepping 08
[    0.004000] Initializing CPU#1
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.164499] CPU1: Genuine Intel(R) CPU           T2500  @ 2.00GHz stepping 08
[    0.164516] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.168024] Brought up 2 CPUs
[    0.168083] CPU0 attaching sched-domain:
[    0.168095] CPU1 attaching sched-domain:
[    0.500550] Switched to high resolution mode on CPU 1
[    0.504007] Switched to high resolution mode on CPU 0
[    0.542781] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.542840] processor LNXCPU:00: registered as cooling_device0
[    0.542844] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.544026] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.544087] processor LNXCPU:01: registered as cooling_device1
[    0.544092] ACPI: Processor [CPU1] (supports 8 throttling states)
root@macbook:~# 

```and this is maybe also intersting


**dpkg -l |grep linux-image |grep ii**


```
root@macbook:~# dpkg -l |grep linux-image |grep ii
ii  linux-image-2.6.30-9-generic                   2.6.30-9.10                                Linux kernel image for version 2.6.30 on x86
ii  linux-image-2.6.31-2-generic                   2.6.31-2.17                                Linux kernel image for version 2.6.31 on x86
ii  linux-image-2.6.31-3-generic                   2.6.31-3.18                                Linux kernel image for version 2.6.31 on x86
ii  linux-image-generic                            2.6.31.3.14                                Generic Linux kernel image
root@macbook:~#
```

---

### Post by rtalcott on 2009-07-14
This was an upgrade from 9.04 to Alpha2...the first line of
dpkg -l |grep linux-image |grep ii
look strange.

Here is what those commands gave me:
rt

rtalcott@ubuntuAMD:~$ uname -a
Linux ubuntuAMD 2.6.31-3-generic #19-Ubuntu SMP Tue Jul 14 16:07:02 UTC 2009 x86_64 GNU/Linux

rtalcott@ubuntuAMD:~$ dmesg |grep CPU
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages at ffff88002801f000, static data 89952 bytes
[    0.000000] Initializing CPU#0
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 0/0x0 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.018678] weird, boot CPU (#0) not listed by the BIOS.
[    0.020000] Brought up 1 CPUs
[    0.020000] CPU0 attaching NULL sched-domain.
[    0.409310] processor LNXCPU:00: registered as cooling_device0
[    0.409313] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.524102] Switched to high resolution mode on CPU 0

rtalcott@ubuntuAMD:~$ dpkg -l |grep linux-image |grep ii
ii  linux-image-2.6.28-11-generic              2.6.28-11.42                               Linux kernel image for version 2.6.28 on x86
ii  linux-image-2.6.31-2-generic               2.6.31-2.17                                Linux kernel image for version 2.6.31 on x86
ii  linux-image-2.6.31-3-generic               2.6.31-3.19                                Linux kernel image for version 2.6.31 on x86
ii  linux-image-generic                        2.6.31.3.14                                Generic Linux kernel image
rtalcott@ubuntuAMD:~$

---

### Post by Jimleko211 on 2009-07-14
Try doing a clean install, if possible.  Maybe something went funky in the upgrade?

---

### Post by rtalcott on 2009-07-14
I may do that tomorrow....clean install....been too lazy up to now!
rt

---

### Post by wayne_cat on 2009-07-14
Please wait with the new installation ... someone else with an AMD CPU will have a look at this thread ... Maybe the wrong kernel version

could you please show me the result from:

**ls /var/cache/apt/archives/ | grep linux-image-2.6.31**

---

### Post by rtalcott on 2009-07-14
I can definitely wait...that's not a problem at all....however I suspect this will end up either being "operator error" or maybe an upgrade gone bad.  I usually do clean installs but this time I thought I would take the easy path!
rt



rtalcott@ubuntuAMD:~$ ls /var/cache/apt/archives/ | grep linux-image-2.6.31
linux-image-2.6.31-2-generic_2.6.31-2.17_amd64.deb
linux-image-2.6.31-3-generic_2.6.31-3.18_amd64.deb
linux-image-2.6.31-3-generic_2.6.31-3.19_amd64.deb
rtalcott@ubuntuAMD:~$

---

### Post by rtalcott on 2009-07-14
This caught my eye too!  **weird boot**

[ 0.004000] CPU: Processor Core ID: 0
[ 0.018678] weird, boot CPU (#0) not listed by the BIOS.
[ 0.020000] Brought up 1 CPUs

rt

---

### Post by wayne_cat on 2009-07-14
It may be interesting for the lauchpad people .. let's see if other AMD users have the same problem.

Thank you for the results ... at least the right kernel seems to be installed.

---

### Post by caryb on 2009-07-14
Might be a strange question but you do have hyper-threading turned on in the BIOS?


Cary

---

### Post by rtalcott on 2009-07-14
wayne_cat,

I appreciate your help!  Regardless of what it is ( operator error, bad upgrade etc.) I'd like to know what the problem actually is....and I'm sure I'll learn a bit along the way!

Unemployed with too much time on my hands so  time isn't a problem!
rt

---

### Post by rtalcott on 2009-07-14
caryb,
I thought hyperthreading was an Intel only feature...which is turned on in the bios of my P4 machines...
rt

---

### Post by rtalcott on 2009-07-18
Downloaded the latest daily build and burned a copy...booted up the live-cd...motherboard is an ECS a740gm-m....still seeing only 1 core of two...I am starting to think either I have a motherboard problem (but I saw 2 cores with 8.10 and 9.04) or maybe some Alpha issue?

I think I'll go ahead and do a clean install but I don't think it will fix the problem....anyone else seeing anything like this?

thanx
rt

---

### Post by taavikko on 2009-07-18
> **wayne_cat said:**
> It may be interesting for the lauchpad people .. let's see if other AMD users have the same problem.


```
taavikko@hp-dv5:~$ sudo dmidecode -s processor-version
AMD Athlon(tm) X2 Dual-Core QL-62
```

and I have two CPU's in use

But for the sake of argument, I suspect that the issue might lie in the BIOS of mobo.
Or in the mobo in itself.

---

### Post by inportb on 2009-07-18
Right... perhaps a BIOS update might help?

---

### Post by DougieFresh4U on 2009-07-18
```
dougie@DougiesLeanMachine:~$ sudo dmidecode -s processor-version
AMD Athlon(tm) 64 X2 Dual Core Processor 5200+      


```
Also in System Monitor, showing both cores

---

### Post by rtalcott on 2009-07-18
I will check for a bios update.....just completed a clean install...same issue...seems strange (maybe not if someone would explain) that 8.10 and 9.04 did not have this problem...

rt

---

### Post by wayne_cat on 2009-07-18
Latest BIOS : 2009/07/14


[http://www.ecs.com.tw/ECSWebSite/Products/ProductsDetail.aspx?detailid=864&CategoryID=1&DetailName=Bios&MenuID=1&LanID=0](http://www.ecs.com.tw/ECSWebSite/Products/ProductsDetail.aspx?detailid=864&CategoryID=1&DetailName=Bios&MenuID=1&LanID=0)

---

### Post by rtalcott on 2009-07-18
wayne_cat...Thank You!

Right now I'm finishing up the clean install from the daily build...
rt

---

### Post by Stereotypical Rage on 2009-07-18
> **rtalcott said:**
> EVERYTHING else is GREAT!  Unfortunately, the machine is clearly slower than I had expected...I have no clue as to the cause or how to fix it...wondering if anyone else has seen this.
rt

What kernel are you using? 

'uname -a' from a terminal.

---

### Post by rtalcott on 2009-07-18
rtalcott@ubuntuAMD4:~$ uname -a
Linux ubuntuAMD4 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 x86_64 GNU/Linux
rtalcott@ubuntuAMD4:~$ 

No luck with the clean install...

rt

---

### Post by wayne_cat on 2009-07-18
> **rtalcott said:**
> rtalcott@ubuntuAMD4:~$ uname -a
Linux ubuntuAMD4 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 x86_64 GNU/Linux
rtalcott@ubuntuAMD4:~$ 

No luck with the clean install...

rt

I think it is time for a bug report. Losing a core is not a "minor problem"

---

### Post by rtalcott on 2009-07-18
wayne_cat...I agree...turns the machine into a slug!

However since I appear to be the only person seeing this I continue to think that it's maybe not an issue of Ubuntu's but of my particular hardware...although as I have said before...8.10 & 9.04 were fine...I think I'll check my sanity and boot up the 9.04 Live CD tomorrow...

And...as I also mentioned before.....this version gives me my audio and usb hardware....apparently they were not recognized before...so going back to 9.04 does not sound like a great idea.
rt

---

### Post by wayne_cat on 2009-07-18
please report this as a bug. You are not the only Linux user with this motherboard and this seems to be a complicated problem ... I think it can not be solved here in the forum. The Launchpad specialists will ask for further information and they will forward this problem to other developers (kernel/mainboard geeks) if they don't know a solution ... the result is a fix.

The important information:

it seems to be related to the A740GM-M motherboard

---

### Post by ronacc on 2009-07-18
if the 9.04 live cd sees both cores definitely report it as a bug and mark it as a regression . if the live cd don't see both suspect a hardware problem , I am running an amd64x2 ( different mobo ) and have not seen this problem at any time since the start of karmic .

---

### Post by rtalcott on 2009-07-19
Booted up 9.04 64 bit and definitely see 2 cores....filed a bug:
[https://bugs.launchpad.net/ubuntu/+bug/401374](https://bugs.launchpad.net/ubuntu/+bug/401374)

Any more suggestions would be greatly appreciated and Thank Everyone for the assistence!
rt

---

### Post by rtalcott on 2009-07-24
Tried 32 bit Alpha3....same issue...although I don't have the problem on other machines...
rt

---

### Post by gcordoba on 2009-08-07
Same problem here:
--------------------------
gcordoba@urcunina:~/programs/titan/titan2D$ uname -a
Linux urcunina 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux

gcordoba@urcunina:~/programs/titan/titan2D$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz
stepping	: 11
cpu MHz		: 2000.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 5984.57
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz
stepping	: 11
cpu MHz		: 2000.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 5984.92
clflush size	: 64
power management:

gcordoba@urcunina:~/programs/titan/titan2D$ dmesg |grep CPU
[    0.000000]   Transmeta TransmetaCPU
[    0.000000] SMP: Allowing 8 CPUs, 6 hotplug CPUs
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 8, nr_node_ids 1
[    0.000000] Initializing CPU#0
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.450807] CPU0: Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz stepping 0b
[    0.004000] Initializing CPU#1
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.536440] CPU1: Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz stepping 0b
[    0.536451] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.540029] Brought up 2 CPUs
[    0.540074] CPU0 attaching sched-domain:
[    0.540082] CPU1 attaching sched-domain:
[    1.908010] Switched to high resolution mode on CPU 0
[    1.908490] Switched to high resolution mode on CPU 1
[    2.500262] processor ACPI_CPU:00: registered as cooling_device0
[    2.500309] processor ACPI_CPU:01: registered as cooling_device1
gcordoba@urcunina:~/programs/titan/titan2D$ dpkg -l |grep linux-image |grep ii
ii  linux-image-2.6.28-11-generic              2.6.28-11.42                              Linux kernel image for version 2.6.28 on x86
ii  linux-image-2.6.28-14-generic              2.6.28-14.47                              Linux kernel image for version 2.6.28 on x86
ii  linux-image-generic                        2.6.28.14.19                              Generic Linux kernel image
gcordoba@urcunina:~/programs/titan/titan2D$ sudo dmidecode -s processor-version
Not Specified
----------------------------------------
Probably is not only a bug for AMD machines. I just installed ubuntu 9.04 yesterday and it is the only operative system here.
Best regards,
Gustavo

---

### Post by wayne_cat on 2009-08-07
> **gcordoba said:**
> Same problem here:
--------------------------
gcordoba@urcunina:~/programs/titan/titan2D$ uname -a
Linux urcunina 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux

gcordoba@urcunina:~/programs/titan/titan2D$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz
stepping    : 11
cpu MHz        : 2000.000
cache size    : 4096 KB
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
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow vnmi flexpriority
bogomips    : 5984.57
clflush size    : 64
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz
stepping    : 11
cpu MHz        : 2000.000
cache size    : 4096 KB
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
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow vnmi flexpriority
bogomips    : 5984.92
clflush size    : 64
power management:

gcordoba@urcunina:~/programs/titan/titan2D$ dmesg |grep CPU
[    0.000000]   Transmeta TransmetaCPU
[    0.000000] SMP: Allowing 8 CPUs, 6 hotplug CPUs
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 8, nr_node_ids 1
[    0.000000] Initializing CPU#0
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.450807] CPU0: Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz stepping 0b
[    0.004000] Initializing CPU#1
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.536440] CPU1: Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz stepping 0b
[    0.536451] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.540029] Brought up 2 CPUs
[    0.540074] CPU0 attaching sched-domain:
[    0.540082] CPU1 attaching sched-domain:
[    1.908010] Switched to high resolution mode on CPU 0
[    1.908490] Switched to high resolution mode on CPU 1
[    2.500262] processor ACPI_CPU:00: registered as cooling_device0
[    2.500309] processor ACPI_CPU:01: registered as cooling_device1
gcordoba@urcunina:~/programs/titan/titan2D$ dpkg -l |grep linux-image |grep ii
ii  linux-image-2.6.28-11-generic              2.6.28-11.42                              Linux kernel image for version 2.6.28 on x86
ii  linux-image-2.6.28-14-generic              2.6.28-14.47                              Linux kernel image for version 2.6.28 on x86
ii  linux-image-generic                        2.6.28.14.19                              Generic Linux kernel image
gcordoba@urcunina:~/programs/titan/titan2D$ sudo dmidecode -s processor-version
Not Specified
----------------------------------------
Probably is not only a bug for AMD machines. I just installed ubuntu 9.04 yesterday and it is the only operative system here.
Best regards,
Gustavo

Hmmm ... You have 2 CPUs in /proc/cpuinfo and dmesg also reports 2 CPUs with kernel
2.6.28 ... but you have just 1 CPU with the kernel version 2.6.31 ... right? ... could you
please post the results after booting 2.6.31

---

### Post by gcordoba on 2009-08-07
Sorry my ignorance. How to boot on kernel 2.6.31?

---

### Post by keypox on 2009-08-07
> **gcordoba said:**
> Sorry my ignorance. How to boot on kernel 2.6.31?

it appears your using 9.04.  This thread is about 9.10.  IF you install 9.10 you will get upgraded to the .31 kernel.  

Or you could install it on your 9.04.

---

### Post by Stereotypical Rage on 2009-08-08
> **rtalcott said:**
> Tried 32 bit Alpha3....same issue...although I don't have the problem on other machines...
rt

So the Jaunty 64 bit LiveCD worked but Alpha 2/3 (32 and 64 bit of Karmic failed?

I'm on Karmic (I don't have your mobo) and I have a quad-core Phenom and I do see all 4 cores and all 8GBs of RAM in both places (sys mon and /proc/cpuinfo).(Just needed the PAE kernel to see all 8GB RAM as the server kernel was done away with on 32bit)

Linux ChubbyBunny 2.6.31-4-generic-pae #23-Ubuntu SMP Mon Jul 27 19:37:25 UTC 2009 i686 GNU/Linux

Have you tried a different kernel series? Such as the Server Kernel? linux-image-2.6.31-5-server is current I show. It seems to me it's a kernel bug and not a hardware problem.

---

### Post by rtalcott on 2009-08-08
Correct...9.04 see two cores BUT Alpha 3...32 and 64 bit does not.

Good suggestion...trying the server....I have not done that...

I would certainly prefer a kernel bug to a hardware issue!
rt

---

### Post by gcordoba on 2009-08-11
Hi,
thanks for your replies.
Yes I am on 9.04, but this seems to be an issue carried on from 7.04. I do not remember if some years ago it was fixed and how, but clearly the problem remains even in 9.10. If this is a bug, and it is fixed on one of the flavours, I hope it will be fixed on any other flavour for good.

By the way, I could not install .31, as synaptic does not show me that option (looking for linux-image). Thus, I assume that it can be a bit risky to install .31 for my self.
Now I have a silly question as I become a bit confused, because the dmesg and cpuinfo correctly report two processors, but uname seems to see just one:

gcordoba@urcunina:~/programs/titan/titan2D$ uname -a
Linux urcunina 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux

I was expecting to see "...2009 i686 i686 GNU/Linux" instead, as it used to be. My question is: is there any other means to test if a computer is actually using more that one processor?

Thanks,
gustavo

---

### Post by wayne_cat on 2009-08-11
> **gcordoba said:**
> Hi,
thanks for your replies.
Yes I am on 9.04, but this seems to be an issue carried on from 7.04. I do not remember if some years ago it was fixed and how, but clearly the problem remains even in 9.10. If this is a bug, and it is fixed on one of the flavours, I hope it will be fixed on any other flavour for good.

By the way, I could not install .31, as synaptic does not show me that option (looking for linux-image). Thus, I assume that it can be a bit risky to install .31 for my self.
Now I have a silly question as I become a bit confused, because the dmesg and cpuinfo correctly report two processors, but uname seems to see just one:

gcordoba@urcunina:~/programs/titan/titan2D$ uname -a
Linux urcunina 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux

I was expecting to see "...2009 i686 i686 GNU/Linux" instead, as it used to be. My question is: is there any other means to test if a computer is actually using more that one processor?

Thanks,
gustavo

You can trust /proc/cpuinfo ... btw ... uname does not show the number of processors. 

```
NAME
       uname - print system information

SYNOPSIS
       uname [OPTION]...

DESCRIPTION
       Print certain system information.  With no OPTION, same as -s.

       -a, --all
              print all information, in the following order, except omit -p and -i if unknown:

       -s, --kernel-name
              print the kernel name

       -n, --nodename
              print the network node hostname

       -r, --kernel-release
              print the kernel release

       -v, --kernel-version
              print the kernel version

       -m, --machine
              print the machine hardware name

       -p, --processor
              print the processor type or "unknown"

       -i, --hardware-platform
              print the hardware platform or "unknown"

       -o, --operating-system
              print the operating system

       --help display this help and exit

       --version
              output version information and exit

```

---

### Post by gcordoba on 2009-08-11
Thanks,
thus despite uname is no longer showing the number of processors, I will trust /proc/cpuinfo, which shows that both of the processors are at least identified, as you suggest. I hope that both of them will be used in a parallel process that I need to run.
Matter of faith?...

Thanks again,
Gus

---

### Post by wayne_cat on 2009-08-11
> **gcordoba said:**
> Thanks,
thus despite uname is no longer showing the number of processors, I will trust /proc/cpuinfo, which shows that both of the processors are at least identified, as you suggest. I hope that both of them will be used in a parallel process that I need to run.
Matter of faith?...

Thanks again,
Gus

It is really easy to see the cpu utilization of each core (multicore cpu). Install the package "sysstat"

```
sudo apt-get install sysstat
```and the run the command with the "-P ALL" option

```
root@macbook:~# mpstat -P ALL
Linux 2.6.31-5-generic (macbook)     11.08.2009     _i686_    **[COLOR=Red](2 CPU)[/COLOR]**

18:21:03     CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
18:21:03     all    8,34    0,01    3,00    0,84    0,03    0,02    0,00    0,00   87,76
18:21:03       **[COLOR=Red]0[/COLOR]**    9,46    0,02    4,20    1,47    0,07    0,04    0,00    0,00   84,73
18:21:03       **[COLOR=Red]1 [/COLOR]**   7,25    0,01    1,83    0,22    0,00    0,00    0,00    0,00   90,69
root@macbook:~# 
```

---

### Post by gcordoba on 2009-08-11
Enough evidence!
Thanks.

---

