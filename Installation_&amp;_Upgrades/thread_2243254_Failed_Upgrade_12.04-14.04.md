---
title: "Failed Upgrade 12.04-14.04"
date: 2014-09-07
forum: Installation &amp; Upgrades
---

### Post by wg5o on 2014-09-07
I’ve happily used used 12.04 for a very long time, but Update Manager kept offering 14.04, and I caved in and punched Upgrade.  Big mistake!  It all seemed to go smoothly.  It asked a few questions and I tried to pick the answer it seemed to want.  When it came time to reboot, my Desktop background came up, with my name and password box.  But it wouldn’t accept my password.  I tried login as a guest.  No good.  Both cases say, “Failed to start session.”  Win XP is on a 2nd HD, and it starts and runs fine (whoopee).

1.   I can’t get to Terminal.  Ctrl+Alt+t does nothing.  Rt. click to the Desktop does nothing.

2..  Ctrl+Alt+F1 gets me into tty1, and I can log in there.

3..  Also, a new feature of Grub, “Advanced options for Ubuntu,” offers a lot of items, including root.  At the root shell prompt, I can log in, but don’t have a clue what to do next.   I need guidance before doing more.

Andy in San Antonio, TX

---

### Post by Bashing-om on 2014-09-07
wg5o; Well,

There are a couple of things here we need to verify;
a) Did the upgrade complete successfully ? 
From the "Ctrl+Alt+F1 gets me into tty1"
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg -C

```

Now IF that all returns in a positive light, there is 
b) Look at authorizations to the /home directory:
```

ls -al .Xauthority
ls -al .ICEauthority
ls -al /home
groups

```

[INDENT][INDENT]maybe as esay as 
[INDENT][INDENT][INDENT]1-2-3
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wg5o on 2014-09-07
Thank you, but it didn't work.  

Step a) set off a long, orderly looking installation process that took hours.  When I did step b) "ls -al .ICEauthority" didn't work; it said "No such file or directory."  Anyway, I can't say that I understood much of the step b) results, but I didn't see anything worrying.  F7 out, restart, no change.  I worried that I missed the last step of a), so I did a) over, and it went rather quickly.  F7 out, restart, no change.

My case seems different from similar problems that I found on line in that I can't get to Terminal.

Thanks again.

Andy

---

### Post by glennbates on 2014-09-07
I have had problems after upgrading also. Wish I hadn't have. I feel like this was designed by Apple or Microsoft.

---

### Post by Bashing-om on 2014-09-07
wg5o; OK;

Let's start finding out where the failure is:
Post back the outputs - Between code tags - of the terminal commands from step a.
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg -C

```
to insure the package manager is in a consistent state.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Depending on what is seen by those is what we do next.

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT][INDENT]it's fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ibjsb4 on 2014-09-07
Hay Bashing, I wonder what desktop environment was wg5o running in 12.04?  Unity 2D, 3D, something else?

---

### Post by kansasnoob on 2014-09-08
If you have any Ubuntu live media (even an older version) it would be good to see some basic hardware info:

```
cat /proc/cpuinfo | head -10
```

```
lspci -v -s `lspci | awk '/VGA/{print $1}'`
```

```
free -m
```

---

### Post by axm- on 2014-09-08
Hello i have a little problem with my system.  I can't update it and i can't install nothing
The error is:
> W:Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources](http://mk.archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources](http://mk.archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources)  404  Not Found
, W:Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources](http://mk.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources)  404  Not Found
, W:Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources](http://mk.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources)  404  Not Found
, W:Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages](http://mk.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages](http://mk.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages](http://mk.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages](http://mk.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources](http://mk.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources](http://mk.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources)  404  Not Found
, W:Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources](http://mk.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources)  404  Not Found
, W:Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources](http://mk.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources)  404  Not Found
, W:Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages](http://mk.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages](http://mk.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages](http://mk.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages](http://mk.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources](http://mk.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources](http://mk.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources)  404  Not Found
, W:Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources](http://mk.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources)  404  Not Found
, W:Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources](http://mk.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources)  404  Not Found
, W:Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages](http://mk.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages](http://mk.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages](http://mk.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages](http://mk.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.
Do You know how do i fix it? 
i have no hope anymore :(

---

### Post by kansasnoob on 2014-09-08
> **axm- said:**
> Hello i have a little problem with my system.  I can't update it and i can't install nothing
The error is:

Do You know how do i fix it? 
i have no hope anymore :(

You really need to start a new thread rather than hijacking this one but it looks like you're running Quantal which is EOL:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

About the only thing you can do is install a supported version like Trusty.

---

### Post by Bashing-om on 2014-09-08
wg5o; IRT;

> **ibjsb4 said:**
> Hay Bashing, I wonder what desktop environment was wg5o running in 12.04?  Unity 2D, 3D, something else?

Good thought ! Graphics is always a top priority .

[INDENT][INDENT]a process of fault isolation
[INDENT][INDENT][INDENT]to restoration
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-09-08
wg5o; IRT ;

> **kansasnoob said:**
> If you have any Ubuntu live media (even an older version) it would be good to see some basic hardware info:

```
cat /proc/cpuinfo | head -10
```

```
lspci -v -s `lspci | awk '/VGA/{print $1}'`
```

```
free -m
```

Yepper, Gotta have the hosses !

[INDENT][INDENT]we gang up on this thing,
[INDENT][INDENT][INDENT][INDENT]and knock it out
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wg5o on 2014-09-09
A family obligation will limit my computer time during the next 10 days, but I can (sort of) answer re desktop environment:  I don't know.  It is whatever 12.04 came with when I upgraded to it years ago.  However, Update Manager frequently gave me lists of updates, which I proceeded to install (an act of faith).  So, if a change was sent down, that is what I have.

Thanks,

Andy

---

### Post by Bashing-om on 2014-09-09
wg5o;Hey;

We will work around those other obligations you have.

as to the present. Provide us the requested outputs of ALL those terminal commands. That gives us something solid to base any  instructions on.
Please use "code tags" .. makes thing so much easier to read and understand:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And we start the process of getting all things set to right.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-09-09
Thank you.  I've got the code tag thing, that is great.  Where I'm stuck is how to transfer the large amount of code from the jammed-up computer to this one, a little Asus running an old version of Puppy.  Tty1 doesn't seem to work like terminal; there is no mouse, and I don't even know how to see the above the top of the screen.  Sorry I'm so ignorant.  Actually, Ubuntu has worked so well that I've had little need to even go to terminal.

Andy

---

### Post by Bashing-om on 2014-09-10
wg5o; Hello !

The light also dawns on me how difficult this must be on you. It has bem a long day here for me and I am past reliable thinkability at this point.
I will give consideration to this and get back with you in my PM ( about 15 hours hence ).
And hey, to be ignorant is not a sin .. ignorance is easily cured.

We will just have to see what we can do, to work with what we have.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-09-10
wg5o; Hello ! Right on time for me !

OK, ya got access to a usb thumb drive ? I have in mind one solution.
We can write the command's outputs to text file(s), 
and copy those files to the thumb drive - puppy box does support USB drive, yes ? -
And then from the puppy box transfer the files to the post.

If this is doable on your part, I will be more than happy to formulate the procedure.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-09-10
I have the thumb drive, a brand new one.  If Puppy doesn't work, I can use my wife's almost new Mac, though it does strange things.  Lay it on me.  I feel helpless in the tty1 thing.   Day after tomorrow, I will disappear until Sept. 21.

Many thanks,

Andy

---

### Post by Bashing-om on 2014-09-10
wg5o; OK;

Here is one way to so this:
From the terminal:
```

sudo apt-get update > upgrade.txt
sudo apt-get upgrade -y >> upgrade.txt
sudo apt-get dist-upgrade -y >> upgrade.txt
sudo apt-get -f install >> upgrade.txt
sudo dpkg -C >> upgrade.txt

```
That for the 1st upload file.

For ibjsb4's request:
```

echo $DESKTOP_SESSION > desktop.txt
lspci -nnk | grep -iA3 vga >> desktop.txt
sudo lshw -C display >> desktop.txt

```
For  kansasnoob's request:
```

cat /proc/cpuinfo | head -10 > hardware.txt
lspci -v -s `lspci | awk '/VGA/{print $1}'` >> hardware.txt
free -m >> hardware.txt

```

Redirecting to files rather than the terminal for the outputs, there will be nothing on the screen when the commands are executing. Apply patience, and when the prompt returns execute the next command in the series. The 1st '>' direction character creates the file, and the ">>" appends the other outputs to that file.

OK, now that the files are created, we need to copy them off to the USB,
To do that we need to mount that thumb drive from terminal.
To do that we must have a file system on the thumb drive, and a partition(directory) to write the files too.

Let's look and see what we have to work with.
With the USB thumb drive plugged in what returns:
```

sudo fdisk -lu

```
Depending on what is on the thumb drive presently, we may have to make up a "transfer" directory for our use. I can foresee a bit of fumble-ing about to make this happen.

For now, this is enough to keep us busy 'til we know more about the USB thumb drive. Then will provide the means to copy the requested files onto the thumb drive.

[INDENT][INDENT][INDENT]I say again, where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by wg5o on 2014-09-10
This looks very educational, but maybe it is time to cave in.  

I did a "Back in Time" backup of my files, on an external HD, before pushing the Upgrade button, so is there an alternate path?  It will mean some work to get my files back, but, so it goes.  I looked through my old CDs and found, "Ubuntu 7.04, bootable," and "Ubuntu 8.04.1, 32bit, desktop -386."  By the way, I have been using 32 bits, because of some forgotten problem with 64 bits. The computer was locally assembled in 2007, and has an Asus A8V-VM SE circuit board with a  2.20 GH AMD Athlon 64 processor.  It has been retrofitted with a wi-fi board and Nvida vidio card.  

I'm grateful and impressed with the amount of work you have done on my account.   Whichever way we go, I think it will have to wait until after 9/21.  

Andy

---

### Post by Bashing-om on 2014-09-10
wg5o; Well;

My attitude to backups - I do it weekly- Is I back up my personal files only( a script to do so). There is no need to backup any system files as they are readily available and in the event of a serious problem - (RE-)install the operating system. I can, and have, (RE-)installed in about 20 minutes, then with a fast internet connection, updated in 15 minutes more.  I personally keep a "change-log" of all changes I make to the system, and again is but a matter of minutes to have my system exactly as It was.

There are a few tips and tricks round to use in a heavily modified system.

Now that said, I have no knowledge of "Back in Time" . I do not know what would be involved in the restoration process, All I can advise is try it and see. There is always the ability to backup your personal data and do a clean fresh install, then copy your files back onto the new install. One should always keep a liveDVD on hand for the system installed ( yeah, yeah, I have been caught with my own pants down, too).

All depends on how much trouble and aggravation in the choice one makes to resolve the problem, one chooses to exert. The choice is up to you, and what you want to do. We are here to assist, and guide. It can be a good learning experience, and bring you closer to your operating system of choice ( ubuntu !)

[INDENT][INDENT]it is all in the care and feeding
[INDENT][INDENT][INDENT]of your 'buntu
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kansasnoob on 2014-09-10
> **wg5o said:**
> This looks very educational, but maybe it is time to cave in.  

I did a "Back in Time" backup of my files, on an external HD, before pushing the Upgrade button, so is there an alternate path?  It will mean some work to get my files back, but, so it goes.  I looked through my old CDs and found, "Ubuntu 7.04, bootable," and "Ubuntu 8.04.1, 32bit, desktop -386."  By the way, I have been using 32 bits, because of some forgotten problem with 64 bits. The computer was locally assembled in 2007, and has an Asus A8V-VM SE circuit board with a  2.20 GH AMD Athlon 64 processor.  It has been retrofitted with a wi-fi board and Nvida vidio card.  

I'm grateful and impressed with the amount of work you have done on my account.   Whichever way we go, I think it will have to wait until after 9/21.  

Andy

You would not want to install either 7.04 or 8.04 because they're both long past EOL. So if you're going to perform a fresh install I'd say it's best to try a fresh install of 14.04.1. The only two Ubuntu options really are Precise or Trusty:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

To take things even a bit further, those who do want or need Precise need to be aware of LTS HWE:

[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Installing Precise with either the 12.04.2, 12.04.3, or 12.04.4 images will land a user in HWE EOL with an unsupported kernel:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A12.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A12.04.x_Ubuntu_Kernel_Support)

Those who install using the latest 12.04.5 images will be on the Trusty HWE stack anyway so they might as well give Trusty a try.

Those who require an older kernel or X stack can get the original 3.2 series kernel and matching X stack (which is supported until April 2017) only by installing with the archived 12.04 or 12.04.1 images:

[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)

Also, if this is a dual-boot you need to be aware of this horrible bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

Have I confused you yet?

---

### Post by wg5o on 2014-09-10
Thank you.  I'll think on it and address the problem when I have more time.  One day, with other things going on, will not do it.

Thank you again,

Andy

---

### Post by kansasnoob on 2014-09-10
> **kansasnoob said:**
> If you have any Ubuntu live media (even an older version) it would be good to see some basic hardware info:

```
cat /proc/cpuinfo | head -10
```

```
lspci -v -s `lspci | awk '/VGA/{print $1}'`
```

```
free -m
```

If you were to use one of those old live CD's in the live environment and post the output of those three commands we might be able to recommend which version and flavor of Ubuntu would possibly work best for you. No guarantees mind you, but it would give us some idea.

---

### Post by wg5o on 2014-09-11
I plugged the thumb drive in  to the Puppy box, where there is a real Terminal that I can copy and paste.  It didn't know sudo, but here is what "fdisk -lu" returned:


```

Disk /dev/hda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders, total 16514064 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    11261564     5630751   83  Linux
/dev/hda2        11261565    16498754     2618595   82  Linux swap

Disk /dev/sda: 7876 MB, 7876902912 bytes
256 heads, 39 sectors/track, 1540 cylinders, total 15384576 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          32    15384575     7692272    c  W95 FAT32 (LBA)
# 

```

Andy

---

### Post by Bashing-om on 2014-09-11
wg5o; Whoahh ;


Hey, hey, making progress. You did good !

"sudo" is SUper user DO . Where to execute and operate with the elevated privileges of the administrator you tell the system who you are.
Precede a directive with "sudo", will ask for your password to insure you are who you say you are, and you now have that access.

How old is this machine we are working with ? Think Kansas is on the right track here ! Bet you do not have the horse power to run the top-of-the-line ubuntu !

We see for the hard drive:
8455 MB -> somewhat less than 81/2 Gigs
/dev/hda1 -> where 'hda' is the old IDE interface 
"assuming" this output is not off the Puppy box.

We best await the remainder of the requested outputs before jumping to conclusions and making an erroneous advisement.

[INDENT][INDENT]even this
[INDENT][INDENT][INDENT]we can work through
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wg5o on 2014-09-11
Oops.  I thought you were just interested in the thumb drive.  It is the last entry, above.  The other stuff is for my little bitty Puppy box.   The only way I have to transfer data from my primary computer is to copy it by hand, walk down the hall to this box, and enter it.  I did check that the thumb drive gives the same output on the locked-up computer.  As I previously mentioned, it was locally assembled in 2007.

Here is what I guess is the main info for the primary, locked computer:

```

sudo fdisk -lu
password for andy

Disk /dev/sda: 164.7 GB
       /dev/sda1 ... HPFS/NTFS/exFAT
      
Disk /dev/sdb: 40GB
       /dev/sdb1 ... Linux
       /dev/sdb2 ... Extended
       /dev/sdb5 ... Linux swap/Solaris

```

Ubuntu 12.04 ran just fine, except that, after years of operation, it choked up with accumulated junk.  I found a set of instructions that allowed me to clean it out and get back to normal operation.  The last time I checked, I had plenty of remaining HD space. (I'm an old man; I don't collect music, etc.)

Andy

---

### Post by Bashing-om on 2014-09-11
wg5o; Hey;

I too can wig out ! // OK, so we looking to be good on the dual boot box.
Trying to see what it will take to transfer the requested files to the thumb drive:
OK, we know that the 1st hard drive 'sda' contains Windows, the 2nd hard drive ' sdb' is the ubuntu install.
Boot back to ubuntu's terminal on the crippled system and once booted, plug in the USB thumb drive
What now results from the terminal command:
```

sudo fdisk -lu

```
Is the USB thumb drive recognized now as 'sdc" ??
And is it correct that the USB thumb drive is this " 32    15384575     7692272    c  W95 FAT32 (LBA) " ??

Then we look and see what is to be done to mount the thumb drive from terminal.

Are you also aware, that from the liveDVD, it is a very simple process to relay the requested outputs ? Then would not have to utilize the intermediary thumb drive.

[INDENT][INDENT]there are those times, I do not know
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-09-21
I'm back.  I was very sorry to let this laps, but we had a planned steamboat trip, St. Louis to St. Paul.  Here are some answers:

[QUOTE=Bashing-om;13120166]wg5o; Hey;

"What now results from the terminal command:
```

sudo fdisk -lu

```
"Is the USB thumb drive recognized now as 'sdc" ??

Answer: YES

"And is it correct that the USB thumb drive is this " 32    15384575     7692272    c  W95 FAT32 (LBA) " ??"

Answer: YES

"Then we look and see what is to be done to mount the thumb drive from terminal"

Please NOTE:  I'm in tty1.  I can't get to terminal.

---

### Post by wg5o on 2014-09-21
I started on the commands listed in #18.  After the second one, I got:

"Warning: Current package is openjdk-7, but binary format already installed by openjdk-6."

Proceed?

---

### Post by Bashing-om on 2014-09-21
wg5o; OK,
Let's see what we can do:

from the TTY1 terminal:
```

sudo mkdir /mnt/work
sudo mount /dev/sdc1 -t vfat -o umask=000 /dev/sdc1 /mnt/work
ls -al /mnt/work ##maybe permissions issues ??

```
IF that 'ls' command returns positive, we are in business !
Now, as we manually mounted the USB drive we are responsible to UN-Mount it; Once all operations are completed:
```

sudo umount /mnt/work

```

[INDENT][INDENT]making progress
[/INDENT][/INDENT]

Edit: looking back at post #18 .

---

### Post by Bashing-om on 2014-09-21
wg5o; Yeah !

IRT post #18, proceed. We do want to see those errors that the system generates and in the context of the commands that generated them.

Then we work on getting those generated files onto the USB thumb drive to transfer to the thread from the puppy install.

[INDENT][INDENT]whewhh !
[INDENT][INDENT][INDENT]what a way to do things
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wg5o on 2014-09-21
It says: "srwxr-xr-x 2 root root 4096 Sept. 21 19:00
             "srwxr-xr-x 3 root root 4096 Sept. 21 19:00"

---

### Post by Bashing-om on 2014-09-21
wg5o; Well !

Root still owns the mount ?? goes to show what I do not know about Windows' file systems !

OK;
what returns:
```

sudo ls -al /mnt/work

```
looking for the place to copy files to .

[INDENT][INDENT][INDENT]one way or another
[/INDENT][/INDENT][/INDENT]

---

### Post by wg5o on 2014-09-21
sudo ls -al /mnt/work

It says the same thing.  But, I failed to say the quote was proceeded by "Total 8."

"Total 8
" drwxr ... " etc.

---

### Post by Bashing-om on 2014-09-22
wg5o; Humm ??

Surprising that there is nothing been written to the USB drive ??
Let's set up a directory on the USB drive.
If we can set up the directory, we can copy files to it !
```

sudo mkdir /mnt/work/save

```

As I have said, we 
[INDENT][INDENT]fumble our way through this
[/INDENT][/INDENT]

Edit: I failed to post this last - my last night, sorry about this delay !

---

### Post by wg5o on 2014-09-22
> **Bashing-om said:**
> wg5o; Humm ??

"```

"sudo mkdir /mnt/work/save

```"

Answer: It just swallowed that and returned to the prompt.

"Edit: I failed to post this last - my last night, sorry about this delay !"

Where the heck are you?  It sure ain't Arkansas.

---

### Post by Bashing-om on 2014-09-22
wg5o; Yeah !

> 
Where the heck are you? It sure ain't Arkansas.

I sometimes wonder !

OK, as to the 'mkdir' command, yep, if it did as told, will see no response ( no sas, no back talk, just doing as told )..
Let's look and see what it did:
```

ls -al /mnt/work/

```
and we should now have a directory, 'save' .
Ready now to move some files into the 'save' directory ?

[INDENT][INDENT][INDENT]guilty;
[INDENT][INDENT][INDENT]scatter-brained as charged
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wg5o on 2014-09-22
It says:

total 12
drwxr-xr-x 3 root root 4096 Sept 22 15:35 .
drwxr-xr-x 3 root root 4096 Sept 21 19:00 ..
drwxr-xr-x 2 root root 4096 Sept 22 15:35 save

I've been waiting to see how we save the files to the drive.  In tty1, I can't move around, go up page, or find work previously done.  I suppose I need to go back to #18, and enter those commands?

---

### Post by Bashing-om on 2014-09-22
wg5o; Yepper !

Look'n good !
> 
I've been waiting to see how we save the files to the drive. In tty1, I can't move around, go up page, or find work previously done. I suppose I need to go back to #18, and enter those commands?

Yes, now we are ready to make up the files to copy to the USB drive.
Do as directed in post #18 and ->
With the USB drive mounted in terminal in TTY1 ->
```

cp upgrade.txt /mnt/work/save
cp desktop.txt /mnt/work/save
cp hardware.txt /mnt/work/save

```
If you get permission issues ( possible as the directory 'save' is grouped and owned by "root" ) precede the commands with "sudo" to make it happen.

OK, now that the files are on the USB drive, here in the thread use the paper clip icon to 'attach' the files to your post.
We read those files and now we have a good idea of what is going on with your system !

[INDENT][INDENT]even after all this time
[INDENT][INDENT][INDENT]still making progress
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wg5o on 2014-09-23
Re #18 I think that I succeeded in creating the first two files, upgrade.txt and desktop.txt.  The third one hung-up on the second command; it said the -s is an invalid slot number.  When I took out the -s, it gave me a lecture on mounting.  That didn't help me.

It was not clear, to me, what the status of the thumb drive was/is.  I had kept it plugged in, but the computer has been on and off.  I assumed it was mounted, and entered the cp command after each file, as it was completed.  But, "sudo umount /mnt/work" gave me, "umount: /mnt/work: not mounted."  I was unsure what that indicated, so I took the thumb drive to the Pup and mounted it there,  It looked empty.  After a couple of events like that, I got a thumb drive with known data and opened it w/o difficulty.  In addition, when I plugged the drive back into the faulty box, the drive's light flashes, and the computer seems to get busy writing data.  It says, "no caching mode page found," then, "Assuming drive cache: write through."  It repeats that three times, but gets stuck on the third one.  It does return to the prompt when I hit, "Return."   Whatever, the data isn't going on the thumb drive.

Darn.  I had hoped to get the info to you today, but no luck.

Andy

---

### Post by Bashing-om on 2014-09-23
wg5o; Well, not all bad.

> 
It was not clear, to me, what the status of the thumb drive was/is. I had kept it plugged in, but the computer has been on and off. I assumed it was mounted, and entered the cp command after each file, as it was completedIt was not clear, to me, what the status of the thumb drive was/is. I had kept it plugged in, but the computer has been on and off. I assumed it was mounted, and entered the cp command after each file, as it was completed.

To :
know "what the status of the thumb drive was/is"
```

mount

``` will tell you all the file systems that are presently mounted and where.

Don't think this "I had kept it plugged in, but the computer has been on and off." is a good thing to do at all. Maybe messed up the "lock" ??
One should ALWAYS (UN-)mount what ever was manually mounted prior to shutting the system down, otherwise the system may be left with open files and shutting down in this circumstances can leave the system in an inconsistent state. Maybe now is a good time to check that USB (Windows File System). Can you take the USB drive to a Windows machine and run the Windows chkdsk utility on it ? Then we look at it again on the ubuntu or the puppy machine.

> 
The third one hung-up on the second command; 

I can not say, I see no fault with that command, and it does run on my box. Maybe, you missed that final back tic when you copied the command - that last 'mark' is a 'back tic' ... located at the upper left of an ascii keyboard on the same key as the 'tilde (~)' just below the "Esc" key.

Let's see if those files are present.
Boot the ubuntu install to terminal:
terminal commands:
```

ls -al upgrade.txt
ls -al desktop.txt
ls -al hardware.txt

```

Once Windows has checked the USB drive, we can try again.
We must mount the drive each time it is plugged in ( and UN-mount it prior to un-plugging/ turning the box off )
We have a permanent mount point, so just attach the usb drive to it, thus:
```

sudo mount /dev/sdc1 -t vfat -o umask=000 /dev/sdc1 /mnt/work
ls -al /mnt/work
ls -al /mnt/work/save

```
Where we still see our target directory "drwxr-xr-x 2 [color=red]root root[/color] 4096 Sept 22 15:35 save"  // and a close look at the permissions -> ONLY root has write access ! Someone with greater familiarity to accessing Windows' file system, please correct my code to allow user access !
so we will use 'sudo' on the copy commands !
```

sudo cp upgrade.txt /mnt/work/save
sudo cp desktop.txt /mnt/work/save
sudo cp hardware.txt /mnt/work/save

```
Let's check the results of our efforts:
```

sudo ls -al /mnt/work/save/upgrade.txt
sudo ls -al /mnt/work/save/desktop.txt
sudo ls -al /mnt/work/save/hardware.txt

```
Done copying so now prior to unplugging the USB drive we MUST manually UN-Mount it !
```

sudo umount /mnt/work

```

OK, now we can take the USB drive over to the puppy box and transfer the files to the forum thread.

We are now not in no big rush to do this, and this is time well spent as a learning experience ( even though I do not want to learn about Windows' FAT file system, or ways to access it ) ; we do what we need to do.

So:
[LIST]
[*]do our files exist on the ubuntu install ?
[*]are the files copied to the USB drive ?
[*]Have we got the files transfered to the forum ?
[*]
[/LIST]

all in all
[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-09-24
> **Bashing-om said:**
> wg5o; Well, not all bad.


"To :
know "what the status of the thumb drive was/is"
```

mount

``` will tell you all the file systems that are presently mounted and where."

Got it.  Thanks.

"Don't think this "I had kept it plugged in, but the computer has been on and off." is a good thing to do at all. Maybe messed up the "lock" ??
One should ALWAYS (UN-)mount what ever was manually mounted prior to shutting the system down, otherwise the system may be left with open files and shutting down in this circumstances can leave the system in an inconsistent state."

I'll remember. Thanks.

 "Maybe now is a good time to check that USB (Windows File System). Can you take the USB drive to a Windows machine and run the Windows chkdsk utility on it ? Then we look at it again on the ubuntu or the puppy machine."

I have Win XP on the other drive of the problem box, that's all (wife has a Mac).  To get to XP, I have to restart, and I have been afraid that I would loose my work if I did that; uncertain, I skipped this step.  It is a new thumb drive, never before used.

"I can not say, I see no fault with that command, and it does run on my box. Maybe, you missed that final back tic when you copied the command - that last 'mark' is a 'back tic' ... located at the upper left of an ascii keyboard on the same key as the 'tilde (~)' just below the "Esc" key."

It worked with the 'back tic.'  I didn't know it was there!  I used quotes, instead.

"Let's see if those files are present.
Boot the ubuntu install to terminal:
terminal commands:
```

ls -al upgrade.txt
ls -al desktop.txt
ls -al hardware.txt

```"

I get:
```

-rw-rw-r-- 1 andy andy 15394 Sep23 14:46 upgrade.txt
-rw-rw-r-- 1 andy andy 823 Sep23 14:55 desktop.txt
-rw-rw-r-- 1 andy andy 968 Sep24 14:01 hardware.txt

```


"Once Windows has checked the USB drive, we can try again.
We must mount the drive each time it is plugged in ( and UN-mount it prior to un-plugging/ turning the box off )
We have a permanent mount point, so just attach the usb drive to it, thus:
```

sudo mount /dev/sdc1 -t vfat -o umask=000 /dev/sdc1 /mnt/work
ls -al /mnt/work
ls -al /mnt/work/save

```"

As mentioned above, the mount statement didn't work.  So, that is as far as I got today.  Sob!

"Where we still see our target directory "drwxr-xr-x 2 [color=red]root root[/color] 4096 Sept 22 15:35 save"  // and a close look at the permissions -> ONLY root has write access ! Someone with greater familiarity to accessing Windows' file system, please correct my code to allow user access !
so we will use 'sudo' on the copy commands !
```

sudo cp upgrade.txt /mnt/work/save
sudo cp desktop.txt /mnt/work/save
sudo cp hardware.txt /mnt/work/save

```
Let's check the results of our efforts:
```

sudo ls -al /mnt/work/save/upgrade.txt
sudo ls -al /mnt/work/save/desktop.txt
sudo ls -al /mnt/work/save/hardware.txt

```
Done copying so now prior to unplugging the USB drive we MUST manually UN-Mount it !
```

sudo umount /mnt/work

```

"OK, now we can take the USB drive over to the puppy box and transfer the files to the forum thread."

"We are now not in no big rush to do this, and this is time well spent as a learning experience ( even though I do not want to learn about Windows' FAT file system, or ways to access it ) ; we do what we need to do.

"So:
[LIST]
[*]do our files exist on the ubuntu install ?"

I think so ... is that correct?

"[*]are the files copied to the USB drive ?
[*]Have we got the files transfered to the forum ?
[*]
[/LIST]

"all in all
[INDENT][INDENT]ain't no step for a stepper"
[/INDENT][/INDENT]

1

---

### Post by Bashing-om on 2014-09-24
wg5o; Hey, hey :

See, we are making progress !
> 
"So:
do our files exist on the ubuntu install ?"

I think so ... is that correct?

Yepper, them there files do exist.

So now we are back to verifying the USB drive - I still suggest take it to  XP and have Windows check that USB drive ( fat32 is a Windows file system and we should use Windows' tools to check it). Then IF Windows can mount - and "safely remove" in Windows too !  - and access the USB drive, we plug it back into ubuntu and see then if ubuntu can access the file system on that USB drive.
When ubuntu can access the file system of the USB drive, we can then copy our files to the drive ( un-mount it when the files are copied ) and then mount that USB drive on the Puppy box and then then then transfer the files to the forum.

[INDENT][INDENT]the longest journey
[INDENT][INDENT][INDENT]can end; even with the smallest of steps
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wg5o on 2014-09-24
I restarted the prob computer and went to XP.  Win XP said the device is working properly.  I installed it, I put a little test file on it, uninstalled it, mounted it on Puppy, and read the test file, no problem.

What about the problem with the mount command?

Andy

---

### Post by Bashing-om on 2014-09-24
wg5o; Well, then.

We blame it on me, and I do some homework and make sure of the syntax for that mount command.

I be Backkk.
[INDENT][INDENT]If I knew everything
[INDENT][INDENT][INDENT]I would not be me
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-09-24
wg5owg5o; I am back !


Let's try it like this:
Make sure the USB drive is still seen as 'sdc' ;
```

sudo fdisk -lu

```
Mount that sucker IF it is still 'sdc' ;
```

sudo mount -t vfat /dev/sdc1 /mnt/work -o uid=1000,gid=1000,utf8,dmask=027,fmask=137

```
Check we have access to the directory ;
```

ls -al /mnt/work
ls -al /mnt/work/save

```

So far so good ? OK, copy the files!
```

cp upgrade.txt /mnt/work/save
cp desktop.txt /mnt/work/save
cp hardware.txt /mnt/work/save

``` We should not need the elevated privileges of 'sudo'; I think I have the access set for "you" in the mount command.

Now let's look and make sure the files were copied :
```

ls -al /mnt/work/save

```

Files copied ? Then all good and we are done here. So,:
```

sudo umount /mnt/work

```
and unplug the USB drive.
-------------------
Puppy box, plug in the USB drive and copy files to the forum.
We look at those files and see what action(s) to take to fix the installed system.

[INDENT][INDENT]sounds like a plan to me
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-09-24
1. Yes, it is still sdc1.
2. Mount appeared to work.
3a.  It said total 28, and listed six, the first dated Dec 31 1969 (!). the others recent.  I'll type them out, if needed.
3b.  ```

ls -al /mnt/work/save

```

It says "Cannot access /mnt/work/save: No such file or directory."

Andy

---

### Post by Bashing-om on 2014-09-24
wg5o; Huh ??

At one time that directory did exist ( reason I am a bit confused, and willing to take the time to redo the mount syntax); what is going on now ?
Mount the USB drive as you have been doing so and ->
Show us the output of:
```

ls -al /mnt/work

```

As there has
[INDENT][INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT][/INDENT]

---

### Post by wg5o on 2014-09-25
```

ls -al /mnt/work

```

Result:
drwxr-x---4 andy andy 4096 Dec 31 1969 .
drwxr-xr-x 3 root root 4096 Sep 21 19:00 ..
drwxr-x---- 4 andy andy 4096 Sep 23 17:26 .Spotlight-V100
-rw-r-----1 andy andy 4608 Sepm24 18:48 Test.doc
drwxr-x---2 andy andy 4096 Sep 23 17:26 .Trashes
-rw-r-----1 andy andy 4096 Sep 23 17:26 .-.Trashes

I had trouble getting that right; I copied it on too small a scrap of paper and had to make a lot of trips to check.

Andy

---

### Post by wg5o on 2014-09-25
Sorry.  Post #49 did have some errors.  The 3rd and 4th statements should read:

drwxr-x--- 4 andy andy 4096 Sep 23 17:26 .Spotlight-V100
-rw-r----- 1 andy andy 4608 Sep 24 18:48 Test.doc

Andy

---

### Post by Bashing-om on 2014-09-25
wg5o; Sheessh .. OK ;

Our directory (save) for some reason has disappeared !

Let's make it up once more - and explicitly set the access rights.
Mount the USB drive from terminal, and
```

sudo mkdir /mnt/work/save
sudo chown andy:andy /mnt/work

```
Now, can we copy our files into place on the USB drive ?
```

cp upgrade.txt /mnt/work/save
cp desktop.txt /mnt/work/save
cp hardware.txt /mnt/work/save

``` I do regret that it is such a hassle to relay information, but we are getting there.

Now do our files exist on the USB drive ?
```

ls -al /mnt/work/save

```
IF they now exist, and you are prepared to remove the USB drive:
```

sudo umount /mnt/work

```
[INDENT][INDENT][INDENT]are we there, yet ?
[/INDENT][/INDENT][/INDENT]

---

### Post by wg5o on 2014-09-25
Not yet ...
```

sudo chown andy:andy mnt/work

```

It said: chown: cannot access 'mnt/work': no such file or directory
So I added '/save'; same result.  It said It said: chown: cannot access 'mnt/work/save': no such file or directory.

Andy

---

### Post by wg5o on 2014-09-25
Not yet ...
```

sudo chown andy:andy mnt/work

```

It said: chown: cannot access 'mnt/work': no such file or directory
So I added '/save'; same result.  It said It said: chown: cannot access 'mnt/work/save': no such file or directory.

Andy

---

### Post by Bashing-om on 2014-09-25
wg5o; Yuk !

This is getting weird and weirder .

OK, let's see if that mount point still exist .. !
```

ls -al /mnt

```
to show the contents of that directory, which is where we are making the connection to the USB drive ( /mnt/work) .

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-09-25
Later, tried self help.  Looked at 'man mkdir' and added -v, then tried again.

Result: "cannot create directory 'mnt/work/save': File exists.

Now, what?

Andy

---

### Post by Bashing-om on 2014-09-25
wg5o; I see said the blind man !

I miss typed ! // sorry bout that:
> 
"sudo chown andy:andy mnt/work"

Should have a leading 'slash' to denote 'root' as in the path !
Correct to be:
```

sudo chown andy:andy /mnt/work

```
NOW, the terminal command:
```

ls -al /mnt

```
should show all the files listed within that directory, that we are using to make the mount point for the USB drive.
We hope to see the directory "work" in that output !

[INDENT][INDENT]I try to proof read, recon I missed that one ! (too)
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-09-25
I think we are there.  But the attchment tool doesn't work.  So... copy and paste.
```


02:00.0 VGA compatible controller [0300]: NVIDIA Corporation G98 [GeForce 8400 GS Rev. 2] [10de:06e4] (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device [1043:82b2]
	Kernel driver in use: nvidia
04:01.0 Audio device [0403]: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller [1106:3288] (rev 10)
  *-display
       description: VGA compatible controller
       product: G98 [GeForce 8400 GS Rev. 2]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:24 memory:fa000000-faffffff memory:c0000000-cfffffff memory:f8000000-f9ffffff ioport:d800(size=128) memory:fbde0000-fbdfffff

```
```

processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 47
model name	: AMD Athlon(tm) 64 Processor 3400+
stepping	: 2
cpu MHz		: 2194.814
cache size	: 512 KB
physical id	: 0
siblings	: 1
02:00.0 VGA compatible controller: NVIDIA Corporation G98 [GeForce 8400 GS Rev. 2] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 82b2
	Flags: bus master, fast devsel, latency 0, IRQ 24
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at d800 [size=128]
	[virtual] Expansion ROM at fbde0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia

             total       used       free     shared    buffers     cached
Mem:          1001        815        186         14         82        488
-/+ buffers/cache:        244        756
Swap:         1608          0       1607

```
[code]
Ign http://security.ubuntu.com trusty-security InRelease
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Get:2 http://security.ubuntu.com trusty-security Release [59.7 kB]
Get:3 http://security.ubuntu.com trusty-security/main Sources [44.9 kB]
Get:4 http://security.ubuntu.com trusty-security/restricted Sources [14 B]
Get:5 http://security.ubuntu.com trusty-security/universe Sources [10.8 kB]
Get:6 http://security.ubuntu.com trusty-security/multiverse Sources [700 B]
Get:7 http://security.ubuntu.com trusty-security/main i386 Packages [136 kB]
Get:8 http://security.ubuntu.com trusty-security/restricted i386 Packages [14 B]
Get:9 http://security.ubuntu.com trusty-security/universe i386 Packages [48.4 kB]
Ign http://extras.ubuntu.com trusty InRelease
Hit http://extras.ubuntu.com trusty Release.gpg
Ign http://us.archive.ubuntu.com trusty InRelease
Hit http://extras.ubuntu.com trusty Release
Ign http://us.archive.ubuntu.com trusty-updates InRelease
Hit http://extras.ubuntu.com trusty/main Sources
Ign http://us.archive.ubuntu.com trusty-backports InRelease
Hit http://extras.ubuntu.com trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty Release.gpg
Get:10 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg
Hit http://us.archive.ubuntu.com trusty Release
Get:11 http://security.ubuntu.com trusty-security/multiverse i386 Packages [1,398 B]
Ign http://extras.ubuntu.com trusty/main Translation-en_US
Get:12 http://us.archive.ubuntu.com trusty-updates Release [59.7 kB]
Ign http://extras.ubuntu.com trusty/main Translation-en
Get:13 http://security.ubuntu.com trusty-security/main Translation-en [69.8 kB]
Hit http://us.archive.ubuntu.com trusty-backports Release
Hit http://us.archive.ubuntu.com trusty/main Sources
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Hit http://us.archive.ubuntu.com trusty/universe Sources
Hit http://us.archive.ubuntu.com trusty/multiverse Sources
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty/main i386 Packages
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/universe Translation-en
Get:14 http://us.archive.ubuntu.com trusty-updates/main Sources [120 kB]
Get:15 http://us.archive.ubuntu.com trusty-updates/restricted Sources [1,408 B]
Get:16 http://us.archive.ubuntu.com trusty-updates/universe Sources [84.8 kB]
Get:17 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [3,527 B]
Get:18 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [317 kB]
Get:19 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [5,820 B]
Get:20 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [205 kB]
Get:21 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [9,545 B]
Get:22 http://us.archive.ubuntu.com trusty-updates/main Translation-en [145 kB]
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/main Sources
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Fetched 1,326 kB in 36s (36.1 kB/s)
Reading package lists...
Reading package lists...
Building dependency tree...
Reading state information...
The following packages have been kept back:
  linux-generic linux-generic-pae linux-headers-generic
  linux-headers-generic-pae linux-image-generic linux-image-generic-pae
The following packages will be upgraded:
  apt apt-transport-https apt-utils chromium-codecs-ffmpeg-extra dbus dbus-x11
  libapt-inst1.5 libapt-pkg4.12 libdbus-1-3 libnspr4 libnspr4-0d libnss3
  libnss3-1d libnss3-nssdb linux-libc-dev
15 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 5,052 kB of archives.
After this operation, 42.0 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libapt-pkg4.12 i386 1.0.1ubuntu2.4.1 [634 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main apt i386 1.0.1ubuntu2.4.1 [953 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libapt-inst1.5 i386 1.0.1ubuntu2.4.1 [58.4 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libdbus-1-3 i386 1.6.18-0ubuntu4.2 [132 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe chromium-codecs-ffmpeg-extra i386 37.0.2062.120-0ubuntu0.14.04.1~pkg1049 [837 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe libnspr4-0d i386 2:4.10.7-0ubuntu0.14.04.1 [6,586 B]
Get:7 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libnspr4 i386 2:4.10.7-0ubuntu0.14.04.1 [111 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libnss3-1d i386 2:3.17-0ubuntu0.14.04.1 [9,308 B]
Get:9 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libnss3-nssdb all 2:3.17-0ubuntu0.14.04.1 [10.6 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libnss3 i386 2:3.17-0ubuntu0.14.04.1 [1,055 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main apt-utils i386 1.0.1ubuntu2.4.1 [172 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main apt-transport-https i386 1.0.1ubuntu2.4.1 [25.4 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main dbus i386 1.6.18-0ubuntu4.2 [233 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main dbus-x11 i386 1.6.18-0ubuntu4.2 [18.5 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-libc-dev i386 3.13.0-36.63 [795 kB]
Fetched 5,052 kB in 18s (276 kB/s)
(Reading database ... 202415 files and directories currently installed.)
Preparing to unpack .../libapt-pkg4.12_1.0.1ubuntu2.4.1_i386.deb ...
Unpacking libapt-pkg4.12:i386 (1.0.1ubuntu2.4.1) over (1.0.1ubuntu2.3) ...
Setting up libapt-pkg4.12:i386 (1.0.1ubuntu2.4.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.3) ...
(Reading database ... 202415 files and directories currently installed.)
Preparing to unpack .../apt_1.0.1ubuntu2.4.1_i386.deb ...
Unpacking apt (1.0.1ubuntu2.4.1) over (1.0.1ubuntu2.3) ...
Processing triggers for man-db (2.6.7.1-1) ...
Setting up apt (1.0.1ubuntu2.4.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.3) ...
(Reading database ... 202415 files and directories currently installed.)
Preparing to unpack .../libapt-inst1.5_1.0.1ubuntu2.4.1_i386.deb ...
Unpacking libapt-inst1.5:i386 (1.0.1ubuntu2.4.1) over (1.0.1ubuntu2.3) ...
Preparing to unpack .../libdbus-1-3_1.6.18-0ubuntu4.2_i386.deb ...
Unpacking libdbus-1-3:i386 (1.6.18-0ubuntu4.2) over (1.6.18-0ubuntu4.1) ...
Preparing to unpack .../chromium-codecs-ffmpeg-extra_37.0.2062.120-0ubuntu0.14.04.1~pkg1049_i386.deb ...
Unpacking chromium-codecs-ffmpeg-extra (37.0.2062.120-0ubuntu0.14.04.1~pkg1049) over (37.0.2062.94-0ubuntu0.14.04.1~pkg1042) ...
Preparing to unpack .../libnspr4-0d_2%3a4.10.7-0ubuntu0.14.04.1_i386.deb ...
Unpacking libnspr4-0d:i386 (2:4.10.7-0ubuntu0.14.04.1) over (2:4.10.2-1ubuntu1.1) ...
Preparing to unpack .../libnspr4_2%3a4.10.7-0ubuntu0.14.04.1_i386.deb ...
Unpacking libnspr4:i386 (2:4.10.7-0ubuntu0.14.04.1) over (2:4.10.2-1ubuntu1.1) ...
Preparing to unpack .../libnss3-1d_2%3a3.17-0ubuntu0.14.04.1_i386.deb ...
Unpacking libnss3-1d:i386 (2:3.17-0ubuntu0.14.04.1) over (2:3.15.4-1ubuntu7.1) ...
Preparing to unpack .../libnss3-nssdb_2%3a3.17-0ubuntu0.14.04.1_all.deb ...
Unpacking libnss3-nssdb (2:3.17-0ubuntu0.14.04.1) over (2:3.15.4-1ubuntu7.1) ...
Preparing to unpack .../libnss3_2%3a3.17-0ubuntu0.14.04.1_i386.deb ...
Unpacking libnss3:i386 (2:3.17-0ubuntu0.14.04.1) over (2:3.15.4-1ubuntu7.1) ...
Preparing to unpack .../apt-utils_1.0.1ubuntu2.4.1_i386.deb ...
Unpacking apt-utils (1.0.1ubuntu2.4.1) over (1.0.1ubuntu2.3) ...
Preparing to unpack .../apt-transport-https_1.0.1ubuntu2.4.1_i386.deb ...
Unpacking apt-transport-https (1.0.1ubuntu2.4.1) over (1.0.1ubuntu2.3) ...
Preparing to unpack .../dbus_1.6.18-0ubuntu4.2_i386.deb ...
Unpacking dbus (1.6.18-0ubuntu4.2) over (1.6.18-0ubuntu4.1) ...
Preparing to unpack .../dbus-x11_1.6.18-0ubuntu4.2_i386.deb ...
Unpacking dbus-x11 (1.6.18-0ubuntu4.2) over (1.6.18-0ubuntu4.1) ...
Preparing to unpack .../linux-libc-dev_3.13.0-36.63_i386.deb ...
Unpacking linux-libc-dev:i386 (3.13.0-36.63) over (3.13.0-35.62) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Setting up libapt-inst1.5:i386 (1.0.1ubuntu2.4.1) ...
Setting up libdbus-1-3:i386 (1.6.18-0ubuntu4.2) ...
Setting up chromium-codecs-ffmpeg-extra (37.0.2062.120-0ubuntu0.14.04.1~pkg1049) ...
Setting up libnspr4:i386 (2:4.10.7-0ubuntu0.14.04.1) ...
Setting up libnspr4-0d:i386 (2:4.10.7-0ubuntu0.14.04.1) ...
Setting up apt-utils (1.0.1ubuntu2.4.1) ...
Setting up apt-transport-https (1.0.1ubuntu2.4.1) ...
Setting up dbus (1.6.18-0ubuntu4.2) ...
Installing new version of config file /etc/dbus-1/session.conf ...
Setting up dbus-x11 (1.6.18-0ubuntu4.2) ...
Setting up linux-libc-dev:i386 (3.13.0-36.63) ...
Setting up libnss3-nssdb (2:3.17-0ubuntu0.14.04.1) ...
Setting up libnss3:i386 (2:3.17-0ubuntu0.14.04.1) ...
Setting up libnss3-1d:i386 (2:3.17-0ubuntu0.14.04.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.3) ...
Reading package lists...
Building dependency tree...
Reading state information...
The following NEW packages will be installed:
  linux-headers-3.13.0-36 linux-headers-3.13.0-36-generic
  linux-image-3.13.0-36-generic linux-image-extra-3.13.0-36-generic
The following packages will be upgraded:
  linux-generic linux-generic-pae linux-headers-generic
  linux-headers-generic-pae linux-image-generic linux-image-generic-pae
6 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 61.4 MB of archives.
After this operation, 222 MB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-3.13.0-36-generic i386 3.13.0-36.63 [14.7 MB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-generic-pae i386 3.13.0.36.43 [1,748 B]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-generic-pae i386 3.13.0.36.43 [1,746 B]
Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-extra-3.13.0-36-generic i386 3.13.0-36.63 [37.1 MB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-generic i386 3.13.0.36.43 [1,784 B]
Get:6 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-generic i386 3.13.0.36.43 [2,362 B]
Get:7 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-generic-pae i386 3.13.0.36.43 [1,750 B]
Get:8 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-3.13.0-36 all 3.13.0-36.63 [8,909 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-3.13.0-36-generic i386 3.13.0-36.63 [715 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-generic i386 3.13.0.36.43 [2,350 B]
Fetched 61.4 MB in 3min 24s (301 kB/s)
Selecting previously unselected package linux-image-3.13.0-36-generic.
(Reading database ... 202415 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-36-generic_3.13.0-36.63_i386.deb ...
Unpacking linux-image-3.13.0-36-generic (3.13.0-36.63) ...
Preparing to unpack .../linux-generic-pae_3.13.0.36.43_i386.deb ...
Unpacking linux-generic-pae (3.13.0.36.43) over (3.13.0.35.42) ...
Preparing to unpack .../linux-image-generic-pae_3.13.0.36.43_i386.deb ...
Unpacking linux-image-generic-pae (3.13.0.36.43) over (3.13.0.35.42) ...
Selecting previously unselected package linux-image-extra-3.13.0-36-generic.
Preparing to unpack .../linux-image-extra-3.13.0-36-generic_3.13.0-36.63_i386.deb ...
Unpacking linux-image-extra-3.13.0-36-generic (3.13.0-36.63) ...
Preparing to unpack .../linux-generic_3.13.0.36.43_i386.deb ...
Unpacking linux-generic (3.13.0.36.43) over (3.13.0.35.42) ...
Preparing to unpack .../linux-image-generic_3.13.0.36.43_i386.deb ...
Unpacking linux-image-generic (3.13.0.36.43) over (3.13.0.35.42) ...
Preparing to unpack .../linux-headers-generic-pae_3.13.0.36.43_i386.deb ...
Unpacking linux-headers-generic-pae (3.13.0.36.43) over (3.13.0.35.42) ...
Selecting previously unselected package linux-headers-3.13.0-36.
Preparing to unpack .../linux-headers-3.13.0-36_3.13.0-36.63_all.deb ...
Unpacking linux-headers-3.13.0-36 (3.13.0-36.63) ...
Selecting previously unselected package linux-headers-3.13.0-36-generic.
Preparing to unpack .../linux-headers-3.13.0-36-generic_3.13.0-36.63_i386.deb ...
Unpacking linux-headers-3.13.0-36-generic (3.13.0-36.63) ...
Preparing to unpack .../linux-headers-generic_3.13.0.36.43_i386.deb ...
Unpacking linux-headers-generic (3.13.0.36.43) over (3.13.0.35.42) ...
Setting up linux-image-3.13.0-36-generic (3.13.0-36.63) ...
Setting up linux-image-extra-3.13.0-36-generic (3.13.0-36.63) ...
Setting up linux-image-generic (3.13.0.36.43) ...
Setting up linux-headers-3.13.0-36 (3.13.0-36.63) ...
Setting up linux-headers-3.13.0-36-generic (3.13.0-36.63) ...
Setting up linux-headers-generic (3.13.0.36.43) ...
Setting up linux-generic (3.13.0.36.43) ...
Setting up linux-generic-pae (3.13.0.36.43) ...
Setting up linux-image-generic-pae (3.13.0.36.43) ...
Setting up linux-headers-generic-pae (3.13.0.36.43) ...
Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 desktop4shared       file manager to access 4shared web account from PC
 libjson0:i386        JSON manipulation library (transitional package)

---

### Post by Bashing-om on 2014-09-25
wg5o; Sometimes

I think someone should take me out behind the wood shed;
I failed to consider where in the operating system we were.
OK, the hardware outputs look good, should run 14.04.
As to the update/upgrade outputs.. My bad again, as those are from the liveDVD, and not from within the install. To get that we must change from within the liveDVD to the install:
That is what is termed as a CHange Root:
From the liveDVD terminal; mount the USB drive once more and execute these terminal commands to copy the files once more ( overwrite what is in the files located at /mnt/work/save)
```

sudo mount /dev/sdb1 /mnt/
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
sudo chroot /mnt/

```

OK, Now copy the files: 
In the CHange Root environment you are "root" and as such there is no need to elevate privileges with "sudo". so:
```

apt-get update > upgrade.txt
apt-get upgrade -y >> upgrade.txt
apt-get dist-upgrade -y >> upgrade.txt
apt-get -f install >> upgrade.txt
dpkg -C >> upgrade.txt

```
OK, at this point we should have the "proper" file made up. 

Copy the file to the USB drive:
```

cp -p upgrade.txt /mnt/work/save

```
All done with the CHange Root, back out of it gracefully !
```

exit
sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt

```
check that the new file exists on the USB drive:
```

ls -al /mnt/work/save/upgrade.txt

``` look at the date and time to see that it is the new file that has been written.

Now also done with the USB drive for now, safely remove it:
```

sudo umount /mnt/work

```

NOW transfer that file back here to the forum.

[INDENT][INDENT]thus this tale is told
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-09-25
What live DVD?  There was no live DVD involved.  I don't have one.  

I'm done for the day.  I gotta go out for supper and a play.

Andy

---

### Post by wg5o on 2014-09-26
Sorry.  I should have repeated how I got into this trouble: Update Manager kept offering me 14.04 LTS, and I finally backed-up my files and pushed the Upgrade button in Update Manager.  That was August 28.

Andy

---

### Post by Bashing-om on 2014-09-26
wg5o; Hey !

Looking good then ( as I had my wires crossed think'n still on 12.04, and seeing 14.04 sources !!) .. all to the good here !

OK you have made the transition to 14.04 and are looking good - believe it or not ! What I now 'think' is going on is that in that 12.04 install you were running a proprietary graphics driver for the Nvidia card, that in the upgrade process the driver got broke.
Before addressing replacing the graphics driver- and getting you up on the GUI -  let's work on the little niggly hiccup that the package manager advises us of. And as well get the patches for 'bash' due to the recent security risk factors:
terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install --reinstall libjson0:i386 

```
Do not know yet where this "desktop4shared file manager to access 4shared web account from PC" is coming from ?? Maybe a 3rd party PPA ?

Once the above runs clean, we look at the graphics driver situation and get you up on the desk top !

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-09-26
All done.  No apparent problems.  "Upgrade" produced a good deal of work, maybe 10 minutes.  "Dist-upgrade" found no changes to make.

I've gotten hung-up on Nvidia before, and have notes, somewhere, on where to find a driver.  However, by desktop picture [Chineese(?) city] looks just fine.

I don't know where, "desktop4shared file manager to access 4shared web account from PC" came form.  But I've been running 12.04 for a long tome, and I have trouble remembering what happened yesterday.  

Note:  After this afternoon, I won't be able to get back to this until Monday morning.

Andy

---

### Post by wg5o on 2014-09-26
All done.  No apparent problems.  "Upgrade" produced a good deal of work, maybe 10 minutes.  "Dist-upgrade" found no changes to make.

I've gotten hung-up on Nvidia before, and have notes, somewhere, on where to find a driver.  However, by desktop picture [Chineese(?) city] looks just fine.

I don't know where, "desktop4shared file manager to access 4shared web account from PC" came form.  But I've been running 12.04 for a long tome, and I have trouble remembering what happened yesterday.  

Note:  After this afternoon, I won't be able to get back to this until Monday morning.

Andy

---

### Post by Bashing-om on 2014-09-26
wg5o; OK !

Making great progress. As it is now, can you boot to a functional GUI desk top ? OR still only able to login from the TTY1 terminal ?
We still working to get up on the GUI ? OR we moving on the fix the desktop ?

Will place " desktop4shared" on the back burner and let it simmer a bit, while we address higher priority issue.

No big deal as to when we finish up here, we work at your schedule. 

[INDENT][INDENT]A focus for our attention
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-09-26
"As it is now, can you boot to a functional GUI desk top ?"

Answer: No change. I restarted, and got the same thing:  My desktop background, my name, and login block.  Still can't log in as me or        as guest.

 "OR still only able to login from the TTY1 terminal ?"

Answer:  Yes.

"We still working to get up on the GUI ? OR we moving on the fix the desktop ?"

Answer:  I think so.  If I can login, it might work.

Andy

---

### Post by Bashing-om on 2014-09-26
wg5o; Well !

Let's look. 1st is to insure that "you" have authority to access the GUI :
```

ls -al .Xauthority
ls -al .ICEauthoruty
ls -al /home

```
My output for reference:
```

sysop@1404mini:~$ ls -al .Xauthority
-rw------- 1 sysop sysop 209 Aug  1 10:10 .Xauthority
sysop@1404mini:~$ 

sysop@1404mini:~$ ls -al .ICEauthority
-rw------- 1 sysop sysop 15322 Sep 26 11:43 .ICEauthority
sysop@1404mini:~$

sysop@1404mini:~$ ls -al /home
total 28
drwxr-xr-x  4 root  root   4096 May 19  2013 .
drwxr-xr-x 25 root  root   4096 Sep 23 12:01 ..
drwx------  2 root  root  16384 May 19  2013 lost+found
drwxr-xr-x 28 sysop sysop  4096 Sep 26 14:21 sysop
sysop@1404mini:~$

```
Where my 'username' is "sysop" does your outputs all reflect 'you' as "andy" ??

IF so we move on to replacing the graphics driver:
I want to install the open source driver, and then see what we are going to do:
To that end, has Nvidia blacklisted 'nouveau' ?
```

sudo grep 'blacklist.*nouveau' /etc/modprobe.d/*

```
If there is no response, we can assume that the open source driver is not blacklist and we can continue:
```

sudo service lightdm stop
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo apt-get install linux-headers-generic
sudo apt-get install ubuntu-desktop
sudo apt-get install dkms
sudo apt-get install xserver-xorg-video-nouveau
sudo update-initramfs -u

```

OK;  NOW reboot, and let's see the effect, I do expect that you boot to the GUI desktop .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-09-26
[QUOTE=Bashing-om;13129964]wg5o; Well !

Let's look. 1st is to insure that "you" have authority to access the GUI :
```

ls -al .Xauthority
ls -al .ICEauthoruty
ls -al /home

```

Answer:  My response is similar to yours, where I am 'andy,' execpt that I have no 'lost + found' statement.

IF so we move on to replacing the graphics driver:
I want to install the open source driver, and then see what we are going to do:
To that end, has Nvidia blacklisted 'nouveau' ?
```

sudo grep 'blacklist.*nouveau' /etc/modprobe.d/*

```
If there is no response, we can assume that the open source driver is not blacklist and we can continue:

Answer:  Just returned to prompt, so I went on.

```

sudo service lightdm stop
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

Answer:  ... purge Nividia gave a long list ending in ' ... so not removed,' well it said they weren't installed.  Only removed:
```

nividia-173* nividia-common*nvidia-settings

```

Stuck on the last (backup) command:
"mv: cannot stat '/etc/X11/xorg.conf' No such file or directory"


Andy

xxxx

---

### Post by Bashing-om on 2014-09-26
wg5o; Shucks,

All in all, looking good - but,:
> 
nividia-173* nividia-common*nvidia-settings

says we are going to have to roll our sleeves up and do some more work.
What returns from:
```

sudo find / -name "nvidia"
sudo find / -name "NVIDIA-Linux-*"
sudo find / -name  "*.run"

```
The find command searches the files on the system looking for a match; It does take a while to complete; patience.
Bet there is still some files about from the OEM driver install. Will have to make sure we remove all of these files prior to installing the open source driver. Likely this is the issue that caused the release upgrade problems.

As to "mv: cannot stat '/etc/X11/xorg.conf' No such file or directory" I had expected that file to exist, as Nvidia does use it. As it is not present, no worry, as we will not be using it with the open source driver.

We get all the Nvidia stuff removed - with the results of the find commands - , we then go ahead with the remainder of the process.

again, we are making progress
[INDENT][INDENT][INDENT]a bit at the time
[/INDENT][/INDENT][/INDENT]

---

### Post by wg5o on 2014-09-30
```

sudo find / -name "nvidia"
/etc/appamor.d//abstraction/nvidia
/sys/bus/pci/drivers/nvidia
/usr/src/linux-headers-3.13.0-35-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.13.0-36-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.13.0-35-drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.13.0-35-drivers/vidio/nvidia
/usr/src/linux-headers-3.13.0-36-drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.13.0-35-drivers/vidio/nvidia
/usr/lib/nvidia
/lib/modules/3.13.0-36-generic/kernel/drivers/net/etnernet/nvidia
/lib/modules/3.13.0-36-generic/kernel/drivers/vidio/nvidia
/lib/modules/3.13.0-35-generic/kernel/drivers/net/etnernet/nvidia
/lib/modules/3.13.0-35-generic/kernel/drivers/ne/vidio/nvidia
/lib/modules/3.2.0-68-generic-pae/kernel/drivers/vidio/nvidia
/lib/modules/3.13.0-36-generic/kernel/drivers/vidio/nvidia
/lib/modules/3.13.0-36-generic/kernel/drivers/vidio/nvidia


```

```

sudo find / -name "NVIDIA-Linux-*"
/home/andyandy/Nvidia/NVIDIA-Linux-x86-270.41.06.run
/home/andyandy/Nvidia-Linux-x86-270.41.06.run
/home/andyandy/Nvidia/NVIDIA-Linux-x86-260.19.21.run
/home/andyandy/NVIDIA/NVIDIA-Linux-x86-260.19.29.run
/home/andy/Desktop/Documents/Computer/NVIDIA-Linux-x86-256.53.run
/home/andy/Desktop/NVIDIA-Linux-x86-256.53.run

```

```

sudo find / -name  "*.run"
/home/andyandy/Nvidia/-Linux-x86-270.41.06.run
/home/andyandy/Nvidia/NVIDIA-Linux-x86-270.41.06.run
/home/andyandy/Nvidia/NVIDIA-Linux-x86-260.19.21.run
/home/andyandy/Nvidia/NVIDIA-Linux-x86-260.19.29.run
/home/andy/andy/Desktop/Documents/Computer/NVIDIA-Linux-x86-256.run
/home/andy/andy/Desktop/NVIDIA-Linux-x86-295.71.run

```

This is very labor intensive and subject to errors.  I need to learn how to put stuff on the thumb drive to transfer it.

Andy

---

### Post by Bashing-om on 2014-09-30
wg5o; Hey !

Just now getting caught up on the forum to where I have seen your response.

Let's see what this "poke" does:
```

cd Nvidia

```
This should change the systems' perspective to see directly the files we want to work with.

Do you see those Nvidia .run files when you do:
```

ls -al

```
IF you are 'there' and see the .run files.
Then terminal code:
```

./NVIDIA-Linux-x86-270.41.06.run --uninstall

```
And let's see if Nvidia's uninstaller will work for us for this 1 of 6 drivers installed.
We want to remove ALL proprietary drivers and related files, and then install the open source driver, see what things look like running the open source driver and consider IF we want to change that driver.

As to copy and paste .. practicing to make perfect gets real old in a hurry. As you have a USB drive, open 2 instances of a window in the file manager , Copy and paste the terminal outputs to a file (untitled -> save/rename to something meaningful) and drag and drop the files between the 2 windows. Easiest way I know of.

[INDENT][INDENT]I hope it is this easy to remove the Nvidia drivers,
[INDENT][INDENT][INDENT]I have my doubts !
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wg5o on 2014-09-30
Reminder:  I'm still stuck in tty1.

I didn't get far:

```

cd Nvidia
No such file or directory
sudo cd Nvidia
sudo: cd: command not found.

```

How could I screw up something so simple?

Andy

---

### Post by Bashing-om on 2014-09-30
wg5o; sheesshh; 

Sorry bout that - forgetting we are in terminal - no GUI ... 
EDIT: By the way, we can still get command outputs to a file (redirection), mount that usb drive from terminal, and copy the files to the USB drive. - This is linux, where there is a will, there is a way -

OK, here we have a condition that we are trying to lie to the operating system, and of course, the system will not believe us.
We need to tell the system where we want to go to in the file system.
From your lastest reply the directory that holds those Nvidia .run files:
> 
/home/andyandy/Nvidia/NVIDIA-Linux-x86-270.41.06.run

is in some sub directory located in the /home directory.
Let's find them for sure, so we can tell the operating system the truth.
In terminal do:
```

ls -al /home/andy

```
in that output do you find something similar:
[color=green]d[/color]rwxr-xr-x  2 andy andy    4096 May 19  2013 [color=red]Nvidia[/color]
where 'd' in the drwxr-xr-x field represents a directory AND the name Nvidia IS case sensitive; such that nvidia does not equal Nvidia

Let's say that the name at the end of that line is indeed Nvidia with a capital 'N', and is spelled 'exactly' the same; then;
terminal command:
```

ls -al /home/andy/Nvidia

```
Will list the contents of that sub directory, do you see those Nvidia .run files ?

IF yes, then we know the 'path' so we can correctly 'cd' (change directory) so the system is looking directly at the files, and we do not have to tell the system explicitly every time we type a command where these files are. That is the whole point of 'cd-ing'.

-------------------
By the way, your patience with this little issue is to be commended. Like anything else, once you know how it is EASY.

still, rolling out sleeves up
[INDENT][INDENT]getting ready to fight with non-ubuntu proprietary drivers
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-01
The path proved to be:

```

/home/andy/andy/Nvidia
cd /home/andyandy/Nvidia

```
So, back to #70
Entered ./NVIDIA-Linux etc
got:
./NVIDIA-Linux-270.41.06.run: command not found

I tried "man uninstall' & got "No man entry ..."

Now what?  It is more ignornce than patienceI!  I thought that I would need a live DVD to start over and I have no way to make one, but I can make a CD, and I now understand that is good enough.  (Also, being w/o my comptuer for over a month is hurting.)

But, onward!

Andy

---

### Post by Bashing-om on 2014-10-01
wg5o; Hi !

OK, I hope it is but a slip of the fingers:
> 
cd /home/andyandy/Nvidia

where "andyandy" should be 'andy/andy' with that '/' are a directory directive.

And I have had another thought on the means to transfer information, that is much quicker and easier ! ubuntu maintains a "pastie" site we can use.
install the tool:
```

sudo apt-get install pastebinit

```
and to use it !
```

ls -al /home/andy/andy/Nvidia | pastebinit

```
Which will generates a URL in your terminal. That URL contains the information from the terminal command as executed.
I access the pastie site with the URL you provide and now I can manipulate your data to the forum as required ! So now I have a means to see what you see ! And, hopefully give much better advise.

Now as to:
> 
./NVIDIA-Linux-270.41.06.run: command not found

You have shown me that the file does exist, so let's find out what is going on starting with the info provided by the pastbinit command.

As to making up another liveDVD, nope, a CD is no longer large enough to hold the image. A CD is limited to 700Mb, all the desktop images are greater than 700Mbs. It now takes a DVD or a USB (OR a working 'buntu install).

One can make a server or "minimal" image and that WILL fit on a CD.

[INDENT][INDENT]we will struggle through this
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-01
```

See:  http: //paste.ubuntu.com/8474822/

```

It is /andy/andy/Nvidia and the directory you want is /andy/Nvidia.  (That was caused by my bad housekeeping when I had to use backup files for some forgotten reason.)

I did buy another thumb drive, just in case.

Aside:  Since you can see my mess, maybe you can tell me how to get rid of, "-System-Product-Name."

Andy

---

### Post by Bashing-om on 2014-10-01
wg5o; Hey , now that works !

From your -> ??? I do not know what path !
we have:
> 
drwx------  2 andy andy     4096 Apr 24  2011 Nvidia
-rw-r--r--  1 andy andy 29648476 Apr 22  2011 NVIDIA-Linux-x86-270.41.06.run

 as I am again totally confused in YOUR paths
"It is /andy/andy/Nvidia and the directory you want is /andy/Nvidia." Huh ???
The output from the http //paste.ubuntu.com/8474822/ is from what path ??
I asked it to be " ls -al /home/andy/andy/Nvidia " to pastebinit .

The double andy/andy is really playing havoc with my dyslexia. Trying to understand the path to the Nvidia .run files.
-------------------------
I have no point of reference for this:
> 
Aside: Since you can see my mess, maybe you can tell me how to get rid of, "-System-Product-Name."

What exactly is 'System-Product-Name' what do you see where ?
In the ubuntu operating system, maybe the prompt ? or what is seen where , when you do - what ?
------------------------------

Mind you at this time all we are trying to do is remove all the Nvidia drivers ( maybe broken and maybe conflicting with one another) .. and then install the open source driver.
Get a a firm foundation with the operating system and see what else is to be done,

[INDENT][INDENT]should not be a big deal
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-01
Sorry.  I thought pastebinit would allow you to see what I see.  My prompt reads:
```

andy@andy-System-Product-Name$

```

The files you listed are the 1st and last of 7 that result from:
```

~/andy/Nivdia$ ls -al

```

The screwed-up prompt and file system just happened over the years, and, since I seldom use terminal, I didn't take the trouble to figure out how to fix the mess.  I'm just a desktop user, not a Linux hobbyist. 

Andy

---

### Post by Bashing-om on 2014-10-01
wg5o; Good !

OK; the prompt; 
You need to edit 2 files.
1) /etc/hosts ->
Make a backup of any file prior to editig, just never can tell what might happen
```

sudo cp /etc/hosts /etc/hosts-01oct2014

```

now open the text editor with the elevated privileges to edit a system file:
```

gksudo gedit /etc/hosts

```
Now see that little bitty portion in the 2nd line .. that has the present "andy-System-Product-Name" ?
In the text editor change it to what ever you desire.
save the file.
exit out of the text editor.

Now you MUST also edit:
2) /etc/hostname
again make a backup
```

sudo cp /etc/hostname /etc/hostname-01oct2014

```
Fire up the text editor ( yeah again, one track mind !)
```

gksudo gedit /etc/hostname

```
this file only contains that one thing,, a name !
Change this name to EXACTLY what you chose to use in the '/etc/hosts' file
save the file
exit out of the text editor.

Re-boot the system and you will see your new prompt !
---------------------------
Sorry, that I still do not understand the path situation to the Nvidia drivers - so I can direct you to that proper location to run the commands to -Maybe- remove the drivers.
let's try this:
do:
```

cd

```
that will change your perspective back to your /home directory.
Now from your home directory:
```

ls -al /home/andy/andy | pastebinit

```
and pass me back that generated URL
and now If I see what I expect to see, I have control on this path situation ! 
Next I will ask to see the contents of the directory containing the drivers.
and once more I pass you the proper 'cd' syntax and the command to remove 1 of those drivers.
------------------
Clarification of pastebinit's output, - regret that I confused you -; What is in that file is the results of the command. The result you would see if you ran that command .
You do "ls -al /home/andy/andy" and you see the output on your terminal.
You do " ls -al /home/andy/andy | pastebinit" that generates a file at the web site that I can access to also see what you would have seen in your terminal with the command. In your browser you may also read the file by putting the URL in the address bar. It is a "web page".

[INDENT][INDENT]We are getting there !
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-01
Thank you.  I'll let the prompt wait until the basic problem is fixed.

Your link:
```

http://paste.ubuntu.com/8476041/

```

---

### Post by Bashing-om on 2014-10-01
wg5ol Hey !

The paths are starting to make sense to me, I have our bearings !

ok, we have a path !
from: /home/andy/andy   I see for sure 1) a .run file -> NVIDIA-Linux-x86-270.41.06.run; 2) a Nvidia directory -> drwx------ Nvidia .
All right ! Let's see what we can do with the .run file.
change the perspective: starting from your /home directory do:
```

cd andy

```
And change the permissions on the file to make it executable - Hey I missed this the 1st time around !
```

sudo chmod +x NVIDIA-Linux-x86-270.41.06.run

```

Let's see if there is enough for the uninstall to operate with:
```

./NVIDIA-Linux-x86-270.41.06.run --uninstall

```
As we can not copy and paste, take you time and enter the commands exactly as shown, NVIDIA is all uppercase - case matters !
and L != l (Linux) upper case 'L' here.
What is this result ?

OK when all done here, report back to the /home directory, so we keep our sense of presence:
```

cd

```

Next is to start all over and look at what is in " /home/andy/andy/Nvidia "  

[INDENT][INDENT]we be step'n now
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-01
I think I did it:
```

./NVIDIA-Linux-x86-270.41.06.run --uninstall

```
I got a blue stripe that said the uninstall has to be run as root.  Clicked OK.  Blank screen with prompt at the bottom.  Used the up arrow to get the command back and added "sudo."  That seemed to work.  Blue stripe saying: "There is no NVIDIA driver installed."  Clicked OK, and then entered the "cd."

---

### Post by Bashing-om on 2014-10-01
wg5o; Great !

We do'n good .. OK, on to the next set:
```

ls -al andy/andy/Nvidia | pastbinit

```
and pass the URL. please.
Where it is an upper case 'N' and the remainder are all lower case.
Reminder to self .. go back and remove this file, all done with it -- also remember to check if "Nvidia call home".

I am done for this session, we pick this up in my after noon ( firewood work !)

[INDENT][INDENT]moving smartly along
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-02
```

ls -al andy/andy/Nvidia | pastebinit

```
'ls: cannot access andy/andy/Nvidia: No such file or directory
You are trying to send an empty document, exiting.'

So:
```

cd andy
ls

```
I found 'Nvidia' (in blue) & 'NVIDIA-Linux-x86-270.41.06.run' (in green).
```

ls -al /andy/Nvidia | pastebinit

```
Got the same result as above.  Should I have omitted the leading '/'?
```

cd Nvidia
ls | pastebinit

```
Result:  http: //paste.ubuntu.com/8480215

Sorry, I don't know how to remove the file, or how to check if "Nvidia call home".

For sure, I'm really out of business now. My beautiful desktop background is long gone.

Andy

---

### Post by Bashing-om on 2014-10-02
wg5ol Yuk.

I am so frustrated, I seem to have lost the path again ! such a simple thing , and I keep loosing track.
Let me try and simplify the command to remove those other Nvidia drivers;
Let's re-affirm what that true path the these files are.
```

cd

```
puts the perspective back to "/home/andy" .
OK, confirm, post back the result of terminal command:
```

pwd

```

Now also confirm:
```

ls -al /home/andy/andy/Nvidia/NVIDIA-Linux-x86-260.19.21.run

```
that you get a positive result here .

Now as to the concern:
> 
For sure, I'm really out of business now. My beautiful desktop background is long gone.

we are working hard to get a known foundation established for that display driver ( we will install open source ) and get that beautiful desktop back !

[INDENT]patience - Bashing-om, is a virtue
[/INDENT]

---

### Post by wg5o on 2014-10-02
```

cd
andy@andy-System-Product-Name:~ $

```
```

pwd
/home/andy

```
```

ls -al /home/andy/andy/Nvidia/NVIDIA-Linux-x86-260.19.21.run
-rw-r--r--1andyandy 28463230 Dec 7 20210 /home/andy/andy/Nvidia/NVIDIA-inux-x86-260.19.21.run

```

---

### Post by Bashing-om on 2014-10-02
wg5o; OK !!

Let's do this with the explicit path, even though it is a lot more typing. Exercising care I feel it is a surer method.
Upfront, with a "root shell" - BE Careful !! check at least 3 times. In this root shell there is no forgiveness for a mistake or an error.
From your /home directory as the -Present -Working -Directory: (/home/andy)
```

sudo -i

``` you are now 'root' and have supreme authority. You should not now have to deal with acquiring root when executing the  uninstall script.
Note the change in your prompt where as before there was '$', now there is '#' to remind you of where you are at and to be careful .

In the terminal there is a "history" to recall a former command, arrow up and just edit the last numbers ! But triple check that these edits are correct. ( as you can not coy/paste, we want to limit a condition to error, and lessen the amount of typing )
Do:
```

chmod +x /home/andy/andy/Nvidia/NVIDIA-Linux-x86-260.19.21.run
chmod +x /home/andy/andy/Nvidia/NVIDIA-Linux-x86-260.19.29.run
chmod +x /home/andy/andy/Nvidia/NVIDIA-Linux-x86-270.41.06.run

sh /home/andy/andy/Nvidia/NVIDIA-Linux-x86-260.19.21.run
sh /home/andy/andy/Nvidia/NVIDIA-Linux-x86-260.19.29.run
sh /home/andy/andy/Nvidia/NVIDIA-Linux-x86-270.41.06.run

```

All done so get out of this root shell !
```

exit

``` 

Make sure our work here is done:
```

ls -al /home/andy/andy/NVIDIA*
ls -al /home/andy/andy/Nvidia/
ls -al /home/andy/andy/Nvidia/NVIDIA*

```

I do expect no returns - a good thing - and that "ls -al /home/andy/andy/Nvidia/" is now an empty directory, and we will then delete this directory.
-------------------------
Pending:
1) make sure "Nvidia call home" is not in effect
2) make sure 'nouveau' is not blacklisted
3) make sure there are no other Nvidia driver files on the system
4) install the open source driver 'nouveau' !

[INDENT][INDENT]just a little farther
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-02
Not there yet ...

Got to # prompt OK
1st 'chmod': OK.  2nd gave, "Cannot access ... No such file or directory.'  3rd OK, back to prompt.

1st 'sh' displayed the license agreement. I thought I was pushing 'accept.'  WRONG, it aborted.  Started over, and this time accepted.  Got a blue stripe with, 'The distribution-provided pre-install script failed.  Continue installation anyway?'  Punched 'yes.'
Another blue stripe: "ERROR: The kernel header file '/lib/modules/3.13.0.36-generic/build/include/linux/version.h' does not exist.  The most likely reason for this is that the kernel source in '/lib/modules/3.13.0-36-generic/build' have not been configured."  Punched 'OK.'  Yet another blue stripe: "Installation has failed. Please see ... etc."  Pushed 'OK.'  Back to the prompt. 

After the 2nd 'sh,' when I entered the 3rd one, I found an error in the 2nd, they were different lengths.  So, I fixed that and ran the 2nd last.  Result: Another license which gave statements similar to the1st.

3rd 'sh' I got another 'can't open' statement.

Got back to the $ prompt OK.

Three 'ls' items:
1st: '-rwxr-xr-x 1 andy andy 29648476 Apr 22 2011 /home/andy/andyNVIDIA-Linux-x86-270.41.06.run' with the '/home ... run' in green.
2nd said total 84648 & listed 7 files, two in green ... dates Apr4, Feb 5, Oct 3, May 18, Dec 7, Dec 28, Apr 22.
3rd gave 3 files, 2 in green: Dec 7, Dec 28,  Apr 22.

Perhaps you could tell me how to delete files, and I could go find them and do the hit job?  This is getting tiresome.  I sure hope the open source driver works.

Andy

---

### Post by Bashing-om on 2014-10-03
wg5o; Yep;

We have done the best we can with what we have to work with, As there is not enough for the Nvidia installer to work with, we are done with that aspect of this operation.
```

sudo rm /home/andy/andy/NVIDIA-Linux-x86-270.41.06.run  
sudo rm /home/andy/andy/Nvidia/NVIDIA-inux-x86-260.19.21.run
sudo rm /home/andy/andy/Nvidia/NVIDIA-Linux-x86-260.19.29.run
sudo rm /home/andy/andy/Nvidia/NVIDIA-Linux-x86-270.41.06.run
sudo rmdir /home/andy/andy/Nvidia

```

Cleanup !
```

ls -al /var/lib/dpkg/info/Nvidia*.list
ls -al /var/lib/dpkg/info/NVIDIA*.list
ls -al /var/lib/dpkg/info/nvidia*.list

```
I really do not expect any of these files to exist, but, if any one does, will be a big help in cleaning things up.
---------------------------------
1) Let's make sure now that Nvidia can not rebuild ( call home):
post back the URL from if any entry for Nvidia exists:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*
cat -n /etc/apt/sources.list | pastebinit
tail -v -n +1 /etc/apt/sources.list.d/* | pastebinit

```
Here if there is any entry for nvidia - STOP - We need to take care of this before re-booting !
Else: no entries for Nvidia, we proceed !
-----------------------------
2) Make sure 'nouveau' is not blacklisted:
##A no-return here is great !##
```

sudo grep 'blacklist.*nouveau' /etc/modprobe.d/*
grep -ri nouveau /etc/modprobe*

ls -la /etc/modprobe.d/ | pastebinit

```
--------------------------
3) make sure there are no other Nvidia driver files on the system:
```

sudo apt-get purge nvidia-\*
sudo apt-get purge nvidia*

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

ls -ld /lib/nvidia*
dpkg -l  | grep nvidia

sudo service lightdm stop ##run this just in case##

```
----------------------------------
4) install the open source driver 'nouveau' ! :
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install linux-headers-generic
sudo apt-get install dkms
sudo apt-get install ubuntu-desktop
sudo apt-get install xserver-xorg-video-nouveau
sudo update-initramfs -u

```
--------------------------

Let's see what is !
Re-boot and let's see that beautiful Desk Top you have missed for so long.

[INDENT][INDENT]hey, It could happen !
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-04
IT WORKED!  And, it is nice and warm out side (Hell didn't freeze over).

```

sudo rmdir /home/andy/andy/Nvidia

```

Directory not empty.  It still had 'nstel Nvidia Howto'.  I  tried to remove it, no luck, but it seemed harmless. 

```

http://paste.ubuntu.com/ 8489279/
http://paste.ubuntu.com/8489308/
http://paste.ubuntu.com/8489361/

```

```

sudo apt-get install xserver-xorg-video-nouveau

```
Said '... nouveau is already the newest version'
```

sudo update-initramfs -u

```
I got '/boot/initrd.img-3.13.0-36-generic'

Reboot. It was a slow boot, but boot it did, to my desktop w/o asking for a password.

THANK YOU, many times over.  It was slow, but interesting.

Now, I have a lot of catch-up work to do.

Andy

---

### Post by Bashing-om on 2014-10-04
wg5o; Outstanding !

You do good work !

As to 'rmdir' yep, will not delete a directory if files are present, shucks slipped my mind that the directory was not empty !

One other way
```

rm - R /home/andy/andy/Nvidia/

``` Will (R)ecursively remove the file(s) and then the directory. - not to be entered into lightly -

When you get caught up, come back here, and let's check and clean your system up and make sure all is current !

[INDENT]this fat lady is going to sing yet
[/INDENT]

---

### Post by wg5o on 2014-10-06
I have put the change suggested in this post on hold, pending some catch-up work, and have discovered a lingering problem:

When I start the computer, the boot is slow, but it comes up with my desktop with all of its folders.  If I let the computer go to sleep, the folders are gone when I wake it.  A reboot is needed to get back to normal.  Is this a bug in 14.04, or is it unique to my box?

Andy

---

### Post by Bashing-om on 2014-10-06
wg5o; Yuk !

No, that behavior is not normal. We may add that to the list .. After - at that later time - we do all the clean up and such.
Then look at the start up process .. get ready to learn to read log files !

-------------------------
Off Topic:
I presently have made myself some booting problem, and I may not be on the forum as frequent for a while.
Study to see how I can do this (my booting) better, so this does not happen again will keep my focus.

[INDENT][INDENT]we work through
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-10-12
wg5o; Hello !

Just checking in to inquire of your status.

[INDENT]can not leave you Un-Happy[/INDENT]

---

### Post by wg5o on 2014-10-12
Bashing-om:  Worst that previously described, although I have been able to catch up on my record keeping,etc.  The computer is usable, but when it goes to sleep and I wake it, not only are my desktop folders missing, but applications are sometimes  non-responsive, and I have to restart, which seems quite slow.

Thank you for not forgetting me.

Andy

---

### Post by Bashing-om on 2014-10-12
wg5o; Well, wellll..
I have been considering .. and I just do not know .

BUT -> let's clean thing up and make sure the system is ship shape as far as the package manager is concerned:
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

#check the condition of the package manager now
sudo apt-get -f install
sudo dpkg --configure -a

```

IF all that returns clean, time to start looking at the logs !
Let's take a look at the logs and see if there is any adverse conditions reported:
```

dmesg | pastebinit

```
for a place to start .
If all looks good in the initial dmseg, we do another after a sleep/wakeup cycle; see if there is a difference.

Maybe better then to start a new thread on this, and gain a new wider audience.

[INDENT][INDENT]this fat lady is going to sing, yet
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-14
I did catch up on some of the stuff I skipped:

#78 Couldn't make the backup work.  Did 'cat' and it looked easy, so took a chance.  Got a long error message:
'(gedit:2446): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files'

#90  I couldn't make the remove statement work, so decided it (the Nvidia file) is harmless & gave up.

#95
```

http://paste.ubuntu.com/8562138/

```

Andy

---

### Post by Bashing-om on 2014-10-14
wg5o; Welp"

#78: You can safely ignore, a script file complaining, One size here does not fit all.
#90: Humm ...let's look. Post back the output of:
```

ls -al /home/andy/andy/

```
========================================
#95
Now the biggy, all this time delay, I saw several gaps in the times.
> 
6.494679] EXT4-fs (sdb1): INFO: recovery required on readonly filesystem
12.029058] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)12.029058] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)12.029058] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)

28.355073] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro

Best take a check on the file system here, see what is going on and maybe check the hard disk's health ??

Wireless is not an area of expertise with me - to say the least, and I sure do not know why ipv6 and not ipv4 - IT sure is taking a long time to get wireless up. 
> 
 29.332869] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
54.256512] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
 60.445278] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
63.291529] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


And here is the big time delay:
The warning seen several times.
> 
78.028803] init: plymouth-upstart-bridge main process ended, respawning78.028803] init: plymouth-upstart-bridge main process ended, respawning
180.079186] systemd-hostnamed[2363]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
906.878841] [<f8450120>] rhine_interrupt [via_rhine]
[  906.878843] Disabling IRQ #23
[ 1370.815710] systemd-hostnamed[2686]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!

this bears investigating: nss-myhostname

And I assume this is the end of the log and you are finally up
> 
[ 1735.382319] Btrfs loaded
[ 2462.054534] perf samples too long (3096 > 2500), lowering kernel.perf_event_max_sample_rate to 50000

-----------------------------
These issues have nothing to do with the original thread, we will be much better served to start new threads on each of them.
We would be drifting way to far off-topic to continue with them in this thread.

all in all I think there are solutions
[INDENT][INDENT]where there are solutions there are no problems
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-15
```

http://paste.ubuntu.com/8567219/

```

nss-myhostname ... sorry, I don't get it.  In fact, most of the above is Greek to me.  I assume it has to do with the excessive startup time.  The other prolem is loosing my desktop follders and associated unresponsiveness after the computer has been asleep (but, not after every nap).  All of this started when I hit the 'Upgrade" button, back in August.  

Now that I have a sort of useful box, should I just make a live DVD for 14.04 and start over?

Andy

---

### Post by Bashing-om on 2014-10-15
wg5o;

Let's back up a bit and re-confirm. 
From post #95, did all run, and

```

#check the condition of the package manager now
sudo apt-get -f install
sudo dpkg --configure -a

```
does not show any errors ?

If all runs clean and no errors are reported, then we can conclude that the upgrade is completed successfully, and move on the these other issues.

For sure need to check the 'sdb' drive.

For think'n purposes presently regarding the big delay in booting:
We do:
```

apt-cache search on the package:

```
> 
sysop@1404mini:~$ apt-cache search nss-myhostname
libnss-myhostname - nss module providing fallback resolution for the current hostname
sysop@1404mini:~$


So it is connected to networking, some how. What I do not know is where or how. I am not sure of what path here to pursue. IF the wireless were doing ipv4 routing rather than ipv6, would that resolve the "Changing the local hostname might make it unresolveable. Please install nss-myhostname! "?

Let's keep in mind we may just follow the advise and install it .. but might behoove us to look at what is set for "hosts names" .
post back:
```

cat /etc/hosts
cat /etc/hostname

```
And we ponder what action to take.

Pending: sdb1 ! -> recovery required on readonly filesystem

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]othertimes I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-15
Package Manager:  No problem there.

Sbd1 seems OK.  It has Win XP, and it seems happy (I was afraid that we deleted it).
SBD2 is Ubuntu ... tell me how to check it., please.
```

apt -catch search nss-myhostname

```
After a pause, it just returns to the prompt.  Also, thanks.  My prompt is fixed, now, 'andy@andy:~$'

Network:  I use witeless with a 2Wire Home Portal 1000HW, located in another room.  
Hosts:  It said the listed (five) lines are desirable for IPv6 capable hosts.  Each line included 'ip6.'

Andy

---

### Post by Bashing-om on 2014-10-16
wg5o' Hey ;

Overall looking good.

My little mind can only deal ( and focus well ) on one thing at a time.

Presently the " nss-myhostname " issue.
So once more:
Post back the outputs of terminal commands:
```

apt-cache search nss-myhostname
cat /etc/hosts
cat /etc/hostname

```
as we have the system "Please install nss-myhostname!"; maybe we best give it what it wants ??
Chances are, as you have the prompt as you desired, the 2 files are correct, but I want to know.

As I do not have wireless, and I manage my networking manually, I can not look at things - in your perspective - from my system.

"apt-cache search libnss-myhostname" advise sure looks promising in your case ! Note this is [color=green]libnss[/color].

I think this is what we are going to do.

[INDENT][INDENT]practicing to make perfect
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-16
#101

[http://paste.ubuntu.com/8576718/](http://paste.ubuntu.com/8576718/)
[http://paste.ubuntu.com/8576728/](http://paste.ubuntu.com/8576728/)
[http://paste.ubuntu.com/8576735/](http://paste.ubuntu.com/8576735/)

Wireless is just more convenient, otherwise, the result seems the same.
The prompt is back to normal, great!

My biggest problem is having to restart almost every time the computer goes to sleep.  I looked for the control to set the delay to an hour or such and didn't find it in "power.'  I'll look again.  Anyway, all the desktop folders disappear, and often, but not always, the system becomes unresponsive.  

Andy

---

### Post by Bashing-om on 2014-10-16
wg5o; yeah !


In the file:
/etc/host
Change the line" 127.0.1.1	andy-System-Product-Name
with your text editor
to " 127.0.1.1	andy " without the quotes

Now reboot, and show a new dmesg output:
```
 dmesg | pastebinit

```

and let's see if we still need to install ' libnss-myhostname ' .

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-17
Here you go.  I hadn't edited anything in s long, it took a  while to work out how it goes.
```

http://paste.ubuntu.com/8581246/

```

Andy
77

---

### Post by Bashing-om on 2014-10-17
wg5o; Well, 

Now looking much better !

However, we have:
> 
2.869597] usb 3-1.4: new low-speed USB device number 4 using uhci_hcd
[    3.029595] usb 3-1.4: New USB device found, idVendor=045e, idProduct=00b9
[    3.029599] usb 3-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.029602] usb 3-1.4: Product: Microsoft USB Wireless Mouse
[    3.029605] usb 3-1.4: Manufacturer: Microsoft
[   18.047661] Adding 1646624k swap on /dev/sdb5.  Priority:-1 extents:1 across:1646624k FS
[   18.174061] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready

A whopping 15 second delay between adding the USB devices and starting "swap" !! What in the world ??
OK, what all have you got plugged into the USB ports ? ( the USB ports themselves are found and configured, no problem ) Can you remove all and do you have a common wired mouse to attach ? -> see if it is wireless that is driving the system nuts .

Then we have this delay:
> 
24.650459] init: cups main process (654) killed by HUP signal
[   24.650476] init: cups main process ended, respawning
[   26.710030] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.710495] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.681355] init: samba-ad-dc main process (845) terminated with status 1
[   30.233893] audit_printk_skb: 75 callbacks suppressed


A wireless printer ? How does 'samba' play into the picture ?

Then in addition is:
> 
   33.996229] wlan0: associate with 00:0d:72:44:d1:29 (try 1/3)
44.004139] wlan0: deauthenticating from 00:0d:72:44:d1:29 by local choice (reason=3)

10 seconds just to validate the wireless internet ?? While nothing else is being done ???
---------------------------------------
Not recovering from sleep :
maybe this is a pointer in the right direction ?
> 
 0.089954] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
0.090062] acpi PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
<snip>
0.092191] pci 0000:00:10.0: System wakeup disabled by ACPI
<snip>

0.100295] pci 0000:04:01.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'


File systems ! You had advised that sdb1 "Sbd1 seems OK. It has Win XP, and it seems happy" the system does not agree:
> 
   2.571674] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)


Best check that all the ducks are in a row here, and some config file ( samba ???) is not in error reference to sdb1 as a Windows partition.
Check for sure what the system sees:
```

sudo fdisk -lu
sudo blkid

```


-------------------------
Do you actually use a floppy drive ??
> 
[    1.212160] Floppy drive(s): fd0 is 1.44M

=============================
Pull every thing off the box not required to boot, 
disable 'samba'
Make sure 'sdb1' is in fact a linux "ext4" partition, and nothing is referencing it as a Windows partition.
do you have a hard wired connection we can go to -- ??? Come back up on a wired internet connection.

Now let's see what dmesg says about the booting situation:
```

dmesg | pastebinit

```

When we can get it booting on bare metal no problems, then ! start installing the add-ons and see what results, one thing at a time to find the source of the delays ! ( ASPM & ACPI kept in mind ).
Add one, check dmesg . add another, check dmesg.

[INDENT][INDENT]sounds like a plan to me
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-18
Remember, this stuff started when I pushed 'upgrade,' on 8/29.  Well, it was slow starting, but nothing like this.

Code block #1.  USB devices:  Unused lead for my camera; Cheap four-way hub; Printer; Microsoft mouse.
I removed the mouse and pliged in an old, rolling ball mouse.

Code block #2.  Well, Google thinks samba is related to printing, but I use a little USB printer.

Code block #3.  No comment.

Code block #4.  I did 'pcie_aspm=force,' and set the 'suspend' time bac to 5 minutes.

Code block #5.  No comment, except, I think Grub lives pm sdb1.

```

sudo fdisk -lu 
Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x80408040

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   321669494   160834716    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfd478bc7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    74862591    37430272   83  Linux
/dev/sdb2        74862961    78156224     1646632    5  Extended
/dev/sdb5        74862963    78156224     1646631   82  Linux swap / Solaris
andy@andy:~$ ^C
andy@andy:~$ 
Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x80408040

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   321669494   160834716    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfd478bc7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    74862591    37430272   83  Linux
/dev/sdb2        74862961    78156224     1646632    5  Extended
/dev/sdb5        74862963    78156224     1646631   82  Linux swap / Solaris
andy@andy:~$ ^C
andy@andy:~$ 
[/copde]

[code]
andy@andy:~$ sudo blkid
/dev/sda1: UUID="132B03D7C0FE68F1" TYPE="ntfs" 
/dev/sdb1: UUID="da3b3759-3caf-43af-9250-004036d3bd3a" TYPE="ext4" 
/dev/sdb5: UUID="5f07c745-d80e-4462-850a-46d88599557a" TYPE="swap" 
andy@andy:~$ 

```

Floppy:  I would like to, but 12.04 wouldn't let me.  It looks as if they fixed that!  [I] find floppies easier to handle and store than CDs, and I have a lot of them handy.)

Note:  I have no idea how to disable samba.  If I have to, I'll lug the modem (or whatever it is) in and plug it in.  Let's try wireless first (see my opening comment).

```

http://paste.ubuntu.com/8587096/

```

---

### Post by Bashing-om on 2014-10-18
wg5o; Morning !

For your reference is my old dual AMD athlon system; it boots in 11 seconds.
Note I do have some minor bios issues and as well some small configurations I could address.
see:
[http://paste.ubuntu.com/8585705/](http://paste.ubuntu.com/8585705/)

Your latest dmesg: I do not know what to think .. for all intents you have booted in less than a minute, and then the system spazes out !
We have again " nss-myhostname is not installed. " which should now not be an issue .
Repairing the kernel, for some reason ??

Maybe reboot and see if this is a one time occurrence ?

My dmesg ->
[INDENT][INDENT]may not be a great standard
[INDENT][INDENT][INDENT]but a good one
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-19
During the night, I realized that the wireless link is not part of the problem.   The wireless link comes up after the system boots.

I think the problem of loosing desk top folders is fixed.  But, someting worse may be going on.  After starting the sym. while I did something else, then waking it and starting to work, every thing sort of fell apart.  I got a partial login page, it broke up, and I had to manually turn the computer off and restart.  Is my HD going out?  

On restart, I timed Grub to desktop, about 73 seconds.

```

http://paste.ubuntu.com/8591259/

```

This is still with just the old ball mouse and no USB devices.

Andy

---

### Post by Bashing-om on 2014-10-19
wg5o; Agrreed !

Not good to see this again - this soon !
> 
2.437945] EXT4-fs (sdb1): INFO: recovery required on readonly filesystem
[    2.437951] EXT4-fs (sdb1): write access will be enabled during recovery


From the 'disk utility" run a SMART test on the hard disk. Does it pass ?

And then from the liveDVD run a file system check (again ).
Activate GParted, and turn swap off ( right click, on 'sdb5" -> "swap off" )
Then run terminal commands:
```

sudo e2fsck -C0 -p -f -v /dev/sdb1

```

IF errors are reported:
```

sudo e2fsck -f -y -v /dev/sdb1

```

Hold our breath here, see what results .. then consider where we go from here.

[INDENT][INDENT]when we know better we can do different.
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-19
1. I used 'Disks,' and it said all ok.
2. I don't have a live DVD.  I got into trouble by pushing, 'Upgrade,' in Update Manager.
3. Installed GParted and did , 'swap off.'
4. Problem:
```

andy@andy:~$ sudo e2fsck -C0 -p -f -v /dev/sbd1
e2fsck: No such file or directory while trying to open /dev/sbd1
Possibly non-existent device?
andy@andy:~$ 

```

Andy

---

### Post by Bashing-om on 2014-10-19
wg5o; Ah My ..

We can only run a file system check when the partition(s) are not mounted, The easier way to do this is from a live DVD(USB).

As you do not have one, Then we stop right here, make one up, run the file system check from the liveDVD. As the system keeps reporting " recovery required on readonly filesystem ". The thing to do now is heed the advise and comply.
Get 14.04: (L)ubuntu ->
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

verify the .iso file:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Burn the .iso as an image:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Verify the DVD integrity:
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

As you have a single core motherboard, and unity is such a resource hog, you will find that (L)ubuntu will run much faster on your system. (L)ubuntu is designed to run on the older hardware. If/When that time comes.
In the meantime we will use the (L)ubuntu liveDVD to do the file system check/repair.

[INDENT][INDENT]That is just what I think
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-21
I think it may be time to buy a new computer.  Yesterday, the screen image broke up, a long bunch of code followed, and concluded:

"Kernel panic -not syncing: Fatal exception drm_kns_helper: panic occurred, switching back to console" ... but it didn't seem to go to to console.  (That's terminal, isn't it?).

I got stuck, again.  I decided to make a live thumb drive on my wife's relatively new Mac.  I worked my way up to where I was ready to burn the image to the drive, and the Mac demanded a password.  Wife couldn't find it!  Worse, because I know her negelgent ways, and feel sure I recorded it for myself; I couldn't find it, either.

Andy

---

### Post by Bashing-om on 2014-10-21
wg5o; Naawwhh;

Sounds more like the kernel is contaminated, rather than the hardware failing - though that too does happen, nothing last forever.

Might I suggest that you burn a DVD and test the operating system from a DVD ?? In some way, before blaming the hardware.
I know from direct experience that the AMD Sempron -singe core- chips will not run (u)buntu, my wif's graphics station, and we had to go to (L)ubuntu when 10.04 went End-Of-Life. ( Non-support of Adobe Flash in linux made her go back to Windows ).
Hence is my suggestion to try (L)ubuntu.

As to the Mac EIFRT (?) I can not advise, I have not touched a Mac in years. I would assume, however, that the firmware onboard is to do with a form of "secure Boot", and with out that password, one will not change the boot order. Nor, do I think that the file format on Mac is compatible with that of 'buntu. Hence I do not know that a DVD burned on Mac will work on an AMD based operating system. But mind you, I do not know know.

Does Windows still boot on that box ? .. There are means to burn the ubuntu image to disk from Windows .

[INDENT][INDENT]when it rains it pours
[INDENT][INDENT][INDENT][INDENT]all we want to do is compute
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-23
1.  Thanks for the XP suggestion.  I had sort of forgotten about it.

2.  I now have a good, live Lubuntu CD ... although I almost wasted my whole supply of blank CDs before I got a good one.

3.  I think I found one part of the slow boot:  It was set to boot on the hard disk last.

4.  Ubuntu 12.04 ran fine on my box.  Are you telling me that 14.04 won't, and we have been wasting our time?

Andy

---

### Post by Bashing-om on 2014-10-23
wg5o; Hey hey !

Andy , OK, IF the liveDVD of (L)ubuntu boots, hardware is all good, so back to kernel issues !

> 
3. I think I found one part of the slow boot: It was set to boot on the hard disk last.

Great ! ( had not occurred to me )

> 
4. Ubuntu 12.04 ran fine on my box. Are you telling me that 14.04 won't, and we have been wasting our time?

As 12.04 ran fine, 14.04 will run even better. So, no; in that case we are not wasting our time.

So to fixing this install:
Boot the liveDVD of (L)ubuntu -> "try ubuntu " mode -> terminal
Terminal commands:
```

sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see: man e2fsck for details##
sudo e2fsck -f -y -v /dev/sdb1

```

and let's see if the files system gets fixed !

[INDENT][INDENT][INDENT]worth a shot
[/INDENT][/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-24
```

sudo e2fsck -C0 -p -f -v /dev/sdb1

```
Seemed to reset the clock and count the files.
```

sudo e2fsck -f -y -v /dev/sdb1

```
It said something like:  e2fsck: no such file ... trying to open /dev/sbd1.

We are not there yet.  Last night, I couldn't post because the server wasn't available, and after waiting, and the computer went to sleep, the display fell to apart.   This morning (10/24), I pushed the start button and went to eat.  Back, I woke the computer and the desktop folders were gone and it wouldn't respond.  Manual restart.  Warning, 'System program problem detected.'  I've gotten a lot of them.

Andy

Andy

















this morning (10/24)

---

### Post by Bashing-om on 2014-10-24
wg5o; Weehlll;

My thoughts:
Until such time as the file system check/repair runs clean AND the package manager is in a consistent state, we can do nothing.
> 
sudo e2fsck -f -y -v /dev/s[color=red]d[/color]b1

IF that is the input to the command, then yes the response is true, that 'sbd' "no such file" is accurate ; the device is "s[color=green]d[/color]b1".
- as in sdb1 -
(frustration can get the better of us, sometimes we do not see the forest for that tree.)

Small steps, make sure the file system is consistent, make sure the package manager is consistent
THEN, I think, focus on the unity (compiz) issues.

[INDENT][INDENT]A plan of attack
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-24
Sorry about the failing brain cells.  I redid #115 and got:

lubuntu@lubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sdb1
/dev/sdb1: Superblock last mount time is in the future.
	(by less than a day, probably due to the hardware clock being incorrectly set)  FIXED.
/dev/sdb1: Superblock last write time is in the future.
	(by less than a day, probably due to the hardware clock being incorrectly set).  FIXED.
                                                                               
      285873 inodes used (12.20%, out of 2342912)
         357 non-contiguous files (0.1%)
         534 non-contiguous directories (0.2%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 236682/204/1
     4395324 blocks used (46.97%, out of 9357568)
           0 bad blocks
           1 large file

      194566 regular files
       25863 directories
          57 character device files
          25 block device files
           0 fifos
          46 links
       65350 symbolic links (48893 fast symbolic links)
           3 sockets
------------
      285910 files
lubuntu@lubuntu:~$ 


lubuntu@lubuntu:~$ sudo e2fsck  -f -y  -v /dev/sdb1
e2fsck 1.42.9 (4-Feb-2014)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

      285873 inodes used (12.20%, out of 2342912)
         357 non-contiguous files (0.1%)
         534 non-contiguous directories (0.2%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 236682/204/1
     4395324 blocks used (46.97%, out of 9357568)
           0 bad blocks
           1 large file

      194566 regular files
       25863 directories
          57 character device files
          25 block device files
           0 fifos
          46 links
       65350 symbolic links (48893 fast symbolic links)
           3 sockets
------------
      285910 files
lubuntu@lubuntu:~$ 

That seems OK, except it had the same time prob. as before.  I'll reboot and see what happens.

Andy

---

### Post by Bashing-om on 2014-10-24
wg5o; Humm ??

I agree, the file system check looks good. Confirms the file system is intact ! - Why then were there errors in dmesg ???

So OK, how 'bout we boot to terminal in the install ( grub boot menu -> 'e' key -> exchange quiet splash with text, ctl+x -> login here ).
What now returns:
```

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a
sudo dpkg -C

```
to insure that the package manager is all in a happy state.

IF and only IF that returns all good and clean;
From that same Command Line Interface do;
Terminal command:
```

sudo service lightdm start

```
starting the desktop from terminal and watching to see the errors that may be generated.
IF the GUI starts, to return to terminal (and reexamine for reported errors ); key combo ctl+alt+F1.
To go back to the GUI from TTY1, key combo ctl+alt+F7 .


To reboot gracefully from the terminal ( if needed) :
```

sudo shutdown -r now

```
to shutdown completely:
```

sudo shutdown -h now

```

[INDENT][INDENT]things sure look promising to me
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-25
1.  "grub boot menu -> 'e' key -> exchange quiet splash with text, ctl+x -> login here" gave :  "Syntax error.  Incorrect command." 

2.  I restored the original text (Esc), and F10 to boot.  Opened terminal and entered the list of commands thru 'sudo dpkg -C.'  All was well thru the last command.  That produced:

andy@andy:~$ sudo dpkg -C
[sudo] password for andy: 
The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 desktop4shared       file manager to access 4shared web account from PC

andy@andy:~$

Andy

---

### Post by Bashing-om on 2014-10-25
wg5o; Humm,

Do not know how "desktop4shared " would effect the desktop, but needs to be addressed .
However, on checking I get:
> 
sysop@1404mini:~$ apt-cache show desktop4shared
N: Unable to locate package desktop4shared
E: No packages found
sysop@1404mini:~$

Please verify that the package name as given is correct.

As to " login here" gave : "Syntax error. Incorrect command."
If you typed - login here - yeah, not a valid command. What I meant, at the TTY1 prompt to 
enter you user name, followed by your pass word ( no response to the screen when pass word is entered).
Once done you would be " logged in " to the system.

Once you have logged in to the system at the TTY1 terminal:
What results from:
```

sudo service lightdm start

```
Holding my breath that 'desktop4shared (??) ' is not a factor.

[INDENT][INDENT]still, after all this time
[INDENT][INDENT][INDENT]work'n to get to the bottom of things
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-25
```

desktop4shared

```

It is correct. I copied and pasted the result.  A year or so ago, I tinkered with getting things set so I could look at this box from the others in the house.  It is probably related to that effort.

```

sudo service lightdm start

```

I can't get grub to remember the changes I make.  I can't get to TTY1 ... 'F' keys don't do it.  I can get to command line in grub, but it doesn't know any of the words in the command you ordered.

Andy

---

### Post by Bashing-om on 2014-10-26
wg5o;

Let's go back to the basics, and re-affirm the focus of our attention.
We need to boot to terminal, this will exclude the GUI as a factor in the boot process, and then we control starting the GUI.

> 
I can't get grub to remember the changes I make. I can't get to TTY1 

An edit to the boot parameters from grub directly will not persist across a reboot. These edits are one time things, and must be repeated each time the system is booted ( though system files can be edited to make it persistent).
So, we have a system with 2 hard disks
1st is Windows on 'sda';
2nd hard drive is ubuntu installed onto 'sdb'

We want to boot ubuntu, exclusive of any thing else:
Start the system, and adjust the boot priority as 'sdb' as the 1st boot priority.
In order to boot to a textual terminal, grub looks for an escape key - there is but a 4 second window of opportunity that grubs looks, and then moves on -> as soon as the bios screen clears depress and hold the right shift key ( as ubuntu is the only system installed on the hard disk, and 'perhaps' Windows is not chainloaded, then the default behavior  is NOT to display the grub boot menu - unless the the boot process is "escaped".
So, the boot process is "escaped" with the right shift key -> grub boot menu. Here there are several means to affect the booting of the system. We want to do a 1 time edit to the boot process and boot to a terminal.
In the grub boot menu, with a normal kernel having an 'asterisk' on the left edge of the selected kernel, press the 'e' key for edit mode.

This brings up the boot parameters screen that can be edited. In this case we want to boot to terminal.

Arrow down to the line similar :
> 
 linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff

- in a default configuration, that is.-
Arrow across to the terms quiet splash, and replace these with the term text;
Key combo ctl+x to continue the boot process;
One should now be booted to a textual terminal - TTY1 . Log into the system:
type your username -> will be prompted for your pass word. Enter you pass word - there is no response to the screen when the pass word is enter (security reasons).

You are now logged in the system, and the GUI is not to this time a factor, just the bare bones operating system; that we control !

Can you reliably boot to terminal ?

[INDENT][INDENT]small steps,
[INDENT][INDENT][INDENT]one thing at a time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-26
I tried following your instructiona, but grub is on the 1st HD, sdba or whatever.   Grub comes up by defualt with its list to choose from, with the 1st choice being *Ubuntu.  I was confused about what you wanted me to type, quotes would help a lot, but I put in 'text' and that worked.  I logged in to TTY1 and while there, went back to #121:
```

sudo service lightdm start

```
My regular desktop came up, and I went on line for this post.

Andy

---

### Post by Bashing-om on 2014-10-26
wg5o; Outstanding !

And you got no errors reported in terminal when you started the GUI (sudo service lightdm start) ?

also:
> 
but grub is on the 1st HD, sdba or whatever


We should consider putting Window's boot code on the 1st hard drive (sda) and grub onto the 2nd hard drive (sdb). If that were done one could boot Windows independent of ubuntu by selecting in bios which hard drive to boot from.

pending still is looking at : 
> 
The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
desktop4shared file manager to access 4shared web account from PC


May be tricky as the package no longer exists !

OK, to the situation of the desk top: When starting from terminal confirm there are no problems .

[INDENT][INDENT]as we seek to find the cause
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-26
```

And you got no errors reported in terminal when you started the GUI (sudo service lightdm start) ?

```
That is correct.
```

We should consider putting Window's boot code on the 1st hard drive (sda) and grub onto the 2nd hard drive (sdb). If that were done one could boot Windows independent of ubuntu by selecting in bios which hard drive to boot from.

```
Nope.  A non-problem: When I boot, Grub comes up with a menu, I can choose one of Ubuntu versions or Windows XP.  If I just hit enter or do nothing, Ubuntu 14.04 LTS  comes up.

Andy

---

### Post by wg5o on 2014-10-26
```

And you got no errors reported in terminal when you started the GUI (sudo service lightdm start) ?

```
That is correct.
```

We should consider putting Window's boot code on the 1st hard drive (sda) and grub onto the 2nd hard drive (sdb). If that were done one could boot Windows independent of ubuntu by selecting in bios which hard drive to boot from.

```
Nope.  A non-problem: When I boot, Grub comes up with a menu, I can choose one of Ubuntu versions or Windows XP.  If I just hit enter or do nothing, Ubuntu 14.04 LTS  comes up.

Andy

---

### Post by Bashing-om on 2014-10-27
wg5o; Humm ..

Andy, I got to think on this. What can differ between starting the GUI from terminal, and from the Display manager (auto) .
I do not have a lot of experience with display managers .. so may take a bit to reconnoiter .

As you are real happy with the booting arrangement, I can sure live with it.


Edit: In the meantime, I am still seeing what I can come up with to isolate the fault.

[INDENT][INDENT]I shall return
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-10-27
wg5o; Hey !

I am making some progress, and I keep coming back to " desktop4shared ".
For instance; See:
[http://seperohacker.blogspot.com/2012/10/solved-4shared-desktop-crashes-on-linux.html](http://seperohacker.blogspot.com/2012/10/solved-4shared-desktop-crashes-on-linux.html) <- 4shared desktop crashes on Linux .

So, I am back to removing this application from the system as you are not currently using it. THEN once removed, see  how unity performs.

[INDENT][INDENT]no quit in my nature
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-27
As I understand it, desktop4shared is for external storage, not desktop sharing.  It must be part of 14.04, since I never heard of it before.  Do what referenced post says?   I think NO; wait for you to tell me how to get rid of it altogether.

Info:  Windows insists on being  first in line, although, somehow Grub gets ahead of it.  Actually, I thought installations with Grub work like mine, or maybe everyone has to have Grub because of the other choices offered?

Andy

---

### Post by Bashing-om on 2014-10-27
wg5o; Well;

Andy, grub is nothing more than a boot loader, and only does what it is configured to do. If you are happy with the way it is functioning, that is all that is important .

I find nothing in 14.04 for " desktop4shared" and I am all for trying to remove it.
What have we got to work with ?
What returns:
```

ls -al /var/lib/dpkg/desktop4shared.list

```

IF that returns that the file does exist, what is in the file - in the event there are problems getting the package manager to purge it ?
```

cat /var/lib/dpkg/desktop4shared.list

```

and we see what can be done from there.

[INDENT][INDENT][INDENT][INDENT]work'n  to make all right
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-28
Well, I hate to admit it, but I missed your post because I forgot I wasn't in the 'Inbox' folder, last evening.  I went off on my own and opened terminal:
```
 
locate desktop4shared

```
It was there, so I cded my way to it and did: 
```

ls

```
A long list resulted.  Today, I went to Ubuntu Softwear Center, which said it was installed and described it in glowing terms.  I pushed, 'remove' and it should be gone.  Now, I'll go do something else and see what happenes when the box naps.

Andy

---

### Post by wg5o on 2014-10-28
Removing desktop4shared seemed to make matters worse, surely not better.

Note:  I keep forgetting that that I frequently get, "System program problem detected," and "Ubuntu has experienced an internal problem."

Andy

---

### Post by Bashing-om on 2014-10-28
wg5o; Hummm ..

Were not for bad luck would have no luck at all ?
> 
Note: I keep forgetting that that I frequently get, "System program problem detected," and "Ubuntu has experienced an internal problem."

Let's see if we can get any hints:
```

dpkg -l desktop4shared
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo dpkg -C

``` depending, maybe we start poking at unity directly, see it it bites back.

[INDENT][INDENT]pound on it long enough
[INDENT][INDENT][INDENT]something is going to give
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-29
```

dpkg -l desktop4shared

```
No package found
```

sudo apt-get update

```
A bunch of packages.  Done.
```

sudo apt-get upgrade

```
I noticed a list of uri/ files with "unknown media" ... Done
```

sudo apt-get -f install
sudo dpkg -C

```
Install said, "0 upgrade, 0 newly installed, 0 to remove, 6 not upgraded."
The last command just returned to the prompt w/o comment.

I'll see what happens next.

Andy

---

### Post by Bashing-om on 2014-10-29
wg5o; All to the good !

File system check is good;
package manager is in a happy state;
But, let's take care of:
> 
0 to remove, 6 not upgraded.

yeah, back in terminal, do:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

Now !
Let's poke at unity and see what.
'dconf' isn&#8217;t a standard bit of software to play with, so proceed with caution.

Boot to terminal, and run terminal commands:
```

sudo apt-get install dconf-tools
dconf reset -f /org/compiz/

```
Log out of your desktop session and back into Unity for changes to take effect.

Step 2
To refresh your Unity launcher with the default set of icons, run the following in a Terminal:
```

unity --reset-icons

```
This command will &#8220;restart&#8221; Unity immediately, running from the Terminal. Closing the Terminal will also &#8216;close&#8217; Unity, so it&#8217;s best to log out and back in after running this command.

Reboot.

Now is unity behaving it's self ? OR do we need to get the more aggressive ?

[INDENT][INDENT][INDENT]maybe YES
[/INDENT][/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-29
Today, 2014/10/29 is significant:
1.  It marks two months that we have been fooling with this mess,
2.  Today's mail brought a live DVD that I ordered.

It may be time to use the DVD and do a complete reinstall?

What the heck is Unity?

After following your instructions, and rebooting, I let the system go to sleep.  It woke nicely, but when I tried to select an icon, it froze, then displayed a long bunch of text, ending in something about, "trappped," the desktop finally broke up completely, so I had to manually restart. 

Andy

---

### Post by Bashing-om on 2014-10-29
wg5o; Welp;; ..

Like this, in 2 months all we have been able to accomplish is to (re-)install the graphics driver, and get you back up on a semi-useful system.
Not to discount the progress made on the learning curve in administering the system.

If at any time frustration and aggravation exceeds the threshold, the nuclear solution is available to (RE-)install.

unity, is the interface between the GUI ( desktop that you see ) and the kernel ( THE operating system foundation).

As unity - your desk top -stands now the only problem is when you resume the system from standby ? 
Are you booting in a reasonable amount of time now ?
In that event we are looking at how power management is utilized.- or maybe even a corruption of the image within the swap partition when either written into or out of swap (??).

As a means to isolate the problem(s) to the install; boot the liveDVD and check how all works in that liveDVD environment. It is not beyond the realms of possibility that there does exist hardware/software/configuration incompatibilities .
In that event we can re-focus our attention.

graphics driver works
file system is intact
package manager is happy
unity is functional - until resumed 

we have come a long way
[INDENT][INDENT]we have no end in sight
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-29
Start time is still quite long, but, if I can push the button, walk away , and find a good computer when I get back, I can live with that.

Yes, having everything fall apart when I wake the computer is the BIG problem.

Also, I keep loosing the mouse pointer (previously unmentioned).  I'm back to the wireless mouse, but the old, wired mouse did the same thing.

It could be that something has failed in the last two months, but everything ran fine (12.04 LTS) until I pushed the upgrade button.

Andy

---

### Post by Bashing-om on 2014-10-30
wg5o; Ok,

We keep plugging away at this.
As we have :
> 
Also, I keep loosing the mouse pointer (previously unmentioned). I'm back to the wireless mouse, but the old, wired mouse did the same thing.

and the mouse is a component of xorg, let's see what hints we get when xorg is re-configured:
From terminal:
```

sudo service lightdm stop
sudo dpkg-reconfigure xserver-xorg

```
which I expect will start a wizard, follow it's prompts to reset what the system is looking for.

Then.once finished, reboot to see the effect:
```

sudo shutdown -r now

```

As we have liveDVDs it might be nice to have confirmation that there is no hardware related issues -> fire up a liveDVD, run it a bit and make sure ALL is functioning from within this live environment. Then we may conclude that the problem(s) reside within the install.

[INDENT][INDENT]something is going to give
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-30
```

sudo service lightdm stop

```

This command caused the screen to go black, with a flashing cusor.  I waited, and waited, nothing happened, and I couldn't type a command or log in or whatever.

I'm using the live DVD to send this.  It seems to be OK, although I did have trouble connecting to the modem/server, even though it immediately found the wifi signal.  This try, I got a nice clean start, and all worked fine.

Andy

---

### Post by Bashing-om on 2014-10-30
wg5o; I can not imagine what:

> 
This command caused the screen to go black, with a flashing cusor. 

could cause this turn of events.

Let's just re-install the desk top;

At the login screen key combo ctl+alt+F1 to get a console;
Log in here and In this console:
```

sudo apt-get install ubuntu-desktop^

```
the ending caret is important ->  re-install the task, which will pull in any missing bits that should be there.

reboot and let's see if there is any effect.

[INDENT][INDENT]sometimes I just do not know
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-10-31
I am 86 years old, have no interest in exploring the mysteries of command line work, we have destroyed my launcher, the spelling dictionary I finally built has vanished, and we are using up a lot of my remaining time on this planet.  So, what is wrong with doing a reinstallation with the live DVD?

I appreciate your devotion to the problem, but I do have a few other things to work on, including my obituary.

Andy

---

### Post by matt_symes on 2014-10-31
Hi

> **wg5o said:**
> ```

sudo service lightdm stop

```

This command caused the screen to go black, with a flashing cusor.  I waited, and waited, nothing happened, and I couldn't type a command or log in or whatever.

I suspect if you had changed to a different VT then you may have got a login prompt as it sounds like you may have been on the VT that lightdm was running on.

> **wg5o said:**
> I am 86 years old, have no interest in exploring the mysteries of command line work, we have destroyed my launcher, the spelling dictionary I finally built has vanished, and we are using up a lot of my remaining time on this planet.  So, what is wrong with doing a reinstallation with the live DVD?

Not wishing to step on any toes here but the first post was on September 7th, 2014. 

Agreed with the re-installation. Stop flogging this dead installation. Backup any data and reinstall. Life's to short.

Kind regards

---

### Post by Bashing-om on 2014-10-31
wg5o; Agreed;

Matt, as always, appreciate your thoughts.

> **matt_symes said:**
> Hi



I suspect if you had changed to a different VT then you may have got a login prompt as it sounds like you may have been on the VT that lightdm was running on.



Not wishing to step on any toes here but the first post was on September 7th, 2014. 

Agreed with the re-installation. Stop flogging this dead installation. Backup any data and reinstall. Life's to short.

Kind regards

Agreed, the return is not worth the effort; we are getting nowhere faster. Back up and do a fresh clean install and be done with the matter.

[INDENT][INDENT]it is that time
[/INDENT][/INDENT]

---

### Post by wg5o on 2014-11-04
Well, I did the reinstallation from the purchased DVD, and I have been working to recover my backuped data (the backup program, Backintime, has baulked), but my data are safe on an external drive.

Interestingly, the problem I was having with waking the computer seems to still be there, and I've had one case of the display falling apart.  I also have had notices of program problems, and have allways said to send in a report.

There is no end to my trouble.

Andy, 11/04

---

### Post by Bashing-om on 2014-11-05
wg5o; Hello ;

I do feel for you:
> 
Interestingly, the problem I was having with waking the computer seems to still be there, and I've had one case of the display falling apart. I also have had notices of program problems, and have allways said to send in a report.

There is no end to my trouble.

It is regretful that the condition persist even in a new install. I do not have a solution right off-hand.
May I suggest that you start a new thread with this theme to gain the attention of those who do have the knowledge/experience to deal with this situation.

We do so want to make things right !

[INDENT][INDENT]If I knew everything
[INDENT][INDENT][INDENT][INDENT]I would not be me
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wg5o on 2014-11-05
Good idea.  I just wanted to let you know the 'end-point' status.  I'll accumulate some more experience, and, if necessary, start a new thread.  I installed updates today, and the problem may have been corrected.

Thanks again,

Andy

---

### Post by Bashing-om on 2014-11-05
wg5o; Yeah ;

Updates can work wonders.

[INDENT][INDENT]fingers crossed
[/INDENT][/INDENT]

---

