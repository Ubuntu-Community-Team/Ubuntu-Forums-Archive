---
title: "Removing Image Gallery"
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by textguru on 2006-12-14
I need to reinstall Image Gallery Server as indicated on [http://ubuntuguide.org/wiki/Dapper#Image_Gallery_Server](http://ubuntuguide.org/wiki/Dapper#Image_Gallery_Server) due to some deleted or moved files that I made. I have tried to run again the commands but it seems I cannot due to existing program on my machine. hope you could help me remove the gallery. Here is the commands that I made:
> sudo apt-get install gallery (when prompted to restart Apache, choose No or Cancel)
sudo apt-get install imagemagick
sudo apt-get install jhead
sudo apt-get install libjpeg-progs
sudo /etc/init.d/apache2 restart
sudo sh /usr/share/gallery/configure.sh

---

### Post by FryerFox on 2006-12-14
What is the error message?

---

### Post by textguru on 2006-12-14
> **FryerFox said:**
> What is the error message?
here is the details
> ubuntu@mypc:/var/www$ sudo apt-get install gallery                  Password:
Reading package lists... Done
Building dependency tree... Done
gallery is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


if I will try to run configure:
ubuntu@mypc:/var/www$ sudo sh /usr/share/gallery/configure.sh

You are now in setup mode.  Your Gallery installation
can be configured by pointing your web browser
to the setup wizard (e.g. [http://www.example.com/gallery/setup/index.php](http://www.example.com/gallery/setup/index.php))

When accessing thru a browser here is the error:

**Warning**:  mkdir() [function.mkdir]: No such file or directory in **/usr/share/gallery/classes/gallery/UserDB.php** on line **43**
Error: Unable to create dir: /var/www/albums/.users                      Upgrading Users
  The user database in your gallery was created with an older version of the software and is out of date.   This is not a problem!   We will upgrade it.  This may take some time.   Your data will not be harmed in any way by this process.   Rest assured, that if this process takes a long time now, it's going to make your gallery run more efficiently in the future.    If you get an error, and only some users are upgraded, try refreshing the page to upgrade remaining users.   
  
Please Wait... 
**Fatal error**:  Call to a member function getUsername() on a non-object in **/usr/share/gallery/classes/gallery/UserDB.php** on line **337**

Hope you might help.

---

### Post by FryerFox on 2006-12-14
I'm not sure where these errors could be coming from, but it seems that a directory and/or file was not created - possibly due to file permissions.

You might try uninstalling gallery (select Mark for Complete Removal in Synaptic), and then reinstalling to see if the post-install script takes care of this. Or even better, if there is a README file that comes with the distribution, then scan through that to see if you need to manually change permissions or something else before running it.

---

### Post by textguru on 2006-12-15
> **FryerFox said:**
> I'm not sure where these errors could be coming from, but it seems that a directory and/or file was not created - possibly due to file permissions.

You might try uninstalling gallery (select Mark for Complete Removal in Synaptic), and then reinstalling to see if the post-install script takes care of this. Or even better, if there is a README file that comes with the distribution, then scan through that to see if you need to manually change permissions or something else before running it.
I am using a server. Can I just remove it on the terminal? need the exact application name.

---

