---
title: "How reinstall Ubuntu 18.04 on single boot system and keep personal data"
date: 2020-04-03
forum: Installation &amp; Upgrades
---

### Post by itsmarco on 2020-04-03
Hey there, 

after messing around with the user permissions in /var/ and  /etc/ and other undocumented things it happened to me that my computer does not boot into GUI. Several error messages and only be able to access via shell. I decided to create an Ubuntu USB stick and reinstall Ubuntu 18.04. Seems easier than debugging. Took me already 3 hours.

Unfortunately, I do not get the Reinstall Ubuntu option ([described here]("https://www.fosslinux.com/2920/how-to-reinstall-ubuntu-by-keep-your-data-safe-in-event-of-system-failure.htm")). So now I have 4 options but I really want to keep my personal data I had before in the home directory (*/dev/sda)* and another hard drive I add as partition (*/dev/sdb)*[B]

1. Erase Ubuntu 18.04.04 LTS and reinstall[/B][B]
2. Install Ubuntu 18.04.04 LTS alongside [/B][B]18.04.04 LTS
3. Erase disk and install Ubuntu
4. Something else[/B]
    You can create or resize partitions yourself, or choose multiple partitions for Ubuntu.

I think I could go for 2. and then manually copy the files from the home directory to the new home directory? Or for 4. and keep my partitions. I am not sure how to do that. 

Before the options I get the following

[I]The installer has detected that the following disks have mounted partitions:
/dev/sda, /dev/sdb, /dev/sdc
Do you want the installer to try to unmount the partitions on these disks before continuing?  If you leave them mounted, you will not be able to create, delete, or resize partitions on these disks, but you may be able to install to existing partitions there.

[/I]Maybe someone could help me or point me to a tutorial. Thank you!

---

### Post by TheFu on 2020-04-03
Backup any data you cannot lose to other storage. Period.
The data disk should be unplugged during the install.

it is very common for someone to make a mistake during an install and accidentally wipe all the data.  it has happened to me, very, very long ago when i thought i knew what i was doing.

if you have real system backups, then these minor problems are easily solved in about 30 minutes.  Perhaps add that to the list of things you'll setup on the new system.

---

### Post by Impavidus on 2020-04-04
The "Something else" option is for manual partitioning and will probably allow you to do what you want, but to give more details we have to know how your hard drives are currently partitioned.

---

### Post by itsmarco on 2020-04-04
> **Impavidus said:**
> The "Something else" option is for manual partitioning and will probably allow you to do what you want, but to give more details we have to know how your hard drives are currently partitioned.

So I have two hard drives. SSD with 128gb (sda) and HDD with 1tb (sdb). When I look into gparted.

Partition | File System | Flags

dev/sda1 | ext4 | boot 
dev/sda2 | extented |
dev/sda5 | linux&#8722;swap |
dev/sdb2 | ext4 |

I have plenty of space in the sdb hard drive. Is sda1 used for booting and my user with all home directory data is inside?

---

### Post by itsmarco on 2020-04-04
TheFu, when you look at my latest message, is it possible to back up my user data into sdb temporarily, then reinstalling ubuntu 18.04 (only sda is effected?) and then simply override the home directory of sda with the backup data from sdb? Thank you for your helpful message

---

### Post by TheFu on 2020-04-04
> **itsmarco said:**
> TheFu, when you look at my latest message, is it possible to back up my user data into sdb temporarily, then reinstalling ubuntu 18.04 (only sda is effected?) and then simply override the home directory of sda with the backup data from sdb? Thank you for your helpful message

Sure. Stuff in a HOME directory is just data.  As long as it gets put back with the correct owner, group, and permissions, there shouldn't be any issues.  It helps that it where it gets put appears to be in exactly the same directories.  The underlying storage really doesn't matter at all.  You could switch from ext4 to LVM or ZFS or whatever else, if you wanted.  It is all about the directory structure, owner, group, permissions and the actual data.  Lose the permissions, and you have next to useless data for anything NOT in a Home directory.  There are certain HOME directory files that must have specific permissions and ownership to work at all,  but it isn't THAT critical like /etc/ or /var/ are.

---

### Post by Impavidus on 2020-04-04
Can you use [boot-repair]("https://help.ubuntu.com/community/Boot-Repair") to create a boot info summary and show us the link? It will tell us exactly how your harddrives are partitioned.

(Don't attempt the standard repair; the tool wasn't made for your kind of problem.)

---

### Post by itsmarco on 2020-04-04
> **Impavidus said:**
> Can you use [boot-repair]("https://help.ubuntu.com/community/Boot-Repair") to create a boot info summary and show us the link? It will tell us exactly how your harddrives are partitioned.

(Don't attempt the standard repair; the tool wasn't made for your kind of problem.)
Hey, yes sure. Here is the report

[http://paste.ubuntu.com/p/FfXnyzkbzq/](http://paste.ubuntu.com/p/FfXnyzkbzq/)

---

### Post by itsmarco on 2020-04-04
[https://ibb.co/W5wX5k1](https://ibb.co/W5wX5k1)
[https://ibb.co/Bgq2nvG](https://ibb.co/Bgq2nvG)

some more information from gparted. I did **2. Install Ubuntu 18.04.04 LTS alongside ****18.04.04 LTS **and now the second Ubuntu was installed in the sdb and not in sda. I think this is because I didnt partition the drive again and it auto-detect that on sdb was enough space. I think I should now delete this new Ubuntu installation, start from the USB stick again, partion sda (around 18gb) and let Ubuntu be installed right there. Is this correct?

---

### Post by TheFu on 2020-04-04
gparted isn't exactly useful in this situation.

**sudo parted -lm** would be.  It will be text that you can select/paste then wrap in "code tags", so all the columns line up here like they do in the terminal.

But really, there wasn't anything odd about your setup.

* backup and data you cannot lose.
* showdown the machine
* disconnect the HDD you don't want touched. That can be power, USB, or SATA cable. 2 of those would be best.
* boot into a "Try Ubuntu" environment - xubuntu, ubuntu-mate, whatever flavor, provided it has a "Try XXXXXX" option is fine.
* There should only be 1 physical disk and the flash drive you booted using seen.
* Run sudo -H gparted and delete all the partitions on the internal HDD you want to start over using.  That's delete, then **Apply** in gparted.  If you don't Apply, nothing happens.
* On the Try Ubuntu Desktop, there should be an "Install" option.  Double-click on that.
* do the install however you like
* reboot in the end. It should say to remove the Disk or Flash media used to install. Do that.
* login on the fresh install, look around a bit. See that stuff is how you like it. If not, now is the time to fix partitions, encryption, whatever.  Don't install stuff or restore the backup data yet.

When you are happy about the partitioning, only then should you shutdown, connect the other HDD up, and restore that data.

---

### Post by Impavidus on 2020-04-05
The boot info summary tells us that you've got a fairly standard system. Unfortunately, the information is already outdated as you attempted to install Ubuntu on sdb.

There's something weird about your screenshots. You've got mbr partitioned hard drives and you old system in installed in legacy mode, but your new install on sdb created an EFI partition, suggesting you installed in UEFI mode. Best not to mix modes.

You can use a dirty reinstall. You can use manual partitioning ("Something else"), select sda1 to use as root partition and NOT format it. That will reinstall Ubuntu, leaving your documents untouched. It's more convenient though to have your documents and the OS in separate partitions.

But I think right now it's best to use a clean install, as TheFu suggests. Copy your documents to a backup drive, disconnect the backup drive, install, restore your backups. If you wish, you can take the opportinuty to repartition your drive.

---

### Post by pbear42 on 2020-04-05
> **Impavidus said:**
> You can use a dirty reinstall. 
Was going to suggest that option.  One way to make it cleaner: Delete all the directories except /home.
Now, don't have to rely on stuff being overwritten (or harmless if not).

---

### Post by itsmarco on 2020-04-11
I did a "dirty" reinstall. Moved my home direction back and added the files to new created one. Most of the data was available except some hidden folders and applications (like the thunderbird profile, etc). I wasn't so hard to get all programs and settings back and it took me less time in finding the error from the problem before. 

Thank you form your help a lot! :-) I guess for the future I will separate the /home directory and I learned a lot about the linux system in general.

---

