---
title: "No Kernel after upgrades"
date: 2024-02-01
forum: Installation &amp; Upgrades
---

### Post by copperheadbill on 2024-02-01
This is my first post in the forums, so please don't hesitate to scold me if I post something stupid.

I have Ubuntu 22.04 running with root on zfs and after upgrading some packages (not sure what they were) I cannot get it to boot.  Initially when I selected the 6.5 kernel from the grub menu it would post a message: 
error: file '/BOOT/ubuntu_xxxxxx@/vmlinuz-6.5.0-15-generic' not found.
error: you need to load the kernel first.

When this first started it would load some options on the grub menu, but I have managed to screw it up worse, as now it simply skips straight to the grub prompt.  I tried following some of the steps in this post: 

[https://develmonk.com/2022/05/20/mount-ubuntu-22-04-zfs-partitions-using-live-iso-for-disaster-recovery/](https://develmonk.com/2022/05/20/mount-ubuntu-22-04-zfs-partitions-using-live-iso-for-disaster-recovery/)

I know it's an older kernel but it seemed most everything worked.  Anyway when I search my system from grub with ls I find a partition with /grub and /efi in it but no /boot or initramfs.  I can see all the data in my pools, and when I chroot into it everything seems good (apt updates etc).

Please let me know what you need to help diagnose this issue, or I guess I'll wipe and start over (not preferred solution).

(Edit) 
This might help from boot rescue disk: 

[https://pastebin.ubuntu.com/p/FjjRRpC7hF/](https://pastebin.ubuntu.com/p/FjjRRpC7hF/)

Please ignore sdi, I was trying to install bootloader on another drive and screwed that up too.  I was going to wipe it if I could get everything fixed.  Also this was the first time I booted in compatibility mode, I was just trying something different.

-Bill

---

### Post by foxsquirrel on 2024-02-01
You seem to have a serious mess that I am not sure has a good solution. The 6.5 kernel update has caused us plenty of problems, the only good solution at the present time is to back peddle to 20.04, sorry.

Might try pulling the drive and mount it in another machine and look for some some clues in the logs then maybe fix it that way, just a guess, at least worth a try. If you can salvage all the good stuff you might be better off to start over. I would not use the same drive, it might have an issue and it was just bad luck timing with the OS update. Use a new drive then a fresh install then see what you can save.

---

### Post by #&amp;thj^% on 2024-02-01
This seems to be a new but common problem on jammy 22.04
```
error: file '/BOOT/ubuntu_xxxxxx@/vmlinuz-6.5.0-15-generic' not found.
error: you need to load the kernel first.
```

I hope you have good back-ups.

By chance is this a AMD CPU machine?

---

### Post by copperheadbill on 2024-02-01
Xeon CPU.

I think I may have found the culprit, via
[https://savannah.gnu.org/bugs/index.php?64297](https://savannah.gnu.org/bugs/index.php?64297)

When I try to do grub-install it fails with error "error: compression algorithm inherit not supported"

I had set up zfs-auto-snapshot and this was the first reboot after installation.  

I am trying to figure out the best way to install zfsbootmenu to see if that can detect/boot into the OS.  The documentation on it are a little daunting, if anyone has experience with it I would love to get any tips/pointers you have.

Fortunately I was able to pull all vital data off with the live boot rescue usb drive and move it to offsite backup.  I really don't relish the idea of re configuring everything I had set up on there, but hey it's just time, right? lol...

---

### Post by #&amp;thj^% on 2024-02-01
Ah that's interesting.....I'm following that now.
I still take snapshots, but for me I keep a rEFInd usb and boot to through that when I'm doing testing. And seems to for the most part keep me out of trouble.
```
zfs list
NAME                                               USED  AVAIL  REFER  MOUNTPOINT
bpool                                              244M  1.51G    96K  /boot
bpool/BOOT                                         244M  1.51G    96K  none
bpool/BOOT/ubuntu_l7y21m                           244M  1.51G   244M  /boot
rpool                                             39.8G   852G   192K  /
rpool/ROOT                                        10.6G   852G   192K  none
rpool/ROOT/ubuntu_l7y21m                          10.6G   852G  6.74G  /
rpool/ROOT/ubuntu_l7y21m/srv                       192K   852G   192K  /srv
rpool/ROOT/ubuntu_l7y21m/usr                       688K   852G   192K  /usr
rpool/ROOT/ubuntu_l7y21m/usr/local                 496K   852G   496K  /usr/local
rpool/ROOT/ubuntu_l7y21m/var                      3.88G   852G   192K  /var
rpool/ROOT/ubuntu_l7y21m/var/games                 192K   852G   192K  /var/games
rpool/ROOT/ubuntu_l7y21m/var/lib                  3.85G   852G  3.68G  /var/lib
rpool/ROOT/ubuntu_l7y21m/var/lib/AccountsService   212K   852G   212K  /var/lib/AccountsService
rpool/ROOT/ubuntu_l7y21m/var/lib/NetworkManager    324K   852G   324K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_l7y21m/var/lib/apt              88.3M   852G  88.3M  /var/lib/apt
rpool/ROOT/ubuntu_l7y21m/var/lib/dpkg             91.7M   852G  91.7M  /var/lib/dpkg
rpool/ROOT/ubuntu_l7y21m/var/log                  25.6M   852G  25.6M  /var/log
rpool/ROOT/ubuntu_l7y21m/var/mail                  192K   852G   192K  /var/mail
rpool/ROOT/ubuntu_l7y21m/var/snap                  192K   852G   192K  /var/snap
rpool/ROOT/ubuntu_l7y21m/var/spool                 276K   852G   276K  /var/spool
rpool/ROOT/ubuntu_l7y21m/var/www                   192K   852G   192K  /var/www
rpool/USERDATA                                    28.6G   852G   192K  /
rpool/USERDATA/me_2u9hr7                          28.6G   852G  28.6G  /home/me
rpool/USERDATA/root_2u9hr7                        5.11M   852G  5.11M  /root
rpool/keystore                                     510M   852G  63.0M  -

```

I'm not sure I'm going to play with zfsbootmenu though.

If interested in rEFIind on a USB link is here: [https://sourceforge.net/projects/refind/files/0.12.0/refind-flashdrive-0.12.0.zip/download](https://sourceforge.net/projects/refind/files/0.12.0/refind-flashdrive-0.12.0.zip/download)

But I'm happy to hear you have recovered most of what you need.

---

### Post by copperheadbill on 2024-02-01
I just created an rEFInd flash drive.... I'm gonna stick it in and give it a go tomorrow. I'll update with results, maybe this post will help someone else this bug has potentially affected.

If this works I will be installing rEFInd to the hdd.  Do you still use grub when you are not booting from USB?

---

### Post by #&amp;thj^% on 2024-02-01
> **copperheadbill said:**
> 
If this works I will be installing rEFInd to the hdd.  Do you still use grub when you are not booting from USB?
No it is it's own bootloader.
Good luck and keep us posted.

I'm going to ask another member to join this thread I think he will find it useful and interesting. :)

---

### Post by MAFoElffen on 2024-02-01
Here is the info behind the Bug, the released fix that they put into Grub2 2.12... And a bug report Requesting that it gets backported for Jammy, with Grub2 2.06:
[https://bugs.launchpad.net/ubuntu/+source/grub2-unsigned/+bug/2051999](https://bugs.launchpad.net/ubuntu/+source/grub2-unsigned/+bug/2051999)

I need both of you to join that bug as affected, so that it gets confirmed... Let's make this working in the channels that should be native... and get launchpad to apply the fix... This is an LTS. They should fix it. The fix is already there, it just needs to be applied.

If you look at the OpenZFS link, there is a work-around by installing Grub2 version 2.12... Or we can see if LaunchPad jumps on this in a timely manner to get 2.06 patched.

---

### Post by #&amp;thj^% on 2024-02-01
I've added myself to it as well.

---

### Post by copperheadbill on 2024-02-02
I put myself in the bug report.  I tried rEFInd, but it didn't see the OS files, just the grub loader.  

I'm trying to install 2.12 now, but after compiling it has removed several files it is dependent on: x86_64-efi, pretty much all the efi files.  Not sure how to restore those, or if I can just copy from a working install.

---

### Post by MAFoElffen on 2024-02-02
Post the output of what it says, and I'll try to come up with something...

---

### Post by MAFoElffen on 2024-02-03
I'm stuck on this make error:
```

mawk: ./genmoddep.awk: line 110: function asorti never defined

```
asorti is an internal function of gawk, and gawk is installed(?)

And here is the call in /home/mafoelffen/Downloads/Grub2-2.12/grub-2.12/grub-core/genmoddep.awk
```

    }
    modlist = ""
    depcount[mod] = 0
    n = asorti(uniqmods, w)
    for (i = 1; i <= n; i++) {
      depmod = w[i]
      modlist = modlist " " depmod;
      inverse_dependencies[depmod] = inverse_dependencies[depmod] " " mod
      depcount[mod]++
      total_depcount++
    }

```

---

### Post by #&amp;thj^% on 2024-02-03
> **MAFoElffen said:**
> I'm stuck on this make error:
```

mawk: ./genmoddep.awk: line 110: function asorti never defined

```
asorti is an internal function of gawk, and gawk is installed(?)

And here is the call in /home/mafoelffen/Downloads/Grub2-2.12/grub-2.12/grub-core/genmoddep.awk
```

    }
    modlist = ""
    depcount[mod] = 0
    n = asorti(uniqmods, w)
    for (i = 1; i <= n; i++) {
      depmod = w[i]
      modlist = modlist " " depmod;
      inverse_dependencies[depmod] = inverse_dependencies[depmod] " " mod
      depcount[mod]++
      total_depcount++
    }

```

Yann wanted me to try this: [https://lore.kernel.org/all/20231224102548.4881C82617@busybox.osuosl.org/T/](https://lore.kernel.org/all/20231224102548.4881C82617@busybox.osuosl.org/T/)

Did i ever PM you on that I can't remember??  Overloaded and aging mind.....LOL

---

### Post by MAFoElffen on 2024-02-04
But that is where I'm stuck, exactly there. It should be fixed with that commit, but I still get that error.

I'll PM you on the other question. Maybe shouldn't be said in public.

---

### Post by copperheadbill on 2024-02-04
I've spent enough time trying to backpedal, and I've changed so many things that I've decided I need to just get this system back up and running.  I've wiped clean and reinstalled 22.04 on zfs.  I got all my data moved back and systems reinstalled so nothing was lost except time.  

I've got to say I'm a little perturbed by this whole situation.  I've been using Linux for many years and never had one go belly up that I couldn't fix without some research and elbow grease.  Maybe had I diagnosed the issue correctly in the first place I could have gotten it nipped, but hind sight is always 20/20. And I may have yet been able to recover had I invested more time.  

Thanks for the help guys, I'll keep an eye on that bug and I will not be snapshotting my bpool (lol)

Also I may try to get on these forums a little more often.  Maybe I can help some other folks with things I have seen in the past.  I'm no guru but I betcha I can help some folks get on facebook.

Should I go ahead and close this thread or leave it open for a few days.  Not sure on etiquette.

---

### Post by MAFoElffen on 2024-02-04
You said you "joined the bug"... I'm not sure that you did that at launchpad.net. After you said that, and before others joined in, I didn't see anyone except me and 1fallen. That was the one I am referring to.

What I would do to get around this bug, is to do backups of the bpool with tar, rsync or rdiff-backup. The need is still there.

I feverishly welcome anyone who wants to share experience with others. That is how this works. This is a good community of members who help each other. Especially those who have ZFS experiences. ZFS has a learning curve. Here there are me and 1 fallen... Then one or two others that are starting to help others on ZFS with their new experience. 

ZFS is has been good to me. A few things, but I'm used to that.

If you are going to watch this thread, I would like this to remain open, until we get some resolution to this problem, then close it when it does get resolved. Please? If not too much trouble or work for you. I think that is the best option. I think that would help many others to see what is happening with this, and where it goes.

---

### Post by #&amp;thj^% on 2024-02-04
I seen him in there (the bug report) that day. I'll check again though. Yes he's there post#6

---

### Post by copperheadbill on 2024-02-04
I’ll gladly leave it open. I would like to see what happens also. I will double check launchpad when I’m on a proper pc to make sure I am listed as affected.

---

### Post by #&amp;thj^% on 2024-02-04
EDIT: New Disclaimer, My post below is most certainly for 24.04 NN (Noble) and possibly Mantic 23.10 [B][U](NOTE Possibly use only if you know what your doing)
[/U][/B]

*We have been warned that this could or will break things on Jammy 22.04*

The grub issue with a PPA solved it for NNoble
```
apt policy grub-common
grub-common:
  Installed: 2.12-1ubuntu1~ppa1
  Candidate: 2.12-1ubuntu1~ppa1
  Version table:
 *** 2.12-1ubuntu1~ppa1 500
        500 https://ppa.launchpadcontent.net/ubuntu-uefi-team/build/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status
     2.12~rc1-12ubuntu4 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages

```

---

### Post by MAFoElffen on 2024-02-05
Wait until you see this (LOL):
```

mafoelffen@jammy-zfs-grub:~$ uname -r
6.5.0-15-generic
mafoelffen@jammy-zfs-grub:~$ lsb_release -d
Description:    Ubuntu 22.04.3 LTS
mafoelffen@jammy-zfs-grub:~$ apt policy grub-common
grub-common:
  Installed: 2.12~rc1-12ubuntu4
  Candidate: 2.12-1ubuntu1~ppa1
  Version table:
     2.12-1ubuntu1~ppa1 500
        500 https://ppa.launchpadcontent.net/ubuntu-uefi-team/build/ubuntu noble/main amd64 Packages
 *** 2.12~rc1-12ubuntu4 100
        100 /var/lib/dpkg/status

```
This work-around it just that... A workaround until we can get the fixes into the upgrades, and into a new 22.04 installer...

Disclaimer--> This work-around uses advance techniques. Do not try to use the same methods used here, on something else unless you know what you are doing.

I posted this in this comment in the Bug Report: [https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/2051999/comments/23](https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/2051999/comments/23)

This was repaired booted from an Ubuntu 22.04.3 LTS Desktop Installer LiveUSB > Try > Terminal session.
```

# The command log for the work-around for a broken jammy install:
sudo su -
zpool export -a
zpool import -N -R /mnt rpool
zpool import -N -R /mnt bpool
UUID=$(zfs list | awk '/^bpool\/BOOT\/ubuntu_/ {print $1}' | sed 's/bpool\/BOOT\/ubuntu_//g')
zfs import rpool/ROOT/ubuntu_$UUID
zfs import bpool/BOOT/ubuntu_$UUID
zfs mount -a
mount --make-private --rbind /dev /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys /mnt/sys
mount --make-private --rbind /run /mnt/run
chroot /mnt /bin/bash --login
mount -a

# Make backup of the original Jammy sources.list
cp /etc/apt/sources.list /etc/apt/sources.list.jammy

# Create a new Noble sources.list
sudo nano /etc/sources.list.noble

# Fill with these contents:
deb http://us.archive.ubuntu.com/ubuntu/ noble main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ noble-updates main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ noble-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu noble-security main restricted universe multiverse
# Save and exit
cp /etc/apt/sources.list.noble /etc/sources.list
apt update

# Add the Grub2 2.12 ppa
add-apt-repository ppa:ubuntu-uefi-team/build

# Modify the sources.list line of the PPA to work with Jammy
nano /etc/apt/sources.list.d/ubuntu-uefi-team-ubuntu-build-jammy.list

# Change the active line to:
deb [trusted=yes] https://ppa.launchpadcontent.net/ubuntu-uefi-team/build/ubuntu/ noble main
# Save and exit nano
apt update

# Install the Grub2 packages
apt install grub-efi-amd64 grub-efi-amd64-signed
# This will pull in some needed depends of Grub2 2.12~rc1 from the Nolble Repo's

# Reinstall/configure grub
grub-install --target=x86_64-efi --efi-directory=/boot/efi \
--bootloader-id=ubuntu --recheck --no-floppy

# Update the intramfs images
update-intramfs -c -k all

# Change the repo sources back to Jammy
cp /etc/apt/sources.list.jammy /etc/apt/sources.list
apt update

# Test: (Skip if snapshots already exist...)
zfs snapshot bpool/BOOT/ubuntu_2nlhsy@20230204a
zfs snapshot bpool/BOOT/ubuntu_2nlhsy@20230204b
zfs snapshot bpool/BOOT/ubuntu_2nlhsy@20230204c

zfs list -t snapshot

# Output:
#NAME USED AVAIL REFER MOUNTPOINT
#bpool/BOOT/ubuntu_2nlhsy@20230204a 0B - 298M -
#bpool/BOOT/ubuntu_2nlhsy@20230204b 0B - 298M -
#bpool/BOOT/ubuntu_2nlhsy@20230204c 0B - 298M -

# Exit Gracefully:
exit
mount | grep -v zfs | tac | awk '/\/mnt/ {print $3}' | \
xargs -i{} umount -lf {}
zpool export -a

reboot

```

---

### Post by #&amp;thj^% on 2024-02-05
Nicely done Sir!
That should be pretty straight forward for users on 22.04 Jammy. (Including the Warning)

BTW @ copperheadbill, I have no input for "zfs-auto-snapshot" I've never used it, so I have no Idea if that will work in the Grub "2.12-1ubuntu1~ppa1"
As shaky as this has been for ZFS user's I'm not one to play with it ATM. :)

---

### Post by MAFoElffen on 2024-02-05
@1fallen --- Check your PM, then the bug report.

Mate warned against that work-around. Is cautious. Then asked where to go from here.

I mapped out 2 options and 3 working work-arounds that I have come up with for this...

---

### Post by #&amp;thj^% on 2024-02-05
Yep I got them....I'm going to amend Post #19 to reflect that.

---

### Post by MAFoElffen on 2024-02-05
launchpad.net is down right now...
```

(10:31:28 AM) The topic for #launchpad is: We are experiencing issues due to an outage. We are looking into it, and will notify the channel once everything is in the clear. || Help contact: ialmeida (08:00-16:00 UTC, Mon-Fri) | Launchpad is an open source project: https://dev.launchpad.net/ | This channel is logged: http://irclogs.ubuntu.com/ | User Guide https://help.launchpad.net/ | Support and spam reporting: https://answers.l
(10:31:28 AM) Topic for #launchpad set by nesda at 07:27:20 AM on 02/05/2024
328: https://launchpad.net/

```

---

### Post by #&amp;thj^% on 2024-02-05
I just got notified:
> Uh oh!
Something has gone wrong. We're sorry!

If we are in the middle of an update, Launchpad will be back in a couple of minutes. Otherwise, we are working to fix the unexpected problems. Check @launchpadstatus on Twitter or @launchpadstatus@ubuntu.social on Mastodon for updates.

If the problem persists, let us know in the #launchpad IRC channel on libera.chat.

Technically, the load balancer took too long to connect to an application server.

Reload this page or try again in a few minutes

EDIT: Now resolved. :)

---

### Post by copperheadbill on 2024-02-06
Well if that works it's quite brilliant.  I've never thought about switching repos like that.

---

