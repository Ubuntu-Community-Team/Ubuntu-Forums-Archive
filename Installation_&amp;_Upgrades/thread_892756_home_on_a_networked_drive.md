---
title: "/home on a networked drive?"
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by Odyssey1942 on 2008-08-17
I now have two Ubuntu computers running on the same network and can see that file syncronization is going to become an issue, so I am thinking of moving my /home from the older of the two (new one hasn't been used yet other than beginning configuration) to a file server setup so that both linux computers can access the same files.

So I have these questions. I would like to use a Cavalry 1 TB ethernet connected RAID enclosure that I have just ordered to contain the /home directory. In principle, is there any conceptual problems with this? If none, does one just partition the Cavalry and format one partition for Ext3 to use for /home? The remainder of the Cavalry will be for Windoze files.

Once a suitable file server location is established, how does one transfer /home to the new location? (My current /home resides in its own partition.)

TIA

---

### Post by werries on 2008-08-17
I can't see a reason why this wouldn't work, but I dont know if its advisable. You could always rsync every once in awhile, but i dont see a point in always running it off the network. 

As for transfer, symbolic links could work, or rysnc. 
Seriously, look into rsync, its a brilliant tool.

---

### Post by cariboo on 2008-08-17
It would probably work, but both computers would have to be setup exactly the same otherwise you are going to run into problems with all the configuration files in your home directory. The configuration files are normally hidden in Nautilus. To see the hidden files and directories just hit Ctrl-h when you have Nautilus open.

I have 4 computers running different linux distributions, the computer I use everyday is where I store all my email and do most of my web browsing. I use foxmarks to sync bookamrks between the two Linux computers that run a gui as well as two other computers running XP and Vista. All downloads get transfered to a file sever at the end of the week so that the can be accessed from any of the computers on the network.

Even though my file server has a raid1 array I still have 2 eSata and one external usb drive for backups. You can never have to many up to date backups.

Jim

---

### Post by ilrudie on 2008-08-18
Proceed with caution:

If you can't see the file share for some reason your computers may hang when booting (hard mounted NFS).  Not sure what will happen if you soft mount /home and the network isn't there.  I have never tried booting or logging in without a valid /home partition.

Also you may have problems with config files in your home directory being locked or written while the other computer is trying to read them (or in a worst case write to them).  If you break an applications user config on 1 computer it will be broken on both.

My suggestion:  Keep /home local and have another mount point soft mounted where your shared files will live.  Soft link from your home folder to this mount point.  If you have a problem with your file share or network you can still boot you just lose access to the shared files.

---

### Post by Odyssey1942 on 2008-08-18
Thanks for the good counsel.

Thinking further about this, it is probably the right time to jump up a level or two and examine the objectives.

I use my computers for the following in roughly this order of frequency:
Browsing
Email
music listening (both internet streaming and mp3's on hdd)
document processing (formatted and text)
spreadsheets
forum activity for problem solving

I use a Windoze computer in addtion to the linux (now two linux), and my wife uses a windoze computer mainly and an Apple (banking and bill paying). Her computer use will be basically the same as mine except she sometimes watches TV on hers and does not use forums much.

I have extensive files and bookmarks going back several years, well classified and structured so that things are relatively easy to find. I would like to have all of this information in one place so that we can reach it from any computer (linux or windoze) in our lan. My first thought was to put it all on a NAS device, but assuming it can be impemented, it could be on any one of the computers and I'll just backup to the NAS.

Given this additional information, what do you recommend and why? ilrudie's suggestion sounds very persuasive.

Would this change if I threw remote access over the Internet into consideration?

TIA

---

### Post by Odyssey1942 on 2008-08-20
Anyone have any thoughts on this?

---

### Post by ilrudie on 2008-08-20
Would this change if I threw remote access over the Internet into consideration?\
[INDENT]YES.  Samba (which is what you will end up using if you want windows and mac and linux to read off a share) is not an acceptable solution for accessing this over the internet.  Look into sshfs if this is a must.  Otherwise you will need to make a VPN to access the samba share.  Do not share samba over the internet.
[/INDENT]My first thought was to put it all on a NAS device, but assuming it can be impemented, it could be on any one of the computers and I'll just backup to the NAS.
[INDENT]Either way would work.
[/INDENT]

---

### Post by Odyssey1942 on 2008-08-21
IL, very good to know. Thanks.

---

