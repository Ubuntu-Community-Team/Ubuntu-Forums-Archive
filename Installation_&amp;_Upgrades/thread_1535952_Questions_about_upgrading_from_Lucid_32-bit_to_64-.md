---
title: "Questions about upgrading from Lucid 32-bit to 64-bit"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by cscj01 on 2010-07-21
I am going to upgrade from Lucid 32-bit to Lucid 64-bit, and I have some questions as to what I need to do.  My system is a dual boot of XP and Lucid, but I only use XP rarely nowadays.  I know I have to do a clean install, so here goes.

[LIST=1]
[*]Do I have to blow away my current install of Lucid?
[*]If the answer to (1) is yes, what about Grub?
[*]How do I get a list of my currently installed applications?
[*]Currently Lucid is on one partition.  I have a Clonezilla copy of the file system.  Can I restore the /home directory from that copy once I have installed the 64-bit system?
[*]If I decide to make /home a separate partition, are there any good rules of thumb about how much space to allocate to the various partitions?
[*]Are there any other directories or files I should consider copying from the Clonezilla copy?
[*]Have I forgotten anything important?
[/LIST]

---

### Post by lechien73 on 2010-07-21
You're right that you will have to re-install. Since 32-bit to 64-bit is an architecture switch, there's no direct upgrade path.

With that in mind, I would suggest that you first move /home to a new partition. I'm sure there's plenty of tutorials around on how to do that, but I wrote my own last week: [http://uri.tl/e](http://uri.tl/e)

To get a list of your installed packages, from your new home directory type:

```
sudo apt-get install dselect
sudo dpkg --get-selections > installed-packages
```

This will generate a text file with your list of currently installed packages.

Then backup all your data before installing Lucid 64-bit.

When prompted during the install, format the current 32-bit partition for the install. Mark the newly created /home partition as the mount point for /home, but DO NOT FORMAT!

After the installation, check that your documents and general settings are ok. To reinstall your installed applications from the text file we created earlier, type:

```
sudo dpkg --set-selections < installed-packages
sudo dselect
```

This should re-install all of the previous packages - but with the right architecture.

It's not as difficult as you think - I did essentially the same thing after Lucid was released, but I upgraded Karmic 32-bit to Lucid 64.

Hope this helps - just remember to make backups (so I'm not responsible if anything goes wrong :P) and it should go quite smoothly.

---

### Post by oldfred on 2010-07-21
If you have a separate /home your system install only needs 20-25GB. You can even have less if hard drive space is a problem. I have lots of apps installed and have used about 6GB. But if you want to write a DVD you may need 4+GB in /tmp to create DVD. 

Swap should be 2GB or if you want to hibernate the same as RAM. The old rule of 2X RAM was when you only have 256MB of RAM.

Have you made any custom configurations in /etc? If so you might want to back them up. 

I made the switch from 32 to 64 with Karmic but also created a separate /home and then a separate /data as I also bought a new drive and had lots of room. I kept both partitions just in case I missed something and only had one or two things I did go back to find but could have recreated in just about the same time.

---

### Post by cscj01 on 2010-07-22
To oldfred and lechien73:  Thanks for the help.

Here is where I am.  I have installed 64-bit Ubuntu.  I have copied my /home/me backup to my new /home/me.  I have run the following:

```
sudo dpkg --set-selections < installed-packages
sudo dselect
```

Now I have a few more questions.

[LIST=1]
[*]I have a home network.  I had set this up under the 32-bit version.  Can I get a config file from somewhere (I have a backup of the old file system) to get this going again?
[*]I was using print sharing before.  Can I get a config file for that from my backup?
[*]I had customized my Main Menu, Startup Programs, and Panels.  Can I recover these customizations from my backup? startup programs
[/LIST]

Everything seems to be functioning properly at this time.  I'll test the rest of my system as soon as I know whether I have to re-customize or not.:D

---

### Post by cscj01 on 2010-07-23
> I had customized my Main Menu, Startup Programs, and Panels. Can I recover these customizations from my backup? startup programs

This was taken care of with a reboot after all the copying of /home.

In addition to items 1 & 2 above, I have a problem connecting to my MySQL databases.  Can I recover this from the backup?

---

### Post by oldfred on 2010-07-23
I do not know exact files. I had some network settings in /etc/network/interfaces. 

All your custom settings are someplace in /etc. I tried to keep track of any that I manually edited and copied them into a folder in /home so my normal backup of /home included those settings without having to backup all of /etc.

---

### Post by lechien73 on 2010-07-23
Your printer settings would probably be stored in the old /etc/cups folder.

It depends how customised your home network was - you could probably try comparing the /etc/networks files for a start.

How are you connecting to MySql? Is MySql running on your new 10.04 installation, or are the databases remote?

---

### Post by cscj01 on 2010-07-23
> How are you connecting to MySql? Is MySql running on your new 10.04 installation, or are the databases remote?

The databases are local.  However, things have gone beserk in a hurry.  While trying to get MySQL straightened out, it hung on me.  Since that time, I cannot connect in any way.  If I issue a ```
sudo stop mysql
or
sudo start mysql
``` it hangs.  I finally tried uninstalling and reinstaliing, but to no avail.  I tried using Synaptic and apt-get --purge.  Neither takes care of the proble.  I am constantly receiving the following message:
```
Lost connection to MySQL server at 'reading initial communication packet', system error: 111
```

I have searched the Internet for a solution to this, but I cannot find one.  At times I get resource locks I cannot clear.

I need some help big time on this one.

---

### Post by cscj01 on 2010-07-23
Well, I finally got MySQL started using ```
start mysqld
```

I am not sure whether all is repaired or not, but it is running correctly at the moment.  I have no idea if it is clean now nor why it suddenly started.  I hope someone can tell me how to check the installation for any problems.  Thanks for your help to this point.  Now I'll tackle the printer sharing.

---

