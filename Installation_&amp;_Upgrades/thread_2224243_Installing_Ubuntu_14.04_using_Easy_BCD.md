---
title: "Installing Ubuntu 14.04 using Easy BCD"
date: 2014-05-15
forum: Installation &amp; Upgrades
---

### Post by rickey2 on 2014-05-15
[FONT=arial black][FONT=microsoft sans serif][SIZE=4]Hello:
I have Windows 7 installed. I am trying to install Ubuntu 14.04 on another drive. I want to make that I have format the drive the right way. So could you please tell me from the beginning to the end how to do this !  I have tried but keep messing it up !  Also what setting to use in Easy BCD  !   I don't want to mess up MBR.   


                                                                                                                                                                                        Thanks !

P.S>  Yes this is my first try at Ubuntu !
[/SIZE][/FONT][/FONT]

---

### Post by oldfred on 2014-05-15
If you have two drives, install grub to the MBR of the second drive.
Many suggest disconnecting Windows drive and install Ubuntu as then there is no way it will create issues. If you do not disconnect drive you have to use Something Else, manually create partitions and select the Ubuntu drive as the location for the install of the grub2 boot loader.
You can set BIOS to boot Ubuntu drive and grub will show both Ubuntu & Windows as boot options. If you want to directly boot Windows it still has its boot loader in the Windows drive and you can boot it directly.

 Install to external drive. Also any second drive.
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

If using Something else, I have two examples. One I am installing to sdc to an existing partition with an old install and another installing to sdd also overwriting an old install. Both show the sda drive as default for boot loader as I have not yet changed it.

 Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)



How large is second drive? You may want more than default of just / (root) and swap?

---

### Post by rickey2 on 2014-05-15
[SIZE=4]It is 160gb hard drive ! Do[/SIZE] [FONT=microsoft sans serif][SIZE=4]you format them as primary or logical drives [/SIZE][/FONT][FONT=microsoft sans serif][SIZE=4]? How many partions do I need to have ?[/SIZE][/FONT]  [FONT=microsoft sans serif][SIZE=4]The first drive is 500gb, but I have Windows 7 & Windows 8.1 on it ! Because I have tried a few times, but wouldn't boot in to Ubuntu !! They were format as primary it didn't give me any other choices. Really am a NEWBIE when it come to Linux ! All the help is greatly appreciated ![/SIZE][/FONT]  [FONT=microsoft sans serif][SIZE=4]I did the formatting from the Live[/SIZE][/FONT] [FONT=microsoft sans serif][SIZE=4]CD ! G-Partion I think !![/SIZE][/FONT]

---

### Post by philinux on 2014-05-15
If the other drive is sdb then when you install ubuntu choose sdb as the location to install grub.

then from windows run easy bcd and tell it to look there for the linux installation. It should find it auto magically..

reboot and you will get the option to run win or ubuntu

make sure to follow oldfreds advice.

---

### Post by mastablasta on 2014-05-16
2 partitions are needed root (/) that is using linux format (use default ext4) and swap (/swap) that is using "swap" format. swap is like pagefile in windows. so it should be about the size of ram. if you have more ram then it can be about 2GB. if you unplug the first (windows) disk and install on second erasing all data on it (firstinstall option) then all partitions are setup for you automaticly and you do not have to worry abotu partitioning. furthermore partitions can always be added later since linux (unlike windows) doeasn't have such a fragmented filesystem. so it's easy to add more partitions if needed later on.

---

### Post by rickey2 on 2014-05-19
[FONT=microsoft sans serif][SIZE=4]Answer a Question for me !! Okay I installed Ubuntu 12.04 LTS, unhook the Windows Drive First ! Everything went okay, but when I boot into Windows 7 and go into Easy BCD and try an get the boot loader for Unbuntu  it doesn't work no matter if I pick or Easy BCD picks ! I also noticed there is a Fat32 partion on the Ubuntu Drive ![/SIZE][/FONT] [FONT=microsoft sans serif][SIZE=4]And it does have the grub boot loader in that Fat32 ![/SIZE][/FONT]  [FONT=microsoft sans serif][SIZE=4]So what would happen if I would delete that Fat 32 partion ?  I wouldn't be able to get into Ubuntu (right) ? Both are Gigabyte motherboard, GA-B75M-D3H & GA-970A-DS3P .[/SIZE][/FONT]

---

### Post by oldfred on 2014-05-19
Is Windows installed in BIOS boot mode and you installed Ubuntu in UEFI boot mode. They are not compatible so you can only boot from UEFI menu. You may have to turn on CSM/BIOS to boot Windows and turn on UEFI to boot Ubuntu. Some auto switch.

Post link to BootInfo report:
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

