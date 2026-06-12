---
title: "Dual booting Truecrypt Vista and dmcrypt Ubuntu 12.04"
date: 2014-04-01
forum: Installation &amp; Upgrades
---

### Post by augustrigmarole on 2014-04-01
I've been trying to set up a dual boot computer where one operating system is Vista (encrypted with Truecrypt) and the other is Ubuntu 12.04, encrypted using the alternate CD's built-in system (I believe it was called dmcrypt). I read many guides, but many of them are out of date or didn't exactly match my situation. I think I'm close, but I'll provide a summary of what I've done so far, and hopefully someone else can tell me what I'm missing.

First, I installed Windows Vista. More accurately, I "restored" it. Because it wasn't directly installed from a disc that can be used on any computer, I ended up with 2 partitions: 1 bootable partition about 1-2 GB in size, and the other partition consisting of the rest of the hard drive (about 500 GB).

I reduced the size of the main partition using Gparted to make room for Linux; I freed up about 200 GB. Then I set up the following partitions using Ubuntu 12.04's alternate installer CD:

/boot (unencrypted): 200 MB
Root (encrypted): 10 GB
/home (encrypted): 180 GB
swap (encrypted): The remaining space

It took a lot of trial and error (and many reimages) to get the installer not to complain with errors, but the installer was finally satisfied that I had arrived at a working scheme with my manual partitioning. Installation appeared to proceed. I was asked where I wanted to install the boot loader, and I specified the /boot partition I had created rather than the MBR, because I read that this can conflict with Truecrypt's own boot loader. Shortly afterwards, the disc ejected and I was prompted to restart.

This is where I am now. The problem I am facing now is that I cannot boot into Ubuntu. There is no option for me to do so when the computer restarts. I am not asked whether I want to boot into Windows or Linux. This means although Ubuntu was most likely successfully installed, I don't know how to boot into it. At this point, some guides would suggest that I proceed to do an encryption of the Windows partitions with Truecrypt. I would, but I don't think Truecrypt will somehow fix my booting problems. Intuitively, it seems to make more sense to make sure I can boot into Ubuntu before doing the Truecrypt encryption.

How should I proceed? How do I boot into Ubuntu, and at what point should I use Truecrypt to finish the job? My final objective is to have fully encrypted installations of both Vista and Linux, perhaps with the exception of the boot partitions.

---

### Post by Mark Phelps on 2014-04-01
Have you booted into Vista to confirm that it still works after shrinking it? Asking, because shrinking Vista with GParted risks corrupting the filesystem -- not always, but often enough that it is a serious problem.  In future, you should only use the Vista Disk Management tool to shrink it.

Also, according to the list, you now have six partitions on your drive -- which is unlikely if you have an MBR-formatted disk (not GPT).  You should boot from the Ubuntu install media, get to a terminal, enter "sudo fdisk -lu" (lowercase L, not a one), and post back the results -- so we can see what partitions you have on your drive.

---

### Post by oldfred on 2014-04-01
One user just installed grub2's boot loader to a flash drive. Then if he wanted to boot Ubuntu, he chose to boot flash drive using one time boot key. It avoided the one MBR issue and tying to modify Truecypt's booting.

You can just install grub to flash drive, or install a full grub2 to have its own grub.cfg which you then would have to manually maintain, or you can put entire /boot with kernels on flash drive, but that probably would make system a bit slower like a full install to a flash drive.

---

### Post by augustrigmarole on 2014-04-01
> **Mark Phelps]Have you booted into Vista to confirm that it still works after shrinking it? Asking, because shrinking Vista with GParted risks corrupting the filesystem -- not always, but often enough that it is a serious problem.  In future, you should only use the Vista Disk Management tool to shrink it.

 Also, according to the list, you now have six partitions on your drive -- which is unlikely if you have an MBR-formatted disk (not GPT).  You should boot from the Ubuntu install media, get to a terminal, enter "sudo fdisk -lu" (lowercase L, not a one), and post back the results -- so we can see what partitions you have on your drive.[/QUOTE]

Yes, I did boot into Vista to confirm that it still works after shrinking it and before doing anything else. Vista ran some kind of checkdisk program on itself and made a minor adjustment, but booted fine after that. In fact, even after I installed Ubuntu, Vista still boots just fine said:**
> One user just installed grub2's boot loader to a flash drive. Then if he wanted to boot Ubuntu, he chose to boot flash drive using one time boot key. It avoided the one MBR issue and tying to modify Truecypt's booting.

 You can just install grub to flash drive, or install a full grub2 to have its own grub.cfg which you then would have to manually maintain, or you can put entire /boot with kernels on flash drive, but that probably would make system a bit slower like a full install to a flash drive.

I'm sure this is a perfectly acceptable option to some people, but I am really hoping I don't have to depend on using a flash drive just to boot into an operating system that is already on the disk. Some users have reported being able to achieve a setup where if they entered the Truecrypt password, they were able to boot into Windows, but if they pressed Esc at the Truecrypt boot loader's screen, they were then directed to Ubuntu. I would like to achieve this or something similar without using any external media if possible.

---

### Post by oldfred on 2014-04-01
Then you may have better luck in the truecrypt forum.

This user used some info from the truecrypt forum, but not sure what he did. But it was to mount/boot an ISO?
       Restore lost partiiton that was truecrypt
[http://ubuntuforums.org/showthread.php?t=1874260](http://ubuntuforums.org/showthread.php?t=1874260)

---

### Post by augustrigmarole on 2014-04-02
Right now, this isn't a Truecrypt problem yet. It's just an Ubuntu problem. I only have an unencrypted Windows installation and a dmcrypt encrypted Ubuntu installation.

Let's take it one step at a time. How can I boot into Ubuntu? The installer finished, so it must have accepted my manual partitioning. As I said, I installed the boot loader in the /boot partition, which in the sudo fdisk -lu output above is /dev/sda5. Why can I only boot into Windows, but not into Linux? I tried messing with the BIOS by the way; nothing I do there will help. The BIOS only lets me choose the boot order of physical hard drives rather than partitions within hard drives. Something about installing Ubuntu's boot loader to my /boot partition has essentially rendered the Ubuntu installation invisible. There must be a way to fix this.

To give everyone who's reading this a better picture of how my hard drive is partitioned right now, I've included a screenshot from Gparted. In the picture, /dev/sda1 is my Windows boot partition, /dev/sda2 is my Windows data partition, /dev/sda5 is my Ubuntu /boot partition, /dev/sda6 is my Ubuntu /root partition, /dev/sda7 is my Ubuntu /home partition, and /dev/sda8 is my Ubuntu swap partition. I don't know how there is 1.02 MiB of unallocated space left; I didn't leave any free space after the Ubuntu install, so maybe the installer created it automatically.

---

### Post by oldfred on 2014-04-02
BIOS based computers only boot from the MBR, not from a PBR (partition boot sector). If you have a boot loader that allows multibooting then one system may let you boot another. But Windows is not a system that allows multibooting anything other than other copies of Windows.
Grub2 also does not properly fit into a PBR. It converts to hard coded addresses or blocklists.

If not yet truecrypt, just install grub to MBR. That will let you boot both Ubuntu & Windows.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by augustrigmarole on 2014-04-02
I'm working on that Boot Repair report right now. In the meantime, let me try to get a clearer perspective on the problem. You said BIOS based computers boot only from MBR, rather than PBR. If this is true, what computers do support booting from PBR? The only possibility I can think of right now is UEFI. Is this correct? Assuming that only UEFI computers can boot PBR, and also assuming that Truecrypt's boot loader can't be coaxed into allowing multibooting, then it would seem that my mission of dual booting a Truecrypt-encrypted Windows installation and a dmcrypt-encrypted Ubuntu installation has just become impossible. Am I missing something here?

---

### Post by oldfred on 2014-04-02
No computers that I know of boot from PBR. BIOS has since beginning (35 years ago) only booted from MBR.
Windows boots from MBR, but that code in MBR looks at partition table for boot flag or active partition and loads more boot code from PBR. The old Lilo Linux boot loader works similarly.
Grub only uses MBR, but adds code in sectors after MBR (core.img) and had files in Ubuntu partition to complete boot process.

This is how all BIOS systems work. While Vista it applies to all BIOS Windows systems.
       Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

UEFI systems boot from an efi partition, not sure if Windows still has some boot code in PBR or not (I think so), but Ubuntu does not. UEFI directly reads every folder in efi partition for .efi files to use to boot. Somewhat like having mulitple MBRs as each efi folder is another system without any real limit other than size of UEFI's NVRAM.

---

### Post by augustrigmarole on 2014-04-02
Ok, I read most of the multiboot article, but so far, no luck. As you know, Ubuntu asked me where I wanted to install the boot loader, and I said specified /dev/sda5 (screenshot with partition information is above). I created /dev/sda5 to serve as the boot partition, and I even specified that it be /boot. Based on the multiboot article, I tried to help the MBR by setting the boot flag on /dev/sda5 instead of /dev/sda1 where it was (screenshot shows this). Even with the boot flag on Ubuntu's /boot partition (AKA /dev/sda5), my computer tells me I have no bootable partition. Ubuntu just won't boot! Did I mess up the partitioning scheme when I was doing the install? If I did, the installer gave no indication; it finished without complaining!

Many users have claimed to be able to successfully boot into Ubuntu even after installing the boot loader into a manually created /boot partition. If booting Ubuntu after installing its boot loader this way is possible, then booting Ubuntu after installing its boot loader this way must not be the same as booting from PBR because as you said, that is impossible.

I am completely confused and overwhelmed. I spent weeks reading guides on this problem already, and I can't even get a working Ubuntu installation. Any help would be appreciated.

---

### Post by oldfred on 2014-04-02
It is best just to install grub2 boot loader to the MBR.

The Windows boot loader also has internal code to make sure you only boot from a primary partition. There is a work around but it is better to have grub in MBR. The grub code in PBR is functional but may need to regularly be replaces as updates to grub may move files on partition and hard coded address will be wrong. You then have to have Ubuntu live installer readily available to make fixes to reinstall grub2.
Move boot flag back to Windows as Windows need to see that flag when it uses Windows boot loader, makes repairs to Windows or installs Windows. Or boot flag is vital for Windows. Grub does not use a boot flag.

If you try to install to a partition like this command, you get this error. On a new install it bypasses error but probably should not.
 grub-setup -v /dev/sda6
> Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
Embedding is not possible, GRUB can only be installed in this setup by using blocklists. However blocklists are UNRELIABLE and its use is discouraged.
error: If you really want blocklists, use --force 

---

