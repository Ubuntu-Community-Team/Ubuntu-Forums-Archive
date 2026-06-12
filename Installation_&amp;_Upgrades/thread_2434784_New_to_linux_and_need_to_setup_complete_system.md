---
title: "New to linux and need to setup complete system"
date: 2020-01-10
forum: Installation &amp; Upgrades
---

### Post by jabersold on 2020-01-10
[LEFT][COLOR=#000000][FONT=Ubuntubeta]Good afternoon I need assistance in trying to achieve setting up a dedicated media server using Linux. I would like to do that is by loading ubuntu (have usb iso)  I want to install the operating system on a 256 gig as SSD  along with 2 2TB hard drives for storage.  This will be a fresh load everything from scratch  Please assist with the directions on what needs to be accomplished.[/FONT][/COLOR][/LEFT]

---

### Post by GhX6GZMB on 2020-01-10
Just boot from the USB .iso and follow the instructions. Nothing magic about it :)

---

### Post by oldfred on 2020-01-10
If new system it will be UEFI, not 35 year old BIOS/MBR.
Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Do you want to see both 2TB drives as one (bit more advanced as you use LVM which is volumes,not partitions, and then if one fails lose all data, or as two drives and you manage what you store on each? Or is one for data and other for backup of data?
Full install of SSD will only need 25 to 30GB for / (root) if all your data is on the 2TB drives. You also can then have /home with other than media on SSD.

Also links to more info
[http://gparted.org/documentation.php](http://gparted.org/documentation.php)
[https://gparted.org/news.php](https://gparted.org/news.php)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by TheFu on 2020-01-10
> **jabersold said:**
> Good afternoon I need assistance in trying to achieve setting up a dedicated media server using Linux. I would like to do that is by loading ubuntu (have usb iso)  I want to install the operating system on a 256 gig as SSD  along with 2 2TB hard drives for storage.  This will be a fresh load everything from scratch  Please assist with the directions on what needs to be accomplished.

Which media center software did you plan to use? There are a bunch of different options.
What type of media?
Will there be any clients to this server?
Will you have any TV tuners connected?
Do you have a solution for backups? It would be a shame to fill 4TB of data, then lose it.

In general, the OS and applications will use less than 25G.  For that reason, I'd not have the 2TB disks connected when doing the installation. Best not to confuse yourself.  Linux uses storage identifiers that would be unfamiliar to someone with a different background.

Depending on the specific media center software and settings you select, some additional storage might be desirable just for the database it will use. I wouldn't keep a DB on the SSD.

The main clients have NFS access to the server storage for photos, music, audiobooks, and video media.  My nextcloud server also gets read-only access via NFS to the same stuff.  I run the nextcloud server on a virtual machine on the media center server.

Popular media center software includes:
* Kodi
* Plex Server
* miniDLNA
* OpenELEC
* MythTV
Those are off the top of my head.  I use Kodi on most clients and Plex on my server, though I also use VLC and BubbleUPnP on clients.  Picking the server that meets your needs is a key choice.  If all the clients cannot play the files directly, then you'll want a media server that can transcode as needed for the different clients.  Most servers don't do this. 

As for install stuff, others can cover that better than I can.  I've posted storage layouts in these forums before as have others.  Lots of research to be done, you have.

---

### Post by CelticWarrior on 2020-01-10
I used to use Kodi only but then found [Emby]("https://emby.media/"). 
Much nicer because it can run in the background using very few resources. The only caveat is that for some reason it doesn't play ball with storage mounted in /media, but changing it to /mnt and everything is fine.

---

### Post by jabersold on 2020-01-10
Thank you for the follow up.  I was going to use Plex server on this for the complete range from music, streaming, live tv, dvr all media to be viewed by all devices in our home i.e. three tv's, two laptops etc...

---

### Post by jabersold on 2020-01-10
Have used kodi for sometime but concerned about the longevity of it.  Going to blend with Plex

---

### Post by TheFu on 2020-01-10
> **jabersold said:**
> Have used kodi for sometime but concerned about the longevity of it.  Going to blend with Plex

If you do that, you'll want to add 100G partition from the HDD mounted to /var/lib/plexmediaserver/  Keep this storage separate from the / partition. You'll thank me later.  If you allow it, plex will eat this storage up quickly. There are some settings to control that.  You'll want to read the plex guides.

 If possible, I'd use LVM so you can expand the storage as needed later.  On each 2TB disk, setup a single PV, a single VG and LVs based on the size you need for the next quarter.  DO NOT ALLOCATE ALL THE STORAGE TO THE LVs!  LVM makes adding storage where it is needed trivial, 4 sec of some, but reducing LVs is difficult.  Also, you will probably want to leave some unallocated storage to be used by snapshots.

I don't use plex for TV watching or streaming from outside the network.  Also, I don't use any plex clients or have a plex login account.  For accessing media over the internet, I'll use a self-hosted VPN to get on my plex LAN, then use the webGUI to stream.  No plex account necessary and best of all, no need for any ugly plex client apps. Of course, what is ugly is in the eye of the viewer.  Any video player that covers subtitles during pause fails as far as I'm concerned.  Plus, plex hides technical data about the media that I sometimes want to know.

You should look through these forums about setting up plex storage.

---

