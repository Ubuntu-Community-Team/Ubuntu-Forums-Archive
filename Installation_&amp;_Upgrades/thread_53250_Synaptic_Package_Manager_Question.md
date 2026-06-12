---
title: "Synaptic Package Manager Question"
date: 2005-07-30
forum: Installation &amp; Upgrades
---

### Post by es012 on 2005-07-30
When I use the Synaptic Package Manager to download and install programs, it downloads at 200 to 900 bytes per second. This is very much too low a download speed to download any large programs, so I would like to download these programs, and the dependencies, using windows. I would like some help with installation of programs that are tar and rpm, and how to make them appear in the menu. Its either this or can any one tell me if there is some way to speed up the download speed? Thanks for the help!

---

### Post by amohanty on 2005-07-30
What kind of a connection do you have?

Also check your speed at testmy.net

AM

---

### Post by es012 on 2005-07-31
My connection is a dial-up 56k modem. I am using a Boca Tidalwave v.90 56k serial modem. This is the results from that site while using winxp:

:::.. Download Stats ..:::
Connection is:: 36 Kbps about 0 Mbps (tested with 579 kB)
Download Speed is:: 4 kB/s
Tested From:: [http://testmy.net/](http://testmy.net/) (server1)
Test Time:: Sun Jul 31 2005 12:20:09 GMT-0500 (Central Standard Time) 
Bottom Line:: 1X faster than 56K 1MB download in 256 sec 
Diagnosis: May need help : running at only 20.34 % of your hosts average (pressenter.com) 
Validation Link:: [http://testmy.net/stats/id-15902NTGS](http://testmy.net/stats/id-15902NTGS) 

I will try the site using Ubuntu and see what the stats are in that OS.
Thanks, ES

---

### Post by amohanty on 2005-07-31
That is very slow. You could look at the forums at testmy.net to figure out some speedup tips.

AM

---

### Post by wildrose71 on 2005-07-31
I have been experiencing this too. I am on a 56k modem that never goes up to 56k :-)

However, there is something to try.....I am now doing an apt-get instead and it downloads MUCH faster that way. I have also tried to download from sites and that went fast too but then I don't know how on earth to get the program installed from where I have stored them *sigh* I guess I'll figure that one out eventually :-)

Anna

---

### Post by amohanty on 2005-07-31
The very first line in /etc/apt/sources.lst points to your cdrom drive. 
Replicate the structure in your cdrom drive on a local dir and copy the cdrom line in sources.lst into another one change the location. viola! you will have a local repository to work with.

AM

---

### Post by kosmic on 2005-07-31
Or use the dpkg-scanpackages (your debs location/.*) | gzip > Packages.gz

To make a local repository :)

---

### Post by es012 on 2005-08-01
I figured out my problem: I installed GnomePPP and used that to connect to the internet. I now connect at a higher speed. When I started the Synaptic Package Manager and hit reload it started to download at 13 KB/s, then went down to 4000 - 5000 bytes per second - instead of 200 - 800 bytes. Apparently, when I dialed using the networking interface it wasn't doing it correctly, by selecting the modem and hitting activate. I will now use GnomePPP to activate my modem. Below is the results after installing and connecting with GnomePPP; I could not move through the site when being connected before the installation of this program. Thanks for the help! ES.

:::.. Download Stats ..:::
Connection is:: 37 Kbps about 0 Mbps (tested with 579 kB)
Download Speed is:: 5 kB/s
Tested From:: [http://testmy.net/](http://testmy.net/) (server1)
Test Time:: Sun Jul 31 2005 13:13:28 GMT-0500 (CDT) 
Bottom Line:: 1X faster than 56K 1MB download in 204.8 sec 
Diagnosis: May need help : running at only 23.57 % of your hosts average (pressenter.com) 
Validation Link:: [http://testmy.net/stats/id-26K9EV0BQ](http://testmy.net/stats/id-26K9EV0BQ)

---

I just connected to the Internet using my Dynex 56k v.92 USB modem. The results from the testmy.net site are very sad. I cannon make this modem work in Ubuntu - and after seeing what it connects at I don't want to! I ran this test twice and the first time it connected at 27.

:::.. Download Stats ..:::
Connection is:: 24 Kbps about 0 Mbps (tested with 579 kB)
Download Speed is:: 3 kB/s
Tested From:: [http://testmy.net/](http://testmy.net/) (server1)
Test Time:: Mon Aug 01 2005 19:44:37 GMT-0500 (Central Standard Time) 
Bottom Line:: 0X faster than 56K 1MB download in 341.33 sec 
Diagnosis: May need help : running at only 18.75 % of your hosts average (pressenter.com) 
Validation Link:: [http://testmy.net/stats/id-WRM89KLTD](http://testmy.net/stats/id-WRM89KLTD)

---

