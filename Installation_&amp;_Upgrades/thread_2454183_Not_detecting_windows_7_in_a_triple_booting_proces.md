---
title: "Not detecting windows 7 in a triple booting process"
date: 2020-11-24
forum: Installation &amp; Upgrades
---

### Post by prasun08 on 2020-11-24
I wanted to install ubuntu but it is not recognising my windows 7 on an already dual booted hard disk with windows 8.1 and windows 7
Thank you in advanced
Waiting for a reply

---

### Post by tea for one on 2020-11-24
Before you proceed any further, are you familiar with the following:-

Secure boot
Fast Start Up (Windows setting)
UEFI mode or Legacy (BIOS) mode

Please read this thoroughly first [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by prasun08 on 2020-11-24
i am familiar with secure boot and uefi mode or legacy bios but not with fast start up (windows settings)
my bios settings are set to legacy boot without secure boot
and both my windows oss are booting from legacy mode only

---

### Post by tea for one on 2020-11-24
Have you turned off **Fast Start Up** in both your Windows systems?

Have you backed up **all** your data?

Do you have Windows repair disks?

Do you have more than one disk on your PC?

Do you have proprietary graphics?

---

### Post by prasun08 on 2020-11-24
haven't backed up my data as I am not having hard disk to back it up 
even do not have a windows repair disks but I can get it easily from one of my neighbour
am using dell 5500 laptop with 1 TB Hard disk (note not a SSD)
don't have a GPU or neither a graphic card

---

### Post by prasun08 on 2020-11-24
have turned off fast start on my windows 8.1 but not on windows 7

---

### Post by CelticWarrior on 2020-11-24
Actually this is simpler than tea for one is putting it.
What you need to understand in a multi-boot system with different Windows versions is that one of those Windows is in charge of booting itself and all the others and because of that Ubuntu (Grub) will detect only ONE Windows and that one is Windows 8 in this case. By selecting the Windows entry in the Grub menu you'll then be presented with the Windows multi-boot menu you already know and from there select one or the other.

Additional notes:
[LIST=1]
[*]**Windows 7 is EoL (end of life)**. Do NOT use it connected to the internet and better to NOT use it at all, it's obsolete.
[*]Windows 8 is still support but not for very long and it's a dead-end anyway. If you need Windows then install Windows 10 (you may still get away with a free upgrade from Windows 8 or even 7)
[*]UEFI hardware asks for UEFI mode. It's a bad idea and an anachronism to force legacy mode for ANY of the OSes mentioned here.
[/LIST]

---

### Post by prasun08 on 2020-11-24
actually this was a problem while installing Ubuntu on my system and not while booting in it.
I selected something else while allocating drive space and there this problem arose. it wasn't detecting windows 7 but only windows 8 in the partition table so I abandoned the installation and came here to ask about it before making any changes to my system
additional info:
my hard drive is  not supporting windows 10 making as it makes my device very slow. 
tried using windows 10 before.
then switched to windows 7 which worked smooth like butter with my hard drive and then tried windows 8.1 which is also working fine.
inbuilt settings for my laptop were legacy mode and not uefi as it came with windows vista initially
my bios is set up to boot in legacy mode and uefi mode is not set up on it

---

### Post by CelticWarrior on 2020-11-24
> **prasun08 said:**
> haven't backed up my data as I am not having hard disk to back it up 
even do not have a windows repair disks but I can get it easily from one of my neighbour

You definitely should have backups BEFORE attempting such potentially destructive process as an OS installation, no matter which.
And yes, you should have Windows installation media of the same version in case it needs repairs. And in Legacy mode it's really a must. Once installed, Grub will replace the Windows bootloader in the MBR. If anything happens to Grub/Ubuntu you won't be able to boot, period.
One of the great advantages of the UEFI mode is the possibility to boot any installed OS directly.

> am using dell 5500 laptop with 1 TB Hard disk (note not a SSD)
 

A Dell Latitude 5500 has UEFI therefore UEFI mode is always preferred.

> don't have a GPU or neither a graphic card
GPU = Graphics Processing Unit = Graphics card (or integrated or embedded chip)
Yes, you do have one because otherwise you wouldn't have video output.

Now, why do you want to install Ubuntu? You can test it in a live session or even install it within Windows as a virtual machine.
Installing (bare metal) in a multi-boot scenario and even worse with a single drive, knowing the tech level you showed so far, is very a likely a recipe for disaster. Again, BACKUPS before anything else.

---

### Post by prasun08 on 2020-11-24
> **CelticWarrior said:**
> 

Now, why do you want to install Ubuntu? You can test it in a live session or even install it within Windows as a virtual machine.
Installing (bare metal) in a multi-boot scenario and even worse with a single drive, knowing the tech level you showed so far, is very a likely a recipe for disaster. Again, BACKUPS before anything else.

I wanted to install Ubuntu to get hands on it and then dropping out windows forever after getting well acquainted with the command line
speaking about creating a virtual machine (have  bad luck with it.) virtualisations in my laptop are very slow even after assigning around 6 gb of ram (have 8 gb ram) and 2 processors(having 2 cores only and both assigned to the virtual machine)
tried virtual box, VMware player and even VMware pro but the same result

---

### Post by CelticWarrior on 2020-11-24
> **prasun08 said:**
> I wanted to install Ubuntu to get hands on it and then dropping out windows forever after getting well acquainted with the command line
speaking about creating a virtual machine (have  bad luck with it.) virtualisations in my laptop are very slow even after assigning around 6 gb of ram (have 8 gb ram) and 2 processors(having 2 cores only and both assigned to the virtual machine)
tried virtual box, VMware player and even VMware pro but the same result

Yeah... NO.
You NEVER assign more than half the host's RAM, ever. It's surprising that it only became "very slow", it should have froze right then and there.
And assigning all the available cores is simply impossible, no hypervisor allows that.

---

### Post by tea for one on 2020-11-24
> **prasun08 said:**
> haven't backed up my data as I am not having hard disk to back it up 


**Back Up** is your first priority - nothing more, nothing less

---

