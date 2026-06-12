---
title: "Grub does not show up in dual boot Win 8.1 and ubuntu 13.10"
date: 2014-01-03
forum: Installation &amp; Upgrades
---

### Post by riton72 on 2014-01-03
First, happy new year to all
 I am stuck in front of a dual boot issue and I have no clue how to progress so I am coming here to see if someone can help me. 
For the first time, I built up a PC that works in UEFI. For the storage, I am using a 256Go SSD and  a 500Go HDD reused from my previous PC that I reformated. Both disk are formated in GPT. I first installed successfully Windows 8.1 Pro in 64 bit on the SSD with the secure boot desactivited then I installed Ubuntu 13.10 using a mix of partitions on the SSD and the HDD (e.g I put the swap partition on the HDD). Full détails of the partitions scheme after a Boot-info analysis is available here: [http://paste.ubuntu.com/6673838](http://paste.ubuntu.com/6673838)
The problem I am facing is that the system is booting systematically and directly on Windows. I did not succeed to go to Grub even trying to force Ubuntu through  the UEFI menu. I tried to use Windows boot manager using editbcd to get a boot choice menu without success. I then downloaded "boot-repair" that I put on a bootable USB key to try to fix the issue but when I launched it at boot, I get  the following messages that I do not understand:
-After the initial scan at boot-repair launch, I get the following message: ""EFI detected. Please check the options". Why this message ? what are the parameters to check ? I did not notice relevant parameters in boot-repair menus but I am not an expert. 
-After I got the following warning message:  " This will install necessary packages from Ubuntu 13.04 repositories. Please back-up your data before this operation". Here also, why this message ? It there something to worry about ?
-Finally when I tried to executed the automatic repair from Boot-repair it fails and I got the following message "Please close your package managers (software updater, ..., Synaptic) Then try again" while I did not launched any package managers and I do not see such software running. 

Any idea about what is going wrong ? Can someone help me ?

---

### Post by fantab on 2014-01-03
In your UEFI/BIOS 'boot menu' set Ubuntu as your first boot, or it should be before Windows. Right now its set to boot Windows first.
This will take you to Grub menu... boot Ubuntu and boot Windows. There is chance that your Windows will not boot. If Windows does not boot, then use Boot-Repair.

Those Boot-REpair warnings are precautions that BR takes. They don't mean much. Usually, the 'Recommended Repair' does the job for you. 
During the repair BR will ask you to rename EFI files... reply in 'NO'.
Also before you run BR, back up your EFI partition using any Windows tool for the job.

---

### Post by riton72 on 2014-01-04
My motherboard is a Gigabyte B85M-HD3, I mention it because I do not know how to do a screen capture of the UEFI to copy it here.
The UEFI boot menu has 6 entries ordered by priority: the first two are already Ubuntu (Ubuntu is explicitely mentioned in the naming), the next two are Windows (Windows is explicitely mentioned in the naming), then comes my DVD drive and finally the last one seems to be a kind of generic entry labelled with the SSD naming. Even with this set-up I always boot directly on Windows  ](*,)
Btw : Why do I see two Ubuntu and two Windows entries ? 
I have tried to modify the order but when the Ubuntu or Windows entries are listed first (whatever the order) I always boot directely on Windows and when one offor  two others are first I get a message asking to insert a bootable device and to restart. 

Do you have an idea of what is happening ? Thanks for your help and feedback

---

### Post by westie457 on 2014-01-04
This from your Pastebin > [COLOR=#BB4444]Failed to mount '/dev/sda4': Operation not permitted[/COLOR][COLOR=#BB4444]The NTFS partition is in an unsafe state. Please resume and shutdown[/COLOR] [COLOR=#BB4444]Windows fully (no hibernation or fast restarting)[/COLOR]
To turn off Fastboot follow this guide. [http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

To disable Hibernation go through the power options adjusting them as you want. If you want to reclaim the space used by the hyberfil.sys follow this. [http://www.techrepublic.com/blog/tr-dojo/delete-hiberfilsys-by-disabling-windows-hibernate-function/](http://www.techrepublic.com/blog/tr-dojo/delete-hiberfilsys-by-disabling-windows-hibernate-function/) It works in Windows 8.

After this run Boot-Repair again.

---

### Post by riton72 on 2014-01-05
Hum, this is odd :  I knew Windows 8 FastBoot can create some issues so it is disabled both in Windows menu (in line with the guide you point in eightforums) and also in the UEFI where I noticed a FastBoot option in the so-called "BIOS features" menu that I disabled. I re-run Boot-repair info analysis to check I did not change something by accident between the analysis report I posted above and now but I still have the sentence you noticed indicating "Failed to mount '/dev/sda4' ...."
I am completely lost. Do you have other ideas of things to do to fix or better diagnose the root cause of the problem ?

---

### Post by westie457 on 2014-01-05
Dis you go through the second link as well? Only asking because when I had a similar issue as you have I had to disable all forms of hibernation/sleep/suspend to force Windows to shutdown completely so the partitions are unmounted.
The Windows partitions need to be unmounted for the Ubuntu installer and Boot Repair can report the true size and state of the partitions and make any necessary adjustments.

The above had to be done for Windows 8 and after the free upgrade to Windows 8.1.
In Windows 8.1 if you press the Windows key+X you get a power-users menu, you can force a clean shutdown from there as well.

---

### Post by riton72 on 2014-01-05
Thanks to point this Westies457, I initially did not look at it as I though it was only related to reclaim the hyberfil.sys file space :oops:
I have now  followed the indication of the second link and I disable the hibernation in Windows register (meaning it was indeed still enable). I re-run Boot-repair info analysis the result is there: [http://paste.ubuntu.com/6697083](http://paste.ubuntu.com/6697083)[COLOR=#dd4814] [/COLOR]  as you can see the message indicating "Failed to mount '/dev/sda4' ...." has disapeared. However, running Boot-repair Recommended Repair still failed with the message error I reported earlier: "Please close your package managers (software updater, ..., Synaptic) Then try again" while I still do not see such software running. Would you have an idea to work around this one ?

---

### Post by oldfred on 2014-01-05
Boot-Repair has an option to mount a separate /boot, but does it even offer to mount your separate /var? If not you may be able to manually mount it? 

And why ext2 for /var? I have seen some issues with ext2 on new systems. It used to be suggested for small rarely written to partitions like a /boot or for flash drives. But now in those cases ext4 but with journal turned off is preferred.

---

### Post by riton72 on 2014-01-05
Thanks for this feedback, Oldfred.
After reading a book "A practical guide to Ubuntu Linux" from M.G Sobell, I choosed to put  the partitions with data that changes frequently: swap and /var on the HDD to preserve my SSD and I selected ext2 for /var just to select a filesystem without journaling feature - I did not know journaling can be turned off from ext4. 

I do not catch your point about mounting partitions with Boot-Repair. Are you saying that I need to mount (or unmount  ?) manualy partitions before running the "recommended repair" of Boot-Repair ? 

Do you think I should remove all the linux partitions and reinstall Ubuntu with all the partitions but the swap on the SSD ? Going further, is it possible to create the swap and the /var on the SSD at the install and to move them to the HDD afterward ? 

Thanks in advance for your guidance.

---

### Post by oldfred on 2014-01-05
You can move partitions around, but not really for beginners. I moved /boot to a new partition for all of 5 minutes and then realized I wanted a /boot/grub partition back with grub legacy. You have to preserve ownership & permissions and paths. 

Does Boot-Repair give an option to mount other system partitions somewhere. I have not looked at that detail.
Or just manually mount. But not sure how Boot-Repair would want it mounted. It runs a chroot and has you copy commands? I would include the mount there if possible.

I used to suggest swap on hard drive and that is what I have. But I have 4GB of RAM and almost never use swap. Or even if on SSD it would not be used, so it is not an issue.
I do the opposite as I want all system files including /home on SSD for fast access and put all data on rotating drive. But I move all data folders to rotating drive and link them back. The only thing I have not moved is .wine which I understand is not as easy to move as linking may not work or work correctly? But I only then use 11GB of / (root) out of my 28GB and .wine is nearly 2GB of that for Picasa.

I have seen many suggestions of moving temp folders into memory but have not done that. But I do make some settings to reduce writes to SSD.

---

