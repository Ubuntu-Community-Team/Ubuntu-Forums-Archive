---
title: "Installing Ubuntu on a Win XP System"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by ak825989 on 2007-10-05
Forgive me for starting a new thread on what appears to be a hoary old topic, but I've had a good look at existing posts, and I've been unable to find help on the specific issue I have.

I've tried to install Kubuntu Feisty Fawn from a Live CD on a laptop running Win XP, to replace an existing CentOS install. The laptop has only one hard drive, but is partitioned as required.

I'm an old hand at multi-boots - two other PCs dual boot Win XP and CentOS, one also has Win 98!

My normal procedure is to retain Win XP's 'boot.ini' as the primary bootloader, and use the 'bootpart' utility - [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm) - to create the boot.ini entry and bootsector file for the other OS, on the Win boot drive. If the other OS is a linux install, this launches GRUB on the linux boot partition.

In a CentOS install, one is specifically given the option of installing GRUB on the first hard disk/partition (giving it primary control), or on the linux boot partition (giving it secondary control, as I wish).

This does not seem to be an option with Kubuntu.

Or is it? What is the implication of installing GRUB to (hd0) - the only option offered via the 'advanced' dialogue at the final install screen, before selecting 'install' and committing changes.

I assumed this would install GRUB to the first partition of my disk; I thus edited the line to '(hd0,4)' (the linux boot partition).

However, GRUB doesn't appear to have been instlled at all, anywhere; thus using 'bootpart' has not enabled me to set up 'boot.ini' to boot to Kubuntu. However, getting back into the installation reusing the Live CD shows that the selected partitioning has been carried out, and files installed; everything else looks pretty normal.

So, two questions, really. Can I install GRUB to the Kubuntu boot partition, and if so, how, at installation stage? Or, can I install GRUB there now  from the Live CD, and if so, how?

With thanks in advance in anticipation of a simple answer to what is hopefully a simple problem!

---

### Post by Mr_JMM on 2007-10-05
If I'm reading your post correctly, you want to end up with a dual boot of XP and Kubuntu, just those two. You also want to use Grub as boot loader.

If that is the case, I'd just reformat the partition you want to install Kubuntu on then install Kubuntu and let it sort everything out. That's at least how I went about it and it worked fine.

Actually, i did have one problem once where nothing would load after I buggered a pre-partitioned install and had to use Windows recovery consule to 'fixboot' and fixmbr' then install a Linux Distro.

Don't forget to check md5sums.

---

### Post by confused57 on 2007-10-05
You can install grub to the root(or boot) partition, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by maybeway36 on 2007-10-05
I don't know anything about the Windows bootloader, sorry.
I can tell you this:
(hd0) - installs to the master boot record at the beginning of the hard disk
(hd0,0) - installs to the first partition
(hd0,1) - second partition, and so on...
(hd0,4) - first "logical" partition (ones inside an extended partition)
(fd0) - floppy disk. Funny how those never go away...

I would suggest using GRUB and having it have an option to boot WinXP. You can always get rid of GRUB and make your computer boot straight to Windows; this can be done with a Windows install CD or a DOS boot floppy/CD.

---

### Post by ak825989 on 2007-10-05
Problem solved! Though it was a case of trial and error.

Thanks for confirming by your post, maybeway36, that it was a valid option to edit the GRUB installation line, in the 'advanced' dialogue at the final installation settings screen, to specify the partition.

However, I had to go through three re-installations before I found the one that worked, finally using (hd0,6), for reasons that defeat me.

According to my understanding of GRUB, that means the 7th partition on the hard disk. Yet GRUB is actually installed on the 6th partition (5th if you discount the extended partition). There are two primary and four logical partitions on the disk (plus one extended).

Bootpart identifies that partition as 7, but that's because Bootpart creates two partition numbers for every logical partition, to identify its extended partition 'wrapper', as it were.

The Ubuntu installer (which apparently thinks my laptop has a SCSI hard disk) lists only 6 partitions, numbering them sda1,2,5,6,7,8. This may be a legacy of frequent re-partitioning and/or previous dual boot setups, the MBR retaining entries for now non-existent partitions. GRUB is installed on sda7.

Is it a coincidence that the installer, and GRUB, both (incorrectly) identify the same partition as 7?

If it is not a coincidence, then in summary, it appears to be the case that to install Ubuntu in addition to a Win XP installation, where you want to use the Win XP bootloader as the primary one, you have to note the installer's numbering of the disk/partition where the boot files are installed (a7, in my case), then edit the 'advanced' dialogue at the final settings confirmation screen, rendering this into GRUB-speak (hd0,6).

Then using Bootpart (using whatever part number it gives for the relevant partition), you can add an entry to the Win XP bootloader, from which you can launch GRUB to boot into Ubuntu, if that's what you want to do.

Obvious, really ](*,)

---

### Post by metramo on 2007-11-03
Hi,

All this seems a bit confusing.

Am I to interpret that you need grub anyway, even if you use bootpart, and that you installed grub in the
same (ext3) partition as ubuntu was installed ?

Or is it lilo that was installed to that partition ?

Br

---

### Post by Joshua R. on 2007-11-03
I am confused--I want to dual boot XP and ubuntu. I installed ubuntu first and then XP (with separate partitions and all[I think!]). Now I can only boot from xp. I went into the BIOS (toshiba) and cannot find anything there that will help. Do I need any of the above mentioned programs? Or is there a simpler way? I am new at all of this Linux stuff and just thought that it would be a good experiment.

---

### Post by Craigus on 2007-11-03
> I installed ubuntu first and then XP (with separate partitions and all[I think!]). Now I can only boot from xp

That is normal and expected behaviour. The way most people do it is to first install XP and then a linux / BSD. 

You can probably install a boot manager program that will enable you to use your existing installations. Have a look at:

[http://www.ranish.com/part/xosl.htm]("http://www.ranish.com/part/xosl.htm")

---

