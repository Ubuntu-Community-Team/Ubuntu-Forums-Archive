---
title: "Ubuntu+windows dualboot final steps"
date: 2014-04-06
forum: Installation &amp; Upgrades
---

### Post by spacerocket on 2014-04-06
Hello!

I have system C(windows) 43Gt and unallocated space 68Gt. I want to install ubuntu 13.10 on that unallocated space. Should I proceed as follows:

1) Create from unallocated space 45000MB Exf4 journaling file system mount point /

2) Create from unallocated space swap area 6270 MB

3) Create partition for /boot maybe 300MB is enough? I should use this partition as ? (options swap, /boot, /home etc)

4) Maybe create /home partition do I need it? what size?

Thanks

---

### Post by oldfred on 2014-04-06
Most desktops do not need /boot as a separate partition. 
If using RAID or LVM or LVM with encryption on a full drive install you may need a /boot.

If allocating 68GB, I might do 20GB for / and your 6GB for swap and the rest for /home.
Or you can just have the entire amount as / (root) as that is not really large. It is those who do a default of / & swap into a new multi-TB drive that may have / way too large and need data partition(s) or /home so / is not too large.

But do you even need 6GB for swap? IF you have 4GB or more of RAM you may not need that much unless you hibernate and Ubuntu boots fast enough that hibernation does not save much if any boot time. If hibernating you need swap equal to RAM in GiB not GB or a bit more.
       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by spacerocket on 2014-04-06
Ok then I may use only 2000MB for swap and I don`t need /home. I may even allow 450000MB for /. But if I don`t create a separate /boot should the system automatically create windows+ubuntu bootloader? Now I don`t have bootloader at all, the system automatically directs me to windows7. 

Thanks for your time.

---

### Post by oldfred on 2014-04-06
If it auto boots Windows then you have a Windows boot loader.
If a BIOS based system, BIOS loads MBR or first sector of hard drive and it takes over boot. Since MBR is tiny, only one sector, it is just a bit of code to find more code elsewhere on drive.

Your Ubuntu install should put grub2's boot loader into the MBR and let you boot both Ubuntu & Windows. So not install grub boot loader to a partition.

If issues you can always repair you Windows with a Windows repair CD or flash drive which you should make before installing anything. Some Windows repairs can only be made with a Windows repair drive.
And you should make a full image backup of Windows just in case.

---

### Post by spacerocket on 2014-04-06
Ok Now I created 70847MB ext4 / on /dev/sda4 and swap area 1999MB on /dev/sda5. I had the first 3 as follows: /dev/sda1 efi 104MB used 33MB /dev/sda2 134 MB used: unknown /dev/sda3 ntfs 46946MB used:31MB. Free space: 0MB. 

Then I selected device for boot loader installation: /dev/sda ATA KINGSTON SV300s3 (120.0GB)  and after that installed ubuntu.

Then I restart my computer -> goes directly to windows.

If I press F11, I get a menu where is **UEFI: Build in efi shell** -> goes to windows  
                                                  **SATA2**:**KINGSTON** **SV00S37A120G -> **goes to windows
                                                  **Windows Boot Manager (P1:KINGSTON SV300S37A120G) **-> goes to windows
                                                  **TSSTcorpCDDVD** **SE-208DB TS02** -> this is probably for cd/dvd
                                                  **[COLOR=#ff0000]ubuntu (P1:KINGSTON SV300S37A120G) [/COLOR]**-> goes to boot loader where I can choose whether to go to ubuntu/windows. This is what I want
                                                  **[COLOR=#ff0000]ubuntu (P1:KINGSTON SV300S37A120G) [/COLOR]**-> goes to boot loader where I can choose whether to go to ubuntu/windows. This is what I want

Now my problem is that the system automatically goes for **UEFI: Build in efi shell **and I wasn`t able to find  **[COLOR=#ff0000]ubuntu (P1:KINGSTON SV300S37A120G) [/COLOR]**[COLOR=#000000]in bios boot option 2 (1 is for cd/dvd of course)

If you have any ideas they are welcome. Thanks for your time
[/COLOR]

---

### Post by oldfred on 2014-04-06
Is Windows in UEFI boot mode?

Why would you want a Ubuntu in BIOS boot mode from flash drive? But it still should work if you do not have secure boot on or UEFI only on.

You may have two entries for Ubuntu as one is grub and the other shim which is grub for signed or secure boot. I thought shim was to be the standard whether secure boot or not, but you have both.

---

### Post by mstutson on 2014-04-07
I think I follow but...I am in the same sutuation sort of. I have a Windows 7 and a previous attempt 12.04 load with a freash 13.10 desktop load. I have attempted to repair my windows/ubuntu system.

I installed and froze 3 or 4 times and force reboot, checked the Windows bios and it was ok.

Next attempt loaded with LVM I believe. Kept the drives that had windows configurations (fingers crossed). Used all available space for Ubuntu. Used windows to shrink the sda 1T drive to 49***MB. Used the remaining 43***MB for /
Used an unused spacw on sda1 135MB for swap. Used another drive for 252GB for /home and /var @120GB each with a 10GB swap.The Ubuntu boots and reboots but I get nothing else. I have loaded crome and witnessed Ubuntu work but I no longer have access to Windows. Although this does not break my hart since I am rinning my laptop only on ubuntu since I got it. I would like to fix my duel boot to windows.

Also please forgive me if I requested help in the wrong place because I used a post like my problem.

---

### Post by spacerocket on 2014-04-07
Yes it is (or was). Sorry. I went to mess up with BIOS settings first  disabled all boots then my computer won`t start/load anything. I don`t  know how to change them back. After adjusting now when I press F11 I get  a menu where is UEFI:Build in EFI shell. This is where the system goes  automatically.When I click this the system goes nowhere(please select  correct boot device and reboot). The second option is Ubuntu  (P1:KINGSTON SV3605..) and loads windows+ubuntu bootloader. 

Is it possible to get the windows+ubuntu bootloader to ** UEFI:Build in EFI shell**.  Then I don`t need to press F11. Or did I select wrong boot device when  installing ubuntu, should it be in /dev/sda2 ntfs where is windows so  the system would automatically load the correct bootloader?

Thanks for your time.

---

### Post by spacerocket on 2014-04-07
Ok now I disabled all UEFI and the system goes directly to the bootloader. Success! If  there is easier way to do this in the future without needing to mess up with BIOS can you tell me. Maybe from the installation?

Thanks

---

### Post by oldfred on 2014-04-07
It depends on what you want.

Ubuntu installer will install in either UEFI or BIOS boot mode if you have correct partitions on a gpt partitioned drive. And how you boot installer either UEFI or BIOS is then how it installs.

But if Windows is UEFI you have to have Ubuntu in UEFI to dual boot from grub menu. If both systems are not in same boot mode you can only boot from UEFI menu and may have to turn on/off UEFI or turn on/off BIOS to boot a system in that mode. Some auto switch or have a UEFI or BIOS Mode.

---

