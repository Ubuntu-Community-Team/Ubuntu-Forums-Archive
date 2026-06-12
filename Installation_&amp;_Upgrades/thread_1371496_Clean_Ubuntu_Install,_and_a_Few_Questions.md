---
title: "Clean Ubuntu Install, and a Few Questions"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by izz.y on 2010-01-03
Currently I am running Ubuntu 9.04 on my computer, and it is the only OS installed. I purchased the $30 student WIn7 Professional upgrade. I have a XP Pro CD + Key, and I plan on using that just to upgrade to Win7. I love Ubuntu and it is my primary OS, it is just that every now and then you come across some program that requires windows (Propellerhead Reason 4, Adobe Photoshop CS4, Atomix Virtual DJ etc.) and it requires full system resorces so you do not want to use wine. I love Linux, but somtimes I just have to use WIndows, so I do not want to hear any arguments about that.

HERE'S THE DEAL:

I want to do a clean install of everything, and I have data + programs backed up, I would like to install Ubuntu 9.10, WinXP Pro and I want to Upgrade XP Pro to 7. I am completely new to GRUB 2, and upgrading windows; but I have experience with Linux and Windows, and dual booting. I would like to install Ubuntu 9.10 on its own partition (No WUBI), and WInXP + Win 7 on there own partitions (3 Partitions Overall). I would like to know what to do at this point, Should I install Ubuntu then Xp then 7, Xp then 7 then Ubuntu, etc. I know how to make Partitions, I just need to know the order in which I should install the operating systems, and how to get it to dual boot.


MY COMPUTER:

I had a Sony Vaio PCV-RS530G, and the mobo failed, so I rebuilt it, the case, processor, fans, CD/Floppy drives, TV tuner and power supply are unchanged, everyhing else has been replaced, here is the breakdown:

Proecessor:                Intel Pentium 4 3.20 GHZ, HT Technology, No 64-Bit or VT-x
Motherboard:             Biostar P4M900-M4
Hard Disk Drive:        Seagate 1TB SATA (IDE Mode, no RAID)
Graphics Card:           Nvidia GeForce 8400 GS, PCI Express, 512 MB RAM
RAM:                         2 GB Corsair, DDR2-5300


QUICK QUESTIONS:

I had a few quick questions, I would really appreciate it if someone could answer these:

1) How can I install all the screen savers that were in Jaunty, but are missing in karmic?

2) Can Win7 be installed without a key, and then have the key entered later (I AM NOT PIRATING, I JUST WANT TO PUT THE KEY IN AND ACTIVATE AFTER I CAN TEST OUT EVERYTHING AND MAKE SURE THAT WINDOWS AND UBUNTU ARE RUNNING SMOOTHLY)

3) Will XP mode in Win7 work on a processor without virtualization technology?

4) I have Icon sets, cursors, window borders, and panel backgrounds from different     sources, can I export this as a complete theme in 1 file (Deb Packages are preferable, but even a tar-ball is fine) so I can install it easily on more machines, and share it with friends?

5) How do you  use native windows DLLs in WINE?

6) My PC has a tv tuner, how do I use it in Ubuntu?

7) What is a good size for a swap partition for my computer (Detailed information below)?

---

### Post by izz.y on 2010-01-03
If you have experience with this issue, please answer the poll above, I am on vacation right now, so I will install Ubuntu and Windows on the 16/17 of January, so the Poll closes on the 13th. Unless a good answer is given, then I will install according to the results of the poll.

---

### Post by J V on 2010-01-03
Wine
Is
Not an
Emulator

And as such, it sacrifices compatibility for native speed: it will run at windows speed or even better.

**Installation:** Windows will *destroy* any other operating system, thats the way they made it...

First format some partitions, windows will require primary partitions, but linux should be put on an extended (for reasons I will explain shortly)

Install XP, Install 7, and install linux in the extended...

During install you will want to specify 3 logical partitions underneath the extended for linux.

The first, about twice your RAM size, will be a SWAP partition
The second at about 8 - 10 Gb you will mount at /
The third you will use the rest of the space for and mount at /home

This lets you install a different linux OS (Or fresh upgrade to the next version) without having to backup your data (Its all kept on its own partition) and you can share /home data between OS...



All windows I know of could be activated after install, but Microsoft has been getting arrogant, and you might need it ready...

Windows 7 squeezes more money out of you... unless you buy professional or higher it won't run XP or older programs (Wine for windows? yay!)

(Finding out this next one crashed firefox... yay... more typing...)
Just hit save as in the appearances window and you should save most of it, just tar the rest yourself, can't take long...

You should never use windows DLLs in wine... NEVER!

Tv tuners have always been trouble, use google, methinks you just open up a movie player...

Hope that answered them...

---

### Post by raymondh on 2010-01-03
Similar to JV's response ... my thoughts


- Create the partitions beforehand. 
- install XP and update
- install win7 and update
- install ubuntu

or,

Create 2 partitions (both NTFS) and make the second one bigger
Install XP in the smaller partition and update
Install win7 in the bigger partition and update.
Defrag the win7 partition
Shrink the win7 to make space for ubuntu
Install Ubuntu in the 'largest continuous free space'.

Regards,

Raymond

---

### Post by Mahngiel on 2010-01-03
An amendment to these gents:

You may want to create a 'Storage' area that is accessible to all 3 of your Operating Systems.  This will be for things you download, music, photos, etc.  Create it as part of your extended partition as NTFS, which is readable by both windows and linux, and you're not restrained by a max file size of 6 GB.

---

### Post by izz.y on 2010-01-04
Thanks a lot for the advice, I purchased the student upgrade of Win7 professional (only 30 USD), Ubuntu is my primary OS, so I do not care about shared space, I will just use Windows 7 every now and then for some high resource programs like Adobe Photoshop (It beats gimp, for now at least), and Propellerhead Reason 4. Anyway I am really eager to know how I can get the Ubuntu 9.04 screen-savers, and can someone please give me detailed tutorial on how to export the current theme.

---

