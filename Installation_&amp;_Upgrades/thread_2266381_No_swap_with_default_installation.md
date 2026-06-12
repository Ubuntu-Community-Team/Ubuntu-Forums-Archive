---
title: "No swap with default installation?"
date: 2015-02-22
forum: Installation &amp; Upgrades
---

### Post by marklovescoffee on 2015-02-22
Hello guys,

So I just bought a new laptop, and of course the first thing I do is put Ubuntu on it. I use the standard installer with LVM and encrypted home directory, but otherwise I don't mess with any manual partitioning. It seems to work fine, but upon booting for the first time, I get an error that there's no swap. Still boots, so I verify with swapon command that there is no swap.

Looking at the partition manager, it seems I have 3 partitions:
dev/sda1 (fat32, /boot/efi), dev/sda2 (ext2, /boot), dev/sda3 (lvm2 pv)

This can't be the intended behavior. Any idea what went wrong? A few possible culprits:

1) LVM - although I doubt it
2) EFI - I've never installed to an EFI system before. I don't care about Windows, but I read Ubuntu works with EFI, so I left it on. Should I disable it?
3) Hybrid hard drive - I have a 1 TB hard drive with 8 GB "cache". Could this be causing problems for the installer?
4) Encrypted home directory - again, doesn't seem likely, but I'll list it here just in case

Right now I have nothing on the hard drive and I want a clean install, so if I can figure out how to make Ubuntu install with swap properly I'll do that. If not, I found commands to add swap, so perhaps I could try that. Any suggestions? Also, if I did find a bug in the installer, I'd like to diagnose it and file a bug report so other users aren't affected by this.

Thanks to all who can help.

---

### Post by sudodus on 2015-02-22
This method will eat the whole drive.

There should be swap, but I think it is crypswap inside the LVM partition. The root partition is also inside the LVM partition.

What does it look like when you run logged in with your user id?

There is a good instruction for testing the Lubuntu alternate iso file with encryption. I think you can use it (with modifications) also for other iso files, for example the Ubuntu desktop iso files. See this link

[http://iso.qa.ubuntu.com/qatracker/milestones/318/builds/73663/testcases/1439/results](http://iso.qa.ubuntu.com/qatracker/milestones/318/builds/73663/testcases/1439/results)

There is also this direct instruction set for Ubuntu, which I have not used,

[http://iso.qa.ubuntu.com/qatracker/milestones/318/builds/73658/testcases/1451/results](http://iso.qa.ubuntu.com/qatracker/milestones/318/builds/73658/testcases/1451/results)

I think it works well too.

---

### Post by oldfred on 2015-02-22
LVM is a logical set of partitions inside the physical partition, in your case sda3. 
The default will be / & swap but you cannot see that from outside the LVM.

With UEFI you have the efi partitin and the /boot partition outside the LVM, but rest of drive is LVM.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

---

### Post by marklovescoffee on 2015-02-22
sudodus,

Thanks for the reply. I understand this method will eat the whole drive. I don't need Windows, so I'll devote the whole drive to Ubuntu. Unless there is some way to utilize the 8 gb cache of the hybrid drive (seems not, but if there might be, let me know!) I'll just wipe the entire drive and install.

I've been doing a little more reading, and I think it is definitely something to do with the encryption. It really seems I have no swap though, or at least various commands (swapon, blkid) are telling me so. How can I test for the encrypted swap?

Also, would reinstalling without LVM solve the problem? I don't really need it, just chose it because there seemed to be no downside to choosing it.

Also, I don't really need the whole disk encrypted. I'd just very strongly prefer my home drive was. I didn't check the encryption option while setting up LVM and partitioning. I selected a much later option to encrypt only the home folder, at the same time I was choosing my log-in information. Full-disk encryption is overkill when I only really want to protect my personal files in the home directory.

---

### Post by marklovescoffee on 2015-02-22
oldfred,

Since you seem to be knowledgeable about LVM, perhaps I should ask you this. With my setup (1 TB hard drive with 8 gb cache) is it a good idea to be using LVM or not? I thought there was really no downside to it, but if the Ubuntu installer doesn't handle it well and the benefits really only seem to apply to having multiple drives, then is it even worth using? Thanks.

---

### Post by sudodus on 2015-02-22
I have tested LVM and whole disk encryption several times and it works according to my previous post. But if you don't need it, don't use it, because it makes things more complicated.

I don't know if the 8 gb cache of the hybrid drive is causing your problems. I have no own experience of such systems.

---

### Post by marklovescoffee on 2015-02-22
sudodus,

I guess I really have nothing to lose by trying to reinstall without LVM. If I still run into problems, I'll be back here to try and figure out what is causing the problem.

Thanks for the help

---

### Post by sudodus on 2015-02-22
Good luck, and welcome back, whatever result you get :-)

---

### Post by oldfred on 2015-02-22
I do not use LVM, just picked up some info since many seem to select it without realizing what it is. But it does seem to be required for full drive encryption, but can be just another advanced way to partition.

There also is an option to encrypt just /home with normal partitioned install. But with any encryption you must have very good backups.  If encryption gets corrupted you rarely can recover data from it even if you know pass phrase. 

I do not know about the hybrid drive and whether that does anything with Linux or not.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by marklovescoffee on 2015-02-22
Just reinstalled, default install with with no LVM but still with encrypted home directory. I'm getting an error with /dev/mapper/cryptswap1, but I can't really tell exactly what it is because my system is in Chinese and the characters are not displaying properly. But based on Google I think it's this error "The disk drive for /dev/mapper/cryptswap1 is not ready yet or not present".

Is this normal or an error?

I'm looking up how to solve this at the moment. Might something like [http://punygeek.blogspot.com/2012/10/ubuntu-1204-how-to-solve-disk-drive-for.html](http://punygeek.blogspot.com/2012/10/ubuntu-1204-how-to-solve-disk-drive-for.html) help?

---

### Post by marklovescoffee on 2015-02-22
oldfred,

Yeah, seems I don't really need LVM, so I won't use it. Ideally I'd like to encrypt the home partition, but it seems quite complicated to do at the moment. I am searching for ways to make it work on Google, but it's a bit over my head. I'm just blindly entering in command and I really don't understand what it does, so I think I will probably just reinstall (yet again lol) without the encryption, for the moment. I honestly just want to get the computer up and running and not have to play around with stuff like this. Perhaps when 15.04 comes out I'll try the encryption again and see if it has been improved by then.

So at this moment I'm no longer in need of help. Thanks for helping.

---

### Post by sudodus on 2015-02-22
Maybe you should try the ***standard Ubuntu desktop version***, for example 14.04.1 LTS or 14.04.2 LTS and select ***English*** language. Check if cryptswap works in that case! It will help finding what is causing the error.

---

