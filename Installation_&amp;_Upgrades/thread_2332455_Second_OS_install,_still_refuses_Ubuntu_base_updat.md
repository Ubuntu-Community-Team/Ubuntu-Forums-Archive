---
title: "Second OS install, still refuses Ubuntu base updates. Auto-partition incorrect?"
date: 2016-07-31
forum: Installation &amp; Upgrades
---

### Post by giga+bytes on 2016-07-31
The first install of Ubuntu was problematic and I found out I did not disable "secure boot" in the BIOS. I believe I have the BIOS properly set for Ubuntu this time, yet software updater still will not install Ubuntu base updates, which I assume are *important* updates.

System specs: Lenovo G50 laptop; AMD 6410 CPU, 8GB RAM, original HDD (with OEM Win10, never activated) replaced with Samsung 850 EVO & Ubuntu (no Windows at all), BIOS is a Legacy type (I have a UEFI desktop, so know the difference).

I chose "Erase disk and install", then ran "lsblk" to see what it created for partitioning, which showed this:
sda          232.9G
sda1 vfat  512m /boot/efi
sda2 ext4  225.4G /
sda3 swap 7G [swap]
sr0           1024m

I forgot to check what the first Ubuntu auto-install created, so cannot compare to see if anything changed. I know that swap partition seems rather much, but am not familiar enough with partitioning to know if there are any other mistakes.

The only thing I changed in the "Ubuntu Software Center" is switching the download server from my countrys' to the main, because I encountered problems with the first install & downloading updates from my county's server.

Other than that, I activated and configured the UFW, following the thread in these forums titled "Creating a firewall for your Ubuntu desktop".

Do I have to reinstall and manually configure the partitions? Or is that part fine, and something else needs to be done?

---

### Post by Bucky Ball on 2016-07-31
I can't help with your problem but I can add this which will save you some time and stop the circular motion. Stop wasting your time re-installing. Your problem appears to have nothing to do with that. Your system is running fine apart from the update issue I'm presuming? If so, best to try and figure out the issue. A re-install will more than likely bring you back to square one (exactly where you are now).

Open a terminal and run these commands:

```
sudo apt autoremove
sudo apt clean
sudo apt autoclean
sudo apt update
sudo apt full-upgrade
```

Post back any errors you get from any of these commands or anything odd that happens. Use code tags for terminal output please (see the link in my signature).

While your patitioning may not be the way I'd go about it myself (no need for a /swap that big) there is absolutely nothing wrong with it and how you partition your drive has nothing to do with whether you can update or not ...

* Just a point. You say 'BIOS is a legacy type'. You mean you wanted to install in legacy mode? If so, you have installed in UEFI. At least, you have a UEFI partition on the drive created by the auto-install (sda1).

---

### Post by giga+bytes on 2016-07-31
It is only the second install (first re-install), so only one circle so far. Was previously having lock-ups with green lines, occasional system restarts and other odd issues. Just a few minutes ago it restarted for no reason while online.

What I meant regarding the BIOS is it is not a UEFI type. It is a simple old-school keyboard arrow navigation type. I was hoping the auto-install would recognize that (now that secure boot has been disabled), but apparently it did not.

That last command, "full-upgrade", does that mean to the newest Ubuntu version? I am using 14.04 right now (forgot to mention that) and from what I have been told (and read in discussions) I should stay with that for now, until AMD support is better for 16.04 (though if I recall that is only for those who want to use the proprietary driver). Should I switch to 16.04 instead?

---

### Post by Bucky Ball on 2016-07-31
No. 'full-upgrade' will NOT upgrade your system to 16.04. It will upgrade anything in your current release that needs to be. 

If you are wanting to install in legacy I'd start again as you have a UEFI install, judging by the EFI FAT32 partition you have there. What is surprising is that this has happened if your motherboard/BIOS can't do UEFI. :-k

The last link on the first link of my signature is 'Boot Repair'. Could you perhaps give the output from that. When you launch Boot Repair, you will see an option to create a bootinfo summary. Don't run the recommended repair, just the bootinfo. Once complete, it will provide you with a link to the bootinfo summary. Please post that link here so we can have a better look at what you have there. 

Your other option is to use 'Something Else' at the partitioning section of the install and partition the drive manually. 

All I can think is that your BIOS can handle UEFI installs, something is still switched on in there, or you have chosen to launch the install media in UEFI mode (which is how you get a UEFI install). Puzzled as to how an EFI partition could have appeared in your install if your BIOS can't deal with one ... (even more puzzling is that you can boot your machine into an EFI Ubuntu install).

---

### Post by giga+bytes on 2016-07-31
I just looked in the BIOS and found there is an option to select *either* UEFI or Legacy, and it is set to UEFI. The two things I had to check for (this & secure boot) and I somehow missed both of them!

I want to set it to Legacy and re-install *once* more, this time _manually_ configuring the partitions properly for an Ubuntu-only install. What I need is help with the partitions. From what I understand it should be partitioned like this:

swap (2GB to 4GB size, Primary partition type)
/ (root, 20GB to 25GB size, Primary partition type, Ext4 journaling file system)
/home (rest of SSD space, Logical partition type, Ext4)

Is that correct?

---

### Post by Bucky Ball on 2016-07-31
If you want to go that way, yes. I'd go in this order, which is rule-of-thumb, but not essential:

/ = 20-25Gb, which is probably more than you'll need;
/home = large as you like;
/swap = 2Gb on the end of the drive after /home.

FYI, a lot of folk don't use a separate /home partition, preferring to leave Ubuntu to create default /home partition inside / and linking to folders on a separate data partition from that (I have four, from memory, install which all use the same data partition this way and therefore access the same data, no redundancy or confusion).

For your purposes, though, the /, /home, /swap should work fine.

You may want to [have a look at this]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352") to help you along with the Something Else part of the install. Any questions, just ask. ;)

(One last point: it was advisable to leave part of an SSD 'unallocated' space at the end of the drive to extend SSD life expectancy. This is not so important anymore but I still leave about a sixth (20Gb on a 120Gb SSD) unallocated and not as part of an extended partition. Others may have more to add re. this.)

---

### Post by giga+bytes on 2016-07-31
Thanks, I will create those partitions in that order. That is actually the guide I was referring to and am following, so good to know it is recommended!

I have heard about that with SSD's. I can do that, and then use it for extra space if needed later, or add another /home if I want.

---

### Post by oldfred on 2016-07-31
UEFI uses the newer gpt partitioning system rather than the 35 year old MBR partitioning.

And Ubuntu can boot in BIOS or UEFI from gpt partitioned drives. Windows only boots in UEFI mode from gpt.
But you need an ESP - efi system partition to boot in UEFI mode or a 1 or 2MB unformatted partition with the bios_grub flag. I normally add both partitions, so I can later change drive to another system or change how I want to boot.

Since you have an ESP, your drive is probably gpt already. And grub will not install to MBR correctly without the bios_grub partition.

       I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

---

### Post by giga+bytes on 2016-08-01
Are you saying that I need to add another partition? This computer will be Ubuntu only, I will not be installing Windows on it at all. Is that bios_grub partition still needed in this case?

---

### Post by giga+bytes on 2016-08-01
Well, the main reason I was keen on installing in Legacy mode is because I read that it is the best method for installing Ubuntu 14.04. If it does not make any actual difference, then I need to figure out whether to change anything with the installation or not. If there will be no benefit whatsoever, then there is no point.

---

### Post by Bucky Ball on 2016-08-01
No benefit. Each has its pros and cons. You are not limited to four partitions on the one physical hard drive with EFI. That is one advantage.

---

### Post by oldfred on 2016-08-01
There are/were some vendors UEFI that are not very good and made it difficult to use UEFI. But we now seem to have discovered work arounds for most systems. And vendors have updated UEFI.

There are issues with Atom processors and AMD video where 14.04 seems to just work, but boot parameters or newer drivers are required. I think those issues apply whether UEFI or BIOS.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
But if you use gpt and want to also install Windows, you must use UEFI. Ubuntu can boot with BIOS or UEFI from gpt partitioned drives.

       
 UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by giga+bytes on 2016-08-01
Until I am absolutely sure what to do, I put a re-install on hold. Especially considering you are both saying it makes no noticeable difference and should not be the reason for the problems I am having.

The last thing I did yesterday before calling it quits for the night was to run those commands Bucky Ball posted earlier in this thread. The first 3 (autoremove, clean and autoclean) I got the message "E: Invalid operation", but the last 2 commands did a bunch of things and everything seems to have gone well with no problems. Out of curiosity I checked the software updater to find the Ubuntu base update (that refused to install) no longer shown, so I am guessing it was installed.

Reading up on Ubuntu 16.04 there was mention that the software center/software updater in 14.04 has been in need of replacing for a while. Could that be the reason for base updates not installing? Should I be getting updates via the terminal instead?

---

### Post by oldfred on 2016-08-01
Software Center & updates are two separate things.

I actually use the old synaptic tool to get new software or install. The I see the exact name of the application where in Software Center you just get the generic name of the app. And you can get some more info on dependencies, and info on app.

Updates are usually a pop-up. But at any time you can run them from  command line.

I have 16.04 and it has a new Software Center. But I have not even used it.

---

### Post by giga+bytes on 2016-08-02
Since the purpose of this thread may be solved (will know in a few days or so), I will start a new thread to ask more specifics about partitioning.

---

### Post by oldfred on 2016-08-02
My new install process is now a new 25GB partition and new clean install. 

I still have my old working 14.04 install and my new working 16.04 install on my SSD. And I have several of the 6 month releases in 25GB partitions on HDD, so I can see what changes. Each 6 month change is not usually large, but by the change to new LTS the changes can add up.

---

### Post by giga+bytes on 2016-08-02
Every day I learn more about how very different linux OS's are from Windows!

Well one problem has reappeared so far: last night a family member was watching a show online and the laptop restarted itself.

---

### Post by Bucky Ball on 2016-08-02
Now that is unusual and the stuff of a new thread if you'd like some support with that. :-k

---

