---
title: "partitioning suggestions?"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by spezticle on 2010-06-03
I have a 500gb hdd with intent to run only Ubuntu.
/home currently consumes about 400GB of this hdd and i'm using about 80gb of this space.
nobody else uses my computer so there's always only 1 user account for desktop login.

i've been thinking about different methods for partitioning and i'm not sure the best way to implement the optimal partition table.

I want to keep security priority because most of the content of /home is made available to /var/www for apache purposes and about 5gb is private data that isn't intended to share so a /home/user/Private (encrypted) would be it's own partition. while /var/www would be it's own partition as well, it would be large for the bulk of my 80GB of files.

i've never tried using a partition table in this manor before and i'm not sure how it will work out. any insight or suggestions would be much appreciated :)

---

### Post by srs5694 on 2010-06-03
First, on a Linux-only installation, you might consider using the [GUID Partition Table (GPT)](http://en.wikipedia.org/wiki/GUID_Partition_Table) partitioning system rather than the more common [Master Boot Record](http://en.wikipedia.org/wiki/Master_boot_record) system. GPT has several minor advantages, including the elimination of the primary/extended/logical distinction that causes so many headaches, backups of all important partition definitions, checksums of partition definitions to help spot problems, and partition names (independent of filesystem names). GPT also supports disks over 2 TiB in size, but that's not really an advantage for you at the moment. To use GPT, you'd either create a new partition table using GParted or parted; or you can convert an existing MBR disk to GPT without data loss using GPT fdisk (gdisk). You'll need to re-install your boot loader.

Second, what sort of data are you sharing between your home directory and your Web server? In most cases, my recommendation would be to put that data in /var/www rather than in /home. If necessary or convenient, you could put a symbolic link in /home/user to /var/www for easier access. Depending on permissions, chroot status of your Web server, etc., this is likely to be a cleaner, and perhaps a safer, configuration than storing the files in /home and putting symbolic links to the files in /var/www. You can split off /var or /var/www into its own partition, which can simplify some types of backups, enable you to use the best filesystem for your needs in /var or /var/www, and perhaps even mount /var or /var/www read-only by default (if you don't change those files often).

Third, if you're concerned about the security of your private data on a system that also runs a Web server, perhaps it would be better to use two computers for these two functions. If two physical computers aren't practical, you could use virtualization to help. I'd think running the Web server on a virtual machine would be the safer approach, but then you'd have issues about how to access the files served by the Web server -- do you keep them within the virtual machine (on a separate partition mounted by the VM, say) or store them on the physical machine (shared to the VM via NFS or Samba, for instance)?

---

