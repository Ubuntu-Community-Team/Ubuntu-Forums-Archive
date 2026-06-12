---
title: "Ye Olde Laptop"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by JusticeZero on 2008-01-29
Someone in the family wants me to put Ubuntu on their laptop, which dates from aproximately the time of steam engines. It's a Pentium something horribly slow with 64MB memory, currently running Windows and having issues which are very likely because of some corrupt stuff in Windows (but might be hardware, I don't know and I can't tell)
No floppy, it has a CD-ROM drive but I can't find any way to -boot- from it. No internet, possibly because of the fried Windows issue. (Like I said, I can't diagnose the thing.)
Any suggestions how to plow an xubuntu install onto it to see if it works better with an OS that hasn't had gods only knows what programs put on it for 10 years?
It is a Dell Latitude CP. (Just found the label)

---

### Post by Craigus on 2008-01-29
> Combining what we now know from both our experiences, a mini-HOWTO would read something like this:

HOWTO boot a Live or Install CD on machines that insist on booting from hard disk even when you select 'boot from CD' option in the BIOS.

1.) Create a boot floppy with the sbm.bin image on it. Here are two possible ways.

1a) If you have access to another Linux machine, this is easy: (I assume the cd is mounted on /media/cdrom1 and the floppy drive is /dev/fd0 and is not mounted

Insert the Live or Install CD, and a formatted 1.44M floppy into the drive. then

# cd /media/cdrom1/install
# dd if=sbm.bin of=/dev/fd0 bs=512

From this thread:

[http://ubuntuforums.org/archive/index.php/t-121518.html]("http://ubuntuforums.org/archive/index.php/t-121518.html")

---

### Post by pebo on 2008-01-29
Try [this]("https://help.ubuntu.com/community/Installation/LowMemorySystems") tutorial. You won't be able to install from the live cd with less than 256MB RAM, you need the alternate cd download.

---

### Post by .nedberg on 2008-01-29
Isn't 64MB RAM too little for Xubuntu? DSL might bee better, though not as user friendly

---

### Post by Partyboi2 on 2008-01-29
Quote from xubuntu web page
> To run the Desktop CD (LiveCD + Install CD), you need 128 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to run or 192 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to install. The Alternate Install CD only requires you to have 64 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM").
 To install Xubuntu, you need 1.5 [GB]("http://en.wikipedia.org/wiki/Gigabyte") of free space on your hard disk.
 Once installed, Xubuntu can run with 64 MB RAM, but it is strongly recommended to have at least 128 MB RAM.

[alternate iso for xubuntu ]("http://mirror.internode.on.net/pub/ubuntu/xubuntu/7.10/release/")

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

or maybe consider something like [darn small linux]("http://www.damnsmalllinux.org/")
or [puppy linux]("http://www.puppylinux.org/user/viewpage.php?page_id=1") both run on low ram machines

---

### Post by TeaSwigger on 2008-01-29
Personally I wouldn't consider trying ubuntu / kubuntu or xubuntu on an old laptop with 64mb ram. I would suggest seriously trying the suggestions by Partyboi2 for Darn Small Linux (DSL) or Puppy Linux. 

If you do want something else and expect a remotely modern system, you'll probably have to do a lot of homework. This site:
[http://kmandla.wordpress.com/](http://kmandla.wordpress.com/)
may be of invaluable help as it's focused on running on low spec systems like that.

---

