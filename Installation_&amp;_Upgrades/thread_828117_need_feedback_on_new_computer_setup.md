---
title: "need feedback on new computer setup"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by whiterabbit7500 on 2008-06-13
I'm seriously considering redoing my computers entire OS/hard drive system. Right now, I'm running XP Pro on a 40gb internal, w/ 2 other internals i barely use, and a 500gb external for my data. I want to set it up as follows, comments/feedback/advice welcome!

40 GB drive- Recovery images of drives/Pagefile
160GB drive- XP Pro SP3
200GB drive- partion 1- BackTrack 3
             partion 2- Ubuntu
300GB external- My Docs/pics
500GB external- Movies/Music

my questions/concerns-

1- how difficult is it to setup a tri-boot system in this configuration? I know the 40gb is on an ide cable, and the 160 and 200 gb are on SATA.
2- would backtrack and ubuntu recognize my external drives and be able to access them?
3- Would it be difficult to configure and maintain the harddrives, and could i be able to use my normal Windows HD maintanence process (defrag, chkdsk, etc) on the linux drives?

your feedback/advice is more then welcome, thank you :-)

---

### Post by Herman on 2008-06-13
> 3- Would it be difficult to configure and maintain the harddrives, and could i be able to use my normal Windows HD maintanence process (defrag, chkdsk, etc) on the linux drives?You can safely use the Ubuntu installer's partitioner to partition your hard drive for Ubuntu and Backtrack. We also have 'Gnome Partition Editor' in Ubuntu.
You can't use any Windows filesystem maintenance programs for Linux file systems. We have our own file system utilities and they're very good.
> 2- would backtrack and ubuntu recognize my external drives and be able to access them? I know that Ubuntu will, I have never tried Backtrack so I can't say for sure, but I imagine so.
> 1- how difficult is it to setup a tri-boot system in this configuration? I know the 40gb is on an ide cable, and the 160 and 200 gb are on SATA.
It shouldn't be too difficult. You might need to play around with GRUB a little bit. The easiest way would probably be to install Windows first, then Backtrack and then Ubuntu last. 
Ubuntu will try to install GRUB to MBR in your first hard disk, but when we have IDE and SATA disks together, with some BIOSes it sometimes guesses wrong. If so ,the easy way to fix that is to change the hard disk boot priority in your BIOS to agree with GRUB.
If Backtrack is a Linux distro that uses LiLo for its boot loader, you might be able to install LiLo to the first sector (boot sector) of Backtrack's partition. If you can then it's easy to chainload Backtrack from GRUB in Ubuntu. Ubuntu might automatically add a direct booting option for booting Backtrack, but a chainloader boot might be better.
Ubuntu will set GRUB up to chainload your Windows automatically in most cases, only sometimes (rarely), it needs some minor editing.

Regards, Herman :)

---

### Post by whiterabbit7500 on 2008-06-13
thanks for your quik response. is GRUB provided w/ ubuntu? I'm a total n00b at Linux distros. Do you think it would give me a problem having backtrack and ubuntu on the same physical disk, but on diff partions? sorry for the n00b questions, but I'm trying to cover all my bases and make this as seemless as possible. also, is there a program similar to Norton ghost that will take a image of the partition for recovery purposes that works with Linux? I have ghost for windows, but I want to be able to do a system recovery in the event of a faliure from the 40gb hd

---

### Post by snowpine on 2008-06-13
> **whiterabbit7500 said:**
> thanks for your quik response. is GRUB provided w/ ubuntu? I'm a total n00b at Linux distros. Do you think it would give me a problem having backtrack and ubuntu on the same physical disk, but on diff partions? sorry for the n00b questions, but I'm trying to cover all my bases and make this as seemless as possible. also, is there a program similar to Norton ghost that will take a image of the partition for recovery purposes that works with Linux? I have ghost for windows, but I want to be able to do a system recovery in the event of a faliure from the 40gb hd

Hi WhiteRabbit, 1. GRUB is included with Ubuntu and it should be set up automatically as part of the install. 
2. Ubuntu is quite happy running from its own partition.
3. This thread has some tips on creating a complete backup: [http://ubuntuforums.org/showthread.php?t=825680](http://ubuntuforums.org/showthread.php?t=825680)

Good luck!

---

### Post by Herman on 2008-06-13
> thanks for your quik response. is GRUB provided w/ ubuntu? Yes, GRUB is provided for free with Ubuntu, it's the default boot loader for Ubuntu, but if you use the 'Alternate' CD, you can also choose LiLo instead if you prefer.  Most people use GRUB. 
I looked in Backtrack's Wiki and it looks from a quick visit as if it can boot with either GRUB or LiLo too.
> I'm a total n00b at Linux distros. Do you think it would give me a problem having backtrack and ubuntu on the same physical disk, but on diff partions?
It'll be no problem at all, they won't fight, you won't have any difficulties.
>  sorry for the n00b questions, but I'm trying to cover all my bases and make this as seemless as possible. also, is there a program similar to Norton ghost that will take a image of the partition for recovery purposes that works with Linux? I have ghost for windows, but I want to be able to do a system recovery in the event of a faliure from the 40gb hdYes, you can use a simple 'dd' command, but Partimage is an excellent program for making a backup of an entire partition or operating system. I have used that a number of times with great success. Here's a link about that in case you want to see what it looks like,  [Use PartImage]("http://www.psychocats.net/ubuntu/partimage").

---

### Post by whiterabbit7500 on 2008-06-13
ty so much guys. Im planning on doing all this as soon as my buddy gives me his "copy" of xp ;-) I'll keep you guys up to date. thanks again!

---

### Post by whiterabbit7500 on 2008-07-10
so, finally got around to doing this setup...and it works perfectly. Installed XP 1st, then BT3, then Ubuntu. Grub auto-loads Ubuntu on boot, with the choice to boot BT3 or XP as well. Was actually able to install Ubuntu and BT3 on their own HD's, since i found out I had an extra 160gb internal i had forgotten about :-p few questions though...

1. How come the Ubuntu HD is now showing up as hidden under windows, yet BT3's shows up fine?
2. Does linux have drivers pre-installed for Firewire 1394 support? I installed that 300gb external using firewire, and it couldn't read it after I installed linux. Had to go back to USB.
3. What PCI wireless card works nativly with Linux w/o having to use ndiswrapper?

---

