---
title: "Black screen when booting (again)"
date: 2011-11-29
forum: Installation &amp; Upgrades
---

### Post by jvincek on 2011-11-29
Hi all, no one replied in the closed thread so I'm posting in a new one...

I need some help booting my Ubuntu OS (11.10). The problem is the black  screen after booting and I can't resolve the problem (or at least not  with full success).
As I understand it (by looking at various forums and "guides"), the  problem is in the fact that my laptop (HP G72-a26EZ) has 2 graphic chips  (one "standard" - ATI HD 5470, and one on the CPU itself - Intel  Pentium P6000).

So far I tried most of the options that I found and seemed remotely related to my problem, including but not limited to:
xforcevesa, acpi_osi= , acpi_osi="Linux", acpi_osi="Windows 2006" and  some others... Listing the available vga modes with vbeinfo also didn't  help.

I got the best results with the "nomodeset" option. Using that, i  successfully booted in graphics mode (no black screen), but the problem  is that I'm then limited to a low resolution ( 1024x768 ), which is not  even the correct aspect ratio (native resolution is 1600x900). I think  that using "nomodeset" my laptop is running with the "CPU-GPU" (that's  only my guess), but AFAIK there is no way of switching it to the ATI  card, or setting a greater resolution.

When I booted with "nomodeset" I tried installing the ATI drivers, and  the install was successfull, but again there was the black screen during  startup. I read somewhere that after installing the graphic card  drivers you could then boot without the "nomodeset", but that didn't  work in my case...

If anyone could give me some alternative solutions or share there  experience with the same/similar hardware I would be very grateful.

I need to use Ubuntu for OpenGL development but currently I'm limited to  the VirtualBox solution which is much slower and more unpractical then  the "normal" dual-boot option.

Thanks in advance.

---

### Post by Hakunka-Matata on 2011-11-29
Hi, Welcome;

In my BIOS Setup, there is an area that allows me to choose the first Graphic device, I can switch between the GPU on the MOBO, or a separate PCIE card I use.  But simply plugging your monitor into the video connector of choice should tell the system which GPU to use.

Just to get onboard and understand your situation better would you please post the output of some commands:
```
sudo lshw -C display
```Example: My System: 
```
das@sdb1GUID:~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: Radeon 3100 Graphics
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:18 memory:d0000000-dfffffff ioport:d000(size=256) memory:fbef0000-fbefffff memory:fbd00000-fbdfffff

```

---

### Post by mahmoodkamal on 2011-11-29
> **jvincek said:**
> Hi all, no one replied in the closed thread so I'm posting in a new one...

I need some help booting my Ubuntu OS (11.10). The problem is the black  screen after booting and I can't resolve the problem (or at least not  with full success).
As I understand it (by looking at various forums and "guides"), the  problem is in the fact that my laptop (HP G72-a26EZ) has 2 graphic chips  (one "standard" - ATI HD 5470, and one on the CPU itself - Intel  Pentium P6000).

So far I tried most of the options that I found and seemed remotely related to my problem, including but not limited to:
xforcevesa, acpi_osi= , acpi_osi="Linux", acpi_osi="Windows 2006" and  some others... Listing the available vga modes with vbeinfo also didn't  help.

I got the best results with the "nomodeset" option. Using that, i  successfully booted in graphics mode (no black screen), but the problem  is that I'm then limited to a low resolution ( 1024x768 ), which is not  even the correct aspect ratio (native resolution is 1600x900). I think  that using "nomodeset" my laptop is running with the "CPU-GPU" (that's  only my guess), but AFAIK there is no way of switching it to the ATI  card, or setting a greater resolution.

When I booted with "nomodeset" I tried installing the ATI drivers, and  the install was successfull, but again there was the black screen during  startup. I read somewhere that after installing the graphic card  drivers you could then boot without the "nomodeset", but that didn't  work in my case...

If anyone could give me some alternative solutions or share there  experience with the same/similar hardware I would be very grateful.

I need to use Ubuntu for OpenGL development but currently I'm limited to  the VirtualBox solution which is much slower and more unpractical then  the "normal" dual-boot option.

Thanks in advance.

I had Acer Aspire 5336, blank screen upon booting problem

upon inserting acpi_osi=Linux, i have to press Fn+brightness keys every time upon boot and it wakes up.

---

