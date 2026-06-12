---
title: "OpenOffice Won't Open"
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by 3z3k3l on 2006-07-06
Actually none of my OpenOffice apps will open. I have been regularly applying the updates that are in that little pop up window, and since then Open Office stopped working. Drapper is working fine except anytime I open OpenOffice, the splash screen opens up and then after a second just closes and no apps show.

Is there an upgrade or fix somewhere? I tried re-Installing the OpenOffice package from Syn. but that didn't do anything.

Any tips?

---

### Post by John.Michael.Kane on 2006-07-06
Are you running 32bit or 64bit ubuntu? if it's 64bit then you may need to check to see if the 32bit lib's are installed. i'm not running openoffice so these are guesses.

you can also try

sudo aptitude update 
followed by::
sudo aptitude upgrade 
after which:
sudo aptitude install openoffice.org

---

### Post by 3z3k3l on 2006-07-09
> **SD-Plissken said:**
> Are you running 32bit or 64bit ubuntu? if it's 64bit then you may need to check to see if the 32bit lib's are installed. i'm not running openoffice so these are guesses.

you can also try

sudo aptitude update 
followed by::
sudo aptitude upgrade 
after which:
sudo aptitude install openoffice.org

Thanks for the reply,I am not sure which version I have installed? I just upgraded to drapper and I believe it worked it has only been since I started using the automated update things that things stop working like MPlayer and OpenOffice, it seems like a lot of apps try to run then just shut down before they start.

I did exactly as you posted up but still no go.
Here are the results.

> Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
Writing extended state information... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release [30.9kB]Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages [41.9kB]Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [27.4kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages [14B]Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources [24.5kB]Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [4253B]Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources [14B]Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [7105B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [974B]Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [6042B]Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages [1677B]Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [902B]Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources [533B]Fetched 177kB in 1s (112kB/s)
Reading package lists... Done
rcruz@localhost:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  libdvbpsi3 libwxgtk2.4-1 ttf-thryomanes
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 5915kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 112532 files and directories currently installed.)
Removing libdvbpsi3 ...
Removing libwxgtk2.4-1 ...
Removing ttf-thryomanes ...
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.
rcruz@localhost:~$ sudo aptitude install openoffice.org
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
rcruz@localhost:~$


Should I reboot or something?

Thanks for your help. I am almost ready to uninstall this it was great on 5.5 but upgrading is starting to give me a lot of problems.

---

### Post by Cheule on 2006-07-10
Are you using a Radeon card below a 9500? There were several issues with the latest ATI drivers, one of which stops OpenOffice from loading at all.

Not sure if this is your problem though.

---

### Post by Malac on 2006-07-10
I had this exact same problem and it turned out that removing what I assumed was a totally unrelated program in Synaptic(can't remember which one) also took out one of the openoffice libs.

I went into Synaptic and did a search for openoffice under "Description and Name" entries and marked them all for re-install and this solved the problem for me.

Hope this helps.

---

### Post by cory223 on 2007-11-11
Did you ever get a fix for this problem? I have the same issue. Clicking on open office in Feisty does nothing.

---

