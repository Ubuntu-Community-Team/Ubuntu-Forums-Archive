---
title: "Offline installation, help"
date: 2011-09-08
forum: Installation &amp; Upgrades
---

### Post by kooba on 2011-09-08
Just installed 11.04 via USB without a hitch - on a friend's computer.
He doesn't have internet but obviously needs updates.  
Is there a quick easy solution to getting the updates for him on my laptop (11.04) onto USB and then onto his computer?

Thanks.

I only came across this 
[https://help.ubuntu.com/11.04/ubuntu-classic/add-applications/C/offline.html](https://help.ubuntu.com/11.04/ubuntu-classic/add-applications/C/offline.html)

---

### Post by ~!geek!~ on 2011-09-08
> **kooba said:**
> Just installed 11.04 via USB without a hitch - on a friend's computer.
He doesn't have internet but obviously needs updates.  
Is there a quick easy solution to getting the updates for him on my laptop (11.04) onto USB and then onto his computer?

Thanks.

I only came across this 
[https://help.ubuntu.com/11.04/ubuntu-classic/add-applications/C/offline.html](https://help.ubuntu.com/11.04/ubuntu-classic/add-applications/C/offline.html)

 If you installed and updated your machine recently, you may try to look in the directory /var/cache/apt/archives!! This is the directory where deb files of updates and softwares are stored which are downloaded while updating or installing softwares in ubuntu!! You may copy the deb files to some storage device and paste them in the corresponding directory of your friend's machine!!  Now use this command to install them (all of them) using command line (terminal): >  cd /var/cache/apt/archives/   >  sudo dpkg -i *.deb  Enter sudo password!   Beware of the use of word `recently` in very first line of this post. I used it because if you have external ppas (or other sources) added to your machine and your friend doesn't, software installed using the above command will install those external softwares too! But since the ppas are not added to your friend's machine, they will not be updated. Same applies to the case when software sources are not identical for both the machines! You can check it using this: open update manager->click on settings->enter password->See if all the tabs have identical checkboxes ticked etc. (both should have identical contents in all tabs to work it correctly)  Also you may suggest this blogpost to your friend to manage his machine furthur with not so active internet connection:  [http://xperiencegnulinux.blogspot.com/2011/07/manage-ubuntu-without-active-internet.html](http://xperiencegnulinux.blogspot.com/2011/07/manage-ubuntu-without-active-internet.html)

---

### Post by ~!geek!~ on 2011-09-30
> **kooba]Hi geek..you helped me in this thread a few days ago.
ubuntuforums.org/showthread.php?t=1841017

Now I have all the files on my friends desktop in a folder labeled &quot said:**
> 
  Oops, I apologise for not replying to your message! I just didn't take a look at the inbox of mine!!  I hope somebody from forums already solved your problem! Anyways,let me put the way I would have solved it. My solution: So I assume you copied the deb files from /var/cache/apt/archives of updated machine to the machine which needs to be updated (lets say it machine2) in a directory called updates.  Now just to be safe, in case something goes wrong, I would like you to run these commands in terminal of machine2 to backup the original files n directories present there. The commands are: > sudo cp -r /var/cache/apt/archives ~/tempbackup  It will create a Directory named `tempbackup` in home folder of machine2. This backup can be used to put back original contents of the apt/archive directory, we r gonna play with!  After successfully copying the files using the above command, now proceed as follows: (I am assuming the updates directory you mentioned is on the Desktop) Run this in terminal: [QUOTE]sudo cp -r ~/Desktop/updates/ /var/cache/apt/archives  If this command prompts you for overwrite some files, answer it y or yes. After this command executes successfully, open the update manager, check for updates and ask it to install them for you, Since the files update manager needs to download are already there in apt/archives, it should not download them again. If it does, cancel it.  Now run the following command in terminal: > sudo dpkg -i /var/cache/apt/archives/*.deb  It should do it for you!!   At any moment if you feel something went wrong just copy back the backup I asked you to create and start over again! If solution does not work for you, put your query here. I will try to answer if I could!!

---

### Post by Lars Noodén on 2011-09-30
You can try using [apt-cacher](https://help.ubuntu.com/community/Apt-Cacher-Server) on the networked machine to store material for use offline later.

---

