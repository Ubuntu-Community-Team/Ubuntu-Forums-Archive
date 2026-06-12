---
title: "/ drive full?"
date: 2010-06-29
forum: Installation &amp; Upgrades
---

### Post by Toker S-10 on 2010-06-29
First off i know nothing about computers. Someone I knew put ubuntu on my computer 2 years ago and i love it. But im trying to update to 10.04 from 9.10 and it gets to a point and says my "/" drive needs more room but my computer says i have 134.7 Gb of free space. I've tried a bunch of things to get rid of stuff that I've read online but the number of Mb i need still goes up and down every time. Sorry if i put this in the wrong place i really don't know what I'm doing.

---

### Post by NoBugs! on 2010-06-29
Applications-Accessories-Disk Usage Analyzer may help to find large files.

---

### Post by Toker S-10 on 2010-06-29
i have 140.7 gb and i've used 6.0gb it says i have 134.7gb left. if i type df -h into the terminal it says:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             7.4G  5.5G  1.6G  79% /
udev                  943M  324K  943M   1% /dev
none                  943M  300K  943M   1% /dev/shm
none                  943M   88K  943M   1% /var/run
none                  943M     0  943M   0% /var/lock
none                  943M     0  943M   0% /lib/init/rw
none                  7.4G  5.5G  1.6G  79% /var/lib/ureadahead/debugfs
/dev/sda6             134G  521M  127G   1% /home

---

### Post by Toker S-10 on 2010-06-29
Can anyone help? i just need to know how to clean that folder out with out messing up my computer.

---

### Post by jocko on 2010-06-29
> **Toker S-10 said:**
> i have 140.7 gb and i've used 6.0gb it says i have 134.7gb left. if i type df -h into the terminal it says:
Filesystem            Size  Used Avail Use% Mounted on
**[COLOR=Red]/dev/sda3             7.4G  5.5G  1.6G  79% /[/COLOR]**
udev                  943M  324K  943M   1% /dev
none                  943M  300K  943M   1% /dev/shm
none                  943M   88K  943M   1% /var/run
none                  943M     0  943M   0% /var/lock
none                  943M     0  943M   0% /lib/init/rw
none                  7.4G  5.5G  1.6G  79% /var/lib/ureadahead/debugfs
[COLOR=Red]**/dev/sda6             134G  521M  127G   1% /home**[/COLOR]
Well, your / (/dev/sda3) is only 7.4GB and is close to 80% full. I don't think you can "clean it out" to get enough room. It is too small.
On the other hand your /home (on /dev/sda6) is 134GB, of which you only use about 500MB.
You can probably resize your partitions to add more space to the / partition. You'll need to download a live cd to do that.
Could you post the full output of this command:
```
sudo fdisk -l
```

---

### Post by DJonsson2008 on 2010-06-29
I'm not trying to be funny here but,
have you emptied your trash.

Also I don't know how you have been using the machine but I found 
a lot of trash in my root account when trying to figure where all
the space went.

/home/<user_name>/.Trash

I found emptying trash via my desktop icon did not
delete all the trash all the time. So go to the folder
and check it.

If you have more than 1 user on the machine
there may be more trash out there.
and
/root/.Trash 
sudo nautilus to get at root trash.

---

### Post by DJonsson2008 on 2010-06-29
but like Jocko said you may need more space for the upgrade even after you clean trash and other files. gparted live should help you to resize but it would be wise to back things up before changing partition size.

---

### Post by Toker S-10 on 2010-06-29
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11f2341e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1441    11574801    7  HPFS/NTFS
/dev/sda2   *        1442       11640    81923467+   7  HPFS/NTFS
/dev/sda3           11641       12613     7815622+  83  Linux
/dev/sda4           12614       30401   142882110    5  Extended
/dev/sda5           12614       12856     1951866   82  Linux swap / Solaris
/dev/sda6           12857       30401   140930181   83  Linux

---

### Post by robert shearer on 2010-06-29
If you have been doing your updates regularly (well done) then your apt cache is probably full of old packages.

To make some space try...
```
sudo apt-get autoremove
```
Which will remove packages that are no longer needed or are residual from apps you have uninstalled.

If that doesn't free up enough then try...
```
sudo apt-get autoclean
```
Which will remove packages that are no longer current.

and if that doesn't do it try....
```
sudo apt-get clean
```
to empty the cache completely.
Note that this will remove previous kernel versions which you may wish to keep.

Check size after running each command. The apt cache can get rather large and is exactly as it is called, a cache of the packages you have downloaded.

---

### Post by Toker S-10 on 2010-06-29
i don't have permission to get at the root trash. it's been saying i don't have permission to do a lot of things... And yes my trash is empty. so how to i change the partition sizes? is that something that i'll be able to do myself?

---

### Post by Toker S-10 on 2010-06-29
yeah i do updates every few days. And omg did if find a lot of crap with that first command. That alone got rid of a Gb.

---

### Post by DJonsson2008 on 2010-06-29
To get at root trash
open a terminal and type

sudo nautilus

then go to /root/.Trash

Be sure not to delete anything else when in there.
and exit nautilus when done.

As to whether you will be able to resize your partitions on your
own, I'd say if you are not familiar with partitions you best find
some help with the task. 

In any case it seems wise to backup a drive before resizing its partiions.

---

### Post by robert shearer on 2010-06-29
> **Toker S-10 said:**
> yeah i do updates every few days. And omg did if find a lot of crap with that first command. That alone got rid of a Gb.

Ok try the second one and that should do it.
Hold off on the third, you may have enough space for the upgrade with just the two.
Try it and see.

if not then run the third command.

---

### Post by Toker S-10 on 2010-06-29
i already ran the other 2 the other night. i read them on some web page so i tried them. im gonna try to update now.

well i got to a new screen that says it's gonna work i think. So thanks everyone that helped. I appreciate it.

---

### Post by Toker S-10 on 2010-06-29
So it installed but it said it failed to mount. im not sure what that means or if its an issue b/c it seems to be working fine.

---

### Post by DJonsson2008 on 2010-06-30
That you were able to do a 10.04 update all that within a 7.4G partition is absolutely cool. 

Out of curiosity how much space do you now have left on the 7.4gb partion?

---

### Post by DJonsson2008 on 2010-06-30
Per your mount problem - it must be a partition other than your
OS partition as you booted. 

I'm not at a 10.04 machine at the moment but I recall under system there was a very easy to use disk and drive gui utility that will tell you what is happening, and help you mount any the other partition.

With 7.4gb as OS partition you will likely need to keep bulky things like MP3s and photos on other partition or external drive.

---

### Post by Toker S-10 on 2010-06-30
why is that cool? i think i have 2.3gb left. i had 2.4 before the install.

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             7.4G  4.7G  2.3G  68% /
none                  939M  344K  939M   1% /dev
none                  943M  1.1M  942M   1% /dev/shm
none                  943M   80K  943M   1% /var/run
none                  943M     0  943M   0% /var/lock
none                  943M     0  943M   0% /lib/init/rw
/dev/sda6             134G  524M  127G   1% /home

---

### Post by robert shearer on 2010-06-30
Happy here to see it worked for you.

Keep up with the updates and monitor that partitions state from time to time.

You can run 
```
sudo apt-get autoremove
```
at any time to remove old packages and keep the amount of wasted space to a minimum.

The more apps you install the more you will fill the root partition.  (apps in root. data in home)
 If you have installed an app and find you no longer use or want it then use Synaptic package manager to remove it and then run 
```
sudo apt-get autoremove
```
to clean up any associated packages that are no longer needed.

7.4Gb is a little on the low side but I have run Ubuntu using a 5.5Gb root partition. It just needed daily attention and removing big apps like Open Office so that updates didn't jam it.

9-10Gb for root is what I use on most of my installs.

Don't worry about the size of your partition, just check it from time to time and remember, if it isn't broke then don't fix it.
It has got you through 2 years use no trouble so must work ok eh ?

---

### Post by akelsall on 2010-06-30
I've always found it useful to use the GUI to get a quick snapshot of what's available/free in each partition. The program is called gparted. It can be accesses via the menus (can't recall right now, but I think it's under the right-most menu (to the right of Applications and Places), then select Administration, then I believe Disk Usage Analyzer.

A quicker way is to just open a terminal window and enter:

sudo gparted &

Andy

---

### Post by Toker S-10 on 2010-06-30
ok so i just need to make sure i keep it cleaned up. i can do that. So what do i need to do about this mounting problem? And i just wanna say thanks again with out all your help i wouldn't of been able to figure this out.

---

### Post by DJonsson2008 on 2010-07-01
I think its interesting you can do all this on a 7GB partition as the compactness of Ubuntu from my point of view is part of the OSs potential.

I'm not on a Lucid machine at the moment...but as to mounting the other partition, look at your menus under System>Administration for a mounting utility, as I believe 10.04 comes with a GUI drive/disk partition utility for doing that.

---

### Post by Toker S-10 on 2010-07-01
see i have no idea how cool it is to do it with 7gb. I found that utility but it looks way to complicated for me. Idk if this makes a difference but i'm running windows and ubuntu on this computer.

---

### Post by Sanjeevtrip on 2010-07-01
also check if you have free inodes

```

 df  -hi

```

---

### Post by Toker S-10 on 2010-07-01
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sda3               478K    248K    230K   52% /
none                    212K     852    211K    1% /dev
none                    214K       5    214K    1% /dev/shm
none                    214K      57    214K    1% /var/run
none                    214K       1    214K    1% /var/lock
none                    214K       1    214K    1% /lib/init/rw
/dev/sda6               8.5M     12K    8.4M    1% /home
toker@toker-laptop:~$

---

### Post by DJonsson2008 on 2010-07-01
Something here does not make sense

Your original listings listed 

/dev/sda6 134G 521M 127G 1% /home

Now it lists the drive as...

/dev/sda6 8.5M 12K 8.4M 1% /home

Anyhow if this is an ntfs drive you are attempting to mount
you will likely need ntfs-config

Otherwise I've found the KDE mountconfig tool to be very handy
in mounting drives, but I don't know if either of these will
be an improvement (and or easier to use) than the disk utils gui included in 10.04.

Whatever the case it sounds like you have a functioning Ubuntu install
mounting your ntfs drive may not be all that important if you are able to do what you need to do.

---

### Post by DJonsson2008 on 2010-07-01
For perhaps more clarity as to your drives status in a terminal try 

sudo fdisk-l 

(that's a small l as in list)

And post the results here for further comments.

---

### Post by Toker S-10 on 2010-07-02
that didn't do anything.

---

### Post by jocko on 2010-07-02
"sudo fdisk -l" didn't do anything? Are you sure? Run it again.

---

### Post by robert shearer on 2010-07-02
> **DJonsson2008 said:**
> For perhaps more clarity as to your drives status in a terminal try 

sudo fdisk-l 

(that's a small l as in list)

And post the results here for further comments.


try again with
 ```
sudo fdisk -l
```

(space between )

---

### Post by Toker S-10 on 2010-07-02
ok it worked with the space. this is what it said:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x11f2341e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1441    11574801    7  HPFS/NTFS
/dev/sda2   *        1442       11640    81923467+   7  HPFS/NTFS
/dev/sda3           11641       12613     7815622+  83  Linux
/dev/sda4           12614       30401   142882110    5  Extended
/dev/sda5           12614       12856     1951866   82  Linux swap / Solaris
/dev/sda6           12857       30401   140930181   83  Linux

---

### Post by mancocapa on 2010-07-02
Hello Toker 
 
I am in the same boat as you knowing nothing about computers but liking ubuntu
I have 9.04 and I get the same "/"when I try and use update manager
 
Although I have made myself a root user sudo does not work for me it just asks for my password and when I try to enter it nothing happens
 
Forgive my ignorance.......help with this would be appreciated
 
Thanx

---

### Post by Toker S-10 on 2010-07-02
if you read threw this thread and do the cleaning commands it mite work. that's how mine finally did.

---

### Post by robert shearer on 2010-07-02
I am not sure what partition it fails to mount here.
> **Toker S-10 said:**
> So it installed but it said it failed to mount. im not sure what that means or if its an issue b/c it seems to be working fine.

When you say it works fine then i presume you are able to: boot up, run applications, save files and access them later, and shut down ??.

When does the "failed to mount' message happen and what is the complete message ?

From what you have posted you appear to have a Windows O/S and the Ubuntu root partition as primary partitions then an extended partition containing the Ubuntu swap partition and your Ubuntu Home partition. ??

You are dual booting Windows and Ubuntu.?

Can you access you Windows partition from Ubuntu ? 
(Places=>"xxx-something"-Filesystem)

---

### Post by Toker S-10 on 2010-07-05
idk whats failing to mount. Yes im dual booting windows and ubuntu, basicly when i turn it on it gives me the option to boot or windows. I pick ubuntu and the first screen that isn't just words on a black screen says failed to mount Skip or Manual. And yes i can go in a look at all my windows stuff from ubuntu still. So idk what the problem is.

---

