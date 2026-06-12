---
title: "Interrupted update to 11.10, now computer wont boot. fix?"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by PFactorial on 2011-10-23
**[SIZE=3]Hi all,[/SIZE]**
 
 
 
I started the download and upgrade to 11.10 from 11.04 on root account then I went to a guest account to continue my work/play/whatever while the root account installed the packages I logged out of the guest account later, and the computer didnt respond so I did a hard reset(which was pretty stupid but the computer wasn't responding) and then when I boot, a splash screen of "UBUNTU 11.04" appeared and there was a bit at the bottom about not being able to mount a network or something like that. It went along the lines of "Press S to skip boot or Press M to manually configure". And it would never do anything except sit there. So can anyone help me out? Thank You!

---

### Post by drs305 on 2011-10-23
Try pressing 'Skip' (S), which is often caused by an entry error in /etc/fstab. If the system can run without mounting the errant partition entry, it may boot and allow you to correct fstab (note the error before you press S).

You can also try booting to the Recovery mode and see if there is an option to fix broken packages. Run that, if it is an option, and then resume the boot.

The next thing I'd try would probably be to accomplish an fsck check on the Ubuntu partition. Do this from a LiveCD (the partition must be unmounted). Substitute the correct drive/partition values for X,Y:

```
sudo unmount /dev/sdXY  # Just to ensure it's not mounted
sudo e2fsck -fyv /dev/sdXY

```

Reboot. It's very possible the problem is with mixed apps from the two releases, but this may clear things up if the installation either didn't get very far or came close to completing.

---

### Post by PFactorial on 2011-10-23
I tried booting the computer again, but now all my monitor does is freak out and flash between "Cannot display this video mode" and going idle

---

### Post by PFactorial on 2011-10-23
See, "Cannot display this video mode" happens everytime I start the computer up, but it goes to the login screen soon after. This time, after a quiet period of "Cannot display this video mode", I see the little round loading circle of Ubuntu and it starts freaking out

---

### Post by cbowman57 on 2011-10-23
Have you tried logging into Recovery mode and select Fix Broken Packages?

---

### Post by PFactorial on 2011-10-23
That screen doesnt even pop up anymore. My monitor just flashes and spazzes out

---

### Post by cbowman57 on 2011-10-23
That would be a problem.  Do you have multiple kernel entries in your grub screen?  If so try an alternate kernel.

---

### Post by PFactorial on 2011-10-23
Oh I can boot into a rescue CD. But I dont really know what to do while in the session

---

### Post by PFactorial on 2011-10-24
<deleted>

---

### Post by cbowman57 on 2011-10-24
Here's a chunk of mine, maybe it will help you construct a new one. ```
# / was on /dev/sda1 during installation
UUID=11a2b514-dc28-4d48-a533-ae3821a6507b /               ext4    relatime,errors=remount-ro 0       1
```

---

### Post by PFactorial on 2011-10-24
uh. do i just paste that in?
sorry i'm a newb, recently introduced to linux

---

### Post by PFactorial on 2011-10-24
Here is what i got after "sudo e2fsck -fyv /dev/sda1"
[FONT=monospace]
sudo e2fsck -fyv /dev/sda1
e2fsck 1.41.14 (22-Dec-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  207322 inodes used (16.54%)
     329 non-contiguous files (0.2%)
     174 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 177456/153
 1900719 blocks used (38.01%)
       0 bad blocks
       2 large files

  145021 regular files
   28751 directories
      59 character device files
      26 block device files
       0 fifos
       0 links
   33449 symbolic links (29611 fast symbolic links)
       7 sockets
--------
  207313 files

[/FONT]

---

### Post by PFactorial on 2011-10-24
BTW Thanks to all of you for replying so quickly!
I've never seen a more helpful community.

---

### Post by cbowman57 on 2011-10-24
> **PFactorial said:**
> uh. do i just paste that in?
sorry i'm a newb, recently introduced to linux

Try it this way ```

/dev/sda1 /               ext4    relatime,errors=remount-ro 0       1
```

---

### Post by drs305 on 2011-10-24
> **PFactorial said:**
> "aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0"

That's the contents of /etc/fstab/
i'm pretty sure my hard drive is on sda1.

That is not the content of your *installed* version of fstab. To view or modify your fstab, you have to mount the Ubuntu partition first. If Ubuntu is on sda1, you would:
```

sudo mount /dev/sda1 /mnt
gksu gedit /mnt/etc/fstab
```
I don't think your fstab is the problem, but that is how you would access it.

While you have the Ubuntu partition mounted, you can also try to edit the Grub menu. There are some settings in the menuentry that set the video mode, and there is a problem with at least one of them. The symptoms don't exactly match your problem, but it won't hurt to try changing them.

With the Ubuntu partition still mounted, open the Grub configuration file:
```
gksu gedit /mnt/boot/grub/grub.cfg
```
Find this [COLOR="DarkRed"]line[/COLOR] and change it to **[COLOR="Navy"]this[/COLOR]**. In Grub 1.99 it's about line 46. Do not run 'update-grub'.

>   [COLOR="DarkRed"]set gfxmode=<some value or 'auto'>[/COLOR]
  **[COLOR="Navy"]set gfxmode=640x480[/COLOR]**

Next find your first 'menuentry' and the two lines below it:
> menuentry 'Ubuntu, with Linux  <kernel version>' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	[COLOR="DarkRed"]set gfxpayload=$linux_gfx_mode[/COLOR]
Change the last line to:
> **[COLOR="Navy"]set gfxpayload=text[/COLOR]**
Save the file and try rebooting.

If it works we will make the changes permanent.

---

### Post by PFactorial on 2011-10-24
> **cbowman57 said:**
> Try it this way ```

/dev/sda1 /               ext4    relatime,errors=remount-ro 0       1
```

So do I paste that in?

---

### Post by PFactorial on 2011-10-24
> **drs305 said:**
> That is not the content of your *installed* version of fstab. To view or modify your fstab, you have to mount the Ubuntu partition first. If Ubuntu is on sda1, you would:
```

sudo mount /dev/sda1 /mnt
gksu gedit /mnt/etc/fstab
```I don't think your fstab is the problem, but that is how you would access it.


Oh. Right. This is the Ubuntu partition's fstab: 
```
 # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=3ac9c069-613f-4065-90d0-8553f5b6049b /               ext4    errors=remount-ro 0       1 

```

---

### Post by PFactorial on 2011-10-24
Okay, so I replaced
UUID=3ac9c069-613f-4065-90d0-8553f5b6049b /               ext4    errors=remount-ro 0 
with this:
/dev/sda1 /               ext4    relatime,errors=remount-ro 0       1
and got this error message:
```

init : ureadahead main process (262) terminated with status 5

```

---

### Post by PFactorial on 2011-10-24
BTW it doesnt flash anymore. It just displays "Cannot display this video mode" with no "going idle"s or spazzes of yellow light

---

### Post by PFactorial on 2011-10-24
So do I change it back or do I leave fstab like that?

---

### Post by drs305 on 2011-10-24
I don't know what is going on with your system.

I am not quick to request a reinstallation, but often it is faster than trying to rectify an interrupted upgrade. If you have data or settings you want to retrieve, you can mount the Ubuntu partition via a LiveCD and copy them to a partition or external device that won't be used during the installation. I'd go through this entire thread once more to make sure you didn't miss anything.

Of course, it's your decision as to how long you wait to try to analyze the problem. Perhaps someone will come along to provide a decent solution, or you can find something by searching the net with your error messages.

---

### Post by PFactorial on 2011-10-24
> **drs305 said:**
> That is not the content of your *installed* version of fstab. To view or modify your fstab, you have to mount the Ubuntu partition first. If Ubuntu is on sda1, you would:
```

sudo mount /dev/sda1 /mnt
gksu gedit /mnt/etc/fstab
```I don't think your fstab is the problem, but that is how you would access it.

While you have the Ubuntu partition mounted, you can also try to edit the Grub menu. There are some settings in the menuentry that set the video mode, and there is a problem with at least one of them. The symptoms don't exactly match your problem, but it won't hurt to try changing them.

With the Ubuntu partition still mounted, open the Grub configuration file:
```
gksu gedit /mnt/boot/grub/grub.cfg
```Find this [COLOR=DarkRed]line[/COLOR] and change it to **[COLOR=Navy]this[/COLOR]**. In Grub 1.99 it's about line 46. Do not run 'update-grub'.


Next find your first 'menuentry' and the two lines below it:

Change the last line to:

Save the file and try rebooting.

If it works we will make the changes permanent.

Wait! It did work! except it led me to this page:
GNU GRUB Version 1.99 ~ rc1-13ubuntu3

ubuntu, with linux 2.6.3811-generic
ubuntu, with linux 2.6.3811-generic(recovery mode)
previous linux versions
Memory test(memtest8bt)
Memory test(memtest8bt,serialconsole115200)

and it prompted me to choose one of those
Then, when i chose the first choice
it led to this:
init : ureadahead main process (262) terminated with status 5
which only happened after i modified fstab. I tried putting the original contents back, but i still got the same error message

ITHINKITSWORKING

---

### Post by drs305 on 2011-10-24
> **PFactorial said:**
> 
ITHINKITSWORKING

Don't forget to try one of the older kernels 'hidden' in the "Previous" subfolder if you don't get the first one to boot.

Added: If you do have to try a 'previous' entry, if it doesn't work try to edit the menuentry as you did on the first one.

---

### Post by PFactorial on 2011-10-24
so, does 
"init : ureadahead main process (262) terminated with status 5" 
mean anything?

---

### Post by PFactorial on 2011-10-24
I tried "ubuntu, with linux 2.6.38-08-generic" in the previous linux subcategory
and my computer just stopped responding, monitor went idle

---

### Post by PFactorial on 2011-10-24
I also tried "ubuntu, with linux 2.6.38-10-generic" in the previous linux subcategory
and the same ureadahead error came up

---

### Post by drs305 on 2011-10-24
> **PFactorial said:**
> I tried "ubuntu, with linux 2.6.38-08-generic" in the previous linux subcategory
and my computer just stopped responding, monitor went idle

I searched earlier today for the ureadahead errors and didn't come up with anything definitive.

Can you boot to the recovery mode and get to a root prompt? Do you have an Nvidia video card?

---

### Post by PFactorial on 2011-10-24
Yes, I believe I can get to a root prompt, and Yes, I do believe that my integrated graphics card is NVIDIA

---

### Post by PFactorial on 2011-10-24
And is this:
[http://forums.techarena.in/operating-systems/1428761.htm](http://forums.techarena.in/operating-systems/1428761.htm)
a good way to resolve it?
since deleting config files seems a bit risky...

---

### Post by drs305 on 2011-10-24
There is a thread that discusses ureadhead:
[http://ubuntuforums.org/showthread.php?t=1518110&page=2]("http://ubuntuforums.org/showthread.php?t=1518110&page=2")

I can't say the 'sed' solution will work. If you get to the Recovery root prompt, don't use 'sudo'.

If the solutions in that thread don't help, here are the only two things I can think of:

1. Reinstall ureadahead. Make sure you have an Internet connection with the first command before running the second:
```
sudo apt-get update
sudo apt-get purge ureadahead
sudo apt-get install ureadahead
```

2. Reinstall nvidia-current. Assuming you still have Internet
```
sudo apt-get purge nvidia-common nvidia-current
sudo apt-get install nvidia-common nvidia-current
```

---

### Post by PFactorial on 2011-10-24
wait, but if I'm doing this from the rescue disk, how will it affect my ubuntu install?

---

### Post by drs305 on 2011-10-24
> **PFactorial said:**
> wait, but if I'm doing this from the rescue disk, how will it affect my ubuntu install?

Those commands are only to be run from the Recovery mode from your normal Grub menu. 

If you had to run them from the LiveCD, you would have to use a chroot procedure. I have some chroot instructions for another issue in the 'Chroot' link in my signature line.

---

### Post by PFactorial on 2011-10-24
oh, so how do i connect to a wireless network with WEP security in recovery mode?

---

### Post by PFactorial on 2011-10-24
because recovery mode is just that black terminal, right?

---

### Post by PFactorial on 2011-10-24
Never Mind. I suppose I can't get into recovery mode because of that ureadahead error.

---

### Post by PFactorial on 2011-10-24
So do I reinstall grub2 like the CHROOT tutorial says?

---

### Post by PFactorial on 2011-10-25
Okay, so I tried to do the CHROOT thing like this, using your method to first mount the device then CHROOTing it with his method:
[http://askubuntu.com/questions/35168/ubuntu-netbook-update-interrupted](http://askubuntu.com/questions/35168/ubuntu-netbook-update-interrupted)
and this is what happened:
```

mint / # sudo apt-get install ureadahead
sudo: unable to resolve host mint
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ureadahead
0 upgraded, 1 newly installed, 0 to remove and 85 not upgraded.
Need to get 23.9 kB of archives.
After this operation, 147 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  ureadahead
Install these packages without verification [y/N]? y
Err http://archive.ubuntu.com/ubuntu/ natty/main ureadahead i386 0.100.0-11
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/u/ureadahead/ureadahead_0.100.0-11_i386.deb  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
mint / # 


```

---

### Post by PFactorial on 2011-10-25
<deleted>

---

### Post by PFactorial on 2011-10-25
I tried this:
```

sudo mount --bind /etc /mnt/etc

```
and it allowed me to install the ureadahead package, but I'm not sure if that was the right way to do it
THEN:
No other linux kernel would boot EXCEPT "ubuntu, with linux 2.6.38-08-generic" in the previous linux subcategory
THEN:
It showed me this:
```

an error occurred while mounting /var/lock
press S to skip mounting, M for manual recovery
mount:mount point var/lock is a symbolic link to nowhere
mount:according to mtab, none is already mounted on /run
mountall:mount /run [404] terminated with status 1

```
AND THEN:
I pressed S.
THEN:
Some successful stuff popped up, but this error came up:
```

update-binfmts: unable to open /var/lib/binfmts

```
And the newer versions of the linux kernel didn't respond. There was a flashing "_" on a black screen forever.

---

### Post by drs305 on 2011-10-25
The 'wicked' message may have occurred because it looks like you are using a 'Natty' CD. If the system got far enough to install Oneiric, you may very well have problems trying to chroot into an 11.10 installation with a 11.04 disk.

Regarding the /var error, the ureadahead error message you have been getting: In other threads the Error 5 message has to do with a separate /var partition. While you may not have a separate /var, it could point that some sort of corruption of the /var folder is your problem. I don't know how you would go about solving that other than trying to boot an 11.10 CD, running the chroot procedure, and again trying to purge and reinstall ureadahead. But if you are going to that much trouble, a clean installation would be faster and simpler.

---

### Post by PFactorial on 2011-10-25
But if you do a reinstall, won't some data files be erased? Such as the user info, preferences, etc

---

### Post by drs305 on 2011-10-25
> **PFactorial said:**
> But if you do a reinstall, won't some data files be erased? Such as the user info, preferences, etc

Yes. But your computer will work....

If you can mount the Ubuntu partition, which you apparently can, you can copy any data you want. You can also copy your /home folder and the /etc folder for future reference on your new installation. You wouldn't be able to use the files directly in most cases, but you could refer to their contents when setting up your new installation.

If you have the space, you could leave the existing partition intact and create a new partition for the installation. That way the entire old installation wouild be available for either reference or repair should you come across a solution later. It would also be much easier to chroot from a more or less identical installation to try to repair the original one.

Other than trying to reinstall ureadahead, though, I've just about run out of recommendations. You'll have to wait for someone else to chime in or start doing some detailed Internet searches for solutions found by others.

---

### Post by PFactorial on 2011-10-25
So could you guide me through CHROOTing through a 11.10 CD?
because I'm not sure I know how to chroot.

---

### Post by drs305 on 2011-10-25
> **PFactorial said:**
> So could you guide me through CHROOTing through a 11.10 CD?
because I'm not sure I know how to chroot.

Click on the 'Chroot' link in my signature line. The thread was designed to help users repair their Grub installations. You would be mounting *sda1* 

The procedure would be the same all the way through the Internet check (apt-get update). 

At that point, you would run the 'apt-get purge ureadahead' and 'apt-get install ureadahead' commands.

We have still not established whether or not your upgrade resulted in a possible usable installation.  If the chroot repair doesn't work, you could try running the repair commands as well. Since you are in a chroot, you don't need 'sudo':

```
apt-get install -f
dpkg --configure -a
```

---

### Post by PFactorial on 2011-10-25
So you don't have to bind any folders together?

---

### Post by drs305 on 2011-10-25
> **PFactorial said:**
> So you don't have to bind any folders together?

The command "for i in ....." does all that for you - the /dev, /dev/pts, /proc and /sys folders.

---

### Post by PFactorial on 2011-11-02
```

ubuntu@ubuntu:~$ sudo mkdir /mnt/temp
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/temp
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i; done
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
ubuntu@ubuntu:~$ sudo chroot /mnt/temp
 ________________________________________
/ "Unfortunately there are so many ads   \
| for old tin cans for sale when you     |
| search the web so a search is useless" |
|                                        |
\ Husse Apr 4 2007                       /
 ----------------------------------------
  \
   \   \_\_    _/_/
    \      \__/
           (oo)\_______
           (__)\       )\/\
               ||----w |
               ||     ||
ubuntu / # sudo apt-get purge ureadahead
sudo: unable to resolve host ubuntu
E: Could not open lock file /var/lib/dpkg/lock - open (2: No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ubuntu / # apt-get purge ureadahead
E: Could not open lock file /var/lib/dpkg/lock - open (2: No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ubuntu / # 

```

Did I do something wrong?

---

### Post by awtovey on 2011-11-03
I'm in exactly the same situation as you and am really frustrated. The most I can do is boot off a USB but the session seems to be isolated from anything else. When I try to access the files from my old Ubuntu version I get a 'permission denied' message.

If someone can help here it would be great. I dont understand code or commands or anything so throwing that at me will be useless. I'd need talking through it. Would really appreciate a helping hand here. Andrew

---

### Post by drs305 on 2011-11-03
> **PFactorial said:**
> 
Did I do something wrong?

The way you chrooted looks correct. As you discovered, you don't use 'sudo' in a chroot'.

Normally the 'lock' error message means that the user has two APT processes trying to run at the same time. An example would be having Synaptic open while also running an "apt-get" command. In this case, it looks like it can't *find* the 'lock' file. While it's possible the 'lock' file doesn't exist, it's also possible there the system folders didn't get mounted properly or there is a structural problem with your folders.

This points to something we touched upon earlier - a problem with the /var folder. You can try just creating the 'lock' folder but I suspect there are bigger issues with your /var or /var/lib/dpkg folder. 

To create the lock file (use sudo if in your normal installation):
```
touch /var/lib/dpkg/lock
```
I suspect this isn't going to resolve your bigger issue.

The only other thing I can think of if your /var folder is corrupt would be to try to mount the CD's /var folder during the chroot. I don't know if it contains all the files necessary to accomplish the 'ureadahead' operations or not, but it might. If you mount the CDs /var folder, I'd run only the ureadahead commands and then exit chroot and umount /var.

While accomplishing the chroot, after running the "for i..." command, also mount the /var command:```

Edited:
[s]sudo mount /var /mnt/temp/var[/s]
sudo mount -B /var /mnt/temp/var
```

---

### Post by PFactorial on 2011-11-03
ubuntu@ubuntu:~$ sudo mkdir /mnt/temp
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/temp
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i; done
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
ubuntu@ubuntu:~$ sudo mount /var /mnt/temp/var
mount: /var is not a block device
ubuntu@ubuntu:~$ 

That is what i got after trying the sudo mount

---

### Post by PFactorial on 2011-11-03
Is the animal thing weird/out of place?
because I never saw it while playing with the terminal in my installation
I only saw it on the linux mint live cd.

---

### Post by PFactorial on 2011-11-03
and this is what I got after doing the lock file thing:
```

ubuntu@ubuntu:~$ sudo mkdir /mnt/temp
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/temp
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i; done
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
ubuntu@ubuntu:~$ sudo mount /var /mnt/temp/var
mount: /var is not a block device
ubuntu@ubuntu:~$ sudo chroot /mnt/temp
 _________________________________________
( You attempt things that you do not even )
( plan because of your extreme stupidity. )
 -----------------------------------------
   o
    o
        .--.
       |o_o |
       |:_/ |
      //   \ \
     (|     | )
    /'\_   _/`\
    \___)=(___/

ubuntu / # touch /var/lib/dpkg/lock
touch: cannot touch `/var/lib/dpkg/lock': No such file or directory
ubuntu / # 

```

---

### Post by drs305 on 2011-11-03
Sorry, you would have to use the same extended command as for the others:

```
sudo mount -B /var /mnt/temp/var
```
But even then I don't think it's going to work. I'm guessing your /var folder is messed up and I don't know a way to recreate it without reinstalling.

---

### Post by PFactorial on 2011-11-03
So if you did a reinstall, what would you lose?

---

### Post by PFactorial on 2011-11-03
<deleted>

---

### Post by drs305 on 2011-11-03
> **PFactorial said:**
> So if you did a reinstall, what would you lose?

Customizations/configurations you have made (shortcuts, links, extra installed packages, etc). 

More importantly, any data files you have stored in any files in your Ubuntu partition (normally in /home/<yourusername>). During the installation, you are supposed to be able to retain things in your /home folder if you choose not to format that partition (using the Choose Something Else/Manual Partitioning option), but I personally would not trust any data to this procedure.

You can transfer your /home folder to a separate partition and retain some customizations if desired.

---

### Post by PFactorial on 2011-11-04
NEW UPDATE

I reinstalled ureadahead and this is what I got after booting the oldest linux kernel:
```

Filesystem check or mount failed
A maintenance shell will now be started
CONTROL-D will terminate this shell and continue booting after re-trying filesystems
root@cardamom : ~#

```
and it was a terminal flashing screen thing.

---

### Post by drs305 on 2011-11-04
To accomplish an fsck check,you can run the following from the LiveCD (since the / must be unmounted):
```
sudo e2fsck -fyv /dev/sda1
```
or from a running system you can schedule an fsck check on the next boot with this command:```

sudo touch /forcefsck
```

---

### Post by PFactorial on 2011-11-04
This is my fsck check result:
```

ubuntu@ubuntu:~$ sudo e2fsck -fyv /dev/sda1
e2fsck 1.41.14 (22-Dec-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  207310 inodes used (16.54%)
     331 non-contiguous files (0.2%)
     174 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 177459/153
 1900805 blocks used (38.02%)
       0 bad blocks
       2 large files

  145026 regular files
   28749 directories
      59 character device files
      26 block device files
       0 fifos
       0 links
   33441 symbolic links (29603 fast symbolic links)
       0 sockets
--------
  207301 files

```

---

### Post by PFactorial on 2011-11-16
anyone?

---

### Post by PFactorial on 2011-11-19
So how would you reinstall? Would you just install alongside it, or what?

---

### Post by drs305 on 2011-11-19
> **PFactorial said:**
> So how would you reinstall? Would you just install alongside it, or what?

I would create a new partition with Gparted and then use the manual partitioning option during the installation to designate the newly-made partition. Ubuntu should find any existing swap partition and use it, so you shouldn't have to designate it or create a new one.

Once it completes the installation, you might be able to use or at least check the contents of the previous installation for various customizations you may have made. Evenutually you could then just reformat the old installation once you are sure there is nothing you need from it, and use the space for data or another OS.

---

