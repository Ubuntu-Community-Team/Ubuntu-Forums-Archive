---
title: "How to use 7.10 boot parameters?"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by digbyt on 2007-10-23
Does anyone know how

---

### Post by digbyt on 2007-10-23
Initial post went out prematurely.. :confused: 

What I wanted to ask was does anyone know how we are supposed to use the 'Special boot parameters' described in the F1 help screens on the 7.10 install disk? Ths instructions refer to the 'Boot:' prompt which seem no longer to exist in the 7.10 disc. There is an F6 option for 'Other options', which produces the command line:
 'Boot Options file=/cdrom/pressed/ubuntu.seed boot=casper xforcevesa initrd=/carper/initrd.gz quiet splash --'
 but if I append the "aic7xxx.aic7xxx=no_probe" which I think I need (and is mentioned the help screens) the kernel produces the message
 "[    0/000000] Unknown boot option 'aic7xxx.aic7xxx=no_probe':ignoring"
and unsurprisingly my system continues to hang :(

It is not clear where on this line the parameters are supposed to be put (if it matters), but all the combinations I have tried produce the same results..

Is this a problem with the 7.10 workstation install CD, or am I missing something?

Thanks,
DigbyT

---

### Post by shof2k on 2007-10-23
If you download the linux source, you will find a file in /usr/src/linux/Documentation called kernel-boot-parameters.txt.  it explains all the options and what they do.  

I've attached the file.

---

### Post by digbyt on 2007-10-24
Thanks, but the problem isn't so much not knowing how to use linux kernel boot parameters in general - just that I don't know how I am supposed to pass parameters to the kernel in Ubuntu 7.10.  

The problem seems to be that the help screens are copied verbatim from Debian and dont apply to the current Ubuntu install disk configuration - and either give me boot options that arn't valid on the supplied kernel, or I have not worked out how to pass them properly in this setup...

Either way it seems to be a flaw in the 7.10 install disk as it stands, and there is a need for some elaboration on what the help screens should say...

DigbyT

P.S. for what it is worth, I tried a Debian 4.0r1 netinstall last night, and appart from having to tweak the xorg.conf file, it worked like a charm. Odd because ubuntu used to be the easier to install..

---

### Post by wislon on 2007-10-24
I am battling with some of these things myself (for instance I can't get anything since Edgy to boot without "acpi=force"). I would love to know what things like "noapic" and things like that do :)

---

### Post by wislon on 2007-10-24
digbyt : you can pass parameters to the kernel on the boot commandline (in the grub menu). You can either do this dynamically (by pressing 'e' on the initial boot, and then 'e' again on the "kernel" line in the commands presented to you). Go to the end of that line, and insert whatever parameters you need to, then press "b" to continue booting. These parameters only "stick" for that session tho.

Otherwise, do a gksudo gedit /boot/grub/menu.lst to do it, and those changes will stay until the kernel is next upgraded. 

HTH :)

---

