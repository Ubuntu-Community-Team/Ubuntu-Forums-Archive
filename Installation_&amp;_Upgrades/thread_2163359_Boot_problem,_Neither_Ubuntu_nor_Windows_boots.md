---
title: "Boot problem, Neither Ubuntu nor Windows boots"
date: 2013-07-18
forum: Installation &amp; Upgrades
---

### Post by mzubair01 on 2013-07-18
I bought a new laptop with Windows 8 pre-installed and I  tried to make it dual boot like my windows vista laptop with Ubuntu.  Turns out because of some boot sector changes its really complicated  now!
  Ubuntu installed fine, but it wouldn't boot up windows anymore. After reading a new threads on here about people with the same problem, I Installed and ran the Boot repair software ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) 
  After going through the instructions, I rebooted my computer and it gave me a "Grub Rescue" screen saying 
  [HTML] error: invalid arch independent ELF magic.  grub rescue> [/HTML]  I am running Ubuntu from the live cd now...and have tried to fix that problem by running
  
sudo mount /dev/sda1 /mnt  sudo grub-install --root-directory=/mnt /dev/sda   This ended up booting in the "grub" window where it allows me to type some rudimentary commands.

  Can anyone help me fix my computer and get back to 1. Ubuntu booting up! 2. Dual boot with my windows which is still installed


  Here is the pastebin that Boot-repair gave me to write down after the installation: [http://paste.ubuntu.com/5835513](http://paste.ubuntu.com/5835513) 
      


I've been running the ubuntu live cd for almost a month now! Please help! I need both windows and ubuntu on my computer because I use both for different purposes!

---

### Post by p-dh on 2013-07-18
Looking through your boot repair report, I believe that you should have typed:
sudo mount /dev/sda***6*** /mnt
This will point the files to the /boot/grub directory, which is on sda6.
Is this the partition that you chose when you ran boot-repair? It will show every partition where you have an OS installed, but you need to pick the right one. You may want to run boot-repair again and choose /dev/sda6.

Peace,
Paul :cool:

---

### Post by oldfred on 2013-07-18
You have Windows in UEFI and really need Ubuntu in UEFI to easily dual boot. But it looks like at least initially you installed grub in BIOS mode not UEFI mode.
You also converted an essential but mostly hidden Windows partition to the bios_grub partition. If booting Ubuntu in BIOS mode you need the bios-grub partition but it only need to be 1MB. You need to convert sda3 back to the Windows system reserved partition for Windows to work in UEFI mode.
       Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)


 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)

Boot-Repair should be able to convert a BIOS install to UEFI install for Ubuntu by uninstalling grub-pc and installing grub-efi. But does your computer boot with secure boot off? Some only boot with it on, others work either way. Ubuntu does have the Microsoft signed key in its grub shim file and signed kernels and Boot-Repair will install those if you boot Boot-Repair in UEFI secure boot mode.

---

### Post by mzubair01 on 2013-07-18
> **oldfred said:**
> You have Windows in UEFI and really need Ubuntu in UEFI to easily dual boot. But it looks like at least initially you installed grub in BIOS mode not UEFI mode.
You also converted an essential but mostly hidden Windows partition to the bios_grub partition. If booting Ubuntu in BIOS mode you need the bios-grub partition but it only need to be 1MB. You need to convert sda3 back to the Windows system reserved partition for Windows to work in UEFI mode.
       Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)


 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)

Boot-Repair should be able to convert a BIOS install to UEFI install for Ubuntu by uninstalling grub-pc and installing grub-efi. But does your computer boot with secure boot off? Some only boot with it on, others work either way. Ubuntu does have the Microsoft signed key in its grub shim file and signed kernels and Boot-Repair will install those if you boot Boot-Repair in UEFI secure boot mode.


Thanks for the reply fred
How would i convert sd3 back to windows system reserved parition?

I was able to boot ubuntu now after turning to UEFI mode with secure boot disabled (had to set a supervisor password before it let me disable the secure boot) 
With secure boot it wouldn't boot anything (not even the cd) and gave me warnings that the security policy didn't allow the harddisk or the boot manager or the cd rom to run

---

### Post by oldfred on 2013-07-18
I was not sure if gparted had that option or not, but it does. You can also use Windows tools. You should have a Windows repair flash drive to make those type of repairs.
If you go into gparted choose sda3 and right click to manage flags. Assign the msftres flag. Do not format that partition as it must be unformatted.

Not sure if Windows will boot with secure boot off or not. You will just have to experiment. If Windows only boots with secure boot on then you have to convert Ubuntu to secure boot also.

 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

