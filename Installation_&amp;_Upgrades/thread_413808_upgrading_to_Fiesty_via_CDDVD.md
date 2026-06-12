---
title: "upgrading to Fiesty via CD/DVD"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by krypto_wizard on 2007-04-19
I have read some stories of Ubuntu not being installed properly on many boxes and even breaking many.

I have downloaded the CD and I want to upgrade via CD.

Can someone please help me ? What are the steps ?

Thanks

---

### Post by spd106 on 2007-04-19
Try this [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by krypto_wizard on 2007-04-19
Has anybody upgraded using CD so far and any success ?

> **spd106 said:**
> Try this [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by marioleon on 2007-04-19
I downloaded the alternate CD and try to upgrade, but when it's goes into "modifying software channels", it throws an error, that says that it's impossible to calculate the installation.

Anybody who can help me with this????

---

### Post by Patrick K on 2007-04-19
Same thing here. Could not calculate the upgrade.

---

### Post by Forceflow on 2007-04-19
I just updated from the cd, worked perfectly. (so far )

---

### Post by Big_J on 2007-04-19
I downloaded the alternate cd and there is no upgrade option?
There's only install options, and there are only text modes on the cd. 

How do I upgrade??

---

### Post by OsakaWilson on 2007-04-19
> **Big_J said:**
> I downloaded the alternate cd and there is no upgrade option?
There's only install options, and there are only text modes on the cd. 

How do I upgrade??

I heard that you could upgrade from the alternate CD and tried that too, but I couldn't figure out how to do it either.

---

### Post by Patrick K on 2007-04-19
You have to run "cdromupgrade" from inside Edgy (it's on the cd). That is, pop the cd in while Edgy is running. If it doesn't start automatically, double click on the file.

---

### Post by netsurfau on 2007-04-19
Went to the link above: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
Followed link to upgrade notes, then clicked on 6.10 - 7.04 and was sent straight
back to the "upgrading" page.

---

### Post by awells527 on 2007-04-19
I downloaded the upgrade CD because people were complaining of the download speeds being slow for the people doing it the apt-get way.

Well, the installer pulled the first 1000 packages from the alternate CD and now it's pulling the remaining 400 from the Internet when I told it to pull the upgrade from the CD only.  Now it's downloading at a blazing (not really) 23kb/s.  It says 8 hours remaining at this point, so I guess I'm just going to let it run overnight.

Just because it didn't work for me doesn't mean it doesn't work though.  This is my first time upgrading.

---

### Post by netsurfau on 2007-04-19
Patrick K - What's the path to "cdromupgrade"?
Haven't been able to locate it.

---

### Post by lagartoflojo on 2007-04-19
netsurfau, I think you may have downloaded the "Desktop" CD... To upgrade via CD you must download the "Alternate" CD.


From the "upgrading" page:
> Upgrading using the alternate CD/DVD

Use this method if the system being upgraded is not connected to the Internet.

   1. Download and burn the alternate installation CD
   2.Insert it into your CD-ROM drive ***(WITH EDGY RUNNING)***
   3.A dialog will be displayed offering you the opportunity to upgrade using that CD
   4.Follow the on-screen instructions

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:

```
gksu "sh /cdrom/cdromupgrade" 
```

Note that for Kubuntu the upgrade dialogue will not be displayed and you will need to install gksu before running the above command (it will not work with kdesu). 

I was also getting the calculate errors, but only when I told it not to get the updates from the Internet... have you tried saying "Yes" when it asks?
(I'm in the process of upgrading via CD right now... hope it works!)

---

### Post by maluze on 2007-04-19
I am currently running Edgy. I tried to upgrade first by using Update manager, but it would never open. I then tried to update using command line, but it failed to fetch many pf the packages and didnt work...so by mistake i downloaded the desktop version, and i can't find anywhere if i can use the desktop version to upgrade (not clean install) to 7.04. I did an MD5sum on the desktop.iso that Idownloaded, and it is different than the number posted on distrowatch (apparently its not up at the Ubuntu site..yet)..this is what CLI returned after performing the MD5sum: a1ee4a23edf13712ab1bc49b66233300  ubuntu-7.04-desktop-i386.iso

my question is, i only have one blank CD, and I want be positive that I can use my desktop file to upgrade to 7.04, keeping my music intact. If it doesnt work..i just wasted 2 something hours downloading this and will dl the alternate version when i have the time =/ but i really do not want to do that :confused:

---

### Post by jgcamp99 on 2007-04-20
I'm reading them too. 6.06 to 6.10 was a nightmare for me. I think I'll clean install it and do a simple data migration. Seems like too many changes for customizations and personal preferences to simply get a clean and easy upgrade. The problems one encounters, often require more effort to fix than a clean install and desired application load. It would be nice to pull it off just once though. I think the closer you are to having just a generic installation of the previous OS version, perhaps the more likely the upgrade is to be 100 % successful ? But in that case, a clean install would make more sense too. Personally though, I'm not sure when I'll do it if at all. 6.06 to 6.10 was simply more work and I didn't perceive any advantages from my normal usage, outside of the newer/newest versions of applications. 6.10 was only 4, close to 5 months after 6.06. This one feels too similar of an experience just from the live cdrom for me to justify scrapping 6.10 for a clean install of 7.04. 7.10 is around the corner and it's around my birthday, so I count it as a Linux birthday gift.

Part of what keeps me from migrating too, wireless for the notebook. That was a tough nut to crack. I'd expect it to be better/easier this time, but before I upgrade, I'll let other's tell me how cold the water is this time.

---

### Post by Patrick K on 2007-04-20
> **netsurfau said:**
> Patrick K - What's the path to "cdromupgrade"?
Haven't been able to locate it.

It's in the root directory of the alternate cdrom.

---

### Post by Patrick K on 2007-04-20
Well, I got past the cannot calculate error but about half way through the installation it aborted. I posted a bug report but doubt I'll hear anything before next week, or maybe the week after that. 
And now Edgy is pretty dodgey. 

I have another bug report that's been sitting there with no action for many days.

---

### Post by quinton.dupreez on 2007-04-20
is there a link t download the dvd installer for 7.04. cn anyone tell me wher i cn fnd the iso not a torrent

---

### Post by Big_J on 2007-04-20
> **Patrick K said:**
> You have to run "cdromupgrade" from inside Edgy (it's on the cd). That is, pop the cd in while Edgy is running. If it doesn't start automatically, double click on the file.

The only reason I decided to upgrade using a cd, is because a recent security update broke my edgy...
sh /cdrom/cdromupgrade
does not work. Says no such file or directory
yes, my cd drive is mounted on /cdrom.
I need to be able to upgrade from the command line. I really don't want do a fresh install, I have way too much data to back it up.

Edit: I accidently mounted cdrom0 onto /media/cdrom (I have too drives). Now the right one is mounted, but I get "Gtk-WARNING **: cannot open display:"
I need to do it from the command line, because I'm not able to log in in graphical mode

---

