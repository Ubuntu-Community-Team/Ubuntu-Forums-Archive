---
title: "How ton mount  a cd-rom drive?"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by IxAxU on 2008-11-19
Hi, I'm a newbie to linux.
I'm trying to install the server editon (64-bit) version 8.10
I'm having problems to install/mount my cdrom
the drive, is hdc. Read my other posts to see the problem I'm having.

Thanks.
IxAxU

---

### Post by IxAxU on 2008-11-19
mm.. i got the best idea.. I took out the drive.. and saw this.
CD-RW/DVD-ROM DRIVE
model: GCC-4120B

S/N: 2053020358

(may 2002, pretty damn old?)

---

### Post by IxAxU on 2008-11-19
[CENTER][SIZE="7"][FIXED][/SIZE](No i was wrong, not fixed)
I searched "GCC-4120B ubuntu mount"

got the results of an archive..
[http://ubuntuforums.org/archive/index.php/t-205449.html](http://ubuntuforums.org/archive/index.php/t-205449.html)
tells you what path it is.. :)



**NVM i was wronged..**
[/CENTER]

----
I typed ```
# mount -t iso9660 /dev/hdc /media/cdrom0/
```
in the console..

my error, > failed:no such file or directory

than i tried.
```
# mount -t iso9660 /dev/hdc
```

> Cant' find dev/hdc in etc/fstab

So.. once again I'm stuck =/

---

### Post by IxAxU on 2008-11-20
*bump*

---

### Post by snova on 2008-11-20
mount requires that the target directory exist.

Possibly look into pmount?

---

### Post by IxAxU on 2008-11-20
I'm a total newbie to linux.. could you give me an example command?

---

### Post by IxAxU on 2008-11-20
*bump*

---

### Post by cariboo on 2008-11-20
> # mount -t iso9660 /dev/hdc /media/cdrom0/

Remove the trailing slash from the above command so it looks like this:

```
# mount -t iso9660 /dev/hdc /media/cdrom0
```

Jim

---

### Post by IxAxU on 2008-11-21
> **cariboo907 said:**
> Remove the trailing slash from the above command so it looks like this:

```
# mount -t iso9660 /dev/hdc /media/cdrom0
```

Jim

```
Mount: Mounting device /dev/hdc/ /media/cdrom0 failed: No such file or directory
```

I'm getting pretty bored trying to mount this dumb drive..
How do I make that file/directory?
(command line would be appreciated)

---

### Post by IxAxU on 2008-11-21
If I do,
> ls /dev/hdc 
and it turns up not existant.. would that mean the whole time trying to mount hdc it wasn't even existing? 

How do I make sure I have the right command for the cdrom?
How can I find the cdrom directory?

---

### Post by Arseny92 on 2008-11-21
> How can I find the cdrom directory?to view the files on the cd
```

ls /media/cdrom0

```
> 
If I do,
[QUOTE]ls /dev/hdc
and it turns up not existant.. would that mean the whole time trying to mount hdc it wasn't even existing? 
[/quote]
are you sure that your drive is /dev/hdc ? maybe is it /dev/sda (sdb, sdc..) ? Note, that when I installed ubuntu, it mounted my hard drive as /dev/sda (first SCSI disk), although it is plugged to the systemboard via IDE as primary master (it should be /dev/hda , but...)..

---

### Post by ciscosurfer on 2008-11-21
Please post the output of the following command```
sudo fdisk -l
```

---

### Post by IxAxU on 2008-11-21
> **Arseny92 said:**
> to view the files on the cd
```

ls /media/cdrom0

```

are you sure that your drive is /dev/hdc ? maybe is it /dev/sda (sdb, sdc..) ? Note, that when I installed ubuntu, it mounted my hard drive as /dev/sda (first SCSI disk), although it is plugged to the systemboard via IDE as primary master (it should be /dev/hda , but...)..
-- I can't ls /media/cdrom0 (because I never mounted the cdrom0)

How can I know, I tried, /dev/sdc,sda,sdb,sde,hda,hdb,hdc,hdd,
all come out.. as no such file/directory.

(my setup is, master (hard drive) slave (cdrom)


> **ciscosurfer said:**
> Please post the output of the following command```
sudo fdisk -l
```
sudo does not work. 
-/bin/sh: sudo not found.. (guess it's not a default command?)

.. why is this so hard :-p

---

### Post by Arseny92 on 2008-11-21
> sudo does not work. 
-/bin/sh: sudo not found.. (guess it's not a default command?)
sudo is used to gain root privileges in ubuntu
if sudo does not work, you can try to run fdisk -l when logged in as root (note, that logging in as root is unsafe, because root is the superuser, and he has privileges to do anything) without sudo, just fdisk -l

---

### Post by ciscosurfer on 2008-11-21
@IxAxU,

I guess I'm a little confused.  If you don't have the system installed yet, how are you typing these commands?  If you're running from the Server disk, it means the CD is already loaded.  When you inserted the CD, you didn't get an Installation screen?  Please fill in some of these details.

The fact that sudo is giving you trouble is also of concern.  Please run and provide the output for these commands```
which sudo
whereis sudo
```I also need you to run this command and attach the output to your next post or paste it directly into your post, your choice```
dmesg > dmesg.txt
```Also run```
groups
```Do you see cdrom or not? Then run```
id
```and post the output.

---

### Post by IxAxU on 2008-11-22
Ty for helping me out cisco..
Let me rephrase myself, and also give you some more information.

I downloaded and converted the ISO (server 64-bit 8.1) and placed it on a disk..The disk works.. the CDROM works.. I'm in the installation process of the server o.s.

But the setup requires it "Detect and mount CD-ROM"

I also saw a few posts about the "Aperture beyond 4GB. Ignoring."  error.. but that doesn't seem to be a problem because the installation went forward.

When the installation tries to detect and mount.. it tries to detect the CD-ROM.. but fails.. and asks for a floppy disk driver.
I do not have a floppy drive, nor the drivers.. 

But I did give me the option to use the console (ALT-F2)
to mount the cdrom drive..

---
Now I will post my results from the following commands you asked me for.
---
I wrote "dmesg > dmesg.txt"
exactly like shown in the console.. but I do not get any results.
```
groups
```
gives me
> -/bin/sh: groups:not found
```
id
```
> uid=0(root) gid=0(root)

basically.. all commands.. are non-existent.

---

### Post by ciscosurfer on 2008-11-23
> **IxAxU said:**
> I downloaded and converted the ISO (server 64-bit 8.1) and placed it on a disk..The disk works.. the CDROM works.. I'm in the installation process of the server o.s.I'm going to assume that when you say "converted" that you just mean "burned" to disc, seeing as how you say the disc and the drive are okay (but that's debatable at this point, in my opinion). The CD-ROM may simply be too old and might be having a hard time reading the disc; and conversely, the OS may be having a hard time trying to detect the CD-ROM drive.

> But the setup requires it "Detect and mount CD-ROM"

I also saw a few posts about the "Aperture beyond 4GB. Ignoring." error.. but that doesn't seem to be a problem because the installation went forward.Yeah. I'm reading through some bug reports on this error right now. Do you have a need to run the 64-bit version b/c you might have better luck with the 32-bit version as these errors don't seem to be reported when installing from the 32-bit version. Apparently the error you were getting has to do with the GART IOMMU and one way to bypass the error is to set a kernel line option of iommu=soft

One link I'm reading is here.

> When the installation tries to detect and mount.. it tries to detect the CD-ROM.. but fails.. and asks for a floppy disk driver.
I do not have a floppy drive, nor the drivers..Asking for a floppy driver is the default fallback from what I understand when it cannot detect any media. Nothing to concern yourself about--we're concerned about your CD-ROM.

> But I did give me the option to use the console (ALT-F2)
to mount the cdrom drive..Interesting problem: you normally need to mount a CD with sudo permissions but sudo doesn't seem to be loaded. If the system boots with sudo permissions enabled, you could leave "sudo" off and do something like```
mount -t iso9660 /dev/scd0 /media/cdrom0
```Or create a mount point and then try to mount```
mkdir /media/intrepid
mount -t iso9660 /dev/scd0 /media/intrepid
```But, considering the option is given to switch to another tty to try and mount the disc, and normally one would need sudo permission to do so, leads me to believe that using sudo is not necessary.
> 
Now I will post my results from the following commands you asked me for.
...
When you ran **dmesg > dmesg.log** what happened is you redirected the output of **dmesg** to a file called "**dmesg.log**"  and that's my fault for not explaining that more clearly. So, once you run that command and then run an **ls** command, you'll see the file called dmesg.log inside the directory you are in. The absense of certain other details from the other commands tells me where in the install process you are and that was all I needed to know.

To recap, here are the things I would recommend trying to do:
1) Evaluate first if you need to be running the 64-bit OS, if not, try the 32-bit version instead
2) Whichever option you decide on from above, download and burn a fresh copy just to be sure that the ISO is good.  It would be a good idea to md5sum the ISO as well to make sure the download is in tact
3) Try using **/dev/scd0** for your device name when trying to mount
4) Evaluate if the CD-ROM isn't just broken (the CD should have been automatically mounted when inserted and the install process should begin from there
5) You can try using other kernel options at boot time to prevent certain problems.  See [this page]("https://help.ubuntu.com/community/BootOptions#Kernel%20Options") for more details.

That was probably long-winded, but there are a lot of "potentials" going on here: a broken disk, a bad burn, a bad iso, a bad drive, incorrect device names being called...

---

### Post by IxAxU on 2008-11-23
I've never md5sum an ISO.. this is the first ISO I had burned.
I will try to re-burn it..
I'm almost 100% sure that my CD-ROM is able to read the disc.. and that the o.s. is just having trouble to mount my CDROM because of it's late model. (2002)

I will try the 32-bit edition server, I don't have any reason to use a 64-bit edition o.s. but there's a first for everything.
:)

I will use your tips.. and explanations..
and see what the outcome is..
hopefully it'll turn  out well..
I may not reply.. tonight.. or tomorrow.
b/c my job is interfering.

---

### Post by IxAxU on 2008-12-19
Okay, I finally got my new wireless adapter.. because my USB adapter was a pain in the ***, kept dropping my connection when downloading the .Iso

Now I have a problem, with CRC (cyclic redundancy check)?
> which as I understand it is like a a checksum. It compares the new cheksum with its previous value. If the checksums dont match, the system will halt.
Which means this checksum for my iso was corrupt?
That sucks, because I made sure it was good.. and it was..
but perhaps burning it went bad? But my burner even verify's the burn.

:/ .. I'll try to re-burn..

---

### Post by IxAxU on 2008-12-19
> **Arseny92 said:**
> sudo is used to gain root privileges in ubuntu
if sudo does not work, you can try to run fdisk -l when logged in as root (note, that logging in as root is unsafe, because root is the superuser, and he has privileges to do anything) without sudo, just fdisk -l

Well.. even with a fresh copy of 32-bit server, fdisk -l does not work.
fdisk was not found, in /bin/sh

I tried to cat, /dev/hdc/ but /hdc/ is not a directory.. so I have no idea how to find out what directory the device is in.. :[

---

