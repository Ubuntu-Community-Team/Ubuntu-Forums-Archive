---
title: "Uninstalling Ubuntu"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by Auszug on 2007-05-25
I've had a nice stint with Ubuntu, but i sacrificed my d: drive to it, and i want it back.  i don't use ubuntu as much as i thought i would, so i want to get it off my computer.  i may re-install it in the fall, but im not sure.  anyway, i cant find anything anywhere that tells how to remove Ubuntu.

---

### Post by BobbyBionic on 2007-05-25
Hi

It's the same brute way  to uninstall any os : delete his partition !

---

### Post by jonallport on 2007-05-25
If you just remove the partition from Windows' disk manager that leaves Grub in command of the MBR.

So, either:
1) Before dumping Ubuntu (sob, wipe away tears, blub) edit the grub config to boot the Windows partition and remove the Ubuntu entries, i.e. on boot grub->ntldr->Windows
2) Re-write the MBR to load ntldr, removing Grub

Option 2 requires booting into recovery mode from Windows original media and runnign 'fixboot /mbr'

Having said this, my recomendation would be - remove Windows, keep Ubuntu! ;^)

---

### Post by Auszugg on 2007-05-25
thanks for the info, guys, cant do it now but im gonna try it later.

> **jonallport said:**
> 

Having said this, my recomendation would be - remove Windows, keep Ubuntu! ;^)

haha, i wish i could, i wish i could...  unfortunately i need Windows for school.  like i said, i may install it again, but right now, i need my d: drive, rotfl.  thanks again

---

### Post by ddrplayer512 on 2007-05-25
I had to do this on a laptop, it was not a good idea to keep Ubuntu at the laptop anymore since the new owner wanted only windows.

I'm assuming you are using Windows XP.

First, get a Windows XP Installation Disc. Follow the instructions to boot into the recovery console.
Next, log on to your Windows installation. Once you're done type the following command:
```
fixmbr
```
Say yes. Reboot. Did you boot into windows okay? Great!
Then download the GParted live cd at [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php).
Boot into that to delete that partition that Ubuntu is stored on.
Then, create a new FAT32 partition of equally the same size as the Ubuntu partition.
Accept Changes.
Then boot into Windows. You will see your D: drive there!

I hope you will give Ubuntu another chance someday, I know I will on my desktop!:p

Have fun computing!
:popcorn:

---

### Post by flip_flop on 2007-05-26
I am also quite new to ubuntu but while installing i noticed an instruction that would return the mbr back to its original state.  As i have third party software running beneath windows which controls my back ups and factory standard back ups i do not want to use the standard methods of using windows commands can any one help.

---

### Post by delilahjed44 on 2007-05-26
> **Auszug said:**
> I've had a nice stint with Ubuntu, but i sacrificed my d: drive to it, and i want it back.  i don't use ubuntu as much as i thought i would, so i want to get it off my computer.  i may re-install it in the fall, but im not sure.  anyway, i cant find anything anywhere that tells how to remove Ubuntu.


Hey, I had troubel getting back into Windows XP because I did a full in-stall with Ubuntu.  Now you will need your re-installations disk.  What I had to do, I basically chose to re-install Ubuntu, then when it came to partitioning the drive, I chose to do a clean erase, then it erased the total hard-drive including Grub, which is what I could not get past.  When it began to re-install Ubuntu, I shut down the pc, then and only then was I able to boot back up into F12 and F2 as to re-install my Windows.  

Otherwise the grub would not let me boot back into Windows with my CD on XP to re-install it.

I am working on a possible dual boot, as I prefer Ubuntu BIG-TIME, but it will not apply to any of my lanquage programs with or without wine, thus my return to windows was crucial.  Good luck, remember this method above will wipe out all including windows/ubuntu on drive.

Sherri

---

### Post by mejohnsn on 2007-05-27
I couldn't find instructions on uninstall either. This is a curious omission in the documentation, especially since uninstall followed by reinstall is often recommended instead of upgrading (if, for example, you need to go straight from Breezy Badger to Feisty Fawn).

So yes, I am hoping that some developer reading this thread will add this to the documentation to-do list;)

In the meantime, I am facing a very similar problem. I installed the Breezy Badger version included on an Install CD shipped with the Apress book on Beginning Ubuntu, only to find that 1) it is an old release and (worse) 2) it does not recognize my primary network hardware, which is a wireless card.

Curiously enough, on the very same laptop, I can easily use the wireless card with a LiveCD of Dapper Drake Ubuntu. So I am assuming that the problem is not the difference between Install and LiveCD, but between Badger and Dapper Drake, i.e., Breezy Badger is too old to correctly detect my hardware.

But just how the Install program decides how to handle partitions on the disk is a bit of a mystery to me, so it is unclear to me whether simply editing Grub config and removing the Ubuntu partitions will do the right thing.

BTW: several people has answered in this thread saying "delete its partition" (or words to that effect). But surely there are multiple partitions: ext, swap and boot? Don't they all have to be removed? I would think so, especially for the scenario posed by the OP, who wants his D: drive back: presumably all Linux partitions are on that drive (except for perhaps boot, due to BIOS  limitations).

But for my scenario, that would not be necessary, if the Install program is clever enough to recognize an Ubuntu partition from a previous install and reuse it. Is it that clever? Or am I better off deleting them all running GParted (leaving it as free space for the Install program to see)?

---

### Post by rillip on 2007-05-27
Yes, you will need to delete all the partitions you do not want that Ubuntu is using.

Not to be down on any posters, but find me a guide to uninstalling Windows.

I think it goes like this:

boot from some bootable media that will give you a command prompt

type: format c:

Removing pretty much any OS is the same, you just destory it from outside of the OS from some bootable media and install the new one.  Windows is just a triffle easier to destroy because it only uses one partition.

Reinstalling whatever OS you want will even take care of the MBR, just like Ubuntu did, so grub isn't even an option.  A Windows install will nuke the MBR back to Window's way too.

Edit: come to think of it, the Windows installer has a partition manager that will let you nuke the partitions and make a new one too.  So just install Windows, if that's what you're going to.  If you find an OS that can't do something like this... tell them they suck.

---

### Post by Auszugg on 2007-05-29
ok, im a bit confused as to what i should do.  ive heard several different ways, but im not sure which one i should do.  im thinking about deleting the partition through grub, but i dont know how to find the grub config.  again, im dual booting windows XP and ubuntu, and i partitioned my d: drive to ubuntu.  i now want to remove ubuntu and get my d: drive back for windows

---

### Post by rillip on 2007-05-31
Grub is just the loader.  Removing it from there will mean it won't boot, but won't give you any space.

Fire up a liveCD, like gparted or the Ubuntu install disk, or Windows install.  Delete the partitions you had Ubuntu installed on.  Done, Ubuntu is removed.

---

