---
title: "Looking for Grub, and I need it to not. Need to revert the process."
date: 2022-02-02
forum: Installation &amp; Upgrades
---

### Post by p2bc on 2022-02-02
Hey, long time no post. Truthfully, haven't had a problem in awhile, thanks to a solid product.

What is to follow is user error -ish, I am screwed if I don't get this fixed, and I mean hard. As such some may find this predicament to be humorous; That is fine. So here... we... go...


On an external NVMe, we will refer to as "/dev/sdc". There are two partitions. On the first partition has Kubuntu install. Like INSTALLed, not liveCD, actual install. with the grub, and MBR everything. On the second is simple NTFS so it could be use regular USB drive that could be moved around and store file like you do.

Here is the problem. I inserted that external NVMe drive in my work computer, just to copy some files over I was working on at home. Everything went on without a hitch, as you would expect. Nothing eventful so far right.

When I was finish for the day, I shutdown my work computer running Win10, and went home. Not thinking on the NVMe drive that was still attached to the work computer. Next day, I turn on my computer, go grab a coffee, and come back to my work computer, to see the grub menu. ????

Oh, I forgot the NVMe attached, which has a partition with a bootable Linux. I don't have access to bios, to choose that partition, so I did not even think that this would happen. So I logged into Kubuntu for fun. Pocked around. My work station is a pretty beefy machine so it was fun to use a good OS on it for a bit. I did do a "sudo apt update" and "sudo apt upgrade" since I had not been in the OS for a while might as well get it up to date for the next time I will need to actually use it. It is self contained....    I can start hearing the chuckles already.

I believe there was a kernel update in those update so it must have done a grub-update after the changes.

Because, now when I shutdown and unplug the external drive, so the system will boot from the first drive like it use too. I get "Grub not found" and "Grub Rescue". If I plug the NVMe back in and let grub load, and get the grub select screen, I can scroll down, and select Windows 10, but I don't want to have to keep my NVMe drive plug in. Nor explain how this came about.

Now I hear slight laughter.


I don't have access to anything more that BASIC, it is a work computer, managed by an outside I.T. AND I signed an agreement that I would not try to supersede the security on the computer, including the BIOS, yes they specifically mention the BIOS and Bios password, which I didn't. Not sure they will care about a technicality.

I hear actual laughter now.


So please help. Not to familiar with grub. I know it in theory, but not extensive practice. How can I remove, what I am guessing grub from the MBR/UEFI so that computer will boot normally directly into Windows. I do have full access to the Linux side, and basic access on the Windows side, no access to BIOS


If you were laughing, that is only because you know my pain, all cool. Can we get this fixed pretty plz?

Thank you  in advance.

---

### Post by oldfred on 2022-02-02
If it is looking for grub on a reboot, then is it an UEFI system?
And a major update of grub would add a new UEFI boot entry and set it as new default boot.
If old BIOS it may reset boot order, or reinstall grub to MBR of first drive, often sda or first NVMe drive.

Need to know which it did to see if it can be undone without UEFI/BIOS access.

From Ubuntu on work system can you run Boot-Repair, do not run any fixes, we just want to see report with details on what is where.

Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO (ISO not updated as frequently as ppa)
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by tea for one on 2022-02-02
You had no access to the boot priority in the BIOS (or UEFI) of your work PC, yet you managed to boot and use Kubuntu on your external nvme drive.
This means that the PC setting will allow booting from external devices before internal drives? 

Possibly, a Windows 10 ISO (is it version 10?) on a USB stick will boot and repair the Windows Boot Manager.

You could be in a fortunate position after this problem has been solved.
i.e. In a couple of weeks, you could show the top brass that the PC security is imperfect.
Extra week of paid holiday  ;)

---

### Post by p2bc on 2022-02-02
Ok, super stealthy, feel like MI. Running linux desktop in an office where anyone person who can stick their head over a cubical wall and say "What is that? That is not Windows!".

Here you go, hope it says something useful.


[https://paste.ubuntu.com/p/6xm4mW39QC/](https://paste.ubuntu.com/p/6xm4mW39QC/)

---

### Post by p2bc on 2022-02-02
> **tea for one said:**
> 
...
You could be in a fortunate position after this problem has been solved.
i.e. In a couple of weeks, you could show the top brass that the PC security is imperfect.
Extra week of paid holiday  ;)

I like how you think, but at the moment i just want to keep my job. Only had it for 3 weeks so far.


On a more serious note, actually sad, spoke to the I.T. guy and they only have one linux machine running, for their PBX. Their have it running in the corner, hasn't been touched in a "LONG TIME", because they are scared to. No one knows what to do with it, and they are worried for the day they come in and it is not on.

---

### Post by p2bc on 2022-02-02
Oh, I forgot, it is version 10.

---

### Post by tea for one on 2022-02-02
Your work PC is a Legacy installation in msdos (mbr) mode.
Probably Windows 7 originally - updated to Windows 10.

No EFI System Partition therefore not UEFI 
No partitions are GPT

[COLOR="#0000FF"]Lines 157 and 162[/COLOR] [COLOR="#FF0000"]Raid[/COLOR] on sda and sdb
[COLOR="#0000FF"]Line 5[/COLOR] - Grub installed on sdc (your nvme external drive)

It is quite complicated.
You need to copy the mbr details from sdc to sda and/or sdb (due to Raid)

Boot-repair will not fix Windows boot problems without introducing Grub (which will spill the beans to your employer).

Three choices spring to mind:-

[LIST=1]
[*]Download a Windows 10 ISO, prepare a boot disk and attempt a repair.
[*]You can possibly use a Linux system to attempt to relocate mbr [https://www.cyberciti.biz/faq/howto-copy-mbr/](https://www.cyberciti.biz/faq/howto-copy-mbr/)
[*]Crawl on your hands and knees to your kindly employer and beg forgiveness.
[*]
[/LIST]
My instincts veer towards choice 3.

Please do nothing until other suggestions are offered.

Fingers crossed.

---

### Post by grahammechanical on 2022-02-02
I might be reading this all wrong but it seems to me that the boot  order has been changed and that should not be possible if the BIOS  utility has a password set. This might be another security failing.

The  Boot Repair summary indicates that sda & sdb not GPT drives. I am  guessing that Windows 10 on sda & sdb is installed in  Legacy/BIOS/CSM mode. I am also guessing that this machine has BIOS  motherboard and not a UEFI motherboard.

I am not familiar with  Kubuntu but it should have a utility similar to Gnome Disks which will  show whether the drives are GPT or MBR and whether there is an efi boot  partition on sda & sdb.

Based on my experience using a BIOS  motherboard it is possible to set the boot order to look for an OS on a  particular drive and if that fails then to continue looking for the OS  by checking a list of drives. It is also possible to set the BIOS to  look for an OS on one particular drive and no other. This speeds up  booting.

Does the motherboard splash screen inform you of the key  to press to access the BIOS setup utility. If the BIOS is password  protected then you will not get very far but you can back out.

Regards

---

### Post by oldfred on 2022-02-02
Boot-Repair can fix a BIOS/MBR Windows but due to licensing cannot install the "Windows" MBR. It installs syslinux which works like the Windows MBR. MBR boot is from BIOS, to MBR, to NTFS partition with boot flag which has more of Windows boot files.
Report did not show MBR of sda & sdb which it normally does.
And some other info is missing. Is Windows using encryption?

Bit surprised system is still BIOS/MBR, Microsoft has required vendors to install in UEFI boot mode using gpt partitioning since 2012, so almost all hardware is now UEFI.
And surprised a user system is using RAID. RAID is not backup, but for uptime. Or more for servers.

You could try a Windows repair flash drive & the fixMBR command which writes to MBR.
But with your configuration, it may have (had?) a proprietary encrypted MBR, not a standard Windows MBR.

Not sure why if you remove external drive, it does not default to booting Windows. Grub is not showing in sda or sdb and would not normally install to a different drive. It either installs to same drive or may error out if internal drive not same as original install's internal drive. BIOS grub saves a drive info on where  to reinstall.

---

### Post by p2bc on 2022-02-02
Ok, where to begin.

1- The machine does "look' a little old, dust, and what have you. Not a fancy modern case, very much a black box. It does have a Xeon processor, with 32 gig of ram, so perhaps an old server that is now repurposed as desktop for CAD design. Might also explain the RAID setup.

2- Encryption. not to my knowledge, but I doubt it.

3- COMPLETE clarity. This happened before last week. Booted into Grub boot window, I panic and rebooted the system. Unplugged the drive, booted up as expected. This time when it happened i say, what the heck let see how Linux would perform on this system. Short - well. It was then that I did a "sudo apt update/upgrade" played around on a few apps, was impress on the responsiveness, and rebooted. Came in this morning, turn on the computer and "No grub / Rescue Grub". Pulled out the drive, plugged it in and tried again, and boom came up. Reboot again, taking the drive off again, and again "No grub / Rescue Grub". Plugged the drive in, booted up, and selected "Windows 10", and have been doing my work day as usual. Secretly panicking.

4- POST screen, has very little, no typical text. It is a HP, don't know if HP don't display instructions on the POST screen. i did try "Del", F12, F8, and F2 with no luck.

---

### Post by tea for one on 2022-02-02
> **p2bc said:**
> It is a HP, don't know if HP don't display instructions on the POST screen. i did try "Del", F12, F8, and F2 with no luck.

Make sure the boss isn't looking............

F10 for HP Bios and F9 for Boot Menu
Any joy?

---

### Post by p2bc on 2022-02-02
> **tea for one said:**
> 

F10 for HP Bios and F9 for Boot Menu



Thanks, did not know they were different, will try later.


I don't mind working late, and have been, that is how all this started. My boss is cool. I.T. is another story though. 

True story: First day, Jan 10th, got yelled at by I.T. because he said I was talking down to him and disrespecting him, that he has been with the company for 12 years.
What did i say, you wonder to elicit such a response; I was explaining what I did up to that point to rectify the problem before i actually called him, so as to not bother him. And how i kinda know a little bit about computers. Been a linux user for 14+ years, and have been studying for my CCNA. So I get accused of being disrespectful. Best part, he hung up on me before I finished. I had the pleasure of calling him back and said," And you claim I disrespected you, but you just slam the phone down on me." He replies, "You said you got connected so..." I said, "Yes, but there is more than one issue. If you hadn't been so quick to hang up you would know that."  

So you can see, I HAVE TO GET THIS FIXED!

---

### Post by p2bc on 2022-02-02
@tea for one

Oh my goodness, thank you, thank you!

Press F9 for boot menu, and was greeted to a list:

- UFEI - hp DVDRAM GUBON
- Legacy - hp DVDRAM GUBON
- Legacy - Intel Volume 0
- Legacy N/W - IBA GE slot 00C8 v1550
- Boot from file

Picked - Legacy - Intel Volume 0, made the most sense to me, ...and... it worked. I even did it twice, to make sure it worked.

I was never so happy to see the stupid spinning loading wheel of Windows until that very moment.


I now can go home. And breath a sigh of relief.


Thank you all again. I appreciate it. Stressful afternoon, but i learned something, so not all bad.

1. -  Boot Repair app (that will be useful)
2. - F9 and F10 for HP (ok if I ever get another HP, or have to troubleshoot someone's HP computer)
...and the most important one ...
3. - Never do something like this again on a work computer. ( I will probably forget, or laugh about it in a couple of weeks; Right now though... No)


Thank again everyone.

---

