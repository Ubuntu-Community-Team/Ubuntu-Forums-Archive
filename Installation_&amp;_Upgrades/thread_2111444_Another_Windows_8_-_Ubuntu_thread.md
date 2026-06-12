---
title: "Another Windows 8 - Ubuntu thread"
date: 2013-02-01
forum: Installation &amp; Upgrades
---

### Post by dave032 on 2013-02-01
Hello,

I am trying to get ubuntu to dual boot with windows 8 on my notebook. Whenever I boot up, it goes directly to windows. The notebook is a lenovo z580 that came preloaded with windows 7. I did a clean install for windows 8. I am a newbie to linux so please bare with me.

My bios states that "UEFI Boot" is enabled in boot settings, but its seems that the windows 8 partition is ntfs and loads through mbr.  (windows Diskpart doesn't indicate that its gpt either)

Here are my steps.
I shrunk the windows partition to free up space using a third party program in windows since windows disk management would only allow me to shrink  2 gigs.

I used a liveusb of the 12.10 secure-remix x64. I've tried different install configurations. First one was choosing the "something else" option then created the /swap and /root, with /sda for boot information. 

In another attempt I created a /boot partition and had boot info go there. I also tried the same things using an external harddrive.

Finally I did a "install along side something else" (which I understand to be the same thing as my first attempt.  I tried boot repair (recommended settings) for all these attempts with no effect.

And now here I am.  here is the bootinfo for the last attempt [http://paste.ubuntu.com/1599352/](http://paste.ubuntu.com/1599352/)

Thank you.

---

### Post by Thee on 2013-02-02
I dont have UEFI, but as I understand you need to disable it in the BIOS and disable "quick boot" also. Then you should be able to make Ubuntu dualboot.

---

### Post by dave032 on 2013-02-02
> **Thee said:**
> I dont have UEFI, but as I understand you need to disable it in the BIOS and disable "quick boot" also. Then you should be able to make Ubuntu dualboot.

I've thought about disabling uefi boot, but I am unsure what would happen to my windows installation. I would rather try to avoid rebuilding the system.

Uefi boot is the only option that mentions "uefi". There is nothing for quick boot/ secure boot, but I believe those options are only for new computers preloaded with windows 8. Mine came preloaded with windows 7.

---

### Post by oldfred on 2013-02-02
A few Windows 7 systems had Windows 7 in UEFI mode, but not with secure boot. But most Windows 7 systems had the old BIOS/MBR configuration even though computer had UEFI/BIOS.

If you have gpt partitioning and an efi partition as sda1 or sda2 then you are in UEFI mode. If MBR(msdos) and no efi partition then you are booting in BIOS mode.

Ubuntu needs to be installed in the same mode UEFI or BIOS as Windows to allow dual booting.

Best to see details. Post this from terminal in Ubuntu's liveCd/DVD/Flash installer:

       sudo parted /dev/sda unit s print

---

### Post by dave032 on 2013-02-02
Number  Start       End         Size        Type      File system     Flags
 1      2048s       718847s     716800s     primary   ntfs
 2      718848s     859252589s  858533742s  primary   ntfs            boot
 3      859252734s  976771071s  117518338s  extended
 5      859252736s  964468735s  105216000s  logical   ext4
 6      964470784s  976771071s  12300288s   logical   linux-swap(v1)

---

### Post by oldfred on 2013-02-02
You have a BIOS based boot with MBR(msdos) partitions. With UEFI and gpt there are no logical partitions.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)
    

If a Windows issue Boot-Repair will not fix it in most cases. Windows may need chkdsk or other repairs from a Windows repairCD. But Boot-Repair may show us what the issue is.

---

### Post by dave032 on 2013-02-02
I generated a boot info report last night after I attempted a boot repair with recommended settings. [http://paste.ubuntu.com/1599352/](http://paste.ubuntu.com/1599352/)

I can rerun boot repair and generate another boot info report if needed.

My computer bios states that uefi boot is enabled but the harddrive type is mbr. I'm not sure if that could be part of my problem.

---

### Post by oldfred on 2013-02-02
I do not know if report is before running Boot-Repair but it has a Windows boot loader (syslinux) in the MBR. But from UEFI menu you have to choose to boot in legacy/BIOS/CHM or whatever it is called, not UEFI mode.

Boot-Repair says it installed grub to MBR, so from a BIOS boot do you get Windows or Ubuntu?

---

### Post by dave032 on 2013-02-02
That boot info report was automatically generated after a boot repair with recommended settings.

I re-ran boot repair with recommended settings and it generated this report:
[http://paste.ubuntu.com/1602750/](http://paste.ubuntu.com/1602750/)

So in the bios should I set "uefi boot" to disabled?

Would there be any risk to my windows 8 system?

Thanks for helping.

---

### Post by oldfred on 2013-02-02
Should be fine. 

It is the new pre-installed Windows 8 systems that are installed with UEFI and UEFI's secure boot enabled.

With MBR partitioning you can only boot Windows in BIOS mode. With UEFI Windows has to have gpt partitioning.

---

### Post by dave032 on 2013-02-02
The UEFI boot was the issue. I disabled it, reinstalled ubuntu, ran boot repair with recommended settings (just for caution), and it worked.

Thanks for the help.

---

### Post by oldfred on 2013-02-02
Glad you got it sorted out. :)

---

