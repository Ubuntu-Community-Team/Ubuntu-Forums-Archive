---
title: "fiesty upgrade error - not enough disk space in /boot"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by dfro on 2007-04-20
I am getting an error that states I do not have enough disk space in my /boot partition.  It tells me to free up at least 19.1 M of space.  I checked the partition using gparted and it shows my /boot partition is 47.03 MB in size, 22.94 MB used, and 24.10 MB unused.  It seems to me that I have enough space.  Is this a bug?

How can I fix this problem?

Thanks

---

### Post by Helmi on 2007-04-20
Same situation here except it tells me i have to have 12.1 M of space. I definitely have >20 M. So looks like a bug? Also checked other partitions where plenty of space is left.

/boot is ext3 primary - all other partitions on a LV.

---

### Post by cruss on 2007-04-20
Same situation, df -h shows 23M on /boot but the upgrade says I need 18.5M free. Tried from both the network and "alternative install" cd.

---

### Post by Björn Schließmann on 2007-04-20
Same here (Ubuntu 6.10):

$ df -h /boot
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda6              37M  9.0M   26M  26% /boot
$

update-manager says:

Not enough free disk space

The upgrade aborts now. Please free at least 14.9M of disk space on /boot. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

:(

Regards,


Björn

---

### Post by organiccookie on 2007-04-20
I've got the same problem, only I do have nearly 100% of /boot used... so I guess a better question for me is how to free up space when you need it?

---

### Post by warewolf55 on 2007-04-20
I will add that I am getting the same issue.

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              45M   13M   30M  30% /boot

When I run the upgrade it says that I need to free up 11.2Mb on /boot. Is it possible that /boot needs to be formatted to a clean partition before the upgrade will install? I certainly do not want to 'experiment' as I finally got rid of Winblows and have no other alternative OS to turn to atm.

---

### Post by Helmi on 2007-04-20
i already did some upgrades and i'm sure that /boot doesn't have to be cleaned up before.

---

### Post by Pete051 on 2007-04-20
I had the same problem solved it by re-installing but I do wonder if it was  bug

---

### Post by Meister_Eder on 2007-04-20
It seems similar to the issue already posted here: [http://ubuntuforums.org/showthread.php?t=414450](http://ubuntuforums.org/showthread.php?t=414450)
I suggest you free up more space since I believe the upgrade program is indicating the additional space that you need rather than the absolute space.

---

### Post by Björn Schließmann on 2007-04-20
organiccookie: If you have much of /boot used and can't remember using it yourself, it's probably old kernels. Uninstall them (linux-image-...) but remember to keep at least one ;)

Meister_Eder: Are you really serious? The installer wants more free space than /boot has if it's empty, at least in my case. Why the heck would one need more than 30 MB on /boot? I'm quite sure this is a bug. Or a very serious design flaw.

Regards,


Björn

---

### Post by Björn Schließmann on 2007-04-20
Found the reason. This is from DistUpgradeController.py:

# we check for various sizes:
# archivedir is were we download the debs
# /usr is assumed to get *all* of the install space (incorrect,
#      but as good as we can do currently + savety buffer
# /boot is assumed to get at least 50 Mb
# /     has a small savety buffer as well

LOL, few lines below it this can be found:

 ("/boot", 40*1024*1024), # savetfy buffer /boot

Noot 50 MB but 40 as sa**f**ety buffer.

According to the Changelog, this was done for bug #70638, where some guy upgraded to Edgy with less than 5 MB in /boot, which made bulding the initramfs or whatever impossible.

I think that's ridiculous, but if anyone may show what you could need 50 MB on /boot for, or why initramfs building can't be done elsewhere, I'm willing to change my opinion. Not that it counted. I don't like repartitioning.

Perhaps I'm going to try changing this value and seeing if it works. If I do, I'm going to check back.

Displeased regards,


Björn

---

### Post by dfro on 2007-04-20
Bjorn,

I will be interested in how your experiments turn out.  When I first installed Ubuntu, I read many posts and websites about setting up multi-partition file systems.  I put /boot on its own partition and made it a generous size as per all of the tutorials and forum posts.  It stinks that this is now not sufficient.

I too do not want to have to adjust the partition size.

Dave

---

### Post by Helmi on 2007-04-20
same goes for me dfro.

I've been rather new to desktop-linux when installing edgy a 2 months or so ago. (though i already tested dapper and edgy on my laptop some times). I chose a seperate ext3-partition for /boot and a LVM for the rest. now it doesn't seem there's any space to extend /boot :( and i don't know how to change this nasty situation.

/boot has 50 MB where 16 are currently used.

---

### Post by warewolf55 on 2007-04-20
> **Björn Schließmann said:**
> Found the reason. This is from DistUpgradeController.py:

# we check for various sizes:
# archivedir is were we download the debs
# /usr is assumed to get *all* of the install space (incorrect,
#      but as good as we can do currently + savety buffer
# /boot is assumed to get at least 50 Mb
# /     has a small savety buffer as well

LOL, few lines below it this can be found:

 ("/boot", 40*1024*1024), # savetfy buffer /boot

Noot 50 MB but 40 as sa**f**ety buffer.

According to the Changelog, this was done for bug #70638, where some guy upgraded to Edgy with less than 5 MB in /boot, which made bulding the initramfs or whatever impossible.

I think that's ridiculous, but if anyone may show what you could need 50 MB on /boot for, or why initramfs building can't be done elsewhere, I'm willing to change my opinion. Not that it counted. I don't like repartitioning.

Perhaps I'm going to try changing this value and seeing if it works. If I do, I'm going to check back.

Displeased regards,


Björn

I changed the line (580) from a 40 to a 25 and kicked off the upgrade again. This time it passed the "safety check" and started downloading files. It will be a few hours yet before I know if anything had broken.

---

### Post by DnasTheGreat on 2007-04-20
For the record, I've disabled the check and done the upgrade. Things seems to be running fairly smoothly, with few problems. (Sound doesn't seem to work in the feisty kernel for me, but it's fine in my self-rolled kernel.)

First of all, let me mention that I have a 30MB boot partition. I'll probably need to redo my parititons later, but meh. So I had to flip the switch.

How to upgrade:

Run update manager.
When it gets you to the gksudo (enter password) bit, look at the folder where it's in. (/tmp/tmpSOMETHING).

Go to another virtual terminal (Ctrl-Alt-F1) and edit the file as mentioned above.

Type the password and continue the upgrade.

If you have too little space, it'll at some point error out at a regenerate-initrd step. This is because it saves a backup and doesn't have enough room to hold your old kernel, new kernel, old initrd, new initrd, backup of initrd, and scratch-work of currently generated initrd at the same time. That's fine. Just temporarily move your files in /boot out (and rm the .bak initrds), run apt-get upgrade to have to re-configure the bad packages. Then move your files back.

---

### Post by Björn Schließmann on 2007-04-20
warewolf55: I changed it to 25 too ;)

DnasTheGreat: I did the same, as mentioned, and ran into virtually no problems (36 MB boot partition). I monitored the used space in /boot during the install. When the initrd would regenerate, I would move out all .bak files into some own directory in ~root. No problems at all. At least, I still had some 6.5 MB free (IIRC old kernel, new kernel, both with initrd, backup thereof, and the work version of one kernel's initrd dpkg was processing).

Instead of setting an insanely high free space minimum for /boot, the kernel initrd build process should be changed. (build it in frickin' /tmp!)

Regards and good luck everyone,


Björn

---

### Post by bryanlking on 2007-04-20
If your boot partition is setup as ext3, that could perhaps be the problem.  I believe that ext3 is set up for maintaining a journal of the filesystem which uses a percentage of the available space, even if it is technically available.

I don't know this to be the case, I was just thinking it could be the cause.  If you set up the boot partition as ext2 you won't have the journal taking up space.

---

### Post by kairuri on 2007-04-20
> **Björn Schließmann said:**
> Found the reason. This is from DistUpgradeController.py:

# we check for various sizes:
# archivedir is were we download the debs
# /usr is assumed to get *all* of the install space (incorrect,
#      but as good as we can do currently + savety buffer
# /boot is assumed to get at least 50 Mb
# /     has a small savety buffer as well

LOL, few lines below it this can be found:

 ("/boot", 40*1024*1024), # savetfy buffer /boot

Noot 50 MB but 40 as sa**f**ety buffer.

[snip]
Björn

I am using kubuntu 6.10 - Where can I find this file to edit? 
Just for the record, I have
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              45M   13M   30M  29% /boot

after I have deleted all my old kernels.  I have had 3 alternate kernels in there before so there is plenty room for a feisty kernel.

In the past I have used 20M for /boot with no probs - I thought I was being generous with 45M when I did a fresh install of Edgy

not happy.
Kairuri

---

### Post by K0LO on 2007-04-20
Rats.. me too. My /boot partition is 50 MB and has 36 MB of free space. The upgrader seems to want 41 MB of free space, and is telling me to give the /boot partition "at least 5390k more free space".
 
In my case the /boot partition is the first one on the drive. To enlarge it I would have to move several other partitions up higher. 
 
Perhaps this situation was not well thought-out by the developers? I would venture to say that there will be a lot of people with a too-small /boot partition.
 
I guess I'll bite the bullet and move some partitions around to free up some more space for my /boot partition...
 
**Edit**
 
I enlarged the /boot partition from 50 MB to 100 MB, and now the installer still wants yet another 1 MB of free space! The problem here is that I left the partition as ext3, so when the partition was enlarged the free space only changed from 36 to 41 MB. The rest must have gone to the journal. So I converted the partition to ext2 and now the free space is 81M and the installer is happily downloading the update.

---

### Post by Karl S. on 2007-04-20
I've had the weird problem of it first telling me that I needed 8258K more in boot. I deleted material (about 9M) relating to old kernels, and then tried again. Now it tells me I need 8446K more. Bizarre. I'm holding off on upgrading until I see an easy solution; either that, or I'll just do a fresh install when I have time, which will be months from now.

EDIT: Just tried it again. Now it says I need 10.3M space free in /boot.

For what it's worth:
karl@karl-laptop:~$ df -h /boot
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             4.6G  2.8G  1.6G  64% /
karl@karl-laptop:~$ 

Any idea why the amount of space I have to free keeps changing? I sudo apt-get clean between every failed attempt to install feisty.

---

### Post by Helmi on 2007-04-21
I did the edit like DnasTheGreat did it and it seems to work fine. The upgrade is just running - let's home it will work ;)

---

### Post by Björn Schließmann on 2007-04-21
bryanlking: Just for the records, I always use ext2 for my boot partition, and I had the problem too.

---

### Post by DnasTheGreat on 2007-04-21
(My /boot is also ext2 and my dpkg configuring errored out of space.)

Hopefully this won't be a problem in future upgrades. I seem to recall reading in some bug that the reason they want 40MB is because it's unknown how many kernels you'll install, and they want about 10MB per kernel. I think it was mentioned that the next upgrade will take into account how many kernels will actually be installed.

That said, 10MB per kernel wasn't enough for me because of the backups, regenerated initrd, and stuff (And I had already uninstalled my self-rolled kernel to make sure there was plenty of space.). Also my old kernel got a regenerated initrd, so at one point /boot contained.

old kernel - ~1M
old kernel initrd ~5M
old kernel initrd bak ~5M
new kernel - ~1M
new kernel initrd - ~5M
new kernel initrd.bak - ~5M

(I had about 19MB free before the upgrade and it only installed one kernel.)

And it was trying to generate another initrd. Which makes about 27M used... these numbers are rounded down and there are some other files like config, etc., so it's pretty easy to see how my 30MB partition would get filled.


Things to consider for next upgrade:
Generate initrd in /tmp
Save backups elsewhere?
Don't bother saving backups for new kernels?
Take number of kernels into account
Have installer yell at you if you try to make a 30MB boot partition. ;)
Make the installer temporarily move files out if space is low?

---

### Post by dfro on 2007-04-21
This seems to be an example of the hangover that follows the new release party.  Unexpected problems are revealed that you cannot foresee until a large amount of people try to download/upgrade/install the new version.

Personally, much of what people are describing I cannot completely follow - i.e. removing old kernels, regenerated initrd,  the DistUpgradeController.py file, etc.  I do not want to break my system messing around with the /boot directory and all that it contains.  I hope to see 7.05 or 7.04.1 out soon with a fix for this.

What I really am excited about is the Ubuntu Studio release, which is built on top of Feisty Fawn!

---

### Post by Björn Schließmann on 2007-04-21
DnasTheGreat: ACK. Using /boot as a working directory, is IMHO, crap. Good suggestions. It should only (and that *means* only) be used to store the kernels and their "accessories". That's trivial to achieve.

dfro: This problem can hardly be called "unexpected", IMHO, better a "dirty fix". /boot partitions are traditionally small, and assuming one must have more than 40 MB free space is just not sane. On one hand, the space greatly suffices if you only have one kernel installed, on the other hand, if you have some ten kernels, 40 MB won't be enough. BTW, good luck waiting for a fix. I hope they will fix it soon, though I guess it'll take some time.

Regards,


Björn

---

### Post by Antrix on 2007-04-22
> **DnasTheGreat said:**
> For the record, I've disabled the check and done the upgrade. Things seems to be running fairly smoothly, with few problems. (Sound doesn't seem to work in the feisty kernel for me, but it's fine in my self-rolled kernel.)

First of all, let me mention that I have a 30MB boot partition. I'll probably need to redo my parititons later, but meh. So I had to flip the switch.

How to upgrade:

Run update manager.
When it gets you to the gksudo (enter password) bit, look at the folder where it's in. (/tmp/tmpSOMETHING).

Go to another virtual terminal (Ctrl-Alt-F1) and edit the file as mentioned above.

Type the password and continue the upgrade.

If you have too little space, it'll at some point error out at a regenerate-initrd step. This is because it saves a backup and doesn't have enough room to hold your old kernel, new kernel, old initrd, new initrd, backup of initrd, and scratch-work of currently generated initrd at the same time. That's fine. Just temporarily move your files in /boot out (and rm the .bak initrds), run apt-get upgrade to have to re-configure the bad packages. Then move your files back.

Thanks so much for sharing this information and to you guys that figured this out.

I followed this procedure and it seems to work just fine.

Hopefully they will address this issue, as I'm guessing a lot of people with previous Linux experience have a separate /boot partition.

Regards, Antrix

---

### Post by amsch on 2007-04-22
I have the same problem using Kubuntu - can anybody help me to solve this problem?

---

### Post by Karl S. on 2007-04-22
Still not working.

I tried editing DistUpgradeControler.py (for those who don't know, here's how to do it. As specified above, when upgrade manager asks you for your password, control-alt-f1 to go to a virtual terminal. Go to /tmp/tmpWHATEVER (where whatever = some random string of letters and numbers that you can see if you type dir in the /tmp directory), sudo vim DistUpgradeControler.py, go to line 580, hit c to edit, change the boot number to 25, hit ESC, then ZZ (that is, shift+Z twice), then alt-F7). Proceed with the upgrade. Then it should work.

Except it doesn't work for me.

When I first tried to upgrade, the manager told me I had too much in /usr. So I uninstalled OpenOffice and a lot of fonts I won't use.

Then it told me I had too much in boot. I uninstalled all my old kernels (and got rid of all the files associated with them in /boot that the uninstaller didn't delete). Still too much. So I edited DistUpgradeControler per this thread.

And now it's telling me I have too much in /. What a pain! First it told me I needed 2348K more. So I deleted 5M or so of stuff. Next time, it told me I needed **2683K.** This has been the pattern throughout. I make the space, sudo apt-get autoclean, try again, and then it tells me I need *more* space. This happened when cleaning out the /boot area and now it's happening with /. 

Since I'm quite happy with my Edgy install, I'd rather go without feisty than reinstall (and believe me, if you have a successful wireless with a Broadcom BCM 4318 and successful Beryl with an ATI Radeon Xpress 200M and VirtualBox with WXP reading data off the host machine perfectly, you don't want to reinstall and start all over). But it should, you know, work. Any suggestions?

By the way, I don't have a separate boot partition, so why it should tell me I need more space in /boot AND up the amount I need on every install (unless I just restart: then it resets the count, so to speak) is a total irritating mystery to me. Should I just wait for feisty + 1?

karl@karl-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             4.6G   2.8G  1.6G  64% /
varrun                 950M   156K  950M   1% /var/run
varlock                950M  4.0K    950M   1% /var/lock
procbususb        10M    108K   9.9M   2% /proc/bus/usb
udev                   10M     108K   9.9M   2% /dev
devshm               950M   16K    950M   1% /dev/shm
lrm                       950M   21M   930M   3% /lib/modules/2.6.17-11-386/volatile
/dev/hda5             6.5G   3.8G  2.4G  63% /home
/dev/hda1             9.6G   9.1G  473M  96% /media/hda1
/dev/hda6              35G    32G  2.3G  94% /media/hda6
karl@karl-laptop:~$

EDIT
Well, this is probably stupid, but I decided to change the value of the "small savetfy buffer" from 10 to 4. Now feisty is installing. I guess I'll know in an hour or so if my impatience screwed everything up.

EDIT TWO
Well, it worked. Mostly. VirtualBox took a minor tweak to fix ("sudo /etc/init.d/vboxdrv setup" in terminal). Wireless works. Sound works. Beryl: not so much. I'll look around for a fix.

---

### Post by abado on 2007-04-22
I was having the same problem updating from edgy eft to deisty tonight, tried to free up some space in /boot by deleting older kernel and finally found a solution [[COLOR="Red"]here[/COLOR]]("http://www.informit.com/articles/article.asp?p=667418&rl=1") 
Look under the heading  "I Tried to Upgrade My System, but I Get an Error" and follow thez instructions there, it works for me, I am downloading Feisty now.
Hope this helps :)

---

### Post by redir on 2007-04-23
Ok same problem here to I have:

#df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              20G  620M   18G   4% /
varrun                505M  156K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
procbususb             10M  160K  9.9M   2% /proc/bus/usb
udev                   10M  160K  9.9M   2% /dev
devshm                505M     0  505M   0% /dev/shm
/dev/sda1              23M   17M  3.9M  82% /boot
/dev/sda10            169G  3.5G  157G   3% /home
/dev/sda6             236M  9.0M  214M   5% /tmp
/dev/sda8              20G  2.2G   17G  13% /usr
/dev/sda9              20G  434M   18G   3% /var

The installer is asking me to free at least 37.9M on /boot and I only have 3.9. From previous posts it really doesn't seem to matter if space is freed or not but how does one go about freeing space on /boot?

Could this problem be solved by CLI install with sudo apt-get dist-upgrade? They highly recommend against doing that on there web site.

I guess I will just sit on the fence and wait around awhile.

---

### Post by i8bugs on 2007-04-24
My install asked me to clear 459M in /var.  Do you think the bug fix will cover this too?  I'm not wondering out of my comfort zone to mess with the install code.
bugs

---

### Post by Denis on 2007-04-29
I also had problems updating with the update-manager. It was the same error: not enough disk space. I have a 32 MB /boot partition and only the current kernel was installed.

As mentioned here, I adjusted the script in /tmp before the install. I changed the safety buffer to 18*1024*1024, which was almost the space that was left at /boot. I didn't get the error message any more and the update continued. 

However I started getting errors near the end of the update. Some essential items couldn't be installed (including hal, udev, ubuntu-minimal...). In the end the update failed, leaving the system in an unusable state. I'm pretty sure the problem had to do with the boot partition, because when I checked with a liveCD /boot had no space left on it. 

There was nothing I could do to fix the system, I had to do a clean install :( I suggest everyone to be careful when using this solution. If you get the error about the disk space, it might be a better idea to just make the poot partition larger.

I'm surprised that this bug wasn't fixed yet. There must be more people with this problem?

---

### Post by Björn Schließmann on 2007-04-30
Denis: You've been warned :) As I said, I used 25 MB limit and had 6.5 MB free space during the installation, that makes approx. 19.5 MB needed by the installer.

The reason of many core packages not being installed is probably that the kernel installation failed. All packages you listed depend on the latest kernel, IIRC.

Normally, you don't need to reinstall cleanly at this state. Just delete backups from /boot and use aptitude to continue the installation (I did this once).

"Just" making the boot partition larger is often difficult. It involves heavy filesystem manipulation with at typical installation (where boot partition is at the beginning and has no free space around it). 

Regards,


Björn

---

### Post by DnasTheGreat on 2007-04-30
> My install asked me to clear 459M in /var. Do you think the bug fix will cover this too? I'm not wondering out of my comfort zone to mess with the install code.

Did you run apt-get clean? That will make apt clean out its cache in /var. Usually saves a good bit of space. Other than that, I don't see how you could be using all that much in /var. I only have 1G total and I haven't apt-get clean'ed lately.

Does the default apache install put stuff into /var? I forget. If that is the case, perhaps consider moving the directory.

> The installer is asking me to free at least 37.9M on /boot and I only have 3.9. From previous posts it really doesn't seem to matter if space is freed or not but how does one go about freeing space on /boot?
You'll want some space for the kernel itself. With some fussing, you can get by with much less than the safety buffer, but I think 3.9 might be pushing it. Kernels take about 1.7M and their respective initrd's are about 5 or 6M.

Cleaning up space in /boot is done by removing old kernels, which isn't done by default. Just apt-get remove linux-image-FOO, where FOO is the version number. tab-complete can help a ton here.

Don't remove your currently running kernel though, that might cause some problems. ;) Run uname -r to see what kernel you're running... and I think apt will yell at you if you try to remove your current kernel... if it doesn't, it definitely should.

You should be able to get down to under 10MB used without much difficulty. If not, temporarily move files out and move them back afterwards.


> However I started getting errors near the end of the update. Some essential items couldn't be installed (including hal, udev, ubuntu-minimal...). In the end the update failed, leaving the system in an unusable state. I'm pretty sure the problem had to do with the boot partition, because when I checked with a liveCD /boot had no space left on it.

There was nothing I could do to fix the system, I had to do a clean install I suggest everyone to be careful when using this solution. If you get the error about the disk space, it might be a better idea to just make the poot partition larger.
I had the same problem. All the packages got installed fine, but they never got past their configure or setup or whatever the name is stage.

For future reference or for others, you can remove the initrd.bak files in /boot (you don't need them) and run apt-get upgrade to continue the install. If it still errors out, you can move files out and move them back.

/me is tempted to write an Upgrade-with-small-/boot guide.

---

### Post by redir on 2007-05-02
> **DnasTheGreat said:**
> 

Cleaning up space in /boot is done by removing old kernels, which isn't done by default. Just apt-get remove linux-image-FOO, where FOO is the version number. tab-complete can help a ton here.


Here is what I have:

a@a:/boot$ ls -la
total 16172
drwxr-xr-x  4 root root    1024 2007-04-18 11:41 .
drwxr-xr-x 20 root root    4096 2007-04-02 16:40 ..
-rw-r--r--  1 root root  285721 2006-12-05 17:47 abi-2.6.17-10-generic
-rw-r--r--  1 root root  285721 2007-03-13 19:51 abi-2.6.17-11-generic
-rw-r--r--  1 root root   74707 2006-12-05 16:20 config-2.6.17-10-generic
-rw-r--r--  1 root root   74707 2007-03-13 18:25 config-2.6.17-11-generic
drwxr-xr-x  2 root root    1024 2007-04-18 11:41 grub
-rw-r--r--  1 root root 5455373 2007-03-16 14:42 initrd.img-2.6.17-10-generic
-rw-r--r--  1 root root 5454977 2007-04-18 11:41 initrd.img-2.6.17-11-generic
drwxr-xr-x  2 root root   12288 2007-03-16 12:57 lost+found
-rw-r--r--  1 root root   94600 2006-10-20 07:44 memtest86+.bin
-rw-r--r--  1 root root  728778 2006-12-05 17:47 System.map-2.6.17-10-generic
-rw-r--r--  1 root root  729932 2007-03-13 19:51 System.map-2.6.17-11-generic
-rw-r--r--  1 root root 1636700 2006-12-05 17:47 vmlinuz-2.6.17-10-generic
-rw-r--r--  1 root root 1635958 2007-03-13 19:51 vmlinuz-2.6.17-11-generic

a@a:/boot$ uname -r 
2.6.17-11-generic

 df -h /boot
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              23M   17M  3.9M  82% /boot
jmckenna@jmckenna1:/boot$ 

So apparently that all takes up 17MB. So you are saying I can run apt-get remove inux-image-2.6.17-10. Is that correct?

Thanks in advance.

---

### Post by Denis on 2007-05-02
> **redir said:**
> Here is what I have:
So apparently that all takes up 17MB. So you are saying I can run apt-get remove inux-image-2.6.17-10. Is that correct?


Yes, you can safely remove "vmlinuz-2.6.17-10-generic" since you now have a more recent kernel running.  

You can always remove the previous kernel if the current one is working allright for you,

---

### Post by redir on 2007-05-02
> **Denis said:**
> Yes, you can safely remove "vmlinuz-2.6.17-10-generic" since you now have a more recent kernel running.  

You can always remove the previous kernel if the current one is working allright for you,

Denis thanks,

To elaborate do I need to use apt to remove this stuff properly or can I just go in and rm them? For example I tried this: 

:/boot$ sudo apt-get remove linux-image-2.6.17-10
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-image-2.6.17-10
:/boot$ 

Should I just go into /boot and rm any file with '2.6.17-10' in it or is that asking for trouble?

Thank you.

---

### Post by DnasTheGreat on 2007-05-02
You can rm them manually, but it's usually better to use apt to remove such things. Otherwise apt may still think it's installed and try to perhaps regenerate an initrd, etc.

---

### Post by Denis on 2007-05-02
> **redir said:**
> 
:/boot$ sudo apt-get remove linux-image-2.6.17-10
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-image-2.6.17-10
:/boot$ 

Should I just go into /boot and rm any file with '2.6.17-10' in it or is that asking for trouble?


The name of the package is probably "linux-image-2.6.17-10-generic". So the command should be: sudo apt-get remove linux-image-2.6.17-10-generic

You can also look up the package in Synaptic. Search for "linux" and and you will find the kernel package in the list. Then you can mark it for removal. 

It is definitely not a good idea to remove it manually. The kernel, just like any normal program, is best removed with apt-get (or a graphical interface of it, e.g. Synaptic).

---

### Post by redir on 2007-05-02
Thanks Denis that worked perfectly. Unfortunatlly I still get the disk space error since it did not clear enough :(

---

### Post by Halsnalle on 2007-05-02
> **i8bugs said:**
> My install asked me to clear 459M in /var.  Do you think the bug fix will cover this too?  I'm not wondering out of my comfort zone to mess with the install code.
bugs

I get the same error: It asks me to clear some 270M in /var and emptying my trashcan, but doing so does not free up enough space.  :confused:

---

### Post by brizius on 2007-05-05
> **Denis said:**
> The name of the package is probably "linux-image-2.6.17-10-generic". So the command should be: sudo apt-get remove linux-image-2.6.17-10-generic

You can also look up the package in Synaptic. Search for "linux" and and you will find the kernel package in the list. Then you can mark it for removal. 

It is definitely not a good idea to remove it manually. The kernel, just like any normal program, is best removed with apt-get (or a graphical interface of it, e.g. Synaptic).

Thank's, Denis, for your hint!
I had the error message about not enough disk space in /boot partition, too (more or less 4.5 MB).
Then I removed the old kernel using Synaptic and now I can enjoy with my new Feisty!!

---

### Post by DnasTheGreat on 2007-05-05
> **Halsnalle said:**
> I get the same error: It asks me to clear some 270M in /var and emptying my trashcan, but doing so does not free up enough space.  :confused:

/var is a system folder. Emptying Trash will only help with cleaning /home.

Run
```
sudo apt-get clean
```

Hmm, the Ubuntu upgrader really ought to do this step itself... Or have a "Would you like to clean the APT cache? (Will not harm your system.)" dialog.

---

### Post by Halsnalle on 2007-05-05
> **DnasTheGreat said:**
> /var is a system folder. Emptying Trash will only help with cleaning /home.

Run
```
sudo apt-get clean
```

Hmm, the Ubuntu upgrader really ought to do this step itself... Or have a "Would you like to clean the APT cache? (Will not harm your system.)" dialog.

Yes, my trash is empty anyway, and I've tried ```
sudo apt-get clean
```, but it only frees up a few MBs, so the problem persists.

I first thought it had something to do with me running Ubuntu under Parallels (on a MacBook Pro), but it seems that other people are having similar problems.

---

### Post by DnasTheGreat on 2007-05-05
Hrm.

That's weird. How can you be so low on space in /var. There's very little in there. (mine's not even 1G)

What are the outputs of
```
df -h
```
and
```
sudo du -sh /var/*
``` (reports disk usage in /var)

---

### Post by Halsnalle on 2007-05-06
This is the output:

Filsystem            Storlek Anvnt Tillg Anv% Monterat på
/dev/hda1             2,8G  2,2G  413M  85% /
varrun                143M   80K  143M   1% /var/run
varlock               143M     0  143M   0% /var/lock
procbususb             10M   76K   10M   1% /proc/bus/usb
udev                   10M   76K   10M   1% /dev
devshm                143M     0  143M   0% /dev/shm
lrm                   143M   18M  126M  13% /lib/modules/2.6.17-11-generic/volatile

2,7M    /var/backups
26M     /var/cache
1,5M    /var/crash
12K     /var/games
153M    /var/lib
4,0K    /var/local
0       /var/lock
2,3M    /var/log
4,0K    /var/mail
4,0K    /var/opt
80K     /var/run
60K     /var/spool
404K    /var/tmp

...and now Upgrade Manager tells me to free up 265M in /var/cache/apt/archives/ !

---

### Post by dfro on 2007-05-27
I did a fresh install of Fiesty - Ubuntu Studio.  When I got to the partitioning part of the install, I chose 'manual partition' not automatic and made sure my original /home partition had the /home label.  I also flagged the installer not to overwrite/modify that partition.  It went through with the install and when I started up Ubuntu Studio (with the very cool splash screen and noir vibe), my /home partition was intact with all of the files and original user preferences and settings I had before - whew!

WARNING: I am a newbie who got lucky with this install, copy this with great caution, and backup your /home folder using rsync, etc.

Ubuntu Studio rocks!!!!!

---

### Post by Pumalite on 2007-05-28
I have '/' 100% occupied, but it updates anyway. ????

---

