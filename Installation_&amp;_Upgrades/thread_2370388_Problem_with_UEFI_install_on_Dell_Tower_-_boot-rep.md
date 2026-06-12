---
title: "Problem with UEFI install on Dell Tower - boot-repair does not fix"
date: 2017-09-02
forum: Installation &amp; Upgrades
---

### Post by kmeek on 2017-09-02
Whe I first tired to install ubuntu on my new DELL XPS 8920 tower the SSD drive was not showing up as an option.

I figured out I had to enable the UEFI boot in the bios -- then I could see the drive, and was able to install 17.10 on the SSD drive /dev/nvme0n1p1.

When I rebooted it worked great for several weeks - but after installing some updates and rebooting I am unable to get the boot loader to start grub.

I tried booting to live cd off of USB stick and installing and running boot-repair  but it did not solve problem.

Here is the paste bin output from boot-repair: [http://paste.ubuntu.com/25453270/](http://paste.ubuntu.com/25453270/)

I don't care about /dev/sda -- that is a 1 TB drive I will use for data later.  

Goal is to just get UBUNTU running from the SSD ( which was working )  

Would be ok if I could just make a usb that would boot and let me add an entry to launch linux from the SSD.

Can anyone help me get this Dell bios to recognize and boot my uefi

FYI:  I am running EFI with secure boot off.

---

### Post by oldfred on 2017-09-02
Did you turn RAID off in UEFI and set drives to AHCI?
Windows may need the AHCI driver loaded first to be able to boot.

You installed in the Advanced LVM Logical Volume manager configuration. That does not use standard partitions except as a container for the LVM.
Did you also choose full drive encryption? LVM is required for full drive encryption but is optional otherwise.
You have to understand LVM and its differences to standard partitions. And have to always include the lvm2 driver, to be able to mount the LVM.

I do not really know LVM, so cannot help much on that.
       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

It also looks like you have another install on the HDD sda drive. Ubuntu only has one of different installs as the default boot loader in the ESP - efi system partition.
Script does not post grub.cfg that is in ESP, it is only 3 lines and is a configfile(chain entry) to the full grub.cfg in your install. But you can only have one, so either have to boot from grub from default into preferred install and reset it by reinstalling grub as new default. Or manually edit /EFI/ubuntu/grub.cfg.
Post your /EFI/ubuntu/grub.cfg.

You many be able to use Boot-Repair's advanced mode. Make sure it sees the LVM install & then do a total uninstall/reinstall of grub which should reset /EFI/ubuntu/grub.cfg to boot LVM install.

 Dell with NVMe needs AHCI & boot option nvme_load=YES
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en) 
    Dell XPS 8920 & Nvidia GTX 1060 & PCIe M2 drive Raid change to AHCI
[URL="https://ubuntuforums.org/showthread.php?t=2360929"]https://ubuntuforums.org/showthread.php?t=2360929
[/URL]Dell XPS 8910  16.04.1 works, 16.04 did not
[https://ubuntuforums.org/showthread.php?t=2351949](https://ubuntuforums.org/showthread.php?t=2351949)
Dell XPS 8900 i7-6700 pcie_aspm=off (also: Asus X555UB)

Some Dells needed UEFI update from Dell & firmware update for SSD.
[http://askubuntu.com/questions/760257/ubuntu-16-04-failed-clean-install-on-new-hard-drive](http://askubuntu.com/questions/760257/ubuntu-16-04-failed-clean-install-on-new-hard-drive) 


[URL="https://ubuntuforums.org/showthread.php?t=2360929"]
[/URL]

---

### Post by kmeek on 2017-09-02
I did set drives to AHCI -- I think I had to do that to see the SSD I think.

I typically use LVM so I can modify add disks / grow my partitions -- I am an experienced Sysadmin using linux 15+ years so LVM I can handle lvm.

The install on sda was an attempt to install on the SATA drive -- just to see if that would boot -- but it doesn't boot either.

I posted the grub.cfg  -- [http://paste.ubuntu.com/25453832](http://paste.ubuntu.com/25453832)

But I think that directory still has lots of other messed up stuff. including the old Windows boot driver -- maybe that is what is messing me up.  

It also has attempts from doing boot-repair and other things I did to try and get it to work.  

I'd like to try to recreate just what I need in there for EFI boot, but not sure what that is...

I think boot-repair is trying to fix the /dev/sda install and naming that ubuntu

You say: Dell with NVMe needs AHCI & boot option nvme_load=YES  --- But I was able to use it install from live cd without adding this option as long as I had UEFI unsecured boot in bios.  Maybe because I'm using 17.10 ( newer ubuntu might have that driver )

Where would I add these links in my grub configs? I'm not even getting the grub menu so boot options are not my problem I think.

Also -- when I try to add a UEFI boot option from file menu my bios hangs up... just black screen.

Kevin

---

### Post by oldfred on 2017-09-02
Your grub.cfg in the ESP is booting sda2 on HDD.
>  search.fs_uuid 1e16051e-abd4-4ad8-b81c-38200c715f62 root hd0,gpt2  



You can manually edit that to have UUID of LVM's root. It looks like you do not have a separate /boot which most LVM installs I have seen have. You may then need an insmod of the lvm.mod so grub can see the LVM partition. The grub entry you have for that install shows the insmod lvm line in the install, but that is too late if not in a boot partition. So I think the insmod lvm must be in  the grub.cfg in the ESP.

Not sure if then Boot-Repair is not working as it expects a separate /boot with LVM.

With two installs, you should not be running Boot-Repair's auto fix. Only use the Advanced mode and choose an install. I might make sure it sees LVM install, make sure separate /boot is unchecked and see if a full uninstall/reinstall of grub works.

Having /EFI/Microsoft should not matter.

You seem to have a lot of Boot-Repair's reports. I might houseclean most out. Maybe save first & most recent for now.

---

### Post by kmeek on 2017-09-02
So right now I have 2 partitions on the SSD

p1 is the boot,esp drive -- that has the UEFI info for boot chain right?
p2 is the lvm  -- which has everything on one.

Are you saying I should have a /boot that is just ext4 separate from my lvm root volume to make booting simpler?

The reason I'm not seeing the grub menu is that the pointer in the exp directory points to an lvm volume that it can't open without the drivers?

Maybe I can mount the lvm partition -- shrink it and create a partition and move the /boot info to an ext4 partition and point the grub.cfg to that?

Before I do that I will try the boot repair again with advanced mode -- selecting the lvm , unchecked separate boot and see if that works.  BTW -- I get some errors on boot-repair, I think because I have 17.10 - I'll try to make better note of them this time to see if they might cause issue.

BTW Thank you very much for your assistance. This has been driving me nuts.  New HW is supposed to be better.!!

---

### Post by oldfred on 2017-09-02
I thought LVM had to have the /boot partition. 
But several posters have said they installed without one as grub had been updated to not need /boot and grub could directly boot into LVM partitions.

Again I do not use nor know much about LVM, but do know booting and UEFI booting.

I have not tried running boot repair on my 17.10 install. I do use 16.04 LTS as main working install, but have most other current versions installed also. But only Ubuntu with fallback/gnome-panel not other flavors. 

I know UEFI entries require device like /dev/nvme0n1, and I filed a bug report to add listing of NVMe  against bootinfoscript which is a separate program, but also the first part of Boot-Repair's report.
[https://github.com/arvidjaar/bootinfoscript/issues/5](https://github.com/arvidjaar/bootinfoscript/issues/5)

So have not been able to see many /EFI/ubuntu/grub.cfg's to know how they are configured since maybe not hd0,gpt1? But search by UUID should be all that is required. So if you enable grub's lvm and search by UUID the grub in the ESP should then be able to find full grub in /boot folder inside your LVM?
If/when you get it working I would be interested in seeing the correct /EFI/ubuntu/grub.cfg.

Instead of 3 line grub, I have seen this also:
>  configfile (hd0,gpt7)/boot/grub/grub.cfg 


The use of  (search by)UUID or specific device in grub like (hd0,7) for set root is optional. But grub changed to UUID as many systems will redefine drive order, but UUID rarely change.

---

### Post by kmeek on 2017-09-02
I tried to re-run boot-repair -- advanced with 

Looks like it fixed the boot.cfg to refer to the SSD partition 2 -- it even mentions lvm so I think it "did" the right thing. 
But it doesn't work.

ubuntu@ubuntu:/mnt/EFI/ubuntu$ cat grub.cfg
search.fs_uuid 30313bba-fbdf-46ee-a9da-87cdc2473a08 root lvmid/z3ak4f-6JM7-6gxM-wpwT-d8Gu-6W0h-7fOmss/SNR1uw-f9Wi-nNNS-Zf00-T1sj-wxeb-dD26UY 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


Full output of boot-repair:  [https://paste.ubuntu.com/25455506/](https://paste.ubuntu.com/25455506/)

[COLOR=#000000]You said earlier that I may need to do  insmod of the lvm.mod so grub can see the LVM partition.   I'm thinking that is my issue now.  
What is syntax to put that in the grub.cfg on the esp partition?

I'd like to try that before I try to redo the partition to move the /boot directory to it's own ext4 partition.[/COLOR]

---

### Post by kmeek on 2017-09-02
How can I confirm that my bios is reading the correct grub.cfg from the eps directory on the SSD?

This thread seems to say Dell looks for certain things in efi boot directory.. [https://askubuntu.com/questions/731931/uefi-not-finding-a-bootable-system-on-xps13](https://askubuntu.com/questions/731931/uefi-not-finding-a-bootable-system-on-xps13)

The bios allows you to add UEFI entry -- but it hangs when It try to do that...

---

### Post by oldfred on 2017-09-03
I might try this, but not sure if lvm is in ESP?

```
insmod lvm
search.fs_uuid 30313bba-fbdf-46ee-a9da-87cdc2473a08 root  lvmid/z3ak4f-6JM7-6gxM-wpwT-d8Gu-6W0h-7fOmss/SNR1uw-f9Wi-nNNS-Zf00-T1sj-wxeb-dD26UY  
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```
 And the mod files for grub are here.
/boot/grub/x86_64-efi

And you normally do not add mod files to grub in ESP. so not sure if you also have to copy lvm.mod into ESP and then whether in /EFI/ubuntu or in a sub-folder for grub to find it?
Some drivers are automatically included in grub, so all the .mod files are not always needed. Do not know if with LVM install you already have the lvm installed? 

I am sure I saw someone say they had LVM without a /boot partition. I will later search & see if I can find it, but not before tomorrow.

---

