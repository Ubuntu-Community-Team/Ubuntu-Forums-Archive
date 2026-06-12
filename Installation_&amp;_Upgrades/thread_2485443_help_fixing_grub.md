---
title: "help fixing grub"
date: 2023-03-29
forum: Installation &amp; Upgrades
---

### Post by daredare13 on 2023-03-29
[SIZE=4]Hi,
I took my Windows 10 laptop and copied the ssd to a 2 tb ssd,  shrunk the partition to make a 1 tb partition to install ubuntu. I  installed ubuntu. when i reboot the computer it only boots into windows.  So I went to [https://www.supergrubdisk.org/super-grub2-disk/](https://www.supergrubdisk.org/super-grub2-disk/) and put it  on a flash drive. when I boot to that it looks for operating systems  and if I pick ubuntu then it boots to ubuntu. I have secure boot turned  off, the ssd is GPT, the bios is set to UEFI. 
I'm not sure how to use this forum. I tried to post something but it gave me an error. So I attached pictures. 
see the attachment gparted.jpg if you want to see the partitions. 
I installed grub customizer. 
see the attachment grub customizer.png to see the entries it found on my system.
See Win Boot Mgr.png - I think this is what needs to be edited. 
When  I boot up I want the computer to give me an option to choose to boot to  windows or ubuntu. is the windows boot manager entry what needs to be  edited? what does it need to say?
Thank you,
Darren Patton[/SIZE]

---

### Post by oldfred on 2023-03-29
I see Acer mentioned. What model?
Issue on many models of Acer is "trust" setting in UEFI on unknown UEFI entry. You set trust & change to ubuntu.

Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044) & 
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)
Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)
Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

---

### Post by daredare13 on 2023-03-29
I added the shimx64.efi, grubx64.efi to the trusted list in the bios and had to choose the boot order and add those two at the top of the list, and that gave me the boot menu to choose ubuntu or windows boot manager. So now I can boot to either one. that solved the problem. Thank you.

---

