---
title: "Recovery Partition Access / Dual Boot Ubuntu &amp; Windows"
date: 2013-07-15
forum: Installation &amp; Upgrades
---

### Post by DAShuck on 2013-07-15
Recovery Partition Access / Dual Boot Linux & Windows


Hello

       I am new to this forum and I really need your help!  This is not your typical Linux query but I really need help from someone with more Linux experience than I have.  I hope that someone will find this problem interestingly enough to help me out or at least take pity on me.  :-)   My first couple attempts at loading Ubuntu on a two drive notebook ended badly.  The Ubuntu install overwrote the Bootmgr file and left Windows in operable.    I was trying load Ubuntu so that I could get back to learning Linux.   I need to get proficient in Linux and in Windows for some upcoming certification exams.   This issue just got even more complicated due to hardware problem with my new Notebook, see description below. 


       Background - I recently purchased a Toshiba Notebook (NB)and from day one there were problems. The biggest of which was a defective HDD.  After spending a lost of time with their Tech support, I realized I was going to have to diagnose he root cause of this problem myself.  They were absolutely no help, at all.   When I finally confirmed that it was the HDD that was causing the problem and not the Motherboard or the OS I contacted them to arrange to have the unit returned for Warranty Service and then they advised that I would have to pay for the round trip shipping, because they do not pay for it as part of their Warranty Service.  I have never had an manufacturer that did not pay for shipping on warranty issues, never.   I have only had the NB for about six week, to long to return it to the store.  That being said, the HDD has now deteriorated to the point that I need to move everything over to a new HDD.  The issue in front of me now is being able to access the "Recovery Partition" on the HDD to that I reinstall Windows.  Since Windows 8 (64) came with the NB, otherwise I will have to either pay to have the unit returned to Toshiba for a new HDD and OS and I really hate to pay them any more than I already have.   


       The issue is,  I need to figure out a way to access the OS in the "Recovery Partition" on my Notebooks HDD, so that I can reinstall the OS on to a new HDD and there is not apparent way to access that partition from within Windows 8.  What I need to be able to due is access it from a non-windows OS, then copy the OS Setup from that Recovery Partition and then copy it to a new HD and execute the System Install.  


       I am looking for any help possible!  Thank you n advance for your help and consideration!!!


Sincerely,

Doug

---

### Post by lukeiamyourfather on 2013-07-15
If the recovery partition is still there you can access it from GRUB or the Windows boot loader. There's often an option to create install discs for Windows and/or the entire recovery partition. That's how I'd recommend dealing with it. Alternatively you can use something like Clonezilla to copy the partition, but it can get ugly trying to make it bootable again on another disk (possible, just not trivial). Also there might be a utility in Windows to burn disc images for a clean install, that was the case with my Lenovo ThinkPad.

Worst case scenario you can just use whatever Windows 8 disc you want for the install and use the Windows product key on the bottom of the notebook. Older versions of Windows had lots of restrictions about what media could be used with what key, now they are all the same media and the keys will work if you install the proper product (Pro, Home, whatever). Then you can get software and drivers specific to that notebook directly from the manufacturer, like drivers and whatever other utilities they install.

---

### Post by ajgreeny on 2013-07-15
How exactly have you diagnosed a hard disk failure/problem which you say has happened?
Are you absolutely certain that this is the problem and not a BIOS/UEFI difficulty that could be overcome if you know how?

You do not say where you are writing this from, but I think in most countries you would have a warranty that covers return of goods to the supplier, not necessarily toshiba, but the shop/warehouse/website from which you purchased the machine if there is a hardware failure.  That is definitely the case here in UK, and I would be surprised if there were not some similar arrangement in your country.

I would double check that this is not the case in your country before trying to do much more.

---

### Post by DAShuck on 2013-07-15
Hi AJ   -   The HDD would thrash a lot, go up to 100% utilization (HDD busy signal ;) with less than 2Mbps of usage.  It was so bad that that my touchpad would quit working until the drive returned to a lower utilization level, the CPU and RAM during this same period of time would be <5% and <40% respectively.   I cloned a spare HDD and swapped the drive out.  The new drive worked perfectly.  I then put the "bad" drive back in and the problem was back immediately.      The problem is that the "bad" drive was also destroying (degrading) the data on HD, to the point that I cannot trust the data on it, nor on the clone.  SFC /scannow shows problems.  And now I can no longer "Refresh" nor replace the OS from the Settings / Recover menu.   Fortunately, I have a "Good" / "Out of the Box" backup of the HDD from the day that it arrived.

---

### Post by DAShuck on 2013-07-15
Hi Darth :-)    -   Thanks for responding!   I have an "Out of the Box" Disk backup of the original HDD with the installed OS and the Recovery Partition.  The issue now is that the OS copy on the replacement HDD won't allow me to access the recovery drive to replace the OS.  My guess is that the installed OS was further degraded by the "bad' HDD or possibly thru the cloning process.  What I would like to do is to access the "Recovery" partition in a way that I can inspect its contents, copy them to a new HDD or Blu-Ray disc if they appear to be intact and then execute the new OS install from there.  Failing that I am faced with the manufacturer's solution or in buying a new OS copy, either of which grinds me the wrong way.  I long for the days when the OS was shipped along with the computer on  CDROM or DVD, this "new" approach really sucks!!!

---

### Post by oldfred on 2013-07-15
As I understand it the new systems all require you to boot into the recovery partition. Many have found by accidentally booting into recovery it automatically rewrites partition table even before starting and that in effect erases a dual install.
If you have UEFI, that should be a boot option from the UEFI menu. Different vendors have implemented it differently. Some have a one key boot that goes straight to recovery. Some have many efi boot files in the standard efi partition. And others have a non-efi partition with efi boot files that they use to boot (somehow)?

---

### Post by DAShuck on 2013-07-16
> **oldfred said:**
> As I understand it the new systems all require you to boot into the recovery partition. Many have found by accidentally booting into recovery it automatically rewrites partition table even before starting and that in effect erases a dual install.
If you have UEFI, that should be a boot option from the UEFI menu. Different vendors have implemented it differently. Some have a one key boot that goes straight to recovery. Some have many efi boot files in the standard efi partition. And others have a non-efi partition with efi boot files that they use to boot (somehow)?           

Hi Fred  -   That is not the case in this instance for some reason, either the Mfg or Windows 8 has buried the EUFI into a buried menu. In that menu layer one has the choice to refresh the "System" or to "Clean the Drive and re-install the OS", neither function works however, both attempt to preform their programming but both return an error message stating that the Install needs to fixed  (but doesn't state how).    I have gone into the BIOS and there is no option there to boot into the recovery partition.      Doug

---

### Post by oldfred on 2013-07-16
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

