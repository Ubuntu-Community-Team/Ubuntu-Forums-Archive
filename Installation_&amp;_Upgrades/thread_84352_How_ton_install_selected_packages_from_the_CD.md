---
title: "How ton install selected packages from the CD?"
date: 2005-10-30
forum: Installation &amp; Upgrades
---

### Post by subscrive on 2005-10-30
Hi,

I have installed ubuntu in a server mode.
Now I want to install xserver, gdm, and very selected packages.
Please tell me how to do it?
After putting the cd in the drive, apt-get install gdm fails?
How can I point apt-get to cdrom and then install it from there?

Thanks.

~A.

---

### Post by aysiu on 2005-10-30
What's your /etc/apt/sources.list look like?

---

### Post by audax321 on 2005-10-30
Also are you sure you're typing:

sudo apt-get install gdm

The sudo command is required to install the package as root.

---

### Post by subscrive on 2005-10-31
I have tried sudo (just didnt write it while posting).

My sources.list is (please note that I have upgraded from hoary to breezy) -->

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb http://in.archive.ubuntu.com/ubuntu breezy main restricted
 deb-src http://in.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb http://in.archive.ubuntu.com/ubuntu breezy-updates main restricted
 deb-src http://in.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://in.archive.ubuntu.com/ubuntu breezy universe
 deb-src http://in.archive.ubuntu.com/ubuntu breezy universe

 deb http://security.ubuntu.com/ubuntu breezy-security main restricted
 deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe

---

### Post by aysiu on 2005-10-31
I'm not sure if this is the problem, but it seems odd to me that your CD-ROM source is for Hoary, and the rest of your sources are for Breezy. How did that happen?

---

### Post by subscrive on 2005-10-31
I installed hoary and then changed the sources.list to point to breezy, did apt-get update, and then apt-get dist-upgrade. Let's not discuss on that.


Suppose I install the hoary without any GUI (with its proper sources.list file with has proper hoary entries - please dont ask me any more abt hoary and breezy. I have already stated that for my current machine I have upgraded from H to B) on some other machine.

Now how can I tell the apt-get to to search the cdrom and then install the GUI?

OR

Say I download a proper breezy ubuntu and then do a server install. How will I be able to install the GUI?

---

### Post by audax321 on 2005-10-31
Well in order to install the debs from the CD you will need the Breezy CD anyway since dist-upgrade changed your distribution from Hoary to Breezy. Now, in order to have it look at the CD, change:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

to

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

Keep in mind the date in the line might change if the CD you downloaded is newer, though I'm pretty sure the images up right now are the same ones that were released. Then while the CD is in the drive, do:

sudo apt-get update

and that should update the list of packages so you can install them.

If this doesn't work, try commenting out all lines but the CD, do sudo apt-get update and then try installing the packages.

---

### Post by subscrive on 2005-10-31
I installed hoary on my 2nd machine.

the sources.list are as follows:
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
#deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) hoary main restricted
#deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
#deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) hoary-updates main restricted
#deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) hoary universe
#deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) hoary universe

#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe





I tried what you said about commenting and then doing apt-get... (ofcource with sudo). But its not working...
it fails giving the same error as one would get if it doesnt find the website source.

---

