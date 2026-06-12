---
title: "UBUNTU no boot after 5 re installations"
date: 2015-03-14
forum: Installation &amp; Upgrades
---

### Post by ahmad18 on 2015-03-14
Re installed Ubuntu 14 32bits on my machine  5times but can not boot, No GRUB interface. I get either GRUB rescue, or no device, or boot from CD/DVD Disk boot failure messages.
tried Boot repair disc sveral times.
OK my machine Sda= windows 7 (SATA 600GB), another separate hard disc SdB (IDE Master, 60GB, NTFS),, then UBUNTU on third separate internal hard disc Sdc (IDE slave, 80GB)
Here is Boot repair disc info report
[Http://paste.ubuntu.com/10592067](Http://paste.ubuntu.com/10592067)
Boot repair disc insists on asking me if Ubuntu disc is removable disc , also I tried tried different options but no way. I even tried to tell it to re install last kernel but it went into empty loop (working for ours without writing anything to Hard disc.
I wish if I can install UBUNTU on separate disc, beside windows7, and can choose to boot into it windows without modifying windows MBR disc setting, and if I want to boot int UBUTU to chjoose the UBUNTU disc from Bios or Via external loader; something simple like Iboot.
N.B I can run UBUNTU and othe linuc distro from live USB with no problems except that may printers dont work, after sending print test page it dont fint fid any print job in Linux or sent to printers.
Help appreciated 
Ahmed

---

### Post by ajgreeny on 2015-03-14
I presume from your comment that you have set the BIOS to boot to /dev/sdc which is where both Ubuntu and grub are installed?  I do not know enough about hardware to know whether or not the fact that sdc is IDE and sda is sata may have some bearing on this, but others may be able to help with that.

There are, however, no ubuntu OSs showing in the two grub.cfg files from either /dev/sdc1 or /dev/sdc7 in your linked boot-repair report so I think you must have made some slip-up when you installed the system.  Did you let the installation proceed as default or did you choose "Something Else" at the partitioning stage? With grub on /dev/sdc.
 I think you must have used "Something Else" or grub would default to sda.

Did you ensure you set a mountpoint of / (or root) for the main OS partition when you installed?

---

### Post by oldfred on 2015-03-14
Not sure how you got a grub.cfg in sdc7 as that is your /home. Must be left over from an older install where you reinstalled without reformatting?
You have sdc1 as /boot, sdc5  as main install and sdc7 as /home. Swap is sdc6.

You should be able to in Boot-Repairs advanced mode, select the full uninstall of grub and reinstall to sdc. 
Do not use Boot-Repair's auto fix as that will install grub to every MBR which you do not want.

The full uninstall/reinstall of grub should also add a kernel, as ajgreeny noted that you do not have any kernels. Not sure how that occurred. 
If that does not work then a new Something Else reinstall with reformat would then be the easiest choice. Best to choose the same partitions you now have.

---

### Post by ahmad18 on 2015-03-15
Thank you Oldfred and  Ajgreeny for your help. I shall reformat the sdc disc to fat32 then reinstall Ubuntu as follows someting else, default boot system to windows, partion the sdc into ext4 then into 4 partitions ( /boot 0.5GB, /root 20Gb, / home 30GB, /swap 6GB) and set install Grub to sdc,  or should sdc1 (the partition flaged /boot) and add support to ATA , log on automatically
Am I correct? Because I dont know what is wrong

---

### Post by ajgreeny on 2015-03-15
No need to reformat as fat32; just make sure everything on sdc is backedup and you can then choose to delete all the partitions on sdc when you get to the **Something Else** part of installing, then make the new ones you want.

Your suggestion of 4 partitions ( /boot 0.5GB, /root 20Gb, / home 30GB, /swap 6GB) is not ideal, in my opinion.

Firstly I would strongly recommend that you **do not use a separate /boot partition** as it adds complications that are not needed, unless you use LVM or encryption when you must have separate /boot.

20GB for root is fine and I would go with that using an ext4 partition and mountpoint set as /.

6GB of swap may be too much; how much ram do you have? There used to be a general rule of thumb that you needed up to twice the amount of swap as you had ram; that is now largely defunct with most machines having plenty of ram.  Now I suggest a maximum of 2 - 4GB swap even on machines with plenty of ram.  If you want to hibernate, which will have to be re-enabled, you need at least as much swap as you have ram, or it will always fail.

Once you have an appropriate amount of swap, all the remaining space can be used as the /home partition, again using ext4 partition and mountpoint /home.

I hope this is a help but come back with further queries if you need to.

---

