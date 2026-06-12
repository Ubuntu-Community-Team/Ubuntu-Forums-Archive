---
title: "linux mint (ubuntu) won't boot"
date: 2015-11-12
forum: MINT
---

### Post by ramez2 on 2015-11-12
Hi all, 
Thanks for the welcome message :) 

I'm having a problem with my Sony Vaio pro 13" touch. I first tried installing ubuntu Mate by choosing erase disk and install.. but the didn't boot the system. I'm now trying to use Mint Mate and it didn't help either. So I used Boot-Repair and it gave me this address [http://paste2.org/Cmt3WwWU](http://paste2.org/Cmt3WwWU) . A little background on the issue, I completely erased my SSD drive after the first installation failure, also, I have a surface pro with win 10, so I decided to have a full linux laptop (the Vaio). I'm not new to linux, been using it partly at home and at Uni for almost 10 years now. But I must confess that I kept it to the GUI stuff and not so much termal/scripting stuff. I tried installing with EFI enabled/disabled, secure boot enabled/disabled, nothing worked and I'm going crazy here :/. I'm not really sure if I should be posting this here or in linux mint forums. But Boot-Repair's webpage directed me here, Also I'm thinking this problem is at the core of the system which is still Ubuntu. 

Thanks in advance!

---

### Post by howefield on 2015-11-12
Thread moved to the "*MINT*" sub forum.

---

### Post by yancek on 2015-11-12
You don't have any code in the MBR which is correct for a UEFI install.  You have the EFI partition with the correct files for Ubuntu, not sure if Mint uses the same files, might?
You also have windows files in the EFI partition but there is no sign of any windows on the disk??  Should there be?

---

### Post by ramez2 on 2015-11-13
Hi,
No there should not be any windows or anything on the drive for that matter, I did a hard erase or the SSD. I actually managed to solve the problem following this document [http://www.slideshare.net/slideshow/embed_code/27418512](http://www.slideshare.net/slideshow/embed_code/27418512) . Apparently Vaio Will always try to boot into windows even if you have grub-efi installed. 

For someone who may have the say problem (my guess would be other newer vaio models), Just follow the instructions in the link above. It also work with a single boot (only linux) mode.  

I have one question to the veterans in here before I close this thread:

During installation I got a message the rEFInd, I got an error saying that it didn't install correctly. But I continued anyway. Also, in step [J] in the document, cp ./dirvers_x64 didn't work. It didn't find such directory. But I continued anyway. And the laptop boots fine, first it boots into rEFInd graphical menu and then by choosing grub, it boot into linux. 

My question is considering the errors mentioned, should I be worried about future consequences like boot failures?

 Cheers!

---

