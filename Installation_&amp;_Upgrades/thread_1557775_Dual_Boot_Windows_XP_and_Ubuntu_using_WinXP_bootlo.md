---
title: "Dual Boot Windows XP and Ubuntu using WinXP bootloader."
date: 2010-08-21
forum: Installation &amp; Upgrades
---

### Post by KaDMiO on 2010-08-21
[FONT=Arial]Hi everybody:

On many websites there is a short method for loading grub via the Windows bootloader. Although in many cases that should have worked, it didn't for me. So after trying many times, I found an alternative. Consider that this is for pcs which don't have Windows Vista or 7 installed, because in those you can easily use EasyBCD or any program of the sort.

In my case, I've got 2 SATA disk drives. Windows is installed in drive C, and Ubuntu will be installed in the last 2 partitions of the second disk (partitions L and M, for those still thinking in Windows terms).[/FONT]
 [FONT=Arial]
[/FONT] [FONT=Arial]Disclaimer: This procedure involves editing the MBR of your hard drive, so there is always the potential of damaging it. You acknowledge that you do this under your own risk, accepting all responsibilities about it. 
[/FONT]
[FONT=Arial]When doing this on my netbook, I made a mistake by trying not to use EasyBCD and Windows stopped recognizing my Documents partition. Fortunately, I had a backup of the MBR and could fix the problem.
[/FONT]
[FONT=Arial]I will consider that you've already partitioned your HDD to make room for Ubuntu. If you haven't, do it now. You can use the LiveCD and Gparted for it.[/FONT]
 
[LIST=1]
[*][FONT=Arial]The very first thing I recommend     doing, is to make a backup of the MBR as it is, just in case. As     many modifications will be done, it is good to have a backup copy,     just in case. To do this, follow these steps:[/FONT]
[LIST=1]
[*][FONT=Arial]Start Ubuntu from the Live CD.[/FONT]
[*][FONT=Arial]Open the console.[/FONT]
[*][FONT=Arial]Type: sudo dd if=/dev/sda         of=/mnt/window.bin bs=512 count=1[/FONT]
[LIST=1]
[*][FONT=Arial]This instruccion will take the MBR of your first HDD and write it to /mnt/window.bin.[/FONT]
[/LIST]
 
[/LIST]
[FONT=Arial]To make sure it is the right HDD, check with Gparted.[/FONT] 
[/LIST]

[LIST=1]
[*][FONT=Arial]Copy the file /mnt/windows.bin to         any directory accessible from Windows, in order to store it somewhere safe.[/FONT]
[*][FONT=Arial]Then, you need to install EasyBCD     on Windows. You may uninstall it afterwards,     but I recommend keeping it, as it makes some of the dirty work in a     safer manner.[/FONT]
[*][FONT=Arial]Install     Ubuntu on the partition/s you've chosen, and install Grub in     /dev/sda (It has to match with the one of the backup).[/FONT]
[*][FONT=Arial]Start     Ubuntu.[/FONT]
[*][FONT=Arial]Now, you have to make another     backup of the MBR. To do this, follow these steps:[/FONT]
[LIST=1]
[*][FONT=Arial]Open the console.[/FONT]
[*][FONT=Arial]Type: sudo dd if=/dev/sda         of=/home/ubuntu.bin bs=512 count=1[/FONT]
[LIST=1]
[*][FONT=Arial]This instruccion will take the MBR             of your first HDD and write it to /home/ubuntu.bin[/FONT]
[/LIST]
 
[*][FONT=Arial]Copy the         file /home/ubuntu.bin to any directory accessible from Windows, as         we will need it shortly.[/FONT]
[/LIST]
 
[*][FONT=Arial]Restart on     Windows.[/FONT]
[*][FONT=Arial]Open     EasyBCD. It will tell you there are no BCD files to work on, and     will ask you if you want to load them manually. Say no to it.[/FONT]
[*][FONT=Arial]Go to the     "Bootloader Setup" menu.[/FONT]
[*][FONT=Arial]Select the     checkbox “Install Windows Vista/7 Bootloader”.[/FONT]
[*][FONT=Arial]Press     “Write MBR”.[/FONT]
[*][FONT=Arial]Select the     checkbox “Install Windows XP Bootloader”.[/FONT]
[*][FONT=Arial]Press     “Write MBR” and confirm overwriting.[/FONT]
[*][FONT=Arial]Restart.     Expect to see the Windows bootloader. If it doesn't, start over from     point 6.
[/FONT]
[*][FONT=Arial]Copy the     ubuntu.bin file to the root of the C drive.[/FONT]
[*][FONT=Arial]Add the     following entry to the boot.ini file, making a backup first:[/FONT]
[LIST=1]
[*][FONT=Arial]C:\ubuntu.bin="Ubuntu         Linux 10.04 LTS"[/FONT]
[/LIST]
 
[*][FONT=Arial]Restart.     You should see the Windows bootloader with that entry. If you select     if, the Grub should appear, and then you should be able to boot on     Ubuntu.[/FONT]
[/LIST]
 [FONT=Arial]Slightly off-topic:
[/FONT]
[FONT=Arial]I am interested in making a small application to make these changes in a safer manner. I have the programming skills to write the application, but I've never worked with the MBR so I would need someone to guide me in how to modify the MBR without destroying the whole HDD xD. The aim of the program would be to allow any Linux or Windows XP and older user to adjust the MRB and boot.ini in a safe manner, from any of the two operating systems.
[/FONT]
[FONT=Arial]Some of you may think: Why this mess if grub just works fine?[/FONT]
[FONT=Arial]My answer: Because some people I know prefer to see first the WinXP bootloader, and if they wish, they can start with Ubuntu. It seems weird, but it really helps if you are in a transitional phase. It brings a certain "security" that your other operating system is still fine and you can access it anytime.[/FONT]

[FONT=Arial]I anyone is interested in collaborating on the development, feel free to contact me. I haven't got enough time to make everything on my own, but if anyone is willing to help, I'll be glad to start working on this.[/FONT]

[FONT=Arial]If you find any mistakes let me know so I can correct them.[/FONT]

---

