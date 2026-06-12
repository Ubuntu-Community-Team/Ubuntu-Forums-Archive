---
title: "repeated attempts to install lubuntu 15.04 (64 bit iso burnt to CD) desktop fails"
date: 2015-06-29
forum: Installation &amp; Upgrades
---

### Post by Vasu_Muppalla on 2015-06-29
I downloaded the amd64 version of lubuntu 15.04, verified, burnt to CD and again verified the CD- checksums match those given online.

My notebook is hp dm-4310nr. It is an AMD E1800 notebook and I use an SSD. UEFI boot without security. It has a 500 mb vfat partition that I specified as the efi system partition and created a root ext4 partition. It started copying files and toward the end, failed with a disk write error. So I tried again, this time allowing the installer to erase entire disk and create its own partitions and the same result.

It is an SLC type SSD and it was working fine before the installation (it had opensuse before). It is not that old and I am certain it has plenty of life left.

I don't know the actual error as it does not show the underlying error. The CD is fine - no physical damage, no read errors.

---

### Post by ajgreeny on 2015-06-29
Really burned to CD?  Not a DVD?

The iso file is too large to fit on a CD so if you really have forced a burn to a CD in some way, that is undoubtedly why it will not install to an OS.

---

### Post by Vasu_Muppalla on 2015-06-29
It is not the ubuntu iso - LUBUNTU 15.04 iso. It is only 690 MB and it says it is a cd image. Besides, the cd burning and verification worked. 

Also, I was able to run it in live CD mode without errors. I was able to run a few apps, navigate the menu and change desktop settings etc.

---

### Post by ubfan1 on 2015-06-29
Did you run fstrim on the ssd after removing Opensuse?  My limited understanding of SSDs is that just deleting files does not necessarily make the space available again until TRIM has been run.

---

### Post by ajgreeny on 2015-06-30
Apologies; I did not notice this was Lubuntu.

---

### Post by Vasu_Muppalla on 2015-07-18
I should mention the following-

The notebook ( HP dm1-4310nr) has UEFI firmware.

I turned secure boot off and legacy mode on.

Opensuse installs fine, creating the EFI partition and GPT.

I tried several versions of ubuntu. Last time kubuntu unstalled successfully was 13.x when the partition table was regular. A newer version failed to install and I tried ubuntu to same effect. Ubuntu wants to use grub-efi even when it seems unable to handle EFI/GPT for this hardware; opensuse consistently handles it well.

I tried converting the GPT to MBR but lubuntu (15.04) insists on EFI and created ESP - I allow it to take over the disk. It fails at the last stage when doing boot loader installation.
There is no other OS on the disk.

---

### Post by ubfan1 on 2015-07-18
Well if Opensuse install an EFI partition in legacy mode, that's wrong!  Anyway, if your partitioning is GPT, you will need a grub-bios partition (small 1M unformatted partition) to hold the core.img (the guts of the bootloader) which no longer fits after the master boot rec.

---

### Post by Vasu_Muppalla on 2015-07-18
> **ubfan1 said:**
> Well if Opensuse install an EFI partition in legacy mode, that's wrong!  Anyway, if your partitioning is GPT, you will need a grub-bios partition (small 1M unformatted partition) to hold the core.img (the guts of the bootloader) which no longer fits after the master boot rec.

It is the bios which operates in compatibility mode. You can use either grub-efi or grub. Ubuntu attempts to use grub-efi and fails- this has been happening since 14.x or 13.10 ( 2years now). 

Opensuse partitions GPT, created the EFI partition, installs grub-efi successfully.

opensuse succeeds in doing what ubuntu has been attempting for two years ! I was hoping that changing the partition table back from GPT will inspire ubuntu installer to go the legacy route but no, it doesn't.

I was hoping to try lxde and opensuse's lxde is not very good. KDE is too heavy for this laptop. pclinuxos lxde edition does not even boot ( cannot handle UEFI firmware yet). These are my options. Don't want fedora or anything.

---

### Post by sudodus on 2015-07-18
> **ubfan1 said:**
> Well if Opensuse install an EFI partition in legacy mode, that's wrong!  Anyway, if your partitioning is GPT, you will need a grub-bios partition (small 1M unformatted partition) to hold the core.img (the guts of the bootloader) which no longer fits after the master boot rec.

+1

I think ubfan1 has an important point here.If your partitioning is GPT, you will need a bios_grub partition if you want to install in CSM alias BIOS mode. If you have not, there will be problems.

So either create such a bios_grub partition, make an MSDOS partition table, or install Ubuntu in UEFI mode.

---

### Post by Vasu_Muppalla on 2015-07-18
> **sudodus said:**
> +1

I think ubfan1 has an important point here.If your partitioning is GPT, you will need a bios_grub partition if you want to install in CSM alias BIOS mode. If you have not, there will be problems.

So either create such a bios_grub partition, make an MSDOS partition table, or install Ubuntu in UEFI mode.

Maybe I am not clear in explaining or you haven't read all the posts above. 

I allow lubuntu installer to taker over the ENTIRE disk. It creates 3 partitions - ESP, swap and ext4 and starts copying. In the end, it fails, presumably when installing the boot loader. I say presumably because with kubuntu ( older version), I could see that that is where it fails. I LET the installer do its own thing and it does create the ESP partition.

It is NOT a corrupt cd because liveCD works fine. I can boot and run lubuntu desktop off live CD fine.
Hard disk is fine because I was able to install opensuse tumbleweed iso AFTER the ubuntu failure.

---

### Post by sudodus on 2015-07-18
I'm not sure about your problem, but I'm trying to identify what might be a problem. If we can discard it, fine, one thing less to be worried about.

Are you still trying to install in BIOS mode, 'legacy mode on', in other words *not* UEFI mode?

Is it an MSDOS partition table or a GUID partition table (GPT)?

I'm afraid, that the installer does not create a new partition table, so you have to switch manually between an MSDOS partition table or a GUID partition table (GPT). You may say that it is a bug, but if you know about it, you can manage it with Gparted.

---

### Post by Vasu_Muppalla on 2015-07-18
> **sudodus said:**
> I'm not sure about your problem, but I'm trying to identify what might be a problem. If we can discard it, fine, one thing less to be worried about.

Are you still trying to install in BIOS mode, 'legacy mode on', in other words *not* UEFI mode?

Is it an MSDOS partition table or a GUID partition table (GPT)?

I'm afraid, that the installer does not create a new partition table, so you have to switch manually between an MSDOS partition table or a GUID partition table (GPT). You may say that it is a bug, but if you know about it, you can manage it with Gparted.

I repeatedly said in posts above that I tried BOTH partition table types. I explicitly converted the P.T. to msdos so ubuntu would not be stymied BUT it creates the ESP partition in any case and when I inspect the P.T., it is back to GPT so you are mistaken. The installer DOES convert the P.T. type.

Legacy mode support allows you to use it in EITHER mode- UEFI or msdos. It doesn't LOCK you into one mode. I know this because with the same bios mode, opensuse configures UEFI boot. Are you saying that I should turn legacy support off and it will work ? Is that a requirement for the installer ?

---

### Post by ubfan1 on 2015-07-18
A quick question: This is an internal disk, not an external enclosure right?  External disks do have problems installing the bootloader.
You are confusing mode (UEFI vs. legacy or compatibility) and disk partitioning (MSDOS vs GPT).
Neither mode, UEFI nor legacy locks you into any disk partitioning type if Windows is not present.  Windows on UEFI requires GPT partitioning.
Ubuntu doesn't care, but most people have experience with using the UEFI/GPT combination -- That requires an EFI partition for the bootloaders.  The installers definitely work with this combination.
  If you want to go legacy/GPT, you will need to have a grub-bios partition (1M,unformatted), no EFI needed.  Not sure what the installer would do.
  If you want to go UEFI/MSDOS, you will need an EFI partition. Although the live media uses this combination, most hard disk install instructions use GPT, and I am not sure what the installer would do, but since it's the same thing as for UEFI/GPT, they probably work.
You choose the mode in UEFI settings/(aka. BIOS setup).
I would suggest UEFI mode, and GPT partitioning -- the most common.
At this point, I suggest really cleaning off that SSD before trying an install. It may have unwanted backup partition tables or something which will potentially confuse the installer.
I have not installed Lubuntu  on an UEFI, and am assuming the installer is just like Ubuntu's.

---

### Post by sudodus on 2015-07-19
> **Vasu_Muppalla said:**
> I repeatedly said in posts above that I tried BOTH partition table types. I explicitly converted the P.T. to msdos so ubuntu would not be stymied BUT it creates the ESP partition in any case and when I inspect the P.T., it is back to GPT so you are mistaken. The installer DOES convert the P.T. type.

Legacy mode support allows you to use it in EITHER mode- UEFI or msdos. It doesn't LOCK you into one mode. I know this because with the same bios mode, opensuse configures UEFI boot. Are you saying that I should turn legacy support off and it will work ? Is that a requirement for the installer ?

I'm sorry but we do not understand each other - both ways I think. I'm asking questions about things that you have already explained, and I do not understand your explanations. And you do not accept my suggestions, because they do not make sense to you.

Now I try again, with this single request:

Please explain what you mean by legacy mode, and how you set your computer into it (legacy mode)!

---

