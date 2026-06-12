---
title: "change /home"
date: 2010-09-19
forum: Installation &amp; Upgrades
---

### Post by Bananasdoom on 2010-09-19
I am about to do a clean install of Ubuntu 10.04 and I want to have my /home on a separate ntfs partition so that it can be accessed by windows 7. I know that i can move it after the install but i wold rather not go through all the problems of moving it.

---

### Post by Lateralis on 2010-09-19
You can have a separate partition used for /home.  In fact, you can have any arbitrary number partitions which you use for any directory.  You can have separate partitons for /, /boot, /etc, /usr so on and so forth.  During the installation of Ubuntu you will be asked to partition up your hard drive to make space for Ubuntu.  During that step, you make however many partitions you like and under the "mount" option select where that partition is to be mounted.  In this case, make a new partition and set it to mount at /home. 

Question though: Do you really want to put /home on an ntfs partition?  There will be a lot of files in your home directory that are specifically for Linux.  Any files or directories you want to have shared between Ubuntu and Vista can be mounted or symlinked to your home directory from a separate ntfs partition.  Bear in mind that ntfs support in Linux is not 100% fool proof.

---

### Post by Bananasdoom on 2010-09-19
how can i symlink files from the ext4 part to ntfs and have it accessible to windows??

---

### Post by Lateralis on 2010-09-19
You can make links using the **ln** command.  From the **ln** man page (*man ln* in the terminal)

```

SYNOPSIS
       ln [OPTION]... [-T] TARGET LINK_NAME   (1st form)
       ln [OPTION]... TARGET                  (2nd form)
       ln [OPTION]... TARGET... DIRECTORY     (3rd form)
       ln [OPTION]... -t DIRECTORY TARGET...  (4th form)

```

As an example, supposing you have a storage partition mounted to /media/storage.  The file system of /storage can be whatever you like including ntfs.  You can make a sysmbolic link to a directory in /media/storage - say /media/storage/an/example - like this:

```

ln -sv /media/storage/an/example/ ~/link

```

You will then have a symbolic link called 'link' in your home directory which will point to the /media/storage/an/example directory.  The -v switch here is 'verbose' so it will tell you what is linked to what.  The same command can be used to link individuals files, but that is likely to be time consuming and a bit kludgy!  **ln** will know whether you are linking to a directory or to a file when the command is invoked.  

You can then change directory to /media/storage/an/example by typing

```

cd ~/link

```

or navigating to it using nautilus.  

Of course if the device isn't mounted then you will have a broken link.  Isn't much of an issue (I don't think) but alternatively, you can bind the contents of a directory within a partition.  To do this manually you can:

```

mkdir ~/example_dir
sudo mount -B /media/storage/an/example ~/example_dir

```

This means that the contents of /an/exampe in /media/storage is available in two locations at the same time: ~/example_dir and /media/storage/an/example.  

You can also add a bind to your /etc/fstab.

```

/media/storage/an/example/   /home/<your username>/<target directory>   none   bind    0     0

```

Note that the partition which contains /an/examples has to be mounted first in fstab for that entry to be valid.  

Also note that spaces and special characters in fstab have to be escaped properly and codes used; quotes don't work in fstab.  So for a space you'd need \040.  Thus, try and avoid spaces and special characters as often as practicable.  

You also do not need to specify any options such as file system type for a bind in fstab, hence "none".  

Hope this helps.

---

### Post by srs5694 on 2010-09-19
> **Lateralis said:**
> You can have a separate partition used for /home.  In fact, you can have any arbitrary number partitions which you use for any directory.  You can have separate partitons for /, /boot, /etc, /usr so on and so forth.

Actually, /etc is one of a handful of directories that *can not* be put on separate partitions. (Others are /bin, /sbin, and /lib or its bit-specific variants, such as /lib64 or /lib32. /dev is also in this group, except insofar as udev creates a virtual /dev filesystem.) The reason is that these directories contain files that must be accessible by the system before other partitions are mounted. For instance, /etc contains the /etc/fstab file that specifies where other partitions are to be mounted, and /bin contains the mount program that does the mounting.

In principle, you could put just about everything else in its own partition. IMHO, new Linux users are well-served by creating three partitions for Linux: a 10-30GB partition for root (/), a partition of 1-2 times the RAM size for swap space, and the rest for /home. Advanced administrators often put other filesystems on separate partitions, including /usr, /usr/local, /opt, /var, /tmp, and sometimes others. I wrote [this article](http://www.ibm.com/developerworks/aix/library/au-unixfilesys/index.html) a couple of years ago describing the reasons for doing this sort of thing, in case you're interested.

> Question though: Do you really want to put /home on an ntfs partition?

In fact, using NTFS for /home won't work -- or at best, it won't work well. Linux relies on certain Unix-style filesystem features for ownership and permissions in key user home directory files, and NTFS doesn't support these features. Thus, at best you'll see certain Linux programs malfunction if you put /home on NTFS. (I vaguely recall fiddling around with this a while back just to see what would happen. I don't recall the details, but the system wasn't very usable.)

Creating a separate shared-data NTFS partition and then creating symbolic links or binding it, as Lateralis suggests, is the usual way to share data between Linux and Windows. (Giving Linux direct access to the Windows boot partition is easy and convenient, but it poses risks, since Linux can easily trash Windows files that would not be as easily deleted in Windows -- this is the flip side of the permissions issue that makes NTFS an unsuitable choice for use as a Linux /home partition.)

---

### Post by Lateralis on 2010-09-19
> **srs5694 said:**
> Actually, /etc is one of a handful of directories that *can not* be put on separate partitions. (Others are /bin, /sbin, and /lib or its bit-specific variants, such as /lib64 or /lib32. /dev is also in this group, except insofar as udev creates a virtual /dev filesystem.) The reason is that these directories contain files that must be accessible by the system before other partitions are mounted. For instance, /etc contains the /etc/fstab file that specifies where other partitions are to be mounted, and /bin contains the mount program that does the mounting.


Yes, you are quite correct.  My bad.  :)  I knew about the other directories for the reason you give, but for some reason my brain allowed me to say /etc.  Quite worrying really. :P  

Thank you for the correction. 

> **srs5694 said:**
> 

Linux relies on certain Unix-style filesystem features for ownership and permissions in key user home directory files, and NTFS doesn't support these features. Thus, at best you'll see certain Linux programs malfunction if you put /home on NTFS. (I vaguely recall fiddling around with this a while back just to see what would happen. I don't recall the details, but the system wasn't very usable.)


Indeed.  I should perhaps have made this clear in my original post.  Thanks again for clearing that up properly. :)

---

