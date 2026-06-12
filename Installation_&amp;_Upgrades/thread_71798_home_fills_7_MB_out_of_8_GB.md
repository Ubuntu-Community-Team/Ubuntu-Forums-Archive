---
title: "/home fills 7 MB out of 8 GB"
date: 2005-10-04
forum: Installation &amp; Upgrades
---

### Post by Moonbuzz on 2005-10-04
Hello all, 
Here's what happened: up until now, I had two HD on my comp, one with Ubuntu, and one with Windows. I took another HD, that had WinXP on, and added it to my computer. For some unknown reason, that HD has 4 partitions, 3 formatted for Windows, and one which wasn't... (Meaning the person using that computer was actually using a 30GB HD for the price of 40GB).
What I did was to keep the 3 windows partitions, and add the empty one for Ubuntu. I did a clean install of Ubuntu, with one HD set to have 5 GB for / (root), another 1.4 GB for swap, and at the partition manager, I set the entire 8.4 empty partition as /home. I mounted all partitions as "primary" and not "logical".
When the installation was over, and Ubuntu was loaded, I found that the /home folder was about 7 MB big, when I right clicked on it for "properties" it informed me that it "sits" on an 8.4 GB drive. I reinstalled, to make sure I didn't do anything wrong, but no luck there.
Any ideas what I need to do/did wrong with the installation? I'm not that familiar with the partitioning manager, and up until this time I went with the defaults, just going over them to make sure I'm not formatting anything which I wasn't meant to. 
Any thoughts?

---

### Post by mlomker on 2005-10-04
It could be that the installer screen is rounding and the other isn't (some programs consider 1000KB a megabyte but it's really 1024).  

**df -h** from a prompt should give the real numbers.

---

### Post by Moonbuzz on 2005-10-04
I think you missed the point...
The /home folder is only 7 MEGAbytes, but it's an 8 GIGAbyte HD ;)

---

### Post by openmind on 2005-10-04
I'm sure someone will correct me if I'm wrong, (I'm still a n00b myself!) but on a fresh install without any settings or copying any folders over /home **will** be very small. (Only I don't know *how* small).
 
The Kernel, Apps, and most of everything in a new install is put in /(root). /home is waiting on you to fill it with themes, icons, music, pics, settings etc.
 
Log on, root around and see if everything is ok.

---

### Post by mlomker on 2005-10-04
> I think you missed the point...

It's quite possible that I don't get your point, because the question wasn't clear to me and remains unclear.

**df -h** will give you the space in use on each partition and the space that remains available.  That's a better measure of what is installed during an installation than looking at /home.
[URL="http://linux.org.mt/article/terminal#N10190"]
Here is[/URL] a description of the various directories in a stardard linux system.

---

### Post by Moonbuzz on 2005-10-04
The question was, why is the /home folder only 7 MB, and more important, how do I change it's maximum size? The folder, for some reason, doesn't allow me to exceed this 7 MB size. If I try copying anything larger than the 4 MB that are free in it, it'll throw me an error.

---

### Post by Snocrash on 2005-10-04
[QUOTE=openmind]I'm sure someone will correct me if I'm wrong, (I'm still a n00b myself!) but on a fresh install without any settings or copying any folders over /home **will** be very small. (Only I don't know *how* small).
The Kernel, Apps, and most of everything in a new install is put in /(root). /home is waiting on you to fill it with themes, icons, music, pics, settings etc.
Log on, root around and see if everything is ok.[/QUOTE]
I think this is right, the home folder is only 7M because there is nothing much in it yet.  Log in as you user and copy a bunch of stuff into your home folder, then see how big home is. Home is just a folder and will grow with use until it raches the limit of it's partition.
-Sno

---

### Post by mlomker on 2005-10-04
> If I try copying anything larger than the 4 MB that are free in it, it'll throw me an error.

What is the output of these?

```

mount
df -h

```

---

### Post by Moonbuzz on 2005-10-05
/dev/hdc1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev/hdb3 on /home type ext3 (rw)
/dev/hda1 on /home/windows/win-c type vfat (rw,umask=000)
/dev/hda5 on /home/windows/win-d type vfat (rw,umask=000)
/dev/hda6 on /home/windows/win-e type vfat (rw,umask=000)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)


Filesystem            Size  Used Avail Use% Mounted on
/dev/hdc1             4.6G  1.8G  2.6G  41% /
tmpfs                 126M     0  126M   0% /dev/shm
/dev/hdb3             7.4M  2.4M  4.7M  34% /home
/dev/hda1              32G   29G  2.3G  93% /home/windows/win-c
/dev/hda5              32G   26G  5.9G  82% /home/windows/win-d
/dev/hda6              13G  6.0G  6.1G  50% /home/windows/win-e
/dev                  4.6G  1.8G  2.6G  41% /.dev
none                  5.0M  2.8M  2.3M  56% /dev

---

### Post by dcraven on 2005-10-05
Oh I think I understand. His /home **partition** is 7M, but he was saying **folder**, which threw everyone off the scent :). All is more clear now.

As for the problem, I'm not sure but I suspect that it may have something to do with the windows stuff you mount in /home. Maybe mount those things at /mnt and try? I'm just shooting in the dark here though.

I only say this because adding up your windows drives comes pretty close to 80 give or take, and it just looks funny. I'd try mounting them at /mnt, then when you login to the new system, symlink them to your home dir if you like:
```

md ~/windows
ln -s /mnt/win-c ~/windows
ln -s /mnt/win-d ~/windows
ln -s /mnt/win-e ~/windows

```

Someone I'm sure will have better ideas though.
~djc

---

### Post by mlomker on 2005-10-05
> 
/dev/hdb3             7.4M  2.4M  4.7M  34% /home


That's like you said.  There's a known issue in Breezy that causes it to report the wrong sizes, but I was under the impression that it just misreports the size but you could actually continue copying files to it.  You're on Hoary, right?

How about 
```

sudo fdisk -l /dev/hdb3

```

You should be able to multiply the number of sectors by the sector size to get the partition's actual size.

---

### Post by Moonbuzz on 2005-10-05
[QUOTE=dcraven]
As for the problem, I'm not sure but I suspect that it may have something to do with the windows stuff you mount in /home. Maybe mount those things at /mnt and try? I'm just shooting in the dark here though.[/QUOTE]

I don't think so... It was that way before I mounted the windows folders there. I prefer having everything linked to /home, gives me less place to "run around", despite most of the files being elsewhere, but I have about 350 MB of documents and files that I backed up from my previous installation, and I want to place them at my /home/moonbuzz folder... that was the whole idea of adding a HD... But it doesn't allow me to copy anything more than about 4 MB :mad:

---

### Post by Moonbuzz on 2005-10-05
[QUOTE=mlomker]You're on Hoary, right?[/QUOTE]

Right, although anxiously waiting for Breezy. 

> 

How about 
```

sudo fdisk -l /dev/hdb3

```

You should be able to multiply the number of sectors by the sector size to get the partition's actual size.
I'll try it, can you give me a better idea of the actual process?

---

### Post by mlomker on 2005-10-05
```

root@mlomkernote:/ # sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
**Units = cylinders of 16065 * 512 = 8225280 bytes**

   Device Boot      Start         End      Blocks   Id  System
/dev/hda5            **1217        7112**    47359588+  83  Linux
root@mlomkernote:/ # df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda5              46G   22G   24G  47% /home

```

I'm doing some rounding here--as does the df -h output, by the looks of things.  I got the divisor for Gigabytes [from here.]("http://computer.howstuffworks.com/bytes6.htm")

7112 - 1217 = 5895 units
5895 * 8225280 = 48488025600 bytes
48488025600 / 1073741824 = 45.15 Gigabytes

---

### Post by John.Michael.Kane on 2005-10-05
Heres mine. as you can see 35M is used. so unless your installing some major apps or doing photo work ect your home folder will be small.. 

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             9.2G  1.3G  8.0G  14% /
tmpfs                 245M     0  245M   0% /dev/shm
/dev/hda3              27G   35M   27G   1% /home <-----
/dev                  9.2G  1.3G  8.0G  14% /.dev
none                  5.0M  2.8M  2.3M  55% /dev

---

### Post by Moonbuzz on 2005-10-06
I just read that Breezy is about to be released next week. I'm half tempted to delay all this and just wait for the new version... :confused:

---

### Post by mlomker on 2005-10-06
> I just read that Breezy is about to be released next week.

Like always, they'll fix problems as they go.  If you are updating every day then what you have is what'll be available next week.

---

### Post by Moonbuzz on 2005-10-06
[QUOTE=mlomker]If you are updating every day then what you have is what'll be available next week.[/QUOTE]
Not really, as I mentioned, this is a new install, haven't really updated anything yet. So what I have is basically 5.04 vanilla. (Or mocha, come to think about it...:D )

---

