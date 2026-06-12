---
title: "Option to install &quot;alongside&quot; Win10 not showing :("
date: 2016-04-24
forum: Installation &amp; Upgrades
---

### Post by javierdl on 2016-04-24
I already ensure I covered all the tips advised to setup a pc with UEFI.
But the option to install "alongside" Win10 still not showing :(
See the screenshot below to see my options.

According to the Ubuntu Studio 16.04 installer I have Ubuntu 13 installed. I really don't. It must be some remainder files from the time I used gParted to create partitions (I guess).
My 1st question is: [B]
Would Windows 10 be preserved If...[/B] 
I were to choose either:
 "Erase Ubuntu 13.10 and reinstall", 
or an empty partition (ext4) via "Something else" at the bottom ?

Easy Linux Tips Project advises to go with the "[Something else]("https://sites.google.com/site/easylinuxtipsproject/reserve-10")" option. But the link bringing you to the page with the instructions is called "potential solution". Hence implying that it "may" be a solution, or it "may not" :(

Any reassuring thoughts will be appreciated :)

Thanks,

JDL

---

### Post by Bucky Ball on 2016-04-24
*Thread moved to **Installation & Upgrades**.*

Use 'Something Else' and install / to free space or over an existing partition. The existing /swap will be used automatically, if there is one. If not, create a 2Gb /swap or same size as installed RAM if you intend hibernating.

Any partitions that are not set (ticked) to 'Format' will be untouched.

---

### Post by javierdl on 2016-04-24
Excellent!
Thank you so much BB :)

JDL

---

### Post by javierdl on 2016-04-24
Got stuck already :(

[IMG]https://sites.google.com/site/javierwebfolio/_/rsrc/1461521993893/temp/Screenshot_2016-04-24_18-15-07.png[/IMG]

[IMG]https://sites.google.com/site/javierwebfolio/_/rsrc/1461522025239/temp/Screenshot_2016-04-24_18-15-39.png[/IMG]

---

### Post by ubfan1 on 2016-04-24
You need to select the partition you want to install Ubuntu to (sda6?), then click on the "change" button.  Then select ext4 for a filesystem, and a mount point of "/".  Select format if there is nothing on that partition you want to save -- from your description I'd expect it to be empty.
Now for a UEFI machine, the place to put the bootloader is ignored and the bootloaders go into the EFI partition, sda1 I'd guess.  I'd put either /dev/sda or /dev/sda1 there, not sda6.

---

### Post by oldfred on 2016-04-24
If you have Windows 10 best to have fast start up off which really is just hibernation. Then the installer should correctly see the NTFS partitions.
The Linux NTFS driver will not normally mount hibernated partitions, not partitions needing chkdsk. And chkdsk is required after any NTFS partition resize, and often after a hard shutdown.

       Fast Startup off (always on hibernation)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

Windows 8 & 10 should be identical or very similar for dual boot install.

 UEFI install,windows 8 with Something Else screen shots
How To Install Ubuntu Linux Alongside Windows 10 (UEFI)
[http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html](http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html)
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html) 

       
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
Also shows Windows 8 screens or similar to Windows 10
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

---

### Post by javierdl on 2016-04-24
This is more complex than I thought :(
I'm going to have to carefully see those tutorial links you shared oldfred ;)

I installed twice already! And it boots automatically to Win10 everytime! :(

---

### Post by oldfred on 2016-04-24
IF you have installed it may just be settings in UEFI to tell it to boot the ubuntu UEFI entry.

But some systems modify UEFI in violation of UEFI standard which says not to use description as part of boot. And only valid description is "Windows Boot Manager".
But there are several work arounds.

What brand/model system?

If installed run this from live installer:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by javierdl on 2016-04-25
Here's the [report]("http://paste2.org/x9BLPnhx")

I had to use the terminal commands from a Live US usb key. 
The Boot Repair Disk from a Live USB key would not work for some reason. It was giving me a black screen, it stayed that way for at least 10 minutes.
But at least the other way worked.

Thank you so much in advance oldfred :)

---

### Post by oldfred on 2016-04-25
You have an UEFI system.
And Windows installed in UEFI boot mode on sda, which is gpt partitioned.

But sdb & sdc are MBR partitioned.
With Windows you can only boot in UEFI from gpt or only BIOS from MBR.
But Ubuntu does work and even will install to a MBR partitioned drive and in UEFI mode boot from an sda with gpt partitioning. Or with BIOS from a MBR on the MBR partitioned drive.

But best to only use gpt partitioning once you convert to UEFI. But can be difficult to convert if drive is full of data as standard repartitioning erases drive. You may be able to convert in line, but still must have full backup and reinstall of grub, and perhaps added partitions for either ESP or bios_grub required.
 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html) 

With your mixed gpt/MBR you may be able to boot Ubuntu on the MBR drive thru UEFI on the gpt drive. Otherwise you have to only use UEFI/BIOS to choose how to boot as UEFI and BIOS are not compatible and once you start to boot in one mode, you cannot change.

You also show you have an Acer. In UEFI mode you have to set a supervisory password and set "trust" and the ubuntu/grub efi boot files. Make sure you have newest UEFI from Acer.
      
 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912) 
    
Do not use Boot-Repair's auto fix.
Do use its advanced mode only.  Download newest version of Boot-Repair as it just has a new fix for some issues.
If you just want BIOS boot, be sure to boot Boot-Repair in BIOS mode and in advanced mode install grub to MBR of sdb. Then in UEFI or perhaps one time boot key like f10 or f12, you can choose Windows or sdb drive in BIOS mode.
Or boot Boot-Repair in UEFI mode and reinstall grub. That will install to the ESP - efi system partition on sda. You already show the /EFI/ubuntu folder, so at some time you did that.
And then authorize or set trust to allow Acer to let you boot shimx64.efi or ubuntu entry.

But if using UEFI better to convert to gpt.

---

### Post by javierdl on 2016-04-25
Thanks oldfred.
Boy! That's lots of information/choices. Unfortunately this is my first pc with UEFI, so most of what you explained is new to me :(
Any chance you could put it in lamer terms? Maybe less choices? Maybe slimming it down to what you consider the best way to go about it? I'll take your word for it! :)
Better yet, if you could put it in ordered steps, I don't mean to be too demanding, but that would be amazing!
Maybe this is the part I need the most (?):
You said: > [B]"[COLOR=#000000]With your mixed gpt/MBR you may be able to boot Ubuntu on the MBR drive thru UEFI on the gpt drive.[/COLOR]"
[/B]
If so, could you elaborate on it?

You said: > "[COLOR=#000000]In UEFI mode you have to set a supervisory password and set "trust" **and the ubuntu/grub efi boot files.**[/COLOR]"
I understand the first part, but not the second. You made reference to the "ubuntu/grub efi boot files". But you don't say what I'm supposed to do with them. Am I supposed to ALSO set a Supervisory passw and set trust for them too? 

Just to better understand this... I go to BIOS via DEL key, what about UEFI? I thought it was integrated into BIOS.

I appreciate your patience oldfred :)

JDL

---

### Post by oldfred on 2016-04-25
Can or would you want to convert sdb and/or sdc to gpt?
That would be a bit more correct as UEFI standard is gpt partitioning. But it does work with MBR as even Ubuntu installer is FAT32 on MBR(usually). 

Your 16.04 install is on sda, the gpt partitioned drive and is configured for UEFI boot. 
With UEFI you can go into UEFI or one time boot key, often f10 or f12 and boot Windows directly. Turn off the fast start up. (links in Post #6)

Then you have to go into UEFI, set supervisory password and enable "trust" on the grub/ubuntu efi boot files. This is unique to all Acer system.
Make sure you have latest UEFI from Acer.
 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot, many details
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Acer Aspire E 15 Downgrade to older UEFI, password & trust (ACPI issues?)
[http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062](http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062) 


You will not be able to boot BIOS install in drive sdb.

---

### Post by javierdl on 2016-04-26
Only until now I'm realizing that sdc and sdb are my external HDs.
To keep things simple, wouldn't it be better to get the external HDs out of the picture?
Then I would only have sda to deal with. Which is where I want to install Ubuntu S. anyway.
There was a SWAP and an EXT4 partition in sdc. No longer. I deleted them both. I suppose I should try installing US again, but this time with the external HDs unplugged.

I went into UEFI to set the supervisory password and enable trust, as you recommended. But I only found a where to set the password, but no way to enable trust anywhere:

[IMG]https://sites.google.com/site/javierwebfolio/_/rsrc/1461675768871/temp/P_20160426_082421.jpg[/IMG]

In case it makes a difference, I my desktop pc is an Acer Predator G3-710

---

### Post by ubfan1 on 2016-04-26
Did you try the TMP (Trusted Platform Module) options?  Just an idea, I know nothing about Acer setups.

---

### Post by oldfred on 2016-04-26
Several of the threads on setting "trust" have more details on how to do it. Do not have Acer to know.
But I think it was on a different screen.

If external drives should not make any difference, but disconnect them for time being.

From one of the links, but I would review several:

> 
[LIST=1]
[*]Restart the laptop as we did back in Step 1.
[*]Use the right cursor key to highlight "Security"  and use the down  cursor key to highlight "Select an UEFI file as trusted for executing"  and press Enter.
[*]The "Security" window will show HDD0 in white letters. Press the Enter key.
[*]On my laptop two items; they look like folders show up: "EFI and Temp." Highlight EFI and press Enter.
[*]These folders are displayed: ., .., ubuntu, Microsoft, Boot, and OEM. Highlight ubuntu and press Enter.
[*]Another set of folders are listed: ., .., shimx64.efi, grubx64.efi,  and  MokManager.efi. Highlight "grubx64.efi" and press Enter.
[*]The "Add an new file" window will appear in the middle of the screen  with the question: "Do you wish to add this file to allowable  database?"  In the "Boot Description" type in grubx64.efi and press the  Enter key twice.
[*]Press F10 to Save and Exit BIOS.
[/LIST]


---

### Post by javierdl on 2016-04-27
Good news !
I finally got the option to "install alongside the Windows Boot Manager"!
It seems it did. I can't tell yet because it booted directly into Win10 :(
I'll come back in a moment to explain how I did it .

---

