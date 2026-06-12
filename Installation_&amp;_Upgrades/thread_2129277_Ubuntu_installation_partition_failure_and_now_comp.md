---
title: "Ubuntu installation partition failure and now computer is stuck in reboot?"
date: 2013-03-25
forum: Installation &amp; Upgrades
---

### Post by annularvector on 2013-03-25
Deleted

---

### Post by oldfred on 2013-03-25
Probably better to use 12.04 as it now has long term support.

Did you shrink Windows using Windows Disk tools? Windows need to make repairs on a resize and issues like you have do not give it a chance to make those repairs. You now probably need a Windows repairCD or flash drive to run chkdsk.

But lets see what is where. From your live installer download this and run the BootInfo report.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by annularvector on 2013-03-26
I did the boot repair. Here is the address, [http://paste.ubuntu.com/5648850/](http://paste.ubuntu.com/5648850/)

---

### Post by darkod on 2013-03-26
According to both fdisk and parted, there is no space missing. It's much better and recommended to shrink the win7 partition using windows Disk management, instead of doing it with the ubuntu installer.

Do you have a win7 dvd or rescue cd to try repair the boot process?

---

### Post by annularvector on 2013-03-26
I think so. Is there another way of repairing the boot without the CD?

---

### Post by darkod on 2013-03-26
It's best to try with the win7 dvd or rescue cd because i don't think it's the boot process actually. I think it's only confused because of the failed attempt to repartition and it needs chkdsk run on the partition. Linux tools can't help you run chkdsk.

If you boot into the repair command prompt with a windows disc, you can run it from there. That should allow you to boot windows as normal, then do the shrink in Disk Management, and after that you can install ubuntu into the unallocated space created.

---

### Post by annularvector on 2013-03-26
I don't want to install ubuuntu...I just want to get my computer repaired...:) 


Besides....its nice to run it from a live CD.

---

### Post by darkod on 2013-03-26
Then you have your answer. You need windows tools to repair windows. :) It should be ok after running chkdsk, the only thing you can do is try.

---

### Post by annularvector on 2013-03-26
Will it modify my files?

---

### Post by darkod on 2013-03-26
No, chkdsk only checks ntfs partition for errors and repairs them. The boot info shows that you correctly have windows bootloader on the MBR, and the win7 boot files present. That's why my guess it's it only needs chkdsk and will work fine. Unfortunately windows doesn't have live mode, and linux tools can't run chkdsk.

So, you have to do it either with a win7 install dvd (using the Rapir This Computer option and entering into a command prompt), or a rescue cd made from a win7 installation (you should make and have one of these at hand, especially if you don't have win7 install dvd).

If you need more detailed instructions about opening the command prompt from repair mode, you have them here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Ignore the other info, just focus on the How to restore windows vista or 7 bootloader. It explains how to open the command prompt.

---

### Post by annularvector on 2013-03-26
Finally!!!!!!It worked!!!! but now I have a Windows issue...........The accounts screen is not showing up...

Infact the reason I installed ubuntu was to fix the blank screen where the accounts were by loading a different OS. I think the issue is due to the fact that I have changed imageres.dll. Any ideas?

---

### Post by darkod on 2013-03-26
I have no clue about that. It might be time to look at some windows forums too. They can offer you better help with windows issues.

---

### Post by annularvector on 2013-03-26
OK....thank you anyway...I appreciate your help

---

