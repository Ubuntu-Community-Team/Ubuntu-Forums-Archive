---
title: "Reinstall Gutsy"
date: 2008-02-10
forum: Installation &amp; Upgrades
---

### Post by varnil on 2008-02-10
Well basically i got myself into a fairly sticky mess. I installed ubuntu onto my HP Pavilion dv6500 and everything's been running smoothly for a while, and after fixing several hardware problems/issues i finally decided to fix compiz. I have an Intel (M) gm965 chipset gfx accelorator and as such have run into significant problems with compiz out of the box. Basically the graphics card was blacklisted so i comented out the line in compiz' config to ignore it (it claimed that activation of compiz interfered with video playback). Anyways after that i was successfully able to use compiz starting it with compiz --replace. This worked out for a while yet most 3d demanding apps became extremely glitchy. anyways i read somewhere that upgrading to the newer version of the linux kernel would marginally fix the issue. Thus i did the following (and am not sure if it worked): 
1). I added the hardy repository to my sources.list file (Specifically the following 2)
                 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
                 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe 
2). I upgraded to the newest hardy kernel, i.e.:
                 sudo apt-get update
                 sudo apt-get install linux-restricted-modules-2.6.24-7-generic linux-image-2.6.24-7-generic linux-ubuntu-modules-2.6.24-7-generic
3). Well it worked out nicely and i got a success message, however i then figured i'd update to the newest version of the xOrg intel driver. And i instantly realized it to be a mistake (i probably broke compatability somewhere) as it began removing several programs including the majority of the ubuntu gui (nautilus, firestarter, synaptics, ubuntu-desktop, loads of other things i can't remember). anyways the computer rebooted (without giving me a choice) and upon showing the ubuntu loading screen entered the comand terminal (as if in recovery mode)
Well obviously i tried several things to recover i tried starting x windows manually yet got next to nothing (ie i entered xstart/startx (not sure which one) and i got a lowres display with an unmovable mouse) i immediately aborted restarted and from then on am searching for a way to revert all packages to the initial install
--------------------------------------------------------------------------------------------------------------------------
PS: Formating the disk and restarting is not an option for me as i have the better part of 40GB of personal data on that partition and no medium to save it too)
PPS: I (can't believe i'm using the following word's in the same sentence) luckily had a vista install on a seporate (80gb) partition on my hdd  and am currently using it to type this. I also have a 10gb hp restore partition that i CANNOT and if i could COULD NOT move, and a 57Gb partition from which I boot Gutsy. 
PPPS: PLS Help...:confused:

---

### Post by ESPOiG on 2008-02-10
This should help you.

1. Boot Vista
2. Install this Program that allows Windows to read/write ext2/3 (hopefully your linux partition is ext3) [http://www.fs-driver.org/](http://www.fs-driver.org/)
3. Copy the files you need to save onto your Windows HDD
4. Reinstall Ubuntu this time with a seperate /home and / (you can do this manually when you do a fresh install)

That should be all

---

### Post by varnil on 2008-02-10
I am not sure what you mean by the last instruction. Do you mean specify a seporate partition for home and for gutsy itself? if so how exactly does one go about doing that? anyways this is actually a very good fallback plan (also thnx for the ext2/3 software i was unaware that one existed for x64 versions of widows) however i don't have nearly enough memmory on my windows hdd to store my files and as such would still prefer a recovery method...
I have tried fixing the package problems via the following: 
apt-get -f install
dpkg --configure -a
Both of which provided no results

---

### Post by ESPOiG on 2008-02-10
Im not too up on the fixing packages side of things, but for answer your question on seperate partitions, yes what you do is this.

When your installing Ubuntu via livecd or even text mode when you get to the partition section you manually edit your partition table, and you select which partitions you want and for what, basically you have as an example

sda1 - vista/backup
sda2 - vista
sda3 - / (linux root)
sda4 - swap

What you want to get to is

sda1 - vista/backup
sda2 - vista
sda3 - / (linux root)
sda4 - /home
sda5 - swap

Now my knowledge on how many partitions a hdd can have without an extended partition is not with atm, id have to look it up but you may have to do that to get that many which would mean you could have an extended partition with all 3 linux partitions in a group or so.

To do this you just manually configure your partitions while installing ubuntu make sure you set mount points for each partition. Then each time you if you need to reinstall linux you keep your /home and just add the mount point to it and format the / then installing fresh over your clean / you stick with the same /home partition thus keeping your data intact incase of another accident.

I hope that is helpful, im not too good at explaining things.

PS. if you could possibly wipe your vista backup partition you could format it and store all your data on it for backup, you could do this using the Ubuntu disc as it is a live cd.

---

### Post by BobLand on 2008-02-10
ESPOiG,
Can one have home on a separate disk?  I like the idea of separation so reinstalling new versions or even distros makes for a much safer experience.

bobland

---

### Post by ESPOiG on 2008-02-11
> **BobLand said:**
> ESPOiG,
Can one have home on a separate disk?  I like the idea of separation so reinstalling new versions or even distros makes for a much safer experience.

bobland

Yes you can set it up however you want, for example. Say you have 3 hard drives, you could have Windows on one, Ubuntu on the other and and your /home on the other.

sda1 - / (Ubuntu Root)
sda2 - /home
sda3 - Windows

By doing this you can always have your files separate from the install. Also you can always change distribution with no problems, you can just install the Distro over the top of Ubuntu and Still have your /home intact, although i would suggest being careful using the same user name when switching distros because of permissions, but the same distro would be fine, and also if your worried just changed the name of your user or change the name in /home/"user" to something else while in the live cd then you can just make your original user name and just copy the files from one dir to the other, and because they would be on the same partition no long waits.

On another note you never need a huge amount of space for a / (Root Install) since all your personnel files would be stored on another HDD, so can have multiple distrobutions running from the same / hard drive, example.

sda1 - / (Ubuntu Root) / (Arch Root) / (Fedora Root)
sda2 - /home
sda3 - Windows

But still with the user name thing watch for permissions as you might have problems in other distributions.

PS. Sorry i just noticed you mentioned other distros as well, sorry.

---

### Post by Partyboi2 on 2008-02-11
You can move your currrent home folder to its own /home partition see [here]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by BobLand on 2008-02-11
When partitioning, does it matter what order root & home are in?

---

### Post by varnil on 2008-02-11
Is there a way to resize a linux partition in windows? basically i want to delete all non personal files from my basic install, shrink away 5-10gb for my new linux install and use the rest for personal data... is there a way to do this directly in windows or must i copy the files to a new medium format everyithing and start over with Ubuntu...?

---

### Post by Partyboi2 on 2008-02-11
> **varnil said:**
> Is there a way to resize a linux partition in windows? basically i want to delete all non personal files from my basic install, shrink away 5-10gb for my new linux install and use the rest for personal data... is there a way to do this directly in windows or must i copy the files to a new medium format everyithing and start over with Ubuntu...?
You can use gparted on the ubuntu live cd if you like, or if you do not have the ubuntu live cd you can get gparted live from [here]("http://gparted-livecd.tuxfamily.org/")
Gparted on the ubuntu live cd is called "partition" editor and can be found under System>Admin>Partition Editor. Then you will see the option to resize a partition between the copy and delete button.

---

### Post by varnil on 2008-02-11
Wow thnx for the solution seems kindof obvious now, i just didn't think a live session would let me manipulate things like that

---

### Post by Partyboi2 on 2008-02-11
The live cd is good for working on partitions, because the partition needs to be unmounted to work on and the live cd provides that environment.

---

### Post by ESPOiG on 2008-02-15
> **BobLand said:**
> When partitioning, does it matter what order root & home are in?

no it makes no difference, the only thing i like to keep is my first hard drive that boots from bios as my linux one, rather than having windows on it and having problems with bootloader.

---

