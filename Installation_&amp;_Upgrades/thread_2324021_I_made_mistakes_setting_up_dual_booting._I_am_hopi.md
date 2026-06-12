---
title: "I made mistakes setting up dual booting. I am hoping someone can help."
date: 2016-05-10
forum: Installation &amp; Upgrades
---

### Post by richardjwentworth on 2016-05-10
Greetings folks,

I recently took the leap into a more permanent dual boot setup. First I set it up on my laptop and all went very smoothly grub shows Ubuntu and windows 10 just fine and they play nicely together. I then decided to set up dual booting on my desktop. Unfortunately when I did I made 2 pretty big mistakes making it so I can only boot into Ubuntu. When setting up my desktop for dual booting I did not disable hibernation in windows 10 and I used gparted in the live installation to partion my hdd rather than shrinking it from within windows and restarting. Now no matter what I do I cannot boot into windows. I have tried quite a few suggestions that I have found online to get windows to run but unfortunately I have had no luck. I then went ahead and made a Win10 repair disk (need to use a disk unfortunately my desktop wont boot from usb) from my laptop in the hope that I could use that to restore Win10's boot and just redo grub after. The disk worked fine in my laptop but for some reason when I put it into my desktop I get a non system disk error when trying to boot from it. Now my desktop is quite a bit older than my laptop and has the normal plan old bios whereas my laptop has UEFI, I am not sure if that would make a difference or not. 

Any help you may be able to provide is GREATLY appreciated! Any information I can provide please let me know and I will do my best to provide it

Thanks,
Vort

---

### Post by grahammechanical on 2016-05-10
So, to be clear you have Windows 10 on both the laptop & desktop machines. But the laptop has a UEFI boot system and Windows 10 would have been installed in EFI mode and the desktop has a BIOS boot system. So, this version of Windows 10 would have to be installed in BIOS/Legacy mode. correct?

This is beginning to sound like a Windows 10 problem and not a Ubuntu problem. But Boot Repair might help. It has the option to restore a generic Windows boot loader. It may even fix what was the original cause of the problem.

The issue of running a Windows repair disk on a machine that it was not created on, is a secondary problem. Even if you were able to use that disk to repair the Windows boot loader you would have then needed Boot Repair to get the dual boot with Ubuntu working.

Boot Repair will also produce a BootInfo summary report and store it online and give a URL to the location. Post that URL in this thread and we may be able to get a better understanding of the situation.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

So, my advice is to ignore the secondary problem and fix the primary problem and then create Windows repair disks for each machine. The form factor (USB or DVD) is irrelevant information. As is the existence of a laptop that does not have any problems.

Regards

---

### Post by Mark Phelps on 2016-05-10
In all likelyhood, the damaged Windows filesystem can not be easily repaired -- given that you messed with a Hibernated Windows filesystem with GParted.

My guess is that the repair disc you made (from your laptop, right), is UEFI and that is why the desktop can't use it.

What MIGHT work is creating new Win10 boot media downloading from this link:  [http://windows.microsoft.com/en-us/windows-10/media-creation-tool-install?ocid=ms_wol_win10](http://windows.microsoft.com/en-us/windows-10/media-creation-tool-install?ocid=ms_wol_win10)

I would try that and see if the desktop boots from that.

You could also download an ISO file from this link and use ImgBurn (free disk burning Windows app) to burn a bootable CD:  [http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

If you then boot your desktop from that, you can try the various options to see if any of them repair the Windows filesystem.

Good Luck

---

### Post by richardjwentworth on 2016-05-11
My apologies for not getting back to you folks sooner. I have been busy with schoolwork. I have about a week off now so I should be able to get this back in working order now.

[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323"). I tried boot repair a couple of times before but unfortunately it did not work. I have run it again as you suggested so I could get the paste bin link.    [http://paste2.org/htCDPGFO](http://paste2.org/htCDPGFO)

Mark, I figured I may have issues trying to get it working again. I am out of blank dvds at the moment but if I am not able to get it working again via other means I will pick a few up on friday and give that a go.

Thank you,
Vort

[**[COLOR=#000000] [/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323")

---

### Post by oldfred on 2016-05-11
You are missing the /boot/BCD in your Windows install.
Windows only boots from the one primary NTFS partition with boot flag.
But grub looks for bootmgr & BCD to know which partition(s) may be bootable.

A Windows repair flash drive or some third party tools should let you recreate a BCD. But if Windows is hibernated that may be another issue.

With multiple drives, best not to use Boot-Repair's auto fix. That installs one copy of grub to all MBRs which often is not what is wanted.
But you have both operating systems on one drive. I might have installed Ubuntu on sdb or sdc, so I would have Windows able to boot on its own from sda. 
Grub only boots working Windows, so either direct boot from BIOS or Windows repair disk is then required.

Boot-Repair does not fix most Windows issues.

---

### Post by richardjwentworth on 2016-05-11
Oldfred, Thank you for your input. I can't boot directly from usb unfortunatly (system is older). I have been reading that the plop boot manager may allow me to boot into a usb drive by first booting into that. I may give that a try. Also I don't think my windows system was actually in hibernation mode when I installed ubuntu because I actually did a full shutdown before restarting. I just remember reading that you should disable it so I thought that may have been part of my problem. I do have a few blank cd's lying around so I may try burning a copy of Hiren's boot cd and give that Plop boot manager a go to see if I can get the usb repair flash drive to boot.

---

### Post by oldfred on 2016-05-11
Both my laptop and desktop from 2006 booted from USB port. How old is your Desktop?
On my desktop it had many  USB boot options and USB flash drive was none of them. It was under hard drives.

Full Windows shutdown may not be enough, you have to change some settings first.
 Fast Startup off (always on hibernation)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

---

### Post by richardjwentworth on 2016-05-11
I have had the system for about 6-7 years. I am not sure if it is due to the age or the fact that it is from Compaq. It is possible that they just didn't want to allow usb booting or whatnot. I did however get a repair usb working by using the plop boot manager but unfortunately it did not work to fix the problem. I am now creating a new install disk and I am just going to wipe it out and start over. Luckily all my important files are saves on my other HDDs so it won't be too much of an issue. After I reinstall windows I will probably go ahead and reinstall ubuntu after making sure to avoid the mistakes I made last time. Thank you all so much for your help. I really appreciate you taking the time out of your day to try and help me.

---

