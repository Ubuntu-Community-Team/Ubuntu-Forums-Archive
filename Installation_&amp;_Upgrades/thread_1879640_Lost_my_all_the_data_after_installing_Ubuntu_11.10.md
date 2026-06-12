---
title: "Lost my all the data after installing Ubuntu 11.10"
date: 2011-11-12
forum: Installation &amp; Upgrades
---

### Post by rohyt on 2011-11-12
Hi everyone.I just installed ubuntu 11.10 in my laptop.While installing i selected an option "Replace Windows 7 with ubuntu " thinking it remove all the files of win 7 in c drive but it deleted all the files and all the partitions n i am now with a empty laptop with ubuntu 11.10..Readers please suggest me a way to recover the data.It contains all my research articles and my thesis.I havent even booted my laptop after that incident.plz help..

---

### Post by Rodney9 on 2011-11-12
This is terrible, no back ups I'm guessing. 

You did the right thing by not booting, that would overwrite even more, so leave it off for the time being.

You let Ubuntu format the drive, there are data recovery services and some software programs, however what I have heard there either super expensive or not very good.

Hopefully other users have heard of something magical.

I feel for you.

Rodney

---

### Post by Rodney9 on 2011-11-12
Here is a site reviewing data recovery software -

[http://data-recovery-software-review.toptenreviews.com/](http://data-recovery-software-review.toptenreviews.com/)

Rodney

---

### Post by mips on 2011-11-12
Do you have another HDD, external? Or access to a desktop PC?

First thing to do would be to image that drive to an image **file**, you can use GNU ddrescue from a livecd to do this. Be VERY CAREFUL not to mix your source / destination device around as you can kiss your data bye-bye thn.

Once you have an image file mount it from a livecd and have a look at testdisc/photorec.

You can also remove the HDD from your laptop and connect it to a PC that is also running linux, might be a bit easier than using a livecd.

DO NOT boot from that drive.
NEVER try and recover data by writing it back to the same drive.

Edit: For windows based software have a look at:
Ontrack EasyRecovery&#8482; Professional, R-Studio, File Scavenger, Recuva

Once again, do NOT install this software on the drive you want to recover from. Install it on a different PC, remove the HDD from your laptop and connect it to the PC with the software installed.

Where are you located?

---

### Post by blueturtl on 2011-11-12
Echoing what everyone else has already stated:

What ever action you take, be sure you **DO NOT write to the drive any more**. Not anything!

Every write lessens the likeliness that data can be recovered.

What you should do is either hook up the drive to another computer or run a LiveCD with which ever recovery tool you decide to use. This is because running a system from the hard drive will result in some files being written to the drive while it's in use (such as swap, temp files and logs).

There are tools that will bypass the file system and just read the disk raw -- using such a tool it is possible to recover files as long as they have not been overwritten.

---

### Post by jjex22 on 2011-11-12
rohyt, I do really feel for you, having been there myself. First things first, I can reassure you that not everything is gone, but at the same time I must warn you that some things will be. 

A saving grace is that window 7 is a much larger install than ubuntu and both os's will by default install from the beginning of the drive, so most of the overwritten data will be windows 7 system data.

As I said some will be gone - unfortunately away from csi, once data is overwritten it ceases to exist. So rack your brains - have you forgotten about any backups? windows 7 will nag you relentlessly about back-ups and creating a system image? Did you copy all your data across from and old pc, or new data on a thumb drive? you may have forgotten to erase those files? Did you have software like norton? it may have backed up some of your files to external or network drives, and some versions cme with online backups.

Once you've got through all this, the only thing left is to attempt recovery from the re-formatted drive. Once again don't do this from the drive - preferably connect the drive to another pc via a caddy, or by opening up a desktop and plugging it in to a sata connector, failing this you can make a live cd/usb USB stick of Partedmagic using something like this for USB:


[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)


when formatting the drive, use the slider to make sure you have a persistant file so that you can write data to the disk once booted. If you have just a 1GB disk look at puppy and dsl linux. If using this method, you will need an exteral drive to recover data to.

If posible connect to a desktop, as this will be significantly quicker than running from a live cd.

By this stage you should either be sitting at a desktop computer running it's OS and being able to see the connected laptop drive in my computer (windows) or media (linux), or be sitting at the laptop booted from a Patredmagic cd/usb stick, again looking at your drive in /media.... if not ask again how to get here.


Recovering - I recommend PhotoRec - included in partedmagic. If you're connected to a desktop, download PhotoRec for you system:
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

It's opensource and I've had some very good experience with it.

Using photorec - the settings you want to get the most data possible back are 'paranoid mode' and 'keep corrupted files' it will take a very long time be warned, and the output will seem a complete mess to sort back out, but the stuff it should recover should be worth it. 

I'll warn you now, going through the outputted files will drive you mad and take a long time - maybe a day r 2 to sort out everything, but it should be worth it, and finally try not to get fed up and adopt a habit of deleting files you don't want as you go through the lists - this can lead to you accidentally deleting something you do want!

Finally Good luck, Ihope it all goes well for you!

---

### Post by Mark Phelps on 2011-11-13
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions.

Since your data was on a Windows partition, my suggestions are the following (based on my experience at doing this successfully):
1) Find someone with a working Windows PC
2) Remove your drive from this PC.
3) On the Windows PC, download and install the trial version of GetDataBack for NTFS from Runtime Software.
4) Connect your old drive to this Windows PC.
5) Run GetDataBack in deepest discovery mode -- probably best to let it run overnight.
6) In the morning, check the recovery logs and see if GetDataBack was able to find your lost files.
7) If it was, you will have to purchase it to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, BTW, it is not HUNDREDS of dollars for this product. Last time I checked, GetDataBack for NTFS was $80, USD.

Your data ... your money ... your choice.

---

### Post by rohyt on 2011-11-20
finally got my data back......Thanks to you alll...

---

### Post by philinux on 2011-11-20
> **rohyt said:**
> finally got my data back......Thanks to you alll...

Would you mind sharing how you did this. Which software and method. It will help others.

Glad you managed it too. :D

---

### Post by rohyt on 2011-12-01
Ya Sure..i mailed to the runtime software company asking if theirs software "get my data back " works on ubuntu through wine.They said nt properly. So i reinstalled win XP removing all ubuntu and formatting the drive with NTFS mode .I selected win XP coz it takes less space and initial 18 gb was written by ubuntu was overwritten by XP which was of no loss for me..and installed the software and run format recovery..Guess What...Got all my data miracurasly back..thanks you all 
The lines here as a source of inspiration was "Windows filesystem is recoverd by windows software and linux by linux"

Thank u all...

---

### Post by 9412289864 on 2012-12-12
Hi Rohyt,
           Pointers needed for the free "Get my data back" software and the exact steps that you have followed to recover the data.

thanks,
Arpan

---

### Post by coffeecat on 2012-12-12
Old thread closed.

@9412289864, if you need help with data recovery I suggest you start your own thread. The OP has not logged in for a year.

---

