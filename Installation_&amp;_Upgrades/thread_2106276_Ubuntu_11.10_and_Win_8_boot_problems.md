---
title: "Ubuntu 11.10 and Win 8 boot problems"
date: 2013-01-18
forum: Installation &amp; Upgrades
---

### Post by ashish0603 on 2013-01-18
Hi all,
I have a Lenovo ThinkPad with Windows 8 pre-installed. I am trying to install Ubuntu 11.10 on it. I did manage to install it, but there is a problem I am facing. The Grub doesn't load in the beginning, it directly boots into Windows8. So, using EasyBCD I just created a dual boot menu from Windows8, so that it halts for user intervention. Once it halts, if I press ESC twice, I get to see GRUB. Inside GRUB, I have option of Windows, but it doesn't find the physical partition, so I installed boot-repair. It doesn't work out. So, I created this log and you can find it here: [http://paste.ubuntu.com/1546284/](http://paste.ubuntu.com/1546284/)

Boot repair keeps saying that grub-efi purging failed. 
I would also like to tell that to install ubuntu, I created an empty partition from Win8 of about 40 GB. I then used a liveUSB and installed Ubuntu 11.10 64-bit on that partition using the 'Something else' option.

I am not sure, what went wrong, but it has something to do with the partition not being EFI. Please help me out guys. I am a newbie to Ubuntu..

Thanks,
Ashish

---

### Post by oldfred on 2013-01-18
It looks like you installed 11.10 in BIOS/MBR mode, but Windows is in UEFI/gpt mode. Both systems have to be installed in the same mode UEFI or BIOS. Each UEFI or BIOS write data to drive for system and each does it differently, so you cannot dual boot unless installed in same mode.

Windows 8 if pre-installed has the new UEFI setting of secure boot and currently only Ubuntu 12.10 has the capability to work with UEFI secure boot.

        The State Of Linux Distributions Handling Secure Boot
[http://www.phoronix.com/scan.php?page=news_item&px=MTI2MzI](http://www.phoronix.com/scan.php?page=news_item&px=MTI2MzI)
    
If you install 12.10 even in BIOS mode Boot-Repair can convert to UEFI mode, but with 11.10 the efi version will not work.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
       
 Some general info from oldfred and links.
[http://ubuntuforums.org/showthread.php?t=2086883](http://ubuntuforums.org/showthread.php?t=2086883)

     Is this also an Ultra-Book? Brand of computer does not really matter as it is Intel standard.
        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

---

### Post by ashish0603 on 2013-01-18
Thanks for your reply :D

Ya, I earlier had Ubuntu 12.10, but I needed 11.10 for some kernel assignments. I have heard that they work only on 11.10, hence I had to re-install 11.10. So, there is no feasible way of handling Ubuntu 11.10 and Win8 in EFI mode? Will a fresh install of 11.10 do any good?

---

### Post by oldfred on 2013-01-18
You may be able to boot it by going into UEF/BIOS and turn off UEFI and turn on BIOS/Legacy or whatever your system calls it. Then you should be able to boot Ubuntu in BIOS mode. But you have to go back into UEFI/BIOS turn on UEFI to boot Windows. A bit of a hassle.

I have never installed in vitual box. But you might be able to install 12.10 and then install 11.10 in virtual box. Not sure how well virtual box works with the new UEFI or if it matters or the gpt partitioning.

---

### Post by ashish0603 on 2013-01-18
I am already into Ubuntu and I can use both together if I just turn both(EFI and Legacy mode on). Just that I need to double press the ESC key, the thing I explained before. Just not the sophisticated way of doing things. Thanks though. You guided me the right way :)

---

