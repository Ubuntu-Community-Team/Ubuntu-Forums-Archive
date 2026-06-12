---
title: "Windows and Ubuntu - Not the normal questions"
date: 2013-08-02
forum: Installation &amp; Upgrades
---

### Post by doubleloveyou on 2013-08-02
I have a computer that has Windows Vista installed and Ubuntu.  I want to upgrade the windows to Windows 7 in place of Windows Vista.  Is there a way to do that without wiping out my Ubuntu?

---

### Post by GHADDAR on 2013-08-02
u should reinstall grub after installing new windows version , but watch out to not delete any ubuntu partition during win7 setup

---

### Post by doubleloveyou on 2013-08-02
Thanks.  I will try that.  I guess it is not needed to state I should backup before installing.  lol.

---

### Post by oldfred on 2013-08-02
Backup is always a good idea. 

Windows has been known to corrupt partition tables if it installs to a primary partition after the extended. If you Vista is sda1, it should (but still backup) be ok. Often Windows just rewrites partition table without the Linux partitions as it cannot see them, and data is still there.

You will need Ubuntu liveCD/DVD/flash or other Linux repairCD to fix grub2 in the MBR.

 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

