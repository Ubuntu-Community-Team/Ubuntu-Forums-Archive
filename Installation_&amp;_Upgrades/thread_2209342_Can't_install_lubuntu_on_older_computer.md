---
title: "Can't install lubuntu on older computer"
date: 2014-03-05
forum: Installation &amp; Upgrades
---

### Post by bjngchn on 2014-03-05
There is a 6 year old computer which had windows, and then replaced with kubuntu and then replaced with encrypted kubuntu which was screwed during upgrade. I tried all kubuntu's with alt-cd's and all failed for different reason, or no reason (errors saying things like : this step failed). ............So I decide to install lubuntu instead. ...........Here is the ERROR with lubuntu 13.10: ... An unsafe swap space has been detected. .... This is a fatal error since sensitive data could be written out to disk unencrypted. This would allow someone with access to the disk to recover parts of the encryption key or passphrase........... Please disable the swap space and then run setup of encrypted volumes again. This program will now abort.........................................................................................................................Now, I don't understand the error. Aren't we erasing the whole disk already. Who cares what swap space already exist on laptop. ....Also I don't understand the solution. What is swapoff. How do I configure encrypted swap space. All this doesn't make sense. Encrypting the disk is CD's responsibility, not mine. .......

---

### Post by sudodus on 2014-03-05
I think Lubuntu is 'kind enough' to warn you about that standard swap space.

The simple solution is to remove all existing partitions including swap partitions. It probably works.

-o-

Otherwise I suggest that you wipe the first megabyte of the drive (removing traces of the previous partition table and data belonging to it).

You can use ***mkusb*** to make it safe (avoiding overwriting some drive, that you did not want to overwrite). See this link

[URL="http://ubuntuforums.org/showthread.php?t=1958073"]Ubuntu Forums tutorial "Howto make USB boot drives"
[/URL]
But if there is only the target drive and the CD, and you want to use the whole drive, you cannot overwrite any data by mistake.
[I]
- Are there any data, that you want to preserve on any writable drive connected?[/I]
- If the answer is no, you should be able to do it like this:

A. Boot from a Lubuntu 13.10 desktop CD

1. Select Try Lubuntu

2. Open a terminal window and run this command

```
sudo dd if=/dev/zero of=/dev/sdx bs=1024 count=1024
```

where x is the drive letter, probably a, so of=/dev/sda, if the only internal drive.

3. Open ***gparted*** (it comes with the desktop iso file)

- select Device - Create new partition table (This is necessary before you can start creating partitions)

- create partitions for the root file system and swap

I think it is easier to create partitions with gparted, but you can also do it with the installer.

B. Perform the installation with the desktop installer or alternate installer, whichever you prefer.

---

### Post by sudodus on 2014-03-05
See this link for details howto install Lubuntu encrypted

[http://iso.qa.ubuntu.com/qatracker/testcases/1439/info](http://iso.qa.ubuntu.com/qatracker/testcases/1439/info)

---

### Post by bjngchn on 2014-03-06
Installed lubuntu 12.04 successfully, but was never asked encryption pw, so this one will be erased.  Which versions of lubuntu are encrypted (full disk)? Testing takes 1 hour, so it is better to ask.

---

### Post by bjngchn on 2014-03-06
A general question comes to mind: If there is a previous installation, should we manually delete partitions associated to it, before trying to install new *ubuntu? Also, if we buy a new computer with windows in it, is it better to delete all existing partitions first? .. I was thinking until now, if some partitions need to be deleted, installation would take care of it. Why is deleting partitions  such a big deal.

---

### Post by bjngchn on 2014-03-06
I don't understand this sentence from sudous' instructions:  - create partitions for the root file system and swap ----------Will I do this? I have no idea how to create partition for root and swap. Even if I can do it, I don't know what to do while installing. All these partitions should be erased and created by installation. How can I know how to do such things. If I was a linux expert I wouldn't have to visit this forum.

---

### Post by mastablasta on 2014-03-06
> **bjngchn said:**
> A general question comes to mind: If there is a previous installation, should we manually delete partitions associated to it, before trying to install new *ubuntu?


no need as this is usually done by installer if you tell it to use the whole disk. but if you want to you can delete them.
> 
Also, if we buy a new computer with windows in it, is it better to delete all existing partitions first? 


Again this is done by installer if you tell it to sue the whole disk. and agin you can delete the disk space and existing parittions manually if you wish to do it. READ MORE IN NEXT ANSWER BELOW

> 
Why is deleting partitions such a big deal.
it's not, but when you delete partition table/parittion you also delete any data that was there (well actually when you delete parittion table you asign it as free disk space to be overwritten). so if data doens't have to be kept...

> **bjngchn said:**
>  - create partitions for the root file system and swap ----------Will I do this? I have no idea how to create partition for root and swap. .

in gparted. i think you click on empty disk space and then create partition. or during install procedure if you choose something else.

> 
All these partitions should be erased and created by installation. How can I know how to do such things. .

they are erased and new ones are created if you choose to use entire drive on install. at the same time any data on disk is lost with this procedure.

+iread more about full disk encrpytion here: [https://help.ubuntu.com/community/FullDiskEncryptionHowto](https://help.ubuntu.com/community/FullDiskEncryptionHowto)
and here: [https://help.ubuntu.com/community/EncryptedFilesystems](https://help.ubuntu.com/community/EncryptedFilesystems)

---

### Post by bjngchn on 2014-03-06
I get errors everytime. Since there seemed to be  errors about partitions I deleted all partitions. Then there was unsafe swap space error, and I did swapoff -a. And then "ubi-partman failed with 141 " error. Then I applied the command above: sudo dd if=/dev/zero of=/dev/sdx bs=1024 count=1024  . This time previous errors didn't appear. There is now just an error without expalantion: "An error occured while configuring encrypted volumes. The configuration has been aborted." There seems to be no way to escape.

---

### Post by sudodus on 2014-03-06
Which version are you trying to install? 12.04 and 13.04 have passed end of life. If you want Lubuntu, 13.10 is the only alternative today, the other Ubuntu flavours have also version 12.04 LTS with long time support.

And what kind of problems are there? Maybe if you let us know about your hardware (computer), we might be able to help.

---

### Post by bjngchn on 2014-03-06
I tried these again, maybe in a different order this time, and they seem to work now. Thanks to all, especially to sudous.

---

### Post by sudodus on 2014-03-06
You are welcome :-)

And if things settle down, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by stone circle on 2014-07-05
Same happens for me.  Trying to install encrypted Lubuntu 14.04 (standard, not alternate) on VMWare Workstation: "An unsafe swap space has been detected".  Tried to follow Sudodus' instructions without success.  I didn't know which type of partition table nor partitions to create, so just went with the default msdos and two ext4 partitions (one each for swap and file system).  If anyone has fixed this could advise the type of partition table and partitions to create, or any other pointers beyond Sudodus' instructions, it would be greatly appreciated.

Many thanks

---

### Post by sudodus on 2014-07-05
> **stone circle said:**
> Same happens for me.  Trying to install encrypted Lubuntu 14.04 (standard, not alternate) on VMWare Workstation: "An unsafe swap space has been detected".  Tried to follow Sudodus' instructions without success.  I didn't know which type of partition table nor partitions to create, so just went with the default msdos and two ext4 partitions (one each for swap and file system).  If anyone has fixed this could advise the type of partition table and partitions to create, or any other pointers beyond Sudodus' instructions, it would be greatly appreciated.

Many thanks

Are you trying encrypted home or full disk encryption?

The swap partition should be created as such, **linux swap**, and it should have no file system (not ext4). If you use encrypted home, the swap partition will be transformed into a special ***crypt-swap*** partition in the set up process. If you create the swap partition after you created encrypted home, it is more difficult, probably possible, but I have not done it, and don't know how to do it.

This is only guessing, but VMWare might not understand how to recognize a crypt-swap partition.

---

### Post by stone circle on 2014-07-05
Thanks Sudodus, it's full disk encryption.  I'll give linux-swap a try.  Do you know what the root partition and partition table types should be?

---

### Post by stone circle on 2014-07-05
.

---

### Post by sudodus on 2014-07-05
Full disk encryption means that there will be no dual booting or other partitions on that drive (in this case with a virtual machine, it means the virtual drive in the virtual machine). The method to install it is described in the following link. It is intended for iso testing of new versions, but works also for end users to do the installation.

[http://iso.qa.ubuntu.com/qatracker/testcases/1439/info](http://iso.qa.ubuntu.com/qatracker/testcases/1439/info)

I suggest to use the old MSDOS partition type and an ext4 file system for the root partition, but you can also let Lubuntu do the partitioning automatically.

---

### Post by sudodus on 2014-07-05
> **stone circle said:**
> FYI, Lubuntu Alternate image installs fine, no "unsafe swap" error.  I'm just concerned the lightweight version of the already lightweight version of Ubuntu might be more work than it's worth.

The alternate installer creates the same Lubuntu as the desktop installer. It is only the installer that is different, text based and less greedy for RAM.

---

### Post by stone circle on 2014-07-05
Useful to know, but unfortunately the Alternate installer eventually errored too.  However I found another threat that fixed\worked around the Standard installer "unsafe swap" error.  If you quit out of the installer, launch a command window then type 'sudo swapoff -a', then relaunch the installer using the desktop icon, the full-disk encrypted install proceeds fine.  Hopefully the swapoff command doesn't negatively impact security or performance.

---

### Post by sudodus on 2014-07-05
I see. I think the installer grabs the swap partition, and prevent making it into crypt-swap. I think you found a good solution, running the installer without swap should be OK. Maybe you would not get this problem, if you let the installer do all the partitioning (at least I have not seen it during iso-testing earlier versions).

---

### Post by stone circle on 2014-07-06
I spoke too soon with the "swapoff -a" suggestion too, errored\froze can't remember which.  The only way I could install Lubuntu 14.04 with disk encryption was using the Alternate image on VMWare Workstation 10, nothing worked on VMWare ESxi 5.5, and the standard image didn't work on VMWare Workstation 10.

---

### Post by sudodus on 2014-07-07
If you have the time, please help testing these things for the future releases :-)

[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

You need an account at [Launchpad]("https://launchpad.net/") in order to report bugs, and maybe you can also join the Lubuntu mail community <Lubuntu-users@lists.ubuntu.com>

See also this link

[https://wiki.ubuntu.com/Lubuntu/GettingInvolved](https://wiki.ubuntu.com/Lubuntu/GettingInvolved)

---

