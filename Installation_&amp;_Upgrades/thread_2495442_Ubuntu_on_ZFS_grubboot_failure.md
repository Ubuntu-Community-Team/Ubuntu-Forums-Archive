---
title: "Ubuntu on ZFS grub/boot failure"
date: 2024-02-19
forum: Installation &amp; Upgrades
---

### Post by dragonomnus on 2024-02-19
Hi all. I installed Ubuntu 22.04 on ZFS May of last year, primarily to begin learning Linux so I can migrate from Windows, especially for servers.
It mostly functioned well until last week.
2 issues I want to solve:
1- Fixing the boot failure
2- Migrating to a new drive

Regarding #2, I originally installed Ubuntu on an old Samsung 840 SSD but upgraded the drive in my main PC so wanted to migrate Ubuntu to the now unused NVMe, both to give me more to play with and to learn how to migrate Ubuntu on ZFS to a new drive. I read plenty and attempted multiple methods but all failed. I thought I saw a possible solution but that was more than 6 months ago and I became busy with more important issues so never returned to deal with the issue and now forget. Some things I tried:

 - Using gparted to copy non-zfs partitions, then "zfs attach" to mirror bpool & rpool to the new drive followed by "zfs split" to break the mirror with pools intact on both drives, followed by removing the old drive & renaming the pool to the original name (split requires giving a different name). This is a summary of steps, not complete list, but it failed and I forget exactly why.
 - Fresh installing Ubuntu on ZFS to the NVMe, then booting the LiveUSB to delete the rpool on the NVMe and use zfs send/receive to send the original rpool. IIRC, this failed because grub was looking for rpool/ROOT/ubuntu_YYYY but this method transferred the original /ubuntu_XXXX, and I failed to find a method of fixing that.
 - It is possible the ubuntu_X/Y issue was from the 1st method, I forget now.

As said above, I set that issue aside, but this new boot failure seems a good time to try to solve that.

Regarding #1, the system functioned mostly well since May until last week. Important details:
 - I installed zfsautosnapshot. This caused bpool to fill with old snapshot data until it lacked sufficient free space for a kernel update.
 - I finally had some time to learn to deal with that issue so solved that last week by deleting the old snapshots, then updating the kernel (apt update, apt upgrade, apt autoremove). This updated from 6.2* to 6.5*
 - The kernel did its boot/grub update to install the new vmlinuz & initrd where grub could use them, but it found dozens of references to the old 6.2 kernel, I think in the snapshots, not certain. Perhaps this caused part/all of the issue?
 - The present symptom is Ubuntu fails to boot so I get grub saying it cannot find hd1,part3.
 - Doing ls in grub on any hd# or hd#,part# returns "Compression algorithm inherit not supported".
 - Booting to UbuntuLiveUSB, I used "zpool import -R /zfs -a" to verify all the zfs pools & datasets seem to be intact, with the possible exception of bpool.
 - The bpool issue is it shows mounted to /zfs/boot but ls shows /zfs/boot empty, and when I tried to follow instructions from [https://askubuntu.com/questions/826209/re-initialise-grub-for-non-bootable-uefi-zfs-16-04-installation](https://askubuntu.com/questions/826209/re-initialise-grub-for-non-bootable-uefi-zfs-16-04-installation) section 4.3 returned "unknown filesystem type 'zfs_member'.
 - The UbuntuLiveUSB definitely has ZFS capability because I can use zpool & zfs commands and it imported & mounted the zpools & datasets.

I want to learn how to properly solve both these issues, and the present boot failure seems a good time to also learn to migrate drives. I am relatively new to Linux, so I apologize if I failed to provide information you think would help. Please instruct me how to get any extra info you think could help.

---

### Post by MAFoElffen on 2024-02-19
Let's fix #1 first.

The problem booting appeared "after" doing a snapshot (or snapshots) of bpool... (BUG) I have an open bug report with 4 work-arounds for that.
RE: [https://bugs.launchpad.net/ubuntu/+source/grub2-unsigned/+bug/2051999](https://bugs.launchpad.net/ubuntu/+source/grub2-unsigned/+bug/2051999)

Recommend newest/updated work-around: [https://bugs.launchpad.net/ubuntu/+source/grub2-unsigned/+bug/2051999/comments/33](https://bugs.launchpad.net/ubuntu/+source/grub2-unsigned/+bug/2051999/comments/33)

Here, just for FYI... Keep this link handy for the future. Those are tutorials I came up with to chroot into installed ZFS Systems, depending on how they were installed and with differing options:, when things go South, and you have to rescue an install ZFS system when it won't boot:
[https://github.com/Mafoelffen1/OpenZFS-Ubuntu-Admin](https://github.com/Mafoelffen1/OpenZFS-Ubuntu-Admin)

Tell me how that goes...

---

### Post by dragonomnus on 2024-02-20
Thanks for those links. Yet to read all of the OpenZFS-Ubuntu-Admin  stuff but running a non-encrypted root presently so skimmed that.
Read  the launchpad thread you linked, mostly followed as much of your  updated work-around as I could. Before relaying the error, your comment  23 & 33 have differences which could be important.

After your  UUID= line, you list 2 lines beginning "zfs import" for the rpool &  bpool datasets. I think those should be "zfs mount", as import is a  pool function while mount is for the datasets in those steps, correct?
Comment  23 includes instructions to copy the original sources.list file as a  backup, then replace the contents with (I think) only the new sources to  force updates from those instead of default repositories, then pulling  the updates, then restoring the original sources.list.
Comment 33  (the updated workaround) instructs to add the new repository then  perform the upgrade then restore the sources.list, but omits copying the  original as a backup then clearing the active sources.list to force  updating from the source necessary.
After I did the chroot step, I  copied the sources.list before adding the new repository, then found it  did little (basically found no updates to grub) until I cleared the  active sources.list and again added the new repository.
If you re-add  those steps, be careful if you copy/paste from comment 23 to 33 because  23 I think has an error on the line to create a new Noble sources.list,  being /apt was omitted from the directory path, specifying  /etc/sources.list, but seemed to not account for that elsewhere so that  could cause problems for people following exactly who fail to notice the  issue.

It failed for me trying to pull the grub update from the new repo.
Using  your exact command I get "grub-efi-amd64-signed is already the newest  version (1.187.6+2.06-2ubuntu14.4)", followed (skipping some lines) by  "The following packages have unmet dependencies: grub-efi-amd64-signed :  Depends: grub-efi-amd64-bin (= 2.06-2ubuntu14.4) but  2.12-1ubuntu1-ppa1~22.04 is to be installed" then "E: Unable to correct  problems, you have held broken packages."

I then tried to alter the command to "apt install grub-efi-amd64-bin" but it also failed, with a similar but different error:
"shim-signed  : Depends: grub-efi-amd64-signed (>= 1.187.2~) but it is not going  to be installed or grub-efi-arm64-signed (>= 1.187.2~) but it is not  installable"
"E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages."

The arm64 part is irrelevant here.
Any idea how to solve this issue?
I  am also curious why it succeeded for you but is failing for me. What  else is different? Different version of Ubuntu? Did I install an older  Ubuntu than you did? Package updates between then & now? Any info  you think could help?

Also, while this boot failure did  technically begin after snapshots were created on bpool, I installed  zfs-auto-snapshots back in... June I think, so it ran for 8-ish months  with no boot problems. I rebooted it a few times, but thankfully nowhere  near as often as Windows needs... So this issue all began after I  cleared the old snapshots to free the space for the kernel upgrade.
Further,  that launchpad thread indicates auto-snapshots did not cause this  problem, only manual snapshots did, and I created no manual snapshots  since installing zfs-auto-snapshots. Not saying it is not all related,  but I think it important to note that difference.

---

### Post by MAFoElffen on 2024-02-21
Dang sorry. My quick tests on that yesterday morning (while trying to help you on my way to work) were not complete enough.

Try the workaround from Comment #33 again. I made edits to both 33  and updated it based on what it did to you. #33 now uses that same PPA, but uses the Noble sources.list, to pull in the needed depends where it needs to.

I know that #23 works and had tested it a few time on fresh installs of 22.04. The one in #33, I quickly tested on Mantic & noble, which seemingly must not have the same depends as Jammy. Thank you for helping me test that. I made the source.list change to pull in the needed depends from the Noble repo's.

That should work for you now. Thank you for testing this for on Jammy, and sorry for the previous. I can't test this myself "this morning" as, I have an early morning then have to pick up my wife from the airport. Hoping that goes well for you, and as expected.

Please tell me how that goes.

---

### Post by dragonomnus on 2024-02-21
Result:
Was able to progress to the grub-install but it failed with "Compression algorithm inherit not supported".
I checked both the pool & dataset of bpool, encryption is disabled but lz4 compression is enabled. Could this be an issue?
If it is, why now but not before?
Suspecting it must be related to the new bug but why did the solution fail for me if my issue is being caused by the bug?
I wonder if there is another fact at play here layering a 2nd issue on the bug...

That said, I think a flaw remains in the updated instructions.
The line I mentioned before where you instruct to create the new Noble sources.list again lacks /apt from the path, as does part of the line where you say to copy the new Noble version to the default sources.list.
The lines presently read:
"sudo nano /etc/sources.list.noble" (is sudo needed here when we are already in sudo & chroot?) which I think should be
"nano /etc/apt/sources.list.noble"
and
"cp /etc/apt/sources.list.noble /etc/sources.list" which I think should be
"cp /etc/apt/sources.list.noble /etc/apt/sources.list"
As said before I am new to Linux, so I am not certain of those.
Another possible issue is the revised instructions in comment 23 with the line to add the backport repository.
In comment 23 the line reads
"add-apt-repository ppa:ubuntu-uefi-team/build"
but in 33 it reads
"add-apt-repository ppa:ubuntu-uefi-team/backports-build"

Thinking on it, I am wondering if changing that could fix the error I got. I shall try that & update here later.

Edit: Tested adding the backports-build repository then running the update again but now it is not updating grub because it is already up-to-date.
I removed the references to the non-backport build repository in /etc/apt/sources.list.d/ but am wondering if there was a better/proper method. (never removed a repository, shall search a proper method)
No change though, not pulling updates to grub now so I am wondering if we can/should try removing grub to force it to reinstall fresh from the backports-build repository?
If so, what exact command should I use to do that?

---

### Post by MAFoElffen on 2024-02-22
That would be what to do, or to use Software & Updates to uncheck it, which in effect just adds a "#" character to comment out the lines.

So it is still getting that error. Look at the option for creating a new bpool in this: [https://bugs.launchpad.net/ubuntu/+source/grub2-unsigned/+bug/2051999/comments/26](https://bugs.launchpad.net/ubuntu/+source/grub2-unsigned/+bug/2051999/comments/26)

The next work-around to try would be to move forward with plan for #2... How much room do you have in bpool and rpool. Enough for a full recursive snapshot of bpool/BOOT, rpool/ROOT & rpool/USERDATA?

---

### Post by dragonomnus on 2024-02-22
We can work on #2 now if needed, and there is plenty of space for full snapshots of bpool & rpool.
Ironically that is part of the problem, because I was not intending to remove all snapshots from bpool before performing the kernel upgrade but the command explanation was unclear in 1 part so I saw 2 possibilities for it, being where to place the % in the command to remove all older or all newer snapshots. Placing it after the snapshot name removed all newer which was not what I wanted but a minor problem, however I goofed when I redid the command to remove all older snapshots (which were the snapshots consuming all the space I needed to free). I intended to leave the newest snapshot but accidentally used it as the starting point so removed all remaining snapshots. If I did not goof that, I would have a bpool snapshot to restore & probably fix this issue. If I thought about it and took a new snapshot before installing the kernel upgrade, I would be able to restore. Learned my lessons on those.

However, I think we can/should try 1 more thing before calling this a fail, which is my last comment in my prior message. Can we force-remove the grub package somehow to allow it to update from the backports-build repository? The present issue is from the differences which were in comment 23 instructions vs comment 33, being comment 23 said to use "ppa:ubuntu-uefi-team/build" instead of "ppa:ubuntu-uefi-team/backports-build", which properly pulled an update, but now it is finding no update available from backports-build because it already updated from non-backports build. I tried to remove grub but a standard "apt remove grub-efi-amd64 grub-efi-amd64-signed" failed to remove grub, so how can we force it to then allow a new pull from the backports-build repository?

---

### Post by dragonomnus on 2024-02-22
I think above applies, but I realized I failed to provide some possibly  helpful information. I rolled bpool & rpool back to the last  snapshot on each which corrected some of the errors and allowed me to  grub-install & update-initramfs, but no change in failure to boot. I think  no change is because it failed to update grub after the rollback despite  repeating the steps to alter sources.list & add the backports-build  repository again.

I was able to roll both datasets back because I have snapshots of rpool back to when I installed zfs-auto-snapshots and bpool after the kernel upgrade, which leads to another possibly important piece of info I forgot to mention. Ubuntu could not upgrade the kernel because bpool lacked free space because the snapshots were consuming it (which I need to solve also), which is why I deleted the old snapshots which allowed the kernel to upgrade. Ubuntu wanted me to reboot after the upgrade, which I did and it rebooted normally. It was a couple days later when I began noticing issues (for example I tried to access a network share but could not) and found no obvious cause for the issues so rebooted again, which is when it failed to boot. This also means I have some snapshots on bpool *after* the kernel upgrade, if those could help.

That said, I think there is an error in the updated instructions, but not certain.
I  think the line "add-apt-repository  ppa:ubuntu-uefi-team/backports-build" is correct, but if it is then I  think the line "nano  /etc/apt/sources.list.d/ubuntu-uefi-team-ubuntu-build-jammy.list" is incorrect. Notice the 2nd command lacks the backport reference? I think it should be:
nano /etc/apt/sources.list.d/ubuntu-uefi-team-ubuntu-backports-build-jammy.list

And same thing for what to edit in that file, lacking the backport reference, so I think it should be:
deb [trusted=yes] [https://ppa.launchpadcontent.net/ubuntu-uefi-team/backports-build/ubuntu/]("https://ppa.launchpadcontent.net/ubuntu-uefi-team/build/ubuntu/") noble main

Also, I think there is an issue in the later command to update initramfs. I am not certain but
"update-intramfs" should be
"update-initramfs", correct?

I was able to pull an update to grub during 1 of the prior attempts, but I think it was the attempt following the prior instructions which said "build" instead of "backports-build" so the update failed to solve the issue. So now the question is: if I rolled rpool & bpool back to before all these changes (and verified the sources.list etc files were removed/restore), then why is it not pulling a new update to grub from backports-build if I follow the updated instructions? There must be some detail which caused a change in behavior, but the only thing I can say it is doing now is possibly a failure when I try "apt update".
It returns Hit or Ign (Ignored?) on each line and is Ign on all the lines from the backports-build repository (except an error on the line for i386 but that should not be relevant), so perhaps that is why it is not pulling an update from them now?
How can we solve that directly, or to force-update or force-remove to allow an update to grub?

Edit: Intended to say but forgot by the time I was done typing all that...
No worries on the solution failing or your limited ability to test, you have a life. :)
I appreciate your help with this issue and am happy if it helps the Linux community solve an issue.
But I also began thinking after my last post.... I have snapshots of rpool from before the update so I *could* roll it back then try updating grub & stuff.
However, I think that would not be the best idea because I think it is better to find a working solution then push it to the updates channel before this hits too many users.
On that note....
What if we do both? I was thinking perhaps I should image this system so we have it in a non-booting state to play with more if we need, but I can restore bpool & rpool on the drive to the last snapshot before the reboot where it failed so would we need images of the non-booting state or could we fix it then roll the snapshots to break it again?
If that would succeed (if not I can image it, if you help me with that) & help solve this issue further, then perhaps we should image the drive then begin working on #2 of migrating to a new drive.
If we begin working on #2, my preference would be to learn how to migrate an installation (including all users/configs/software/etc). I think using ZFS to mirror & split bpool & rpool should be the best way, but I think that was 1 of the methods I tried before which failed. I remember 1 of the methods I tried failed because of the UUID part of the dataset name, but I failed to solve that issue and cannot remember if that was when I mirrored & split or what.

---

### Post by #&amp;thj^% on 2024-02-22
I'm on Noble currently, but on Jammy I had to hand remove grub:
```
apt list grub* --installed
Listing... Done
grub-common/noble,now 2.12-1ubuntu2 amd64 [installed,automatic]
grub-efi-amd64-bin/noble,noble,now 2.12-1ubuntu1 amd64 [installed]
grub-efi-amd64-signed/noble,now 1.201+2.12-1ubuntu1 amd64 [installed]
grub-gfxpayload-lists/noble,now 0.7build1 amd64 [installed]
grub-pc-bin/noble,now 2.12-1ubuntu2 amd64 [installed]
grub-pc/noble,noble,now 2.12-1ubuntu2 amd64 [installed]
grub2-common/noble,now 2.12-1ubuntu2 amd64 [installed]

```
then update again..."sudo apt update" then install/reinstall all the above. After that it has been pretty solid.

What information do you need from me?
```
apt policy grub-efi-amd64-signed
grub-efi-amd64-signed:
  Installed: 1.201+2.12-1ubuntu1
  Candidate: 1.201+2.12-1ubuntu1
  Version table:
 *** 1.201+2.12-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status
     1.201+2.12-1ubuntu1 500
        500 https://ppa.launchpadcontent.net/ubuntu-uefi-team/build/ubuntu noble/main amd64 Packages

```
Repo nanming:
```
inxi -r | grep ubuntu-uefi-team
  Active apt repos in: /etc/apt/sources.list.d/ubuntu-uefi-team-ubuntu-build-noble.sources
    1: deb https://ppa.launchpadcontent.net/ubuntu-uefi-team/build/ubuntu/ noble main

```

It's pretty easy to forget about the room snapshots will gobble up  (best to check at least weekly)
```
sudo zfs list -o space | sort -k4 --human-numeric-sort
[sudo] password for me: 
bpool                                             1.50G   256M        0B     96K             0B       256M
bpool/BOOT                                        1.50G   255M        0B     96K             0B       255M
bpool/BOOT/ubuntu_2wtpxc                          1.50G   255M        0B    255M             0B         0B
NAME                                              AVAIL   USED  USEDSNAP  USEDDS  USEDREFRESERV  USEDCHILD
rpool                                              417G  29.0G        0B     96K             0B      29.0G
rpool/ROOT                                         417G  16.2G        0B     96K             0B      16.2G
rpool/ROOT/ubuntu_2wtpxc/srv                       417G    96K        0B     96K             0B         0B
rpool/ROOT/ubuntu_2wtpxc/usr                       417G   240K        0B     96K             0B       144K
rpool/ROOT/ubuntu_2wtpxc/usr/local                 417G   144K        0B    144K             0B         0B
rpool/ROOT/ubuntu_2wtpxc/var                       417G  4.86G        0B     96K             0B      4.86G
rpool/ROOT/ubuntu_2wtpxc/var/games                 417G    96K        0B     96K             0B         0B
rpool/ROOT/ubuntu_2wtpxc/var/lib                   417G  4.81G        0B   4.65G             0B       158M
rpool/ROOT/ubuntu_2wtpxc/var/lib/AccountsService   417G   100K        0B    100K             0B         0B
rpool/ROOT/ubuntu_2wtpxc/var/lib/apt               417G  94.4M        0B   94.4M             0B         0B
rpool/ROOT/ubuntu_2wtpxc/var/lib/dpkg              417G  63.3M        0B   63.3M             0B         0B
rpool/ROOT/ubuntu_2wtpxc/var/lib/NetworkManager    417G   160K        0B    160K             0B         0B
rpool/ROOT/ubuntu_2wtpxc/var/log                   417G  54.2M        0B   54.2M             0B         0B
rpool/ROOT/ubuntu_2wtpxc/var/mail                  417G    96K        0B     96K             0B         0B
rpool/ROOT/ubuntu_2wtpxc/var/snap                  417G   472K        0B    472K             0B         0B
rpool/ROOT/ubuntu_2wtpxc/var/spool                 417G   112K        0B    112K             0B         0B
rpool/ROOT/ubuntu_2wtpxc/var/www                   417G    96K        0B     96K             0B         0B
rpool/USERDATA                                     417G  12.7G        0B     96K             0B      12.7G
rpool/USERDATA/me_0wdehs                           417G  12.7G        0B   12.7G             0B         0B
rpool/USERDATA/root_0wdehs                         417G  2.02M        0B   2.02M             0B         0B
rpool/ROOT/ubuntu_2wtpxc                           417G  16.2G     4.99G   6.39G             0B      4.86G

```

---

### Post by dragonomnus on 2024-02-24
> **1fallen said:**
> I'm on Noble currently, but on Jammy I had to hand remove grub

How?
I did the "apt list" you did and saw my grub-efi-amd64* packages were pulled from noble but grub-pc/grub-common/grub2-common were all from jammy so I pulled those updates (and their dependencies) from noble then did another grub-install & update-initramfs.
They both succeeded with no error but no change on reboot, being it again failed.

I am wondering more if my issue is from the grub bug or some other cause, but I already gave all information I know and know how to get.
I would again attempt to migrate to the new SSD as MAfoElffen suggested last, but the methods I read and tried all failed and I would guess every method I know or can think of except hand-picking which directories & files to copy would result in transferring the boot problem also. And I know not which directories to hand-pick to effect a full migration of users/configs/software while not transferring the boot problem.

I could do a fresh install on the new drive, but I need to learn a functional method of system migration (and backup/restoration of Linux/software on ZFS). I suspect the chroot & grub-install I learned thanks to MAfoElffen would help so I can probably try again, but every method I know would copy all of rpool (& bpool) so would almost certainly copy the problem with it.

---

### Post by MAFoElffen on 2024-02-26
I'm back. Busy week at work. Worked until late last nigh. The had to work on my truck, to get is ready for work for this week.

I was thinking about htis in the back of my head while I was working...

First do snapshots. recursively using the "-r" flag. The datasets yu want to make sanpshots of are bpool/boot, rpool/ROOT, and rpool/USERDATA. Then send/receive, replicating the whole datasets using the "-R" flag... To an external disk. That way you can snapshot and restore without carrying any of set pool options that are causing this problem.

I mount my backup disk as a pool called "backups", mounted at a directory called /backups...
```

sudo su --
zfs snapshot -r bpool/BOOT@migrate
zfs snapshot -r rpool/ROOT@migrate
zfs snapshot -r rpool/USERDATA@migrate
zfs send -R bpool/BOOT@migrate > /backups/bpool-boot.migrate
zfs send -R rpool/ROOT@migrate > /backups/rpool-root.migrate
zfs send -R rpool/USERDATA@migrate > backups/rpool-userdata.migrate

```

This will be the easiest way to migrate to a newer larger disk, and not carry over the problem...

First do this to find the name of the disk:
```

ls -e7 -o name,size,model

```
For example sake, lets just say it turned up as "sdb". We then use that value to find the unique disk ID
```

ls -l /dev/disk/by-id | grep -e 'sdb'

```
Lets say it came back like this
```

lrwxrwxrwx 1 root root  9 Feb 18 10:26 ata-Samsung_SSD_870_QVO_2TB_S6R4NJ0R624350W -> ../../sdb

```
We then use that value, to create a reusable variable, so we don't have to retype it each time we need to use it
```

DISK=/dev/disk/by-id/ata-Samsung_SSD_870_QVO_2TB_S6R4NJ0R624350W

```
Then we create new partitions on that disk. This is what the canned Ubuntu install does by rule of thumb:
```

NAME    LABEL                     SIZE     FSTYPE    MOUNTPOINT
sda                               <whatever size>         
 +-sda1                           512M     vfat      /boot/efi
 +-sda2                             2G     swap      [SWAP]
 +-sda3 bpool                       2G     zfs_mem 
 +-sda4 rpool                    <balance> zfs_mem

```
I use different sizes for things to correct size issues for what I do:
```

I set EFI at between 750M to 1G, depending if I am going to add any EFI apps.
I set swap at 1.5 to 2 times the RAM
I set bpool at 3G to allow room for snaphots
I give what balance to rpool, or whatever I decide as appropriate (I usually reserve 10%-20% as reserve for emergencies).

```
That would translate to someting like this, adjusting for your planned needs:
```

sudo su --
## Add partitions
# For ESP EFI
sgdisk     -n1:1M:1G      -c1:EFI    -t1:EF00 $DISK

# For Linux Swap
sgdisk     -n2:0:+32G   -c2:swap   -t2:BF02 $DISK

# For bpool boot
sgdisk     -n3:0:+3G     -c3:bpool  -t3:BE00 $DISK

# For rpool root
sgdisk     -n4:0:0   -c4:rpool  -t4:BF00 $DISK

``` 
Then we are going to do a few things...

copy over the EFI for old to new:
```

sudo dd if=/dev/sda1 of=/dev/sdb11

```
The easiest way to migrate rpool, is to attach ${DISK}-part4 to rpool, (will create it as a mirror of the old). After it finishes resilvering, then "detach" the old partion  then remove the old partition, then set "autexpand=on"...

There is actually 3 wyas to do that, with either add/remove, replace or attach/detach. I find with people, that attach/detach has a better success rate, and you can verify it before the old is removed...

The commands are going to look something like this
```

zfs attach ${DISK}-part4 rpool
zpool status -v rpool 

```
Until it is done resilvering, then it will look similar to this
```

  pool: rpool
 state: ONLINE
config:

    NAME                                           STATE     READ WRITE CKSUM
    rpool                                          ONLINE       0     0     0
      mirror-0                                     ONLINE       0     0     0
      5d133589-303b-1940-80fc-568124015599         ONLINE       0     0     0
      ata-Samsung_SSD_870_QVO_2TB_S6R4NJ0R624350W  ONLINE       0     0     0 

errors: No known data errors

```
So then you are going to detach the old pool
```

zfs detach 5d133589-303b-1940-80fc-568124015599 rpool

```
For bpool, it going to be a bit different... First, we capture the UUID variable thta was used during its origianl install...
```

UUID=$(zfs list | awk -F "_" '/bpool\/BOOT\/ubuntu_/ {print $2}' | awk '{print $1}')

```
Then rename the old bpool, so it doesnt conflist wiht the new one, so we still have access to both
```

umount /boot/efi
zpool rename bpool bpool-bak
zpool set mouuntpoint=/mnt bpool-bak

```
Then create the new bpool, with the new options:
```

zpool create \
    -o ashift=12 \
    -o autotrim=on \
    -o cachefile=/etc/zfs/zpool.cache \
    -o feature@async_destroy=enabled \
    -o feature@empty_bpobj=active \
    -o feature@lz4_compress=active \
    -o feature@multi_vdev_crash_dump=disabled \
    -o feature@spacemap_histogram=active \
    -o feature@enabled_txg=active \
    -o feature@hole_birth=active \
    -o feature@extensible_dataset=disabled \
    -o feature@embedded_data=active \
    -o feature@bookmarks=disabled \
    -o feature@filesystem_limits=disabled \
    -o feature@large_blocks=disabled \
    -o feature@large_dnode=disabled \
    -o feature@sha512=disabled \
    -o feature@skein=disabled \
    -o feature@edonr=disabled \
    -o feature@userobj_accounting=disabled \
    -o feature@encryption=disabled \
    -o feature@project_quota=disabled \
    -o feature@device_removal=disabled \
    -o feature@obsolete_counts=disabled \
    -o feature@zpool_checkpoint=disabled \
    -o feature@spacemap_v2=disabled \
    -o feature@allocation_classes=disabled \
    -o feature@resilver_defer=disabled \
    -o feature@bookmark_v2=disabled \
    -o feature@redaction_bookmarks=disabled \
    -o feature@redacted_datasets=disabled \
    -o feature@bookmark_written=disabled \
    -o feature@log_spacemap=disabled \
    -o feature@livelist=disabled \
    -o feature@device_rebuild=disabled \
    -o feature@zstd_compress=disabled \
    -o feature@draid=disabled \
    -o feature@zilsaxattr=disabled \
    -o feature@head_errlog=disabled \
    -o feature@blake3=disabled \
    -o feature@block_cloning=disabled \
    -o feature@vdev_zaps_v2=disabled \
    -o compatibility=grub2,ubuntu-22.04 \
    -O devices=off \
    -O acltype=posixacl \
    -O xattr=sa \
    -O compression=lz4 \
    -O normalization=formD \
    -O relatime=on \
    -O canmount=off -O mountpoint=/boot -R /mnt \
    bpool ${DISK}-part3
    
zfs create -o canmount=off -o mountpoint=none bpool/BOOT
zfs create -o mountpoint=/boot bpool/BOOT/ubuntu_$UUID

ls /mnt  # To verify it is there...

```
Then copy (rsync) over the filesystem from old-to-new, or restore via send/recieve from the dataset snapshot backup from your recovery pool.

rsync would look like this
```

rsync -r /boot/ /mnt/boot

```
send/receive would look like this... Note that the dataset cannot exist before it is restored from full...)
```

zfs destroy bpool/BOOT/ubuntu_$UUID
zfs destroy bpool/BOOT
zfs receive -F -d bpool/BOOT < /backups/bpool-boot.migrate

```

---

### Post by MAFoElffen on 2024-02-26
PART 2 -

That way, the old bpool and rpool still exist... The new ones are populated...

Then you would intialize/format the swap partition, then update the /mnt/etc/fstab file to point it to the new EFI partition on that drive to mount to /boot/efi.

Export the old bpool-old pool. Export the new bpool, then import it, which will then move the mountpoint from /mnt to /boot.


Reinstall grub2, update grub, then re-gen the initramfs images...  

Exit the chroot, umount and export all. Shutdown and remove the old drive...

Test.

I think I covered everything. Maybe 1fallen can look it over to see if I skipped over anything. Or add any clarifications.

---

### Post by dragonomnus on 2024-02-26
Thanks for the update.
Reading through this reminded me I forgot to mention 1 other issue I encountered when following your prior steps, being the exit process was not completing correctly.
The part at the end where you instructed to exit chroot, then "mount | grep" etc, then "zpool export -a"... If failed with "device busy".
I shall need to test it again, but IIRC, the exit succeeds but both the umount & zpool export would fail with "device busy".
I tried repeating that process but did the umount part before the exit and I think it returned no error, but the zpool exit always returned "device busy".
I am not certain if that is part of the issue, or an error on my part (95% certain I followed your instructions correctly), or some unrelated issue, but thought it worth mentioning as it could be a point of failure in this process.

Regarding the backup, I think I shall try to create the backup including any possible errors present.
Reasoning:
If ZFS send/receive omits copying problematic zpool options (though there should be none) because it sends only the dataset to a new pool instead of copying the pool, there would be no harm copying potential problems as part of the backup because I could use ZFS send to restore if needed. Basically, LIVE>BACKUP>RESTORE, it is irrelevant to RESTORE whether potential problems are skipped during LIVE>BACKUP or BACKUP>RESTORE, so copying them as part of LIVE>BACKUP could allow us to work more with the issues if needed and would cause no problem if later needed to restore from.
Regarding methods of migration/backup and considering an exact clone of the drive, my understanding is dd would copy the partitions exactly & entirely including all blank space, correct?
But gparted is able to skip copying blank space of partitions IF it can read the partition, which it cannot read ZFS (yet) but can read vfat of the EFI partition, so it should generally be better to use for cloning drives/partitions, correct?
Then I can use ZFS attach/detach or send/receive where appropriate for ZFS partitions.
I am not certain if I am misremembering what I read of those differences between dd/gparted or if the information was incorrect or what, so clarification there would be great.
While it would not apply as much to my present situation, there is a big difference in copy time (whether SSD or HDD) and SSD wear when you copy an entire partition including the 60% or 90% free space vs skipping the free space.

Regarding variables in Linux, if creating them is done as you indicated by merely typing "VNAME=string" then how do you delete them? Windows uses the SET command to manage varaibles and I can use a modifier to create a temporary variable which survives until I close the terminal session, is that how the variable created using the method you instructed functions? I need to learn more of Linux variables soon.

Regarding the partition sizes, they were created as you said Ubuntu defaults are, but what to adjust them to is another question.
I would see no need for increasing the size of the EFI partition, but I am not familiar with EFI apps. What extra software could you or would you want to install to EFI? Guess I shall need to research this also.
I seriously doubt I would want a 128G swap partition, and saw no problems with the default 2G even with 75% of my 64GB RAM filled at times (largely due to ZFS caching, but I shall add cache drives later). Unless you know some other benefit of a larger swap partition?
bpool becomes the biggest question. zfs-auto-snapshot filling bpool with old snapshots was a problem, but they were between 200M & 300M each so I would need to expand it to something more like 4G or 5G to store all it creates.
Alternatively, I would prefer to learn how to alter zfs-auto-snapshot in multiple ways, including altering its snapshot name scheme and its retention policy. If I can limit its monthly snapshot retention to 2 or 3 then 2G for bpool should be more than sufficient, the question is would that be better than expanding bpool to 4G or 5G to store an entire year of snapshots?
Regarding its naming scheme, it is needlessly lengthy & redundant. It prefixes snapshots with @zfs-auto-snap_ which is rather self-evident. If you are looking at the ZFS snapshots then you already know you are working with ZFS so starting with @zfs is useless while adding needless length, and same goes for the -snap part. The -auto part is self-evident when you look at the snapshots with names of _hourly/_daily/etc, so none of that prefixing should be there but I am yet to determine how to alter it, but that is also not relevant to the primary issues of this thread.

Regarding how to migrate, add/remove would not function for this because that zfs command adds the new drive as an additional vdev to the pool to expand the pool's capacity or add optional devices (SLOG, spare, etc), attach/detach would be required to clone the pool. Also, my understanding is zfs-remove can safely remove only optional vdevs, not vdevs comprising any part of the main storage, which some people call "a limitation of ZFS" but that same thing is true of all striped RAID arrays as far as I am aware with the exception of splitting a mirror which ZFS can easily do.

Regarding the part where you instruct to detach then rename the old bpool, that is 1 part of this I can offer a suggestion! Use "zfs split" instead because zfs-split splits mirrored drives leaving all intact and directly renames the split pools in 1 command. That said, I am yet to test how it functions with mirrors of more than 2 drives as it says it splits ALL mirrors and retains merely 1, but it could be poorly worded or possibly require naming each split. I shall need to re-read & play with it at some point using more than 2 drives, or use files as pools (purely to test & play, not for actual use).

Regarding creating the new bpool, is it necessary to specify all those options? I know some must be specified at pool creation as they cannot be changed later (ashift for example), but I sadly cannot copy the command on the PC in question because Firefox is not displaying correctly when booting from the LiveUSB on it. Firefox displayed correctly when I originally used the LiveUSB to install but perhaps the GPU I swapped in later is not compatible with some driver (or ?). Hrm, I wonder if this could also be an indication of a problem... It should not be an issue because Ubuntu functioned well with the new GPU, rebooted correctly, Firefox displayed correctly, etc. At least until the reboot which never rebooted... So many variables in this issue.
If those options must all be specified, that also creates extra issues. For example, I know some of those affect file permissions/timestamps/etc between Linux/Windows, and the primary purpose of this is to learn using Linux as a server for a typical Windows environment so I need to learn better which options there must be set to what to allow that to function correctly, but are you thinking that could also be part of the problem with why it is not booting? At least for bpool/rpool, I did a default Ubuntu on ZFS install so they should have Ubuntu's default options, whatever those are. I shall compare them later.
To clarify, I technically have 2 extra zpools for hosting files to the network for clients so I think the options for bpool & rpool can be set to what Linux needs or prefers with no issues. I think, feel free to correct as I am not certain here.

Regarding your zfs-send/receive, your instruction is different than what I read before. I read it needed to be "zfs send source | zfs receive destination", not accounting for options. I shall try it your method, but also wonder if there are differences/benefits to either method.

Finally, I never modified fstab before (FileSystem TABle, correct?), so guess I shall learn now.
I shall read through this again and try to learn it all before I try it, and shall post if I have further questions before I implement. Or to inform you of the results.

---

### Post by #&amp;thj^% on 2024-02-26
> **MAFoElffen said:**
> PART 2 -
I think I covered everything. Maybe 1fallen can look it over to see if I skipped over anything. Or add any clarifications.

You did and very nicely in Post #11
That should get the OP back and running with fresh install and migrate back all needed pools.

I'm not sure what's up with his booting issue though, quite puzzling.

---

### Post by dragonomnus on 2024-02-29
Worked on this when I could over the last few days.
Seemingly achieved progress but the PC now fails differently.

I shall post later when I have more time to write out the changes to your instructions which were needed.
For example, "zpool rename" is impossible because there is no such option for the zpool command.

However, aside from again being unable to unmount all zpools at the end because some device is always busy (as I explained before), the entire process seemed to succeed this time.
Until I rebooted to attempt to boot to the new SSD install.
The prior boot issue was it began booting to the Ubuntu recovery menu, was unable to boot to the Ubuntu install, but could put me in grub.
The present issue is it boots directly to grub.
I used:
```

     set root=(hdX,gptX)
linux /BOOT/ubuntu_UUID/@/vmlinuz root=ZFS=rpool/ROOT/ubuntu_UUID boot=zfs
initrd /BOOT/ubuntu_UUID/@/initrd.img
boot   

```
which seemingly began to boot the Ubuntu install, I saw a few fails but they passed too quickly, I shall try to get them later.
However, it dropped me directly to the command line of "root@mypc" instead of loading the GUI as normal.
The info given there is insufficient to know what I should do, but I tried multiple options ("exit", "systemctl reboot", pressing Control-D).
They either did effectively nothing or resulted:
"Starting default target
Failed to start default target: Transaction for graphical.target/start is destructive (emergency.target has 'start' job queued, but 'stop' is included in transaction)."

To summarize the present other info:
The original SSD should be intact as it was but is disconnected from the motherboard (in the case, though).
I copied the EFI & swap partition to an extra HDD, then mirrored bpool & rpool to it, so it should also be a perfect backup.
The new NVMe also has backups of bpool & rpool so I can re-mirror or re-send them to the active bpool & rpool if needed with no need to reconnect the old SSD or backup HDD.

I shall explain further after I sleep & have time, but that is the present summary.

---

### Post by MAFoElffen on 2024-03-04
Sorry command is "zfs rename". Sorry. Did triple shifts. Slept in my car between shifts at the new locations...

Got home, and got my truck ready for this week. which such be slower.

---

### Post by dragonomnus on 2024-03-12
Hey, sorry, was dealing with bigger issues last week.
Was your week slower as you expected? :)

Any thoughts on how to deal with that new boot issue I mentioned in my prior post?
I am curious what caused that new problem as much as how to solve it.
Is that a problem any person experiencing this new Ubuntu on ZFS boot failure would also experience when trying to fix the issue?
I can possibly try snapshot rollbacks to correct the problems but I think (need to verify) I have no snapshots on bpool prior to the kernel update.
But.... I am 98% certain Ubuntu wanted a reboot *after* the kernel update and it rebooted successfully, it was other odd failures a few days later which convinced me to reboot again and *that* reboot never rebooted.
That leaves me more curious, but it could be some other event I am forgetting or unaware of.
I definitely have older snapshots on rpool though so could possibly do a rollback pre-update on it, but I am not completely certain I am performing all these steps to reinstall grub through chroot correctly because they are not fixing the issue for me as it did you and because of not being able to completely cleanly unmount all datasets & pools after doing the various steps.

I should have time to work on it again later this week.
Either way, thanks for all your help & time thus far.

---

### Post by MAFoElffen on 2024-03-12
Actually... This week is slower. In fact tomorrow I'm on standby. I'll find ot about 7am if I have to rush somewhere.

Dang. Feast or famine. Just when I thought things were starting to get consistent.

---

### Post by dragonomnus on 2024-04-24
Been waiting nearly 2 months for instructions or advice regarding that last issue, but seems none shall be provided.
Thankfully I was mostly busy, but that also meant I had little time to work on it myself so it is yet to be fixed.
I began working on it again recently and was able to photograph some of the errors from the failed boot, uploaded to my Google Drive so I shall link that later.

The 1st error seems to be regarding the unknown command line parameters from the boot command, but those should be correct according to multiple other posts & such I read, and that /BOOT/ section seems to not function if I put bpool before it as I read is needed with the root=ZFS=rpool/ part.
No knowledge if that "Optimal transfer size" part is normal or a relevant issue, but the kernel taint errors I would guess are but no idea how to solve them.
I can see it is failing multiple occurrences of the /usr/bin/unshare part, but uncertain if it is trying to mount that folder on each of those devices or whether they are important errors.
I next see it reads from /dev/disk/by-uuid/9507-4A55 and starts & finishes an fsck on it, it being the gpt1 partition which holds /boot/efi.
Next possible issue I see is "systemd-udev-settle.service is deprecated", but I know not whether that is a problem or how to fix it (yet) if it is.
Next errors I see are "filesystem 'bpool/BOOT/ubuntu_j8657t' cannot be mounted" and "boot.mount: Failed with result 'exit-code'.", but why is this if it can read the efi partition & the boot command reads /BOOT/ from gpt3?
That seems to lead to the subsequent errors of failing to mount /boot and the following tasks which need it, correct?
After that come the sysinit.target errors, but I know nothing of it so shall try to research that some, but not certain if it is presently important or shall be fixed if we can solve the prior issue of being unable to mount /boot so advice here would be helpful.
After that are the results of blkid so you can see which partitions are on which devices & such.

[https://drive.google.com/drive/folders/13esniFet4SYFJeyicpJwqUO73fymhe1V?usp=sharing](https://drive.google.com/drive/folders/13esniFet4SYFJeyicpJwqUO73fymhe1V?usp=sharing)

This is as much as I can presently do with what I know & was able to find, so further instruction or advice is needed if I am to solve this problem.
At this point, I could alternatively consider installing fresh but would need to also learn how to migrate installed software & OS configuration, or manually reinstall & modify everything which would not be easy because 3/4 of it required multiple attempts to convince to function because I know very little of Linux.

---

### Post by MAFoElffen on 2024-04-25
That is a lot of errors and warnings. Some that you think are errors are just warnings.

Remind me, which version of Ubuntu with which version of Grub2?

---

### Post by dragonomnus on 2024-04-26
I originally installed Ubuntu on ZFS 22.04 LTS with whatever GRUB it used. That was around end of May last year.
I ran whatever updates Ubuntu pushed, which it installed a kernel update a few days prior to the reboot which never rebooted.
It would be 22.04 unless I download a newer ISO to update the Ubuntu version, correct?

Is there a command I can run at GRUB or the emergency menu to pull the info you seek?
Guess I should remind you I know very little of Linux yet so need instruction if there is some method of getting information you need.

---

### Post by MAFoElffen on 2024-04-26
Sort of. But since you do not know a lot about Linux... Do what I say, without doing something further on your own please.

At the Grub2 boot menu, Take a pciture of that meneu. Then press the <E> Key to show the main menu option's underlying code in an edit mode. Take a picture of that to post a link of or to upload as an attachment. I want to see what those say...

Press the <Esc> key to get back to the Grub2 Main Menu. At the main menu, select Advanced Options, then select and earlier kernel with recovery. When it gets to the recovery menu, select 'netwroking', then select 'root'... Tell me if it gets to the root prompt.

If it gets to the root prompt, type the command: 
```

zpool list

```
Take a picture of the output. Leave it at that screen, while you post those.

I'll check this at Lunch on my phone, then tonight.

---

### Post by dragonomnus on 2024-04-26
Tried but several issues.
1st, I am moderately certain the menu it dumps me to is GRUB, not GRUB2. Photo uploading, shall link.
The  best I found regarding how to force the GRUB2 menu to appear was to  "hold (right) shift" during boot, so I tried holding both shifts  (separately) but got the same GRUB menu each time and it lacks the  options you mentioned.
Now here is the strange part:
I did what I  wrote before of configuring GRUB to boot to Ubuntu and it went to the  emergency mode console again, but it was not rebooting when I typed the  "systemctl reboot" command it said to use to reboot, so I tried the  "press Ctrl-D to continue" option again for the hell of it but this time  it went to the Ubuntu login screen displaying my user to log on.
I did that option before when I posted of all that months ago but it never took me to the login screen.
However,  it seems to remain problematic because when I pressed Enter to login it  went to a blank grey screen & stayed there until I hard-powered the  system off because I could find no other method of rebooting or  performing any action.

I shall try again later when I have more time to get the "zpool list" you asked for, though I am not certain I can get that from the emergency mode console but think I can.
Would it be acceptable to get that list from a live-boot session instead if not?

The menu it dumps me to:
[https://drive.google.com/drive/folders/1BBk8zd_yoPw5x9jV7_qJlry2T6XMc7HN?usp=sharing](https://drive.google.com/drive/folders/1BBk8zd_yoPw5x9jV7_qJlry2T6XMc7HN?usp=sharing)

That said, you mentioned some of what I thought were errors were merely warnings.
1st,  I posted anything resembling a possible error because I am not a Linux  expert to determine whether it is of relevance to this issue, so I am  not assuming anything either way but am guessing based on what I know.
2nd, clarification would be nice. What were errors and what were not? Which of them is important or not?
That could help me focus my research & effort.

---

### Post by MAFoElffen on 2024-04-27
Do you get to a Grub boot menu? Or just to a Grub command line prompt?

Because that would be if it either just got to a Grub Command line prompt --OR-- if at the Grub boot menu, you pressed the <C> Key.

Second, I asked you not to do "anything" on your own, which you ignored that and did anyways. The reason I asked you to agree to that, is (#1) We need to both know where you are with things, with the same understanding. (#2) If I am going to give you detailed instructions, I have to trust that you can follow them.

This is not going to work if you can't follow instructions, or if you are not forthcoming with requested information.

---

### Post by dragonomnus on 2024-04-27
GRUB command prompt, I linked the photo.

Regarding your next comment?
I been trying to follow all your instructions since I initially posted, but you often ignore my questions.
Your instructions are riddled with typos, errors, non-existent commands.
I am doing my best to follow that but it is difficult.
You asked me to do nothing on my own but I ignored it?
You  told me to perform an action I could not perform, so I tried to perform  the part I *could* perform being to go through the GRUB console to  access the root console to run "zpool import" (not "zpool list" because that command is again non-existent), so I was trying to do that and ended up at the login screen when I was trying to exit the console.
And you are now criticizing me for that?
I repeatedly explained errors in your instructions and repeatedly indicated I am new to Linux so need instruction but you AND 1fallen both failed to provide adequate instructions repeatedly.
I explained all the problems I encountered trying to update GRUB as you instructed me to before but encountered an error where apt-update would not update GRUB because it thought it was already up-to-date so I asked if there was a method of removing GRUB to force it to update.
1fallen responded to say he "hand-removed grub" but said nothing of how, so I again asked how and was again given no answer to that.
You need to trust I can follow your instructions?
Your instructions thus far have been ****, filled with errors & typos so they failed until *I* corrected them.
Further, you *are not giving me* detailed instructions much of the time, you often gave generic statements like "update grub" and expected me to know how to do that despite me REPEATEDLY saying I was new to Linux and asking for instructions on how to do the things you asked.
You are also yet to correct multiple of the errors I found in your posts which instructed how to perform the steps you thought would fix the issue but they did not for me, either because your solution does not apply to the cause of my problem or because your instructions are riddled with errors and I am doing my best to follow them despite my limited knowledge of Linux.
You need to trust I can follow your instructions?
I don't trust your instructions much at this point because I, a person who knows very little of Linux, am finding problems in almost all your commands and correcting them myself.
I can follow your instructions better than you can write them, so be careful with who you blame there.
And not forthcoming with information?
I answered EVERY question you asked and gave you MASSIVELY more information than you apparently bothered reading much of the time while YOU ignored many of my questions and provided me with very little information.

Can any better person help me at this point?

---

### Post by MAFoElffen on 2024-04-28
You have still not answered the questions or posted any of the information I requested from the last two posts of mine.

Me not answering your questions from post #19... I started to write that out and figured much of what I wrote about the details of that was a waste of time explaining that to you... When time could be better spent and dealing with the real problems and getting you fixed. 

Yes. It does seem that you do not want my help. That is fine. I only have over 35 years of professional support experience, and have been using ZFS since 2005. I usually charge people for my services. I am a volunteer here. I do not "need" to help you.  Maybe you need someone with other types of experience(?)

Good luck with this. Lets just see if someone else here with ZFS experience volunteers to help you with this. My advice for you is to help people to be able to help you. Communications is the mutual understanding between all parties involved.

---

### Post by #&amp;thj^% on 2024-04-28
> **dragonomnus said:**
> 
Can any better person help me at this point?

You don't get much better than MAFoElffen, and without seeing what was asked, well No One is Happy here.

I can see a high level of frustration for all concerned here. You with your current problem, and Us waiting to see stuff needed to help you.

Best Regards

---

