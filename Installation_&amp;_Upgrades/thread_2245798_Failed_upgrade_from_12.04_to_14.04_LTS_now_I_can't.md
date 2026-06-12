---
title: "Failed upgrade from 12.04 to 14.04 LTS now I can't boot"
date: 2014-09-26
forum: Installation &amp; Upgrades
---

### Post by tequiladave-n on 2014-09-26
First of all I would like to say that even though I have been using linux for a long time now I am still a newbie as I only use this computer to go on the internet, stream and download stuff. 

Today as I was working at home I decided to upgrade my system to 14.04, so I download the file and started the upgrade process. After maybe 2 hours I was still stuck on the installation of an item (in typical fashion I didn't make a not of this item) so I thought it had stopped or crashed (I know, probably I should've waited longer) and decided to do a hard restart and from that moment onwards I can't boot the computer.

It starts up, goes to the list of OS I want to start up with and I make my choice and it goes to the window with xubuntu on it but then just freezes and goes nowhere.

I tried many different OS from the list at start up and none work. I have tried to start in recovery mode but I don't really know what commands to use to try to fix it.

I considered downloading a fresh version of 14.04 from the Ubuntu site and then sticking it on a pen drive and re-start the computer and start the installation process but I have a few things on this machine I don't want to lose. Will it give me an option to upgrade only or will it format my hard drive and do a fresh install if I go down this route?

Please be gentle with your replies as I really don't know what I am doing here.

I should say I tried to run 

sudo apt-get -f install 

E:dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
[FONT=arial][/FONT][SIZE=4][/SIZE][SIZE=3][FONT=arial]
And got a reply back saying that [/FONT][/SIZE]'Processing was halted because there were too many errors'

Kind Regards

---

### Post by tequiladave-n on 2014-09-26
Update on my problem:

I have now been able, using the two commands above to get the computer to boot but when I log in it doesn't show me anything but the backdrop picture. No folders, no top and bottom bars or no shortcuts.

---

### Post by Bashing-om on 2014-09-26
tequiladave-n; Hi !

Did the upgrade complete ? Let's see what the state of the system is:
Do in terminal:
```

cat -n /etc/apt/sources.list

``` Does ALL lines reflect 'trusty' ? NOT precise ?

What 3rd party software was installed in 12.04, that is not supported in 14.04 ?
```

tail -v -n +1 /etc/apt/sources.list.d/*

```

Sources all look good, and there are no conflicts ( including proprietary graphics drivers ) with 3rd party software.

Then clean up and update the system:
The '#' is not to be entered as they denote a comment on my part for your edification and not to the system .
```

#houseclean
sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get autoremove
sudo apt-get clean
#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required/and install held back packages,A dist-upgrade will install new dependencies for packages already installed and may remove packages if they are no longer needed. This will not bring you to a new release of ubuntu. 
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a

```

Reboot now and let's see the effect.
Advise us of the results.

[INDENT][INDENT]maybe all good now
[INDENT][INDENT][INDENT]maybe more work to be done
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-09-26
Thank you so much for the assistance, unfortunately I think nothing was downloaded, I just got loads of failures. Because I am running it from the recovery screen do you think that would be the reason why it is not working? I can't open the terminal.

Any way to just revert it back to 12.04?

I could then save all my stuff on a hard drive and then just do a clean install of 14.04 LTS.

I am thinking that maybe is due to the age of my machine. It's an AMD64 from 2003 with 1GB of RAM. Do you think that could be the reason?

---

### Post by Bashing-om on 2014-09-26
tequiladave-n; Yikes !

My bad ! I failed to take into account you were in "recovery mode" !

We must 'remount' so you have read/write access to the root partition.
Boot back into recovery mode and do terminal command:
```

mount -o remount rw /

```
Now, you have 'root' read/write access and as such in the clean up/update procedure you will not need 'sudo'. So execute all those commands without 'sudo' . 

That done, reboot and let's see the effect.

[INDENT][INDENT]boy, did I miss that one
[/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-09-26
Unfortunately it behaved exactly the same way and the outcome the same!!!

---

### Post by Bashing-om on 2014-09-26
tequiladave-n; Umphh;;

Let's do this in small easy steps.
make sure we do have internet connection:
boot to recovery mode and also choose "enable networking"
Now what returns for terminal command:
```

ping -c3 google.com

```
as in my return:
```

3 packets transmitted, 3 received, 0% packet loss, time 2000ms

```
If you now have a connection:
What returns from:
```

apt-get update

```

I try and put things into context to determine where the errors are generated from. Now 1 step at a time.

[INDENT][INDENT]fault isolation
[INDENT][INDENT][INDENT]to restoration
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-09-26
Hi from the code apt-get update I get a series of errors and these are some of the errors, all very similar with the sentences below

"could not resolve gb.archive.ubuntu.com"

"could not resolve security.ubuntu.com"

"failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/trusty-security/release.gng"

---

### Post by Bashing-om on 2014-09-26
tequiladave-n;

What was your result from:
```

ping -c3 google.com

```

[INDENT]1 step forward
[INDENT][INDENT][INDENT]2 steps back
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-09-26
So the ping I think it tells us I am not connected to the internet. 

unknown host google.com

---

### Post by Bashing-om on 2014-09-26
tequiladave-n; Sheesshh..

Could be a number of things.
Let's see if we can get out of the recovery console, to a terminal that is easier/safer to work in.
Try this:
Boot to the grub boot screen with a normal kernel highlighted press the 'e' key for edit mode -> boot parameters screen.
Arrow down and across to the terms "quiet splash" and insert the term also "nomodeset".
key combo ctl+x to continue the boot process.
Can you now boot to the GUI ? Degraded graphics is acceptable at this point.
No ?
Then we try a different parameter to boot to terminal.

[INDENT][INDENT]more than one way
[INDENT][INDENT][INDENT]to access ubuntu
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-09-27
So that I can't seem to be able to do... I think I can add the nomodeset but the ctl+x doesn't do anything. I might be in the wrong place.

Meanwhile I contacted my friend that got me on Linux to start off with and he advised me to just get a pen drive and install 14.04 over my previous version or whatever is there, as long as I have a root partition (which I am not sure I have) but even this goes nowhere. I did a bootable pen drive with Xubuntu using Universal USB Installer and I can get to the Installer Boot Menu but once I choose install Xubuntu I just get a white screen and nothing else happens. It goes from an all white screen to a small white rectangle on the top left corner of the screen and nothing else seems to happen from that point.

At this stage I only want to be able to save my photos and the music I have on it but I am getting increasingly worried that I might do something and mess it all up!!!

What is the danger from working on the Recovery console? Can you get me connected back up to the internet from the recovery console?

Kind Regards and sorry to bother you with this.

---

### Post by Bashing-om on 2014-09-27
tequiladave-n; Well... well,

Let's see if we can get you to boot to a terminal.
Again, reboot, and as soon as the [color=red]bios[/color] screen clears, press and held the right -shift- key. OK, the next screen is the grub boot menu. In this menu make sure a ubuntu kernel line is highlighted (or an asterisk symbol in 14.04) and press the 'e' key for edit mode.
The next screen is the boot parameter screen, arrow down and across to the terms "quiet splash" this time replace these terms with the term "text" - without the quotes -.
Key combo clt+x will continue the boot process to a textual terminal (TTY1).
Log in here with your user name and password - there will be no response to the screen when the password is entered, normal.

The reason I prefer we use a terminal rather than "recovery" is in the recovery console one is "root" and it is much to easy to execute "some" commands that will render the system to an even greater degree of failure - or complete destruction. In this recovery console one has to enable all else to work with the system, where as in terminal we have these accesses. In particular, I am concerned that even "enable network" you get no response from a DNS ping to Google from within the recovery console. Give rise to the concern of just how stable the operating system is.

Now IF you are not able to boot to this terminal interface, there are serious serious problems, and I now recommend we access the installed system from a liveDVD(USB) .

At any time you feel the more comfortable, we can back up your personal files IF we can make provision to write these files to either a USB drive or to DVD.

So, bottom line, boot up to the terminal, or advise otherwise.

[INDENT][INDENT][INDENT]we can do this
[/INDENT][/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-09-27
Once again thank you very much for your assistance.

I am really confused but I think I am in the screens you mention but the instruction to go down and across doesn't apply to the options I have got here.

Below you can see a dropbox link where you can see pictures of what I am looking at, hopefully that will shed a light on what I am looking at, sorry about the poor resolution as taking pictures of the screen is not very good.

[https://www.dropbox.com/sh/1bsqjmqzaj1v13l/AAAGTzfkRLC-Tvco6ehs7W5Sa?dl=0](https://www.dropbox.com/sh/1bsqjmqzaj1v13l/AAAGTzfkRLC-Tvco6ehs7W5Sa?dl=0)

Meanwhile I have managed to start copying all my stuff out of it, using Manjaro, which my mate told me to use it to run a Live session. It is going to take a while as it is a slow machine but I am wondering if I should just wipe the hard drive and then just do a fresh install of the OS. What is your opinion?

---

### Post by Bashing-om on 2014-09-27
tequiladave-n; Yuk;

What I see in the screen shots are the kernels for 12.04. I see a whole lot of kernels ! This situation may be the result of the /boot partition filled up and now the system has no operating head room.
OK, let's try this .. with any 3.2 series non-recovery kernel highlighted, press the 'e' key. What results now ??

Great that you are making your backups in the event you choose to (RE-)install. ubuntu is always fixable IF you have an ubuntu liveDVD of the release that is installed; It Is but a matter of time and effort, and a definite learning experience - many many times.

Now the thing is, If one has backups, one can (RE-)install the operating system with a fast internet connection in 20 minutes, and a few more to restore from backups. Over and done with. One learns very little taking this option. BUT, it is always an option.

Me, I abscribe to - if it's broken, FIX IT. That is one way I have learned a lot about this operating system. I break it, I fix it.

it's your time, your effort, your call

---

### Post by tequiladave-n on 2014-09-28
Hello,

I am usually of the same opinion as you, if broke fix it but I hate having to bother other people (You in this case) to fix it and I just seems to be quite a struggle. Any how onwards and upwards.

If I press the e key on any of the 3.2 series non-recovery kernel highlighted I get the screen shown in the picture on the link below

[URL="https://www.dropbox.com/s/3susb3z9vhlamno/IMAG0676.jpg?dl=0"]https://www.dropbox.com/s/3susb3z9vhlamno/IMAG0676.jpg?dl=0

[https://www.dropbox.com/s/ko97ikzjjd377tv/IMAG0677_1.jpg?dl=0](https://www.dropbox.com/s/ko97ikzjjd377tv/IMAG0677_1.jpg?dl=0)
[/URL]

---

### Post by Bashing-om on 2014-09-28
tequiladave-n; Weeelll..

> 
 but I hate having to bother other people (You in this case) to fix it and I just seems to be quite a struggle. 


That is why we are here, is to help. We are all in this together. I am more than willing to help get this install to a stable condition, and thence assist in getting you release-upgraded . I will advise upfront that it will be a struggle and time consuming .. and I promise it will advance you on the learning curve. If I am really good at this, I too will advance on my own learning curve.

Next is to mount that installs's root partition from a liveDVD, have a look, and prepare to remove kernels from a live environment.

OR we can play around trying to boot from grub in the present install... I have no preference as to how to proceed. It will be interesting to see, however, if we can boot the install from grub. IF we can boot from grub into the install, cleaning up will be much easier . Again IF we have a working internet connection IF we need to replace files.

Presently we can make a number of options.
1) Fix IF we can boot up from grub - and have a working internet connection
2) Fix from a liveDVD
3) Do a nice clean fresh install of 14.04

Again, it is your system, your time. your effort ->
[INDENT][INDENT][INDENT]your call
[/INDENT][/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-09-28
ok sweet it sounds like a plan... I have time and I like to learn just worried my level of knowledge is too basic for you so bare with me and my ignorance of the workings of Linux.

I have a LiveCD version I used yesterday to backup my drive so we can go down that route. Which one do you prefer to explore?

---

### Post by tequiladave-n on 2014-09-28
ok sweet it sounds like a plan... I have time and I like to learn just worried my level of knowledge is too basic for you so bare with me and my ignorance of the workings of Linux.

I have a LiveCD version I used yesterday to backup my drive so we can go down that route. Which one do you prefer to explore?

---

### Post by Bashing-om on 2014-09-28
tequiladave-n; Let's boot this sucker !

Get ready to learn about the booting process.

Boot back with the install to gub's boot menu. This time with any 3.2 kernel highlighted, press the 'c' key for a 'c'ommand line interface.
Let's find out if we have a bootable config file: Here I am going to "assume" you have a standard install, with ubuntu installed onto that 1st (only ?) hard disk and installed to the 1st partition. Else will fail for sure !, let's see .
Grub terminal commands:
```

linux (hd0,msdos1)/vmlinuz-3.2.0-69-generic root=/dev/sda1 ro
initrd (hd0,msdos1)/initrd.img-3.2.0-69-generic
boot

```
What results - exactly ! .. If you do not boot, will have to set some additional parameters, and as well insure where ubuntu is installed to. And ahunt'n we will go.

If at any time/point you do not understand, or have a question, please ask. This forum also functions as an institution of teaching/learning ! If you do not ask, we can not answer.

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]do not be dismayed if it is not-so-yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-09-28
I should say that on the grub boot menu it doesn't give me a 14.04 boot option only 12.04.5 LTS, Kernel 3.2.0-69-generic and it goes all the way down to Ubuntu 12.04.5 LTS, Kernel 2.6.27-7-generic, also it has always gone straight to this screen when I boot my computer since I have had linux installed, so I don't press the right shift to get to it, I just boot normally and it comes to this screen which I can then press ENTER or wait 5 seconds and it just goes with the highlighted option. Another thing I didn't mention earlier is that I have always ran Xubuntu and not Ubuntu.

I installed this myself so I followed the on screen instructions and I am not running the system on a dual boot setup with a version of windows on another partition. This computer only has Linux, no windows. Not sure if it is worth mentioning that I have a second hard drive installed on it.

So word for word I get the following, after pressing c on the grub boot menu:
[ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ESC at any time exits.]

grub> _


I have also attempted to type those commands you sent and I get:
First Line "Error 27: Unrecognized command"
Second Line "Error 19: Linux Kernel must be loaded before initrd"
Third Line "Error 8: Kernel must be loaded before booting"

---

### Post by Bashing-om on 2014-09-28
tequiladave-n; Yeah,

We are working to boot this install, in order to clean up the /boot situation.
At that:
> 
grub> _

You are at grub's command line interface.
OK, two things now to "check":
from that grub prompt what returns;
```

ls -lh

```
That output will indicate where "root" is.

```

set

``` which will show all the parameters that grub has set ( so we do not have to re-set them) and we now set what we have to.

A picture at this time will sure be worth that thousand words.

Then we try and boot once more with the correct path and boot parameters.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-09-28
Both those commands return "Error 27: Unrecognized Command"

---

### Post by Bashing-om on 2014-09-28
tequiladave-n; Humm ... That really does not compute =>

as you were able to boot in recovery mode.

Do you have a liveDVD(USB) of 14.04 on-hand ? It is now time to boot up from a known good foundation, and start looking to see the why-fore.

[INDENT][INDENT]we will know why !
[/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-09-28
What is your suggested application to create the USB drive of it?

If  there's a link of the liveDVD of 14.04 I would be appreciated as I do  have a version of Ubuntu 14.04 iso file but when I try to run it from  the pen drive it just freezes so I am thinking it might be to do with  the program I am using to create it. Having said that I managed to run  Manjaro using the same USB drive creating software which is Universal USB Installer.

I will look up liveDVD 14.04 on google and see what comes up.

I found ExLight 14.04.1 and will install it to a pen drive right now

[http://sourceforge.net/projects/exlight/?source=typ_redirect](http://sourceforge.net/projects/exlight/?source=typ_redirect)

---

### Post by tequiladave-n on 2014-09-28
I have the Live version of Manjaro running at the moment and I was looking up some stuff and just noticed that you can run teamviewer on Linux, is this right? if so do you want to have a look in my machine? Let me know

---

### Post by Bashing-om on 2014-09-28
tequiladave-n; Sorry;

Had slipped my mind you have Manjaro  on-hand, That will in all likely food suffice for looking at the hard drive. BUT, not to (re-)install grub.

For now from a terminal in Manjaro, what returns:
```

sudo fdisk -lu
sudo parted -l

``` as we prepare to mount the install partition and take a look around.

I do anticipate (RE-)installing grub, and for that we must have a liveDVD(USB) of release ubuntu 14.04. Seeing as how I do not trust any other means.

-------------------------
A source for ubuntu 14.04:
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

I think the rest you have under control, md5sum, burning to USB ( ubetbootn, pendrive ,ect.).
Then once burned, do not forget to boot to the boot screen and "check disk for defects" .. then BOOT it up and we go again.
------------------

Edit: I failed to post this // doing so at this time. sorry.

as to team viewer, I do not have it installed, and on this my work station I have no audio anyway.. We are making progress here - better if i post my responses ! -  we will work through this to the edification of all who seek a similar solution.

[INDENT][INDENT][INDENT]inquiring minds want to [/INDENT][/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-09-28
so for the first code this was what it returned:
Disk /dev/sda: 152.7 GiB, 163928604672 bytes, 320173056 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x31ae3855

Device    Boot     Start       End    Blocks  Id System
/dev/sda1 *           63   6217154   3108546  83 Linux
/dev/sda2        6217155 320159384 156971115   5 Extend
/dev/sda5      314167203 320159384   2996091  82 Linux 
/dev/sda6        6217281 308158829 150970774+ 83 Linux
/dev/sda7      308158893 314167139   3004123+ 82 Linux 

Partition table entries are not in disk order.

Disk /dev/sdb: 149.1 GiB, 160041885696 bytes, 312581808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x14bd29d8

Device    Boot Start       End    Blocks  Id System
/dev/sdb1         63 312575759 156287848+  7 HPFS/NTFS/


Disk /dev/sdc: 14.7 GiB, 15728640000 bytes, 30720000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x993a63ce

Device    Boot Start       End   Blocks  Id System
/dev/sdc1 *     8064  30719999 15355968   c W95 FAT32 (


For the second code:

Model: ATA Maxtor 6Y160P0 (scsi)
Disk /dev/sda: 164GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  3183MB  3183MB  primary   ext3            boot
 2      3183MB  164GB   161GB   extended
 6      3183MB  158GB   155GB   logical   ext3
 7      158GB   161GB   3076MB  logical   linux-swap(v1)
 5      161GB   164GB   3068MB  logical   linux-swap(v1)


Model: ATA ST3160023AS (scsi)
Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  160GB  160GB  primary  ntfs


Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sdc: 15.7GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      4129kB  15.7GB  15.7GB  primary  fat32        boot, lba


Hope this helps

---

### Post by Bashing-om on 2014-09-28
tequiladave-n; yepper;

From:
> 
/dev/sda1 * 63 6217154 3108546 83 Linux

we know the where.
Now for the what:
From the liveDVD terminal:
```

sudo mkdir /mnt/work
sudo mount /dev/sda1 /mnt/work
ls -al /mnt/work
ls -al /mnt/work/boot

``` to "see" what we are going to do.

Once all outputs are transferred, we are done here for the time being. ReMeMbeR, any file system manually mounted MUST be (UN)mounted - else file system corruption is likely.
```

sudo umount /mnt/work

```

[INDENT][INDENT]one small step completed
[/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-09-28
so I have followed your instructions (i hope):
code:
[manjaro@manjaro ~]$ sudo mkdir /mnt/work
[manjaro@manjaro ~]$ sudo mount /dev/sda1 /mnt/work
[manjaro@manjaro ~]$ ls -al /mnt/work
total 88
drwxr-xr-x 20 root root  4096 10.01.2009 22:06 ./
drwxr-xr-x  3 root root    60 28.09.2014 22:37 ../
drwxr-xr-x  2 root root  4096 10.01.2009 19:34 bin/
drwxr-xr-x  2 root root  4096 10.01.2009 19:28 boot/
drwxr-xr-x  4 root root  4096 10.01.2009 19:26 dev/
drwxr-xr-x 51 root root  4096 26.09.2014 11:18 etc/
drwxr-xr-x  2 root root  4096 20.10.2008 12:27 home/
drwxr-xr-x 12 root root  4096 10.01.2009 19:34 lib/
drwx------  2 root root 16384 10.01.2009 19:25 lost+found/
drwxr-xr-x  4 root root  4096 10.01.2009 19:25 media/
drwxr-xr-x  2 root root  4096 20.10.2008 12:27 mnt/
drwxr-xr-x  2 root root  4096 10.01.2009 19:26 opt/
drwxr-xr-x  2 root root  4096 20.10.2008 12:27 proc/
drwxr-xr-x  2 root root  4096 10.01.2009 19:26 root/
drwxr-xr-x  2 root root  4096 10.01.2009 19:41 sbin/
drwxr-xr-x  2 root root  4096 10.01.2009 19:26 srv/
drwxr-xr-x  2 root root  4096 14.10.2008 13:02 sys/
drwxrwxrwt  4 root root  4096 26.09.2014 11:08 tmp/
drwxr-xr-x 11 root root  4096 10.01.2009 19:34 usr/
drwxr-xr-x 13 root root  4096 10.01.2009 19:26 var/
lrwxrwxrwx  1 root root    11 10.01.2009 19:25 cdrom -> media/cdrom/
lrwxrwxrwx  1 root root    32 10.01.2009 19:27 initrd.img -> boot/initrd.img-2.6.27-7-generic
lrwxrwxrwx  1 root root     4 10.01.2009 19:26 lib64 -> /lib/
lrwxrwxrwx  1 root root    29 10.01.2009 19:27 vmlinuz -> boot/vmlinuz-2.6.27-7-generic
[manjaro@manjaro ~]$ ls -al /mnt/work/boot
total 12168
drwxr-xr-x  2 root root    4096 10.01.2009 19:28 ./
drwxr-xr-x 20 root root    4096 10.01.2009 22:06 ../
-rw-r--r--  1 root root  503560 24.10.2008 07:55 abi-2.6.27-7-generic
-rw-r--r--  1 root root   85316 24.10.2008 07:55 config-2.6.27-7-generic
-rw-r--r--  1 root root 8129803 10.01.2009 19:28 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 24.10.2008 07:55 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1130 24.10.2008 07:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 24.10.2008 07:55 vmlinuz-2.6.27-7-generic
[manjaro@manjaro ~]$ sudo umount /mnt/work


Hope that gives you the info you require!!!

---

### Post by tequiladave-n on 2014-09-28
I have now restarted the machine and it is checking the hard drive for errors running what I believe to be my initial version of Xubuntu! I need to go to bed (I am in the UK) and until tomorrow evening I won't be able to resume any works on this, so for now, thank you very much and if there's anything you need me to do, please let me know!!!

Drive checks have been done and even though it boots, and even get the log on screen and allowing me to log in, still no icons/folders or anything on the desktop main screen

Cheers
David

---

### Post by Bashing-om on 2014-09-28
tequiladave-n; Yukkie poo !

Not at all what I expected, and worse !

OK, you think it is 12.04, but the ONLY kernel that is installed is from the lucid -10.04 -era ( -rw-r--r-- 1 root root 2339712 24.10.2008 07:55 vmlinuz-[color=red]2.6.27-7[/color]-generic) I can not even guess as to why there is only this 1 kernel in existence and it is soooo old !
Here is a kernel from a 12.04 install on my system:
> 
-rw-------  1 root root  4982576 May  2 17:17 vmlinuz-[color=green]3.2.0-61[/color]-generic


SO, what are we working with for sure here, as 10.04 for the desk top is END-Of-Life and has no support !
mount back up the sda1 partition as before.
now what returns from:
```

cat /mnt/work/etc/issue
cat -n /mnt/work/etc/apt/sources.list

```
(UN)mount
```

sudo umount /mnt/work

```

Will tell the tale, 
[INDENT][INDENT]as well dictate what we do, next 
[/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-09-29
So those 2 last codes have returned the following:

code:
[manjaro@manjaro ~]$ cat /mnt/work/etc/issue
cat: /mnt/work/etc/issue: No such file or directory

[manjaro@manjaro ~]$ cat -n mnt/work/etc.apt/sources.list
cat: mnt/work/etc.apt/sources.list: No such file or directory

[manjaro@manjaro ~]$ sudo umount /mnt/work
umount: /mnt/work: mountpoint not found

What do you make of that?

---

### Post by Bashing-om on 2014-09-29
tequiladave-n; Umph;

Slipped my mind we are working from a liveDVD, as such that mount point will not persist through a re-boot.
Once more, with feeling:
```

sudo mkdir /mnt/work
sudo mount /dev/sda1 /mnt/work
cat /mnt/work/etc/issue
cat -n /mnt/work/etc/apt/sources.list

```

(UN)mount
```

sudo umount /mnt/work

```

[INDENT][INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-09-29
ok that seemed to work:

[manjaro@manjaro ~]$ sudo mkdir /mnt/work
[manjaro@manjaro ~]$ sudo mount /dev/sda1 /mnt/work

[manjaro@manjaro ~]$ cat /mnt/work/etc/issue
Ubuntu 8.10 \n \l

[manjaro@manjaro ~]$ cat -n /mnt/work/etc/apt/sources.list
     1    
     2    deb cdrom:[Xubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081028)]/ intrepid main multiverse restricted universe

---

### Post by Bashing-om on 2014-09-29
tequiladave-n; Yikes !

My best advise, as a result of:
> 
[manjaro@manjaro ~]$ cat /mnt/work/etc/issue
Ubuntu 8.10 \n \l

[manjaro@manjaro ~]$ cat -n /mnt/work/etc/apt/sources.list
1 
2 deb cdrom:[Xubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081028)]/ intrepid main multiverse restricted universe

Is to do a fresh clean install of the current release 14.04. Release 8.10 is so far in the past and so much has changed in the operating system since then there is little likely-hood of being able to make that transition to the current release.
8.10->9.04->9.10->10.04->12.04->14.04, I just can not see it happening, not to mention the bandwidth and TIME to make it happen.

Burn a 14.04 and test in the 'live' environment to insure your hardware is still compatible !

IF you require assistance to retrieve any important files of the installed 8.10 I will be more than glad to help.

[INDENT][INDENT]not good
[INDENT][INDENT][INDENT]just the way it is
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-09-29
The problem with that is that 14.04 or any other Ubuntu/Xubuntu just seems to freeze on install. regardless if live or not

---

### Post by Bashing-om on 2014-09-29
tequiladave-n; Welp:

Might be able to do something about that, let's see what your hardware is :
```

cat /proc/cpuinfo
dmidecode

```
and see 'bout matching it to a current kernel version.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-09-29
and this is what came back from those commands:

[manjaro@manjaro ~]$ cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 12
model name    : AMD Athlon(tm) 64 Processor 3000+
stepping    : 0
microcode    : 0x3a
cpu MHz        : 1800.000
cache size    : 512 KB
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext lm 3dnowext 3dnow rep_good nopl
bogomips    : 3618.54
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

[manjaro@manjaro ~]$ dmidecode
# dmidecode 2.12
/dev/mem: Permission denied

---

### Post by Bashing-om on 2014-09-29
tequiladave-n; Hey hey !

So far it looks like you are a prime candidate for (L)ubuntu !
and for 'dmidecode'
do it with the elevated privileges :
```

sudo dmidecode

```

[INDENT][INDENT]it can happen
[/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-09-29
Here you go...
```

# dmidecode 2.12
SMBIOS 2.4 present.
43 structures occupying 2217 bytes.
Table at 0x000F0800.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Phoenix Technologies, LTD
    Version:  3.10
    Release Date: 03/09/2005
    Address: 0xE0000
    Runtime Size: 128 kB
    ROM Size: 512 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/360 kB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        AGP is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Function key-initiated network boot is supported

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: Compaq Presario 061
    Product Name: PX628AA-ABU SR1420UK GB520
    Version: 0nB0411RE101SALMO00
    Serial Number: CZB5160H79
    UUID: 604C7027-CB5B-D911-B10E-AD079CCA5786
    Wake-up Type: Power Switch
    SKU Number:  
    Family:  

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: ASUSTek Computer INC.
    Product Name: Salmon 
    Version: 1.04
    Serial Number: MB-1234567890

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
    Manufacturer: Hewlett-Packard
    Type: Desktop
    Lock: Not Present
    Version: 1111
    Serial Number:  
    Asset Tag:  
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None
    OEM Information: 0x00000000

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
    Socket Designation: Socket 754
    Type: Central Processor
    Family: Athlon 64
    Manufacturer: AMD
    ID: C0 0F 00 00 FF FB 8B 07
    Signature: Family 15, Model 12, Stepping 0
    Flags:
        FPU (Floating-point unit on-chip)
        VME (Virtual mode extension)
        DE (Debugging extension)
        PSE (Page size extension)
        TSC (Time stamp counter)
        MSR (Model specific registers)
        PAE (Physical address extension)
        MCE (Machine check exception)
        CX8 (CMPXCHG8 instruction supported)
        APIC (On-chip APIC hardware supported)
        SEP (Fast system call)
        MTRR (Memory type range registers)
        PGE (Page global enable)
        MCA (Machine check architecture)
        CMOV (Conditional move instruction supported)
        PAT (Page attribute table)
        PSE-36 (36-bit page size extension)
        CLFSH (CLFLUSH instruction supported)
        MMX (MMX technology supported)
        FXSR (FXSAVE and FXSTOR instructions supported)
        SSE (Streaming SIMD extensions)
        SSE2 (Streaming SIMD extensions 2)
    Version: AMD Athlon(tm) 64 Processor 3000+
    Voltage: 1.5 V
    External Clock: 200 MHz
    Max Speed: 3700 MHz
    Current Speed: 2000 MHz
    Status: Populated, Enabled
    Upgrade: Socket 754
    L1 Cache Handle: 0x0008
    L2 Cache Handle: 0x0009
    L3 Cache Handle: Not Provided
    Serial Number:  
    Asset Tag:  
    Part Number:  

Handle 0x0005, DMI type 5, 20 bytes
Memory Controller Information
    Error Detecting Method: 64-bit ECC
    Error Correcting Capabilities:
        None
    Supported Interleave: One-way Interleave
    Current Interleave: One-way Interleave
    Maximum Memory Module Size: 1024 MB
    Maximum Total Memory Size: 2048 MB
    Supported Speeds:
        70 ns
        60 ns
        50 ns
    Supported Memory Types:
        Standard
        SDRAM
    Memory Module Voltage: 2.9 V
    Associated Memory Slots: 2
        0x0006
        0x0007
    Enabled Error Correcting Capabilities: None

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A0
    Bank Connections: 0
    Current Speed: 50 ns
    Type: DIMM
    Installed Size: 512 MB (Single-bank Connection)
    Enabled Size: 512 MB (Single-bank Connection)
    Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A1
    Bank Connections: 2 3
    Current Speed: 50 ns
    Type: DIMM
    Installed Size: 512 MB (Double-bank Connection)
    Enabled Size: 512 MB (Double-bank Connection)
    Error Status: OK

Handle 0x0008, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L1 Cache
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 128 kB
    Maximum Size: 128 kB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Data
    Associativity: 4-way Set-associative

Handle 0x0009, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L2 Cache
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 512 kB
    Maximum Size: 512 kB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Unified
    Associativity: 4-way Set-associative

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PRIMARY IDE
    Internal Connector Type: On Board IDE
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SECONDARY IDE
    Internal Connector Type: On Board IDE
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: FDD
    Internal Connector Type: On Board Floppy
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: 8251 FIFO Compatible

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: COM1
    Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
    External Reference Designator:  
    External Connector Type: DB-9 male
    Port Type: Serial Port 16450 Compatible

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: COM2
    Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
    External Reference Designator:  
    External Connector Type: DB-9 male
    Port Type: Serial Port 16450 Compatible

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: LPT1
    Internal Connector Type: DB-25 female
    External Reference Designator:  
    External Connector Type: DB-25 female
    Port Type: Parallel Port ECP/EPP

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PS/2 Keyboard
    Internal Connector Type: PS/2
    External Reference Designator:  
    External Connector Type: PS/2
    Port Type: Keyboard Port

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PS/2 Mouse
    Internal Connector Type: PS/2
    External Reference Designator:  
    External Connector Type: PS/2
    Port Type: Mouse Port

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB1
    External Connector Type: Other
    Port Type: USB

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB2
    External Connector Type: Other
    Port Type: USB

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB3
    External Connector Type: Other
    Port Type: USB

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB4
    External Connector Type: Other
    Port Type: USB

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB5
    External Connector Type: Other
    Port Type: USB

Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB6
    External Connector Type: Other
    Port Type: USB

Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: VIDEO
    External Connector Type: DB-15 female
    Port Type: Video Port

Handle 0x0019, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: Line In
    External Connector Type: None
    Port Type: Audio Port

Handle 0x001A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: ETHERNET
    External Connector Type: RJ-45
    Port Type: Network Port

Handle 0x001B, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI1
    Type: 32-bit PCI
    Current Usage: Available
    Length: Short
    ID: 1
    Characteristics:
        5.0 V is provided
        PME signal is supported

Handle 0x001C, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI2
    Type: 32-bit PCI
    Current Usage: In Use
    Length: Short
    ID: 2
    Characteristics:
        5.0 V is provided
        PME signal is supported

Handle 0x001D, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI3
    Type: 32-bit PCI
    Current Usage: Available
    Length: Short
    ID: 3
    Characteristics:
        5.0 V is provided
        PME signal is supported

Handle 0x001E, DMI type 10, 12 bytes
On Board Device 1 Information
    Type: Other
    Status: Enabled
    Description:  
On Board Device 2 Information
    Type: Video
    Status: Disabled
    Description:  
On Board Device 3 Information
    Type: Ethernet
    Status: Enabled
    Description:  
On Board Device 4 Information
    Type: Sound
    Status: Enabled
    Description:  

Handle 0x001F, DMI type 9, 13 bytes
System Slot Information
    Designation: AGP
    Type: 32-bit AGP 8x
    Current Usage: In Use
    Length: Short
    ID: 1
    Characteristics:
        PME signal is supported

Handle 0x0020, DMI type 13, 22 bytes
BIOS Language Information
    Language Description Format: Long
    Installable Languages: 3
        n|US|iso8859-1
        n|US|iso8859-1
        r|CA|iso8859-1
    Currently Installed Language: n|US|iso8859-1

Handle 0x0021, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 2 GB
    Error Information Handle: Not Provided
    Number Of Devices: 2

Handle 0x0022, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0021
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 512 MB
    Form Factor: DIMM
    Set: None
    Locator: A0
    Bank Locator: Bank0/1
    Type: DDR
    Type Detail: None
    Speed: Unknown
    Manufacturer: None
    Serial Number: None
    Asset Tag: None
    Part Number: None

Handle 0x0023, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0021
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 512 MB
    Form Factor: DIMM
    Set: None
    Locator: A1
    Bank Locator: Bank2/3
    Type: DDR
    Type Detail: None
    Speed: Unknown
    Manufacturer: None
    Serial Number: None
    Asset Tag: None
    Part Number: None

Handle 0x0024, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0003FFFFFFF
    Range Size: 1 GB
    Physical Array Handle: 0x0021
    Partition Width: 1

Handle 0x0025, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0001FFFFFFF
    Range Size: 512 MB
    Physical Device Handle: 0x0022
    Memory Array Mapped Address Handle: 0x0024
    Partition Row Position: 1

Handle 0x0026, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00020000000
    Ending Address: 0x0003FFFFFFF
    Range Size: 512 MB
    Physical Device Handle: 0x0023
    Memory Array Mapped Address Handle: 0x0024
    Partition Row Position: 1

Handle 0x0027, DMI type 32, 11 bytes
System Boot Information
    Status: No errors detected

Handle 0x0029, DMI type 144, 12 bytes
OEM-specific Type
    Header and Data:
        90 0C 29 00 00 11 D8 D6 5B 1D 37 01
    Strings:
        SiS630E-MAC

Handle 0x0028, DMI type 11, 5 bytes
OEM Strings
    String 1: bid=52GBheREF1,52GBheREF1;C_GOB;IS.N60d;PROD_MSWORKS;RN_STD;RP_S
    String 2: TD;WC_STD;WD_SE;##
    String 3:                                                                 
    String 4:                                                                 
    String 5:                                                                 
    String 6:                                                                 
    String 7:                                                                 
    String 8:                                                                 
    String 9:                                                                 
    String 10:                                                                 
    String 11:                                                                 
    String 12:                                                                 
    String 13:                                                                 
    String 14:                                                                 
    String 15:                                                                 
    String 16:                                                                 

Handle 0x002A, DMI type 127, 4 bytes
End Of Table
```

---

### Post by Bashing-om on 2014-09-29
tequiladave-n; Hey hey;

(L)ubuntu should work OK on this box .. will be a better experience if you were to swap out the ram chips from the "Installed Size: 512 MB" (X2 = 1Gig) to "Maximum Memory Module Size: 1024 MB" -> "Maximum Total Memory Size: 2048 MB".
Which would give you 2 Gigs of ram. NOW that would give you a good experience .
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

Burn this one to DVD, and I bet it runs !

[INDENT][INDENT]one solution
[INDENT][INDENT][INDENT][INDENT]of many
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-09-29
I thought about that many times but I don't even know what to get!!!

And you say burn it to DVD, not use a pen drive???

---

### Post by Bashing-om on 2014-09-29
tequiladave-n;

Either way will work on your box. The method is up to you.

I have had good results with (L)ubuntu on that same same hard ware. -> upgraded to the 2 Gigs.
And I do have a user preference for AMD. The littler guys just try harder.

Now I am prejudiced to (L)ubuntu, that is not to say that with 1 Gig of ram, an even lighter distro will not perform better.
It is linux, all it cost ya is time to "try it" and see.

[INDENT][INDENT][INDENT]open source -> all in this together
[/INDENT][/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-09-29
If I can just get your assistance on a couple more things I would be very appreciated:

1 - Running the live version and I am sure the full version, the screen is like zoomed so I can't actually see the things. I use a television as my monitor and it just seems everything is bigger than the viewing area. Can you help me with that?

2 - It asks me a few questions when trying to install it and I am a little confused:
What language do I pick? (Just joking I know the answer to that one)
Install Lubuntu alongside I am not interested in.
Erase Disk and Install Lubuntu?
Encrypt the New Lubuntu Installation?
Use LVM with the new Lubuntu installation?
Something else?

My friend said he sets a partition just for the operating system and another one to store everything else so when he wants to change Distro he just has to worry about that partition and not lose anything else. Can you help me set it up like that?

Thank you for your assistance till now and we are coming to the end of it and I don't know how to thank you.

I have a Raspberry Pi that I have never used other than to see it working, maybe I will hit you up for that as well ahahaha

Cheers

---

### Post by Bashing-om on 2014-09-29
tequiladave-n; Sure !

We are here to help; not judge, not critisize- just help. ( many times that help is best done by teaching ).
OK;
Yeah I also prefer to set up my partitions for my use case and as well exterior "data" partitions.
For the inexperienced the default "Erase Disk and Install Lubuntu" is just fine good and dandy.
If you have an idea of what you prefer different -> "something else".
If you know what you want -> GParted, and set up the partitions.

"Encrypt the New Lubuntu Installation" Avoid like the plague ! Unless you have some strong over-riding reason to encrpyt your data. Doing this adds a layer of complexity that in times of troube cannot and I do mean can not be overcome. 

"Use LVM with the new Lubuntu installation?" You have a server and/or multiple hard drives ?  No ? then nope !


I do not mind at all assisting you to "set up" partitions, I do prefer to use GParted to set them up prior to the install stage. BUT, I am falling behind the times and have no experience with the new GPT partitioning if we are going to do "large disk" partitioning. 
IF we do decide on GPT, well, we will fumble through it together.
Show what we are working with presently (again ?)
```

sudo fdisk -lu

```

But think'n about it, and though I have done it many times, I have never taken great notice of how I do it, so will again be a matter of fumbling through it. I just do it with-out even thinking about the steps involved. It really is that simple and easy. Just must tell the installer - in the install process what is what (again).

So what is your use case, how big do you want to make partitions ? How many partitins for what ?
If I may:
A partition of some size - maybe like 20 Gigs -  for the operating system  '/' (that is root)
A partition of some size -maybe like 50 Gigs - for your home(s) ( personal data space)
A partition - maybe - for swap depending on how much ram is onborad and IF you hibernate the machine - say 2 Gigs ???
A Partition of some size - say 50 Gigs - for a "shared" data partition -> Windows ?
A partition of some size - say 30 Gigs - for a "shared" data partition -> other 'buntus


As you can see it takes a bit of thought and planning for "your" use case as to how to partition.
Maybe a good help:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
as our means of common ground .

------------------------------
> 
I have a Raspberry Pi that I have never used other than to see it working, maybe I will hit you up for that as well ahahaha

Never tethered a device to my box -> never to old to learn, we can fumble through this together also.
BUT I do not have any devices to tether, so will be at a serious dis-advantage. 


But hey !

[INDENT][INDENT]ain't no steps for a stepper
[/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-09-29
I would like to do a partition of let's say 15GB for the Operating system and another one with the rest of the hard drive for documents and so on. So my hard drive is 163.9GB so we could set one with 13.9Gb for the Root and the rest for Home (is that the name?). I do a lot of downloading.

No need to have loads of partitions and this is not a dual boot, it is a Lubuntu only system, or it will be when we are done.

I am quite worried about the aspect ratio of the screen and how it doesn't fit with my tv screen size.

---

### Post by Bashing-om on 2014-09-29
tequiladave-n; Umph !

slipped my mind !
> 
I am quite worried about the aspect ratio of the screen and how it doesn't fit with my tv screen size.

Many times the TV does not provide the EDID data to the operating system. Then it is on us to tell the operating system what is what.
One  means to do so is by creating ' /etc/X11/xorg.conf '; If the display settings in the GUI can not be used. Again, I have never had to learn to set up to use a TV for the monitor. 
I agree, getting the display right is the 1st priority. No good to install an OS if one can not see it !

I do have lubuntu installed on this box, and when you get to this stage, will boot up and see what we can do from within the GUI to set a resolution.
It will behoove us at the 1st opportunity to  explore our possibilities.
We want to know what grub sees; at a grub > prompt
terminal command
```

vbeinfo

``` and note down ALL the supported resolutions.
Then also in the operating system see what
```

xrandr
xrandr --verbose

```
'xrandr' may even permit us to set the resolution.

We will just play it by ear and see what works best for us.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]all things are possible
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-09-30
From the vbeinfo command I get Unknown command ( I am assuming the grub prompt is the prompt that I see when I press the c when on the screen that allows me to choose the kernel I want to log in with)

From the xrandr command

Screen 0: minimum 320 x 200, current 720 x 576, maximum 4096 x 4096
VGA-1 disconnected (normal left inverted right x axis y axis)
DVI-I-1 connected 720x576+0+0 (normal left inverted right x axis y axis) 708mm x 398mm
   1920x1080      30.0     25.0     24.0     30.0     24.0  
   1360x768       59.8  
   1280x768       60.4  
   1280x720       60.0     50.0     59.9  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   720x576        50.0* 
   720x480        60.0     59.9  
   640x480        75.0     60.0     59.9     59.9  
   720x400        70.1  
TV-1 connected 720x576+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   720x576        50.0*+
   1024x768       50.0  
   800x600        50.0  
   720x480        50.0  
   640x480        50.0  
   400x300        50.0  
   320x240        50.0  
   320x200        50.0 

from the xrandr --verbose
Screen 0: minimum 320 x 200, current 720 x 576, maximum 4096 x 4096
VGA-1 disconnected (normal left inverted right x axis y axis)
DVI-I-1 connected 720x576+0+0 (normal left inverted right x axis y axis) 708mm x 398mm
   1920x1080      30.0     25.0     24.0     30.0     24.0  
   1360x768       59.8  
   1280x768       60.4  
   1280x720       60.0     50.0     59.9  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   720x576        50.0* 
   720x480        60.0     59.9  
   640x480        75.0     60.0     59.9     59.9  
   720x400        70.1  
TV-1 connected 720x576+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   720x576        50.0*+
   1024x768       50.0  
   800x600        50.0  
   720x480        50.0  
   640x480        50.0  
   400x300        50.0  
   320x240        50.0

Screen 0: minimum 320 x 200, current 720 x 576, maximum 4096 x 4096
VGA-1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x51
    Timestamp:  30892
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
DVI-I-1 connected 720x576+0+0 (0x65) normal (normal left inverted right x axis y axis) 708mm x 398mm
    Identifier: 0x52
    Timestamp:  30892
    Subpixel:   unknown
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       0
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID: 
        00ffffffffffff001e6d5f565e630400
        0911010380462778ead9b0a357499c25
        11494ba56e00314045406140d1c00101
        010101010101023a801871382d40582c
        4500c48e2100001e1b2150a051001e30
        48883500bc862100001c000000fc0032
        364c433436200a2020202020000000fd
        00324b1c430f000a20202020202001b2
        020321f14e021101031213041405211f
        202210230907078301000065030c0010
        00011d00bc52d01e20b8285540c48e21
        00001e011d007251d01e206e285500c4
        8e2100001e011d80d0721c1620102c25
        80c48e2100009e8c0ad090204031200c
        405500c48e210000184e1f008051001e
        3040803700bc882100001800000000cc
    dithering mode: auto 
        supported: auto, off, on
    scaling mode: Full 
        supported: None, Full, Center, Full aspect
    subconnector: DVI-D 
        supported: Unknown, DVI-D, DVI-A
  1920x1080 (0x55)   74.2MHz +HSync +VSync
        h: width  1920 start 2008

---

### Post by Bashing-om on 2014-09-30
tequiladave-n; Umph !

Not getting 'vbeinfo' causes me some small amount of concern:
It was in my mind to try a simple edit:
[https://help.ubuntu.com/community/ChangeTTYResolution](https://help.ubuntu.com/community/ChangeTTYResolution)
as the place to start (and maybe good 'nuff !).

Try again, as your approach is correct, see if from the grub > prompt there is a return from the command "vbeinfo'.

Then again, with the internal display not connected, the system at the point of grub has no way to "see" an external (TV) monitor ? In that case, this could get interesting - how to make grub see the TV ?

[INDENT][INDENT]others have done it
[INDENT][INDENT][INDENT]we can too
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-09-30
Sorry I am lost, what do you want me to do?

This edit:
[h=1]FOR 9.10 KARMIC KOALA AND LATER[/h]
or this edit:

[h=1]For 9.04 and before[/h]

---

### Post by Bashing-om on 2014-09-30
tequiladave-n; Hey !

Do not worry about " Sorry I am lost," ... I often go astray !

To give direction to the focus of my intent to get a working display on that TV, I really would be the more comfortable if we can get a response for the command ' vbeinfo '  from the grub prompt.

Please try that command again.
Boot to the grub boot menu
'c' key for a command line interface
terminal command 
```

vbeinfo

```
With the info provided from that command (??), let's see what we can do to effect the TV display by edits to the file " /etc/default/grub "
As that means is much easier to implement, and as well to maintain.

[INDENT]else:
[INDENT][INDENT][INDENT]we do something else
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-09-30
I get a "Error 27: Unrecognized command"

---

### Post by Bashing-om on 2014-09-30
tequiladave-n; Yuk, but but ...


Even with some small amount of hesitation - grub not seeing the TV (??), let's see what we can do:
We not want to overdrive the TV and blow it up !
Let's take the 'randr' output as valid, see what results in the livedvd.
Boot the liveDVD to the boot options screen ( press any key as soon as ubuntu's splash screen appears - icons at bottom of screen)
F6 key for boot options, in the resulting popup is the "boot options" line.
Press ESC to remove the popup screen. The boot command line is now available for editing and will remain so as long as no popup menu is visible. 
This line ends with "--" arrow to the end and insert a space and then vga=772
The command will be executed when ENTER is pressed and the boot sequence will begin.

Where:
 from the output of 'randr' we have the resolution 1024x768 50.0 for  TV-1 .
Now from:
[http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers)
we translate the 'xranr' numbers to 'vga' numbers, here being vga=772
What is the result .. is the resolution on the TV now usable ?

We are just testing:
If this works in the LiveDVD we can make it happen in the install and make it a permanent thing.


[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-10-01
Hello,

I can't seem to be able to do this "Boot the liveDVD to the boot options screen ( **_press any key as soon as  ubuntu's splash screen appears - icons at bottom of screen_**)
F6 key for boot options, in the resulting popup is the "boot options" line.
Press ESC to remove the popup screen."

---

### Post by Bashing-om on 2014-10-01
tequiladave-n; UMpphhh !

Do not know where that fault ( if any) could lie.
There is but a very small window of opportunity for the system to recognize that a key has been pressed. On many of the older bios' the key to press is the escape key.
with the boot priority set to the CD drive in bios ->
Try:
a) as soon as the "bios" screen clears, depress and hold the escape key
b) as soon as the bios screen clears, repeatedly tap that escape key rather than holding it down - a lot depends on what bios has set for the interrupt signal.
One of the 4 methods should get to the liveDVD's boot options screen.

[INDENT][INDENT]if at 1st you do not succeed 
[INDENT][INDENT][INDENT]try something else ( not skydiving )
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-10-03
First of all I would like to apologize for not getting back to you earlier but work has been taking up most of my time in the last couple of days.

Regarding our little dilemma, I have pressed the esc straight after the bios boot sequence menu and I do get a grub: _ prompt at the bottom of the screen but when I type the vga=772 it says un-recognized command. Pressing F6 also doesn't clear the boot options screen.

Shall I just install Lubuntu anyhow? Than we can deal with it? I know it will work as I never had that problem on Xubuntu, so I am guessing we will find a solution for this. What is your opinion?

---

### Post by Bashing-om on 2014-10-03
tequiladave-n; Hello;

No hurry here, we do this at your pace. We are here but to help.

I do not understand why you can not boot in the liveDVD to the boot options screen ! .. But like you I am sure that (L)ubuntu will install just fine, and then from the new install we can work on the resolution situation.
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

What are your newer thoughts on partitioning for this new install ? Planning for the future, and how "you" use your system.

[INDENT][INDENT]in for a penny
[INDENT][INDENT][INDENT][INDENT]in for a pound
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-10-03
I just want to have one partition with the OS and another one to put everything else.

---

### Post by Bashing-om on 2014-10-03
tequiladave-n; OK,

Post back, for easy reference:
```

sudo fdisk -lu

```
and let's see how much space we have to work with,

1 Primary partition for the operating system
1 Extended partition , this will contain a logical partition for swap(2  Gigs, because we do not know how the system will be used) AND a 2nd logical partition for "data1" as a data partition
1 Primary partition to be used as a shared data partition (NTFS ????)

Make sure all personal data from this current install is backed up. When we fire up the partitioner anything on the hard disk(s) is history.

[INDENT][INDENT]let the fun begin
[/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-10-04
I have a second hard drive on this computer which I don't want to format, which is exactly the same size as the main drive. _***I have not backed up my second hard drive.***_

At the time of the command I also have two pen drives connected to the computer.

So the command returned:

lubuntu@lubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x31ae3855

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     6217154     3108546   83  Linux
/dev/sda2         6217155   320159384   156971115    5  Extended
/dev/sda5       314167203   320159384     2996091   82  Linux swap / Solaris
/dev/sda6         6217281   308158829   150970774+  83  Linux
/dev/sda7       308158893   314167139     3004123+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x14bd29d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   312575759   156287848+   7  HPFS/NTFS/exFAT

Disk /dev/sdc: 32.0 GB, 32015679488 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62530624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf530bdd3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              32    62530623    31265296    c  W95 FAT32 (LBA)

Disk /dev/sdd: 15.7 GB, 15728640000 bytes
68 heads, 4 sectors/track, 112941 cylinders, total 30720000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x993a63ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        8064    30719999    15355968    c  W95 FAT32 (LBA)

---

### Post by Bashing-om on 2014-10-04
tequiladave-n; Roger that ;

I see 'sda' as the hard drive holding 'buntu:
> 
/dev/sda1 * 63 6217154 3108546 83 Linux
 all linux partitions.
So how bout this:
We have 160 Gigs of space, the system takes 5 % for it's overhead, leaves us roughly 150 Gigs to split up.
The operating system partition as 70 Gigs - primary partition -
The extended partition as 32 1/2 gigs
With in the extended partition -> a swap partition of 2 1/2 gigs, AND a data1 partition of 30 gigs There abouts, ( house keeping )
The shared data partition - data2 - ( primary also ) of about 47 Gigs .. will take the remainder of the disk space less a tad at the end ( do not want the hard drive's head "bumbing") - The bump space, Not really required, but cheap insurance.

When you are ready, I will be ready;

[INDENT][INDENT]we do this
[/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-10-04
Sounds very technical, not sure why so many different partitions but I trust your advice so let's do it.

---

### Post by Bashing-om on 2014-10-04
tequiladave-n; Humm ...
I thought ( ??)..
> 
Sounds very technical, not sure why so many different partitions but I trust your advice so let's do it.

was as you desired - for separate data partitions. For a standard install, - non technical - there is nothing wrong at all with selecting "erase disk and install ubuntu" in the installer. And Let that be the end of it.

Have you read the guide:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
so we met on common ground .

[INDENT][INDENT]and we do the deed 
[/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-10-04
I just thought we could install the operating system on one partition and the rest for everything else, so if I need to re-install the operating system, at a future date, I don't need to worry about having to backup all my stuff. What are your thoughts on this? This computer I only use to watch television straight from the browser, download torrents, listen to music and watch movies.

---

### Post by Bashing-om on 2014-10-04
tequiladave-n; Like this:

There are as many thoughts on "backup solutions" as there are people installing .
I can only give you my personal take on it,
I back up my important files and data ONLY. In the event ( been there many times, and done that !) of resorting to a (RE-)install I do just that. And then copy my "data" back in place - I also keep a "change log" of any changes I make to the operating system. I see no real distinct advantage of separate partition(s) for a general use home computer. It takes less than 30 minutes with a good internet connection to (RE-)install and copy data back !

It is your call, we are here to help in what ever you want to do. In this particular case, I see no reason to do else than a standard install "erase disk and install ubuntu" . 

Now if you want a separate /home partition we are going to have to rethink the partitioning scheme. What I have presented to you incorporates the /home directory within the 'root' operating system in that 1st partition.

Keep in mind for "data" partition you have that 2nd hard drive.

It is your system, only you can say what your use case is ..

Nor to I have any reservations in participating IF it is your goal to utilize this use case as a means to learn ! But, you must decide ( and do the home work) what you want.

Merely as an example; Here is my "use case":
```

sysop@1404mini:~$ sudo fdisk -lu
[sudo] password for sysop: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065f5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    10242047     5120000   83  Linux
/dev/sda2        10244096    30724095    10240000   83  Linux
/dev/sda3        34207742   976771071   471281665    5  Extended
/dev/sda5       443795688   443811689        8001   82  Linux swap / Solaris
/dev/sda6       443811753   597409154    76798701   83  Linux
/dev/sda7       597409792   976771071   189680640   83  Linux
/dev/sda8        34207744    44447743     5120000   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x502a9772

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002ea65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   102402438    51200195+  83  Linux
/dev/sdc2   *   102404096   204804095    51200000   83  Linux
sysop@1404mini:~$

sysop@1404mini:~$ sudo blkid
/dev/sda1: LABEL="1404mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1404mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1404" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1404mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdb1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
/dev/sdc1: LABEL="1404std" UUID="345cab2e-22e7-4f89-8781-05cc0f7628a2" TYPE="ext4" 
/dev/sdc2: LABEL="ubie1204" UUID="7dd23297-30ea-417a-8f69-3e2df76f3192" TYPE="ext4" 
sysop@1404mini:~$

``` For the way I use MY system and for the way I "think".


[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-10-04
Ok, I think I am going to do the normal install...

I will keep you posted on the progress. Once I installt it I would ask your assistance to set the correct screen resolution

I also have a little ASUS Netbook that I am going to wipe Windows out of it and install this Lubuntu.

This little netbook has 2 partitions on it so I need to delete the second partition and then format the whole thing.

---

### Post by Bashing-om on 2014-10-04
tequiladave-n; Yepper.

A standard install is by far the better " all around " general solution.
Special use case one can then employ other options. 

> 
I also have a little ASUS Netbook that I am going to wipe Windows out of it and install this Lubuntu.

This little netbook has 2 partitions on it so I need to delete the second partition and then format the whole thing.

again, nope - IF a standard install meets your needs - "erase disk and install ubuntu" will take care of everything. The installer will wipe that disk ( all partitions). 
caveat: UEFI is a whole new ball game, and we WILL have to make adjustments if that is the case for the NetBook, but only in how the system boots.

[INDENT][INDENT]many paths to an end
[/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-10-04
I have now done the fresh install on the desktop computer.

This has been done without any problems that I can see for now. I did notice that whilst looking for software on the Lubuntu Software Centre the results are in white(which I can't see unless I click on it) any idea of how to fix that?

Regarding the aspect ratio on the screen, how do we go about changing it?

About the netbook, what is "UEFI is a whole new ball game"?

---

### Post by Bashing-om on 2014-10-04
tequiladave-n; Hey !


IF the NetBook, is  of recent manufacture, and Win8 was originally installed then:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

On the desktop, still with white text on white background in terminal, after the updates have completed ?
Else yeah, we can make some edits and change the background color, for instance,

Desktop resolution:
see: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Post back the output of terminal command:
```

xrandr --verbose

```
And let's make sure nothing has changed from  that last.
Please use code tags for these outputs, as it maintains formatting and thus promotes readability.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)


[INDENT][INDENT]we make'n good progress
[/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-10-04
So the netbook is about 4 years old i think and had originally windows XP installed on it, currently running windows 7 but very slow. 1gb ram.

about the command you asked me to run, this is what it returned:
```

david@DavidDesktop:~$ xrandr --verbose
Screen 0: minimum 320 x 200, current 720 x 576, maximum 4096 x 4096
VGA-1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x51
    Timestamp:  22155
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
DVI-I-1 connected 720x576+0+0 (0x65) normal (normal left inverted right x axis y axis) 708mm x 398mm
    Identifier: 0x52
    Timestamp:  22155
    Subpixel:   unknown
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       0
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID: 
        00ffffffffffff001e6d5f565e630400
        0911010380462778ead9b0a357499c25
        11494ba56e00314045406140d1c00101
        010101010101023a801871382d40582c
        4500c48e2100001e1b2150a051001e30
        48883500bc862100001c000000fc0032
        364c433436200a2020202020000000fd
        00324b1c430f000a20202020202001b2
        020321f14e021101031213041405211f
        202210230907078301000065030c0010
        00011d00bc52d01e20b8285540c48e21
        00001e011d007251d01e206e285500c4
        8e2100001e011d80d0721c1620102c25
        80c48e2100009e8c0ad090204031200c
        405500c48e210000184e1f008051001e
        3040803700bc882100001800000000cc
    dithering mode: auto 
        supported: auto, off, on
    scaling mode: Full 
        supported: None, Full, Center, Full aspect
    subconnector: DVI-D 
        supported: Unknown, DVI-D, DVI-A
  1920x1080 (0x55)   74.2MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   33.8KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   30.0Hz
  1920x1080 (0x56)   74.2MHz +HSync +VSync
        h: width  1920 start 2448 end 2492 total 2640 skew    0 clock   28.1KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   25.0Hz
  1920x1080 (0x57)   74.2MHz +HSync +VSync
        h: width  1920 start 2558 end 2602 total 2750 skew    0 clock   27.0KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   24.0Hz
  1920x1080 (0x58)   74.2MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   33.7KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   30.0Hz
  1920x1080 (0x59)   74.2MHz +HSync +VSync
        h: width  1920 start 2558 end 2602 total 2750 skew    0 clock   27.0KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   24.0Hz
  1360x768 (0x5a)   84.8MHz -HSync +VSync
        h: width  1360 start 1432 end 1568 total 1776 skew    0 clock   47.7KHz
        v: height  768 start  771 end  776 total  798           clock   59.8Hz
  1280x768 (0x5b)   80.1MHz -HSync -VSync
        h: width  1280 start 1344 end 1472 total 1664 skew    0 clock   48.2KHz
        v: height  768 start  771 end  778 total  798           clock   60.4Hz
  1280x720 (0x5c)   74.2MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock   45.0KHz
        v: height  720 start  725 end  730 total  750           clock   60.0Hz
  1280x720 (0x5d)   74.2MHz +HSync +VSync
        h: width  1280 start 1720 end 1760 total 1980 skew    0 clock   37.5KHz
        v: height  720 start  725 end  730 total  750           clock   50.0Hz
  1280x720 (0x5e)   74.2MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock   45.0KHz
        v: height  720 start  725 end  730 total  750           clock   59.9Hz
  1024x768 (0x5f)   78.8MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock   60.1KHz
        v: height  768 start  769 end  772 total  800           clock   75.1Hz
  1024x768 (0x60)   75.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1328 skew    0 clock   56.5KHz
        v: height  768 start  771 end  777 total  806           clock   70.1Hz
  1024x768 (0x61)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  832x624 (0x62)   57.3MHz -HSync -VSync
        h: width   832 start  864 end  928 total 1152 skew    0 clock   49.7KHz
        v: height  624 start  625 end  628 total  667           clock   74.6Hz
  800x600 (0x63)   49.5MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  800x600 (0x64)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  720x576 (0x65)   27.0MHz -HSync -VSync *current
        h: width   720 start  732 end  796 total  864 skew    0 clock   31.2KHz
        v: height  576 start  581 end  586 total  625           clock   50.0Hz
  720x480 (0x66)   27.0MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock   31.5KHz
        v: height  480 start  489 end  495 total  525           clock   60.0Hz
  720x480 (0x67)   27.0MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock   31.5KHz
        v: height  480 start  489 end  495 total  525           clock   59.9Hz
  640x480 (0x68)   31.5MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz
  640x480 (0x69)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   60.0Hz
  640x480 (0x6a)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  489 end  492 total  525           clock   59.9Hz
  640x480 (0x6b)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
  720x400 (0x6c)   28.3MHz -HSync +VSync
        h: width   720 start  738 end  846 total  900 skew    0 clock   31.5KHz
        v: height  400 start  412 end  414 total  449           clock   70.1Hz
TV-1 connected 720x576+0+0 (0x6d) normal (normal left inverted right x axis y axis) 0mm x 0mm
    Identifier: 0x53
    Timestamp:  22155
    Subpixel:   unknown
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       1
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    overscan: 50 
        range: (0, 100)
    hue: 0 
        range: (0, 100)
    saturation: 50 
        range: (0, 100)
    flicker reduction: 50 
        range: (0, 100)
    mode: PAL 
        supported: PAL, PAL-M, PAL-N, PAL-Nc, NTSC-M, NTSC-J
    subconnector: SVIDEO 
        supported: Unknown, Composite, SVIDEO, Component, SCART
    select subconnector: Automatic 
        supported: Automatic, Composite, SVIDEO, Component, SCART
  720x576 (0x6d)   28.7MHz -HSync -VSync *current +preferred
        h: width   720 start  776 end  856 total  960 skew    0 clock   29.9KHz
        v: height  576 start  576 end  588 total  597           clock   50.0Hz
  1024x768 (0x6e)   54.2MHz -HSync -VSync
        h: width  1024 start 1064 end 1200 total 1344 skew    0 clock   40.3KHz
        v: height  768 start  768 end  777 total  806           clock   50.0Hz
  800x600 (0x6f)   32.1MHz +HSync +VSync
        h: width   800 start  840 end  920 total 1040 skew    0 clock   30.9KHz
        v: height  600 start  600 end  604 total  618           clock   50.0Hz
  720x480 (0x70)   25.2MHz -HSync -VSync
        h: width   720 start  752 end  872 total  960 skew    0 clock   26.2KHz
        v: height  480 start  480 end  493 total  525           clock   50.0Hz
  640x480 (0x71)   23.1MHz -HSync -VSync
        h: width   640 start  672 end  768 total  880 skew    0 clock   26.2KHz
        v: height  480 start  480 end  492 total  525           clock   50.0Hz
  400x300 (0x72)   20.1MHz +HSync +VSync DoubleScan
        h: width   400 start  432 end  496 total  640 skew    0 clock   31.4KHz
        v: height  300 start  300 end  303 total  314           clock   50.0Hz
  320x240 (0x73)   14.7MHz -HSync -VSync DoubleScan
        h: width   320 start  344 end  392 total  560 skew    0 clock   26.3KHz
        v: height  240 start  240 end  246 total  263           clock   50.0Hz
  320x200 (0x74)   12.3MHz -HSync -VSync DoubleScan
        h: width   320 start  344 end  392 total  560 skew    0 clock   22.0KHz
        v: height  200 start  200 end  202 total  220           clock   50.0Hz
david@DavidDesktop:~$ 


```

---

### Post by Bashing-om on 2014-10-04
tequiladave-n; OK;

What results:
```

xrandr --output DVI1 --mode 1024x768

```

[INDENT]and we re-adjust from here
[/INDENT]

---

### Post by tequiladave-n on 2014-10-04
I got this returning from the command:
```

david@DavidDesktop:~$ xrandr --output DVI1 --mode 1024x768
warning: output DVI1 not found; ignoring

```

---

### Post by Bashing-om on 2014-10-04
tequiladave-n; Humm;

Will have to scratch my head and do some homework on this as I had expected the 'device' DVI1 to be recognized,


[INDENT][INDENT]I will be back
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-10-04
tequiladave-n; Well,

Try it like this:
```

xrandr --output DVI-I-1 --mode 1024x768

```

[INDENT][INDENT]maybe, maybe yes
[/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-10-04
Whilst the command you sent me worked I believe I probably didn't explain myself very well. The issue I have is like the whole screen is zoomed.

If you notice on the picture on the dropbox link, you can't see the bottom bar, where all the controls are and even the firefox icon is cut on the top edge and on the left hand side edge as well.

[https://www.dropbox.com/s/7mhgcjbppwskkwe/IMAG0740.jpg?dl=0](https://www.dropbox.com/s/7mhgcjbppwskkwe/IMAG0740.jpg?dl=0)

I like the resolution you sent me and I wish to keep it like that so no need to revert the command you sent me previously, just a new command that will allow for the screen to be fully displayed, if you know how of course.

Cheers

---

### Post by Bashing-om on 2014-10-06
tequiladave-n; Good morning ;

Yuk, I failed to 'post' my response from yesterday, here it is belatedly, now.

The only way I know how to effect the display is to change the resolution. I am more than open to learning otherwise.
 
OK, you have both the DVI -1 and the external TV-1 connected for monitors.

Working with DVI -1 at the present time ( remember there is a GUI application available that might be easier to work with, for you), let's try
```

xrandr --output DVI-I-1 --mode 1280x768

```
stepping up the resolution ladder. What  and how is this resolution different that that of "1024x768". In terms of width/height and the the desktop icons.

And to make a resolution permanent we will edit a config file - when we get to that stage ( GUI will do it for us )

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-10-06
Just to clarify, I have no monitor, just the tv connected to the computer.

I have tried the command and there's no noticeable change. If anything I would say it is marginally worse.

---

### Post by Bashing-om on 2014-10-06
tequiladave-n; OK;

> 
Just to clarify, I have no monitor, just the tv connected to the computer.

Just a tad bit confused here as we have shown:
> 
DVI-I-1 connected 720x576+0+0
TV-1 connected 720x576+0+0


But what works for us, works. As the display is marginally worse, let's go in the other direction:
```

xrandr --output DVI-I-1 --mode 832x624

```
Looking for that display resolution that is optimal, before making it "permanent".

[INDENT][INDENT]try try again
[/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-10-06
The TV is connected to the computer via HDMI. I have never had a monitor on this machine since it has been running Linux (4 or 5 Years).

Dropping the resolution made it a lot worse.

Meanwhile I have found this video and I think this might be my problem [http://www.youtube.com/watch?v=YtFKfz2Ptt0](http://www.youtube.com/watch?v=YtFKfz2Ptt0) The problem is that I do not know how to find that on Lubuntu or how to look for it or if it even exists with my video card. I will meanwhile look up LG (my tv brand) fixes for overscan.

---

### Post by tequiladave-n on 2014-10-06
Ok and now I think I might have found some guy teaching how to do it but all seems chinese to me. I am so sorry I am probably not the best pupil you have had. Have a look at the following page, meanwhile I will run the command and see if I can fix it by myself.

[http://www.linkapps.com/hardware/23-ubuntuhdmihtpcoverscan.html](http://www.linkapps.com/hardware/23-ubuntuhdmihtpcoverscan.html)

---

### Post by tequiladave-n on 2014-10-06
So this is what returned from the xrandr --query command

> 
Screen 0: minimum 320 x 200, current 1280 x 768, maximum 4096 x 4096
VGA-1 disconnected (normal left inverted right x axis y axis)
DVI-I-1 connected 1280x768+0+0 (normal left inverted right x axis y axis) 708mm x 398mm
   1920x1080      30.0     25.0     24.0     30.0     24.0  
   1360x768       59.8  
   1280x768       60.4* 
   1280x720       60.0     50.0     59.9  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   720x576        50.0  
   720x480        60.0     59.9  
   640x480        75.0     60.0     59.9     59.9  
   720x400        70.1  
TV-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   720x576        50.0 +
   1024x768       50.0* 
   800x600        50.0  
   720x480        50.0  
   640x480        50.0  
   400x300        50.0  
   320x240        50.0  
   320x200        50.0 


From the GTF command I got the following
> 
david@DavidDesktop:~$ gtf 1280 768 60.4

  # 1280x768 @ 60.40 Hz (GTF) hsync: 48.02 kHz; pclk: 80.67 MHz
  Modeline "1280x768_60.40"  80.67  1280 1344 1480 1680  768 769 772 795  -HSync +Vsync


Now the last step I am really confused as to what to do, can you help?

---

### Post by Bashing-om on 2014-10-06
tequiladave-n; Well, well .


I am very pleaded you are doing your homework in trying to find a solution.

As the Resolution a lot worse - we go 'up" then. I still look at it as "simpler" is better, IF we can make this method work for us.

As to the info from the 1st youtube link .. that is IF one were running the AMD proprietary graphics driver.
Let's look at the graphics situation - again -:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```

2nd link:
Has us using a file, that now-a-days is depreciated - BUT, if we make one, it will be used . That is one possible solution to this, and I admit it may be the better solution. I would prefer a more elegant solution, that is easier to maintain in the future.
We can look and see if that file exists, and consider then if we want to make one up:
```

ls -al /etc/X11/xorg.conf

```

Keep in mind, this is your system, your thought process. My role here is to help - not judge or criticize -  offering  the best advise and guidance I can in a given situation. 


As to :
> 
 I am so sorry I am probably not the best pupil you have had.

Not to sweat that ( an American expression of " do not worry") .. So long as you are willing I also am ! Not to know is not a sin, none of us were born knowing what we know.

This forum also has the mandate to teach ! We do that as the 1st principle !

[INDENT][INDENT]I say again
[INDENT][INDENT]it's buntu
[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-10-06
I just want to add that I now know my graphic card is a Nvidia. Found some guy with the same problem and a solution for Nvidia graphics card. I have installed it but I can't find what he is saying:
"I Have struggled with this problem for longer than I care to say! This  may help if you have a NVidia graphics card, and Ubuntu 14.04. Go to the  Ubuntu software center, search for NVidia drivers and download "Nvidia X  Server Settings". _***Once downloaded, click on the Nvidia icon, and select  x server display configuration. Once there, simply slide the underscan  slider until the desired size is achieved."***_

I can't find the X Server Display Configuration. Can this be because I don't have the most current version of the drivers? Or maybe not running the proprietary drivers?

---

### Post by Bashing-om on 2014-10-06
> **tequiladave-n said:**
> I just want to add that I now know my graphic card is a Nvidia. Found some guy with the same problem and a solution for Nvidia graphics card. I have installed it but I can't find what he is saying:
"I Have struggled with this problem for longer than I care to say! This  may help if you have a NVidia graphics card, and Ubuntu 14.04. Go to the  Ubuntu software center, search for NVidia drivers and download "Nvidia X  Server Settings". _***Once downloaded, click on the Nvidia icon, and select  x server display configuration. Once there, simply slide the underscan  slider until the desired size is achieved."***_

I can't find the X Server Display Configuration. Can this be because I don't have the most current version of the drivers? Or maybe not running the proprietary drivers?

All are likely. Let's look and see for sure what is:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```
Which will tell the tale.

---

### Post by tequiladave-n on 2014-10-06
From the first command I got this reply
> 
david@DavidDesktop:~$ lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation NV18 [GeForce4 MX 4000] [10de:0185] (rev c1)
    Subsystem: XFX Pine Group Inc. Device [1682:2017]
    Kernel driver in use: nouveau


from the second command i got:
> 
  *-display               
       description: VGA compatible controller
       product: NV18 [GeForce4 MX 4000]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: c1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=32 maxlatency=1 mingnt=5
       resources: irq:16 memory:ec000000-ecffffff memory:e0000000-e7ffffff memory:ed000000-ed01ffff



---

### Post by Bashing-om on 2014-10-06
tequiladave-n; Good !

We know now the graphic card that is on your system, and we know that you are running the open source driver "nouveau".
Overall, the system looks to be happy with that .. we just need to tweak a bit,
OK, to that end I intend to reboot into my 14.04 (L)ubuntu install - at my earliest - and see what we can do from the provided GUI display application .

That "might" be the easiest way to proceed to change that resolution to a better fit.

Else, well, we can see what we can do to load up a proprietary driver;
1st from the Additional Drivers utility -> none available ? Then see if that card is now relegated to "legacy status" by Nvidia. In the case Nvidia no longer offers support, we will have to use the open source driver.

[INDENT][INDENT]as around and round we go
[/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-10-06
No worries, my television allows me to move the picture up and down and left and right by offsetting it, I will have to do that till we find a solution.

By the way I have successfully installed Lubuntu in 2 other laptops at home, well the netbook and my GFs old laptop!!!

---

### Post by Bashing-om on 2014-10-06
tequiladave-n; Great !

That relieves the sweat. that the system as installed is "usable" .
Pleased also that 'buntu is your operating system(s) of choice. IMHO 'buntu, the best thing since sliced bread.

I will advise when I am able to reboot into my  (L)ubuntu.

[INDENT][INDENT]we will fumble through this, together
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-10-06
tequiladave-n; Re-booting ->

At this time. As soon as I am done poking about I will be back .

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-10-06
tequiladave-n; Hey !

Regret if I left you hanging - While I was in (L)ubuntu I decided to do the updates and yeah - kernel updates broke my grub and am unable to boot !
I continue to work on (RE-)installing grub,

To your situation, I did look.
Main menu ( lubuntu icon) at far left -> Preferences -> Monitor Settings -> resolution.
From there what results when you change the resolutions ? I found no way to test but to "apply" and reboot to see the actual result.
The good thing is that I can change the resolutions from this application.

It is the easier thing to try
[INDENT][INDENT]maybe easy does it ?
[/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-10-07
Not hanging around waiting, I a m in the uk, I went to bed ahahaha.

Unfortunately I had tried that before, even though I tried again and it doesn't solve my problem.

The issue is the television, I believe, that overscans the signal. Usually televisions have a setting but mine doesn't, that will allow to automatically correct that but since it doesn't then there are people correcting that through software/drivers but I can't seem to find a way.

Another thing is that every time I reboot the resolution goes down and I have to run the command from the terminal, any way to set that as the working resolution?

---

### Post by Bashing-om on 2014-10-07
tequiladave-n;

Understood.

You are running the opensource driver, and the tools are not available that you see when the proprietary driver is installed. IF we can not get a acceptable resolution with the open source driver, we can look about seeing if that graphics card has Nvidia's continued support.

If we do find a suitable resolution then yes we will make it a permanent thing - I presently suspect we can make that happen by editing the ~.xinitrc file.
Open source:
The only other tool, besides "Monitor Settings" is 'xrandr' and "see" what we can do with that tool. We continue to use 'xrandr' and try various resolution settings, and if/when found make that setting permanent by editing particular files to suit the environment you are operating in. When we get to that stage we will explore what the options are to make the resolution setting permanent, such that a manual setting each time you boot will not be required.

There is bunches I do not know, but this is true; deviating from a default install ( open source ) has it's risks and the responsibility to maintain those changes in no longer ALL automagic and many times falls on you, the user, to manage them. Not a long term good thing. Do the gains outweigh the risk ?

IF that is the only way to get an acceptable resolution, then yeah we go that route.

[INDENT][INDENT]just my thought, the way I think
[/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-10-07
The thing is I never had this issue with Xubuntu so I guess the solution is out there... I just need to keep looking, me and you, if you like the challenge of course.

---

### Post by Bashing-om on 2014-10-07
tequiladave-n; Welp;;

We keep on this 'till ! 

What is "under the hood" in (L)ubuntu is the same as (X)ubuntu -> same same kernel. Only differences are the desktop and installed applications. I would think if you were to install 14.04 (X)ubuntu the resolution situation would be the same.

My suggestion at this time remains the same. Try higher resolution setting using the tool 'randr' and see what results. IF acceptable, we edit the required file to make it permanent.

When no good resolution can be obtained with 'randr' then we explore the proprietary drivers that "might" be available in the software repository.

[INDENT]a logical progression of thought
[/INDENT]

---

### Post by tequiladave-n on 2014-10-07
Hi,

On my search for a fix I came across this page [http://filthypants.blogspot.co.uk/2013/03/xrandr-overscan-fix-for-intel-hd4000.html](http://filthypants.blogspot.co.uk/2013/03/xrandr-overscan-fix-for-intel-hd4000.html) have a look and tell me what you think!!! I think it might be towards the solution for the problem.

I have been trying new resolutions and it doesn't work. it gets to 1960x1080 and the bottom bar disappears again.

I have ran the command
```

xrandr --output HDMI2 --transform 0.95,0,-52,0,0.97,-35,0,0,1

```

But whilst it brings the icons inwards which is good, moves the bar down and out of sight but it is towards the right path

---

### Post by Bashing-om on 2014-10-07
tequiladave-n; Hey;

That link does look to have a very promising solution.
Try it and see what results ( --transform ) .. Play with the numbers and see what you get, Just remember the last numbers  (0, 0, 1) are a constant. Do not change them.

To save me booting into (L)ubuntu, does the 'lightdm.conf' file exists on you system ?
```

ls -al /etc/lightdm/lightdm.conf

```
as I know that lubie uses lightdm as the display manager. If so, that is the file we will use to make the resolution setting a permanent thing, once we know what the better setting is.

[INDENT][INDENT]still making progress
[/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-10-07
That returned this:
```

david@DavidDesktop:~$ ls -al /etc/lightdm/lightdm.conf.
ls: cannot access /etc/lightdm/lightdm.conf.: No such file or directory


```

---

### Post by Bashing-om on 2014-10-07
tequiladave-n; Humm ?? surprised;

But not dismayed. How about:
```

ls -al .xinitrc

```

I need to boot into my lubie and 'play' with the boot code, will at that time explore what else we might use for the resolution config.

By the thought way:
remember:
> 
DVI-I-1 connected 720x576+0+0
TV-1 connected 720x576+0+0


Might play about with the 'TV-1' device and see if there is any effect.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-10-07
That is what the command returned

> 
david@DavidDesktop:~$ ls -al .xinitrc
ls: cannot access .xinitrc: No such file or directory


---

### Post by Bashing-om on 2014-10-07
tequiladave-n; Thanks

For that --- looks like I will have to go hunting for a config file, between now and then ... I can do that.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-10-08
tequiladave-n; Hey !

typo on my part !
the file and path should be"
```

ls -al /etc/lightdm/lightdm.conf

```
I had instructed a '.' at the end of "conf" .. so yeah, in that construct the file "lightdm.conf." in fact does not exist, BUT "lightdm.conf" does .. I did go verify the files existence, too me a tic or so to see the error of my ways !
As to:
> 
 xrandr --output [color=red]HDMI2[/color] --transform 0.95,0,-52,0,0.97,-35,0,0,1


I do not think we are messing about with that device; rather TV-1 and/or DVI-I-1 ....I still do not understand why the output of 'randr' shows both connected, as you say there is but the TV connected. Some internals going on there ?

keep poke'n at it 'till something gives

---

### Post by tequiladave-n on 2014-10-08
so the command you asked me to run returned the following:
```

david@DavidDesktop:~$ ls -al /etc/lightdm/lightdm.conf
-rw-rw-r-- 1 root root 119 Oct  4 23:18 /etc/lightdm/lightdm.conf


```

regarding the other code I replace HDMI2 by DVI-I-1

I have been trying different settings and I can't suss out what does what just end up making loads of odd changes and have to end up restarting the machine to revert it all back to the starting point. Not sure where to go from here but I know that might be the solution, just can't figure it out

---

### Post by Bashing-om on 2014-10-08
tequiladave-n; Hi !

I too feel like you are on the right path. As I do not have a TV as a monitor I can not test.

At least, when the acceptable resolution is found we know the file to add the 'resolution settings' to make it stick.

Hang in there and keep trying, rebooting and so forth.


[INDENT][INDENT]will come out in the end
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-10-08
tequiladave-n; Hey :

When all else fails read the instructions:
```

man xrandr

```
And we see instructions for the matrix:
> 
 --transform a,b,c,d,e,f,g,h,i
              Specifies  a transformation matrix to apply on the output. Auto&#8208;
              matically a bilinear filter is selected.  The mathematical  form
              corresponds to:
                     a b c
                     d e f
                     g h i
              The  transformation  is  based  on  homogeneous coordinates.
<snip>


and as well,

> 
 --scale xxy
              Changes the dimensions of the output picture. Values superior to
              1 will lead to a compressed screen (screen dimension bigger than
              the dimension of the output mode), and values below 1 leads to a
              zoom in on the output. This option is actually a  shortcut  ver&#8208;
              sion of the --transform option.

       --scale-from wxh
              Specifies  the  size in pixels of the area of the framebuffer to
              be displayed on this output.  This option is actually a shortcut
              version of the --transform option.


explore these and see where we go.

[INDENT][INDENT]if at first we do not succeed
[INDENT][INDENT][INDENT]we try something else
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-10-12
Hi, Bashing-OM unfortunately I have been feeling poorly and bed bound due to a terrible lower back pain. Meanwhile I have been trying to play with this transform command to no luck, still nowhere closer to a solution.

I have also tried installing a different distro which my neighbor is running which is Linux Mint but that didn't work either so right now I am not sure where to go with this. I thank you for your time and all your support but I think I am going to try to make do with what I have at the moment till I can figure out a better solution (maybe buy a new tv or install Nvidia drivers).

Is there a way to set the current resolution as the set resolution so I don't need to run the command to revert it back to the current resolution? every time I restart the machine I need to run the command from the terminal.

Kind Regards

---

### Post by Bashing-om on 2014-10-12
tequiladave-n; Welp,

Sorry to hear of your pain .. I too suffer from a "bad" back, and on occasion I must resort to doing back exercises   to get that disk back in place.
I spend hours setting before this terminal, and I must have a "lumbar roll" in this chair to conform my back. Else, yeah that disk slips back out of place.

When things do not work as expected, then yeah can be trying to say the least to make things work.
We can make the resolution change "stick" by editing the " /etc/lightdm/lightdm.conf " file.

Post back the command you are presently doing to effect the resolution change and I can further advise what edit to make to the file.

If we are unable to get satisfaction applying 'xrandr' with the open source driver, we can explore and see if the Nvidia card still has support from Nvidia. There are additional tools available with the proprietary driver - if a proprietary driver is available !

There are a number of distributions out there that support older hardware; like knoppix and crunchbang for instance. Very possible will have better results from them.

[INDENT][INDENT]all I know to do is try
[INDENT][INDENT][INDENT]and then try something else
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-10-12
This is the code I am currently using:
```

xrandr --output DVI-I-1 --mode 1280x768


```

I think it's sciatica that I am suffering with...

---

### Post by Bashing-om on 2014-10-12
tequiladave-n; Hey;

To make this mode stick:
edit " /etc/lightdm/lightdm.conf " :
```

sudo cp /etc/lightdm/lightdm.conf /etc/lightdm/lightdm.conf-orig
gksudo gedit /etc/lightdm/lightdm.conf

```
add at the bottom of the file:
```

display-setup-script=xrandr --output DVI-I-1 --mode 1280x768

```

reboot and let's see if that is effective.
I also ran across this nice tutorial:
[http://ubuntuforums.org/showthread.php?t=1370258](http://ubuntuforums.org/showthread.php?t=1370258)

That might prove to be of interest.

[INDENT][INDENT]try'n to help
[/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-10-12
Hi,

I believe something was odd with that editing command you sent, see below all the commands and the replies:
```

david@DavidDesktop:~$ sudo cp /etc/lightdm/lightdm.conf /etc/lightdm/lightdm.conf-orig
[sudo] password for david: 
david@DavidDesktop:~$ gksudo gedit /etc/lightdm/lightdm.conf
david@DavidDesktop:~$ display-setup-script=xrandr --output DVI-I-1 --mode 1280x768
display-setup-script=xrandr: command not found
david@DavidDesktop:~$ 


```

---

### Post by Bashing-om on 2014-10-12
tequiladave-n; Welp !!

What you are going to do is open the file in the text editor;
THEN copy and paste the line " display-setup-script=xrandr --output DVI-I-1 --mode 1280x768 " to the bottom of the file.
save the file in your text editor and exit back to terminal.

NOW log out - and log back into the desk top .. rebooting though clears all memory, better to reboot in may cases.


It is what is called
[INDENT][INDENT][INDENT]editing a file[/INDENT][/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-10-12
But and pardon my ignorance how do I open the file in the text editor? When  I run the command it asks for my password but nothing shows up.

---

### Post by Iowan on 2014-10-12
I haven't read all 112 posts, so I may have missed something.
When you enter a password, there will be no echo to the screen - it's a security feature.

---

### Post by Bashing-om on 2014-10-12
tequiladave-n; Iowan; Yikes !

Think I am the victim of 'tunnel vision" once more. I bet "gedit" is not the editor installed on the system.
(L)ubuntu is it not ?
Then is not 'leafpad' the default editor ?
Then:
```

gksudo leadpad /etc/lightdm/lightdm.conf

```

Maybe also - in my hazy memory, one had to start leafpad, right click on the file and choose "open as root" (???) .

Let's see what is
[INDENT][INDENT][INDENT]and what works
[/INDENT][/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-10-13
Well that worked, thank you very much. Now I am trying to teach myself how to get all the computers in this house on the same network so I can abolish memory sticks to get films and files from one computer to another... I know I know it is probably really easy but since I have windows and linux computers... it is not that easy for me.

---

### Post by Iowan on 2014-10-13
For a mixed environment (Linux and Windows), you'll probably be using Samba.

---

### Post by Bashing-om on 2014-10-13
@tequiladave-n ; Good deal;

samba is the subject of another thread, I do not use Windows, and have no familiarity with samba.
Others will advise better in this context.

@Iowan; Appreciate that you guide, guard and direct the forum and that you have my back.

[INDENT][INDENT]where do we go from here
[/INDENT][/INDENT]

---

### Post by tequiladave-n on 2014-10-13
I did use Samba and managed to link up linux and windows using a tutorial I found online but whilst I am ok opening files from my linux machine on my windows computer, I can't open the Windows files on my Linux machine, at least on VLC

All I want to do is to open video files I might download on either of the two machines and watch it from any of the two.

---

