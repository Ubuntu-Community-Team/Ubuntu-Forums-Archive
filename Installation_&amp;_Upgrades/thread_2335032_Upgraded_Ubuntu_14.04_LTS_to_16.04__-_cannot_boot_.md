---
title: "Upgraded Ubuntu 14.04 LTS to 16.04  - cannot boot - keeps cycling to logon screen"
date: 2016-08-24
forum: Installation &amp; Upgrades
---

### Post by msbooton on 2016-08-24
I upgraded last night using the regular Ubuntu upgrade app.. Install seemed to go fine but now when I try to logon Ubuntu seems to flash, then return to the logon screen. It's an endless logon loop.

I can dual boot to Windoze 7 just fine, but can no longer boot to Ubuntu past the logon screen. However I can boot to the console interface (ctrl+alt+F1) but I don't know what to do after I get to the DOS prompt. I'm running Grub 1.99. Could this be a grub problem? :confused:

HP Pavillion dv6 - AMD64
Windoze 7
Ubuntu 14.045

---

### Post by Bashing-om on 2016-08-24
msbooton; Hello;

Many times what we see here is a broken proprietary graphic's driver.
To see if this is your situation, at the TTY1 console (ctl+alt+F1) log into the system with your credentials and post back the results of terminal commands:
```

sudo lshw -C display
lspci -k | grep -EA2 'VGA|3D'

```

[INDENT][INDENT]we see
[INDENT][INDENT][INDENT]what tale gets told
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by msbooton on 2016-08-25
Thanks Bashing-om:

sudo lshw -C display displayed;

description: VGA compatible controller
product: Core Processor Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 02
width: 64bits
clock: 33MHz
capabilities: msi pm vga.controller bus_master cap_list rom
configuration: driver i915 latency=0
resources: irq:43 memory: d0000000-d03fffff memory: c0000000-cfffffff ioport:5050(size = 8)

lspci -k | grep -EA2 'VGA|3D' displayed;

VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
subsystem: Hewlett-Packard Company Device 3658
kernel driver in use: i915

Thanks for your help!

---

### Post by Bashing-om on 2016-08-25
msbooton; Wellll ..

Graphic's is Intel, and generally Intel just works - the i915 driver is loaded, and there is no other card at play here. The kernel takes care of it .
At this point let us "assume" it is not a graphic's driver issue .
We now look at this as an authorization issue in that "you" do not have the authority to access your desktop.
Let's check:
```

ls -al .Xauthority
ls -al .ICEauthority

```
where "you" are the owner and grouped to the files :

[INDENT][INDENT]check the simple things 1st
[/INDENT][/INDENT]

---

### Post by msbooton on 2016-08-27
Thanks for your help Bashing-om,

ls -al .Xauthority produces:
--rw---- 1 michael 80 Aug 23 16:37 .Xauthority

ls -al .ICEauthority
--rw---- 1 michael michael 85096 Aug 23 16:37 .ICEauthority

Thanks

---

### Post by Bashing-om on 2016-08-27
msbooton; Hummm ..

So much for that idea, you do have the authority to access your desktop .

Let's revert to your original thought that grub is at fault here.
Show:
```

uname -r
cat /etc/issue
lsb_release -a
grub-install --version

```
make sure all our ducks are in a row and next we start reading the log files to find any hints .

[INDENT][INDENT]gotta be a cause
[/INDENT][/INDENT]

---

### Post by msbooton on 2016-08-28
Bashing-om;

uname -r  =  3.2.0-107-generic

cat /etc/issue  =  Ubuntu 14.04.5 LTS \n\l

lsb_release -a  =[INDENT]No LSB modules are available
Distributer ID:Ubuntu 14.04.5 LTS
Release:14.04
Codename:trusty
[/INDENT]

grub-install  --version  =  grub-install (GRUB) 1.99-21ubuntu3.19

A few questions;

[LIST=1]
[*]I upgraded to 16.04 (that's what sent me to Ubuntu hell). Why does "cat /etc/issue" tell me I'm still running 14.04.5 LTS? 
[*]I am the only user on this computer. Why wouldn't I have read, write, and execute privileges? 
[/LIST]

Thanks for your help!

---

### Post by Bashing-om on 2016-08-28
msbooton; Yuk !

Look. the problem goes deeper :
The kernel for 14.04 should be:
```

sysop@1404mini:~$ uname -r
3.13.0-93-generic
sysop@1404mini:~$

```
which will be the main focus of our current effort . To find out why you are still on " 3.2.0-107-generic " .
Let's get this system - trusty - booting the correct kernel, then we get it updated and then if you desire we release-upgrade to 16.04.

Start this process of discovery with what kernels are installed. Post back - between code tags, please - the output of terminal commands:
```

dpkg -l | grep linux-
ls -al /boot

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)


Edit: 
> 
I am the only user on this computer. Why wouldn't I have read, write, and execute privileges?

Becuase "You" are not the only user, or even the primary in any linux system. "you" run under the auspice of root . As the 1st created user under 'root' you have the ability to elevate your system privileges to that of 'root' by involing "sudo" . This measure is the primary reason linux enjoys the security that it does . Only root can access the system files to  make any change.
[INDENT][INDENT]roll up our sleeves
[INDENT][INDENT][INDENT][INDENT]and go to work
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by msbooton on 2016-09-04
Thanks for your help Bashing-om. Sorry for the delay but ... life happens.

I will try to explain the output from the code you asked for. I have omitted the repetitive lines. (**x**) represents a changing number. 
```
dpkg -i | grep linux-
ii linux-image-3.2.0-95-generic   3.2.0-95.135    amd64    Linux kernel image for version 3.2.0 on 64 bit x86 smp
ii linux-image-generic    3.2.0.107.123    amd64    Generic Linux kernel-image
ii linux-libc-dev:amd64    Linux kernel foe development
ii linux-second base    1.0.25+dsfg-0ubuntu1.1    all    base package for ALSA and OSS soundsystem
ii syslinux-common    2:4.05+dsfg-2    all    collection of boot loaders (common files)
ii Syslinux-lagacy      2:3.63+dsfg-2ubuntu5    amd64    Bootloader fpr Linux/i386 using MS-DOS floppies
ii linux-firmware    1.79.18    all    firmware for Linux kernel drivers 
ii linux-generic    3.2.0.107.123    amd64    Complete generic Linux kernel
ii linux-headers-3.2.0-(**x**)-generic    3.2.0-(**x**)
ii linux-image-3.2.0-(**x**)-generic    3.2.0-(**x**)
```
```
ls -al /boot
abi-3.2.0-(**x**)-generic
config-3.2.0-(**x**)-generic
grub
initrd.img-3.2.0-(**x**)-generic
memtest86+.bin
memtest86+-multiboot.bin
system.map-3.2.0-(**x**)-generic
vmlinuz-3.2.0-(**x**)-generic
```

I sure hope some of this info helps. I didn't display the entire output of the code because I don't know how to direct the output to a flash drive to copy/paste the output into the forum which I'm using Windoze to access.

Msbooton

---

### Post by Bashing-om on 2016-09-04
msbooton; Ouch !

the 3.2 series kernels are for 12.04 (precise) !
Begs the question as to why the 14.04 kernels are not installed .. not to even think about why the 16.04 kernels did not get installed.

OK, let's try this to get a more detailed report:
```

cat /etc/issue
lsb_release -a
uname -r
dpkg -l | grep linux-image- | nc termbin.com 9999
apt list linux* | grep installed | nc termbin.com 9999

```
the result of termbin is  a URL back in terminal, pass these links back here and we can access the generated files at the pastebin site.

We then see if we can finger out what is not taking place . Why you remain on the 12.04 series kernels when you say it is 14.04 installed .


[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by msbooton on 2016-09-12
Hi Bashing-om;

```
cat /etc/issue
Ubuntu 14.04.5 LTS \n \l
```

```
lsb_release -a
No LSB modules are available.
Distributer ID: Ubuntu
Description: Ubuntu 14.04.5 LTS
```

```
uname -r
3.2.0-107-generic
```

```
dpkg -l |grep linux-image-| nc termbin.com 9999
http://termbin.com/yaos
```

```
apt list linux* |grep installed | nc termbin.com 9999
WARNING:apt does not have a stable CLI interface yet. Use with caution in scripts
http://termbin.com/r2oj
```

Hope you can help[-o<

---

### Post by Bashing-om on 2016-09-12
msbooton; Humm ...

A lot of kernels installed ! AND all for the 12.04 precise release . 

Tell ya what, how 'bout we clean the system up - primarily removing these old kernels.
Then we try and install the 14.04 kernel.

For this I do need a bit more detailed information.
Pastebin:
```

dpkg -l | grep linux- | nc termbin.com 9999

```
which with the shortened version of the command will also show the related header files. I do want to make sure all matches when we go purging .

EDIT: nother thought too.
Let's also check the sources:
```

cat -n /etc/apt/sources.list | nc termbin.com 9999
tail -v -n +1 /etc/apt/sources.list.d/*  | nc termbin.com 9999

```


Reserve judgement 'til we
[INDENT][INDENT]get our ducks all in a row
[/INDENT][/INDENT]

---

### Post by msbooton on 2016-09-14
Bashing-om; I don't know how the kernals got dicked up. I installed from the Ubuntu site and I haven't used Ubuntu anywhere near its potential so I haven't installed many apps at all.:confused: Just Ubuntu updates.

```
dpkg -l | grep linux- | nc termbin.com 9999
http://termbin.com/q6k3
```

```
cat -n /etc/apt/sources.list | nc termbin.com 9999
http://termbin,com/qbl2
```

```
tail -v -n +1 /etc/apt/sources.list.d/* | nc termbin.com 9999
http://termbin.com/np4s
```

No judgement here. Ducks need to be in a row.
Thanks

---

### Post by Bashing-om on 2016-09-14
msbootonl Well ..

All the above looks in order . 
I have no clue why the trusty kernels are NOT installed and you remain on precise (12.04).

In any event, let's begin the clean up process, get the system cleaned up and on 14.04 kernels.
I like taking a gentle poke at things, see what bites if anything before going whole hog.
so:
what results:
```

sudo apt-get remove linux-image-3.2.0-23-generic
sudo apt-get remove linux-headers-3.2.0-23
sudo apt-get remove linux-headers-3.2.0-23-generic

```
If that goes well we will batch un-Install a bunch of old kernels next.

[INDENT][INDENT]roll up the sleeves and go to work
[/INDENT][/INDENT]

---

### Post by msbooton on 2016-09-15
Bashing-on; I think the cmds went well. Each piece of code produced the same output and they seem to list the same unmet dependencies.

```
sudo apt-get remove linux-image-3.2.0-23-generic
http://termbin.com/42ei
```

 ```
sudo apt-get remove linux-headers-3.2.0-23
http://termbin.com/kmhv
```

```
sudo apt-get remove linux-headers-3.2.0-23-generic
http://termbin.com/ujab
```

Thanks so much!

---

### Post by Bashing-om on 2016-09-15
msbooton; Yuk; Ouch; Oweeee !

As you can see we have a broken system . Now ask yourself if you have the time, and want to expend the effort to repair ??
I am all for repairing ... we will make advancements in the linux learning curve and it will not be an easy one .

As it is the end goal here to release upgrade to 16.04 - we must get 14.04 stable !. I highly suggest - as mysql is a factor - that you do read:
[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)
As we can look forward to reconfiguring the database . Not a fun thing to do . upstart to systemd -
As well we have 32 bit applications installed on this system .. might be a pain to work through them to satisfy the package manager .
At this point, if we are to fix, getting the package manager in a happy state is the 1st priority  so we can do the release-upgrade.
At this point you may want to give serious consideration to backing up your data and doing a clean fresh install . With good backup then it is but a matter of about 30 minutes to freshly install 16.04 .  There is a lot to be said for a clean fresh install and leave all the past garbage behind. There is a lot to be said about repairing-Keeping the system you have and advancing on the learning curve.

That call is yours !  Fixing could be a wild ride, but one we can enjoy .

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by msbooton on 2016-09-15
Bashing-om; I have an external hard drive that plugs into a USB port. How would I find out what drive letter Ubuntu assigns to the external drive from a terminal window? 

Would the copy cmd be something like:
```
cp -p -v /documents/*.* E:/documents
```

Would the above cmd copy sub directories and the contents?

Would I have to go to the ext. drive and make the "documents" directory or would the cp command make it?

Would I also have to backup my Firefox and Thunderbird data too? I assume so. I would have to find where those programs reside and look for their data I guess.

How would you suggest I do a backup from a terminal window?

Your help is invaluable but the mission sucks!

---

### Post by Bashing-om on 2016-09-15
msbooton; Well .

To be sure to identity that external drive;
Without the drive connected run terminal command:
```

sudo fdisk -lu

```
note the drive(s) seen;

Now plug in the external drive ( hot plugging allows this ! ) ;
what now results :
```

sudo fdisk -lu

```
Note the additional device.
Ok the external drive is identified .. for example 'sdc'
Now we need to know the partition on that 'sdc' device as shown from the 'fdfisk' output. What partition on 'sdc' ( as our example) to you want to copy to ?

Let's say there are a few partitions on the external drive that is identified as 'sdc' and we want to copy to the 2nd partition ,.. and perhaps some "backup" directory.
If there is not mount point already set up for this device, we do a number like this in terminal to make that attachment:
```

sudo mkdir /mnt/copy
sudo mount /dev/sdc2 /mnt/copy

```
Where ''copy" can be any name that you like .

Make sure that "you" own the files on this sdc device  and on the directory - if you are going to operate as "you" :

Let's assume on the sdc drive partition 2 there exist a directory " backup"; else create it  first .
then we can do something like:
```

sudo chown -R msbooton:msbooton /mnt/copy/backup

```
where msbooton; is the actual username you use on the system.

Now you are set to copy files from the install to the backup device/directory .

Do a number such as - for an example:
```

cp -R /home/msbooton /mnt/copy/backup

```
which will (R)ecursiviely copy all directories, sub-directories in your home directory and files to the external directory "backup" .

Now -ReMeMber - as we mounted that device, it is our responsibility to insure that it is unmounted when we are all done .
Failure to remove the mount can and will result in file system corruption at some level if you shut the system down with the file system (sdc) in use ( mounted) .
do:
```

sudo umount /dev/sdc2

```

Now I do prefer to do my copies in terminal ( 2 instances of a terminal open ) .. but many prefer to copy with the GUI file manager - nautilus. At some point you may find that the tool 'rysnc' is the handier tool for backup . BUT 'cp' will get the job done !
For the GUI ->
just open 2 instances of the file manager . one at the source .. and the other at the destination .. and drag and drop to you heart's content .

I do operate at the terminal level, my preference. If the above is unclear, or you have questions, by all means ask .. and I try and clear up my muddy waters .
-----------------------

Now, just because I suggest that a fresh clean install is the faster easier solution, does not mean we have to ! If ya want to expend the resources to fix .. I am more than willing to have at it .. but it will be a long hard bumpy road  to arrive at 16.04 .

[INDENT][INDENT]the terminal is your friend
[/INDENT][/INDENT]

---

