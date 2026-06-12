---
title: "intermittant Grub bash-like line editing message instead of grub"
date: 2023-03-17
forum: Installation &amp; Upgrades
---

### Post by Budoc on 2023-03-17
Hello,

On my Dell Inspiron 3793  I've started getting a "Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completion. Anywhere else TAB lists possible device or file completion." message at the splash screen instead  of a grub menu  that'll let me choose to boot ubuntu 20.04.6 and windows 10. This message  doesn't appear every time  - I generally type reboot  or hold the power button until I get an instance where grub loads normally and I'm back into Ubuntu. I've not been fiddling with my partitions and was surprised to see this error!

My boot-repair log obtained from running a recommended repair from a liveusb ubuntu session is here: [https://paste.ubuntu.com/p/fdCM9Srt57/]("https://paste.ubuntu.com/p/fdCM9Srt57/") This did not fix the problem.

Has anyone else encountered this problem, and how do I fix it? The only non-standard grub config I may have is a fix recommended by oldfred here for dells: [https://ubuntuforums.org/showthread.php?t=2445531&p=13965950#post13965950]("https://ubuntuforums.org/showthread.php?t=2445531&p=13965950#post13965950") to fix this bug: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1883785]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1883785")

I hope this is the correct sub-forum to post in, apologies if I've got it wrong! I saw other posts about grub here, so I thought it might be appropriate to post in this forum.

Thanks in advance.

---

### Post by oldfred on 2023-03-17
I am not seeing anything wrong in your configuration. Perhaps someone else may?

Issue often is two versions of grub installs, one BIOS & one UEFI and system is first trying to boot the incorrect (usually BIOS version) and then on reboot booting the correct one. And then incorrect grub and incorrect UEFI setting cause error. But you only show the one UEFI version of grub.

Check UEFI settings, but my Dell 5310 with similar specs just worked with 22.04. I forgot to change any UEFI settings, but did have to turn Windows fast start up & Windows bitlocker off.

---

### Post by tea for one on 2023-03-17
As oldfred mentioned, the grub configuration looks OK.

I did notice that your Ubuntu system partition is quite small and has very little free space.
Line 343 - /dev/nvme0n1p7  2.6G free  84% used space.

Perhaps a bit of housekeeping to free some space may help.

---

### Post by Budoc on 2023-03-18
Thank you oldfred and tea for one  for confirmation that the grub configuration at least looks like it's okay. 

The strange thing is this computer worked for about 18 months with this exact setup before I started getting this intermittent error message recently. Unfortunately, I cannot track it down to a particular software update that has caused it. Would there be any diagnostic logs that might help indicate what's going on? I've popped into BIOS and confirmed that everything is as expected with regards to UEFI (see attached photos). I've also got secure boot turned off which is something I always do after  being stung by it on a previous computer. I believe that fastboot on windows is turned off. I don't use Windows 10 much as unfortunately something's gone wrong with it as when I log in my mouse cursor turns into a spinning wheel and  it's really slow to open  anything. I need to reset it at some stage, but was concerned on the effect it might have on Ubuntu, so I haven't  done it yet. I do all of my work on Ubuntu, so I'm not missing Windows too much!

I'm trying to  reduce the usage of / tea for one. I didn't realise that could effect things. It's difficult when I've got  ubuntu root and windows  all on a 128GB ssd - I opted to put my personal data like home on the 1TB HDD.

---

### Post by tea for one on 2023-03-18
I'm not a big fan of Ubuntu system files on one disk and /home/user on a second disk.
Similarly, I'm also not keen on dual booting Windows and Ubuntu on the same disk.

As you mention that you seldom use Windows, would it be worthwhile to think about a different approach?
Ubuntu inc. /home/user on your SSD.
Windows 10 on your HDD but also create an EXT4 partition for Ubuntu use.

Each disk would have an ESP, which eliminates 99% of boot problems.

---

### Post by oldfred on 2023-03-18
Have you updated UEFI firmware & NVMe firmware.
Dell is pretty good about having updates in fwupdate.
Check if yours model is in list.
Devices using LVFS for firmware updates
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

My desktops are not in fwupd, so I have to manually update UEFI and I have Samsung NVMe drive, so compare firmware with Samsung's site.
Firmware
udisksctl status
inxi -d

sudo apt install nvme-cli
sudo nvme list

---

### Post by Budoc on 2023-03-19
Oldfred: here are the outputs of those commands:

```
udisksctl status

MODEL                     REVISION  SERIAL               DEVICE
--------------------------------------------------------------------------
CL1-3D128-Q11 NVMe SSSTC 128GB 22301116  TW0R3CDK9DH0006H0FKK nvme0n1 
ST1000LM035-1RK172        1002      WKPFPAKM             sda     
HL-DT-ST DVD+/-RW GU90N   A1C5      M2NK5IF2202          sr0  


 inxi -d
Drives:
  Local Storage: total: 1.03 TiB used: 174.35 GiB (16.6%) 
  ID-1: /dev/nvme0n1 model: CL1-3D128-Q11 NVMe SSSTC 128GB size: 119.24 GiB 
  ID-2: /dev/sda vendor: Seagate model: ST1000LM035-1RK172 size: 931.51 GiB 
  Optical-1: /dev/sr0 vendor: HL-DT-ST model: DVD+-RW GU90N 
  dev-links: cdrom,cdrw,dvd,dvdrw 
  Features: speed: 24 multisession: yes audio: yes dvd: yes 
  rw: cd-r,cd-rw,dvd-r,dvd-ram 


sudo nvme list

Node             SN                   Model                                    Namespace Usage                      Format           FW Rev  
---------------- -------------------- ---------------------------------------- --------- -------------------------- ---------------- --------
/dev/nvme0n1     TW0R3CDK9DH0006H0FKK CL1-3D128-Q11 NVMe SSSTC 128GB           1         128.04  GB / 128.04  GB    512   B +  0 B   22301116





```

I have been updating firmware previously either through  Windows 10 or through the Software Center in Ubuntu 20.04, although not recently. I have been getting notifications through the Software Center about a secureboot configuration update (see attached picture). I've not run it as I'm worried about grub not loading  on the reboot and my computer getting bricked. Is this a realistic concern, and should I try to install it? I'm not using secureboot due to problems with it on another computer a few years ago. Updated: a system update is now available for inspirons too in Software Center (see second attachment).



tea for one, that's something to consider in future, thank you. The problem is that my Windows 10 is OEM (I don't own a copy of Windows) and the default set up by Dell was to have Windows 10 OS and backup partitions on the 128 GB ssd and to have the 1 TB HDD as an empty NTFS volume labelled DATA. When I got the computer I thought the sensible choice if I wanted to keep Windows was to leave Windows where it was  on the SSD and shrink it to put ubuntu / in  a partition there. As my home directory could potentially be quite large with lots of Music files, if made sense to me  for it to be in a partition on the large 1TB HDD.  It also helps with the insurance cover the retailer gave me to at least leave Windows in place. Sorry it's so complicated! This was my first foray into  SSD/HDD laptops, and I'm beginning to wish I could have afforded a laptop with  a larger SSD at the time.

Thank you both for your helpful suggestions.

---

### Post by MAFoElffen on 2023-03-19
Well, sort of... With the purchase of your Dell Computer, it came with a licensed copy of an OEM version of Windows 10. The license is via "digital entitlement"...

RE: [https://www.dell.com/support/kbdoc/en-us/000126935/requirements-for-dell-windows-10-activation](https://www.dell.com/support/kbdoc/en-us/000126935/requirements-for-dell-windows-10-activation).

Notice there, it says:
> If the motherboard is replaced, activation no longer works.
Not entirely true... As a certified Dell On-Site Warranty Technician, I had to replace motherboards. Part of the post-process was to reburn the replacement motherboard firmware, with the old motherboard's service tag number, and to make sure the system came back up and Windows stayed activated.

You can request a preloaded Windows OEM installation USB from Dell, and they will send it to you... I would recommend you do, for the "just in cases"... With that, you can install Windows in any layout you want. The digital entitlement is tied to to the motherboard firmware, within the UEFI BIOS. Not what the disks are, or how it's laid out.

You want to check it yourself?
```

sudo dmidecode -t system

```
Dell also has agreements with Canonical, and sells some of their computer models preloaded with Ubuntu... Which their own support documents for Linux Users suggest that users visit this Forum.

---

### Post by tea for one on 2023-03-19
> **MAFoElffen said:**
> The digital entitlement is tied to to the motherboard firmware, within the UEFI BIOS. Not what the disks are, or how it's laid out.
I think that the Microsoft Digital Licence is now more flexible.

November 2021, I purchased a budget-priced Lenovo netbook with Windows 10 S mode pre-installed.
After creating a Microsoft account, I upgraded to Windows 10 Home.
Then I wiped the drive and installed Xubuntu.

April 2022, on my desktop PC (i.e. a different motherboard), I downloaded a Windows 11 iso and created a VM (using KVM).
You can install without a product key via "I don't have a product key"
I linked this Windows 11 VM to my Microsoft account and, surprisingly, the Windows 11 VM is now activated.
Windows 11 Settings > System > Activation > Activation State = Active (green tick within a green circle)
When you look at the details of your Microsoft account, there is no mention of a product key or a digital licence reference.

Why did I do this? - Just to experiment.

My guess is that Microsoft want users to install Windows OS with fewer obstacles than previously.
Subsequently, the user will be encouraged to sign up for paid services, games, storage etc. etc.

---

