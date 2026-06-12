---
title: "Installs on 133/266mhz FSB but not 166/333"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by robster66 on 2010-02-25
I have tried posting this last time under a different title but no one can give me any good answers.  I have tried many things but none of which seem to work.  

Motherboard : N2PAP-LITE
Processor : AMD SEMPRON 2800+ (32 Bit)
Stock FSB Settings : 166/333MHz
Chipset : NVIDIA NFORCE2

This is a really odd problem.  It installs under 133/266MHz and runs fine.  When it's at 133/266 it reconizes it as AMD ATHLON XP in the BIOS and the Linux Installation.  I want to be able to install it using 166/333MHz which is the stock setting of the processor!  When I set it to that in the BIOS it reconizes as a AMD SEMPRON 2800+ but will not install Ubuntu 9.10.

This is the error I get if I try to run it from the CD, Install it, or boot from the current installation which I installed it with 133/266MHz.  

If anyone can please help me figure this out it would be great, im trying to use it as a server and would not like to bottleneck it as it shouldn't be.  I get these errors

```
check_bugs+0xbb/0xe9
start_kernel+0x2dc/0x2ec
? unknown_bootoption+0x0/0x1ab
i386_start_kernel+0x7c/0x83
```

Now if you want the whole error list I will type it up.

This is a link for the motherboard manual.
[http://www.machspeed.com/manuals/VIPER/N2PAP-LITE.pdf](http://www.machspeed.com/manuals/VIPER/N2PAP-LITE.pdf)



Thanks

---

### Post by robster66 on 2010-02-25
The whole code, took forever to write, I hope someone can figure this one out.


```

? mask_and_ack_8259A+0x52/0xf0
handle_level_irq+0x6f/0xe0
handle_irq+0x18/0x30
do_IRQ+0x47/0xc0
common_interrupt+0x30/0x40
? native_safe_halt+0x5/0x10
check_bugs+0xbb/0xe9
start_kernel+0x2dc/0x2ec
? unknown_bootoption+0x0/0x1ab
i386_start_kernel+0x7c/0x83

```

Not the whole thing but most of it.  I get it when I change my FSB settings to 166/333 and try to boot off the install or the cd.

---

### Post by robster66 on 2010-02-25
Does anyone know how I can decipher these codes and figure it out myself??

---

### Post by tgalati4 on 2010-02-25
How old is the machine?  Try installing using the slower speed.  Run memtest overnight.  Make sure you complete 30 cycles without errors.  It will take overnight to complete.

Once the RAM is validated at the slower speed, bump up the bus speed and run memtest again.

---

### Post by robster66 on 2010-02-26
Here are different things I have tried when booting from the 9.10 install disk.

Different options while trying to "Install Ubuntu" with 166/333MHz FSB

-Disabled nolapic (Hangs at black screen with "_" blinking.)
-Disabled acpi (Hangs at black screen with "_" blinking.)
-Disabled acpi=off (Hangs at black screen with "_" blinking.)

Now with this in mind, it INSTALLS with my BIOS set 133/266MHz.

I will let a memtest go overnight and post results, I am really curious to why it is doing this.  Im doing the memtest with 166/333Mhz FSB and 166/333Mhz RAM since that is what im having problems with and will post it in the morning.


The machine is probably 4-5 years old because I built it when I was 14 or 15.  It runs Windows 7 fine...

---

### Post by robster66 on 2010-02-26
Memtest86 v2.11 is what I ran and it detects my processor as an Athlon XP at 2005MHz.

Memory - (2048MB) @ 789MB/s
Chipset - nVidia nForce2 SPP / FSB : 167MHz
Settings - RAM 167MHz (DDR334) / CAS 2.5-4-4-7 / Single Channel (64 bits)

Time : 14:46:00 (10 Passed, 0 Failed)

---

### Post by robster66 on 2010-02-26
Bump

---

### Post by tgalati4 on 2010-03-01
It looks like a non-maskable interrupt (nmi) that causes a safety shutdown.  Try an older live distro such as Hardy.  Could be a regression in the newer kernels.

---

### Post by robster66 on 2010-03-01
What do I do if an older one works?

---

### Post by tgalati4 on 2010-03-01
File a bug with kernel.org for the version of the kernel that doesn't work.  Cut and paste your error and maybe someone working on the kernel can help troubleshoot it.

---

### Post by robster66 on 2010-03-02
It just hangs on 8.04 :(

---

### Post by robster66 on 2010-03-02
Above the call trace it says..

```

EIP:  [<c0103997>] common_interrupt+0x17/0x40 SS:ESP 0068:c0743f64
Kernel panic - not syncing:  Attempted to kill the idle task!
Pid: 0, comm: swapper Tainted:  G    D  2.6.31-19-generic #56-Ubuntu

```

I just wanted to know what this means.


I also looked in kern.log in the GUI I guess it's the current boot and it says 
```

cpufreq-nforce2: Detected nForce2 chipset revision C1
cpufreq-nforce2: FSB changing is maybe unstable and can lead to crashes or data loss.
cpufreq-nforce2: FSB currently at 133MHz, FID 12.0

```

I think im getting somewhere, just need some assistance

---

### Post by RJARRRPCGP on 2010-03-02
nForce 2 supports 166 Mhz FSB, so that's not the problem. 

However, make sure the Vcore is set to AT LEAST 1.65V!

---

### Post by robster66 on 2010-03-02
> **RJARRRPCGP said:**
> nForce 2 supports 166 Mhz FSB, so that's not the problem. 

However, make sure the Vcore is set to AT LEAST 1.65V!

The Vcore is set right, it runs fine on any Windows system.  I just can't get it to run with it set at these settings.

---

### Post by tgalati4 on 2010-03-02
cpufreq-nforce2 is telling you that the front side bus is unstable--it probably did a simple cycle count versus time and detected too much variability.  If your video card is a plug-in type, then take it out, blow the dust out with compressed air, and reinsert the card a couple of times to remove the contact resistance.

Reseat your ram chips and your power connectors while you are at it.

Since your machine is a few years old, it's possible that there is a crystal/timing problem that Windows is not sensitive to, but Linux is.

---

### Post by robster66 on 2010-03-02
I actually just moved everything in a new tower and I have an air compressor so I use that instead to blow everything out.  RAM + Video Card + Drives have recently been reseated a couple days ago.

---

### Post by tgalati4 on 2010-03-02
Try blacklisting the cpufreq-nforce2 module.  My impression is that it's for laptops to save power by throttling the GPU when not busy.  Do you really need it for a tower machine?

Also, take the nvidia card out and use the on-board graphics to do the install.  If the install is successful, then run it for a few days using the on-board graphics to isolate the motherboard from the video card as a cause for the problem.

---

### Post by robster66 on 2010-03-02
I don't have a onboard video card =/, I will try blacklisting it though.

---

### Post by robster66 on 2010-03-02
It still continues to hang on reboot with 166/333...  I don't need any CPU scaling ****.  Also after I reboot it when it hangs, it freezes at grub.

---

### Post by tgalati4 on 2010-03-03
I have run out of ideas.  You can try changing the graphics card to different slots to see if the behavior changes.  It's possible that your older motherboard has become unstable at the higher speeds.  It happens.

Are you sure that you are running at the higher speeds in Windows?  Perhaps windows is slowing the bus down as well, you don't realize it yet.

Kernel panics usually indicate a hardware problem because you don't get helpful diagnostic messages in the log files--like you are supposed to.

Hardware troubleshooting is therefore more difficult, because you don't have accurate diagnostic messages.

I would run at the slower speeds and see how many days of uptime you get.  If you get lockups, then the motherboard may indeed have a problem.

---

### Post by robster66 on 2010-03-03
It doesn't lock up at all it can be on for months and be fine.  I have hardware diagnostic bootable cds and such.  Im sure the system is fine it just doesn't make any sense to me.  I will keep trying and posting maybe ill get closer.

---

### Post by jirah on 2010-03-05
When a CPU fails to successfully boot an operating system at its RECOMMENDED clock speed, it only means one of two things. 1) That the CPU is failing and is no longer able to successfully pass all of the checks that the operating system performs against it to measure its capabilities. 2)That an intervening system which is integrated with the CPU clocking measures is failing. The major system in this category is the RAM, whose timing system is closely linked with the CPU. Since you have ruled out major RAM problems, well, that leaves only one culprit. 

  I successfully run an AMD Athlon 2800+ daily in Ubuntu, the differences being that I always use Via chipsets for these Athlon/Semprons and I am using PC3200 RAM instead of PC2700 as you are. I understand that it can be hard to accept that the system will function fine in Windows but not Linux, that frustration is understandable. But you said something very telling in your old topic, you said "A couple years ago I have had debian, fc, gentoo, ubuntu run on these specs". That tells me that it is not the Linux commands being sent to the CPU that have changed, but that something about your CPU has changed. The fact that the live discs and 8.04 also hang when you set CPU to recommended is also very telling. I fear you are quickly coming to the end of the life of that Sempy. I know that when my Athlon dies I will cry like a baby, it has been so reliable and good to me. But the chip will die, just like the rest of us :-)

---

### Post by jirah on 2010-03-05
I have broken this post up into two lest no one ever read it.

  One thing I have not heard you say is that you have tried this Linux install with this CPU in a different motherboard. Trust me, I know how scarce and relatively expensive these Athlon/XP/Sempron boards are getting. If I lived close to you I would let you borrow mine. But that is going to be the only definitive test to find out whether you have a dying CPU or faulty motherboard. Plus, have you tried the other distros you mentioned in your other thread since you began having this problem?
That would be a way to settle your mind as to whether it truly is a CPU or Linux problem, even though I think by now you know the answer to that question.

  Sorry for the long post but there is a lot to cover here within your troubles. Good luck and continue to let us know your progress please.

  Right, one more thing, even though its a long shot, but you have gotten rid of any sign of cpufreq, the cpu scaling program for controling frequencies in AMD and Intel 64bit processors. If you are not sure then just follow this post [http://ubuntuforums.org/showthread.php?t=1209386](http://ubuntuforums.org/showthread.php?t=1209386) just to make sure. It should not be installed by default based on the CPU you are using, but you never know. Ok, I think I am done now. Good luck.

---

