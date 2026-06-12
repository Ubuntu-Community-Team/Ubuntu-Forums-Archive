---
title: "Ubuntu to ubuntu migration"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by dizzy1234 on 2006-11-06
Hi,

I've just bought a new computer and I want to get as much of my current Ubuntu install off my laptop and on to the new computer with as little hassle as possible. 

I have a full LAMP(HP) stack on my laptop and I could really do with keeping the settings and the data from that but I don't know where all of that is installed. I'd also like my Firefox extensions, etc. and Evolution settings moved over. 

Any ideas?

Cheers
Nick

---

### Post by matthew on 2006-11-06
NOTE: Before you do anything on either computer, [B][I]back up your data!
[/I][/B]
If you have a little hard drive space on your current computer this will be quite easy to do. You can do this several ways. I'll share with you my preferred method, perhaps others will give you some other ideas as well.

If you want to use the same version of Ubuntu that your current laptop has, then I would create a backup of your current hard drive using tar and transfer that backup to the new laptop...this will require an external hard drive or an ethernet connection between the two computers because it will create a very large file.

On the old computer do this, it will create a full backup of that computer in your /home directory with the name backupfilename.tgz
```
sudo tar cvpzf /home/backupfilename.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/tmp --exclude=/media --exclude=/home/backupfilename.tgz /
```Now format the new computer's hard drive as you want it. I recommend booting with the live cd and partitioning the hard drive as follows:```
1 Gb swap
12 Gb /
rest of drive /home
```Adjust as needed/desired. Generally swap should be around 1.5x your ram, but that's not absolute. If you want hibernate/suspend to work it's a good idea to make it somewhat larger than your ram and 1.5x is a good rough estimate. Having separate / and /home partitions are just good practice as it makes OS upgrades easier.

Mount the newly formatted new computer's hard drive and move backupfilename.tgz to the / partition using an external HDD or ethernet connection. Then, in the same directory where the file is issue this command.
```
tar xvpzf backupfilename.tgz -C /
```(don't freak out if you get an error command when it is finished...that's because the entire system has changed. Just recreate the directories below as needed and then reboot.)

then do these to restore the excluded directories:

```
mkdir proc
mkdir lost+found
mkdir mnt
mkdir sys
mkdir media
```-------------

Now I realize this could seem a bit overwhelming if this is totally new to you. 

If the above seems like too much work or too stressful an easier method (to understand/explain, this way will take more work) would be to backup everything in your /home directory, install the Ubuntu OS fresh on the new computer and then put all the data from /home into the new computer's /home. This will preserve all your settings and such. You will need to reinstall all the programs, though, so make a list of what you have installed or at least what you know you need on the new computer. If you do this, make sure the new computer is named the same thing as the old one and that you have the same user name and password as well. This will prevent a lot of problems.

---

### Post by matthew on 2006-11-06
> **dizzy1234 said:**
> I have a full LAMP(HP) stack on my laptop and I could really do with keeping the settings and the data from that but I don't know where all of that is installed. I'd also like my Firefox extensions, etc. and Evolution settings moved over. One more comment. If all else fails or is too complex, you can find your current settings in hidden files in your /home directory. For example, /home/username/.evolution is the folder you want to copy from your old computer to the new one to keep all your email, settings, etc. 

You can see the hidden files using the Nautilus file browser from your menu... 
Places->Home Folder
View->Show Hidden Files

---

