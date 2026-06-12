---
title: "Partitions in Ubuntu server"
date: 2014-02-25
forum: Installation &amp; Upgrades
---

### Post by Eloi_Boronat on 2014-02-25
Hello.

I am trying to install a dedicated server to LAMP and SAMBA. So, I am installing ubuntu server but I need to define de partitions. Which partitions you recommend to build in order to not lost information in a future actualization process of my SO. 

I have found a lot of information by internet about this topic but in each web recommends different partitions.

Thank you in advance.

---

### Post by Kirboosy on 2014-02-25
Welcome to the forums! :D

How many hard drives will you have in your computer? I would recommend using [LVM]("https://wiki.ubuntu.com/Lvm") because that will enable you to change your storage needs in the future. 

If you want to keep it as basic as possible you can just tell Ubuntu to "Use entire disk" This would make everything install on one partition. The most basic but the easiest. (Note, this will delete everything off the hard drive)

If you wanted to get a bit more fancy you could have a multi partition setup. Have your OS install on one partition and your /home/ on another.

Lastly the best option would be LVM although LVM can seem a bit overwhelming at first. 

There are lots of things you can do based on how involved you want to get.
Hope that helps!
~Caboose

---

### Post by Eloi_Boronat on 2014-02-25
> **Caboose885 said:**
> Welcome to the forums! :D

How many hard drives will you have in your computer? I would recommend using [LVM]("https://wiki.ubuntu.com/Lvm") because that will enable you to change your storage needs in the future. 

If you want to keep it as basic as possible you can just tell Ubuntu to "Use entire disk" This would make everything install on one partition. The most basic but the easiest. (Note, this will delete everything off the hard drive)

If you wanted to get a bit more fancy you could have a multi partition setup. Have your OS install on one partition and your /home/ on another.

Lastly the best option would be LVM although LVM can seem a bit overwhelming at first. 

There are lots of things you can do based on how involved you want to get.
Hope that helps!
~Caboose

First of all, thank you for your answer.
 
I have 2 HD of 3TB. The objective is build all the server in the first HD and use the second HD like a mirror (Raid 1).

I have used this partitions but I am open to improve using your suggestions:

Hard disc 1 (sda):

300 MB to be used as /boot
2700 GB to be configured by LVM

Hard disc 2 (sdb):

300 MB to be used as /boot
2700 GB to be configured by LVM

And using this partitions to define two raids1:

Raid Nº1 - Raid 1 between the 300MB partitions
Raid Nº2 – Raid 1 between the 2700 GB partitions

Finally, using the VLM configurator, I have defined:

10GB using ext4 by /
1TB using ext4 by /home
1TB using ext4 by /var
2GB to swap
The free memory will be distributed in the future by VLM.

It is my initial plan. Any suggestion? The LAMP server, theoretically use the partition /var. It is correct?  The files to be shared by SAMBA will use the partition /home, is it correct, to?

---

### Post by Kirboosy on 2014-02-25
You could setup a software RAID at the time of install or have a script/utility that runs backups to the secondary drive. RAID can sometimes be very finicky to get working. I've personally had a nightmare getting my RAID 10 working right. I have lots of weird errors going on with it. Its been pushed to the backburner to get working.

Apache by default houses its pages in /var. Samba can be configured however you see fit. Let me show you my smb.conf. I have a super simple unsecured Samba setup in my house. I have the mentality if you are on my network I let you on there. (Also its just me in the house 90% on the time so I don't go overboard with security inside the house. Getting onto my network is locked down though :) )

```
[House Files]        
        comment = Media Files
        browseable = true
        path = /Data
        guest ok = true
        read only = false
```


/Data on my server is where I store most of my data. I have two webpages that sit in /var/www/ but that doesn't take up much space at all. You can even change the apache config to use another directory besides /var/www. You could make /opt/ huge and store everything in there if you wanted. The choices are endless and at the end of the day it comes down to what works best for you in your situation. Personally. I think 1TB is way too big for /var but I don't know everything about your situation. I would probably go with something more like this.

50Gb /
4 GB SWAP (Depends on your RAM amount. Double whatever RAM you have in the system is the old rule of thumb)
50Gb /home
Rest /opt (or whatever you want to call the data folder)


Hope that helps!
~Caboose

---

### Post by Eloi_Boronat on 2014-02-25
Thank you. I will analyse your configuration suggested. Nevertheless, you have told me yiu have to web pages in /var. How to avoid to erase this data if you change your ubuntu version? Because, if you don't define a particular partition, the /var is inside of / partition, no? And all of this data will be erased if you change the ubuntu server, no?

---

### Post by Kirboosy on 2014-02-25
Right if you don't define a directory it will be included under /. I would have to manually backup the directory if I had to re install. I could move it over to /Data on my drive but I just never have. I guess when I finally get my new server running I will make sure to set it up much better :)

I would also recommend you go with a LTS instead of a regular rolling release. 12.04 and the upcoming 14.04 are LTS. I have run 12.04 on my server no problem since 12.04 was new. This will prevent you from having to upgrade every six months. (Unless of course you like upgrading all the time)

~Caboose

---

### Post by Eloi_Boronat on 2014-02-25
Thank you for your advice about the LTS. I am waiting for the next 14.04 LTS version. 

Now, a recommend for any person who are trying to configure this raid1 over disks of 3TB or more:

1- Create the partitions using Gparted because Ubuntu installation is not able to make the partition bootable. In my case I have defined in both HD:

sda1 -- 2MB -- Flaged: bios_grub
sda2 -- 300MB -- Flaged: raid
sda3 -- 2,73TB -- Flaged: raid

After that, following with the standard Ubuntu installation.

Source: Comment of Almeister9 in this forum: [http://askubuntu.com/questions/215703/installing-12-04-server-as-a-software-raid-1-mirror-fails-to-boot](http://askubuntu.com/questions/215703/installing-12-04-server-as-a-software-raid-1-mirror-fails-to-boot)

---

