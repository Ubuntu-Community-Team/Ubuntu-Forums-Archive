---
title: "Some general formatting information needed"
date: 2005-08-06
forum: Installation &amp; Upgrades
---

### Post by Hig on 2005-08-06
I'm currently running a downloads server on an old PC under XP. I have the following: A 20GB OS drive with apps etc and 2 250GB drives, one for downloading, one for finished files, all NTFS. I have cleared enough room on hdb and hdc so that all files will fit on either drive. My plan is as follows:

1: Using XP copy all files from hdb to hdc.
2: Format hda and install ubuntu
3: Format hdb to a *nix filesystem
4: Mount hdc as ro and copy files over to hdb
5: Format hdc with *nix filesystem and restore my files.

Now, I need some information. I require the following functionality: Azureus with the RSS aggregate feed plugin, GNOME autologin and the ability for the windows computers on my network to read (And possibly write to) the files on hdb and hdc.

What filesystem should I use (I will be downloading large 4+gig files). Does anyone forsee any problems with the above? Oh, and what tools should I use for formatting etc.

Just to clarify my technical expertise, I'm a certified I.T. Professional with MCSE qualification, but I have virtually no experiance with Linux other than the last two weeks having it on my laptop.

---

### Post by az on 2005-08-06
"Now, I need some information. I require the following functionality: Azureus with the RSS aggregate feed plugin, GNOME autologin and the ability for the windows computers on my network to read (And possibly write to) the files on hdb and hdc."

You will need to install java to run azureus.  Look on the wiki, it should take you about four minutes.  Install the samba package to enable filesharing.  It should take you another four minutes to get autologin and network shares set up.



"What filesystem should I use (I will be downloading large 4+gig files). Does anyone forsee any problems with the above? Oh, and what tools should I use for formatting etc."

Pick the default when you install.  Ext3 allows for 16 Gig-sized  files.  If you want to use an entire hard drive for your install, just pick guided partitioning and you are good to go.  Do not format things in advance since many windows tools do not do it properly.  Let the partitioner on the install cd do it.


"with MCSE qualification"

How long a course is that?

---

### Post by Hig on 2005-08-06
6 months if you do it in a college, but I just got the books and paid for the exam. 

ext3 can be read by windows over samba yeah?

EDIT: Sorry, it's 6 months for an MCP, not an MCSE. I always get them confused.

---

### Post by Hig on 2005-08-07
Oh yeah, one more criteria, I need to be able to read my files with my Xbox media centre. Will ext3 be able to be read over my network?

Come on... I need an answer so I can get started.

---

### Post by az on 2005-08-07
Samba is filesystem agnostic.

---

### Post by idokus on 2005-08-07
[QUOTE=Hig]
ext3 can be read by windows over samba yeah?
[/QUOTE]
if you use a linux server and a xp client pc then ext3 can be read in windows via samba. Since samba emulates the SMB from a windows fileserver. But you will need to have a correctly configured samba running on a linux server.
<a href=http://samba.org>samba</a> for more detailed information.

this is for a single pc setup: ext3 cannot be read in winxp unless you use some external apps to save the files from such a partition to an NTFS of FAT partition in xp. (but if you want to swap disks it's better to use fat. which is readable and writable using xp or linux)

---

### Post by Gezzer on 2005-08-07
[QUOTE=][/QUOTE]
 it maybe worth while setting up a partition that is formatted to FAT32

as both windows & linux can read, write to it so it can be used as a gateway/bridge between the two OS's
just a thought ...

---

