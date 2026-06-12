---
title: "How to install Ubuntu Server edition on HP ProLiant DL360 Server?"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by lwj888 on 2007-03-14
Hi, I have bought a new HP ProLiant DL360 Server, and i wanna install Ubuntu Server edition on it. But i don't know how to config SmartArray RAID controller and it seems to have a boot problem. 
Any suggestions?

---

### Post by InlawBiker on 2007-03-19
Here is a fix from a user on the Fedora forums:
[http://forums.fedoraforum.org/archive/index.php/t-100884.html](http://forums.fedoraforum.org/archive/index.php/t-100884.html)

WORKS

Just thought I would post this for future seekers.

PROBLEM FIXED !

Seems FC5 reads IRQ ACPI difference than FC4 and older. For Compaq using Smart Array 2 I had to do the following.

1 At the install boot prompt type in "linux noprobe noapic noapci" without the quotes. Can also be "linux rescue or linux text noprobe noapic noapc"

Once I did this I had to enter the drivers when asked to select drivers
YOU MUST SELECT DRIVERS IN THIS ORDER !

I selected :

1 Compaq smart/2 RAID Controller (cpqarray)
2 Symbios 53c896 (sym53c8xx)

The cpqarray then loads and finds drives. THEN the symbios driver loads and causes no problems. I think it is searching for SCSI tape drive devices. If it loads first it returns device not supported error and the cpqarray driver cannot locate SCSI drives.

I also learned from a HP friend that this works on all his various HP and Compaq units.

Hope this helps someone.

Mesu

---

### Post by cfgtech on 2007-03-30
Will this work also for a Proliant 8500 with the built in Array controller? I believe it's a 5i

---

### Post by InlawBiker on 2007-04-26
I managed to get 6.06.1 (LTS) server installed on the Compaq Proliant DL360 G2.  The process was a little different than for Fedora FC6.

For Ubuntu, the cpqarray module is never installed. I believe the symbios driver detects the Compaq array and so the system just assigns that driver.  Unfortunately it detects it but it doesn't work.

So to get around this follow these steps. 

1. Boot the install CD. At the splash screen hit [esc] to get the boot: prompt and enter: "expert" (no quotes) as the only option.

2. Do all the steps up to & including "Install the Base System"

3. After installing the Base System, hit Alt-F2 and enter the console.

4. type: echo "cpqarray" >>/target/etc/mkinitramfs/modules
* Earlier dists used: echo "cpqarray" >>/target/misc/mkinitramfs/modules
- check to see which one your system is trying to use.

5. Exit the console. Press Alt+F1 to return to the install.

6. Continue the installation steps as normal.

Some good resources for this machine:
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/26632](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/26632)
[http://www.mcnabbs.org/andrew/linux/proliant/](http://www.mcnabbs.org/andrew/linux/proliant/)

---

### Post by astra2000 on 2007-05-28
hello ppl, I have a proliant DL360 and i'm tring to install the ubuntu 7.04 server edition.

I go trying install the ubuntu now :)

---

### Post by astra2000 on 2007-05-28
:(

I can't install this :( 

look..... 
[IMG]http://xs215.xs.to/xs215/07221/erro.jpg[/IMG]
[IMG]http://xs215.xs.to/xs215/07221/erro2.jpg[/IMG]
[IMG]http://xs215.xs.to/xs215/07221/erro3.jpg[/IMG]
[IMG]http://xs215.xs.to/xs215/07221/erro4.jpg[/IMG]
[IMG]http://xs215.xs.to/xs215/07221/erro5.jpg[/IMG]

---

### Post by astra2000 on 2007-05-30
nobody??? :(

---

### Post by jaydeel on 2007-06-01
Also see thread... Can't install Feisty Server on Compaq Proliant

Compaq Prolinea ML370 with Smart Array Controller
I am having this exact same issue, Unable to determine drive geometry/size. The raid disk shows up in the list, but the size shows 0G0.

/dev/ida/c0d0 exists, but no partitions are visible. ie c0d0p1, etc.

and fdisk /dev/ida/c0d0 isn't able to open the drive either.

Anyone else run up against this? is the option to downgrade to edgy?

I did a dmesg, and found errors identical to the post found below...

> For all 2.6 kernels before 2.6.18 (released Sep 20, 2006), there was a problem with the RAID driver in Linux. The error messages look like: "cpqarray: Finding drives on ida0", "cpqarray: ida0: idaSendPciCmd Timeout out, No command List address returned.", "cpqarray: error sending ID Controller", etc. It turns out that the RAID device would be taken by another driver (sym53c8xx) before the cpqarray driver could claim i
it.

What confuses me now is that the feisty server kernel is 2.6.20, shouldn't this be fixed?

---

### Post by Qrawler on 2007-06-04
Hi there I have the same problem, tough I'm going to try an fresh install tomorrow morning but than
with the smartstart cd(5.5) first to configure the disks and than try to install feisty
I dont know if anyone else tried this?

---

### Post by LabRat79 on 2007-06-04
Having the exact errors posted in the screens above on my DL360 with Feisty Server...

I tried the smartstart thing, didn't help. Post if it works for you, I'll try again.

---

### Post by jaydeel on 2007-06-06
I got it installed!! I’m doing this on Compaq Prolinea ML370, using feisty fawn. But the problems seem exactly similar so hopefully it will work for you guys.

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

### Post by astra2000 on 2007-06-06
I'm not a Super user, i dont have any idea how to make this :(

It is possibel that u send a Iso to the internet, than i can download ride away finished ???

tnks in advanced

---

### Post by lenny8088 on 2007-06-12
Been doing my best to follow along with these posts and get Fiesty installed on a ML570 Proliant. And most of it went well. 

But after install and reboot I get the error 
```
Booting from local disk...
isolinux: Disk error 01, AX = 0201, drive 80

Boot failed: press a key to retry 

```

- booting into the Rescue Mode gets me
```
ACPI: Looking for DST ... not found!
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
..MP-BIOS bug: 8254 time not connected to IO-APIC
...trying to set up timer (IRQ0) through the 8259A .. failed
...trying to set up timer as Virtual Wire IRQ... failed
...trying to set up timer as ExtINT IRQ...<7>APIC error on CPU0:00(08)
```

and then it hangs and I'm done.

Can anyone point me in the right direction? At a loss at where to begin with this.

---

### Post by jaydeel on 2007-06-19
> I got it installed!! I&#8217;m doing this on Compaq Prolinea ML370, using feisty fawn. But the problems seem exactly similar and seems to affect many compaq models that feature the compaq smart array controller. so hopefully it will work for you.

Since, the problem is a conflict between the compaq smart array and sym53c8xx module. I managed to get the install working by creating a custom install cd image, i modified the initrd.gz and removed the folder for the sym53c8xx_2 module. Recompiled the ISO image, and it's recognizing my compaq smart array RAID. 


I'm sure the same issue will occur using desktop, but im guessing the directions i posted above will also work to modify the cd for the desktop version. Well i hope it works out for you guys.. you will have to follow the second part of the instructions after you burn and install off the iso..

I put the iso image up... Ubuntu 7.04 Server for CompaqSmartArray.iso
[http://www.mininova.org/tor/757728]("http://www.mininova.org/tor/757728")

Follow these instructions after rebooting.. also be sure your /boot partition is at the beginning of the disk...

But, during the installation another kernel is installed and when you reboot you will see &#8220;cpqarray: error sending ID controller&#8221;

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

### Post by mikepeace on 2007-06-23
The download at this link fails:
[http://www.mininova.org/tor/757728](http://www.mininova.org/tor/757728)

Is there another download location ?

---

### Post by rayced on 2007-06-23
Hi,
i'm trying to install ubuntu server on an old compaq proliant with scsi array, to recover the data on those hds. Once installed correctly, is it possible to have the old geometry recognized? It is an old WinNt server.
Also i'm trying to do the steps described here in order to obtain a modified install-cd. On a mac os x machine, but when expanding the archive cpio fails on creating:

dev/console
dev/null

i've tryed with pax command instead of cpio but i've obtained the same error, also trying the command with admin priviliges trough sudo prefix.

Thanks in advance for any help, and sorry for my english.

---

### Post by PanzerMKZ on 2007-06-26
I also have this issue.  Can you post a link to the iso as the torrent does not seem to be shared by anyone.  Thanks for the help btw.  



Panzer

---

### Post by PanzerMKZ on 2007-06-26
ok so I have installed.  but then come to the part about using the rescue mode in the disc.  I issue command # mount /dev/lda/c0d0 and it says can't ffind /dev/lda/c0d0 in fstab.

and I don't see it when I cat /etc/fstab



Panzer

---

### Post by geekfish on 2007-06-26
I used Jaydeel's iso and method and installed 7.04 Server last night.  I switched to console after installing the base system and exited the modules  file to include cpqarray when it build the initrd image as part of the install.  I was able to download the iso overnight. 
I installed on a compaq proliant DL380 G1 machine.
Thanks jaydeel.

I had the same troubles that were captured in the screenshots on the previous page of this thread.

---

### Post by SSCUltima on 2007-07-09
I don't know if anyone is still watching over this thread, but I have re-made the ISO for Ubuntu Server 7.04 and have installed it to my Proliant DL360 at work. Now i do get that cpqarray ID error, but where it says in your instructions jaydeel that you have to do the command 
```
# echo "cpqarray" >> /etc/initramsfs-tools/modules
```
Do i have to create the directory first since its not there?

thanks in advance.

EDIT: I also don't have the command    update-initramfs -u

---

### Post by PanzerMKZ on 2007-07-13
I pulled another DL360 and made the ISO from the steps listed.  It is booting fine.  Thanks btw.  But now my dual 800 reads as a dual 800 but the one that has dual 1.2's only shows up as one cpu.  I am going to test the cpu.  But everything seems to be working great so far.


Panzer

---

### Post by PanzerMKZ on 2007-07-22
Ok I have a few extra of the dl360's.  Has anyone had any trouble going from a single proc DL360' to an SMP one?


Panzer

---

### Post by morenike on 2007-07-23
hello there,
This is for geekfisk or any ubuntu enthusiast on board.My name is morenike,i have been given this task at work:to instal linux on a compaq proliant ML 370 server.Workable instructions will be highly appreciated

---

### Post by jnorth on 2007-08-05
> **jaydeel said:**
> I got it installed!! I&#8217;m doing this on Compaq Prolinea ML370, using feisty fawn. But the problems seem exactly similar so hopefully it will work for you guys.

Since, the problem is a conflict between the compaq smart array and sym53c8xx module. I managed to get the install working by creating a custom install cd image, i modified the initrd.gz and removed the folder for the sym53c8xx_2 module. Recompiled the ISO image, and it's recognizing my compaq smart array RAID. 

Here are the steps I completed.

...



@jaydeel - 

Thanks - I'm on a old DL380 (g1 version) and this worked perfectly.

NOTE - Those having problems creating the iso, make sure you do this stuff sudo otherwise you'll have problems getting commands to run.  May be why it appears you don't have cpio, zcat, etc.

---

### Post by mcfly1204 on 2007-08-28
This is not the exact issue, but I feel it will be related.  I have installed Dapper on a ML570 g2 with one u320 scsi drive, and everything went fine.  I have 4 other u320 scsi drives that I would like to create a raid 5 array on for additional storage.  If I create the array from the bios, gParted and fdisk both acknowledge the array, but I cannot access the disk after mounting.  If I do not create the raid 5 array in the bios, fdisk and gparted will not see the individual disks at all.  Any thoughts on how I might resolve this.  I have notices the issues with cpqarray not being acknowledged in Ubuntu installs, but would this effect my issue?  If so, how might I go about fixing this?

---

### Post by t3hi3x on 2007-09-01
> **mcfly1204 said:**
> This is not the exact issue, but I feel it will be related.  I have installed Dapper on a ML570 g2 with one u320 scsi drive, and everything went fine.  I have 4 other u320 scsi drives that I would like to create a raid 5 array on for additional storage.  If I create the array from the bios, gParted and fdisk both acknowledge the array, but I cannot access the disk after mounting.  If I do not create the raid 5 array in the bios, fdisk and gparted will not see the individual disks at all.  Any thoughts on how I might resolve this.  I have notices the issues with cpqarray not being acknowledged in Ubuntu installs, but would this effect my issue?  If so, how might I go about fixing this?

It probably is a driver issue. Is it the same controller as the u320 with dapper installed on it?

---

### Post by t3hi3x on 2007-09-07
ok. i will host this for a little while. i'd like it if you guys would start some torrents or find some big ftp...dont download this unless its night time please:

[http://www.jbuflashradio.com/t3hi3x/ubuntufeistysmartarray.iso](http://www.jbuflashradio.com/t3hi3x/ubuntufeistysmartarray.iso)

this is a server edition of feisty fawn that will allow you to install it on the compaq smartarray scsi raid controllers.

kinda wish they would just fix the bug in the kernel

thanks!

EDIT::

Please read below. The iso is currently hosted on a 100 MB line now. it is much faster than my server

---

### Post by jasondbsl on 2007-09-10
I have tried several times to download the ISO but it keeps failing.  The other download on page 2 also fails :( Is anyone else having the same problem?

Many thanks,

Jason

---

### Post by t3hi3x on 2007-09-10
lol. the problem is my inet sux. someone is currently in the process of putting the iso on a 100 meg line. i will post the link once that is completed.

thanks,

---

### Post by Supertrue on 2007-09-12
Hi

the ISO is online under [http://skydisc.de/downloads/ubuntufeistysmartarray.iso](http://skydisc.de/downloads/ubuntufeistysmartarray.iso)

supertrue

---

### Post by bingnet on 2007-09-14
Hello, Thanks to whomever eventually seeded that torrent! I was please to find it completely downloaded one morning. The installation was successful, the array was discovered normally. However, on first boot from the logical drive presented by the array I see Grub loading countdown and then...

```

[0.377145] ACPI: Resource is not an IRQ entry
Loading, please wait...
[5.064073] cpqarray: error sending ID controller

```

Then nothing happens, the cursor just blinks indefinitely.

===CORRECTION===

Not indefinitely! A few minutes after I gave up waiting the following additional lines appeared, then the system really stopped doing anything further.

```

Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/3a548628-75da-41d1-a3bb-d88a873188c does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-In shell (ash)
...
(initramfs)


```

Thanks for any help. -Ken.

---

### Post by t3hi3x on 2007-09-15
There has to be something to do with your mount setup. It wouldnt begin to boot at all if it wasn't pulling the drivers. Do you have more than one harddrive going?

---

### Post by TechStan on 2007-09-18
Dose anybody have a good non torrent link to download this. I am a noob and the instruction to compile this is way over my head.  I have tried all the other links and have been unsuccessful in downloading the file. Thanks in advance for any help.

---

### Post by t3hi3x on 2007-09-18
> **Supertrue said:**
> Hi

the ISO is online under [http://skydisc.de/downloads/ubuntufeistysmartarray.iso](http://skydisc.de/downloads/ubuntufeistysmartarray.iso)

supertrue

it really wasn't that hard, it just took for ever to do so. this wonderfully nice person hosted this iso for me. make sure you all thank him

---

### Post by TechStan on 2007-09-18
It would not let me download it from that site. It locks up around 20 to 28 percent downloaded. I will try again.


Edit: OK it worked this time!!!   Thanks

---

### Post by t3hi3x on 2007-09-19
a word of advice when downloading iso: use a download manager. one that you can resume.

---

### Post by TechStan on 2007-09-19
That is sound advice and duly noted. Thanks again

---

### Post by zeroasterisk on 2007-09-25
I was not able to use the modified install CD because it failed integrity checks... Not sure if that was the CD or my drive acting strange... but anyway - in the process I was able to figure out a slightly different approach.

Before installing hit F6, and then F6 again - allowing you to choose "Expert Mode"

Go through the installation, but when it asks you what modules to install:

[LIST=1]
[*]Hit ALT+F2 to get to a shell
[*]type in the following to remove the "bad" modules from the ramdisk: 
```

rm -rf /lib/modules/2.6.20-15-generic/kernel/drivers/scsi/sym53*

```
[*]Hit ALT+F1 to get back to the install interface
[*]de-select all SCSI modules and anything with a "53" in the name.  (not sure how much of this is required, but it worked for me)
[*]carry on with the install... if it asks for module detection again, simply de-select the "53's"
[/LIST]



at any point, from the shell (ALT+F2), you can type in:

```

lsmod | grep sym53

```

if you've got the "sym53c8xx" module listed - you're out of luck.  
(Removing it with modprobe -r didn't work for me)

Good luck... don't know why this module is so hard to identify from the list of modules to install...

thanks,
-alan-

---

### Post by TechStan on 2007-11-14
Dose anyone know if this problem was fixed in Gutsy 7.10?

---

### Post by jtodaro on 2007-11-17
i'm not entirely sure what version of Ubuntu you guys were trying to install, but I have an HP DL360 G3 and the install of 7.08 was flawless. Booted to cd without incident and installed easily. 7.10 upgrade didnt pose no issues either.

---

### Post by TechStan on 2007-11-17
> **jtodaro said:**
> i'm not entirely sure what version of Ubuntu you guys were trying to install, but I have an HP DL360 G3 and the install of 7.08 was flawless. Booted to cd without incident and installed easily. 7.10 upgrade didnt pose no issues either.


We were installing the server version.  My system is a G1 I think there is a difference in the raid card used between our models. The problem is the drivers for the card.

---

### Post by crouton on 2007-11-19
I have a Proliant DL380 with a SMART 2/P card as well as the onboard SCSI RAID.  Removing the small onboard RAID chip solved the 'No drives found' for the onboard (as showcased [here]("http://ubuntuforums.org/showpost.php?p=2734955&postcount=6")), and I am able to continue installing onto the 2/P.  However, when I reboot, I get the 'System not found' error.  I'm thinking this is a BIOS boot-order issue, and am continuing to investigate (finding the appropriate SmartStart CD now...)

---

### Post by TechStan on 2007-11-19
you might want to start reading this post from the beginning.  You will get a lot of insight into this issue.

---

### Post by crouton on 2007-11-19
As I suspected, the onboard SCSI controller was First in boot order and was preventing the 2/P from booting.  SmartStart CD to get to the BIOS and problem solved.

(I did read the post from the beginning.)

---

### Post by t3hi3x on 2007-12-14
> **zeroasterisk said:**
> I was not able to use the modified install CD because it failed integrity checks...

it is not likely for it to pass the test. as it is a modified kernel. the check should be checking for things like that and it is set up to check the "default" disk.

---

### Post by alexeysa on 2007-12-15
Hello, At me the same problem, whether I can not find for it the decision who can help me:confused:

> **bingnet said:**
> Hello, Thanks to whomever eventually seeded that torrent! I was please to find it completely downloaded one morning. The installation was successful, the array was discovered normally. However, on first boot from the logical drive presented by the array I see Grub loading countdown and then...

```

[0.377145] ACPI: Resource is not an IRQ entry
Loading, please wait...
[5.064073] cpqarray: error sending ID controller

```

Then nothing happens, the cursor just blinks indefinitely.

===CORRECTION===

Not indefinitely! A few minutes after I gave up waiting the following additional lines appeared, then the system really stopped doing anything further.

```

Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/3a548628-75da-41d1-a3bb-d88a873188c does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-In shell (ash)
...
(initramfs)


```

Thanks for any help. -Ken.

---

### Post by t3hi3x on 2007-12-15
have you tried the iso that is hosted with updated kernel?

---

### Post by alexeysa on 2007-12-16
> **t3hi3x said:**
> have you tried the iso that is hosted with updated kernel?

yes, i'm download from this link :[http://skydisc.de/downloads/ubuntufeistysmartarray.iso](http://skydisc.de/downloads/ubuntufeistysmartarray.iso)

---

### Post by thekat on 2008-01-06
Not to top post.. but I did this for (7.10) Gutsy Gibbon Server..
and it worked without a hitch.. 

Thank you JayDeel for the hard work.. you saved us a bunch of time..

I have the custom iso and would like to share it if anyone wants it.. 

tk

> **jaydeel said:**
> I got it installed!! I&#8217;m doing this on Compaq Prolinea ML370, using feisty fawn. But the problems seem exactly similar so hopefully it will work for you guys.

Since, the problem is a conflict between the compaq smart array and sym53c8xx module. I managed to get the install working by creating a custom install cd image, i modified the initrd.gz and removed the folder for the sym53c8xx_2 module. Recompiled the ISO image, and it's recognizing my compaq smart array RAID. 

Here are the steps I completed.

To create the custom CD&#8230;..

Mount the install&#8230;

```
mount /dev/scd0 /cdrom
```

Copy the CD.

```
mkdir -p /opt/cd-image
cp -r /cdrom/* /opt/cd-image
cp &#8211;r /cdrom/.disk /opt/cd-image

```
Extract the initrd.gz from the cd image

```
mkdir extract
cd extract

zcat /opt/cd-image/install/initrd.gz | cpio -i 
```

Delete the modules in sym53c8xx_2 directory 

```
rm &#8211;rf ./extract/lib/modules/2.6.20-15-generic/kernel/drivers/scsi/sym53c8xx_2
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

But, during the installation another kernel is installed and when you reboot you will see &#8220;cpqarray: error sending ID controller&#8221;

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

### Post by thekat on 2008-01-10
I am guessing that no one needs this iso...?

No worries.. 

tk

---

### Post by ilko on 2008-01-11
I want this ISO file 
please, share for me !!!

THANKS
!!!

---

### Post by jaydeel on 2008-01-14
I recently had to install on this box again and wanted to use 7.10 (Gutsy) when I did... and thought about making the custom install cd, which should probably still work but I thought it was a lot of work... since it was a module conflict I wondered if I could just suppress loading the module somehow... 

Then i discovered a couple interesting kernel module parameters... that makes installing on this raid controller a breeze...  so.. upon booting press F6 to edit the kernel parameters and I added... this to the line... > sym53c8xx.blacklist=yes sym53c8xx_2.blacklist=yes

Detected the array and everything worked like a charm.. even copies over your blacklist settings to the new installation. Hopefully the need for a custom install cd should be obsolete.

---

### Post by citybird on 2008-01-15
> **jaydeel said:**
> I recently had to install on this box again and wanted to use 7.10 (Gutsy) when I did... and thought about making the custom install cd, which should probably still work but I thought it was a lot of work... since it was a module conflict I wondered if I could just suppress loading the module somehow... 

Then i discovered a couple interesting kernel module parameters... that makes installing on this raid controller a breeze...  so.. upon booting press F6 to edit the kernel parameters and I added... this to the line... 

Detected the array and everything worked like a charm.. even copies over your blacklist settings to the new installation. Hopefully the need for a custom install cd should be obsolete.

I am trying to install the same on a Proliant DL380 G4 with a smart array 6i controller.
It always hangs at booting from hard drive after the installation.
If the current try does not work i will be attempting again with your parameters.

---

### Post by citybird on 2008-01-15
tried your method and it failed at the beginning of the boot process with the following message:

```
Unknown boot parameter sym53c8xx.blacklist=yes ignoring
Unknown boot parameter sym53c8xx_2.blacklist=yes ignoring
```

then i tried it by pressing escape and at the boot: prompt typing 
```
install sym53c8xx.blacklist=yes sym53c8xx_2.blacklist=yes
```

and got the same message.

---

### Post by jaydeel on 2008-01-15
I got those same messages while booting, i dont think it's a message the kernel understands but the debian installer must watch out for kernel parameters sent to it and loads the appropriate modules after the kernel has been started... at any rate... i have no idea if this is how it actually works but thats how i explained off the error messages.

I did also see those messages, but setup continued on and recognized the raid. I think you might be having a problem as I have had with some kernels with buggy acpi support that can cause many systems to hang on boot... try adding another parameter in addition to your blacklist ones.. 

```
pci=noacpi acpi=off
```

to see if that doesn't do something causing the freezing after boot. thats my best guess... is that your seeing the errors about the kernel params the kernel moved on a few steps and then froze from acpi bugginess which doesnt usually produce a message.

 i did have a 5 series smart array controller on a compaq ML370, so our hardware is different... there are a couple other solutions.. creating the custom cd, or deleting the files from the ramdisk at boot time.. they are both outlined in the previous posts.

---

### Post by citybird on 2008-01-16
Thanks, I will try that after my current investigation into whether or not the problem is Grub installing at the wrong location.

I also have the option of booting from the SAN so I can try installing there before going back and trying your suggestion.

---

### Post by lundrog on 2008-01-31
I installed 7.10 server today on a DL380 G4 and G5 without any boot problems, but I can't figure out how to partition the additional raid 1 arrays I have added since.

---

### Post by thekat on 2008-02-10
> **ilko said:**
> I want this ISO file 
please, share for me !!!

THANKS
!!!
Sorry, haven't been on the forums in a while... 
I do have the iso.. but don't really have an ftp spot to put it..

Let me know..

tk

---

### Post by robisaks on 2008-04-13
you can use this same method to install the desktop version of ubuntu on ML370, but you have to use the text install cd.

---

### Post by stonehead on 2008-04-29
Has all these problems of not recognizing RAID been solved with the release of 8.04? I am planning to get a DL160 G5 and was told that only RedHat & SUSE were supported. :(

---

### Post by Ferret-Simpson on 2008-05-19
*shrugs* Worked "Out of the box" on my G1-360 (Ubuntu Server 8.04)

---

