---
title: "Ubuntu installer doesn't detect windows 7"
date: 2014-04-02
forum: Installation &amp; Upgrades
---

### Post by peter94 on 2014-04-02
Hello.

I downloaded ubuntu recently and i am trying to make a dual boot but the installation can't seem to be able to detect that i have windows 7 so it asks me if i want to delete the entire disk. How do i solve this issue?

I have tried running fixparts on windows and then entering the w command.

I also tried using sudo sgdisk --zap /dev/sda with the live cd OS but then when i tried to install i was informed that i don't have enough space. Any ideas? Thanks in advance.

---

### Post by Mark Phelps on 2014-04-02
> I also tried using sudo sgdisk --zap /dev/sda with the live cd OS

So, let me get this straight -- the Linux installer did not see Win7, so you knowingly ran a command that destroyed any GPT and MBR data structures on the disk?

HOW, was this going to help you > trying to make a dual boot ??

---

### Post by peter94 on 2014-04-02
I just kept googling and trying a bunch of solutions that popped up in threads showcasing a similar problem. But apparently i probably did something stupid didn't i? :/
To be honest i just have no clue what i am supposed to do.

---

### Post by oldfred on 2014-04-02
Stop trying to randomly modify drive.

Post this from live installer terminal to see if zap removed all partitions.
sudo parted -l

You did make full backups of Windows before major modifications like a new install?
You did you Windows to shrink the NTFS partition to make space for Ubuntu. 
You checked if you had used all 4 primary partitions which most Windows 7 systems have used and need a bit of work to resolve.

We have posted the above instructions 1000's of times for dual booting Windows & Ubuntu and google would have found most of them.

If partitions are gone, do you have a printout of partition table or any documentation that shows exact sector locations on drive?
You may be able to recover partitions with testdisk, but lets see where you are at.

---

### Post by peter94 on 2014-04-03
I run the command as you said and i got this as a result :

"Error: /dev/sda: unrecognised disk label                                  

Error: Can't have a partition outside the disk"

What should i do next?

PS. Thanks for your time.

---

### Post by oldfred on 2014-04-03
All partition table info has been deleted.

See if testdisk can find old partitions. If you changed partitions, it will find multiple copies. You can only select one set of non-overlapping partitions. Best if you remember size and types of partitions.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)


 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by peter94 on 2014-04-03
EDITED:Never mind. give me a seconds.

---

### Post by oldfred on 2014-04-03
Testdisk has been in repository forever. Sometimes you do have to turn on universe, restricted or multiverse repostories for some packages. 
I often use synaptic to find packages. And it is in 12.04, as I show it installed and it is in universe.

I have never downloaded it and installed it, so not sure if .deb which is easy to install or a tarbell which may be more difficult to install.
 download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by peter94 on 2014-04-04
[IMG]http://i59.tinypic.com/i27j1l.png[/IMG]

Here's the result.

---

### Post by oldfred on 2014-04-04
Disk sr0 is your CD or DVD, it does not have any partitions.

You want sda or sdb or whatever the drive is.

---

### Post by xXIntelXx on 2014-04-04
Edit (my phone is stupid)

---

### Post by peter94 on 2014-04-04
The only option to select is my dvd. I don't have any other options.

---

### Post by oldfred on 2014-04-04
Does BIOS show drive?

I do not think the zap in sgdisk would have erased all the history but perhaps it totally housecleans everything? It looks like it totally erases gpt  info, and MBR partiiton table, but testdisk is looking for old partitions on drive.

---

### Post by peter94 on 2014-04-04
> **oldfred said:**
> Does BIOS show drive?

I do not think the zap in sgdisk would have erased all the history but perhaps it totally housecleans everything? It looks like it totally erases gpt  info, and MBR partiiton table, but testdisk is looking for old partitions on drive.

The bios does show the drive and i can still start up windows.

---

### Post by oldfred on 2014-04-04
THen I do not know why testdisk would not show it.
And if all partitions are deleted, Windows would not work either??

I do not really understand Windows partition tools but what does its partition tool show.

Or does gparted show partitions?

---

### Post by peter94 on 2014-04-04
[IMG]http://oi61.tinypic.com/nmg8ye.jpg[/IMG]

There you go.

---

### Post by oldfred on 2014-04-04
You are not showing any Linux partitions and just three NTFS partitions that look normal.
Did you install with wubi?

You should use Windows partition tools to shrink one of you NTFS partitions, reboot immediately so it can run chkdsk and make repairs to its new size.
Make sure you are not hibernated.

Then does Ubuntu installer see Windows?
If not you may have to use Something else or manual install, but do not run auto install unless it says it sees Windows.

 Install with screen shots, auto install option
[http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT](http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Install options, Do not use erase entire drive unless that is really what you want. That is entire hard drive not just Windows c: "drive".
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
Windows 8 & Ubuntu
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu)

---

### Post by peter94 on 2014-04-04
I cannot install because when i go to the second screen my only options appear to either be erase the whole drive or make a partition table manually. That's what i meant when i said that ubuntu doesn't detect windows. Also as for the commands that you asked me to run i just booted the ubuntu and selected the "try without installing" and then downloaded the tools and run then through the live cd demo.

---

### Post by oldfred on 2014-04-04
Does Windows need chkdsk, it may even boot, but still need chkdsk.
Or are you hibernating in Windows.
Linux cannot see NTFS partitions that have chkdsk flag or hibernation flag set.

Post this from live installer's terminal in try mode.

sudo parted -l
sudo fdisk -lu

---

### Post by peter94 on 2014-04-05
Apparently the cause was the sata ports on my motherboard which cause a partial malfunction as of how the system read the disks. It seems to be ok though(though i will have to reinstall everything and all). But made back ups anyways. After that everything will be fine. Thanks for all your help. :)

---

