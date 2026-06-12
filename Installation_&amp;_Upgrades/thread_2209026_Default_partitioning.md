---
title: "Default partitioning"
date: 2014-03-03
forum: Installation &amp; Upgrades
---

### Post by linuxonbute on 2014-03-03
Hi all,
Can someone tell me what the default partitioning is for Ububtu?
I have not used it for years because i have always found that upgrades have screwed something up.
It used to be that /home was not on it's own partition so a fresh install would mean having to restore it from backup.
As I have been using my own partitioning scheme since around 7.x i have no idea what the default is now anyway.
I have set up ubuntu for several friends and family and have always used the following:
/
/var
/tmp
/home
each on it's own partition.
Oh, and of course a swap area
Each new install has been this way and all partitions formatted  except /home each time.
If I knew enough about how it is set up I could edit the system and create my own disc so it did it
that way without me having to do a manual setup.
tia
Norman

---

### Post by deadflowr on 2014-03-03
The default partition layout for Ubuntu is one large root and one small swap.
Usually, if using whole disk, 
/dev/sda1 = /
/dev/sda2 = Extended Partition
/dev/sda5 = swap

Extra simple.

I think if you install on the newer UEFI systems then it makes a special boot partition.
Never done it myself, so can't elaborate further.

---

### Post by linuxonbute on 2014-03-04
Yes it is very simple but that means it causes the same problems as with Windows.
If the /home was on it's own partition each user would keep all their own settings, passwords and so on.
Linux should lead, not follow, shouldn't it?

---

### Post by oldfred on 2014-03-04
If multi-user, each uses still has own settings. It does not matter if /home is a folder or a partition.

But the advantage of a smaller / (root) is now with hard drives becoming very large. The Linux formats write files throughout entire / so some boot files may be at beginning of drive and some at end. Makes drive work a bit. 
So I often suggest a smaller / of 10 to 25GB and separate /home or what I actually use data partitions and linking of data back into /home. 
My / is 25Gb with 11GB used including /home, but all data in data partitions.

---

### Post by linuxonbute on 2014-03-04
Hi oldfred,
thanks for your thoughts on this.

If it is as deadflowr says and the default is one single partition ( and I have no reason to doubt what he says )
Then an install will wipe out every users settings and data. You cannot let it install a newer version and protect the data if it is all one partition unless you can tell it not to format the drive - which of course you don't get the option to do if you choose the default install system.

Having a separate data partition is, I believe intrinsically, no different to having /home on it's own partition and the default install will not link a data partition or disc to /home.

Sure people like us who have some experience of the system can sort these things out 
but a newcomer from Windows who is not in the same position as us will have no idea about this.

I just wonder why the default isn't a separate partition for /home so this problem doesn't occur.

If I can find out how to change the default settings to do something like this I would for my  own use and that of anyone I install it for.

If they watch me install it and I just select 'Use whole disc' and it does it that way I am sure it will be more likely to convince them Linux is easy to install than if I have to select 'Something Else' and then have to go through using disc partitioning software before it even starts to install Linux on their PC.

---

### Post by mastablasta on 2014-03-04
> **linuxonbute said:**
> 
If it is as deadflowr says and the default is one single partition ( and I have no reason to doubt what he says )

It is.
> 
Then an install will wipe out every users settings and data. You cannot let it install a newer version and protect the data if it is all one partition unless you can tell it not to format the drive - which of course you don't get the option to do if you choose the default install system.

Install and upgrade won't, formatting during install will erase data.
> 
Having a separate data partition is, I believe intrinsically, no different to having /home on it's own partition and the default install will not link a data partition or disc to /home.

it actually is different. it's sort of like having "My Documents" or is it "users" now ?! on separate partition. it works but in certain cases symbolic links to home are better.

> 
I just wonder why the default isn't a separate partition for /home so this problem doesn't occur.

in my opinion there is no problem with home being on /

there is also not really a problem having it on separate partition.
> 
If they watch me install it and I just select 'Use whole disc' and it does it that way I am sure it will be more likely to convince them Linux is easy to install than if I have to select 'Something Else' and then have to go through using disc partitioning software before it even starts to install Linux on their PC.

as mentioned it might be better to create data partition and leave home on /. unless you are multibooting you don't actually need separate /home partition on desktop.

if you wanted to have My documents on separate disk partition or to create data parittion in windows you would also need to choose "advanced" during setup.
Some more opinions on this topic: [http://ubuntuforums.org/showthread.php?t=2091983](http://ubuntuforums.org/showthread.php?t=2091983) 

bottom line - defaults are preety sane.

---

### Post by Norman_Elliott on 2014-03-04
Boot a live disc and choose use whole disc will trash everything on the disc. It will delete all partitions and put the whole system on one partition.
So where am I wrong?
If instead you choose to install along side what is on the disc already it will leave whatever is there and still put the installation on one partition.
There will in both cases there will be no room for a data partition.
Sure I can fire up gparted afterwards and shrink the partition, create a new data partition and symlink it to /home but I will have lost all my data and have to restore from backup.
Now I want to impress a new user with how wonderfully easy linux is to install not perform what is to them arcane magic.
So that is why I asked the original questions.

---

### Post by mastablasta on 2014-03-05
what you want is customized OS install. i mean why stop at one partition? why not create separate Video, Files, Music, Pictures partitions?  Why not create separate program partition?

For example on my windows maschine i have 2 hard disks and the following partitions:
System
Games and programs
Virtual disks
Downloads and pictures
Data, iso images


you can bet that this wasn't offered as system's default. furthermore i doubt everyone else will divide disk like i have. 

for normal user everything on one partition should be OK. Windows usually also comes preinstalled only on one partition (maybe they have additional boot partition, while various tools and restore parittion do not count in this case). same goes for other OS. 

i did show to my father how you install an os in 20 minutes. left it at default partitioning. it erased the preinstalled SUSE (which also had one / and /swap and another restore thing i believe). works just fine.

---

### Post by linuxonbute on 2014-03-05
Hi Mastablasta,

I think you are misunderstanding what I am saying here. Maybe I am not explaining it well enough.

I have always had to do a fresh install because any time I have tried upgrading to the latest release it has messed up.

Now if the default install created / and a separate /home and didn't format /home  then anyone even without absolutely any understanding of computers whatsoever
could just boot a live distro and click 'default install' and no-one would loose their settings. 

All they would have to do afterwards would be to install any extra software they wanted over and above the standard.
 
As it is this just does not happen so anyone who knows about these things as we obviously do could still choose custom install.

However anyone who doesn't understand would just wipe all their photos, documents, and so on and have no way of getting them
 back as they would probably be someone who doesn't do backups either.

---

### Post by mastablasta on 2014-03-05
> **linuxonbute said:**
> I have always had to do a fresh install because any time I have tried upgrading to the latest release it has messed up.

Now if the default install created / and a separate /home and didn't format /home then anyone even without absolutely any understanding of computers whatsoever
could just boot a live distro and click 'default install' and no-one would loose their settings. 


so you issue is the upgrade (which so far has worked for me). Upgrades work well as long as the system is not heavily cusomized.

one can upgrade from internet or from install media.

as i said before oyu can also do a reinstall where you overwrite the previous version with new version leaving the files on disk (without formatting). which is almost what the upgrade does and definatelly what the windows upgrade does (i still have win98 files left over on ye old mashicne...).

more here: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
I underlined..
> Renewing the Installation **without formatting** the partitions (in contrast to upgrading), will also _keep the personal data and configurations under /home but will renew all system settings under /etc as well as the default set of installed packages_. 


mint backup tool - backup the settings if you need them backed up. if you do a reinstall you should backup anyway...

---

### Post by vanadium on 2014-03-05
> **linuxonbute said:**
> Hi Mastablasta,
Now if the default install created / and a separate /home and didn't format /home  then anyone even without absolutely any understanding of computers whatsoever
could just boot a live distro and click 'default install' and no-one would loose their settings. 

That can be a problem. Application config files may change between versions, and that is out of control of the OS. An application might thus break if an old config dir is used. An installer maintaining a separate home would face another problem: the installation routine would have to be able to determine automatically what partition to use for /home. Depending on the current configuration, this may or may not be obvious.
> However anyone who doesn't understand would just wipe all their photos, documents, and so on and have no way of getting them
 back as they would probably be someone who doesn't do backups either.
Rather than have the OS take the more complicated and risky path of defaulting to an install with a separate home (and how could the installer guess what separate partition is to be used?), we'd better teach the users that they need at any time an up to date backup copy of their valuable data on a removable medium. Users that just keep their data on their computer do not know better, and if they do, do not value their data. Hardware or software issues independent of an install may cause them to loose their irreplaceable data.

I agree that the defaults are simple and sensible. As an advanced user, I do things using custom install, but only because I know what I am doing and what I want.

---

### Post by hhtmp88 on 2014-03-05
> **linuxonbute said:**
> Hi all,
Can someone tell me what the default partitioning is for Ububtu?
I have not used it for years because i have always found that upgrades have screwed something up.
It used to be that /home was not on it's own partition so a fresh install would mean having to restore it from backup.
As I have been using my own partitioning scheme since around 7.x i have no idea what the default is now anyway.
I have set up ubuntu for several friends and family and have always used the following:
/
/var
/tmp
/home
each on it's own partition.
Oh, and of course a swap area
Each new install has been this way and all partitions formatted  except /home each time.
If I knew enough about how it is set up I could edit the system and create my own disc so it did it
that way without me having to do a manual setup.
tia
Norman
Hi linuxonbute!

For a 120GB SSD, how you will allocate the size of each of the partitions?
-> Am I right that the boot partition should be arround 250MB?

Thanks for any kind of help!

---

### Post by oldfred on 2014-03-05
For a newer system with an SSD, I would not have a separate /boot.
My SSD is 64GB. I do not have Windows on SSD, and hoped to move it in the future to a new system with UEFI. So I partitioned with gpt, created an efi partition first for future use, a bios_grub for current use and two 28GB / (root) partitions, current & next. All data and swap is then on a rotating drive.

---

### Post by linuxonbute on 2014-03-05
Okay mastablasta,
So I have 13.10 on my system right now with the partitioning I have stated.
If I try an upgrade to 14.04 when it's available you think it will work without problems with this partitioning.
I have a 3TB Nas so I can do a full backup of my 320 Gig hard disc if it comes to it.
Or I could do what I did with my laptop which came with Win7 home premium - used dd to copy the lot and then cleared it all off and 
put Linux on the whole disc.

---

### Post by mastablasta on 2014-03-05
what partitioning? this one?
/
/var
/tmp
/home

i am not sure how exactly the upgrade works, but partitioning alone shouldn't affect it. eventhough it is not clear to me why /tmp and /var would need separate partition on a desktop...

a backup before upgrade is always good (image the disk). 

read more about reinstall here: [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)

Linux Mint does upgrades the following way. you get a mintbackup tool - that will separatelly save home and then save program settings. you backup reinstall and then restore the backups. i never tried it but apparently it works. i did something simialr using Ubuntu and mintbackup tool. howevr i did a new fresh install with disk format at the time. if i remember it was form 10.04 Ubuntu then erased and replaced with 11.04 Kubuntu. so not many of previous settings were usefull but bookmarks and such remained.

mintbackup: [http://community.linuxmint.com/software/view/mintbackup](http://community.linuxmint.com/software/view/mintbackup)

---

### Post by upchucky on 2014-03-05
other than using clonezilla to create an image of your partitions before an upgrade or fresh install it is better to have home on a separate partition and even better to have it on a drive separate from the os partition, this is true in linux and windows.
as for ubuntu setting as a default extra partitions as I have indicated above is not practical because not everyone has the real estate available for extra partitions.
With that said it is very easy to create a separate home partition even after installing ubuntu. the os core partition only needs to be about 25g.
with a separate home partition all files and data will always remain intact after an upgrade or fresh install unless you tell it to use the entire drive. by telling it to use the entire drive it wipes the drive.
Take note that even if you have wiped the old partitions and have not used the computer much there are ways to recover old partitions C.A.I.N.E comes to mind for forensic recovery.

---

### Post by desconocido on 2014-03-05
> **mastablasta said:**
> so you issue is the upgrade (which so far has worked for me). Upgrades work well as long as the system is not heavily cusomized.

Well, upgrades have been a disaster for me too. So I always change Ubuntu version by re-installing.

I now keep /home on a separate partition from / and re-install by selecting "other..." at install time; formatting the partition where / is mounted; not formatting the partition where /home is mounted but first deleting all the hidden files in my home directory except a few essentials like .thunderbird and .mozilla. I find this makes a more stable install.

So an option for the Ubuntu installer to automatically notice in which partitions various bits of linux are mounted and sensibly format them or not (and give a choice) and reinstall into them would be very handy.

---

### Post by mastablasta on 2014-03-06
upgrades will always be a disaster if OS is heavilly cusotmized/tweaked. newbies usually do not do that.

upgrades also used to be an issue if you had proprietary drivers installed. especially GPU. you got an unworking OS on boot. those are now automaticly disabled, system is upgraded and then they are updated and re-enabled. same issue was for PPA's but i think those get disabled now on upgrade as well.

i did a test upgradeing form 13.04 to 13.10 with all extra stuff & tweaks left enabled and upgrade was smooth.

---

### Post by vanadium on 2014-03-06
> **desconocido said:**
> I now keep /home on a separate partition from / and re-install by selecting "other..." at install time; formatting the partition where / is mounted; not formatting the partition where /home is mounted but first deleting all the hidden files in my home directory except a few essentials like .thunderbird and .mozilla. I find this makes a more stable install.


That is also essentially how I work now. Prior to an install, I rename my old home directory. After install, I move the data, the .thunderbird folder and for firefox only the bookmarks to the new configuration. I find an 8 GB root partition is sufficient. If it starts to fill, this is due to old kernels.  Currently, with one backup kernel, I still have 2.2. G free on the root partitioning.

I do, however, also redirect the temp directories /tmp and /var/tmp to the separate home partition so there is no chance to fill the root partition if some app uses it to write a lot of temporary data.

---

