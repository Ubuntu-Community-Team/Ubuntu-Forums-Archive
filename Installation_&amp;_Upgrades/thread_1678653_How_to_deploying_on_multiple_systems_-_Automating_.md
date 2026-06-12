---
title: "How to deploying on multiple systems - Automating the install"
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by ~stephan on 2011-01-30
I am volunteering to assist a non-profit org with their technology, I will be presenting Ubuntu to the teachers this week and I hope to have a positive response to using Ubuntu!

With that said, the org being a bilingual school we will most likely focus on using Edubuntu.  While I personally use Ubuntu and have installed it over the years on multiple laptops & deskptops, I am now facing the task of installing and maintaining on a dozen laptops and another dozen deskptops!

While the install is very straight forward, installing on so many systems will be very time consuming!  In addition, we would like to install additional apps such as Skype, Dropbox, French Language support, Possibly Ailurus and a few other apps.

I am looking for suggestions how to best handle this?  What would be the best method to automate the install across the systems?

Could the best approach be to install Edubuntu and all the apps we require on one system and then create an image from the "master system" to be used for the other systems?

It seems that creating a “master” image would be ideal as it would include everything we need but I have never done that before!

I am looking for a solution as simple as possible and any suggestions are greatly welcome!  

Thank you to the all Ubuntu Community for providing such great software, and the Open Source Community as well for creating so many great apps!

Stephan

---

### Post by oldfred on 2011-01-30
I have not done this.

But a few questions. How similar are the systems? Different video cards and different drive sizes can cause major issues on a standard setup.

Many recommend these for system backup:
[http://clonezilla.org/](http://clonezilla.org/)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

You may not want to download updates for all the systems. Will they be connected to a server where you can control updates?

If not:
aptoncd 
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
Location of downloaded debs
/var/cache/apt/archives/

---

### Post by ~stephan on 2011-01-30
> **oldfred said:**
> I have not done this.

But a few questions. How similar are the systems? Different video cards and different drive sizes can cause major issues on a standard setup.

Many recommend these for system backup:
[http://clonezilla.org/](http://clonezilla.org/)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

You may not want to download updates for all the systems. Will they be connected to a server where you can control updates?

If not:
aptoncd 
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
Location of downloaded debs
/var/cache/apt/archives/
Olfred,

Good point, I should have mentioned that all the systems will be the same:

Laptops: Dell Latitude D410
Desktops: Dell Optiplex GX520

We might have to install a WIFI card on a few of the Deskptops afterwards but don't mind doing this manually.  I actually tested a card on one of these systems and it worked "out of the box" without having to install specific drivers.

I will look at the links you posted, we probably will start installing in about two weeks so that leaves us time to determine the best options.  We will NOT have our own server to download/store updates.

Thank you for the suggestions!

---

### Post by ~stephan on 2011-02-27
Update to this thread, just a few glitches which I hope can be resolved with some suggestions.

1) I installed Edubuntu on on one of the laptops, standard install and all worked great.

2) I installed the additional apps the school needed, Skype, Dropbox, Flash, additional games and a few other apps.  All worked great!

3) I changed the theme, configured compiz & cairo dock and ended up with a very pleasing to eye system for the teachers.

4) I used Remastersys to create and image of the system which could be re-distributed with the intention to re-install the same configuration accross all systems.

5) I used the Ubuntu Start up creator to create the installable image on a USB.

Up to this point everything was very simple and works great!

I installed the distribution on a 2nd Laptop, I get prompted for a user during the install and enter a new user name (user2) for the system.  Install works great and boot without a problem.

The settings from the "master" system being stored in the /home/user1 I used Rsync to include a copy of all the files and hidden directories as part of the image (stored it in /usr/user1_temp_settings.

**Once booted and logged on as user2 on the second system, I used Rsync to restore all files from /usr/user1_temp_settings/ (which was from the "master system") to /home/user2/**

Restarted the system, the deskptop looks identical to the "Master system" but I have two issues:

[B]1) I get prompted to enter the password to unlock the KEYRING each time I logon, I enter the password from the "master system", it works and I am able to to connect to the WIFI network.

While it works, it is really annoying to have to enter the keyring password each time.[/B]

Is there a solution to avoid this?

2) Dropbox seems to want to download the Deamon again, I proceed to do so but can't get it to run with no obvious errors.  Dropbox seem to be storing the hostname (encrypted) in a file and I suspect that might be causing the problem.

I fell I am about 90% there, the objective being to be able to clone each system with the same software, configuration and look & feel.

These are the only two issues I am facing, any suggestions greatly welcomed!

Thanks in advance.
Stephan

---

### Post by Old_Grey_Wolf on 2011-02-27
> **~stephan said:**
> 
[B]1) I get prompted to enter the password to unlock the KEYRING each time I logon, I enter the password from the "master system", it works and I am able to to connect to the WIFI network.

While it works, it is really annoying to have to enter the keyring password each time.[/B]

Is there a solution to avoid this?


Select Ubuntu main menu -> Applications -> Accessories -> Passwords and Encryption Keys.

In Passwords tab, right click Passwords: login. In the menu select Change Password… option.

Change the password from the master system password to the user login password.

It shouldn't ask for the keyring password anymore.

---

### Post by Old_Grey_Wolf on 2011-02-27
If you are going to be working on several computers, you may want to check into ClusterSSH (cssh) [http://sourceforge.net/apps/mediawiki/clusterssh/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/clusterssh/index.php?title=Main_Page).

You can get it from the Ubuntu repositories.

I use it when updating all of the computers may family has in my home. I just enter the commands once and all the computers get the same command in their terminals.

Edit: attached screenshot showing three computer terminals. I sometimes have 4 or more terminals open at the same time.

---

### Post by ~stephan on 2011-02-27
@Old_Gray_Wolf

Thanks for the tip on changing the password for keyring, that fixed the issue.  So that would me one more step after the install process I will need to document (have 20 laptops and 20 desktops to install).

I will try to remove the hidden directory for Dropbox as I suspect some of the encrypted data in some files might be causing the issue.  It is basically thinking the deamon is not installed, it downloads but they just stops.

As far the deployment itself and knowing the laptops will be for each teacher and not shared (we are not using LDAP or any other server authentication.) I am wondering if I am not over complicating the install.

Do I really need to have a different user on each system?  I read this post [http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys) where it suggests to copy the contents of the "master" system /home/user1 to /etc/skel

The article does not really explain the purpose but I have the feeling it will essentially create the same user as the "master" system?

Which if true, then I would have the same user on all systems?  Perhaps I could then create a new user maping the home directory from files copied to /etc/skel ??

I looked around in the forums and did not really see a "best practice" post to document cloning and deploying on multiple systems using different users on all systems.  I will continue to post my results here hoping it will help someone else.

Thank you everyone for the good tips so far!

Renastersys & Rsync/Grsync are really awesome tools!

Stephan

---

### Post by Old_Grey_Wolf on 2011-02-28
> **~stephan said:**
> Do I really need to hav a different user on each system?  I read this post [http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys) where it suggests to copy the contents of the "master" system /home/user1 to /etc/skel

If you look at the screenshot I posted, you will notice that all the accounts were for user "owner". All the systems have Ubuntu 10.04 LTS installed. They also have the same admin account (owner) and password. It just make it easier to use tools like clusterSSH. If I want each user to have their own account, I create an additional account later and give them the necessary permissions. After creating the users account the first time, I doesn't change very often.

LDAP doesn't make sense for my home network.

---

### Post by ~stephan on 2011-03-01
I have not looked at clusterSSH yet but definitely will.  I am somehow not seeing the screenshot?

After reading this article last night [http://www.linfo.org/etc_skel.html](http://www.linfo.org/etc_skel.html) I made a new image after copying all contents from the /home/masteruser to /etc/skel (as root).  

The install on the second system work great and it automatically copied the settings from the master account to the new account on the second machine!   That was awesome!  I only had to change the Keyring password which is only an extra step.

I almost resolved the Dropbox issue by removing the contents from the two hidden directories in the /home/user directory.  I tried that on the second sytem and that prompted Dropbox to re-download the deamon and get me to the setting screen.

I feel I am 99% there in having the image tweaked, the install on the new system will only take about 15-20 mins, one step to change the keyring password and 4 manual steps to re-configure dropbox!

This was my first time creating an image with the objective of cloning to other systems and can't believe how well it works!

Ubuntu rocks!  

Thank you everyone for the tips on this thread!

Stephan

---

### Post by Old_Grey_Wolf on 2011-03-01
> **~stephan said:**
> I have not looked at clusterSSH yet but definitely will.  I am somehow not seeing the screenshot?


The screenshot was in post #6.

---

### Post by ~stephan on 2011-03-02
I must be blind:-) Thank you for pointing it out, I have not looked at ClusterSSH yet but definitely will.  That looks very useful knowing we will have about 20 systems on the network and possibly more down the road.

Thanks again!
Stephan

---

