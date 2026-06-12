---
title: "Cloning Drive"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by infinitezero on 2007-10-17
I am hoping someone can point me in the right direction. I have a Hard drive with a SATA to USB  connector that I want to use as a backup; what I would like to do is use the USB drive to weekly backup(clone) the entire system. This way when the internal drive fails I can just take the backup stick in the system, power on and be back up and running. Any thoughts on how to accomplish this?  


Thanks,
iz

---

### Post by logos34 on 2007-10-17
[http://www.partimage.org/](http://www.partimage.org/)
[http://clonezilla.sourceforge.net/gparted-clonezilla/](http://clonezilla.sourceforge.net/gparted-clonezilla/)
[http://www.debianhelp.co.uk/ddcommand.htm](http://www.debianhelp.co.uk/ddcommand.htm)
[http://www.brunolinux.com/02-The_Terminal/The_dd_command.html](http://www.brunolinux.com/02-The_Terminal/The_dd_command.html)

---

### Post by Xenaco on 2007-10-17
Create a bash script file called *diskclone.sh* with the following line:

[B][I]
dd if=/dev/hdx of=/dev/hdy bs=1M
[/I][/B]

*Note: /dev/hdx is the source disk to be cloned  /dev/hdy is the destination disk*

Save this file to your $home/bin/ directory

Enter:

**crontab -e**

This will open your default editor to allow you to edit your crontab file.
Using this editor enter the following lines:

[B][I]# mail any output to `administrator', no matter whose crontab this is
MAILTO=administrator  #your email here if you want a copy of output sent to you
#
# run at midnight, every Sunday
 0 0 * * Sun      $HOME/bin/diskclone.sh >> $HOME/tmp/backup.log 2>&1[/I][/B]

save this change.

This will execute your diskclone.sh script at midnight every Sunday.

**[COLOR="DarkRed"]WARNING:[/COLOR]**  Make sure that you have entered the correct disk names in the dd command!
If you get these wrong or backwards you will erase or overwrite your data.

---

### Post by raja on 2007-10-17
Partimage is the best bet if you want to make an image of the drive / partition. But you have to boot off a live cd to do this. If imaging is not that essential and you instead are content with backing up important files / data, rsync is what you need.

---

### Post by infinitezero on 2007-10-17
I am looking for a complete system backup. I had considered just backing up the important data, but I think the entire system backup makes more sense for my needs.

Thanks,
iz

---

### Post by Xenaco on 2007-10-17
From what I understand **partimage** will image a single partition at a time.

**dd** using /dev/sdx will clone an entire disk with all partitions.

The easiest and cheapest way to clone a disk is to use **dd** to copy it in it's entirety.

**Partimage** will work but will take a few more steps to restore the drive to it's original state.
By the way, **partimage** can be used in command line or graphic mode. **dd** is only command line.

---

### Post by infinitezero on 2007-10-18
I want to thank everyone for all the suggestion and how quickly all of you responded. After looking at the options I think Xenaco methods may fit my needs best.


Thanks,
iz

---

