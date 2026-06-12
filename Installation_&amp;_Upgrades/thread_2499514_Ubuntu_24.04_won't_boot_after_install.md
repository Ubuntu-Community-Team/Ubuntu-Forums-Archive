---
title: "Ubuntu 24.04 won't boot after install"
date: 2024-07-30
forum: Installation &amp; Upgrades
---

### Post by baubetrieb on 2024-07-30
Hello everyone, 

I had already made a post about my problem [here]("https://help.ubuntu.com/community/BootPartition") but marked that thread as solved since I was able to boot Ubuntu 24.04. But after I installed a software update yesterday, the boot menu won't recognize Ubuntu on my drive again. (Same settings as the working boot)


**System specs** (PC I got for free, so no further information)

I plan to only run Ubuntu.

boot menu says ASUS UEFI BIOS Utility and the BIOS version is listed as 0806 x64 and Build Date as 01/20/2014


CPU: Intel Core i5-4570 @ 3.2 GHz
GPU: Some Palit Graphics Card I can't seem to find the model of, but I plan on removing it anyways
RAM: 24 GB (DDR3) @ 1.6 GHz
HDD: 2 TB (WDC WD20EFRX-68EUZN0)
SSD: 250 GB (Samsung Evo 840)



Naturally I followed the helpful answers to my last post, but it still wouldn't boot from the 2TB drive.
Fed up with everything, I decided to 

1) completely format both my drives while in a live session after selecting 'try or install ubuntu' on UEFI boot from a USB. I then used the installer to install ubuntu on the 2TB disk (selected 'erase disk and install ubuntu'). I restarted the pc as prompted, removed the installation medium when asked and it still didn't recognize the installed OS. I had fast boot and secure boot disabled.

2) restarted the PC again with my USB in it to go back to a live session to use the boot-repair tool. I selected to do recommended repairs.

3) After completing them, the program prompted me with a short report and also said to create a seperate /boot partition via [this guide]("https://help.ubuntu.com/community/BootPartition"), since the boot files where to far from the start of the disk and BIOS might not detect ubuntu because of it. So I followed the guide and it still didn't work.


Disappointed, I redid steps 1) and 2) and just asked boot-repair to paste the report: [https://paste.ubuntu.com/p/mmKmp2PjKw/](https://paste.ubuntu.com/p/mmKmp2PjKw/)

For step 3) I wasn't certain where exactly to create the /boot partition, so I created it between /dev/sda1 and /dev/sda2 ([picture ]("https://imgur.com/a/hKIxDyF")[IMG]https://imgur.com/a/hKIxDyF[/IMG]for reference). If you know details about why this did not work for me, I would be thankful for any advice.


Any help as to what I did wrong or should try will be greatly appreciated :)

---

### Post by baubetrieb on 2024-07-30
Thank you for your reply!

I did all of that except for step 4. I also tried the 2 TB drive as a boot override, but it didn't work either.
I'm gonna try to reinstall grub later, although it's my understanding that boot-repair already reinstalled it.

Since your answer seems to be somewhat general, I'm also gonna look out for a second one more specific to my issue.

---

### Post by tea for one on 2024-07-30
Your installation is in old-fashioned Legacy mode.
Was this a deliberate choice?

---

### Post by yancek on 2024-07-30
> 'try or install ubuntu' on UEFI boot from a USB 

The above statement from your initial post contradicts the output of boot repair which shows a Legacy/CSM install on a GPT drive.  Better to install UEFI as suggested above.  Do you have Legacy/CSM boot enabled in your BIOS firmware?  You do have the 2TB set to first boot priority in the BIOS, right?   On a Legacy install such as you have there is no need for a separate boot partition.  The reason it was suggested is because you did a Legacy install on a GPT drive with requires the unformatted 1MB partition for the Grub core.img file.  Reinstall by booting and installing in UEFI mode will be simpler.

---

### Post by baubetrieb on 2024-07-30
No it's not. Do you think it has something to do with the problem?

Someone in my last post said the manner in which I booted the USB (I chose UEFI) was the manner the OS would be installed. Maybe something went wrong here?

---

### Post by baubetrieb on 2024-07-30
Ok thank you yancek, I must have screwed something up then. The 2TB drive is first priority, yes. I'm gonna try once I get home and come back to you!

---

### Post by tea for one on 2024-07-30
You can double-check that you have booted the live install session into UEFI mode with this terminal command:-
```
redact@gmktec:~$ [ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
UEFI
redact@gmktec:~
```
Also, only have your target disk accessible to avoid any untoward errors.

---

### Post by baubetrieb on 2024-08-01
Thank you, everyone, for your help.

I updated my BIOS Firmware and could then boot Ubuntu in UEFI mode!

:)

---

