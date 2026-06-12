---
title: "Windows 10 and Ubuntu won't boot properly"
date: 2017-02-22
forum: Installation &amp; Upgrades
---

### Post by vergal3 on 2017-02-22
Hello community,

I installed Ubuntu onto my laptop, but when I tried to boot windows 10 I  was unable to do so. Then I tried to fix things myself by using testdisk, but I then  accidentally made Ubuntu boot with regards to the same partition that my  windows was booting from. I now do not have access to both and I've had  to use a USB for temporary access to Ubuntu. I then used the boot  repair program and got the link after the analyses was over. I'm not sure if the paste2 link that I received from boor-repair has too much information to share online, so if someone can also help me with being selective of what information is fine to post. May I  please receive assistance in correcting the errors made. My priority  would be to boot windows 10 and if possible I would like to  have dual capability with Ubuntu. I am a beginner so I am not too  knowledgeable with the correct terminology, but i am trying. Thank you  in advance for your time and assistance.

Sincerely,
Vergal3

---

### Post by vergal3 on 2017-02-22
Also, if avoidable, I do not want to buy a windows recovery disk, but if it can not be helped please let me know.

---

### Post by ubfan1 on 2017-02-22
Please post the link to the boot-repair report.  That will give us the information we need to help you.

---

### Post by vergal3 on 2017-02-22
paste2.org/12sZyZkz

---

### Post by LostFarmer on 2017-02-22
> Disklabel type: dos from your paste2 link. Your MS Windows and Linux was installed on a GPT disk, now it is DOS (MBR). Read on how to convert from MBR to GPT [http://www.rodsbooks.com/gdisk/mbr2gpt.html ]("http://www.rodsbooks.com/gdisk/mbr2gpt.html") 
 
You will very likely have problems booting into win10 due to the GPT partition Unique partition GUID will be changed after conversion.

---

### Post by ubfan1 on 2017-02-22
That "unused" GPT partition table looks like it should be the one in use, the dos partition table does not even have any linux partition.  I'm not familiar with disk repair tools, but it looks like you need to replace the in-use dos partition table with the gpt one. Until then, do not write anything to the hard disk.  At least you have the sectors in the paste link to manually redo the partitions if necessary, but lets see if anyone else with more experience in disk repairs chips in -- maybe change title or start a new thread which has "disk repair needed" in title.

---

### Post by vergal3 on 2017-02-23
Would I make these changes using testdisk or something else? Are there any step by step instructions on what you do and what application to use?.

---

### Post by RobGoss on 2017-02-23
My first thought would be do you have a backup for windows partition?

I don't know how things were installed but I'm guessing you should try fixing Windows first before any more damage is done to your system. If you have a recovery Windows partition I would try using that and see if you are able to access Windows then, work on getting Ubuntu up and running seeing Ubuntu should be a lot easier to fix.

---

### Post by vergal3 on 2017-02-23
Sorry I'm very inexperienced so I honestly don't know. How would I be able to tell?

---

### Post by oldfred on 2017-02-23
It looks like you used testdisk and converted gpt install of Windows to a MBR(msdos) partitioned drive.
But Windows installed in UEFI mode on gpt drive will only boot from gpt partitioned drive.
And Windows installed to MBR drive will only boot in BIOS mode.
If you want to keep MBR, you have to purchase a new legal copy of Windows and install that.
Your Windows product license is actually in the UEFI, and only valid for the Lenovo OEM version originally installed.
This is why we always suggest full backups of Windows (and Ubuntu) before any major system change.

You first need to convert drive back to gpt. Use gdisk as posted above.
       Use gdisk and verify partitions are correct with p, or v to review issues,  and use w to write the partition table. If not correct just use q to quit. That should update primary, backup & protective MBR. Details:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html) 
    
Not sure if testdisk combined any partitions as Windows has to have the system reserved, which is just unformatted space and before first NTFS partition.
Windows normally has this, but often there is a vendor recovery at end of drive also.
[https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)

       Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

---

### Post by vergal3 on 2017-02-23
I used the terminal and typed "sudo gdisk /dev/sda" and in the partition table scan it says GPT: damaged. Then a line under it says which do I want to use. Should I go with GPT even though it says damaged? I'm really worried and don't want to mess things up.

---

### Post by ubunticus on 2017-02-23
> **vergal3 said:**
> Also, if avoidable, I do not want to buy a windows recovery disk, but if it can not be helped please let me know.

If your pc was shipped with Windows 10 installed then you can make a new installation media following the instruction at:
[https://www.microsoft.com/en-us/software-download/windows10](https://www.microsoft.com/en-us/software-download/windows10)

You can use this to do a fresh install without having to have a product key since your Windows 10 is already associated with your motherboard. You can even use the installation media as a recovery disk. Boot up you pc from the installation media and at the bottom left of the installation page choose "repair".

---

### Post by oldfred on 2017-02-23
What specifically does gdisk error say.
Can you copy & paste?
And the results of p command?

One advantage of gpt is that is has both a primary & backup.
It may just say primary damaged (by conversion with testdisk to MBR) and backup is ok, using backup.
A write then corrects backup MBR, primary & backup partition tables.

When using testdisk one of the first choices is whether drive is MBR or efi/gpt. You need to know which you are trying to repair and then testdisk works well, but using it to convert type is not usually the best use of testdisk.

---

### Post by vergal3 on 2017-02-23
Hey you all, I'm up and running now due to the method I mentioned and just going along with it. Windows booted and I'm back on. Thank you all so much!!

---

### Post by RobGoss on 2017-02-23
World you mind sharing your solution with the forum

How were you able to get Windows to boot? it will help others If they run in to something like this

---

### Post by vergal3 on 2017-02-26
To solve the issue i typed [COLOR=#000000]sudo gdisk /dev/sda[/COLOR] into the terminal and it gave me the option to boot from GPT or MBR. I chose GPT and rebooted. It worked after that.

---

