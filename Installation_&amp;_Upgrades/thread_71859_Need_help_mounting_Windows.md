---
title: "Need help mounting Windows"
date: 2005-10-04
forum: Installation &amp; Upgrades
---

### Post by XtremeGamer99 on 2005-10-04
I used this command so that I can edit files from my Windows XP Pro OS from Ubuntu:

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

I can copy files and read them, however, I cannot write to that partition. It says it's read-only. I need to know how to change that.

Thanks.

---

### Post by jatos on 2005-10-04
which user are you logged in as - you can only write to windows partitions as root, which is one of many reason why despite a lot of "bad idea" comments I login as root.

---

### Post by tktreload on 2005-10-04
Hello

As far as i know it's very risky to mod files on an ntfs drive!!!
I recomend mounting ext drives in windows, and moving the other way.
or simply make a small fat partition that you can use as transit for files that need modifying
also the ntfs driver mount command has default write protect....

---

### Post by XtremeGamer99 on 2005-10-04
I have logged on as root. Still won't do it.

How would I edit partitions withough re-installing Windows and Ubuntu again? I really just need to move some backup files I store on Ubuntu so that I could re-install Windows back to Windows. Not realy edit.

---

### Post by Herman on 2005-10-04
If you want you can use the Ubuntu installer's partitioner to make a new FAT32 partition, see the link below. You'll get a few scary looking red screen backgrounds when you are finished and need to exit the partitioner. If you don't mind that, then you can do it this way; (see signature link, and scroll all the way down to 'part two').
I have done it this way a few times and it works. The installer will try to install in the new FAT partition though, but you can just delete the un-needed directories it starts to create later on. The link explains it all.

---

### Post by jatos on 2005-10-04
for some reasoned I assumed (without fully reading your post) that you where on fat32. On NTFS you need to compile the linux kernel yourself with NTFS read/write support, but warning NTFS is only expiremental.

---

### Post by SilentCacophony on 2005-10-04
[QUOTE=XtremeGamer99]I really just need to move some backup files I store on Ubuntu so that I could re-install Windows back to Windows. Not realy edit.[/QUOTE]


I'm not sure if I'm understanding you correctly, but if you already have Windows installed, and you're looking to copy files from ext2 or ext3 partitions to the Windows partition, you can do that from Windows with the [Explore2fs]("http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm") program.

---

### Post by Snocrash on 2005-10-04
Writing to NTFS does require a kernel re-compile with the propper flags turned on....but even then it is VERY limited and DANGEROUS!!!!! It can crash the NTFS partition so hard Windoze won't boot and will need to be reinstalled!!!

There is at least 1 third party product out there for safely mounting and writing to NTFS from Paragon, but it costs around $70.00. I have used it with now problems on my laptop.
Link      [http://www.ntfs-linux.com]("http://www.ntfs-linux.com")

-Sno

---

