---
title: "can not install 12.4 x64 lts on a lenovo z585"
date: 2013-08-01
forum: Installation &amp; Upgrades
---

### Post by stuart_hall2 on 2013-08-01
[h=2]can not install 12.4 x64 lts on a lenovo z585[/h] 		 				 					 					 				 				 		 			 				[INDENT] 					wasn't able to install 12.4x64 would not load any version (didn't give any errors msgs)(tried a few other versions no luck)
  however it did load a old 9.10x32 and then started upgrade to 10.4 x32 LTS do you think I can  then install the 12.4x64 version from there? 
Have never had this type of problem  before. but haven't used a x64 format. the lenovo z584 has 958 hd 6 gig  mem.  came with win8x64 :sad:  				posted also on beginers no help there
[/INDENT]

---

### Post by dino99 on 2013-08-01
maybe you need to bypass acpi or else, using the boot option : [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

note: avoid posting several times the same thread

---

### Post by oldfred on 2013-08-02
If your system had Windows 8 pre-installed it is the new UEFI which is a lot different than the old BIOS with MBR partitioning. I am surprised you even got 9.10 to even install as I did not think it had the gpt partitioning tools.

Best to see where you are at. But it is a lot more complicated particularly if your system is an Ultrabook. Please review the link and many of the links in that link in my signature to understand UEFI. Its a lot.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

