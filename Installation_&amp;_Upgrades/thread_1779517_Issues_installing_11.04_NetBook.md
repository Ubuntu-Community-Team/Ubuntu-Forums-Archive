---
title: "Issues installing 11.04 NetBook"
date: 2011-06-10
forum: Installation &amp; Upgrades
---

### Post by loybanks on 2011-06-10
I downloaded the 11.4 .iso package. Installed onto USB without any problem with help of Universal USB Installer.

Then started the install from USB to New Toshiba Netbook NB505. Installing along side the Windows7 OS. It appeared that all was going well. Little did I know!!!

BUT...right at the end of the install it stopped with message "There is a problem with the configuration server". That alone bamboozles me.

Then another message that appeared is (/usr/lib/libqconf2-4/gconf-sanity-check-2 exited with status 256)

Thinking that I might still get back into Ubuntu I then started getting the message "The configuration defaults for Gnome Power manager have not been installed correctly"

It appears that I can sign into Ubuntu, but one can tell that things just aren't right. Clock is off as well as other things.

By the way, when I try to boot up **I NO LONGER can boot into my Windows OS**!!

Also something all screwed up with capacity set up on the hard drive. It showed that I had run out of room....BUT I know there should have been more than enough room. Using disk usage analyzer....File system capacity showed 20.3Gb, used was 5.0Gb, but showed 100% usage, That is wrong. Used 5.2Gb available from 15.1. Some of this probably doesn't make any sense to you; just think how I must feel? :)

So I'm thinking maybe I should delete all the files in the partition and start all over again. But I don't know how to do that. But perhaps someone out there in Ubuntu Land has a better idea. Remember you're dealing with a 71 year old hard headed neophyte.  My sincerest thanks.

---

### Post by loybanks on 2011-06-10
> **loybanks said:**
> I downloaded the 11.4 .iso package. Installed onto USB without any problem with help of Universal USB Installer.

Then started the install from USB to New Toshiba Netbook NB505. Installing along side the Windows7 OS. It appeared that all was going well. Little did I know!!!

BUT...right at the end of the install it stopped with message "There is a problem with the configuration server". That alone bamboozles me.

Then another message that appeared is (/usr/lib/libqconf2-4/gconf-sanity-check-2 exited with status 256)

Thinking that I might still get back into Ubuntu I then started getting the message "The configuration defaults for Gnome Power manager have not been installed correctly"

It appears that I can sign into Ubuntu, but one can tell that things just aren't right. Clock is off as well as other things.

By the way, when I try to boot up **I NO LONGER can boot into my Windows OS**!!

Also something all screwed up with capacity set up on the hard drive. It showed that I had run out of room....BUT I know there should have been more than enough room. Using disk usage analyzer....File system capacity showed 20.3Gb, used was 5.0Gb, but showed 100% usage, That is wrong. Used 5.2Gb available from 15.1. Some of this probably doesn't make any sense to you; just think how I must feel? :)

So I'm thinking maybe I should delete all the files in the partition and start all over again. But I don't know how to do that. But perhaps someone out there in Ubuntu Land has a better idea. Remember you're dealing with a 71 year old hard headed neophyte.  My sincerest thanks.


In doing some more playing around I am able to get into Ubuntu and play around. I'm downloading a Clip Ap right now. So just may fixing this installation might be the proper solution. What do you think? So many confusing issues here.

---

### Post by garvinrick4 on 2011-06-10
Open a terminal in Ubuntu ctrl/alt/t and run these copy and paste if you prefer:
```
sudo dpkg --configure -a
```
```
sudo update-grub
```
IF those work fine run these:
```
sudo apt-get update && sudo apt-get upgrade
```
If all went well should be able to reboot into Windows.
Let me know any results: There is a post installation guide in my signiture.

---

### Post by loybanks on 2011-06-10
> **garvinrick4 said:**
> Open a terminal in Ubuntu ctrl/alt/t and run these copy and paste if you prefer:
```
sudo dpkg --configure -a
``````
sudo update-grub
```IF those work fine run these:
```
sudo apt-get update && sudo apt-get upgrade
```If all went well should be able to reboot into Windows.
Let me know any results: There is a post installation guide in my signiture.


I ran the first code and it appeared to execute. At least I didn't get any message back.

Then I tried to run the second but got following message...cannot stat 'aufs'

Thanks.

---

### Post by loybanks on 2011-06-10
> **loybanks said:**
> I ran the first code and it appeared to execute. At least I didn't get any message back.

Then I tried to run the second but got following message...cannot stat 'aufs'

Thanks.

Looks like there is another larger issue. The Ubuntu coming up has apparently been from the USB Install Drive, not from the Hard Drive. When I take the USB Drive out and try to boot, the BIOS of course then shows only the Hard Drive....but it won't boot to the drive....Instaed I get the message on the black screen that error: no such device: then a long number and...shows grub rescue>

So now what my friend?

---

### Post by garvinrick4 on 2011-06-10
EDIT: just saw previous post: put your USB back in and boot and run this below:
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
Download to Desktop and run this code and will put a RESULTS file on desktop copy
and paste here. After download run this below in a terminal:
  ```
sudo bash ~/Desktop/boot_info_script.sh
```Make sure you have internet connection below: Make sure internet working!!

Do not run this below we need the boot script:
```
sudo apt-get update
``````
sudo apt-get purge grub grub-common grub-pc
``````
sudo apt-get install grub-common grup-pc
```Toggle with Tab key above if asked and install in sda
```
sudo apt-get update && sudo apt-get upgrade
```##I do not know if it is going to straighted out "aufs" but cannot hurt to try this:
removing grub and reinstalling and to mbr of sda
updating and upgrading. Just to get your other installs in there and grub fixed up.

---

### Post by loybanks on 2011-06-11
Thanks for all your help. After going around and around I decided to just forget about Windows7 on this Notebook and go all the way for Ubuntu. So now I have a new Notebook with Ubuntu Linux installed. I formatted the drive completely. Now to the learning process.

I do have another issue however with this machine. It's concerning Internet Connection. I'm connected using an ether net cable. I can bring up my Firefox, etc.

But when I try to download for example PassKey Ap I keep getting the message...Failed to download package file - Check your Internet connection...And this same thing has happened when trying to download other aps. 

And I know I'm connected. So what might be happening here?

---

### Post by garvinrick4 on 2011-06-11
What happens when you update any errors?
```
sudo apt-get update
```There is a post installation guide in my signature.

---

