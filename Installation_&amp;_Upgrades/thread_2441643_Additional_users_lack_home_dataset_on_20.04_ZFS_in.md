---
title: "Additional users lack home dataset on 20.04 ZFS installation"
date: 2020-04-25
forum: Installation &amp; Upgrades
---

### Post by Nick_NS on 2020-04-25
I have installed 20.04 using the ZFS install option. 

During setup a home directory dataset was created for my initial user as rpool/USERDATA/nicholas_mh6m3r. However when I add additional users to the system using the system settings gui it does not create a new dataset for the user's files. 

I've done some searching online and can't find an answer as to the proper way to add a user so a dataset is created along with the new user and that works with Ubuntu's zfs layout. Can anyone offer any advice on this?

---

### Post by dirtscout on 2020-04-25
This thread below should help out a bit. Short answer without learning to fish? 
sudo useradd -m -d /PATH/TO/FOLDER USERNAME



[https://askubuntu.com/questions/393463/create-the-home-directory-while-creating-a-user](https://askubuntu.com/questions/393463/create-the-home-directory-while-creating-a-user)

[https://www.tecmint.com/add-users-in-linux/](https://www.tecmint.com/add-users-in-linux/)

---

### Post by Nick_NS on 2020-04-25
Perhaps I was not clear enough with my initial post. 

The method you've shown/linked to achieves the same end as the settings gui currently. Yes it creates the folder "/home/USERNAME" but does not create a zfs dataset mounted to said folder. This is the default setup for the root user and initial user set up under the installation wizard. 

Using these methods results in:
[INDENT]Mountpoint <-> ZFS layout
/root <-> rpool/USERDATA/root_mh6m3r
/home/initialUser <-> rpool/USERDATA/initialUser_mh6m3r 
/home/additionalUser <-> rpool/ROOT/ubuntu_mh6m3r/home/additionalUser[/INDENT]

As you can see the additional user's home folder is created under the rpool/ROOT/ubuntu_mh6m3r dataset, which will cause problems if the system ever needs to be rolled back to a previous snapshot as changes to the user's home directory will be rolled back as well.

I can manually create/mount the appropriate dataset first. However, given that the system is set up using zfs out of the box and the initial users are set up under the USERDATA dataset automatically, one would expect the Add User function in the GUI at least to properly configure the new home folder.  I realize the useradd CLI tool will probably never have that kind of functionality due to it's scope, but I was hoping the GUI would have a way to automatically do all the dirty work, since that's what it's designed for.

---

