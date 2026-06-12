---
title: "[SOLVED] Linux Noob - broke grub"
date: 2007-07-25
forum: Installation &amp; Upgrades
---

### Post by mikeliketrike on 2007-07-25
Let me preface this by saying I'm running of the Ubuntu Live CD now, which was created about a week ago and I've read through this and other forums that I found via Google and I don't know enough about Linux to put the pieces together to solve my problem. Ok.

Using a Linux Rescue CD, I partitioned off 40GB for Ubuntu. I then loaded and installed (at least I think I installed) Ubuntu into that space, making a swap partition during the process and then rebooted.

After my computer's POST grub came up and got past stage 1.5, but then tells me to wait while grub loads then error 2 comes up.

So I loaded the Live CD, searched around, and found instructions on how to reinstall grub through a terminal.  No matter what I type in for the command, even if it's just 'grub', I get an error saying 'Illegal instruction (core dumped)'.

Then, I found other instructions to log in as a super user, 'su', and reinstall grub.  But when I try that, it doesn't accept the password I typed in when installing Ubuntu initially.  

The drive that I installed Ubuntu on is mounted (at least I think it is, when I right click on it on the desktop it gives me an option to unmount), and I can browse files in it, so I think I've done that part correctly.  But, I'm not sure of a. what I did wrong and b. how to make everything right.

I just want to be able to dual boot Ubuntu and WinXP and learn more about Linux, that's it.  HELP!:confused:

---

### Post by Gremlinzzz on 2007-07-25
What i would do using the XP cd i would go to install windows and delete the linux partitions making that partition free space . then i would reboot the live ubuntu cd and click to install when the partiton part comes up choose use largest continuous free space. ubuntu does the rest.

---

### Post by floke on 2007-07-25
Don't forget to check the LiveCD to make sure it burned correctly - there's an option for this on the first menu you get when it boots up. But I would go for a new install - it'll take about 30mins, whereas trying to work out how to reinstall grub on its own could take you 30 days :)

---

### Post by manndani on 2007-07-25
> **mikeliketrike said:**
> 
Then, I found other instructions to log in as a super user, 'su', and reinstall grub.  But when I try that, it doesn't accept the password I typed in when installing Ubuntu initially.  


If you're working from the live cd  you will not have a password, at least I don't.

---

### Post by Gremlinzzz on 2007-07-25
Another thing you could try is fixmbr. that stands for fix master boot record than once back in windows delete the linux partitions from windows manager which would make it free space.then put live ubuntu cd in click the install icon when partition part comes up choose use largest continuous free space  how too fix master boot record .Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: fixmbr   at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer.

---

### Post by mikeliketrike on 2007-07-25
> **Gremlinzzz said:**
> What i would do using the XP cd i would go to install windows and delete the linux partitions making that partition free space . then i would reboot the live ubuntu cd and click to install when the partiton part comes up choose use largest continuous free space. ubuntu does the rest.

That sounds reasonable enough.  So I'm clear though... when installing Ubuntu, do I need to create a partition for the swap file?  How about a partition for the boot record (/boot)?

---

### Post by Gremlinzzz on 2007-07-25
When choose use largest continuous free space  ubuntu creates all partitions :guitar:
you will see and choose
Guided - use the largest continuous free space.

---

### Post by mikeliketrike on 2007-07-25
Here's what I did: fixed the master boot record from my windows CD's recovery console, went into windows, right clicked on my computer > manage > disk management > and deleted the partitions I created earlier.  Then, I shut my computer down, ready for round 2.

I booted up, went into the boot menu by hitting F12, put the Ubuntu CD in, booted into the CD, did the disk check from the Ubuntu main menu... no errors.  Then, I went through my second (in as many days) Ubuntu install, this time selecting the largest continuous free space option when on the partition prompt.  Everything seemed to finish fine.  Shut down, took out the CD, booted.

Grub 1.5
Loading Grub Please wait...
Error 2

*expletive**sigh*

I'm back to where I started.  

Oh and btw, thanks for all the great advice so far... I don't think I've ever got such a quick/good response on any forum I recently joined, it's really very impressive.

---

### Post by mikeliketrike on 2007-07-25
In looking at other posts about this subject here's some information that's generally asked:

fdisk results:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7297    58613121    7  HPFS/NTFS

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12257    98454321    7  HPFS/NTFS
/dev/sdb2           12258       14900    21229897+   f  W95 Ext'd (LBA)
/dev/sdb3   *       14901       19929    40395442+  83  Linux
/dev/sdb5           12258       14712    19719756    7  HPFS/NTFS
/dev/sdb6           14713       14900     1510078+  82  Linux swap / Solaris

end of menu.lst:
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=2dee7ecb-900e-4876-b394-80c769144413 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=2dee7ecb-900e-4876-b394-80c769144413 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by sdowney717 on 2007-07-25
[http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)

2 : "Selected disk doesn't exist"

This error is returned if the device part of a device- or full filename refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.

---

### Post by sdowney717 on 2007-07-25
I think grub is looking at the wrong disk or partition and is not configured properly.

Boot into the live CD and then at terminal type 'grub', enter

From there you need to discover where to install grub. I cant remember exactly what the commands are, but I have done this before.

---

### Post by sdowney717 on 2007-07-25
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I think this might help

---

### Post by Gremlinzzz on 2007-07-25
i been searching too found [http://ubuntuforums.org/showthread.php?t=151682](http://ubuntuforums.org/showthread.php?t=151682)
at the end of this donkey kong claims to have fix error 2
[http://www.linuxquestions.org/questions/showthread.php?t=534566](http://www.linuxquestions.org/questions/showthread.php?t=534566)

---

### Post by manndani on 2007-07-26
> **sdowney717 said:**
> [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I think this might help

That way does work,  I've used it several times before,  so easy to follow and never failed me yet.:)

---

### Post by MQMike on 2007-07-26
What you posted from sudo fdisk looks ok, as does everything else.  I'll bet that when you installed this, you didn't install GRUB to the MBR?

Maybe just re-install GRUB, that might make this go.

---

### Post by MQMike on 2007-07-26
Use Ubuntu Live CD
Open a Terminal
Type 
sudo grub
press Enter and wait
Get a GRUB prompt:
grub>
type these commands, pressing Enter after each:

root (hd1, 2)
setup (hd0)
quit
$exit

Close out all windows etc.
Remove CD
Re-boot to test it.

---

### Post by MQMike on 2007-07-26
That should work.  But I’ve said that before many times.
Here’s two references on basic GRUB methods:

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)
(this is one I wrote; also see the many posts following the first post)

Bigpond, home:   [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
(the classic -- esp the GRUB page)

---

### Post by mikeliketrike on 2007-07-26
> **MQMike said:**
> Use Ubuntu Live CD
Open a Terminal
Type 
sudo grub
press Enter and wait
Get a GRUB prompt:
grub>
type these commands, pressing Enter after each:

root (hd1, 2)
setup (hd0)
quit
$exit

Close out all windows etc.
Remove CD
Re-boot to test it.

I tried the above (which was in a previous posted link also) a couple times and still got the same result... error 2.  Per another previous post, both of my hard drives are set to AUTO in my BIOS (and always were).  

I'm going to see what I can find out from the 2 links posted by MQMike (thanks btw) and see how far that gets me.

I really want this to work, so I'll keep trying whatever I can!

---

### Post by MQMike on 2007-07-26
Your menu.lst has the new UUDs, which it should.  I don’t know much about them, except they have caused some people some really subtle problems.  I am told that you can comment those out and use the older sda and sdb notation in the kernel lines.  You ARE getting errors which suggest a bad file reference or some such, right?

The line
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=2dee7ecb-900e-4876-b394-80c769144413 ro quiet splash
would become
# kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=2dee7ecb-900e-4876-b394-80c769144413 ro quiet splash
and add thie following:
kernel /boot/vmlinuz-2.6.20-15-generic   root=sdb3 ro quiet splash

(Note the commented line #. – comment it just to keep it for reference or to revert back.)

Just brainstorming

---

### Post by MQMike on 2007-07-26
One thing, these UUIDs must be consistent with what's in your filesystem table (/etc/fstab)

To see your UUIDs, use the command:   
$ ls /dev/disk/by-uuid/ -alh   
(Note: “ls” is “l” as in “list”; and “-alh” is also with an “l” as in”list”)

---

### Post by jgfoot on 2007-07-26
I had a very similar problem, also with a two-hard-drive system.  The problem is that the installer wrote grub to the wrong master boot record.  One way to try to fix your problem is to change your BIOS so that the other hard drive is the first one to load.

---

### Post by mikeliketrike on 2007-07-26
First of all, thanks for all the great responses, I've tried them all and they've led me to trying other things, but so far it looks like grub hates my computer.

Here's what I can remember doing for troubleshooting steps, in no particular order:

Reinstalled grub pointing the setup to go to hd0, hd1, and hd1,2.

When find vmlinuz, menu.lst, stage1, and stage2 they all point to hd1,2.

Here's what happens when i try cat (hd1,2)/etc/fstab
```
grub> cat (hd1,2)/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=2dee7ecb-900e-4876-b394-80c769144413 /               ext3    defaults,erro
rs=remount-ro 0       1
# /dev/sdb6
UUID=44014073-2732-484a-9544-db23606bb89a none            swap    sw
   0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

I noticed the error on the linux partition (/dev/sdb3), so I tried un/remounting it multiple times and get the same result.  Is that a problem?  Is that THE problem?  How can I fix it...if I need to?

My super awesome BIOS doesn't allow me to select what hard drive boots first, so I did something familiar and played with jumpers, no luck, same grub error 2.

I tried editing menu.lst through gedit by typing 'sudo gedit /boot/grub/menu.lst' and it brought up a blank gedit screen.  If i go through the file browser to the file it shows the whole thing, but can't edit the read only file.

Tried loading Ubuntu AND Windows through a chainloader in a terminal window and nothing changed after i typed 'boot' and hit enter.

If I type 'configfile  (hd1,2)/boot/grub/menu.lst' then I get the grub menu with the appropriate options (haven't tried actually going into one yet because it's up right now and I don't want to loose everything I typed).

So after all that, I'm still at the same spot, error 2.

Edit:
Ok, so I just tried going into Ubuntu 2.6.20-15-generic after typing in configfile  (hd1,2)/boot/grub/menu.lst and got Error 16: Inconsistent Filesystem Structure.  When I tried going into Windows I got 'Segmentation fault (core dumped)'.

---

### Post by Gremlinzzz on 2007-07-27
Error# 2 : "Selected disk doesn't exist"

This error is returned if the device part of a device- or full filename refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.

---

### Post by rbmorse on 2007-07-27
I love GRUB

---

### Post by mikeliketrike on 2007-07-27
It's fixed!!!!

Through all the troubleshooting/installs either the /boot partition or the / ext3 partition or the /swap partition was part of an extended ntfs partition on hd1.  
So at the beginning of each install, on my 2nd hard drive (where I was attempting to install Ubuntu), I had a primary partition, an extended one, both formatted in ntfs.  Each time I installed, whether I created the partitions manually or let Ubuntu do it for me, either the /boot or / or /swap partition was auto-black-magically going into the extended partition.  Which apparently doesn't play well with grub.
So I booted into Windows, moved/deleted everything in the extended partition, then deleted it along with the ones that were being used by Ubuntu, so now all there was on my 2nd hard drive was a primary ntfs partition and lots of beautiful free space.
After that I reinstalled Ubuntu, letting it find and use the free space on my 2nd hard drive on it's own and now grub works.  ******* woot.

Thank you to everyone who helped with my 3 day dilemma, I appreciate all the great input.  Through It all I learned more about Linux/Grub than I would have otherwise, so that's a good thing... right?

Now to enjoy Live CD free Ubuntu for a little bit before I head out to watch the Simpsons movie.:popcorn:

---

### Post by MQMike on 2007-07-28
“Each time I installed, whether I created the partitions manually or let Ubuntu do it for me, either the /boot or / or /swap partition was auto-black-magically going into the extended partition. Which apparently doesn't play well with grub.”

It’s apparent there was nothing wrong with GRUB, as was implied by a negative comment above by rbmorse.

Obviously, there was a glitch in the partitioning, which may have been in the installer or having to do (somehow) with your system setup (drives).  GParted was not in the picture, so it can’t be blamed either, although I don’t recall hearing many complaints about it in this regard.

Congratulations, mikeliketrike, I’d say that was darned good detective work!

---

