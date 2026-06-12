---
title: "Move home folder when upgrading to lucid?"
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by 11010110 on 2010-06-09
Good evening everyone,

I am planning to move to Lucid from Karmic now that I am out of university for the summer and have time. I have heard that there is a way to copy your home folder over to the next release and all of the data and program settings will remain intact. I have tried some research on the subject but everything I have found has been extremely confusing. I want to do a fresh install (as my updater has been failing time and time again and asking for partial upgrades etc). Instead of creating a new partition for the home folder, would it be possible to move it to an external drive and copy it back over (I have tried to copy it to the external but I get some errors even in sudo)? If anyone could help me through this in simple steps it would be greatly appreciated!

Thanks in advance for the help everyone and sorry for the lengthy post.

---

### Post by oldfred on 2010-06-10
You have to be sure to preserve ownership and permissions. So when you copy, it has to be to a linux file system not NTFS and you need to use 

cp -a source destination

see man cp for more info on cp command. Also be sure to copy all the hidden files & folders.

---

### Post by 11010110 on 2010-06-16
thanks for the reply. I didnt use cp and that may have been my problem. Could I copy them to a FAT filesystem? Or does it have to be ext#?

---

### Post by grege on 2010-06-16
Fat32 will be the same issue, it cannot create symlinks or permissions.

It kind of depends on how much data we are talking. You could just reformat an 8gb thumb drive to ext3 if that is big enough. 

It also depends on what you want to preserve.

You can copy docs, music, photos and videos to fat32 or ntfs, then copy back without problems, as when you copy back the system will create ownership to you. Most program config files are in .folder hidden files. Apart from your browser and email folders I would not bother with the rest, you are better off using new configs for the new versions of the programs you are going to install.

What I do is install Midnight Commander from synaptic or sudo apt-get install mc  then run it in a term with the command mc - this gives you a neat two pane view of source and destination folders (use tab to switch sides) with all hidden files visible, making it easy to put things in the right places. Install Midnight Commander and have a play before you use it in anger to ensure you get how it works. You should not need sudo for anything in your home folder as it is your ownership, not the system. Plus you can systematically copy each folder to the ntfs drive and see if you get any errors. It may be the errors are not for anything you care about anyway. I tend to copy everything and only put back that which I value.

You just have to be doubly sure you have everything before you reformat.

Good Luck

---

### Post by oldfred on 2010-06-16
I used this to move /home:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
Without -a and copying as sudo root takes ownership
sudo cp -a

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

When I installed Karmic I did a clean install after updating for about 3 years and having issues with updates. Install worked so well I decided I wanted clean installs everytime, but have to save program lists and settings. I tried to do as much as possible from command line so I could copy history to a bash file and reuse it for next time. I also moved /home into a new 100GB partition (new drive so lots of room), but then moved all data to a /data partition. Home is now only 1GB and still in that 100GB waiting to be reorganized.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

---

