---
title: "Grub Error 15: File not found"
date: 2010-11-02
forum: Installation &amp; Upgrades
---

### Post by celub on 2010-11-02
Hi All, thanks for vewing my post. Appreciate Ubuntu created by lot of people working for free so appreciate any help you can spare.

Have a Dell Inspiron 4100 laptop. 1GB RAM and 1 Ghz processor.
Has a working install of Oracle Enterprise Linux 5.4
OEL uses Grub version 0.97
My OEL install works well and I do not want to make any changes to it such as upogarding GRUB to a later version etc.

I have installed Xubuntu mini and this completed without a problem.

I have a single hard drive.

I went into OEL and mounted the Xubuntu root drive so I could see the /boot/grub/menu.lst file.

I copied the entries for the main xbuntu kernel etc and pasted them into my OEL grub.conf.

title           Ubuntu 10.10, kernel 2.6.35-22-generic
uuid            d6ed555c-54a3-4639-af25-3582c60624ad
kernel          /boot/vmlinuz-2.6.35-22-generic root=UUID=d6ed555c-54a3-4639-af25-3582c60624ad ro quiet splash
initrd          /boot/initrd.img-2.6.35-22-generic
quiet

Rebooted to test this appeared which it did and then selected the Ubuntu entry.

Got the error:

Error 15: File not found

Went back to OEL and edited the grub.conf for OEL so it did not use the uuid and also added a line to specify the root device. I think ubuntu uses Grub 2. I am using grub 0.97. I am no Grub expert and tried a few suggestions on the internet etc.

title           Ubuntu 10.10, kernel 2.6.35-22-generic
root (hd0,0)
# uuid            d6ed555c-54a3-4639-af25-3582c60624ad
kernel          /boot/vmlinuz-2.6.35-22-generic root=UUID=d6ed555c-54a3-4639-af25-3582c60624ad ro quiet splash
initrd          /boot/initrd.img-2.6.35-22-generic
quiet

Still no luck so tried pointing the kernel line to /dev/hda3 which is the root partition for Xubuntu install. 

title           Ubuntu 10.10, kernel 2.6.35-22-generic
root (hd0,0)
# uuid            d6ed555c-54a3-4639-af25-3582c60624ad
#kernel          /boot/vmlinuz-2.6.35-22-generic root=UUID=d6ed555c-54a3-4639-af25-3582c60624ad ro quiet splash
kernel          /boot/vmlinuz-2.6.35-22-generic root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.35-22-generic
quiet

Still no luck so highlighted the OEL grub entry and went into grub.

Entered:

find /boot/grub/menu.lst

and this too returned the same Error 15: File not Found but this works ok.

I tried with the OEL vmlinuz file and it found this and reported it on:

(hd0,0)

Thinking that it must know where the grub is as well it is reading entries from it, I rebooted choose Ubuntu again, got the error, went to grub by typing c and tried:

find /boot/vmlinuz-2.6.35-22-generic

Again Error 15: File not found

This must be something simple. I checked the Ubuntu /boot/grub/device.map file for Ubuntu and this had the entry:

/dev/sda

which does not exist on my system as my main device is

/dev/hda

I changed this and still the same.

Now I don't normally do a dual boot system so not very familiar with Grub and sure this is something very simple, but does anyone know how I manually correct this. Do not want to use a liveCD to do so as I am not 100% confident that it will not affect my OEL install.

And doing manually means you understand what has happened etc.

Looking again at my grub.conf and the OEL entry I could see that for OEL it points the kernel to /vmlinuz... and not /boot/vmlinuz...as with ubuntu. 

Changed entry for ubuntu and tested at command line in grub but no luck.

Have looked at grub doco but have not had any success.

Appreciate any help. 

I am doing this so someone else can borrow this laptop for internet use for a few weeks and OEL is not very user friendly and also want to protect my install.

Cheers Cel

---

### Post by celub on 2010-11-02
Update - not yet fixed:

Tired again and got the usual error.

Went into grub hitting c key at grub menu.

root (hd0,0)

Then:

kernel /(hit tab)

This listed all the files in the OEL /boot/grub directory which I would expect.
Then:

root (hd0,2) which is the partition I installed ubuntu onto. 

This returned saying it was 'Filesystem type ext2fs, partition type 0x83' which is the same reply as when doing

root (hd0,0) which is for OEL

Then:

kernel /(hit tab)

Error 2: Bad file or directory type

Tried various other things like

kernel /boot(hit tab) etc etc and nothing worked.

So it cannot see the files. Is there a way using grub to get some more diag information?

So looks like I have a fundamental problem somewhere but I just don't know dual booting and grub enough to fix. 

Have been working on this install since early yesterday and would really appreciate some help as need to crack on and just get this working. Have spent a lot of time on internet reading up on grub etc.

Will Ubuntu work with grub v 0.97?

I do not want to update my OEL install to use grub 2 etc as it works and I do not want to risk affecting that the moment.

I bet this is something simple, it normally is.

Cheers Cel

---

### Post by celub on 2010-11-02
Update: Not fixed

Thought I would try the rescue option from the original CD.

Booted, choose the rescue option etc. When it came to entering a device to use as the root file system it lists them as:

/dev/sda1
/dev/sda2
/dev/sda3
/dev/sda4
/dev/VolGroup01/LogVol00

Now the last one is my OEL install. What is odd is that the others are listed as sda. They should be hda! e.g.

/dev/hda3

which is where Xubuntu is installed. Why is this? I do not want to proceed here as this does not look right.

Does anyone know a link to 10.10 doco on rescue disk for xubuntu mini?

Thanks for viewing my post.

Cheers Cel

---

### Post by oldfred on 2010-11-02
Do not OEL, but lets confirm where everything is installed, you can run from the liveCD or from most working linux installs:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by celub on 2010-11-02
Hi OF thank you very much for looking at my post. 

Since my last update I gave in, and tried lubuntu which installed but had same issue and now installing Xubuntu 10.10 again. I have tried this before the mini and it always hung at scanning disks but had got past this point this time. Not sure how but it has so lets see what happens this time.

I wish I had not done this now as someone like yourself would have had a look at my grub set-up etc.

To be honest I strongly think the same thing is going to happen again, so once I get to the point of booting I will select Xubuntu and if getting the error will run the script which I have downloaded to OEL before running this current install.

I have read that other OEL users have got this working but have not been able to see their grub set-up etc.

I will update my post as soon as get to selecting the OS at boot time and have the result. Install now installing files so I suspect will be another 40 minutes or so.

Are you aware of any other people who have OEL 5.4 installed first and are trying to install 10.10? 

Thanks again, much appreciated

Cheers Cel

---

### Post by celub on 2010-11-02
Sorry OP made an error in the above. 

I am installing Xubuntu the alternate iso which is why it did not hang. It was the Ubuntu Desktop 10.10 which hung everytime at scanning disks.

This will complete to the end and I will have the same set-up as when I made this post.

Cheers Cel

---

### Post by oldfred on 2010-11-02
Before grub2, I chainbooted grub legacy for all my installs from a grub partition. Old grub installs to a partition easily and can also be chainbooted if necessary. But grub2's osprober is very good at finding other systems and configuring a boot stanza.

Have not tried Xubuntu. Sometimes a version does not have exactly the same apps and works slightly differently.

Usually we can parse the grub menu.lst and grub2 grub.cfg files and work something out.

---

### Post by celub on 2010-11-02
Hi OF, here are the results.

Just to confirm. I have re-installed Xubuntu (XB) using the alternate iso.

When installing I choose to use the old version of GRUB and not GRUB 2 when given the choice to do so.

I also choose to install grub in /dev/sda3 when prompted to choose a location. (well /dev/hda3 - XB seems to refer to sda instead hda). I wonder if this is WRONG and I should have installed elsewhere.

I modified by OEL grub.conf file from within OEL to include the new values from the menu.lst of XB.

When choosing XB at the boot menu I get:

Error 15: File not found

I then set root (hd0,2) the parition on which XB installed - /dev/hda3.

It then gave me Error 2: Bad file or directory type

Pressing c to get to grub command line I entered:

geometry (hd0, and then hit tab. This does return a list of the 4 partitions number 0 to 3.

It is as if it cannot see the files from XB.

Here is the output. Appreciate any help or suggestions. Will keep an eye on post for updates while I look on the internet again.

Thanks OF

Cel

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/hda and looks at sector 30785 on 
    boot drive #1 for the stage2 file. A stage2 file is at this location on 
    /dev/hda. Stage2 looks on partition #1 for /grub/grub.conf.

hda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

hda2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

hda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of hda3 and 
                       looks at sector 42580656 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/hda. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

VolGroup01-LogVol00: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Enterprise Linux Enterprise 
                       Linux Server release 5.4 (Carthage) Kernel on an
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: hda ___________________ _____________________________________________________

Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/hda1    *             63       208,844       208,782  83 Linux
/dev/hda2             208,845    33,977,474    33,768,630  83 Linux
/dev/hda3          33,978,368    49,602,559    15,624,192  83 Linux
/dev/hda4          49,602,560    51,556,351     1,953,792  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/hda1        6af724fd-5076-415f-af03-3412c5ff0a34   ext3       /boot                         
/dev/hda3        27beb052-7f0d-4774-8163-aa3458b9bf62   ext3       xubuntu                       
/dev/hda4        77794764-f900-4d95-907c-183d2a07fc5a   swap                                     
/dev/mapper/VolGroup01-LogVol00 6d9140cc-fc09-480d-90a1-3eb89bfa0cfd   ext3                                     
/dev/VolGroup01/LogVol00 6d9140cc-fc09-480d-90a1-3eb89bfa0cfd   ext3                                     

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
VolGroup01-LogVol00

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/mapper/VolGroup01-LogVol00 /                        ext3       (rw)
/dev/hda1        /boot                    ext3       (rw)


============================= hda1/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,0)
#          kernel /vmlinuz-version ro root=/dev/VolGroup01/LogVol00
#          initrd /initrd-version.img
#boot=/dev/hda
default=0
timeout=180
splashimage=(hd0,0)/grub/splash.xpm.gz
# hiddenmenu
title Enterprise Linux (2.6.18-164.el5)
    root (hd0,0)
    kernel /vmlinuz-2.6.18-164.el5 ro root=/dev/VolGroup01/LogVol00 rhgb quiet
    initrd /initrd-2.6.18-164.el5.img

title           Ubuntu 10.10, kernel 2.6.35-22-generic
uuid            27beb052-7f0d-4774-8163-aa3458b9bf62
kernel          /boot/vmlinuz-2.6.35-22-generic root=UUID=27beb052-7f0d-4774-8163-aa3458b9bf62 ro noapic quiet splash
initrd          /boot/initrd.img-2.6.35-22-generic
quiet

title           Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid            27beb052-7f0d-4774-8163-aa3458b9bf62
kernel          /boot/vmlinuz-2.6.35-22-generic root=UUID=27beb052-7f0d-4774-8163-aa3458b9bf62 ro noapic  single
initrd          /boot/initrd.img-2.6.35-22-generic

title           Ubuntu 10.10, memtest86+
uuid            27beb052-7f0d-4774-8163-aa3458b9bf62
kernel          /boot/memtest86+.bin
quiet


=================== hda1: Location of files loaded by Grub: ===================


    .0GB: grub/grub.conf
    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd-2.6.18-164.el5.img
    .0GB: vmlinuz-2.6.18-164.el5

=========================== hda3/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=27beb052-7f0d-4774-8163-aa3458b9bf62 ro noapic

## default grub root device
## e.g. groot=(hd0,0)
# groot=27beb052-7f0d-4774-8163-aa3458b9bf62

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 10.10, kernel 2.6.35-22-generic
uuid        27beb052-7f0d-4774-8163-aa3458b9bf62
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=27beb052-7f0d-4774-8163-aa3458b9bf62 ro noapic quiet splash 
initrd        /boot/initrd.img-2.6.35-22-generic
quiet

title        Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid        27beb052-7f0d-4774-8163-aa3458b9bf62
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=27beb052-7f0d-4774-8163-aa3458b9bf62 ro noapic  single
initrd        /boot/initrd.img-2.6.35-22-generic

title        Ubuntu 10.10, memtest86+
uuid        27beb052-7f0d-4774-8163-aa3458b9bf62
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== hda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=27beb052-7f0d-4774-8163-aa3458b9bf62 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=77794764-f900-4d95-907c-183d2a07fc5a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== hda3: Location of files loaded by Grub: ===================


  21.7GB: boot/grub/menu.lst
  21.8GB: boot/grub/stage2
  21.8GB: boot/initrd.img-2.6.35-22-generic
  21.7GB: boot/vmlinuz-2.6.35-22-generic
  21.8GB: initrd.img
  21.7GB: vmlinuz

======================== VolGroup01-LogVol00/etc/fstab: ========================

/dev/VolGroup01/LogVol00 /                       ext3    defaults        1 1
LABEL=/boot             /boot                   ext3    defaults        1 2
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
/dev/VolGroup01/LogVol01 swap                    swap    defaults        0 0
=======Devices which don't seem to have a corresponding hard drive==============

hdc 
=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file


```

(I just edited this as did not realise if run boot script more than once it amends a number to end of filename etc and pasted wrong one after ftp'ing it to my pc from linux)

---

### Post by oldfred on 2010-11-02
Some things to try.

Ubuntu is trying to use UUIDs but old grub often had just root

title           Ubuntu 10.10, kernel 2.6.35-22-generic
[COLOR=Red]root           (hd0,2)[/COLOR]
kernel          /boot/vmlinuz-2.6.35-22-generic root=UUID=27beb052-7f0d-4774-8163-aa3458b9bf62 ro noapic quiet splash
initrd          /boot/initrd.img-2.6.35-22-generic
quiet

Or a chain boot if you have installed grub to sda3 or hda3.

title      Xubuntu @ hda3
root        (hd0,2)
chainloader +1

Or boot the partition, not sure if hda3 or sda3:

title    Most Current Xubuntu on hda3
root    (hd0,2)
kernel   /vmlinuz root=/dev/hda3 ro quiet splash
initrd  /initrd.img

---

### Post by celub on 2010-11-02
OF what can I say: swearing outloud to myself. Thank you.

I did the usual after selecting Xubuntu and went to the grub prompt.

I had already tried your first suggestion with no luck.

On your second:

"Or a chain boot if you have installed grub to sda3 or hda3.

title      Xubuntu @ hda3
root        (hd0,2)
chainloader +1"

At the grub prompt I entered:

root (hd0,2)

then

chainloader +1

then

boot

and the boot menu for the 3 XB options appeared (without OEL, so using the XB grub I guess). Select the normal XB and

.... crikey it started up. 

So took 2 minutes from reading your reply and getting to the desktop.

I will  now edit my OEL grub and see what happens as ideally I would like for the system to go straight into XB if this is possible when I lend my laptop to my neighbour for a few weeks to use. When I have it back I will make the OEL visible again.

You know I have worked with UNIX for over 15 years. Cannot remember the first version but I do remember using TCP/IP to run an expensive application across a network where we paid a lot of money to get a TCP/IP stack from a Company called Wollogong I think it was. Sure it was for Vax/OpenVMS. Then ones I hardly remember like SCO Unix , then HP-UX, Solaris, AIX, OS X, HP Compaq Tru, and a few Linux variants and this had me confused. I read too many things on the internet and should have looked at the basics on booting up. I have not had many problems booting and never done dual as nearly always dedicated servers. Not a fan of VM Ware etc although have used it myself at times.

Well in last 2 days I have installed and tried a few times:

Ubuntu Desktop - laptop crawled so canned it
Xubuntu Desktop - had issue with scanning disks stuck at 47% in install - so canned it
Xubuntu alternate - worked ok but this issue so canned it
Lubuntu - similar issue to this I think. I could not boot it with OEL grub
Back to Xubuntu alternate/ mini ( I am loosing track)

Embarassing really to be honest.

Very glad I have been able to boot it up, something simple too as always. But only if you know of course.

Thanks again. I need to go back to do some basics I think. (-:

OF I will make some changes to OEL grub to see if I can get boot straight into Xubuntu and then come back and update the post.

Cheers Cel

---

### Post by oldfred on 2010-11-02
I actually expect all three versions to work and at least in some circumstances they would.

I thought you might just paste all three into your menu and then try booting 3 times.:)

If you were able to manually boot the second version, it definitely should work in the menu.

---

### Post by celub on 2010-11-03
Hi OF I did not try the first again as it just gave the errors I had before when I did it at the grub command prompt.

I edited my grub.conf on OEL and included the 2 other entries.

The 2nd one worked as said before.

The 3rd gave the same error as the first.

It just cannot see the files and gives the Error 2 about bad file or directory.

If I set root (hd0,2) and then enter kernel /(then hit tab) it finds nothing and does not give me the list of files I get if I did the same thing for OEL.

I think that something is working a bit differently with OEL which is basically RH.

Here is the output from the boot script again for reference.

I have been reading a few different posts on the internet about people having an issue with RH/OEL when installing a second OS afterwards for dual boot etc. It seems better to install the other OS first and then do OEL/RH. I don't think this is necessarily to do with the version of Grub being a later one that 0.97 but something else.

For example see this:

[http://blog.katharsys.com/?p=1128](http://blog.katharsys.com/?p=1128)

Although this is about having 2 physical disks with separate OS on each, which in a way should be even easier, katharsys was not able to access the Mythbuntu vmlinuz when using OEL grub. The same issue as I have had until using chainloader. He/she sets root to the correct disk/partition etc but no luck.

There are a lot of people like me who use OEL for Oracle database and Oracle Applications. I have a few laptops with it on but with only OEL on until now.

I think this is something to do with OEL/RH and will have another look, but now need to get my neighbours t-mobile ZTE M626 USB modem up and running so they can use the internet.

Thanks very much again for viewing my post and for you help. Good that this is now working.

I will leave this open for a few days so I can have look at OEL/RH a bit more to see if I can find out what is the problem and will then update post and close as solved.

Cheers Cel


```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/hda and looks at sector 30785 on 
    boot drive #1 for the stage2 file. A stage2 file is at this location on 
    /dev/hda. Stage2 looks on partition #1 for /grub/grub.conf.

hda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

hda2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

hda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of hda3 and 
                       looks at sector 42580656 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/hda. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

VolGroup01-LogVol00: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Enterprise Linux Enterprise 
                       Linux Server release 5.4 (Carthage) Kernel on an
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: hda ___________________ _____________________________________________________

Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/hda1    *             63       208,844       208,782  83 Linux
/dev/hda2             208,845    33,977,474    33,768,630  83 Linux
/dev/hda3          33,978,368    49,602,559    15,624,192  83 Linux
/dev/hda4          49,602,560    51,556,351     1,953,792  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/hda1        6af724fd-5076-415f-af03-3412c5ff0a34   ext3       /boot                         
/dev/hda3        27beb052-7f0d-4774-8163-aa3458b9bf62   ext3       xubuntu                       
/dev/hda4        77794764-f900-4d95-907c-183d2a07fc5a   swap                                     
/dev/mapper/VolGroup01-LogVol00 6d9140cc-fc09-480d-90a1-3eb89bfa0cfd   ext3                                     
/dev/VolGroup01/LogVol00 6d9140cc-fc09-480d-90a1-3eb89bfa0cfd   ext3                                     

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
VolGroup01-LogVol00

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/mapper/VolGroup01-LogVol00 /                        ext3       (rw)
/dev/hda1        /boot                    ext3       (rw)


============================= hda1/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,0)
#          kernel /vmlinuz-version ro root=/dev/VolGroup01/LogVol00
#          initrd /initrd-version.img
#boot=/dev/hda
default=1
timeout=10
splashimage=(hd0,0)/grub/splash.xpm.gz
# hiddenmenu
title Enterprise Linux (2.6.18-164.el5)
    root (hd0,0)
    kernel /vmlinuz-2.6.18-164.el5 ro root=/dev/VolGroup01/LogVol00 rhgb quiet
    initrd /initrd-2.6.18-164.el5.img

title Xubuntu 10.10
root (hd0,2)
chainloader +1
# boot

title Xubuntu 10.10 /dev/hda3
root(hd0,2)
kernel /vmlinuz root=/dev/hda3
initrd /initrd.img



=================== hda1: Location of files loaded by Grub: ===================


    .0GB: grub/grub.conf
    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd-2.6.18-164.el5.img
    .0GB: vmlinuz-2.6.18-164.el5

=========================== hda3/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=27beb052-7f0d-4774-8163-aa3458b9bf62 ro noapic

## default grub root device
## e.g. groot=(hd0,0)
# groot=27beb052-7f0d-4774-8163-aa3458b9bf62

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 10.10, kernel 2.6.35-22-generic
uuid        27beb052-7f0d-4774-8163-aa3458b9bf62
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=27beb052-7f0d-4774-8163-aa3458b9bf62 ro noapic quiet splash 
initrd        /boot/initrd.img-2.6.35-22-generic
quiet

title        Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid        27beb052-7f0d-4774-8163-aa3458b9bf62
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=27beb052-7f0d-4774-8163-aa3458b9bf62 ro noapic  single
initrd        /boot/initrd.img-2.6.35-22-generic

title        Ubuntu 10.10, memtest86+
uuid        27beb052-7f0d-4774-8163-aa3458b9bf62
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== hda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=27beb052-7f0d-4774-8163-aa3458b9bf62 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=77794764-f900-4d95-907c-183d2a07fc5a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== hda3: Location of files loaded by Grub: ===================


  21.7GB: boot/grub/menu.lst
  21.8GB: boot/grub/stage2
  21.8GB: boot/initrd.img-2.6.35-22-generic
  21.7GB: boot/vmlinuz-2.6.35-22-generic
  21.8GB: initrd.img
  21.7GB: vmlinuz

======================== VolGroup01-LogVol00/etc/fstab: ========================

/dev/VolGroup01/LogVol00 /                       ext3    defaults        1 1
LABEL=/boot             /boot                   ext3    defaults        1 2
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
/dev/VolGroup01/LogVol01 swap                    swap    defaults        0 0
=======Devices which don't seem to have a corresponding hard drive==============

hdc 
=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file
```

---

### Post by oldfred on 2010-11-03
I do not know if this is the only issue, but you need a space between root &  (hd0,2):

title Xubuntu 10.10 /dev/hda3
[COLOR=Red]root(hd0,2)[/COLOR]
kernel /vmlinuz root=/dev/hda3
initrd /initrd.img

title Xubuntu 10.10 /dev/hda3
[COLOR=Red]root (hd0,2)[/COLOR]
kernel /vmlinuz root=/dev/hda3
initrd /initrd.img

Whenever old grub had issues, I liked to do the chainloading as that just thru the boot over the fence (transfered it) and then the other system could boot. 

The link you have had issues since they used ext4 and old grub does not use ext4 and will not boot it. Ubuntu modified its version of grub 0.97 to see ext4 with version 9.04 Jaunty. But grub legacy has not been maintained for years and each distribution of Linux used slightly different versions of grub 0.97. They could have just chainloaded to the MBR and made it work. I use grub2 to chainload to another drive's MBR, but drive numbering can be a subtle issue as the boot drive in BIOS is always (hd0). I prefer two drives as that can often add flexibility with two MBRs. And then you do not necessarily have to install a boot loader to the PBR, and chainload to it.

---

### Post by celub on 2010-11-04
Hi OF thanks again for your reply and explanation about the issue I referred to using ext4 etc.

I did correct the missing space between root and (hd0,2) but no luck am afraid.

As said before it just can't seem to see the drive because if I set root to (hd0,2) and then enter kernel / and then hit tab it comes back with error 2 which I guess now just means it cannot find the file or directory.

If I do a similar thing, setting root to (hd0,0) for OEL and repeat kernel / and then hit tab it does list the files in the correct directory.

It is actually listing them from /boot directory which contains:

[FONT=Courier New][SIZE=1]drwxr-xr-x  4 root root    1024 Jul 23 11:40 .
drwxr-xr-x 29 root root    4096 Nov  4 20:20 ..
-rw-r--r--  1 root root   68663 Sep  3  2009 config-2.6.18-164.el5
drwxr-xr-x  2 root root    1024 Nov  4 20:10 grub
-rw-------  1 root root 3227162 Jul 23 11:40 initrd-2.6.18-164.el5.img
drwx------  2 root root   12288 Jul 23 11:29 lost+found
-rw-r--r--  1 root root  107405 Sep  3  2009 symvers-2.6.18-164.el5.gz
-rw-r--r--  1 root root  954947 Sep  3  2009 System.map-2.6.18-164.el5
-rw-r--r--  1 root root 1855924 Sep  3  2009 vmlinuz-2.6.18-164.el5
-rw-r--r--  1 root root     158 Sep  3  2009 .vmlinuz-2.6.18-164.el5.hmac[/SIZE][/FONT]

It lists all of these files if I tab after kernel /

I will keep looking to see if I can find out why, but again thanks very much as my neighbour now has a working laptop to use for a few weeks.

Will have a look at chainloading to to make sure I understand it better.

Cel

---

