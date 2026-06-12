---
title: "Grub Rescue after formatting partition"
date: 2016-04-03
forum: Installation &amp; Upgrades
---

### Post by lakeshore2985 on 2016-04-03
So basically I had two primary partitions on my test machine:

/dev/sda1 = Mint
/dev/sda2 = Ubuntu

What happened is I formatted /dev/sda2 for testing purposes and "active" GRUB was in that partition. Now when i reboot the machine it is looking for the bootable flag that was in /dev/sda2. How do I make it point to the GRUB in the /dev/sda1 partition instead?

Thanks!

---

### Post by grahammechanical on 2016-04-03
Actually, Grub is looking for its configuration file which was in /boot/grub/ on the Ubuntu partition (sda2).

As this is for testing purposes and as sda2 still exists you can re-install Ubuntu into sda2 using the Something Else option. And then load into Mint and use whatever method Mint uses to reinstall & update Grub and then format the Ubuntu partition.

---

### Post by lakeshore2985 on 2016-04-03
Thanks, but since I don't plan to reinstall Ubuntu on this machine (since it is only a testing rig), how could I proceed with rescuing the GRUB bootloader here?

For example, what if I delete the /dev/sda2 partition entirely? I know there's still a useable bootloader sitting in the Mint partition (/dev/sda1).

---

### Post by oldfred on 2016-04-03
You can restore the grub in sda1, better/easier to have done that before deleting sda2.

 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 

Many find Boot-Repair the easiest way.
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If using multiple installs or multiple drives, good to run the Summary Report from Boot-Repair which will tell you which install's grub is in MBR.

---

### Post by lakeshore2985 on 2016-04-03
> **oldfred said:**
> You can restore the grub in sda1, better/easier to have done that before deleting sda2.

 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 

Many find Boot-Repair the easiest way.
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If using multiple installs or multiple drives, good to run the Summary Report from Boot-Repair which will tell you which install's grub is in MBR.

Oh "Boot-Repair", yes... I remember this brilliant piece of software from a long time ago.

The thing here is, I've been doing a lot of tests lately. Was trying to figure out why some people still has a separate partition for /boot, but couldn't; does it have to do with where GRUB is? Like it would be "easier" to manage GRUB if I had multiple operating systems and needed to get rid of some from time to time? Like I wouldn't be running into these kind of bootloader problems if I had a separate partition only for /boot?

---

### Post by yancek on 2016-04-03
My understanding is that with LVM, you need a separate boot partition.  There may be other reasons, I don't know.  I've never used a separate boot partition.  In the past, there were limitations as to how far from the beginning of the drive boot files could be.  Not so much of a problem any longer.

> Now when i reboot the machine it is looking for the bootable flag that was in /dev/sda2

No, as explained above, it wasn't.  The reason you had this problem is because you had Ubuntu Grub code in the Master Boot Record pointing to the Grub boot files on sda2 which you formatted so the files were no longer there.  Most of the Grub code needed to boot is on the system partition.  You could have avoided that problem by booting into Mint and installing the Grub code from the Mint partition to the MBR before formatting the Ubuntu partition.

> Like I wouldn't be running into these kind of bootloader problems 

What you describe is not a bootloader problem, it is a user error.  The actions described above would have avoided it.

For a new user, having a separate boot partition would just complicate things.  There are numerous posts here about the system failing to boot with a separate boot partition because updates install new kernels frequently and the old kernels are not automatically removed which results in a boot partition which is full and thus unbootable.

If you plan to test different systems, in the future install Grub to the partition on which you are installing the new system and keep the Mint boot code in the MBR.  You can then just boot Mint and run:  sudo update-grub.  You could also install Grub to the MBR with each new system and make sure you do not format or delete that partition until you have put Grub from another system in the MBR.

---

### Post by oldfred on 2016-04-04
You just need to know which operating systems version of grub is in MBR.
Often best way to tell is Boot-Repair's summary report or the older bootinfoscript (which is really now part of Boot-Repair's report).

And then always install the boot loader from the system you want in MBR, before deleting any other system.
And normally last installed system will be the one in the MBR, unless you specify otherwise.

---

### Post by lakeshore2985 on 2016-04-04
> **yancek said:**
> No, as explained above, it wasn't.  The reason you had this problem is because you had Ubuntu Grub code in the Master Boot Record pointing to the Grub boot files on sda2 which you formatted so the files were no longer there.  Most of the Grub code needed to boot is on the system partition.  You could have avoided that problem by booting into Mint and installing the Grub code from the Mint partition to the MBR before formatting the Ubuntu partition.

So does that mean I could have also run "*sudo grub-update*" from Mint even after I had formatted/deleted the other partition entirely? Or in other words, one can rewrite the MBR information at any time or circumstances, regardless of where it was previously pointing to? Alright I guess not.

> What you describe is not a bootloader problem, it is a user error. The actions described above would have avoided it.

For a new user, having a separate boot partition would just complicate things. There are numerous posts here about the system failing to boot with a separate boot partition because updates install new kernels frequently and the old kernels are not automatically removed which results in a boot partition which is full and thus unbootable.

Yes, I know. I am just testing things around trying to learn some basic stuff. Basically throwing myself into as many problems as possible, and then try to fix them.

So worst case scenario here is that by having a separate /boot partition it can make the system unbootable if the user chooses to update the kernel? Or updating software messes with kernels too? I mean, by "kernels" you refer to the Unix kernel, right? The system kernel.

> If you plan to test different systems, in the future install Grub to the partition on which you are installing the new system and keep the Mint boot code in the MBR. You can then just boot Mint and run: sudo update-grub. You could also install Grub to the MBR with each new system and make sure you do not format or delete that partition until you have put Grub from another system in the MBR.

So here is what it comes down to... For example, I was wondering which to install first, Linux Mint or Ubuntu Server since the latter doesn't have a GUI, it's much harder to modify GRUB settings using GRUB-CUSTOMIZER software without a graphical interface. But you're saying one can log in to Mint or whatever distro and run "*sudo grub-update*" and it will rewrite the MBR code back to Mint, so it's all fine. Just still can't understand why formatting/deleting previously installed GRUB code partitions will suddenly make this procedure not possible.

> **oldfred said:**
> And then always install the boot loader from the  system you want in MBR, before deleting any other system.
And normally last installed system will be the one in the MBR, unless you specify otherwise.

I have heard that one can also choose not to install GRUB while installing the operating system, but I've never seen any options like that except while installing Ubuntu Server.

---

### Post by oldfred on 2016-04-04
I have never tried this, even though I have multiple Ubuntu's. I just manage which grub is where.

 sudo ubiquity -b
In that case you are able to install Ubuntu without the bootloader. 

The update-grub just redoes menu or grub.cfg.


 #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo parted -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

---

### Post by yancek on 2016-04-04
> So does that mean I could have also run "*sudo grub-update*" from Mint even after I had formatted/deleted the other partition entirely?

If you had been booting from the Grub from Ubuntu installed to the MBR, you could have booted into Mint, deleted the Ubuntu partition, run:  sudo grub-install /dev/sda then run sudo update-grub although there would not have been any point to updating grub as you only had one operating system.

> So worst case scenario here is that by having a separate /boot partition  it can make the system unbootable if the user chooses to update the  kernel? Or updating software messes with kernels too? I mean, by  "kernels" you refer to the Unix kernel, right? The system kernel.
  
Having a separte boot partition won't by itself make anything unbootable.  The problem with it is primarily for new users who create a small boot partition and when they do updates and add new kernels, the boot partition gets full and that is what results in an unbootable system.  Some Linux distributions remove all but the two most recent kernels, Ubuntu apparently does not.  Lots of posts here at the forums with this circumstance.  By kernel I mean the Linux kernel which in Ubuntu and most Linux systems is named "vmlinuz".

> So here is what it comes down to... For example, I was wondering which  to install first, Linux Mint or Ubuntu Server since the latter doesn't  have a GUI, it's much harder to modify GRUB settings

It doesn't matter really.  If you prefer the Mint bootloader because of the GUI thing install its Grub to the MBR.  Then when you install Ubuntu, when it asks you where to install Grub, select to install it to the Ubuntu system partition.  If you install Ubuntu first, you can select either then when you later install Mint, makes sure you install to the MBR which should be /dev/sda if you have only one drive.  Doing this is much simpler than trying to change after already installed systems.

 > But you're saying one can log in to Mint or whatever distro and run "*sudo grub-update*" and it will rewrite the MBR code back to Mint,

No, see the first paragraph above in this post.

> Just still can't understand why formatting/deleting previously installed  GRUB code partitions will suddenly make this procedure not possible.

Again, see the first paragraph above.  You have to be booted to the system which you want code from Grub in the MBR.  Your problems occurred because you had Grub code in the MBR pointing to the Ubuntu partition to find the Grub files.  Since you had formatted (basically deleting to a normal user) the partition, the files were not there.  Again, see paragraph one above on how it needed to be done.

> Just still can't understand why formatting/deleting previously installed  GRUB code partitions will suddenly make this procedure not possible.

I've seen that option with Grub Legacy but don't know if it's available with Grub2.  If you have for example, Mint installed and booting and you install another system, you might select to not install Grub with Ubuntu if that option exists.  Mint should detect the Ubuntu.  I haven't checked whether this option is available so I'm not really sure.  It is definitely possible to install a secondary system without a bootloader.  You would just need to create an entry pointing to the correct partition and the correct path to the vmlinuz and initrd files.

---

### Post by lakeshore2985 on 2016-04-04
@yancek: Alright I get it, I get it. I understand, thanks lol.

> **yancek said:**
> Having a separte boot partition won't by itself make anything unbootable. The problem with it is primarily for new users who create a small boot partition and when they do updates and add new kernels, the boot partition gets full and that is what results in an unbootable system. Some Linux distributions remove all but the two most recent kernels, Ubuntu apparently does not. Lots of posts here at the forums with this circumstance. By kernel I mean the Linux kernel which in Ubuntu and most Linux systems is named "vmlinuz".

OK. So far all I have seen are the disadvantages of having a separate /boot partition, but what about the advantages? Are there any? Well there must be something good about it, right?

> It doesn't matter really. If you prefer the Mint bootloader because of the GUI thing install its Grub to the MBR. Then when you install Ubuntu, when it asks you where to install Grub, select to install it to the Ubuntu system partition. If you install Ubuntu first, you can select either then when you later install Mint, makes sure you install to the MBR which should be /dev/sda if you have only one drive. Doing this is much simpler than trying to change after already installed systems.

Yes, but not all distros offer you the option to choose where to install GRUB on. In fact, from the distros I have installed so far (which are not that many) only Ubuntu Server asks anything related to the bootloader.

But anyway I think I got the hang of it now... whenever I install multiple Linux operating systems, just log into any of them and run the following commands:

[I]sudo grub-install /dev/sdx
sudo grub-update[/I]

Done!

---

### Post by yancek on 2016-04-04
With an LVM install, I believe you 'need' a separate boot partition.  As far as the advantage, I couldn't really say as I've never used a separate boot partition.

 > Yes, but not all distros offer you the option to choose where to install GRUB on

I've installed over one hundred different Linux distributions over the years and the first one I can recall that didn't give me the option as to where to install Grub is CentOS 7 which I installed last week.  If you are using the Install Alongside option, you probably don't see it.  That's basically and auto install which is easier, if it works.  If it doesn't, the disadvantage is that you will have absolutely no idea what happened and therefore will not know where to begin to try to solve the problem.  If you use a Manual option which is referred to as "Something Else" in Ubuntu and most derivative, you will always see at the bottom of the partition windows "Device for bootloader installation" and you can select a partition or the MBR.  I'm not sure what you see with EFI, as I haven't used it yet.

> But anyway I think I got the hang of it now... whenever I install  multiple Linux operating systems, just log into any of them and run the  following commands:


Well, not exactly.  Remember that if you boot into a systm and run those commands, the code from the MBR points to the boot files on that specific partition.  So in your example, if you had Mint installed as well as Ubuntu and you installed Grub to the MBR from Ubuntu and later deleted the Ubuntu partition, you would have an unbootable machine.  So if you planned on formatting or deleting a partition, make sure that FIRST, you boot another system and make sure it's boot code is in the MBR.   If you understand that , you should be good with it.  Remember that you can if you want, you can continue to use Mint and the Grub files from Mint to boot any other system you install later by simply installing the Grub files to the partition you are installing on.  Then simply boot Mint and run:  sudo update-grub.

---

### Post by lakeshore2985 on 2016-04-06
> **yancek said:**
> I've installed over one hundred different Linux distributions over the years and the first one I can recall that didn't give me the option as to where to install Grub is CentOS 7 which I installed last week.  If you are using the Install Alongside option, you probably don't see it.  That's basically and auto install which is easier, if it works.  If it doesn't, the disadvantage is that you will have absolutely no idea what happened and therefore will not know where to begin to try to solve the problem.  If you use a Manual option which is referred to as "Something Else" in Ubuntu and most derivative, you will always see at the bottom of the partition windows "Device for bootloader installation" and you can select a partition or the MBR.  I'm not sure what you see with EFI, as I haven't used it yet.

Damn right, Ubuntu does offer the option where to install GRUB... but I don't see where it gives you the option not to install GRUB.

Btw I just ran "*sudo grub-install /dev/sda*" from the Mint partition and it completed successfully. But it also messed with the Ubuntu Server partition, making it unbootable (error -110).

I might run another batch of tests again. Think I got this figured out this time around.

---

### Post by yancek on 2016-04-06
> Damn right, Ubuntu does offer the option where to install GRUB... but I  don't see where it gives you the option not to install GRUB.

True.  I wasn't sure so I test booted and started the installer for Ubuntu 14.04  as well as a couple of other systems using Grub2 and the options are the MBR of all disks attached and all partitions.  No options NOT to install.  This was available on some systems which used the older Grub Legacy.

> Btw I just ran "*sudo grub-install /dev/sda*" from the Mint  partition and it completed successfully. But it also messed with the  Ubuntu Server partition, making it unbootable (error -110).

Run:  sudo update-grub from Mint to detect any other systems immediately after the grub-install.  Have fun.

---

### Post by oldfred on 2016-04-06
See post #9 for instructions on not installing grub. 
I have never used it, as I normally have several drives and let it install somewhere else than my normal grub/drive for booting.

But UEFI has greatly confused that.

---

### Post by lakeshore2985 on 2016-04-07
> **yancek said:**
> Run:  sudo update-grub from Mint to detect any other systems immediately after the grub-install.  Have fun.

I have tried running "*sudo grub-update*" several times under different distros and it actually never updates the /boot partition in the MBR.

The only viable solution I have found is to select where to install GRUB while installing the operating system, which has to be in the partition where you want it to take control of (in my example, the Mint partition).

Perhaps "Boot-Repair" software might help solve this, but haven't tried yet.

Also found something interesting in case anybody feels like fixing this in a more "geeky" fashion (props to the original uploader):

[https://www.youtube.com/watch?v=ajs9rO5upZA](https://www.youtube.com/watch?v=ajs9rO5upZA)

---

### Post by yancek on 2016-04-07
> I have tried running "*sudo grub-update*" several times under different distros and it actually never updates the /boot partition in the MBR

The command update-grub only works on Ubuntu and it's derivatives so if you have tried it on other systems, it won't work.  I'm not sure what you mean by updating the /boot partition or MBR.  update-grub crates a new grub.cfg menu on the system you run it from. it doesn't change anything in the boot partition or MBR.

To install Grub to the MBR of a system you are booted and the boot code currently in the MBR is not point to the boot files on that partition, you run:  sudo grub-install /dev/sda
That is, if you want it on sda.  If you want it on  the MBR of another drive, change it to /dev/sdb or /dev/sdc, etc.

I'm not sure what you are trying to solve.

---

### Post by lakeshore2985 on 2016-04-08
Perhaps if Ubuntu would offer an option not to install GRUB in the first place it would make things easier.

But anyway problem solved!

Thank you all for the replies!

---

