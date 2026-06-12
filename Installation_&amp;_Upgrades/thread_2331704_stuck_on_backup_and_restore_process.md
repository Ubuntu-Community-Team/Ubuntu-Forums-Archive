---
title: "stuck on backup and restore process"
date: 2016-07-25
forum: Installation &amp; Upgrades
---

### Post by davehenson on 2016-07-25
([COLOR=#000000]APOLOGIES that the post is split up. for some reason when I put everything into a single post, I got an Apache error.)[/COLOR]


I'm confident the issue is something small which is really frustrating. I'm going to try to be thorough in my documentation and provide the needed info. 


Goal - do a complete backup of my UB16.04 notebook so I can install different linux distribs, experiment, break stuff and then easily restore back to last good backup. 


My steps:
After complete install of UB16.04, I have all my programs installed, settings configured, everything is working great.  I then do a backup using this [wiki]("https://help.ubuntu.com/community/BackupYourSystem/TAR")  , specifically I use this command in a term window in the root directory:
```
tar -cvpzf backup.tar.gz --exclude=/backup.tar.gz --one-file-system / 
```


Ok now I have a file named backup.tar.gz which I copy onto a usb hard drive.  That's my backup I'll be trying to restore.

Now I try to test my backup.  Following the directions in the [wiki]("https://help.ubuntu.com/community/BackupYourSystem/TAR"), I restore by booting a live cd (usb key with latest iso on it which is 16.04.1 LTS as of this writing), I attach the USB drive to my notebook, and I run this command in a term window:
```
sudo tar -xvpzf /media/ubuntu/Terapoint5/backup072316.tar.gz -C /media/ubuntu/988836f3d-blahblahharddrivename --numeric-owner
```


The system unzips my file onto /dev/sda2 (which is where it should be as /dev/sda1 is the boot partition and /dev/sda3 is the swap).

Ok per the [wiki]("https://help.ubuntu.com/community/BackupYourSystem/TAR") link I'm following, you will need to restore grub. To do this, you will need to reconfigure it in a chroot. 
```
 sudo -s
for f in dev dev/pts proc ; do mount --bind /$f /media/ubuntu/988836f3d-blahblahharddrivename/$f ; done
chroot /media/ubuntu/988836f3d-blahblahharddrivename


dpkg-reconfigure grub-pc  
```


here's where I run into my first issue. when I issue the last command "grub-pc" I get the following response:
```
dpkg-query: package 'grub-pc' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.


/usr/sbin/dpkg-reconfigure: grub-pc is not installed
```

Ok.....so now I see in the [wiki]("https://help.ubuntu.com/community/BackupYourSystem/TAR") that it states "For more information on repairing grub, see [GrubHowto]("https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB")" which redirects to the [Grub2 wiki page]("https://help.ubuntu.com/community/Grub2").  If you read down to "Installing/Reinstalling/Moving GRUB2" you'll see a link to "[Grub2/Installing]("https://help.ubuntu.com/community/Grub2/Installing")". Under "Fixing a Broken System" there is direction to use the [graphical boot-repair tool]("https://help.ubuntu.com/community/Boot-Repair").  I ran it from download while using the live cd. (also I still had the external hd attached where I stored my image but I tried it as well with it removed and found the same result.)
```

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

```

---

### Post by davehenson on 2016-07-25
It ran and uploaded a log file here - [log]("http://paste2.org/1eIBD7ps") 


shutdown computer and pull the live cd (usb).  Boot up and select "Ubuntu" at the new grub menu and when it eventually comes up, its in the console. the GUI does not start.



APOLOGIES that the post is split up. for some reason when I put everything into a single post, I got an Apache error.



edit to add that I reloaded the boot repair tool mentioned in post #4 and made sure the external hard drive was removed while running it (sdc), rebooted to the same result.  the log file from that repair is [here]("http://paste2.org/vc4VXGIH").

---

### Post by davehenson on 2016-07-26
I looked into a different route by creating a USB thumb drive with Clonezilla. If you google the name it should come up.  there's a good video on youtube that explains how to use it but if you've ever used Norton Ghost then you'll find it very familiar. This way you can snap an image of your "good" system and then feel free to muck it up as much as you need and then get back to a good image.

---

