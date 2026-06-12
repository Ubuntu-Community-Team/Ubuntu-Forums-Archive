---
title: "putting GRUB in a file in 8.04"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by ticklj on 2008-05-02
how do I get 8.04 to put GRUB where I want it not in the 
MBR on a disk where it did not install the system . I want
the GRUB to go to the  root file where it will be loaded by another
boot loader. More exactly where is the HOWTO if there is one.
Thanks

---

### Post by hal8000 on 2008-05-02
You can install grub on a floppy, but if you want GRUB to boot your system it has to be either in the MBR, or a bootable floppy or bootable CDROM.

You dont state whether you are dual booting or why you want to install grub to a different location. I guess you are wanting to multi boot so this link may help:


Have a look at this link:
[http://tldp.org/HOWTO/Multiboot-with-GRUB.html](http://tldp.org/HOWTO/Multiboot-with-GRUB.html)

---

### Post by ticklj on 2008-05-03
As Paul Newman said in "Cool Hand Luke" what we have here is a failure to communicate and mostly my fault. In other distributions that I have tried I get asked at some point where I want Grub installed, either in the MBR or in some linux file likely /boot if any or /root. In some distributions one got asked this with the simple installations in some others one had to select "advanced" or some other option.

In my case I was installing to a SCSI but there was an IDE lying
around and Ubuntu put it on the MBR of the IDE not really the best choice. I realize I could disconnect the IDE but GRUB would no doubt end up in the MBR of the SCSI. I want UBUNTU to ask me where to put it. Can this be done? Or must I resort to some post-installing fooling around to get the deed done.

I have a 4-boot on various disks and some boot manager thingo
Thanks

---

### Post by ianhaycox on 2008-05-03
During the installation dialogues there is an Advanced... option at the end of the process where you can choose where to install Grub, or ignore it completely.

---

### Post by dstew on 2008-05-03
What you want is to install the grub boot loader to a *partition*, rather than the MBR of a disk, and use another bootloader to chainload grub. To install grub to a partition, you can use an Ubuntu Live CD. If your Ubuntu partition is /dev/sda3, for example, the grub root will be (hd0,2), and you want to set it up in the same partition. So, from a live CD boot, on a command line, enter```
sudo grub
```That will get you the grub> prompt. At the grub prompt, enter the commands to install grub to the Ubuntu partition:```
root (hd0,2)
setup (hd0,2)
quit
```Now you can chainload grub using another boot loader. Again, you have to change the commands if your Ubuntu partition is something other than /dev/sda3.

---

### Post by ticklj on 2008-05-04
I infer you meant (sd0,2). After grappling with trying to login
to Live CD (you should read the postings on this subject) I found
that choosing a safe mode session and the user id ubuntu got me in.
I could not mount the linux file system though I could mount 
various other file systems on my disks. The UBUNTU FS is JFS and
I get lots of complaints from the mount command. Is this a known
failure. Also the mount command says It did not like the option
'-t' but I really don't know whether it is complaining about
the -t or the jfs which follows. Anyway I start from the beginning
with a different FS 
Thanks

---

### Post by ticklj on 2008-05-04
It is not for the man in the street.
1: For as long as I can remember SDxx stood for a scsi disk and
HDxx was an ide. With my hardware SD was the scsi BUT it was also
the SATA. Is that the intension or is there an error in the installer? Does the world know about this?
2: When the installer tried to write grub to the partition with
the root, failure was reported.
3: I removed the SATA and did another install with the same failure.
4: After I found myself in a running ubuntu but the only login I could get to work was safe mode and ubuntu uid.
5: this time I was able to run the grub setup and was informed that it was successful. That's a bit of progress.
6: Rebooting, my boot loader came up and I selected linux and LO
grub came up.Cant say that this wasn't good BUT I guess that
the config of grub was not correct or empty. When I typed boot
was told kernel must be loaded.
7: anyway I am considering removing all the hard disks and
attaching a spare ide on channel 1 and see if this goes through.
Is this a good idea. I have a dual processor if that's
causing trouble.
Not for the man in the street

---

### Post by ticklj on 2008-05-05
To put an end to this thread-I began to suspect JFS. When I changed
the FS-type to EXT2 the install went swimmingly. except there is
always one, I can only login to a safe session but I likely can figure this out. Where does one report the JFS failure?

---

### Post by luvr on 2008-05-05
> **ticklj said:**
> how do I get 8.04 to put GRUB where I want it not in the MBR on a disk where it did not install the system.
As **ianhaycox** has already mentioned, there's an *"Advanced"* option on the last screen of install prompts.
That will let you specify [where you want to install the GRUB boot loader.]("http://ubuntuforums.org/showpost.php?p=2746942&postcount=5")

---

