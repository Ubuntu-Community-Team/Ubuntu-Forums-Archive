---
title: "Acer Nitro 7: BIOS Main menu SATA Mode Missing:"
date: 2019-10-25
forum: Installation &amp; Upgrades
---

### Post by Jambhavan on 2019-10-25
My new Acer Nitro 7 (with preinstalled Windows 10) had SATA mode pointing to RST. During Ubuntu dual boot installation, I did the following (after browsing through website information on how to dual boot).

1) In windows, turned off fast boot option
2) Came to BIOS (which was version 1.05, then), in the main menu, a) Enabled F12 boot menu, b) Changed SATA mode to UHCI, kept the UEFI as it is, kept the Secure boot as it is.
3) Then I was able to install Ubuntu using bootable USB, and successfully installed and created users etc, and shut down

I thought we can switch SATA mode to RST premium with Optane, with a thought that, if it does not work, we can come back and change it to UHCI again. [This was the blunder I made, I guess. Frankly, I don't know what is RST/UHCI and all]. As I saved these changes and exited, I went to the Windows.] 

I was just browsing with a thought that everything went well.

I noticed that there was a BIOS update version 1.09 available for this laptop. So why not install it? Thus, I went to Windows, and then installed BIOS update. When the BIOS update was getting finished, I got the grub menu, and I chose to go to Ubuntu to see if I was able to boot to the system, and I was able to get into Linux.

Then, I wanted to make the Windows boot option default. So I restarted the system to go to BIOS but then I noticed my SATA mode is no more there in the main menu.

Can anyone here help me understand how to get the SATA mode again in my main menu. (And if time permits, can you please explain what happened here. Why is the SATA mode is missing in the main menu.)

I hope I gave all the details. Please let me know if you want any other missing information that I left out here.

Other system info:
1 SSD of 256 GB + 1 TB HDD
4 GB dedicated Graphics
Intel I5
Acer Nitro 7


Thanks and Regards,
GV

---

### Post by Jambhavan on 2019-10-25
And following this, I am unable to boot into Ubuntu as well. Now I am left with Windows 10 (and part of the SSD drive where I installed Windows is accessible), and 1 TB empty drive. The part of the SSD drive where I installed Ubuntu is not showing up (even by doing 1) choosing Try Ubuntu with bootable USB, and checking the drives in it, or by 2) Install Ubuntu with bootable USB, to see if the drives are accessible).

Whenever I try to boot into Ubuntu, I am getting the error: 

Problem loading UEFI:db X.509 certificate (-65)
Gave up waiting for suspend/resume device

Gave up waiting for root file system device.

and it goes to (initramfs) prompt.

I tried disabling Secure Boot in the BIOS but no relief.

Please any one help me fix this issue. Thanks.

---

### Post by oldfred on 2019-10-25
All Acer require you to set "trust" from within UEFI for ubuntu UEFI boot entry. May be shown as unknown otherwise.
They typically require the UEFI update, which may reset some of the settings you changed back to defaults.
And many with SSD need SSD firmware update for SSD to fully work.

Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[https://community.acer.com/en/categories/predator](https://community.acer.com/en/categories/predator)

Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

---

### Post by Jambhavan on 2019-10-25
Thanks for the reply. But your suggestions work well for those who are trying to install dual boot Linux + Windows or so on.

Now I got stuck with the mistake of updating my BIOS. Only after updating my BIOS and then after, changing the SATA mode from AHCI to RST Premium with Optane, I lost that SATA mode controller itself. Now I don't see the SATA mode field itself and hence cannot change the mode back to AHCI.

If you know how to get this SATA mode, please reply.

---

### Post by oldfred on 2019-10-25
If you have RST on, you cannot have AHCI.

Intel Optane - See Intel response that no performance difference between RAID & AHCI.
[https://communities.intel.com/thread/121155](https://communities.intel.com/thread/121155)

[https://www.dell.com/support/article/us/en/04/sln306745/optane-memory-module-frequently-asked-questions?lang=en](https://www.dell.com/support/article/us/en/04/sln306745/optane-memory-module-frequently-asked-questions?lang=en)

I know Windows boots so slow, that Microsoft required UEFI fast boot, Windows fast start up and often SSD cache if only HDD, so cache can load faster. Then Windows is not so slow booting. But cache is only used for hibernation file not otherwise. 

If you have SSD for operating system(s), not sure optane gives you much, perhap some speed up on HDD accesses.

---

### Post by Jambhavan on 2019-10-25
Olfred, Thanks for the reply.

No, I don't think I have RST with Optane. But I chose the option as it was available under SATA, and thought I will try that. This is the biggest mistake I did. Till then, I had dual boot working fine.

Now, I couldn't change the SATA mode to AHCI because the option SATA field itself is missing in the BIOS main menu. In the front page summary, the SATA is shown to be RST premium with Optane setting.

How do I change this SATA mode to AHCI (without being able to see this SATA field itself in the BIOS).

Its driving me crazy. I might have shutdown/restarted the system several times with no relief.

---

### Post by magira83 on 2019-10-25
The same situation happened to me with my acer nitro 5. After updating from bios 1.05 to bios 1.09 I have lost my sata mode, it was AHCI and now becomes Rst Premium with Optane. I was happy before this updating because I have just resolved the problem with Optane mode setting in bios AHCI sata mode and reinstalling windows but now how could I resolve this problem? Reverting the bios from 1.09 to 1.05?

---

### Post by Jambhavan on 2019-10-26
Problem solved. I came across another Acer user who responded to my query on Acer community.

To get back the SATA field in BIOS main menu, boot with F2 to get to the BIOS, and go to main menu, and press Ctrl + S. SATA field will reappear. Then change accordingly as you see the SATA option.

---

### Post by magira83 on 2019-10-26
Great news! Thank you.

---

