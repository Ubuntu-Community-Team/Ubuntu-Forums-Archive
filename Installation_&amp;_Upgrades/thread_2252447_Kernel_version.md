---
title: "Kernel version"
date: 2014-11-11
forum: Installation &amp; Upgrades
---

### Post by svref on 2014-11-11
My computer is all screwed up. Please go easy on me.

Ubuntu 14.04.1 LTS
3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC **2012** x86_64 x86_64 x86_64 GNU/Linux

It seems to me that I'm booting by default to a kernel that was built two years before this distribution was created. Doesn't that seem ... highly suspicious? Like maybe the fact that I'm somehow booting an ancient kernel could be causing the hideous display bugs I'm experiencing on my "fully supported" video card?

---

### Post by Bashing-om on 2014-11-11
svref; Hi !

Very likely:
> 
3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

is quite old; 
14.04 latest:
```

sysop@1404mini:~$ uname -a
Linux 1404mini 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
sysop@1404mini:~$

```

Let's see what we can do to get to the bottom of this:
Post back the outputs - Between Code Tags - of terminal commands:

Got operational space in /boot ?
```

df -h
df -i
dpkg -l | grep linix-

```
What is set to boot ?
```

ls -al /vmlinuz*
ls -al /init*

```
What is installed to be able to boot ?
```

ls -al /boot

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Once these are known we have some idea of what steps to take to get the latter kernel booting.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by svref on 2014-11-11
Thank you.

Here you go:

```
quad ~ **df -i**
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/sda1       1925120 366433  1558687   20% /
none             732002      2   732000    1% /sys/fs/cgroup
udev             720754    601   720153    1% /dev
tmpfs            732002    751   731251    1% /run
none             732002      3   731999    1% /run/lock
none             732002     43   731959    1% /run/shm
none             732002     24   731978    1% /run/user
/dev/sda3      38969344 424819 38544525    2% /home
/dev/sda4       1921360 181559  1739801   10% /mint
quad ~ **df -h**
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        29G  9.7G   18G  36% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            2.8G  4.0K  2.8G   1% /dev
tmpfs           1.2G  1.3M  1.2G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.8G   29M  2.8G   1% /run/shm
none            100M   32K  100M   1% /run/user
/dev/sda3       586G  280G  276G  51% /home
/dev/sda4        30G  4.9G   23G  18% /mint
quad ~ **dpkg -l | grep linux | grep image**
rc  linux-image-2.6.28-11-generic                               2.6.28-11.42                                        amd64        Linux kernel image for version 2.6.28 on x86/x86_64
rc  linux-image-2.6.28-13-generic                               2.6.28-13.45                                        amd64        Linux kernel image for version 2.6.28 on x86/x86_64
rc  linux-image-2.6.28-14-generic                               2.6.28-14.47                                        amd64        Linux kernel image for version 2.6.28 on x86/x86_64
rc  linux-image-2.6.28-15-generic                               2.6.28-15.52                                        amd64        Linux kernel image for version 2.6.28 on x86/x86_64
ii  linux-image-2.6.28-16-generic                               2.6.28-16.57                                        amd64        Linux kernel image for version 2.6.28 on x86/x86_64
rc  linux-image-2.6.31-15-generic                               2.6.31-15.50                                        amd64        Linux kernel image for version 2.6.31 on x86/x86_64
rc  linux-image-2.6.31-16-generic                               2.6.31-16.53                                        amd64        Linux kernel image for version 2.6.31 on x86/x86_64
rc  linux-image-2.6.31-17-generic                               2.6.31-17.54                                        amd64        Linux kernel image for version 2.6.31 on x86/x86_64
rc  linux-image-2.6.31-19-generic                               2.6.31-19.56                                        amd64        Linux kernel image for version 2.6.31 on x86/x86_64
rc  linux-image-2.6.31-20-generic                               2.6.31-20.58                                        amd64        Linux kernel image for version 2.6.31 on x86/x86_64
ii  linux-image-2.6.31-22-generic                               2.6.31-22.60                                        amd64        Linux kernel image for version 2.6.31 on x86/x86_64
rc  linux-image-2.6.32-23-generic                               2.6.32-23.37                                        amd64        Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-24-generic                               2.6.32-24.43                                        amd64        Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-25-generic                               2.6.32-25.45                                        amd64        Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-26-generic                               2.6.32-26.48                                        amd64        Linux kernel image for version 2.6.32 on x86/x86_64
ii  linux-image-2.6.32-27-generic                               2.6.32-27.49                                        amd64        Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.35-24-generic                               2.6.35-24.42                                        amd64        Linux kernel image for version 2.6.35 on x86/x86_64
rc  linux-image-2.6.35-25-generic                               2.6.35-25.44                                        amd64        Linux kernel image for version 2.6.35 on x86/x86_64
rc  linux-image-2.6.35-27-generic                               2.6.35-27.48                                        amd64        Linux kernel image for version 2.6.35 on x86/x86_64
rc  linux-image-2.6.35-28-generic                               2.6.35-28.50                                        amd64        Linux kernel image for version 2.6.35 on x86/x86_64
ii  linux-image-2.6.35-30-generic                               2.6.35-30.54                                        amd64        Linux kernel image for version 2.6.35 on x86/x86_64
ii  linux-image-2.6.38-11-generic                               2.6.38-11.50                                        amd64        Linux kernel image for version 2.6.38 on x86/x86_64
rc  linux-image-3.0.0-12-generic                                3.0.0-12.20                                         amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-13-generic                                3.0.0-13.22                                         amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-14-generic                                3.0.0-14.23                                         amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-15-generic                                3.0.0-15.26                                         amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-16-generic                                3.0.0-16.29                                         amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-17-generic                                3.0.0-17.30                                         amd64        Linux kernel image for version 3.0.0 on x86/x86_64
ii  linux-image-3.13.0-39-generic                               3.13.0-39.66                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-24-generic                                3.2.0-24.39                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-27-generic                                3.2.0-27.43                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-29-generic                                3.2.0-29.46                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-32-generic                                3.2.0-32.51                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-34-generic                                3.2.0-34.53                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-40-generic                                3.2.0-40.64                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-41-generic                                3.2.0-41.66                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-51-generic                                3.2.0-51.77                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-52-generic                                3.2.0-52.78                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-53-generic                                3.2.0-53.81                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-56-generic                                3.2.0-56.86                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-57-generic                                3.2.0-57.87                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-59-generic                                3.2.0-59.90                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-60-generic                                3.2.0-60.91                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-61-generic                                3.2.0-61.93                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-70-generic                                3.2.0-70.105                                        amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic                         3.13.0-39.66                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                         3.13.0.39.46   
quad ~** ls -al /vmlinuz***
lrwxrwxrwx 1 root root 30 Nov  5 15:16 /vmlinuz -> boot/vmlinuz-3.13.0-39-generic
quad ~ **ls -al /init***
lrwxrwxrwx 1 root root 33 Nov  5 15:16 /initrd.img -> boot/initrd.img-3.13.0-39-generic
quad ~ **ls -al /boot**
total 151456
drwxr-xr-x  3 root root    12288 Nov  5 15:46 ./
drwxr-xr-x 25 root root     4096 Nov 11 21:40 ../
-rw-r--r--  1 root root   524784 Nov 11  2009 abi-2.6.28-16-generic
-rw-r--r--  1 root root   624388 May 27  2010 abi-2.6.31-22-generic
-rw-r--r--  1 root root   646144 Dec  1  2010 abi-2.6.32-27-generic
-rw-r--r--  1 root root   700977 Jun  7  2011 abi-2.6.35-30-generic
-rw-r--r--  1 root root   730545 Sep 12  2011 abi-2.6.38-11-generic
-rw-r--r--  1 root root  1164547 Oct 28 10:25 abi-3.13.0-39-generic
-rw-r--r--  1 root root   791075 May 21  2012 abi-3.2.0-24-generic
-rw-r--r--  1 root root    90655 Nov 11  2009 config-2.6.28-16-generic
-rw-r--r--  1 root root   105746 May 27  2010 config-2.6.31-22-generic
-rw-r--r--  1 root root   110601 Dec  1  2010 config-2.6.32-27-generic
-rw-r--r--  1 root root   122657 Jun  7  2011 config-2.6.35-30-generic
-rw-r--r--  1 root root   130326 Sep 12  2011 config-2.6.38-11-generic
-rw-r--r--  1 root root   165712 Oct 28 10:25 config-3.13.0-39-generic
-rw-r--r--  1 root root   140341 May 21  2012 config-3.2.0-24-generic
drwxr-xr-x  2 root root     4096 Nov 11 22:49 grub/
-rw-r--r--  1 root root  7284018 Dec  4  2009 initrd.img-2.6.28-16-generic
-rw-r--r--  1 root root  7985577 Jul 14  2010 initrd.img-2.6.31-22-generic
-rw-r--r--  1 root root  9886591 Jan 11  2011 initrd.img-2.6.32-27-generic
-rw-r--r--  1 root root 12652867 Aug 25  2011 initrd.img-2.6.35-30-generic
-rw-r--r--  1 root root 13320508 Oct 15  2011 initrd.img-2.6.38-11-generic
-rw-r--r--  1 root root 27568932 Nov  5 15:29 initrd.img-3.13.0-39-generic
-rw-r--r--  1 root root 20789622 Jul 11  2013 initrd.img-3.2.0-24-generic
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-r--r--  1 root root  1864822 Nov 11  2009 System.map-2.6.28-16-generic
-rw-r--r--  1 root root  2135133 May 27  2010 System.map-2.6.31-22-generic
-rw-r--r--  1 root root  2156429 Dec  1  2010 System.map-2.6.32-27-generic
-rw-r--r--  1 root root  2345040 Jun  7  2011 System.map-2.6.35-30-generic
-rw-------  1 root root  2656297 Sep 12  2011 System.map-2.6.38-11-generic
-rw-------  1 root root  3386936 Oct 28 10:25 System.map-3.13.0-39-generic
-rw-------  1 root root  2884673 May 21  2012 System.map-3.2.0-24-generic
-rw-r--r--  1 root root     1170 Nov 11  2009 vmcoreinfo-2.6.28-16-generic
-rw-r--r--  1 root root     1336 May 27  2010 vmcoreinfo-2.6.31-22-generic
-rw-r--r--  1 root root     1336 Dec  1  2010 vmcoreinfo-2.6.32-27-generic
-rw-r--r--  1 root root     1336 Jun  7  2011 vmcoreinfo-2.6.35-30-generic
-rw-------  1 root root     1369 Sep 12  2011 vmcoreinfo-2.6.38-11-generic
-rw-r--r--  1 root root  3513024 Nov 11  2009 vmlinuz-2.6.28-16-generic
-rw-r--r--  1 root root  3949696 May 27  2010 vmlinuz-2.6.31-22-generic
-rw-r--r--  1 root root  4049888 Dec  1  2010 vmlinuz-2.6.32-27-generic
-rw-r--r--  1 root root  4348528 Jun  7  2011 vmlinuz-2.6.35-30-generic
-rw-------  1 root root  4526784 Sep 12  2011 vmlinuz-2.6.38-11-generic
-rw-------  1 root root  5808544 Oct 28 10:25 vmlinuz-3.13.0-39-generic
-rw-------  1 root root  4965968 May 21  2012 vmlinuz-3.2.0-24-generic


```


So it looks like there are newer kernels there. However, the boot boot time menu presents me only with a list of options dating from 2012. Somehow that menu is controlled by the OS on /dev/sda4, not this OS (/dev/sda1). In the old days, I would have just done "sudo lilo" and that would have installed a new boot menu. But nowadays ... nowadays I don't know what to do. 

Preserving bootability to the OS on /dev/sda4 is not important to me.

---

### Post by Bashing-om on 2014-11-12
svref; Hummm ....

I am surprised, and do not see the .old configs - that makes me put the brakes on hard !
> 
sysop@1404mini:~$ ls -al /vmlinuz*
lrwxrwxrwx 1 root root 30 Oct 29 12:23 /vmlinuz -> boot/vmlinuz-3.13.0-39-generic
lrwxrwxrwx 1 root root 30 Oct  9 12:29 /vmlinuz.old -> boot/vmlinuz-3.13.0-37-generic
sysop@1404mini:~$

sysop@1404mini:~$ ls -al /init*
lrwxrwxrwx 1 root root 33 Oct 29 12:23 /initrd.img -> boot/initrd.img-3.13.0-39-generic
lrwxrwxrwx 1 root root 33 Oct  9 12:29 /initrd.img.old -> boot/initrd.img-3.13.0-37-generic
sysop@1404mini:~$


Not at all certain how to proceed, will take some time to consider on my part.
Meanwhile perhaps others can advise ?

Obviously we need to clean out those old kernels (from a full CHroot to insure we are in the working install ??), also need to look at what is building the grub.cfg file:
```

ls -al /etc/grub.d

```
And what has been built:
```

cat /boot/grub/grub.cfg

```

Consider installing kernel 3.13.0-37-generic .
Consider (re-)installing grub with the OS in sda1 as the primary booting Operating System ?


[INDENT][INDENT]a 1st is a first, no .old - hummm
[/INDENT][/INDENT]

---

### Post by svref on 2014-11-12
The lack of ".old" files goes over my head.

I don't think that *this* grub builds the menu that boots the machine. I think it's whatever's on /dev/sda4. Not even sure it's grub. I'll take a photo of it in a bit...


```
quad ~ **ls -al /vmlinuz* /init***
lrwxrwxrwx 1 root root 33 Nov  5 15:16 /initrd.img -> boot/initrd.img-3.13.0-39-generic
lrwxrwxrwx 1 root root 30 Nov  5 15:16 /vmlinuz -> boot/vmlinuz-3.13.0-39-generic
quad ~ **ls -al /etc/grub.d**
total 92
drwxr-xr-x   2 root root  4096 Nov  5 15:28 ./
drwxr-xr-x 202 root root 12288 Nov 11 23:16 ../
-rwxr-xr-x   1 root root  9424 May 15 15:02 00_header*
-rwxr-xr-x   1 root root  6058 May  8  2014 05_debian_theme*
-rwxr-xr-x   1 root root 11608 May 15 15:02 10_linux*
-rwxr-xr-x   1 root root 10412 May 15 15:02 20_linux_xen*
-rwxr-xr-x   1 root root  1992 Mar 12  2014 20_memtest86+*
-rwxr-xr-x   1 root root 11692 May 15 15:02 30_os-prober*
-rwxr-xr-x   1 root root  1416 May 15 15:02 30_uefi-firmware*
-rwxr-xr-x   1 root root   214 Oct 29  2009 40_custom*
-rwxr-xr-x   1 root root   216 May 15 15:02 41_custom*
-rw-r--r--   1 root root   483 Oct 29  2009 README
quad ~ **cat /boot/grub/grub.cfg**
cat: /boot/grub/grub.cfg: No such file or directory
```

---

### Post by svref on 2014-11-12
[IMG]http://i105.photobucket.com/albums/m235/dcmorse/ss_zps00b78823.jpg[/IMG]

---

### Post by svref on 2014-11-12
The grub I talk to at boot time is a different version than the grub we're dinking around with at the prompt. That's one thing that makes me believe it's the /dev/sda4 OS that's running the show.

On /dev/sda1 (which is what we're trying to fix):
```

quad ~ apt-show-versions grub
grub:amd64/trusty 0.97-29ubuntu66 uptodate

```

---

### Post by svref on 2014-11-12
So it turns out there are multiple places GRUB can install to. Grub-install installs to a place that was being trumped by a more powerful grub-install in the past. "grub-install /dev/sda" seems to have trumped that trump. :D

---

### Post by Bashing-om on 2014-11-12
svref; Morning to ya;

OK, there can be but 1 grub that controls all the boot process - to choose what gets booted. We want the operating system that is installed to sda1 to be that primary operating system.

I find this:
> 
quad ~ cat /boot/grub/grub.cfg
cat: /boot/grub/grub.cfg: No such file or directory

very disconcerting, and we are going to direct our attention to making up this file.
Before we make it up we will get rid of all those old no-longer-needed kernels.

Need to know where we stand now in respect to which operating system grub is booting as that primary.
Did this change it:
> 
"grub-install /dev/sda" seems to have trumped that trump. 

did you install grub to 'sda' FROM the sda1 install ?

Let's look from a different perspective and see what is:
Boot the liveDVD -> "try ubuntu " mode -> terminal:
Post back the outputs of terminal commands:
```

sudo mkdir /mnt/work
sudo mount /dev/sda1 /mnt/work
ls -al /mnt/work/boot
ls -al /mnt/work/boot/grub

```
Once this is done, back out of manual 'mount' gracefully:
```

sudo umount /mnt/work

```
Clean things up, install what is required, and build the required file(s). I can see a CHange Root coming on .

[INDENT][INDENT]no step for a stepper
[/INDENT][/INDENT]

---

### Post by Elfy on 2014-11-12
If post 1 is right and the image is right.

The reason the kernel is not correct could well be that Mint has control of grub, and 14.04 has been installed after Mint.

The kernels showing would match those for a 12.04 install - which is what shows on the grub image.

Mint
12.04 kernels
11.10 kernels

How about booting Mint as that appears to have control and running 

```
sudo update-grub
```

---

### Post by svref on 2014-11-18
Thanks everyone!

Elfy seems right about how the Grub on the Mint partition was driving stuff.

On Bashing-Om's advice, the old kernel versions have been removed. I've run "grub-install /dev/sda" from sda1 (desired Ubuntu), and this has worked.

The only remaining head-scratcher is why the file /boot/grub/grub.cfg does not exist, and why it's needed. Is it possible that it's only a grub 2 thing?

---

### Post by Bashing-om on 2014-11-18
svref; Hey hey :

Good things do happen:
> 
why the file /boot/grub/grub.cfg does not exist, and why it's needed. Is it possible that it's only a grub 2 thing?

deep subject, get your think'n cap on.
I can not say how Mint operates, I can only assume it is similar to ubuntu ( assume = makes and A** out of yoU and ME, careful )

One has to have some means to boot up the kernel, and grub.cfg is that crucial intermediater  in that process, between the boot code and the kernel.
This file is developed from several other scripts, and depending on how it is invoked is where that file gets written to. ( it is possible to direct manually where the grub.cfg file is written out to. )

As you are now booting from 'sda1' I bet if ya look now in /boot/grub/ that you will find the file 'grub.cfg' that now controls the boot process.

Now here is the kicker, with multi-booting - more than 1 linux installed - The operating system that last updated it's kernel becomes the primary operating system unless one takes measures to prevent this. And yeah, grub must be re-installed in the desired primary to re-establish this supremacy .There are several ways to get around this aggravation.
Some like managing grub by making up their own boot stanza that gets written to grub.cfg; see:
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
which I whole heartedly endorse.
Else; one can (ubuntu) turn off 30_os-prober  such that other operating system's boot code is not added to this the primary booting system; or vice-versa. In that arrangement, there must be boot code installed to the hard drive (sdb ? sdc ? ) containing the other operating system - enabling to boot it with a change in bios' boot order. 

I do multi-boot and for my purposes I turn off 30_os-prober in all the other systems, such that then my primary picks up all the other systems, and with 30_os-prober turned off in the secondaty systems, they are not effected by kernel changes in the other systems. I make it a practice, however, when any kernel is updated to "sudo update-grub" in my primary, such that my primary is always aware of what is. 

A lot depends on your understanding the operating system, and what you require of it. Make it do what you want it to do.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]many paths to an end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

