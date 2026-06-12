---
title: "Problems adding Ubuntu 22.04 to multi OS sys. Looking for better UUID understanding"
date: 2024-01-20
forum: Installation &amp; Upgrades
---

### Post by 5circles on 2024-01-20
[Background: long time Ubuntu user, never much attention to partition UUIDs and think I need to learn more about boot process.]

My system had 1TB drive with Windows (unused after installing Ubuntu except for rare problem resolution). I had Ubuntu 14.04. 16.04 (two flavors) and 18.04 which was my workhorse. I skipped 20.04 for some reason, and am now trying to get 22.04 and 18.04 both able to boot.

I cloned the hard drive using dd because SMART numbers on the old drive were making me making me concerned - to a newer 1TB (different manufacturer).  Because I wanted to have both drives in the system, at least temporarily, I changed UUIDs for the partitions using gdisk; the drives are GPT.  I thought that I changed all the partition UUIDs using randomizing from gdisk. But I could be wrong on that - perhaps only the Ubuntu partitions.

Installed 22.04 on a partition I'd previously earmarked for 20.04.  Also have a /data partition which 18.04 was using for MySQL and Virtual servers under Apache2.  

22.04 is working to some extent. [Lots of frazzle, and it's not fully up yet - remote access, Samba, LAMP.]  I took the original hard drive out for Ubuntu 22.04 installation.

I had the impression that the installation/boot process for 22.04 would take the UUIDs I'd changed on the new disk and use them to populate files I could interrogate using 'disks' 'lsblk' 'blkid' and Gparted. I don't know exactly what led me to think  that, but I could see the UUIDs with various tools that didn't match the UUIDs I could see with 'gdisk'.   The 22.04 installation changed the order of the partitions (virtual I assume), as well as the UUIDs.

Question - finally. I'd like to understand the processes that Ubuntu installation, grub updating, and boot use which result in changes to the UUIDs on a drive, and also modifying the /etc/fstab file. If there is a general explanation or two, that would be great.  Did Ubuntu 18.04 use the same techniques, or was Mount by UUID optional with that version?  It's driving me nuts to be faced with what seems like a moving target.  Thanks!

There's a follow up question that I was going to wait to ask. But if anyone has taken the trouble to read this much, it may be quicker to include it - it's possibly related.
[INDENT]I mentioned that I wanted to have the ability to boot multiple versions of Ubuntu. This is probably temporary, once 22.04 is at the point I want. 18.04 is what I need right now. 
When I try to boot 18.04, it goes through the expected Cleans etc. that happen when switching between versions, then displays the graphical startup. The startup never turns into the full graphical desktop. Instead, it presents various error messages about USB 3-6 - partitions for Windows and Recovery - including "[FONT=Courier New]can't read configurations, error -110[/FONT]", and "[FONT=Courier New]Unable to read config, index=0, descriptor /all.[/FONT]" .  I haven't been able to find any information that suggests any steps to take. I've used journalctl to look for related messages, with no success.[/INDENT]
My Questions for the 18.04 reboot fix are: What are my next steps? Can I run update-grub safely (after booting to 22.04)? I think I just answered that - NO. It's stuck with the same messages as I saw on 18.04.

Any help is most appreciated!

---

### Post by oldfred on 2024-01-20
It may be difficult to get 18.04 working.
Since Ubuntu 18.04LTS (Bionic Beaver) became unsupported in April, 2023, Ubuntu 18.04 has passed its End-Of-Life date, and is no longer supported unless you had installed Ubuntu Pro for extended support.
 Upgrade to a supported release.
[https://fridge.ubuntu.com/2023/05/13/extended-security-maintenance-for-ubuntu-18-04-bionic-beaver-begins-31-may-2023/](https://fridge.ubuntu.com/2023/05/13/extended-security-maintenance-for-ubuntu-18-04-bionic-beaver-begins-31-may-2023/)

UEFI boots using GUID/partUUID to find ESP. Then a 3 line grub.cfg in ESP uses UUID of / to find & boot grub.cfg in your install.
Last install is normally the default in ESP and then from grub you can boot other working installs.
sudo efibootmgr -v 
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid
cat /etc/fstab
cat /boot/efi/EFI/ubuntu/grub.cfg  #may not work if fstab has 0077 permissions, then mount & use from live installer.
Check partUUIDs match to ESP - efi system partition(s) you have. Make sure UUIDs are correct

You can see all of the setting in one report. I run this & save into /home to document my system & then /home is backed up.
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed, may default to wrong install. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by 5circles on 2024-01-20
Thank you for the very clear explanation of the process and the warning about 18.04.  It's a pity that I didn't pursue installing 20.04 closer to the time it was released, but Covid and a complicated house move got in the way. 

Having just tried a couple of the steps, I think it may be simpler and faster to finish enough of the installation of the software I need on 22.04 anyway, move the important data from 18.04, and live with anything I discover I wish I still had from 18.04 as that comes up.  I'm not absolutely certain of that decision, but I wanted to mention it in the thread because I have other high priority things to take care of, so I'm trying to avoid spending more time on this for a few days.

---

