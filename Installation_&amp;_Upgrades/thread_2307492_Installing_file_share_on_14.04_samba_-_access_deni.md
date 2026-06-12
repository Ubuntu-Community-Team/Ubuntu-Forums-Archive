---
title: "Installing file share on 14.04 samba - access denied"
date: 2015-12-25
forum: Installation &amp; Upgrades
---

### Post by transporter_ii on 2015-12-25
A fresh install of SAMBA on Ubuntu 14.04 and it took me several days to actually get it to work. Here is a tip. From another Linux box, go to Nautilus (File Manager) and use File > Connect to Server > Windows share, and enter the IP address of the system the file share is on. If you can see the share but not connect to it, or from a Windows box you can not see the share at all or if you can, get Access Denied when you try to access it...is your share on a separate mounted hard drive on the system you are trying to install the share on? If so, this is your problem. To further test, make a share of something like a folder on your desktop (on the system you want the file share on). If it works, but a share to a mounted hard drive does not, here you go:

If it isn't installed, install the graphical samba manager:
sudo apt-get install system-config-samba

Use Unity Dash Home and search for the Samba manager:

[IMG]http://quest4.org/samba/samba001.png[/IMG]

Open it and create a share. It's a home network, so I wanted a straight share that anyone could write to and didn't require a login:

[IMG]http://quest4.org/samba/samba003.png[/IMG] [IMG]http://quest4.org/samba/samba004.png[/IMG]

Next, use Ubuntu's Disks tool. It should already be installed. Go to Unity Dash Home and type Disks in the search bar:

[IMG]http://quest4.org/samba/samba002.png[/IMG]

Using the Disk management tool, go to the hard drive/partition you want to share and click on the little gear box under the partition:

[IMG]http://quest4.org/samba/samba005.png[/IMG]

You need to set the mount options to the following:

[IMG]http://quest4.org/samba/samba006.png[/IMG]

This sets an NTFS partition as mountable by EVERYONE:

rw,auto,user,fmask=0111,dmask=0000

This sets an NTFS partition as mountable by a subset of users:

rw,user,auto,fmask=0177,dmask=0077,uid=1000

To find the documentation for other settings, search google using the terms: ubuntu disks mount options

After days of getting Access Denied and no joy of creating a file share, I had a 3TB NTFS formatted drive available on the network about two minutes after I set the above setting and rebooted my Ubuntu box.

As of now, I have the following setup working and tested: A Samba file share on Ubuntu 14.04. I have tested client access from Windows XP, Ubuntu 12.04, and Windows 7 and have been able to read and write from all of them.

-=-=-

For the record, and this is just kind of a rant. In the past, I have never had this much trouble getting basic things to work in Ubuntu. Every single thing I wanted this Ubuntu box to do, was broken right out of a fresh install. My needs were few. A FreeNX server and a massive file share. You know what, both of these were broken. I still haven't gotten FreeNX to work, though I have it running on several older versions of Ubuntu. Well, OK, it half works, but not with Gnome. AAAAAaaahhhhhhh.

But oh well, maybe the above will help someone.

Jay

---

### Post by Elishasmantle on 2016-01-01
Jay,

Thank You so much for sharing. It is the best thing and courteous thing we can do is to spare someone else the migraines headaches we go through trying to get something accomplished.
I've save this thread as a favourite and will use it as a guide.

Thank You,

Elishasmantle

---

### Post by Morbius1 on 2016-01-01
> This sets an NTFS partition as mountable by EVERYONE:

rw,auto,user,fmask=0111,dmask=0000
Actually it does not since the "user" option has no meaning with an NTFS partition. What it will do ( because of the dmask / fmask options ) is make it possible for any user to access it with read / write permissions. Being able to mount a partition and being able to access the mounted partition are two different things.
> This sets an NTFS partition as mountable by a subset of users:

rw,user,auto,fmask=0177,dmask=0077,uid=1000
Similarly, it's not a question of who can mount it it's a question of who and how it can be accessed. As defined by that line only root can mount the partition and once mounted it will be owned by whoever uid=1000 is and have permissions of 700 meaning only that user and root of course will have access.

Samba interaction with this directory is another matter. I can set Linux permissions to 777 allowing everyone and your Uncle to have access but set the samba share to allow only Scarlett access.

---

