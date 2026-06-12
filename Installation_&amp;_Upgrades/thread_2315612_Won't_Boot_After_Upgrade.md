---
title: "Won't Boot After Upgrade"
date: 2016-03-01
forum: Installation &amp; Upgrades
---

### Post by HDTimeshifter on 2016-03-01
I have a Dell Optiplex 390 running 14.04 LTS and after an upgrade on Sunday requiring a reboot, it says something like "No grub, going into rescue mode". I tried rebooting several times with the 3 finger salute, then holding down the power key to force shut down and restarting, but always goes to rescue mode. Help and "?" are no help at the command line. I ran the Dell UEFI ROM diagnostics and the disk drives passed as well as the intensive memory tests. I ended up reinstalling Ubuntu 14.04 from a DVD, but after the updates, it boots up and says "serious disk errors found - ignore, <some other option that I can't remember>, and manual repair. I had an older computer with the same disk error message on boot that appeared for a year or years, but would still boot up so I kind of think it just means there are some bad sectors, not a fatal disk error. I selected ignore, but then it says "waiting for network initialization", then "waiting 60 more seconds for network initialization", then blank screen with solid underscore cursor at upper left. I tried unplugging and re-plugging in the switch power cable without any different result. The LAN cable port has been lit up correctly even before cycling the switch. So, is the hard drive bad? Should I run an extensive test on it?

---

### Post by Bashing-om on 2016-03-01
HDTimeshifter; Hi !

My take and my thoughts.
In this situation I would first run a file system check/verify/repair.

Boot up a liveDVD(USB) of 14.04 ... and to run the check:
terminal commands:
#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
as per the output of:
```

sudo fdisk -lu

```
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
```

sudo e2fsck -C0 -p -f -v /dev/sda1

```
#if errors: -y auto answers yes for fixes needing response see: man e2fsck
```

sudo e2fsck -f -y -v /dev/sda1

```
fsck [http://www.thegeekstuff.com/2012/08/fsck-command-examples/](http://www.thegeekstuff.com/2012/08/fsck-command-examples/)

depending on what the file system check reveals, may consider RE-Installing grub.
Not to say we do not also have a broken graphic's driver here .

[INDENT][INDENT]there is that way that seems right;
[INDENT][INDENT][INDENT]but leads to a broken system
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by HDTimeshifter on 2016-03-02
The Dell UEFI diagnostics extensive tests passed for all hard drives and all other components, but failed on the optical drive with an error like "OPN spindle failure". I'm no longer able to boot from the DVD, even when manually selecting the DVD drive for one-time bootup from the UEFI menu. I also have a USB that I made bootable and copied the Ubuntu installation files onto, however, it doesn't seem to work as it stops at some point after the "man" icon. I'm going to pull the DVD drive this weekend and replace it with a spare and try booting from DVD again.

Thanks Bashing-om.

---

### Post by HDTimeshifter on 2016-03-06
I replaced the DVD drive and booted from a SeaTools CD and ran a long test (2.5 hours) on the hard drive (250 GB) which showed no errors. Then I booted from a live Ubuntu DVD, ran e2fsck, which showed numerous "multiply claimed blocks" that I fixed, however, upon reboot the system still says serious disk errors found and reboots whenever I select the "manual repair" option, or hangs if I choose the "ignore" option (after trying the "network initialization" a couple of times). So I reinstalled Ubuntu from the live DVD (selecting the "erase drive and install new system" instead of the "delete Ubuntu and install" option). The system seems to be working again. I will update if anything changes. By the way, the last time I reinstalled and got the serious disk errors, it was after trying to set up local shares, which kind of looks like it locks up as one of the install dialogs hangs when installing Samba. This time, I installed all the updates first and will try setting up the local shares later. It's a more complicated process setting up local shares in 14.04 LTS than with 12.04 LTS. With previous versions, selecting "set up local sharing" on a drive/folder would simply install Samba and then work (maybe after a restart and/or restarting remote clients as well). Here's a link to thread on that process for anybody interested:  [http://ubuntuforums.org/showthread.php?t=2307655]("http://ubuntuforums.org/showthread.php?t=2307655").

---

### Post by Bashing-om on 2016-03-06
HDTimeshifter; Hey , hey ...

Look'n good .

There is always that when in doubt .. take that nuclear solution and RE_install ...works every time.

When you are satisfied that all is in order, remember, please, to mark this thread 'solved' :
1st post -> thread tools .

[INDENT][INDENT]who ya gonna call
[/INDENT][/INDENT]

---

### Post by HDTimeshifter on 2016-03-11
Marked as unsolved.

After 3 updates last night and a reboot, it said
```
Errors were found while checking the disk drive for /.

Press F to attempt to fix the errors, I to ignore, S to skip mounting, or M for manual recovery.

```

I selected F, then it said:
```
server login:
find: '/var/lib/apt//lists/: No such file or directory
```

I entered:
```
shutdown -r now
```

On booting, it again said
```
Errors were found while checking the disk drive for /.

Press F to attempt to fix the errors, I to ignore, S to skip mounting, or M for manual recovery.

```
I selected F again, then it said:
```
server login:  *Starting CUPS printing spooler/server
*Starting Samba Auto-reload Integration
*Stopping Samba Auto_reload Integration
```

and then hung, with no prompt.

It seems to be an update problem that is corrupting files, not a disk problem.
I rebooted again and after logging in at the command line, it had the same find '/var/lib/apt//lists/' error, then a bunch of /usr/lib update... /usr/lib/update_notifier/update..., /usr/lib/ubuntu-release..., /usr/lib/update-notifier errors.

Then I booted from a live DVD and ran e2fsck which reported 159 non-contiguous files and 198 non-contiguous directories, but no other errors.

---

### Post by Bashing-om on 2016-03-11
HDTimeshifter; Ouch !

For sure:
> 
find: '/var/lib/apt[color=red]//[/color]lists/: No such file or directory

is a correct statement, as it is NOT a valid file path.
The question then is where is the advisory originating ?
As it 1st appears in booting .. might be that the error is in the (F)ile (S)ystem (TAB)le ?

We can quickly check this:
what is in that control file ?
```

cat /etc/fstab

```
let's verify what the system is "automounting" .

[INDENT][INDENT]something, somewhere, somewhen
[/INDENT][/INDENT]

---

### Post by HDTimeshifter on 2016-03-11
```
UUID = {a UUID}  /     ext4  errors = remount_ro  0  1
UUID = {a UUID}  none  swap  sw                   0  1
```

---

### Post by Bashing-om on 2016-03-11
HDTimeshifter; Well ...

I see no fault there ..

What about the target error condition ?
Can we see a badly named file from:
```

ls -al /var/lib/apt/

```

[INDENT][INDENT]just another thought
[/INDENT][/INDENT]

---

### Post by LostFarmer on 2016-03-11
have you checked memory ?   Bad memory can cause all sorts of weird failures to files and file system.  It is a long shot but.

---

### Post by HDTimeshifter on 2016-03-12
Ok, so there's no apt directory or file in /var/lib Sounds like the apt files are missing? Suggestions from here?

LostFarmer, I ran all the UEFI ROM tests and everything passed. I ran one of the longer tests on memory too.

---

### Post by Bashing-om on 2016-03-12
HDTimeshifter; Ouch !

check that again ! :
```

ls -al /var/lib/apt/

```
on my system the return :
```

sysop@1404mini:~$ ls -al /var/lib/apt/
total 76
drwxr-xr-x  6 root root  4096 Mar 12 00:08 .
drwxr-xr-x 51 root root  4096 Dec  1  2014 ..
-rw-r--r--  1 root root 34801 Mar 12 00:08 extended_states
drwxr-xr-x  2 root root  4096 May 19  2013 keyrings
drwxr-xr-x  3 root root 20480 Mar 12 12:02 lists
drwxr-xr-x  3 root root  4096 May 19  2013 mirrors
drwxr-xr-x  2 root root  4096 Apr 12  2013 periodic
sysop@1404mini:~$ 

```

IF you are missing this crucial/critical system directory ...

I just do not have a good solution; there are so many things that would be dependent on ALL files being present and valid . IF we were to take the time and effort to attempt to rebuild, there would always be that element of doubt we have all back (keyrings !) in a consistent state. I would have no faith.

[INDENT][INDENT][INDENT]trust is the foundation of all
[/INDENT][/INDENT][/INDENT]

---

### Post by HDTimeshifter on 2016-03-12
ls-l /var/lib/apt/
No such file or directory.

ls -l /var/lib
drwxr-xr-x 2 ... 4096 ... rtkill
drwx------ 3 ... 4096 ... sudo

Abbreviated since I'm typing from phone and no brackets available for code and this server is in the basement while my other Internet connected PC is upstairs. I'm just going to try reinstalling again. Arrgh!

---

### Post by Bashing-om on 2016-03-12
HDTimeshifter; Uh Huh ....

In this situation of the absence of critical system files:
> 
I'm just going to try reinstalling again. Arrgh!

as much as it hurts, I agree.
A clean fresh install is the thing to do.

[INDENT][INDENT]a solid foundation
[/INDENT][/INDENT]

---

