---
title: "Advice for bootloader when installing ubuntu over windows xp"
date: 2012-01-17
forum: Installation &amp; Upgrades
---

### Post by isaac12345 on 2012-01-17
Hi guys!

I recently realised that I havent used windows xp in a very long time and I thought that I would install ubuntu over it instead.
At the moment, I have windows 7 and XP installed with the partitions are as follows -

C: - This is where windows xp is installed. It is on a 320gb hdd
D: - A paritition created in windows 7 for storing media,downloads,etc - Its is on a 1Tb hdd
E: - This is where windows 7 is installed. It is on the 1TB hdd
G:- A partition created in windows 7 for installing apps to - It is on the 1TB hdd
L: - A partition created in windows XP for installing games to,used from windows xp and windows 7 - It is on the 320gb hdd
M: - A partition created in windows XP for storing music,ued from windows xp and windows 7 - It is on the 320gb HDD

At the moment, I plan to uninstall all the programs installed in windows xp to free up space from the other partitions. 
I was then thinking of simply using a live USB ubuntu disk to install ubuntu on C: drive. 

My concerns are -

1) Will the usb installer automatically format the C: drive while installing ubuntu or would I have to manually do it?

2) This is my biggest concern. Will the ubuntu installer take care of the bootloader? The part where I select which operating system to boot from? 

Thanks in advance for your replies :)

---

### Post by Mark Phelps on 2012-01-17
If you installed Win7 after you installed XP, and the XP drive was connected to the PC when you installed Win7, it's almost certain that Win7 installed its bootloader files to the XP partition.

So, if you remove it, you will no longer be able to boot Win7.

You can move the bootloader, using a GUI, by downloading and installing EasyBCD from NeoSmart Technologies.  It has an option to move the bootloader files to different "drives" (partitions).

Also, you will have to choose "Something Else" to do manual partitioning (to reformat the XP partition) from the Ubuntu installer as it is not going to install to a Windows filesystem partition.

---

### Post by isaac12345 on 2012-01-17
Thanks for the advice. I used EasyBCD to change the bootloader from C: to E: but as soon as I exit the program it keeps going back to C:. Any ideas why and how to fix it?

---

### Post by Mark Phelps on 2012-01-18
How to you know it keeps going back to "C"?

One way to check is the following: When EasyBCD loads, look in the main window for a line saying easyBCD Boot Device:  -- followed by something like "C\:".  Then look down at your entries.  If Windows 7 also says Drive: C:\ -- then the boot loader is sharing the same partition with Win7.

You can also go into Edit Boot Menu and make a minor change to one of the Entry names (change Windows 7 to Win 7).  Then, look inside the hidden boot directory on your Win7 drive for a file named "BCD".  If that was updated by EasyBCD, it should have a recent date and time stamp.

If neither of these is working as indicated, you need to go to the NeoSmart Technology forums, EasyBCD Support, and post your question there.  They are very good about responding.

---

### Post by isaac12345 on 2012-01-19
When I start the program the output in the main windows is as follows -

[FONT=Arial]There are a total of 2 entries listed in the bootloader.

Default: Windows 7
Timeout: 30 seconds
EasyBCD Boot Device: C:\

Entry #1
Name: Earlier Version of Windows
BCD ID: {ntldr}
Drive: C:\
Bootloader Path: \ntldr

Entry #2
Name: Windows 7
BCD ID: {current}
Drive: E:\
Bootloader Path: \Windows\system32\winload.exe[/FONT]

Then I went to "BCD Backup/Repair", selected "Change boot device", clicked on perform action and then selected E: drive. After a few seconds, a prompt came up saying that it was succesfuly changed.

Then I clicked on view settings and the output of the main window is - 

[FONT=Arial]There are a total of 2 entries listed in the bootloader.
Path: E:\BOOT\BCD

Default: Windows 7
Timeout: 30 seconds
EasyBCD Boot Device: E:\

Entry #1
Name: Earlier Version of Windows
BCD ID: {ntldr}
Drive: C:\
Bootloader Path: \ntldr

Entry #2
Name: Windows 7
BCD ID: {default}
Drive: E:\
Bootloader Path: \Windows\system32\winload.exe[/FONT]

After that I closed EasyBCD and opened it again to find the following output in the main window - 

[FONT=Arial]There are a total of 2 entries listed in the bootloader.

Default: Windows 7
Timeout: 30 seconds
EasyBCD Boot Device: C:\

Entry #1
Name: Earlier Version of Windows
BCD ID: {ntldr}
Drive: C:\
Bootloader Path: \ntldr

Entry #2
Name: Windows 7
BCD ID: {current}
Drive: E:\
Bootloader Path: \Windows\system32\winload.exe[/FONT]

The boot device changes back to C: !! :\

---

### Post by isaac12345 on 2012-01-22
Thanks for your reply. 
I did that and this is the reply I got on the NeoSmart forums - [http://neosmart.net/forums/showthread.php?t=9148&p=69892#post69892](http://neosmart.net/forums/showthread.php?t=9148&p=69892#post69892)

I changed the boot drive from C: (windows xp) to E (windows  7) which is on a  separate hdd, and then changed the boot drive to that  hdd. It shows me  the same choices as the previous bootloader but when I  select the  windows xp option, the system simply restarts. Should I be  worried about  this when installing ubuntu?

---

