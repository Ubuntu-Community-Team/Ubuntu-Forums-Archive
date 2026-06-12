---
title: "trying to reinstall ubuntu 18 without losing data"
date: 2018-09-09
forum: Installation &amp; Upgrades
---

### Post by elsuzu on 2018-09-09
hey guys!
after a failed attempt to update my ubuntu 16 to the newest 18 (would get stuck in command line and ubuntu wouldn’t boot) i‘m trying to reinstall without any data lost. i used an online how-to and stumbled upon a few problems.

first the installation dvd asked if i wanted to use the bios or uefi mode. i chose bios after some googling. now i mounted the ubuntu partition with / and changed nothing else and wanted to start the installation. it warned me that the reserved BIOS boot area is needed, i should make a partition at least 1 MB big. what should i do now? i backed my most important data but would like to keep the not other data as well. and do i need to use the other partitions? (fat32, swap) because they‘d be unused if i don‘t chose them. 

i tried in uefi-mode and it said something about the partition mounted in / might be formatted or something. i just want to get my computer back :( any ideas?

---

### Post by yancek on 2018-09-09
Your post refers only to Ubuntu so answers will assume no other OS installed, correct?

> first the installation dvd asked if i wanted to use the bios or uefi mode

Why did you choose BIOS over UEFI?  THe message about  a reserved BIOS area needed is because you are using GPT and not using EFI.  Would not be necessary on an EFI system.

You mention a FAT32 partition so do you have some windows installed?  Is that an EFI partition?  I would suggest you read the Ubuntu documentation at their page below, at least the first part if you are not dual booting with windows.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If reading the above does not help resolve the issue, you will need to post more info.  Do an online search for "boot repair ubuntu" and go to the site and download and run it selecting the option to Create BootInfo Summary and definitely do NOT try any repairs.  When it finishes, it will give you a link which you can post here for others to view.

---

### Post by elsuzu on 2018-09-09
thanks for your reply! i never had any windows installed on the laptop, it was always ubuntu. 
i chose BIOS because i read on some links that it was the better choice, but i tried again with UEFI. 

when i try it in UEFI, mounting my ubuntu partition in / it says: the file system on /dev/sda2 assigned to / has not been marked for formatting. directories contakning system files (/etc, /lib,...) that already exist under any defined mountpoint will be deleted dring the install. please ensure that you habe backed up any critical data before installing. 

that doesn‘t sound good. 

i can‘t go on the site you mentioned and download anything because i‘m kinda stuck in command line when i start the computer (i‘m writing this on my phone so please excuse any typos :) )

---

### Post by elsuzu on 2018-09-09
also, in UEFI there‘s partitions efi in drive /dev/sda1, ext4 (this is the one where ubuntu is installed) in /dev/, and swap in /dev/sda3. /dev/sda is nameless as are two free spaces. don‘t know if this info helps.

---

### Post by elsuzu on 2018-09-09
[https://ibb.co/esy3FU](https://ibb.co/esy3FU)
this is where i‘m at now. i‘ve read somewhere that i‘m supposed to just agree with the warning i posted above, do you agree?

---

### Post by SeijiSensei on 2018-09-09
It's asking if you want to accept the partition layout and write the boot loader record to the hard drive.  You need to agree to move forward.

---

### Post by elsuzu on 2018-09-09
thanks so much, guys! it worked and all my files are still there :)

---

