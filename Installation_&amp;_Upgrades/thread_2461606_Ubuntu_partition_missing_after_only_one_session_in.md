---
title: "Ubuntu partition missing after only one session in Windows 10"
date: 2021-05-04
forum: Installation &amp; Upgrades
---

### Post by linorion on 2021-05-04
Hello,
I had 2 partitions in my computer with dual boot: the default one with windows 10 and other with ubuntu (version 20.04.2). I used the windows partition only the first day with the purpose of download the ISO of ubuntu and configure the installation usb. Since then, I only worked on my ubuntu partition. Today, I tried to enter Windows and all looked aparently ok, but after I restarted the PC, the windows login screen appeared directly (and not the dual boot startup with windows and ubuntu options, as always). 
When I check the partition list in windows, the ubuntu one does not exist (now it only appears a space not assigned). I tried to access that partition from the pc bios and I have only the windows boot option.

Furthermore, I followed the steps written here: [https://superuser.com/questions/1289741/dual-boot-ubuntu-disappeared](https://superuser.com/questions/1289741/dual-boot-ubuntu-disappeared) and, when I tried to run boot-repair in the linux trial mode, an error message was displayed and advice me to copy the following link: [https://paste.ubuntu.com/p/xJky2JMxQj/](https://paste.ubuntu.com/p/xJky2JMxQj/) and share it in this forum.


I had lot of info, programs, etc in my ubuntu partition and I hope everything continues well. I want to recover it all and avoid this issue in the future, what can I do?

Thank you in advance for giving me your help

---

### Post by yancek on 2021-05-04
Lines 10-17 in boot repair show the EFI files.  Note there are "none" for Ubuntu!   Lines 49-54 show where (the partition) Ubuntu is/was installed.  Looks like it says the mount point is already occupied or in use?  Line 89 in boot repair shows an EFI entry for ubuntu (Boot 0002), can you select that from the BIOS boot options?  If so, what happens?  Can you set that option first in the BIOS boot priority options.  Did you make any changes while booted into windows are did an update run?  Did you use the Ubuntu documentation at the link below to dual boot windows 10 and Ubuntu?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by linorion on 2021-05-04
Hi yancek, thank you for your response.
When I acces the BIOS, the only boot option available is trough windows, so I can not change any priority order :(
However, you asked me if I made any changes or updates. I suppose that you are talking about the windows partition and yes, that time I entered only one minute there, windows update facilities worked during shutting down process... I read somewhere that windows can overwrite other partitions while it's making its own updates, maybe the issue came from that way #-o

---

### Post by linorion on 2021-05-04
Hello again,
**I have already solved the issue!** \\:D/ There is something important that I do not understand yet (but it worked, anyway). Let me present the things that I have done, hope this helps to the possible reader.

**1)** First of all, **in the Windows partition, download the Ubuntu ISO** (with the exactly **same version as the previous Ubuntu partition** that flew out).
**2) **Now, if it is possible, **take the same USB that was used in the original Ubuntu installation and create a bootable USB.**
**3)** Shut down the PC and **enter the PC BIOS** during its restart.
**4) **From BIOS, **boot the USB option** that should be displayed and enter in the ***Ubuntu option boot**.
**5)** After some system checks (and if everything went OK), choose **"Try Ubuntu" **on the windows that appear on screen.
**6)** **Open a terminal and run Boot-Repair**. You can find how in several places, but I will write the console commands here too:
                      sudo add-apt-repository -y ppa:yannubuntu/boot-repair
          sudo apt-get update
          sudo apt-get install -y boot-repair && boot-repair
**7)** A new window should be displayed with the **"Recommended repair option"**, click on that button and wait. Follow the instructions that appear on screen from now.

It was at this last point that I had errors and the boot-repair could not complete the process, displaying the error output that I presented at the beginning of this thread. The difference here is, when I did this the first time I used a different USB from the one that I used in the original installation of Ubuntu. I don't know how can this be relevant... But for me worked!

Regards and good luck if you are still searching for more help!

---

