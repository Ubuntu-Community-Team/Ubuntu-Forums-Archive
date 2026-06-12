---
title: "Attempting to Install Server 7.04 on older Compaq Proliant Server"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by celloyd on 2007-06-15
I'm currently trying to install Ubuntu Server 7.04 on an older Compaq Proliant DL380-R01 server.  I get as far as the partioning of disks and that's where it hangs up.

First I get:

**"Unable to determine geometry of file/device.  You should not use Parted unless you REALLY know what you're doing!"**

Then I can choose **Ignore **or **Cancel**.

Choosing **Ignore **I then get the option to choose a partitioning method.  I choose **Guided-use entire disk** and then it asks me to **select disk to partition:**

The only choice I have is "/dev/ida/c0d0 - 0B0  Compaq Smart Array"

After choosing that I get this:
[B]
Failed to partition the selected disk
This probably happened because the selected disk or free space is too small to be automatically partitioned.[/B]

I know this is not the case so I'm not sure where to go from here.

I am completely new to this and trying to get on board so any and all help would be greatly appreciated!

---

### Post by jaydeel on 2007-06-15
I got it installed!! I’m doing this on Compaq Prolinea ML370, using feisty fawn. But the problems seem exactly similar and seems to affect many compaq models that feature the compaq smart array controller. so hopefully it will work for you.

Since, the problem is a conflict between the compaq smart array and sym53c8xx module. I managed to get the install working by creating a custom install cd image, i modified the initrd.gz and removed the folder for the sym53c8xx_2 module. Recompiled the ISO image, and it's recognizing my compaq smart array RAID. 

Here are the steps I completed.

To create the custom CD…..

Mount the install…

```
mount /dev/scd0 /cdrom
```

Copy the CD.

```
mkdir -p /opt/cd-image
cp -r /cdrom/* /opt/cd-image
cp –r /cdrom/.disk /opt/cd-image

```
Extract the initrd.gz from the cd image

```
mkdir extract
cd extract

zcat /opt/cd-image/install/initrd.gz | cpio -i 
```

Delete the modules in sym53c8xx_2 directory 

```
rm –rf ./extract/lib/modules/2.6.20-15-generic/kernel/drivers/scsi/sym53c8xx_2
```

Repack the modified files.

Cd back to to your extract directory
```

find . | cpio -o --format='newc' |   gzip -9 > ~/initrd.gz.new
```

Put the new file into our CD replacing the old one.

```
cp ~/initrd.gz.new /opt/cd-image/install/initrd.gz
```

Now create the iso image.

```
IMAGE=custom.iso
BUILD=/opt/cd-image/

mkisofs -r -V "Custom Ubuntu Install CD" \
            -cache-inodes \
            -J -l -b isolinux/isolinux.bin \
            -c isolinux/boot.cat -no-emul-boot \
            -boot-load-size 4 -boot-info-table \
            -o $IMAGE $BUILD
```

Burn the image to CD and you should be able to install to your Compaq Smart Array controller.

But, during the installation another kernel is installed and when you reboot you will see “cpqarray: error sending ID controller”

Reboot off your custom install cd, and select the Rescue option. Mount your root partition and execute a shell on it.

(if you have /usr or /var on other partitions you should mount them before continuing)

Now execute the commands 

```
# echo "cpqarray" >> /etc/initramsfs-tools/modules
```

```
# update-initramfs -u
```

After the command finishes, remove the cd, reboot your system and everything should be gravy. 

References.

[https://help.ubuntu.com/community/InstallCDCustomization]("https://help.ubuntu.com/community/InstallCDCustomization")
[http://www.tundranerd.com/2007/02/14/cpqarray-error-sending-id-controller/]("http://www.tundranerd.com/2007/02/14/cpqarray-error-sending-id-controller/")
[http://www.extremetech.com/article2/0,1697,2132616,00.asp]("http://www.extremetech.com/article2/0,1697,2132616,00.asp")

---

### Post by celloyd on 2007-06-16
This is quite awesome...I'm very new to Linux and I will try to follow this but it seems quite overwhelming.  All of your directions are through Linux and I'm very much a novice right now.  I really appreciate your efforts on this.  I have a quick question.  Is the server version of the software without all graphical interfaces, or command line only?  I may need to install the desktop version (which was also giving me the same problems) and then add software later according to any eventual network needs of this machine I'm wanting to run as a server.

---

### Post by bspolarich on 2007-08-02
> **jaydeel said:**
> Burn the image to CD and you should be able to install to your Compaq Smart Array controller.


Hmm...I am having this exact issue on a DL380 G1 box.  I followed your instructions and burned the .iso back to a CD.  I can boot off of it, but I have two issues:

1.  Ubuntu installer says there's a problem reading from the CD-ROM when it tries to find e2fsprogs-udeb.  If I escape to a shell I find the package without a problem.

2.  If I verify the CD, it tells me initrd.gz fails checksum verification.

Any suggestions?

---

### Post by jnorth on 2007-09-16
Sweet - works for me an an old G1!

Edit:  Sorry, I just realized this is a fairly old thread...

---

### Post by celloyd on 2007-09-16
> **jnorth said:**
> Sweet - works for me an an old G1!

Edit:  Sorry, I just realized this is a fairly old thread...


Possibly you can answer a question for me.  Is the server version just like the desk top version or is it all command line?

---

### Post by jnorth on 2007-09-18
> **celloyd said:**
> Possibly you can answer a question for me.  Is the server version just like the desk top version or is it all command line?

Up to you... when you install it is all via cli and ncurses menu interface, BUT, after you have it up and running, you can just do an ```
sudo apt-get install ubuntu-desktop
``` and have a full gnome desktop just like you would get with the desktop version.

Of course, the reason I go with the server version is #1, for the optimized kernel, and #2, because it is a clean installation without having all of the extra x* and g* libs.  This is a apache and mysql dev machine for me, and I don't like all the extra stuff on it slowing it down.

If you really need a gui interface, and won't be doing high-traffic serving on it, I'd say just use the standard desktop version.

HTH

---

### Post by gstark on 2008-03-05
JayDeel,

Thanks for the post.  Your modified ISO worked like a charm for me on my DL380 G1!

---

### Post by dthacker on 2008-03-18
This has been tested on Ubuntu Server 7.10 (Gutsy Gibbon).  Thanks to GlennS and MarkC for posting their workarounds to [here on Launchpad.]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/110585")

Boot off the install CD
Hit F6 to bring up a string of boot options
Add "sym53c8xx.blacklist=true" (don't add the quotes)
Hit Enter to Boot
You **will** see an "unrecognized boot option" error, but your SmartArray will be recognized.

---

### Post by gstark on 2008-04-28
Thanks dthacker!

Your method just worked getting 8.04 to install on a DL380 G1.

---

