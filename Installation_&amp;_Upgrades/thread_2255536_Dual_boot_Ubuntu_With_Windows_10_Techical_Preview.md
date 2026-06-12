---
title: "Dual boot Ubuntu With Windows 10 Techical Preview"
date: 2014-12-05
forum: Installation &amp; Upgrades
---

### Post by Anthony_Corda on 2014-12-05
Ok, so my computer originally came with windows 8 preinstalled on it. At first I had Ubuntu in a dual boot configuration with Windows 8. Now I updated my computer to Windows 10 Technical Preview and reset everything on it. I have my bootable USB stick ready to go. I have disabled fast startup and secure boot. But question is how do I boot from my install Ubuntu USB.

OS:
Windows 10 technical preview

I will appreciate the help!

---

### Post by oldfred on 2014-12-05
Windows 10 Dual boot on Toshiba works - sudodus
[http://ubuntuforums.org/showthread.php?t=2246751&p=13137869#post13137869](http://ubuntuforums.org/showthread.php?t=2246751&p=13137869#post13137869)

Should be the same as any install. You did install in UEFI mode and not convert back to BIOS boot?

What brand/model computer?

      
 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

See also many useful links in the link in my signature below.

---

### Post by Anthony_Corda on 2014-12-05
What do you mean by [B]You did install in UEFI mode and not convert back to BIOS boot?
[/B]

I have the Install Ubuntu written to my flashdrive and now how do boot from it.

---

### Post by oldfred on 2014-12-05
Your UEFI should show two boot options for the flash drive. One clearly says UEFI and the other typically is just the label/brand of the flash drive. So you boot the UEFI option.

Attached is one example which shows toshiba UEFI and just toshiba.

Be sure to use Windows to shrink the NTFS partition to make room for Ubuntu. And reboot immediately so it can run chkdsk and update for its new size. Also make sure fast boot or always on hibernation is off. Windows likes to reset to its defaults. And best to have secure boot off in UEFI. But must have UEFI on, not CSM/Legacy/BIOS.
Best to also make a Windows repair flash drive.
Do not create partitions with Windows, but either gparted in advance (recommended) or with Ubuntu installer.
If Windows not seen, then only use Something Else to install.

       UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shrink Windows if installing on same drive and reboot Windows first. 
But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by Anthony_Corda on 2014-12-05
D: My USB doesent show up ts a 16gb sandisk

Ive tried using wubi.exe but I get the error "wubi does not currently support EFI" but I noticed there are other OS like kubuntu, lubuntu ETC but are there any other OS Like a clone of Ubuntu because... I WANT UBUNTU

---

### Post by eight.coffee.beans on 2014-12-05
Simple copy/paste won't do the job like it does in making bootable Windows 8/8.1/10Tp USB, you'll have to use software like uNetBootIn for making a bootable Ubuntu USB. When you've done that you should enter your notebook/laptop/PC setup by hitting ESC/F1/F2/DEL (depends on the device) and select your USB. For example I booted from UEFI: KingSton Trans-It DataTraveler so you should find something similar in your options.

---

### Post by Anthony_Corda on 2014-12-05
I used unetbooten

---

### Post by eight.coffee.beans on 2014-12-05
> **Anthony_Corda said:**
> I used unetbooten

Are you using laptop/notebook or PC?
If you're using laptop/notebook search Google to see how to enter device's setup or motherboard if using PC.
And just for information, how did you manage to dual-boot before?

---

### Post by Anthony_Corda on 2014-12-05
Ok when im booting up I pressed f11 and it said select boot device and my flash drive does not show up! When I was on windows 8 all I did was disable secure boot, fast start up and put my flash drive in and it would say install Ubuntu. So I did. I just found something! In advanced startup and when I go to device it sais Ubuntu and then when I start it says GNU GRUB. and press tab for a list of commands

im am on a laptop

---

### Post by eight.coffee.beans on 2014-12-05
> **Anthony_Corda said:**
> Ok when im booting up I pressed f11 and it said select boot device and my flash drive does not show up! When I was on windows 8 all I did was disable secure boot, fast start up and put my flash drive in and it would say install Ubuntu. So I did. I just found something! In advanced startup and when I go to device it sais Ubuntu and then when I start it says GNU GRUB. and press tab for a list of commands

From this I'd say the USB isn't prepared correctly to be honest...
I'm not sure what else could be the problem, but does [this link ]("http://www.thewindowsclub.com/uninstall-windows-10-technical-preview")help by any chance in removing Windows 10 Tp?

---

### Post by Anthony_Corda on 2014-12-05
Ok im just gonna go back to win 8 and triple boot the tp and ubuntu

---

### Post by eight.coffee.beans on 2014-12-05
> **Anthony_Corda said:**
> Ok im just gonna go back to win 8 and triple boot the tp and ubuntu

No need to triple-boot if you don't want to. If you have Windows 8 USB/DVD boot from it and wipe out the Windows 10 Tp partition and install Windows 8 and then dual boot it with Ubuntu. I would recommend you installing Windows 10 Tp inside of VMware or VirtualBox if you are eager to test it. :)

---

### Post by Mark Phelps on 2014-12-06
>  Now I updated my computer to Windows 10 Technical Preview and reset everything on it. 

That's actually not a very good idea at this point.  

I'm running Win10TP and it has bugs -- but then, it's only really an "alpha" release.  The actual "beta", what MS calls the Consumer Preview, will be coming out in late January.  The stable release (known as the RTM) won't be out until the Fall.

Since MS won't allow you to "rollback" from an in-place Win10 TP "upgrade install", your better approach, if you want to retain Win8.1, would be to install Win10TP in a VM.

---

### Post by CDuce on 2015-09-13
I'm currently having the same issue, when i got windows 10 on my HP/Compaq PC, who used to have Win 8.1 originally, i've tried literally everything, from CD/DVD to bootable USB, none of these appear in the boot menu, my CD/DVD is a windows 7, and the bootable usb flash has Ubuntu in it, and just to make sure there was nothing wrong, i tested both of them on my DELL PC that runs under Ubuntu, and both worked perfectly.

---

### Post by Mark Phelps on 2015-09-13
CDuce: You most likely have a VERY different situation, in that Win8.1 machines generally have UEFI -- which makes it a very different problem to solve.  You would do better opening your own new thread, than leeching off a thread that is over 9 months old.

---

