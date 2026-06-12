---
title: "Replacing /home SSD"
date: 2021-04-24
forum: Installation &amp; Upgrades
---

### Post by robert48 on 2021-04-24
Hello, whilst running Ubuntu for some time now, I am not up to date with current installation processes when it comes replacing a Solid State Drive (SSD) dedicated and mounted as /home.

My existing 240GB /home SSD is increasingly showing bad sectors and is quite old now. I want to replace it with a 1TB new ssd, again mounted as /home. I remember that I could do a fresh install, having backed up /home on an external SSD, and in the install process could designate a drive mount as /home.

What would be the most efficient way of replacing my /home drive please?

Many thanks

---

### Post by CatKiller on 2021-04-24
> **robert48 said:**
> I remember that I could do a fresh install, having backed up /home on an external SSD, and in the install process could designate a drive mount as /home.
Do you *want* to do a fresh install?

Which partition gets mounted where is controlled by a simple text file: /etc/fstab. You can simply mount your new partition (which you'll need to create on your new drive) somewhere - it doesn't really matter where - and copy your stuff from the old place to the new place. Change your fstab so that it uses the UUID of your new partition rather than the old one to identify what you want mounted at /home, and job done.

---

### Post by rsteinmetz70112 on 2021-04-25
The simplest way is:[LIST=1]
[*]Connect the new drive. 
[*]Format it it to whatever Linux filesystem you prefer, ext4 is the default and a good choice. 
[*]Copy your files or restore your backup to the new drive.  
[*]Edit /etc/fstab.
[*]Remove the old drive.
[*]Mount the new home directory.
[/LIST]

---

### Post by robert48 on 2021-06-26
Thank you all for your assistance.

I now have my system drive failing (12 bad blocks). So I am about to replace that. If I do 'a something else' install, designate a new SSD as the system drive (/) and then designate my new home drive (/home) without formatting the latter, will the install preserve all home files?

---

### Post by ajgreeny on 2021-06-26
I am a little confused about whether or not your home files and folders, not forgetting all the hidden ones, are already in the right place, or if that is an empty new disk as well.

If, as I believe is the situation, your current /home is on the failing disk and simply backed up somewhere else, you **will** need to format the new disk for home as ext4 (or other chosen Linux filesystem) because the files will not yet be on it and also make it use the /home mountpoint.
Now, still using the live system used for installing, copy across everything from your backup to the new home disk, again remembering all the hidden items; you did back them up, didn't you?

Good luck.

---

### Post by oldfred on 2021-06-26
Details on moving /home.

To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by robert48 on 2021-07-01
Thanks again. I have tried to restore Backups to a new drive. My Backups is the home folder.

I can see the backups displayed when I click on the restore button. I select all (which is the Home folder), choose my future /home drive, previously formatted to ext4 using gparted, as 'new folder' then restore. A very long list of 'do not have permission' exceptions are shown including Documents! I do not think using Backups and restoring to a different drive is viable for me.

The help file proposed by oldfred ([https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)) looks understandable to me. I am a little concerned that it was last updated 2015-11-13. 

I have followed the 'Partitioning/Home/Moving' document and got as far as step 7. (Note that steps 6 and 7 are reversed in the Contents and Overview narrative). Moving /home into /old_home. I had a 'Device or resource busy' fail.

> bob@bob-desktop:~$ cd / && sudo mv /home /old_home && sudo mkdir /home
mv: cannot move '/home' to '/old_home': Device or resource busy

Managed to move on by changing /etc/fstab. I changed /media/home to /home and commented out (#) the previous /home line. It worked but I did thoroughly check that copying my old home directory to the new drive was intact before making the switch. I also had a bootable usb stick handy just in case. 

I think the document should be reviewed.

Many Thanks to you all.

---

### Post by robert48 on 2021-07-01
Now back up and running. Had a problem with hairy hippo startup USB stick (failed as grub was being loaded) so installed 20.04 instead. Now all stable...with all my Home stuff! Is there any way I could modify the document to tweak the last 3 steps?

---

### Post by oldfred on 2021-07-01
Because of some issues in the past, they have greatly restricted who can edit.
You have to be registered on Launchpad and then ask permission.
[https://help.ubuntu.com/community/WikiGuide](https://help.ubuntu.com/community/WikiGuide)

---

