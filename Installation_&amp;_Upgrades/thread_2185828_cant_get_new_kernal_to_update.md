---
title: "cant get new kernal to update"
date: 2013-11-04
forum: Installation &amp; Upgrades
---

### Post by leeper69 on 2013-11-04
Hi I am having problems updating to the new kernal and am trying to attach a screenshot of my terminal to show the problem. I tryed using the attchment tool but am doing something wrong. can enyone explain how this is done?

---

### Post by Bashing-om on 2013-11-04
leeper69; Hi !

Show us the output - placed between code tags -:
 code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
of terminal codes:
```

sudo apt-get update
sudo apt-get upgrade

```
And the tale will be told.

[INDENT][INDENT]help is but a keyboard away
[/INDENT][/INDENT]

---

### Post by philinux on 2013-11-04
> **leeper69 said:**
> Hi I am having problems updating to the nwe kernal and am trying to attach a screenshot of my terminal to show the problem. I tryed using the attchment tool but am doing something wrong. can enyone explain how this is done?

Check you have the package linux-generic installed. If not install it.

---

### Post by ajgreeny on 2013-11-04
Can we check that you're not still on ubuntu 10.10 as your details show, because that has now lost support, therefore no repos are available any more at their old url.

---

### Post by leeper69 on 2013-11-04
I am having this problem with ver 13.10 and still cant get the insert  image button to work it just puts quote marks around the url with no picture. I also cant figure out how to get terminal code to work using tags but will try one more time.

---

### Post by leeper69 on 2013-11-04
Hi I am having this problem using 13.10[CODEE: /usr/sh] [/CODE] Well as you can see I still cant get it right I wll keep reading and try agin! well I finaly got a copy of my terminal attched to this post hope it will help.

---

### Post by Bashing-om on 2013-11-05
leeper69; Morning.

I am having difficulty reading and comprehending the screenshot. My disabilities !

Try this to transfer the output to this thread:
The thread is open, click on the "#" icon at the top of the post in the tools bar; this places the code tag into the thread posting. The cursor is now between the "code tags" and when you right click and choose "paste" the contents of your system's clipboard will be inserted - that you have "dragged" to highlight and copied", is inserted between those "code tags".

I can see that there is a problem with a kernel, but not the nature of that problem.

[INDENT][INDENT]my little bit to try and help
[/INDENT][/INDENT]

---

### Post by leeper69 on 2013-11-05
Hi  Bashing-om here goes ```
/home/us/Pictures/terminal.png
```
second try!```
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up initramfs-tools (0.103ubuntu1) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-3.11.0-12-generic (3.11.0-12.19) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.11.0-12-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.11.0-12-generic /boot/vmlinuz-3.11.0-12-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.11.0-12-generic /boot/vmlinuz-3.11.0-12-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.11.0-12-generic /boot/vmlinuz-3.11.0-12-generic
update-initramfs: Generating /boot/initrd.img-3.11.0-12-generic
/usr/share/initramfs-tools/hooks/dmsetup: 1: /usr/share/initramfs-tools/hooks/dmsetup: &#65533;&#65533;&#65533;&#65533;&#65533;: not found
/usr/share/initramfs-tools/hooks/dmsetup: 1: /usr/share/initramfs-tools/hooks/dmsetup: &#65533;&#65533;&#65533;&#65533;&#65533;: not found
E: /usr/share/initramfs-tools/hooks/dmsetup failed with return 127.
update-initramfs: failed for /boot/initrd.img-3.11.0-12-generic with 127.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.11.0-12-generic.postinst line 1010.
dpkg: error processing linux-image-3.11.0-12-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-3.11.0-12-generic:
 linux-image-extra-3.11.0-12-generic depends on linux-image-3.11.0-12-generic; however:
  Package linux-image-3.11.0-12-generic is not configured yet.

dpkg: error processing linux-image-extra-3.11.0-12-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.11.0-12-generic; however:
  Package linux-image-3.11.0-12-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.11.0-12-generic; however:
  Package linux-image-extra-3.11.0-12-generic is not configured yet.

dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    update-initramfs: Generating /boot/initrd.img-3.11.0-7-generic
/usr/share/initramfs-tools/hooks/dmsetup: 1: /usr/share/initramfs-tools/hooks/dmsetup: &#65533;&#65533;&#65533;&#65533;&#65533;: not found
/usr/share/initramfs-tools/hooks/dmsetup: 1: /usr/share/initramfs-tools/hooks/dmsetup: &#65533;&#65533;&#65533;&#65533;&#65533;: not found
E: /usr/share/initramfs-tools/hooks/dmsetup failed with return 127.
update-initramfs: failed for /boot/initrd.img-3.11.0-7-generic with 127.
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-3.11.0-12-generic
 linux-image-extra-3.11.0-12-generic
 linux-image-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
us@us-EP45-UD3R:~$ 

```

---

### Post by leeper69 on 2013-11-05
Hi Bashing-om thank you for taking the time to explain how to post code!!! hope this helps to solve my upgrading problem.

---

### Post by Bashing-om on 2013-11-05
leeper69;Hey,

I am playing catch up. This is the first I have encountered such a situation ! .. Does the control file exist ?
post back, (Haw, now you know how ) the output of terminal code:
```

ls -la /usr/share/initramfs-tools/hooks/dmsetup

```

And only if that file exist; show us:
```

cat /usr/share/initramfs-tools/hooks/dmsetup

```

will see if we can finger this one out.

[INDENT][INDENT]all in the process of learning
[/INDENT][/INDENT]

---

### Post by leeper69 on 2013-11-05
Hi Bashing-om here is the code you asked for```
us@us-EP45-UD3R:~$ sudo ls -la /usr/share/initramfs-tools/hooks/dmsetup
[sudo] password for us: 
-rwxr-xr-x 1 root root 472 May  4  2012 /usr/share/initramfs-tools/hooks/dmsetup
us@us-EP45-UD3R:~$ sudo cat /usr/share/initramfs-tools/hooks/dmsetup
&#65533;&#65533;&#65533;&#65533;&#65533;us@us-EP45-UD3R:~$ 

``` THANKS agin!!!

---

### Post by leeper69 on 2013-11-05
Hi Bashing-om here is the code you asked for```
us@us-EP45-UD3R:~$ sudo ls -la /usr/share/initramfs-tools/hooks/dmsetup
[sudo] password for us: 
-rwxr-xr-x 1 root root 472 May  4  2012 /usr/share/initramfs-tools/hooks/dmsetup
us@us-EP45-UD3R:~$ sudo cat /usr/share/initramfs-tools/hooks/dmsetup
&#65533;&#65533;&#65533;&#65533;&#65533;us@us-EP45-UD3R:~$ 

```
THANKS agin!!!

---

### Post by leeper69 on 2013-11-05
Hi  bashing-om  I posted the above mesage three times because it wasent showing up on the thread. now it is sorry, now it is. in my terminal the 4 dimonds in frunt of us@us have ? marks in them. I have never seen this behavior before eather. I am able to upgrade all other files except for the four showen in the previous code.
THANKS agin!!!

---

### Post by Bashing-om on 2013-11-05
leeper69; Hey,
That certainly indicated where the problem lies !
For reference my output of that file:
```

sysop@1304mini:~$ cat /usr/share/initramfs-tools/hooks/dmsetup
#!/bin/sh

case $1 in
prereqs)
        echo "udev"
        exit 0
        ;;
esac

. /usr/share/initramfs-tools/hook-functions

mkdir -p $DESTDIR/lib/udev/rules.d/
for rules in 55-dm.rules 60-persistent-storage-dm.rules; do
        if   [ -e /etc/udev/rules.d/$rules ]; then
                cp -p /etc/udev/rules.d/$rules $DESTDIR/lib/udev/rules.d/
        elif [ -e /lib/udev/rules.d/$rules ]; then
                cp -p /lib/udev/rules.d/$rules $DESTDIR/lib/udev/rules.d/
        fi
done

copy_exec /sbin/dmsetup

manual_add_modules dm_mod

```

So, how to replace that file in your system ??
Do you have a liveDVD we may be able to pull that file from ?

At this point all I know to do is replace this file and then see if any other damage has been done. I am always leery when I find a system file that has been corrupted, what else is corrupted.

[INDENT][INDENT]doesn't hurt to try
[/INDENT][/INDENT]

---

### Post by leeper69 on 2013-11-05
Hi Bashing-om I do have a live dvd and as far as I can tell the rest of my install is ok.

---

### Post by Bashing-om on 2013-11-05
leeper69: outstanding,

Let's copy that file from the liveDVD to the install !
First we need to determine the location of your "/" so we can copy to it.
show:
```

cat /etc/fstab
sudo blkid

```

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by leeper69 on 2013-11-05
Hi Bashing-om here is the code you asked for```
us@us-EP45-UD3R:~$ sudo cat /etc/fstab
[sudo] password for us: 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=51610bc1-15ed-4ab1-9b6a-59916e614a45 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=f03f4609-1c23-493a-9dd6-01ce52c46642 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
us@us-EP45-UD3R:~$ sudo blkid
/dev/sda1: UUID="5aa169a5-727f-4349-9f30-bd6c63b7f194" TYPE="ext4" 
/dev/sda3: UUID="d0a3e069-a55b-463b-8df6-1aa42e63c8e4" TYPE="swap" 
/dev/sda5: UUID="51610bc1-15ed-4ab1-9b6a-59916e614a45" TYPE="ext4" 
us@us-EP45-UD3R:~$ 




```

---

### Post by Bashing-om on 2013-11-05
leeper69; OK !

Boot the liveDVD to a terminal:
Terminal commands:
```

sudo mkdir /mnt/work
sudo mount /dev/sda5 /mnt/work
sudo cp -p  /usr/share/initramfs-tools/hooks/dmsetup /mnt/work/usr/share/initramfs-tools/hooks/dmsetup
sudo umount /mnt/work

```

boot into the install and do:
```

sudo apt-get update
sudo apt-get upgrade

```

What results ???

[INDENT][INDENT]finer than a frogs hair ?
[/INDENT][/INDENT]

---

### Post by leeper69 on 2013-11-06
Hi Bashing-om I tryed to copy the dmsetup file from my xubuntu 13.10 bata dvd lasy night but ran into the following problems.
could not mount /dev/sda5/mnt/work!
so i booted up my unstable 13.10 on the hard drive and used terminal to go to /mnt then typed ls -a and there was no directory work so typed mkdir work and made one then shutdown and rebooted with the dvd.
I still couldent mount /dev/sda5/mnt/work. the terminal tells me there is no such directory. next I booted up the 13.10 on the hard drive and used file manager to find dmsetup and opend it with mousepad the file is empty.
rebooted with the dvd and opend dmsetup with mouse pad and hand copyed the script.
the following code is a copy of the script hand enterd in mouse pad in 13.10 on the hard drive.
```
#! /bin/sh


case $1 in
prereqs)
        echo "udev"
        exit 0
        ;;
esac
. /usr/share/initramfs-tools/hook-functions

mkdir -p $DESTDIR /lib/udev/rules.d/
for rules in 55-dm.rules 60-persistent-storage-dm.rules; do
        if [ -e /etc/udev/rules.d/$rules] ; then
            cp -p/lib/udev/rules.d/$ rules $DESTDIR /lib/udev/rules.d/
        elif [-e /lib/udev/rules.d/$rules] ; then
        cp -p /lib/udev/rules.d/$ rules $DESTDIR /lib/udev/rules.d/
        fi
done

copy_exec  /sbin/dmsetup

manual_add_modules dm_mod
```
then checked for acuracy with the script on the dvd next I used  chmod to alow me to edit dmsetup and copyed the script from the dvd by hand into the file and saved it with mouse pad as administator then used chmod to reset permision back to the way it was. now the script shows up in dmsetup.
after runing apt-get update and apt-get update the new kernal installed. Thanks for all your help with this!!!

---

### Post by Bashing-om on 2013-11-06
leeper69; Good morning,

There is a space - as the delimiter - between "sda5" and "/mnt/work" that I do not see in your advisement.
Reference for the future; Copy and paste works preventing typos. Copy from the thread and paste the commands into terminal.
 
However, the long way works for me too ! As long as that file is in place, no errors, and permissions restored; I expect it to work great and last long long time.
check: my permission output:
> 
sysop@1304mini:~$ ls -la /usr/share/initramfs-tools/hooks/dmsetup
-rwxr-xr-x 1 root root 472 Mar  2  2013 /usr/share/initramfs-tools/hooks/dmsetup
sysop@1304mini:~$ 


At this point we can expect the package manager to run !

Let us see what results !
```

sudo apt-get update
sudo apt-get upgrade

```

[INDENT][INDENT]more than one way to skin a cat
[/INDENT][/INDENT]

---

### Post by leeper69 on 2013-11-07
Hi Bashing-om
                         Thanks for all your help I wouldent have fixed my problem without it. I will try copy and paste for my next problem.
                          Every thing seemes to be working fine for now and I have learnd how to use the forum tools in the process.
Thanks agin you are a good teacher!!!

---

### Post by Bashing-om on 2013-11-07
leeper69; Glad the situation is under control !

You are quite welcome, sharing is a two way street, and I am but passing on what I have learned. Many people too have helped me along my way.
This too is a small contribution to promote open source in general, ubuntu in particular and to be an asset to our forum.

Please mark this thread as solved -> 1st post -> thread tools. 
Looking forward to our next adventure in learning.

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

