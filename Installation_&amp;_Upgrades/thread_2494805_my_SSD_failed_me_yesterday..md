---
title: "my SSD failed me yesterday."
date: 2024-01-27
forum: Installation &amp; Upgrades
---

### Post by karmapia on 2024-01-27
I tried to install ubuntu on my windows machine yesterday
it went horribly wrong and i had to give up the windows OS i had, and i had to format the whole SSD and reinstall windows.
how it happened is described below.

===============================================

I used to like this ubuntu when i was in a college, and back then there was a thing called wubi.
The thing is, I wanted to run this ubuntu again and run it, so I tried to find that wubi thing. turns out wubi doesn't exist anymore,
so I thought i had to create a 25GB partition on my 500GB SSD, which has the windows 10 OS installed on.
I created a bootable ubuntu usb stick using.... a certain software which i do not remember anymore(..), and the ISO for Ubuntu 22.04.3 LTS. and booted with the stick.

I am not sure how exactly happened, but first ubuntu installation attempt on the 25GB partition that Windows OS created has failed.
I'm not sure why it failed thou, But the ubuntu wouldn't be able to boot on its own.
(And I think the windows was still alive and bootable till this moment.)
So I booted on the stick again, and this time the installer would tell me if i wanted to remove the Ubuntu and reinstall ubuntu on that 25GB partition, so i told him to go ahead.
But on this second attempt, the installer said something like /dev/sda(the SSD) has failed somehow, and this error is critical.

From this point, many things were impossible.
First of all there was no MBR on the SSD on any level. it was completely gone.
I 'tried ubuntu' raw from the bootable stick and tried to use boot-loader(?) program to fix the SSD and but it wouldn't work
So I had to create another stick with Windows ISO
and this windows stick was also completely helpless on
(A) recognizing the Windows partition on the SSD,
(B) Auto-correcting SSD,
or (C) Any information I could find to restore Windows SSD was useless and it was very clear that any suggestion on the web wasn't really working on my case.

So I had to give up the old Windows OS, So I copied the data that i could gather to the usb stick, bulldozed the SSD and clean-installed the Windows 10 on SSD.



=========================================================



I still want to try to install the ubuntu on my computer. but i still do not know why or how i failed.
If anybody have any idea on why i failed, or what mistake i took, or any better method that is known to be much safer than my method, I want to hear it.
And if anybody have any question on details of how i failed, please ask it away if it helps you to diagnose what went wrong with my machine. i'm more than happy to answer any questions you might have.

thx a lot

---

### Post by ajgreeny on 2024-01-27
**Never create a partition that you want for Linux using Windows**; I'm not 100% sure of what Windows does but I believe it can sometimes create the Windows equivalent of a Linux LMV partition which is unfortunately unusable by Linux.

You should have simply created a 25G unallocated area on the disk and then pointed the Ubuntu installer to that.

I'm afraid I can not help further with the problem you have now reinstalling Windows as I have not used any Windows version of my own since 2005 when it was XP.

---

### Post by karmapia on 2024-01-27
oh, but that was exactly what i did thou,
I left the 25GB to be unallocated, because i knew the windows system does not know how to format the space in ext4.
ubuntu easily recognized the empty space and turned the 25GB empty space into ext4 on its first try.
the ubuntu on its first installation had a recognizable boot loader which would give me options including ubuntu and the windows.
it was just that the ubuntu was not properly installed and failed to boot on its course.

---

### Post by oldfred on 2024-01-27
Windows 10 should have been in UEFI boot mode on gpt partitioned drive. Unless you installed it in old BIOS/MBR mode.
Microsoft has required vendors to install UEFI/gpt since 2012 and release of Windows 8.

You then have to be sure to install Ubuntu in UEFI boot mode. 
You mention MBR. UEFI does not use MBR for booting but an ESP - efi system partition which is FAT32.
A gpt drive does have an MBR with just one entry saying drive is gpt, so old partitioning tools do not try to format it and damage it.

Boot-Repair can only fix Linux issues. It primary updates or installs grub. But its report can show boot issues & details on configuration.
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If Windows issues, you typically need your Windows repair/recovery drive. You did make one?
Repair/backup/restore
[https://www.microsoft.com/en-us/software-download/windows10ISO](https://www.microsoft.com/en-us/software-download/windows10ISO) & 
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

Before any major change, you must update your full backup, but you should regularly be doing that anyway.

Or am I telling you to close the barn door after the horses are all gone? :)
We are here to try to help chase them down, if necessary.

---

### Post by TheFu on 2024-01-27
Problems like this are why I don't dual boot.  Instead, I use virtual machines to run other OSes.  This way, only 1 OS controls the actual hardware and provides simulated, fake, hardware, for each "guest" virtual machine.  Either Windows or Linux can be the host or the guest, but your MS-Windows license may force a specific choice.  Since around 2010, virtualization has been excellent with really great performance, except for heavy GPU needs.  If you are doing productivity applications, programming, or running servers, than a virtual machine or 10 is the best answer, IMHO.

Best of all, sometime in the next 12 months, MSFT will screw with the boot files on the box and break any dual boot you install. With virtual machines, that won't matter.

---

### Post by ajgreeny on 2024-01-27
I'm very much with TheFu in suggesting using only virtual machines instead of dual booting which I haven't done now for many years.

Actually, that's not strictly true.
I have just tried a dual boot of my current main OS, Xubuntu 22.04 with the development version 24.04 but quickly decided that it's honestly hardly worth it when I can much more easily use KVM/QEMU to run a virtual machine of the development version.  It lasted just 2 days before I deleted it!

It's so easy to share the data files from 22.04 with 24.04 with a virtiofs shared filesystem that for me one of the previous advantages of virtualbox no longer exists.
If you've never used or tried KVM/QEMU, do read about it and give it a try.  Using it, I find it almost impossible to realise that I'm using a VM not a hard metal install as it runs just like a real OS.

I can't comment on using Windows as a host for VM as I've not used Windows for 19 yrs except on other peoples computers, and I have no reason to run it any more, even as a VM.

For more on KVM see:-
[https://help.ubuntu.com/community/KVM/VirtManager](https://help.ubuntu.com/community/KVM/VirtManager)
[https://www.linux.com/audience/devops/creating-virtual-machines-kvm-part-1/](https://www.linux.com/audience/devops/creating-virtual-machines-kvm-part-1/)
[https://www.debugpoint.com/share-folder-virt-manager/](https://www.debugpoint.com/share-folder-virt-manager/)  # This shows how to share data files between host and guest.

---

### Post by yancek on 2024-01-27
One of the major problems I see is that we don't know what the problem(s) were as you didn't keep notes so all kinds of thngs which might have been explained cannot be now.  If you are doing something new or unfamiliar, the logical thing to do is to keep detailed notes on exacxtly what you did and what happened as a results.  Good luck.

---

### Post by MAFoElffen on 2024-01-27
I have used and created multi-boot systems since 2005, with Windows 7, OpenSolaris, and Linux... With Nvidia GPU's. To me, it is just oldhat, but requires a few things to keep up on.

Even just multiple versions of Ubuntu on my Workstation to test and maintain things can be a challenge, when Grub fights over which release is in control of the main boot process.

I think in more of an overall broader picture of what needs to happen and who does what. Things just happen. 

I do admit that Windows has an ego, and feels that it lives in a vacuum as the sole OS on a machine So that when it makes foundation changes, it cares only about itself. 

Linux, as a whole, is more friendly, neighborly, and aware of what else might be around it.

---

### Post by karmapia on 2024-01-27
> **oldfred said:**
> Windows 10 should have been in UEFI boot mode on gpt partitioned drive. Unless you installed it in old BIOS/MBR mode.
Microsoft has required vendors to install UEFI/gpt since 2012 and release of Windows 8.

You then have to be sure to install Ubuntu in UEFI boot mode. 
You mention MBR. UEFI does not use MBR for booting but an ESP - efi system partition which is FAT32.
A gpt drive does have an MBR with just one entry saying drive is gpt, so old partitioning tools do not try to format it and damage it.

Boot-Repair can only fix Linux issues. It primary updates or installs grub. But its report can show boot issues & details on configuration.
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If Windows issues, you typically need your Windows repair/recovery drive. You did make one?
Repair/backup/restore
[https://www.microsoft.com/en-us/software-download/windows10ISO](https://www.microsoft.com/en-us/software-download/windows10ISO) & 
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

Before any major change, you must update your full backup, but you should regularly be doing that anyway.

Or am I telling you to close the barn door after the horses are all gone? :)
We are here to try to help chase them down, if necessary.

I am not sure if my system was set up UEFI/gpt or BIOS/MBR. But if you ask, i'd say it was in bios/mbr system. Back then, i thought uefi/gpt sounded fairly new and it would be less compatible than bios/mbr.

And there was a partition in my SSD that said 'recovery' on its label, I am not sure what it did when the trouble arose, it did no good when i had the trouble haha.

I didn't really think backup was necessary because my 'c-drive' doesn't store any real data in it. c-drive only has a operating system. all the data, documents, pictures and etc are in a saparate hdd.
So I didn't lose any real data in the process. I just lost my windows OS, so i had to set up a new one.
(btw, the new one is in UEFI/gpt this time)

---

### Post by karmapia on 2024-01-27
> **TheFu said:**
> Problems like this are why I don't dual boot.  Instead, I use virtual machines to run other OSes.  This way, only 1 OS controls the actual hardware and provides simulated, fake, hardware, for each "guest" virtual machine.  Either Windows or Linux can be the host or the guest, but your MS-Windows license may force a specific choice.  Since around 2010, virtualization has been excellent with really great performance, except for heavy GPU needs.  If you are doing productivity applications, programming, or running servers, than a virtual machine or 10 is the best answer, IMHO.

Best of all, sometime in the next 12 months, MSFT will screw with the boot files on the box and break any dual boot you install. With virtual machines, that won't matter.

That was the original idea that i had before i try to install ubuntu. But I wanted something that is very separate and runs very stable, but virtual machine didn't quite meet my expectation.

Basically what i wanted to run was [1] a torrent program running with [2] VPN and [3] VM, but i couldn't quite get that. So i was trying to find a way to get rid of [3]VM by running dual boot.

---

### Post by karmapia on 2024-01-27
> **yancek said:**
> One of the major problems I see is that we don't know what the problem(s) were as you didn't keep notes so all kinds of thngs which might have been explained cannot be now.  If you are doing something new or unfamiliar, the logical thing to do is to keep detailed notes on exacxtly what you did and what happened as a results.  Good luck.

haha, i don't think i was even capable of taking a detailed note.

you can take a note about uefi/gpt or bios/mbr ONLY WHEN YOU KNOW what uefi/gpt and bios/mbr is.
I knew very very little about uefi/gpt before the problem happened so I can't even remember correctly if i had bios/mbr or uefi/gpt.

The only one thing i know for sure is that my previous windows 10 system was 'not compatible' with windows 11 upgrade because of something called TPM 2.0
And that TPM problem couldn't be solved unless i format the entire c-drive.
My memory on why it required me to format the c-drive is very foggy and unclear.
I 'think' it was TPM2.0 incompatible because the system was in bios/mbr rather than uefi/gpt. but not so sure.

---

### Post by karmapia on 2024-01-28
Thank you for giving me your thoughts on my situation.

Even thou my description was horribly lacking in detail, I could still assume that the reason why it went horribly wrong is because (A) I tried to create an partition from the windows machine instead of ubuntu installer, and (B) the SSD was in MBR not in GPT.

So, (A) I didn't try to create any partition within the windows OS and went straight to the ubuntu installer and let it make the partition on its own, and (B) was already solved since my new windows OS was already on UEFI/GPT

I set up ubuntu OS yesterday, working all proper and shining. Thank you for giving me your insight on my situation.

---

