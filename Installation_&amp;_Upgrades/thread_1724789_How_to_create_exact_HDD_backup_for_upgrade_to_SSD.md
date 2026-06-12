---
title: "How to create exact HDD backup for upgrade to SSD?"
date: 2011-04-08
forum: Installation &amp; Upgrades
---

### Post by poltak on 2011-04-08
Hey there. Just got a small question:

I currently have been using 10.10 on my new netbook. I've been an Arch user for a while, but recently come back to ubuntu for my new netbook since it's a lot simpler to get working from installation, imo (oh and I'm quite impressed with how far Ubuntu's come in the last year since I used it :)).

Anyway, I want to upgrade to a 128GB SSD but I also want to keep the current setup I'm running on my current 320GB HDD. Is there any good HDD imaging tools for Ubuntu/Linux (that's relatively easy to use), as I've never done this before?

Also, bear in mind, my current HDD has a three partition setup. 4.1GB swap, 8.2GB ext3 (/ directory), 308GB ext3 (/home directory) respectively.

And also an additional question: As the new SSD has only 128GB (compared to my current 320GB), is it possible to shrink my /home partition but keep the other partitions at their current sizes? (as my /home partition has probably over 128GB free space anyway)

Oh and also, how big do Ubuntu root partitions have to be in general? I think my 8.2GB / is a bit of an overkill, is it not?

Thanks a lot for your time :),
poltak

---

### Post by oldfred on 2011-04-09
Users have posted these:

[http://clonezilla.org/](http://clonezilla.org/)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)


But I believe in clean installs. Are you keeping the current 320GB drive for data? If so just create partitions of the size you want and install. All your user setting are in /home so if you copy it to your new /home you will have all your new settings. Just keep same user or you may have issues.

I suggest 10-20GB for / (root). I use 20-25GB and have at least one system installed on every drive. I like to keep all the system files on one drive so if any drive fails I can still boot the other. I rotate Ubuntu versions around so I have old install, current install and next/alpha/beta/RC for testing.

My roots have a lot of software and I have used about 7GB in root. But if creating a DVD you may use another 4GB in /tmp and then I have used about half of my root space which is the most I want to use.  

You may have a few system wide settings in /etc but do not copy files back from another install. New versions often are different. I just copy my settings if I still need them. 

You also want to export a list of installed apps and reinstall those.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

List Packages
dpkg --get-selections > ubuntu-files
Reinstall
sudo dpkg --set-selections < ubuntu-files && sudo apt-get dselect-upgrade

---

### Post by poltak on 2011-04-09
> **oldfred said:**
> 
You also want to export a list of installed apps and reinstall those.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

List Packages
dpkg --get-selections > ubuntu-files
Reinstall
sudo dpkg --set-selections < ubuntu-files && sudo apt-get dselect-upgrade

I like this idea. I never knew you could do this with the dpkg. Very nice, as I also believe in fresh installs.

Have you actually done it this way before? So from what I can see it just goes through the saved list of apps and installs them all sequentially, ignoring the apps already installed?

I'm assuming I'd also have to copy over my mirrorlist for ppa's and such, also?

---

### Post by oldfred on 2011-04-09
If you copy ppa's you also have to update version. Yes it only reinstalls current versions of apps not already installed. You may want to house clean list, it is long. You do not want old kernels and if upgrading to Natty for instance you get LibreOffice and then may not also want OpenOffice. Other older apps you may not want. I think I still get python 2.5.

I have use dpkg for all my installs since 9.04, but have run it against several of the versions, beta, RC, final on each. I also have a script to install some defaults and set up some things.

I will post my script, but it is for my configuration. First half of script which has some logic to check versions  was posted by someone else and I added that to mine. My original script was just a copy of history from one install. I just tried to do as much as I could from command line. Then I listed history. A lot is commented out as I changed how/what I did but kept command(s) in case I wanted to revert.

---

### Post by poltak on 2011-04-10
Ah, lovely :) I'll get the SSD tomorrow morning and try this out and tell you how it goes.

Thanks a lot for your help so far. Very much appreciated! Learnt some new things.

---

