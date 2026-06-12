---
title: "Problem unmounting RAID 5 to do e2fsck"
date: 2014-04-24
forum: Installation &amp; Upgrades
---

### Post by bphillips2 on 2014-04-24
Ok, I'm a bit of a beginner, but I'm confident enough to follow instructions and fill in most gaps.  I'm having trouble adding a drive to my RAID 5 set up.

I'm following the instructions [here]("http://www.allmyit.com.au/mdadm-growing-raid5-array-ubuntu") and am at the point where I need to extend the file system onto the free space.  The instructions provide say the following (my notes in [COLOR=#ff0000]red[/COLOR]):
[COLOR=#666666][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#666666][FONT=Arial]Now its time to move onto expanding the current file system onto the free room on the array. We will first need to unmount the current raid array using:[/FONT][/COLOR]
> $sudo umount  /dev/md0[COLOR=#666666][FONT=Arial]Replace &#8220;/dev/md0&#8243; with your raid array.[/FONT][/COLOR]
[COLOR=#666666][FONT=Arial][COLOR=#ff0000]I did this, but had to add -l to the command (sudo umount -l /dev/md0).  Without the -l I couldn't get it to unmount.  It would say "Device is busy".  When using the -l it appears to unmount, at least it does not cause an error.[/COLOR]

Now we use the e2fsck command to check the file system (will take around 10 minutes on a 1TB array):[/FONT][/COLOR]
> $e2fsck -f /dev/md0[COLOR=#666666][FONT=Arial]Once again replace &#8220;/dev/md0&#8243; with your raid array.[/FONT][/COLOR]
[COLOR=#666666][FONT=Arial][COLOR=#ff0000]When entering this command next, I get the following result:

> [FONT=Verdana]brad@home-server:~$ e2fsck -f /dev/md0[/FONT][/COLOR][/FONT][/COLOR]> 
[COLOR=#ff0000]e2fsck 1.42 (29-Nov-2011)
/dev/md0 is mounted.  


WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

 [/COLOR][COLOR=#666666][FONT=Arial][COLOR=#ff0000][FONT=Verdana]Do you really want to continue<n>?[/FONT][/COLOR][/FONT][/COLOR][COLOR=#666666][FONT=Arial][COLOR=#ff0000]

I of course hit "n" to stop it.

Now back at the prompt, I attempt to unmount the RAID again using
[/COLOR][/FONT][/COLOR]
> $sudo umount  /dev/md0[COLOR=#666666][FONT=Arial]
[COLOR=#ff0000]I get 
> [FONT=Verdana]brad@home-server:~$ sudo umount /dev/md0[/FONT][/COLOR][/FONT][/COLOR]> 
[COLOR=#ff0000] [/COLOR][COLOR=#666666][FONT=Arial][COLOR=#ff0000][FONT=Verdana]umount: /: not mounted[/FONT][/COLOR][/FONT][/COLOR][COLOR=#666666][FONT=Arial][COLOR=#ff0000]


[/COLOR][COLOR=#000000]I'm at a loss.  Does anyone know what I can do to correct this?
[/COLOR][COLOR=#ff0000]
[/COLOR][COLOR=#000000]If this info helps, here is my disk info.  sda is the new drive I am trying to add
[/COLOR][COLOR=#ff0000]
[/COLOR]> [COLOR=#222222][FONT=Verdana]brad@home-server:~$ lsblk[/FONT][/COLOR][/FONT][/COLOR]> 
NAME    MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda       8:0    0   1.8T  0 disk  
&#9492;&#9472;sda1    8:1    0   1.8T  0 part  
  &#9492;&#9472;md0   9:0    0   4.5T  0 raid5 /
sdb       8:16   0 931.5G  0 disk  
&#9500;&#9472;sdb1    8:17   0 916.4G  0 part  
&#9474; &#9492;&#9472;md0   9:0    0   4.5T  0 raid5 /
&#9492;&#9472;sdb2    8:18   0  15.1G  0 part  
  &#9492;&#9472;md1   9:1    0  60.3G  0 raid5 [SWAP]
sdc       8:32   0 931.5G  0 disk  
&#9500;&#9472;sdc1    8:33   0 916.4G  0 part  
&#9474; &#9492;&#9472;md0   9:0    0   4.5T  0 raid5 /
&#9492;&#9472;sdc2    8:34   0  15.1G  0 part  
  &#9492;&#9472;md1   9:1    0  60.3G  0 raid5 [SWAP]
sdd       8:48   0 931.5G  0 disk  
&#9500;&#9472;sdd1    8:49   0 916.4G  0 part  
&#9474; &#9492;&#9472;md0   9:0    0   4.5T  0 raid5 /
&#9492;&#9472;sdd2    8:50   0  15.1G  0 part  
  &#9492;&#9472;md1   9:1    0  60.3G  0 raid5 [SWAP]
sde       8:64   0 931.5G  0 disk  
&#9500;&#9472;sde1    8:65   0 916.4G  0 part  
&#9474; &#9492;&#9472;md0   9:0    0   4.5T  0 raid5 /
&#9492;&#9472;sde2    8:66   0  15.1G  0 part  
  &#9492;&#9472;md1   9:1    0  60.3G  0 raid5 [SWAP]
sdf       8:80   0 931.5G  0 disk  
&#9500;&#9472;sdf1    8:81   0 916.4G  0 part  
&#9474; &#9492;&#9472;md0   9:0    0   4.5T  0 raid5 /
&#9492;&#9472;sdf2    8:82   0  15.1G  0 part  
  &#9492;&#9472;md1   9:1    0  60.3G  0 raid5 [SWAP]
[COLOR=#666666][FONT=Arial][COLOR=#222222][FONT=Verdana]sr0      11:0    1  1024M  0 rom [/FONT][/COLOR][/FONT][/COLOR][COLOR=#666666][FONT=Arial][COLOR=#ff0000]
[/COLOR]
[/FONT][/COLOR]

---

### Post by Double.J on 2014-04-24
Hi there! 

Afraid I've only grown a raid once and didn't have this problem, but I didn't want your question to go unanswered so thought I'd jump in.

Just a thought, but does mounting the raid read only and I mounting resolve the processes running on it?
```
sudo mount -o ro /dev/md0 /wherever
``` 
if it's still stuck in the is mounted/isn't mounted debacle, maybe try
[CODE]sudo mount -o remount,ro /dev/md0 /wherever[CODE]

Jj

---

### Post by bphillips2 on 2014-04-24
Thanks for the response Double.J

Your response led me to another question.  I see in your code you suggested that I need to replace "/wherever" with the directory I want to mount the file system into.  Problem is, I don't know what that is.  Is there a command I can use to see what directory it is currently mounted into?

This lead me to another possible solution.  There is a comment on the tutorial I was using:
> [COLOR=#666666][FONT=Arial]If you&#8217;re raid is mounted as something important to the system, e.g. as /home, it is best to go to single user mode (Grub / Recovery mode) prior to extending the file system.[/FONT][/COLOR]
Could this possibly be my issue? If it is mounted into /home, how do I go into single user mode?

Thanks for the help thus far.

---

### Post by Double.J on 2014-04-24
Hey,

well I can help to see all mounted devices:
```
mount
```

since it's supposed to be mounted by default, I'm thinking it should be in /etc/fstab? I know by default things in ubuntu are mounted to /media, though I'm not sure this applies to system raid? As far as I know if you need single user mode, you have to enable root. It's pretty easy to do, but I can't post it here as it's against forum rules to advise on it sorry!

Jj

---

### Post by steeldriver on 2014-04-24
It looks like /dev/md0 contains your system's root partition (/) - if that's the case, you will need to boot from a live CD / USB system in order to run the fsck, I think

---

### Post by bphillips2 on 2014-04-24
Thanks again for the help! Your answer helped lead me to what I was needing.  I just had to reboot in recovery mode in order to perform the command.

Thanks!

---

### Post by Double.J on 2014-04-24
Actually thinking about this, I think we've answered our own question - if it's the raid device for home, it'll be mounted at /home, if it's your mail server stuff it's mounted at /var/mail and it it's the root directory, it's mounted at /?

i did just add a bit of goolging to the mix and found that you can see which processes are using the mount point with 
```
fuser -m /mountpoint
``` and add a -k to kill them.

Jj

---

### Post by Double.J on 2014-04-24
Just found this guide
[URL="http://ubuntuforums.org/showthread.php?t=1449154"]
http://ubuntuforums.org/showthread.php?t=1449154[/URL]

which says you can enter single user with /sbin/telinit1

Hope it helps!

---

