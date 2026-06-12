---
title: "MythTV Installation"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by LTBP5WD2 on 2006-11-05
I am a newbie when it come to Linux.  I am looking for a SIMPLE set of directions to install MythTV on a fresh install of Ubuntu 6.06.  I have read allot of posts and it all looks like o foreign language to me.  I tried to install from Synaptic Package Manager but I got some kind of Mysql error.  No I am lost.  Thanks for any help that you can give.  I have downloaded the three packages from MythTV.  Now what??

[http://www.mythtv.org/modules.php?name=Downloads&d_op=viewdownload&cid=1](http://www.mythtv.org/modules.php?name=Downloads&d_op=viewdownload&cid=1)

---

### Post by rothgar on 2006-11-05
scrap 6.06 and install 6.10.
then follow the instructions here
[http://www.parker1.co.uk/mythtv_ubuntu.php](http://www.parker1.co.uk/mythtv_ubuntu.php)

6.06 doesn't have repositories for myth .20 and has mysql 5 which doesn't work with myth .19

---

### Post by LTBP5WD2 on 2006-11-05
I have not been able to install 6.10  The system freezes during the install.  I had to modify the ATI drivers to get 6.06 to install.

---

### Post by superm1 on 2006-11-05
If you want to use 6.06, I have packages built for dapper.

Add these to your /etc/apt/sources.list:

```
deb http://home.eng.iastate.edu/~superm1 dapper main
deb-src http://home.eng.iastate.edu/~superm1 dapper main
```


Follow the edgy install guide at [http://help.ubuntu.com/community/MythTV](http://help.ubuntu.com/community/MythTV)
The dapper one isn't finished, and there should be minimal differences between the two when said and done.

---

### Post by LTBP5WD2 on 2006-11-07
I am a complete newbie.  How do I add to my source list?  What is the best setup instructions to use?  There are many out there. The one I tried turned out to be for the server version and messed everything up. I think I installed something having to do with X windows.  I have done a fresh install of Dapper. I have the ATI drivers set and all updates have been done.  My /home is set as XFS 210gis.  Now what?

---

### Post by superm1 on 2006-11-07
You can add to your /etc/apt/sources.list by typing this in a terminal:

```
sudo gedit /etc/apt/sources.list
```

Paste the contents at the bottom of the file and hit save.
Open up synaptic package manager, and hit the reload button and you will update the repositories available.


If at all possible, it would be a better idea to install with edgy at this point.  The packages are included on the repositories, and I have a much more complete howto written for edgy to use those packages.
[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by LTBP5WD2 on 2006-11-07
what would be the best way to upgrade to Edgy?  I made an ISO image of Edgy but I cannot get it to install. The system freezes.  I am willing to try Edgy since it is so easy to insall Ubuntu (after I run sudo nano /etc/X11/xorg.conf) to set up Video card.  After Unbubtu install I have to udate fglrx to get the ATI X800GT recognized, Then I am good to go.

---

### Post by superm1 on 2006-11-07
The easiest way for an upgrade is:
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

If you don't have too much invested in your current install however, burning that ISO and reinstalling will make sure things go smoothly (i've read some not so great things about the edgy upgrades).

---

### Post by LTBP5WD2 on 2006-11-07
When I try to use the ISO of Edgy my system freezes. I can give it a try again.  Let me try to upgrade tonight.  I will try both methods to get Edgy on my system.  Is the Alternated CD different than the ISO?

---

### Post by superm1 on 2006-11-07
The alternate CD has a text based installer.  Its not the same as the server CD though, which won't install a GUI.

---

### Post by LTBP5WD2 on 2006-11-07
So do I burn the ISO and then follow the instructions for the alternate CD? 

 Thanks for your help.

---

### Post by superm1 on 2006-11-08
Depending which role or profile you choose -

Either you need a live disk or a server disk.  If the live disk is freezing upon startup, you can try to go into safe graphics mode off of it.  If that is still freezing, then you can use an alternate install disk.

---

