---
title: "managing partitions to put 20.04 on Intel Compute Stick?"
date: 2020-04-29
forum: Installation &amp; Upgrades
---

### Post by anotherChris on 2020-04-29
I am trying to put Lubuntu 20.04 on an Intel Compute Stick STCK1A8LFC  (1.33 GHz Atom Z3735F, 1 GB of RAM and 8 GB of storage), and I have 3 questions as described below...

I think this installation should work because Lubuntu 19.04 was successfully installed on the same device, as described here: 
[https://forums.intel.com/s/question/0D50P00004JhY4qSAF/compute-stick-stck1a8lfc-is-running-ubuntu-1904-and-now-1910-well?language=en_US](https://forums.intel.com/s/question/0D50P00004JhY4qSAF/compute-stick-stck1a8lfc-is-running-ubuntu-1904-and-now-1910-well?language=en_US)
Following that plan, I have attached a powered USB hub to the Compute Stick and attached my keyboard/mouse, USB with 20.04 iso image, and USB with 20GB free storage space.

I have already booted from the USB and am running Lubuntu 20.04 on the Compute Stick now.  I started the 20.04 installer, but only made it to the section about partitions.  The 20.04 installer is not giving me the option to erase the entire disk, only the manual partition option.  As shown below (see photo), the Compute Stick has 4 partitions: FAT16 space, FAT32 space, Ubuntu 14.04 OS, and swap space.   I stopped at the next step, asking me if I want to create a new partition table (see photo) because I don't know what will happen if I click OK.  

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=285672&d=1588146220[/IMG]

My three questions:

(1) If I click OK at the stage shown in the image above, will it create a new partition table and erase the disk immediately, or will I still have the option to cancel installation without having erased the disk?

(2) Is it okay to erase and/or size-reduce the FAT16, FAT32, and swap partitions so there is (hopefully) enough space to install the Lubuntu 20.04 OS?   (I kind of understand what FAT16&32 are, but I don't know if it is important for these partitions to be on the Compute Stick for it to work properly... if I reduce them to negligible size, can I just a USB or SD for storage in the future?)

(3) If I am going to go ahead and click OK at the stage above, which kind of partition table should I create (see photo)?

Thank you very much.

---

### Post by anotherChris on 2020-04-29
Well, I've learned a little by reading on the web.  I need to go with the GPT type of partition, I think.  Also, it looks like I need a 512 MB partition at the beginning for EFI.   If anyone can give me more info, please go ahead.  I really don't know anything about building computer, hard drives, partitions, etc.

---

### Post by ubfan1 on 2020-04-30
You probably only need a 50M EFI partition, not 512M.  Keep a swap (935M on mine), and the rest root.  BUT far better to experiment with putting the install onto a microSD, of 8G or better 16G+.

---

### Post by anotherChris on 2020-04-30
Thanks for your reply. 

> **ubfan1 said:**
> You probably only need a 50M EFI partition, not 512M. 

Are you sure, because I read that 512 is needed.  But again, I am not knowledgeable, and I am finding that learning enough about hard drive architecture to be able to answer questions myself is difficult!


 > **ubfan1 said:**
> Keep a swap (935M on mine), and the rest root.  

OK, but I don't *need* the swap, right?   Also, can't I add swap space after the install?  (Also, another question I haven't been able to answer myself yet--can I put swap space on a USB device, like a memory stick?)


> **ubfan1 said:**
> BUT far better to experiment with putting the install onto a microSD, of 8G or better 16G+.

2 issues with that: (1) I read some places where other people discussed that and it sounds like it results in worse performance; (2) I live in Japan, and the Amazon Fire Sticks are all temporarily out stock.  The Intel Compute Stick was supposed to be an alternative to the Amazon Fire Stick.  I got it for about $45, so it was basically the same as the 4K Fire Stick would have been.  But if I have to start buying $20 per pop micro-SD cards, the price of the Compute Stick is going to go up.

---

### Post by ubfan1 on 2020-04-30
Your FAT16 at 47.7M is the current EFI partition, populated with grub and shim bootloaders., so would probably work if you just edit the /boot/efi/EFI/ubuntu/grub.cfg file to the new UUID of your new root, and probably the device/partition.
With 1G memory, you certainly will need swap for even Lubuntu.  Look at the existing 14.04 compressed swap setup and use that on your new system. Add the equivalent to the /etc/default/grub: ...intel_idle.max_cstate=1 zswap.enabled=1 zswap.compressor=lz4 quiet splash $vt_handoff
You will not find swap on USB2 fast enough, but in an emergency, can be used (like in setting up the system).  Swap on a microSD might be fast enough, but I have use the internal swap partiiion even when running the root off a microSD.
Any kernel 4.19 or later should provide full functionality, wireless, bluetooth, and HDMI sound.
After the EFI ans swap, the remaining root space (assuming all remaining) may be too small for the installer to accept -- you can try and edit the space check out, or install to a big enough microSD and copy the resultant install to the internal partition (adjusting any UUIDs as necessary in /etc/fstab).
I have not tried Lubuntu 20.04 desktop on the ICS, but Ubutnu 20.04 server runs nicely off an 8G microSD.  Debian 10 did fit onto the stick and runs OK, but might have used a USB swap and a copy of the install off a microSD.
Memory is the real bottleneck on the ICS, so what I find works best for me as a general computer is Antix19 using ICEwm/Rox.
The existing Ubuntu 14,04 install with unity!) runs amazingly well, better than the later ..buntus.
Your second partiton, the FAT32, is the recovery partition for reinstalling the Ubuntu 14.04. (third is root, fourth is swap).  Keep the 1 &4, making rest into a bigger partition for your new root.  The ICS is a full secure-boot capable, UEFI 64 bit quad core machine, but with limited resources.

---

### Post by anotherChris on 2020-04-30
> **ubfan1 said:**
> The existing Ubuntu 14,04 install with unity!) runs amazingly well, 

Yes, I was surprised.  I was having an issue with Wi-Fi, but based on reading on the web, I think it was not to do with Ubuntu.  I would have just kept 14.04 but the applications are too old.  To make it into a media device, need updated browser.

> **ubfan1 said:**
> better than the later ..buntus..

Sorry to hear that.

I have some free time right now and so does the TV, so will try to install 20.04.  If it doesn't work, maybe I'll try Debian 10.  I've never used any Linux OS except Lubuntu, and I have also considered myself stupid and ignorant about computers and pushing my luck with using Lubuntu.  But maybe I should try another OS.

Thanks for all your advice and help!!!

---

### Post by ubfan1 on 2020-04-30
Take a look at:
[https://askubuntu.com/questions/1170053/i-did-a-newbie-mistake-and-trashed-my-stick-computer/1170684#1170684](https://askubuntu.com/questions/1170053/i-did-a-newbie-mistake-and-trashed-my-stick-computer/1170684#1170684)
Flashing the BIOS/firmware is really important, many issues have been fixed.  Get the latest from Intel, put the file on a FAT USB, and select flash at boot time -- pretty easy.

---

### Post by anotherChris on 2020-05-01
> **ubfan1 said:**
> Take a look at:
[https://askubuntu.com/questions/1170053/i-did-a-newbie-mistake-and-trashed-my-stick-computer/1170684#1170684](https://askubuntu.com/questions/1170053/i-did-a-newbie-mistake-and-trashed-my-stick-computer/1170684#1170684)
Flashing the BIOS/firmware is really important, many issues have been fixed.  Get the latest from Intel, put the file on a FAT USB, and select flash at boot time -- pretty easy.

Thanks.  I've seen that before because my original idea was to just fix the Wi-Fi, and I was looking for a way to do it.  

Anyway, guess what?  It's all working now!!  With your help, I guess I understood partitioning enough to do the right thing, and now my wife is watching *Leon: The Professional* from Amazon Prime on our new Lubuntu 20.04 stick computer!!

I created 3 partitions: 

(1) a 100 MB FAT32 partition mounted at **/boot/efi** and tagged "boot"

(*Even though you said 50MB was enough, I found somewhere on an official Ubuntu.com page that EFI boot partition should be minimum 100.  I suspect 50 would have worked, but, well, it's done now..*.)

(2) a 6500 MB ext4 partition mounted at **/ **

(3) the remainder a linux swap partition without a mount point and tagged "swap"

My plan was just to see what happened when I did that.  I thought the installation would fail, but actually it worked.  The installer took about 15 minutes to finish.   It made me wonder... how small could the ext4 partition have been...?  Do you think I would get better performance if I re-installed with a larger swap space?  Also, do you think I would get better performance with Debian 10?

Without making any changes, the Wi-Fi is now working much better than with 14.04.  In fact, web pages seem to load faster on the Compute Stick than on my Dell Inspiron 1545 laptop  (also running Lubuntu 20.04).  I did have to re-start one time so far because YouTube videos stopped loading (YouTube showed me a message that said I should re-start), but right now my wife is about 40 minutes in to *The Professional* and there have been no interruptions in the video streaming.   So, maybe I will try to update the BIOS, but maybe I shouldn't press my luck...?

I am confused about the structure of the Compute Stick as it came out of the box.  I posted [a question about its architecture at SuperUser ]("https://superuser.com/questions/1547559/why-did-my-computer-come-with-fat16-partition-for-efi-boot")if you're interested in following that...

Thanks again so much for your help!!!

---

