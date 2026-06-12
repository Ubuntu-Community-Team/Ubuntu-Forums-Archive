---
title: "Ubuntu dual boot Windows Vista Question"
date: 2010-11-20
forum: Installation &amp; Upgrades
---

### Post by hyperAura on 2010-11-20
Hi there, I have a laptop which has two hard drives. First hard drive is used for installing OS's and second hard drive is used to store data.

In the past I bought this laptop with windows vista. Later on I installed ubuntu (8.04 I think) and I installed Windows 7 which caused only vista and 7 to show up in boot loader. After that I reinstalled Ubuntu (9.04 I think) and I lost both entries from boot loader of windows vista and 7 but not their partitions. Since I had the factory recovery discs of windows vista I decided to reinstall vista on the vista partition and now I want to reinstall Ubuntu but I want to know how not to mess up the boot loader this time.

Details of my hard drives are:

Hard drive 1:
Partition 1: Windows Vista 80gb
Partition 2: Windows Seven 100gb
Partition 3: Ubuntu 50gb
Partition 4: Windows Vista Recovery Partition 10gb

Hard drive 2:
Data (250gb)

I always do manual installation of ubuntu when it says to choose where to install thus I get the option to choose where the boot loader is going to be installed. That's always the point where I mess up with the installation.

Thanks

---

### Post by cchhrriiss121212 on 2010-11-20
The boot loader is always installed by default to the primary hard drive, so you should have no problem. If GRUB does not show you the correct options just do this from within Ubuntu:
sudo update-grub

---

### Post by hyperAura on 2010-11-20
i tried installing ubuntu through wubi but i get a problem towards the very end of the installation "permission denied about a log file in a windows folder" and it stops.. dont know if anyone else has faced this problem recently..

---

### Post by hyperAura on 2010-11-20
also i was wondering why is wubi downloading the 64 bit version of ubuntu 10.10 instead of the 32 bit for my laptop? i checked but there is no selection for choosing to install the 32 bit version..

---

### Post by garvinrick4 on 2010-11-20
Go into boot off of Ubuntu install CD and choose Try Ubuntu: that is called a Live CD:
Now open a terminal: Applications to Accessories to terminal: copy and paste:
```
sudo fdisk -l
```
(lower case L)
This will show your partition table:
I believe we should make the one you are going to make an extended partition and
put your Ubuntu install using manual install in a logical partition inside of extended.
Incase you want to make it larger in future or add anything at later date. Since you have
4 primary partitions now and that is all you get lets do this right: Post your output of code earlier to this thread and what version of ubuntu are you going to install and how much RAM  you have installed in your machine.

---

### Post by hyperAura on 2010-11-20
well first of all i have 2gigs of ram.. i think its better if i download the 32 bit version of 10.10 right?

---

### Post by garvinrick4 on 2010-11-20
If you are installing WUBI from server and not from a CD then it looks at your machine and decides if it is 64 bit capable and uses it. You can have 32 bit Vista and 64 bit WUBI. Wubi is just a folder in C drive in windows called Ubuntu right next to Users. If you feel more comfortable with WUBI use it, I think most all users would say lets use the 50 gigs you set aside for Ubuntu in drive. Do what is comfortable to you.

---

### Post by garvinrick4 on 2010-11-20
Yes if we want to do the install in the partition the right way lets use 32 bit for your first install. Good choice install in partition. Go into Windows also and make sure there is no WUBI install in C: Drive called Ubuntu next to Users, open and uninstall so that is gone.

---

### Post by hyperAura on 2010-11-20
Since WUBI does not work for my machine I am currently downloading the 32 bit.. I will burn it and go try ubuntu, then run the command and post the results..

---

### Post by kansasnoob on 2010-11-20
If you're installing 10.10 you might find some of what I posted here useful:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

If that leaves you with questions I'd like to know :)

---

### Post by garvinrick4 on 2010-11-20
> **hyperAura said:**
> Since WUBI does not work for my machine I am currently downloading the 32 bit.. I will burn it and go try ubuntu, then run the command and post the results..
Ok, I will be here when you are done, you are my afternoon project lets make this a nice clean install.

---

### Post by hyperAura on 2010-11-20
On the last screenshot "Device for bootloader installation"  I can't find any explanations as where about should the boot loader be installed.. I do not have any problems with the rest of the process, apart from this last step.. Thanks

---

### Post by hyperAura on 2010-11-20
Hey [garvinrick4]("http://ubuntuforums.org/member.php?u=899097") thanks for willing to help me but you should take a long break as the results will be a little late.. I am currently downloading the iso file and there is still 1 hour and 20 minutes to download.. I don't know why is so slow, guessing is either my connection or that it might be downloaded from a server in outer space.. Average download speed is 120 kb/s.. :(

---

### Post by garvinrick4 on 2010-11-20
##Kansasnoob has written an install thread that is nice;
I was going to suggest you make the 50 gig partition an extended partition.
Inside of that partition:
10 gig logical partition for / (your file sytem) in ext4
30 gig logical partition for /home in ext4 (all your personals)
10 gig logical partition would be ntfs for data (so gives a letter in windows like G: and a sda# in
                                                         linux. So both linux and windows can use that partition for data)

#No real need for swap you have 2 gigs of RAM
when asks about Ram just ignore and go to next.

#Your boot will go into sda not sda1 or sda3 but sda that will put it into your mbr (master boot record) and you can then boot all 3 of your installs from grub2. Make sure you put
in sda

#Seperate /home so if need to reinstall need to just install / and not mess with /home
  or if more linux installs can share /home

#If you need any personal help making these partitions in gparted or installing just ask.( I will look in on this thread to see how you are progressing)

---

### Post by hyperAura on 2010-11-20
hey I have now booted into Ubuntu live through a CD and I am trying to understand how to create the partitions you have told me..

I have attached two images, one from the gparted and one from the output of running the command sudo fdisk -l

Thanks

---

### Post by garvinrick4 on 2010-11-20
Your whole Ubuntu labeled partition is in a extended already so
sda6 is the logical partition for ubuntu so.
In gparted: (nothing is to be mounted)
#right click on sda6 and make a new partition as logical and ext4 of 10 gig
and hit green apply arrow.
#right click on 40 gig left over and make a 30 gig partition as ext4 hit green apply arrow
#right click on left over of about 10 gig and format ntfs (is ntfs but do it again) green apply arrow, right click on again and Label data(green arrow)
#Now write down the sda#'s assigned to / to /home and to ntfs. (10 to /, 30 to /home and 10 to ntfs data.) ( data is done now.)
#Go to your install and choose manual and use these partitions for what they were made for. (screen shots in kansasnoobs thread) just 2 to use. 10 gig / and 30 gig /home both ext4
## grub go's in sda
## Do not need to make an Extended partition already have one to house the logical partitions (I have never used one first in line, seems to work)
## I notice you have a external named data so change one of them to what ever you want in Label.

---

### Post by hyperAura on 2010-11-20
where it says device for boot loader installation should I leave it as it is? Sorry for asking so many times but I just want to be sure. Thanks

---

### Post by oldfred on 2010-11-20
The sda is the drive and that is where you want grub2's boot loader.

---

### Post by hyperAura on 2010-11-20
yeah but if I leave it as it is wouldn't it overwrite the MBR?

---

### Post by garvinrick4 on 2010-11-20
You want to install grub2 in sda and it will overwrite the windows boot manager
so you can boot all 3 installs so sda is right.

---

### Post by hyperAura on 2010-11-20
Thanks! I will now proceed with the installation..

---

### Post by garvinrick4 on 2010-11-20
When installation is complete boot into Ubuntu install and open a terminal and:
```
sudo update-grub
```
will update your grub menu and config and show all installs.

---

### Post by hyperAura on 2010-11-20
I never got stuck in an installation before but today I guess is just not my lucky day..

As you can see in the attachment, I cannot forward to complete the installation.

If I go back I get to select keyboard layout and timezone but there is not exit button.

Is there any way to cancel the installation in order to do it without booting into Ubuntu?

---

### Post by garvinrick4 on 2010-11-20
You have not started the installation yet, you have just did the set up.
You cannot go back and then quit? Whatever it takes to quit and restart 
the procedure: 
Did you tell it to get time from network server maybe and it is frozen there looking.

---

### Post by hyperAura on 2010-11-20
No there is no cancel button at any point in the process.. I can go back twice but still no cancel exists or anything..

Is it possible that Ubuntu people did not think about cancelling the installation?

Also I cannot restart or shut down the machine. I think I will make a forced shutdown through the power button.

---

### Post by garvinrick4 on 2010-11-20
How ya doin hyperAura?

---

### Post by hyperAura on 2010-11-21
Hey [garvinrick4]("http://ubuntuforums.org/member.php?u=899097"), yesterday I forced the machine to shut down and I left as it was really late here where I come from. I will re-attempt the installation today from the CD without booting into Ubuntu though.

---

### Post by hyperAura on 2010-11-21
Thanks guys for helping me, this time I have managed to install the system without messing up!! :)

---

### Post by garvinrick4 on 2010-11-21
Hey, congrats that is good news to start my day with. You were running off of install cd not HDD and had not 
started installation so shutting down could not hurt. I am happy you kept at it and got a working system 
with your triple boot and did not give up, you learned something and some when faced with adversity just give up. 
For users installing with new installation process in 10.10 (obiquity) here is kansasnoobs link
that helped OP.

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

---

