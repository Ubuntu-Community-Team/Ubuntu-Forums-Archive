---
title: "installing ubuntu alongside Windows 7"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jsowoc on 2009-10-23
A friend (completely new to computers) is buying a laptop with a single hard drive and Windows 7 pre-installed. I showed them Ubuntu 9.10 RC netbook remix, and that is what they want to use as their primary OS. They would like me to set it up, and I'd like the installation to run as maintenance-free as possible.

I don't want to get rid of Windows 7 entirely, as they may need it for some specific application sometime. I'm quite experienced at dual-booting Ubuntu/XP in all its combinations, but I've read several threads about problems with dual-booting with Windows 7 (a combination I haven't tried yet). The problems mostly pertained to upgrades from Vista or to multi-drive setups.

Does anyone have advice as to whether a Wubi (I know I need to run it in Vista-compatibility mode) or a grub installation would be easier to install/maintain? Anything special I should know about dual-booting Windows 7 (as opposed to XP) with Ubuntu?

Thanks for any advice.

---

### Post by Mark Phelps on 2009-10-24
While it's true that people don't post here when stuff works, nonetheless, we've got a LOT of posts with folks being unable to get Wubi to work in a system where Windows 7 was installed to a clean drive.  Appears to have something to do with the new 2-partition installation scheme of Windows 7.

Your best bet would be to use the standard dual-boot setup where Ubuntu has its own partitions.

Before you do that, however, use the new Recovery Disk creation built-in feature of Seven to make and burn your own Recovery CD.  That might come in valuable later.

After that, use the Seven built-in Disk Management utility to shrink the second NTFS partition to make room for Ubuntu.  Do NOT use the Ubuntu installer to do that.

Then, when you boot from the Ubuntu CD, use Manual Partitioning to install the OS.

This is the lowest-risk approach for installing Ubuntu in a preloaded MS Windows system.

---

### Post by jsowoc on 2009-10-24
Thank you for the advice. I was thinking the independent Windows/Ubuntu partitioning scheme would be the best, but wanted to make sure it was the path of least resistance.

Here is what I understood is the lowest-risk approach:
1. Create a "Windows 7 Recovery Disk" (where do I find this option normally?)
2. Using Windows 7 disk management, I shrink the Windows 7 partition to create room for Ubuntu (is this easy to find?)
3. Select manual partitioning in Ubuntu install, and manually create my Ubuntu partitions (I can do this :-) ).
4. ...

Would you suggest a safer option to be using grub to boot both Windows or Linux, or would you suggest installing grub to /dev/sda3 (or whatever the /boot of Ubuntu would be), and then pointing the Windows bootloader there (if that is possible)?

---

### Post by jsowoc on 2009-10-26
I got it working, so am posting a "how-to".

"Safe way to dual-boot Windows 7 and Ubuntu w/out altering the boot record."

The laptop with Windows 7 pre-installed had 3 primary partitions:
- system recovery (~20 GB)
- Windows boot (~100 MB)
- Windows (~230 GB)

You can shrink the last one to ~100 GB (within Windows). Doing a custom install, make a 4th primary partition and install Ubuntu onto it. Install grub to /dev/sda4 (or whatever the new Ubuntu partition is).

Now, you can make grub in /dev/sda4 be the thing that starts by changing which is the active partition in fdisk. Run:

```
sudo fdisk /dev/sda
```
and make the Windows boot partition inactive, and Ubuntu's one active.

Violà - grub should load, and allow you to boot into Windows 7. If you ever want to go back to the Windows bootloader, simply go back into fdisk, and change which partition is active.

---

### Post by coffeecat on 2009-10-26
> **jsowoc said:**
> I got it working, so am posting a "how-to".

Congratulations, but a few comments.

> **jsowoc said:**
> The laptop with Windows 7 pre-installed had 3 primary partitions:
- system recovery (~20 GB)
- Windows boot (~100 MB)
- Windows (~230 GB)

Your particular laptop has three primary partitions. I presume the 20GB system recovery is some sort of manufacturer's utility. Some manufacturers split their hidden/utility/restore partitions into 2 partitions with earlier versions of Windows. If they do this with W7 (only time will tell), what with W7's 2 partitions, that will use up the full quota of four primary partitions and snooker anyone wanting to dual-boot with Linux. I suppose this is a watch-this-space scenario.

> **jsowoc said:**
> make a 4th primary partition

Which means that you've used up the full quota of primary partitions and have no room for further flexibility - such as setting up a multiboot with more than one flavour of Linux. It will also mean that you don't have a swap partition. It might be better to create an extended partition in the space you've made and then make as many logical partitions as you need in the extended.

> **jsowoc said:**
> make the Windows boot partition inactive, and Ubuntu's one active.

Aaaargghh! No. :wink: Linux doesn't need the boot flag. Linux is indifferent to the boot flag. You don't have to make a Linux root partition active, but you do need to make a Windows one active - but you're probably getting the Windows boot flag set with the "makeactive command" in the grub Windows stanza.

Did I say that you don't need to make a Linux partition active for it to boot successfully with grub? :p


Hope this helps.

---

### Post by jsowoc on 2009-10-27
> **coffeecat said:**
> 
Aaaargghh! No. :wink: Linux doesn't need the boot flag. Linux is indifferent to the boot flag. You don't have to make a Linux root partition active, but you do need to make a Windows one active - but you're probably getting the Windows boot flag set with the "makeactive command" in the grub Windows stanza.

Did I say that you don't need to make a Linux partition active for it to boot successfully with grub? :p


From what I understand, the only way for grub to get loaded is either to:
1. install it directly to /dev/sda, overwriting the Win MBR (something I didn't want to do)
2. install it to a primary partition (such as /dev/sda4), and make that partition "active" -> I don't need to overwrite the Win MBR, simply mark it as inactive

Was it possible to make an extended partition, make it active, and have grub boot from /dev/sda5? I know that I didn't make a separate /home, /var, /boot, and swap, but I thought I needed to install grub onto a primary partition.

---

### Post by solnyshok on 2009-10-27
You don't need this "active partition" stuff. Simply choose install grub to /dev/sda (or /dev/hda) works. 

However, there is one more thing to check. As far as I remember, when I played with "active" partitions on my setup, Windows would loose ability to properly hibernate-wakeup if you make its partition "in-active".

---

### Post by coffeecat on 2009-10-27
> **jsowoc said:**
> 2. install it to a primary partition (such as /dev/sda4), and make that partition "active" -> I don't need to overwrite the Win MBR, simply mark it as inactive

OK, I think I see what you mean, but it's **so** much easier to let grub write its stage 1 to the mbr. If you ever tire of Linux and want to restore the Windows bootloader back to the mbr, and if you don't have a "proper" Windows installation disc to do a "FIXMBR", all you need is the [SuperGrub Disk]("http://www.supergrubdisk.org/") which can also restore the Windows mbr in seconds. Every Linux user should have one in his/her toolkit because it can repair broken grub as well, or simply boot into any OS on the hard drive.

---

### Post by Jazmac on 2009-10-27
Seems to me Wubi breaks stuff at the boot level.  I'm not sure what or why but with Windows 7, Wubi does something weird but doesn't indicate a problem and still doesn't run.  I have a separate hard drive I use for Ubuntu Karmic. My other hard drive is Windows 7.  Neither are in the computer at the same time.  I swap them out especially since Karmic is still an RC.  

Last night I dropped my Windows 7 drive back in and lo and behold, Grub is asking to remove all disks and hit any key to continue.  I don't know why or how except that Karmic may leave bird droppings in my external drives that are read at boot up but I'm getting Grub messages and this hard drive never touched Ubuntu.

That Grub remove disk message is the same I get from my Karmic drive which is pure Ubuntu.

So at this poiint, I don't think Windows 7 and Ubuntu dual boot is quite there.  Something in Wubi is different because Jaunty worked before with 7 but Karmic does not.

-JazMac

---

