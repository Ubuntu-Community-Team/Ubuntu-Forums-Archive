---
title: "Stuck on UEFI Bios screen after new install of Mythbuntu 14.04 LTS"
date: 2014-06-09
forum: Installation &amp; Upgrades
---

### Post by gabriel23 on 2014-06-09
I recently put together a new HTPC. Here are the components:

CPU: AMD Athlon 5350 APU
Mobo: Asus AM1M-A
Memory: G. Skill Eco Series (2x2GB) 240-Pin DDR3 SDRAM 1333 (PC3 10666) [F3-10666CL8D-4GBECO]
PSU: Seasonic 80 Plus Bronze SS-350ET 350W
Case: Silverstone TJ08B-EW
Hard Drive: [COLOR=#1B4D88][FONT=arial][COLOR=#222222]WD[/COLOR] [/FONT][/COLOR][COLOR=#010101][FONT=arial]WEWD30EFRX [/FONT][/COLOR][COLOR=#010101][FONT=arial]3 TB [/FONT][/COLOR][FONT=arial]WD[/FONT][COLOR=#010101][FONT=arial] [/FONT][/COLOR][FONT=arial]Red[/FONT][COLOR=#010101][FONT=arial] SATA 3.5" NAS Hard Drive [/FONT][/COLOR]

After installing using a Live CD of Mythbuntu, I restart, and then I get taken to the ASUS UEFI Bios screen. From there, I manually select to boot from the hard drive, the screen goes black, and then I get taken back to the ASUS UEFI Bios screen. If you try to boot again from the hard drive, you get taken back to the UEFI Bios screen. I also tried a installing a from a  live Cd of Ubuntu 14.40 LTS and I get the same result with the endless loop with the UEFI Bios. I changed the Bios settings for boot, from secure boot enabled to disabled by enabling CSM and deleting the keys and selecting Other OS and I get the same result. I tried the hard drive in another PC (AMD A10-5700 with Asus F2A85-V Pro FMS) and Mythbuntu boots without an issue. Note, before going into the Bios, I do get one beep from the post.

I've been playing around with the different choices offered in CSM to no avail. It seems like I need to find out if there is an issue with my motherboard. If I'm able to run the "Try" feature of the live CD, can I rule out all the other hardware components? I'm thinking of either buying a different mobo or trying to install a copy of windows XP to see if that works. Or should I try a different distribution of linux? 

Any suggestions?

---

### Post by oldfred on 2014-06-09
If it is a 3TB drive, you cannot use XP. The large drive required gpt partitioning.

If you install in CSM/BIOS mode you should have a bios_grub partition, or if you install in UEFI boot mode then you should have an efi partition as the first or near beginning of the drive.

Best to see details, post link to BootInfo report. You can just install into the live mode version you used to install.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by gabriel23 on 2014-06-11
After running the boot repair from the live CD, my issues were solved. Thank you!

---

### Post by oldfred on 2014-06-11
Glad that worked, you can change thread to solved.

---

