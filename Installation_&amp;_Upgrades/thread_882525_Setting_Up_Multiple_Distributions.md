---
title: "Setting Up Multiple Distributions"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by happynobita on 2008-08-07
Hello, I am a 2-day old Xubuntu user. A friend of mine, who is not the greatest with computers, has an old laptop with 256mb of RAM, 40gb hard drive, and about 15gb of media. Windows was running too slow for her, so I setup Xubuntu to see if things would speed up. 

They have a lot. However, it still feels slow to me, and I am considering installing Fluxubuntu, instead. 

My problem is the 15gb of media. She does not have an external hd. I have one, but it's configured for my mac, so it is not recognized. i originally sent the media to my mac, and then when xubuntu was installed, sent it back. I don't want to do that again, because it's not firewire and it took forever.

I read on a forum that one guy has a 40gb 'home' partition, and then several smaller partitions, each with different linux distribution on it. Once booted into either one of these partitions, he can access the 'home' partition. 

I understand grub is used to select at boot up, but I have no idea how to go about setting that up and separating the hard drive. Is it even possible to do this without losing my data, or should I back it up one more time? Does this make sense? Thanks for any help.

---

### Post by huxterby on 2008-08-07
Hi happynobita.

What you can do is use Gparted partition editor (either from a Live CD or install it), to shrink the Xubuntu partition. Then Create a new partition in the free space using either Ext3 format if only Linux access is needed, or Fat32 if you want the files accessible to a networked Windows machine (you should get at least 25 Gb from a 45 Gb partition with 15Gb of media)

Move the 15Gb media to the new empty partition. 

Now you can install Fluxbuntu in place of Xubuntu.

Huxterby

**Partitioning Guide**
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

**Mounting a Linux partition**
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Basically psychocats.net has the essential Ubuntu guides.

---

### Post by happynobita on 2008-08-07
Thanks for the fast reply. Will give this a try. 

A few more questions. Does partitioning to FAT32 have any drawbacks? She's not connected to a windows network.

Also, once this 'media' partition is set up, can I get Fluxubuntu a try without deleted the Xubuntu partition? It seems I can use gparted to create another 'fluxubuntu' partition and install it on that. If I do that, how would I go about booting up correctly?

---

### Post by comradekingu on 2008-08-07
I suspect you will run into the max filesize of 4GB.
Go with EXT3. Ntfs is better than FAT32 both in terms of compatibility and technology. I wont reccomend it, but its a better choice than FAT32

---

### Post by SkonesMickLoud on 2008-08-07
> **happynobita said:**
> Also, once this 'media' partition is set up, can I get Fluxubuntu a try without deleted the Xubuntu partition? It seems I can use gparted to create another 'fluxubuntu' partition and install it on that. If I do that, how would I go about booting up correctly?

You don't need a separate partition for that.  You can have multiple environments inside of one Ubuntu installation.

All you have to do is open up a terminal and type:

```
sudo aptitude update && sudo aptitude install fluxbox
```

Once it's gone with the install and config, log out.  In GDM (or KDM) there will be a "Session" button.  Click this and select "Fluxbox".  Then log in as normal.  It may ask you if you want to make Fluxbox your default, which is up to you.

If fluxbox is still too heavy, check out this site:

[http://xwinman.org/](http://xwinman.org/)

---

### Post by snowpine on 2008-08-07
> **SkonesMickLoud said:**
> You don't need a separate partition for that.  You can have multiple environments inside of one Ubuntu installation.

All you have to do is open up a terminal and type:

```
sudo aptitude update && sudo aptitude install fluxbox
```

Once it's gone with the install and config, log out.  In GDM (or KDM) there will be a "Session" button.  Click this and select "Fluxbox".  Then log in as normal.  It may ask you if you want to make Fluxbox your default, which is up to you.

If fluxbox is still too heavy, check out this site:

[http://xwinman.org/](http://xwinman.org/)

This is good advice, but a little bit misleading. Fluxbox and Fluxbuntu are not exactly the same thing, just like Xfce and Xubuntu are not the same thing. 

Fluxbuntu is a complete distro that uses the Fluxbox windows manager. It also includes an entire set of lightweight applications--web browser, word processor, music player, etc.--as well as attractive artwork, preconfigured menus, etc. It is ready to use (except for a couple of minor bugs you can fix in 5 minutes). There are two main downsides to Fluxbuntu: 1) it is no longer under development, so it is slightly outdated and doesn't have an active user community like Ubuntu; 2) you can't install Fluxbuntu on the same partition as an existing Xubuntu install, so you would need to either replace Xubuntu or create a new partition. You can read more of my thoughts about Fluxbuntu here: [http://ubuntuforums.org/showthread.php?t=855596](http://ubuntuforums.org/showthread.php?t=855596)

Fluxbox is a windows manager, nothing more or less. You can install fluxbox (using Skone's instructions), then choose between Xfce (Xubuntu's windows manager) or Fluxbox sessions each time you log in. The advantages of doing this is you keep your existing installation, and you have a choice--maybe you only know how to do a particular task in Xfce, so you pick that session today, then tomorrow you need speed, so you pick Fluxbox. The disadvantage is that it won't be set up for you like Fluxbuntu is; you will need to learn how to configure Fluxbox (which is mostly done by editing text files) if you want things like wallpaper, custom menus, desktop icons, auto-mounting of USB devices, etc.

I hope that helps clear things up. As for my personal decision, I am currently using the Fluxbox windows manager over a Crunchbang (a lesser-known Ubuntu "remix" using the Openbox windows manager) installation plus the Fluxbuntu artwork. The reasons I finally gave up Fluxbuntu were 1) no updates since 2007, and 2) I didn't like or need the lightweight applications--I don't have an ancient computer, so I'm happier with "full" applications like Firefox, Openoffice, etc. However, I used Fluxbuntu for many months to familiarize myself with what's possible using Fluxbox before I was comfortable setting it up for myself. Your mileage may vary. :)

---

### Post by shrinathk87 on 2008-08-09
I have a question about multilple linux distros on a single hard drive..like Ubuntu,Mandriva, OpenSUSE and Windows...

I found my topic in a READ-ONLY Archive..n so i cudnt ask questions..
its here "Partitioning For Multiple Linux Distributions"

[http://ubuntuforums.org/showthread.php?t=560625&page=2](http://ubuntuforums.org/showthread.php?t=560625&page=2)

.. I didnt want to mess up things by starting a new thread, so i am posting it here...

I have a 30 GB Hard drive,currently runnig Ubuntu and Windows.I want to install other Linux distros using UNETBOOTIN utility. My question is,

Can i create TWO primary partions, 5GB and 25GB and install windows on the 5, and then since i heard linux organizes everythings as FOLDERS, can i just use the one primary partion as a folder where i can install all the distros ? I mean, can that partition have a single / and /home etc. folders and have all the info about all the distros..? all the users of all the distros will be found in the /home drive..

If it is possible, then cant a ubuntu user see a mandriva user's files ?

If it is not possible..tell me how to share the same SWAP space as i have a problem with space ( only 30GB ! ) also, i heard a maximum of FOUR primary partitions are allowed..so i cant install more than 4 distros ? or a logical ( n not primary ) partition is enough for a distro installation.

Thanks in advance.

---

### Post by SkonesMickLoud on 2008-08-09
> **shrinathk87 said:**
> I have a question about multilple linux distros on a single hard drive..like Ubuntu,Mandriva, OpenSUSE and Windows...

I found my topic in a READ-ONLY Archive..n so i cudnt ask questions..
its here "Partitioning For Multiple Linux Distributions"

[http://ubuntuforums.org/showthread.php?t=560625&page=2](http://ubuntuforums.org/showthread.php?t=560625&page=2)

.. I didnt want to mess up things by starting a new thread, so i am posting it here...

I have a 30 GB Hard drive,currently runnig Ubuntu and Windows.I want to install other Linux distros using UNETBOOTIN utility. My question is,

Can i create TWO primary partions, 5GB and 25GB and install windows on the 5, and then since i heard linux organizes everythings as FOLDERS, can i just use the one primary partion as a folder where i can install all the distros ? I mean, can that partition have a single / and /home etc. folders and have all the info about all the distros..? all the users of all the distros will be found in the /home drive..

If it is possible, then cant a ubuntu user see a mandriva user's files ?

If it is not possible..tell me how to share the same SWAP space as i have a problem with space ( only 30GB ! ) also, i heard a maximum of FOUR primary partitions are allowed..so i cant install more than 4 distros ? or a logical ( n not primary ) partition is enough for a distro installation.

Thanks in advance.

If I understand your question, you want each distro to share / and /home on the same partition?  AFAIK that cannot be done.  Each flavor needs it's own partition.

You could however create 1 /home and 3 / partitions.  You're right about the 4 primary limit, however, only Windows needs a primary.  Linux can be installed to a Logical partition.

You'll probably run into space issues with what you're planning though.  Assuming you use 5GiB partitions, you'll use up fully half of your HDD with 3 / partitions.  Count on 10 GiB's for Windows, and you're left with a 5GiB /home, which is tiny.  This also doesn't provide any room for swap.  Which, by the way, you can use 1 swap for all of your flavors, just make sure to set the swap partition in the installer, which it'll probably do automatically.

---

### Post by happynobita on 2008-08-18
Thanks for all the tips! What I ended up doing was installing icebox, and I just select it at the login screen. So no need for separate partitions.

---

