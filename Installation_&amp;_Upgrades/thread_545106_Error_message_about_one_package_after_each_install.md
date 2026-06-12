---
title: "Error message about one package after each install"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by johann_p on 2007-09-07
After installing the recommended (by the update manager) update to Drupal, I got the message

dpkg: error processing drupal-5.1 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 drupal-5.1


Now this message appears each time I use Synaptic, also if I install other packages. 

How can I figure out what the problem is and how can I get rid of the problem, and the message?

---

### Post by jtuchscherer on 2007-09-07
I have the same problem here. Would like to resolve this, too.
Any addvide is welcome.

---

### Post by Pumalite on 2007-09-07
Try this: sudo dpkg --configure -a
If not, then: sudo dpkg --remove --force-remove-<packagename>

---

### Post by jtuchscherer on 2007-09-08
Even removing and reinstalling the package didn't help.

Here is the console output:
johannes@desktop:~$ sudo aptitude install drupal-5.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following NEW packages will be installed:
  drupal-5.1 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/761kB of archives. After unpacking 3383kB will be used.
Writing extended state information... Done
Preconfiguring packages ...
Selecting previously deselected package drupal-5.1.
(Reading database ... 154178 files and directories currently installed.)
Unpacking drupal-5.1 (from .../drupal-5.1_5.1-0ubuntu2.1_all.deb) ...
Setting up drupal-5.1 (5.1-0ubuntu2.1) ...
dbconfig-common: writing config to /etc/dbconfig-common/drupal-5.1.conf
Replacing config file /etc/drupal/5.1/sites/default/dbconfig.php with new version
dbconfig-common: flushing administrative password
dpkg: error processing drupal-5.1 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 drupal-5.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up drupal-5.1 (5.1-0ubuntu2.1) ...
dbconfig-common: writing config to /etc/dbconfig-common/drupal-5.1.conf
Replacing config file /etc/drupal/5.1/sites/default/dbconfig.php with new version
dbconfig-common: flushing administrative password
dpkg: error processing drupal-5.1 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 drupal-5.1

---

### Post by Pumalite on 2007-09-08
At this point I would download a new package,

---

### Post by jgneff on 2007-09-08
If you go to the install URL on your Drupal machine:

```
http://localhost/drupal/install.php?profile=default
```

you'll notice it's failing to connect to the MySQL database.  That's why the installation script fails.  The following post-installation script is looking for the message "Drupal installation complete" in the URL response:

```
/var/lib/dpkg/info/drupal-5.1.postinst
```

I had the same error and got around it by simply defining my own password for the database user "drupal51" when prompted, instead of letting the installation script generate a random password.

You define your own password when the package configuration prompts you with "MySQL application password for drupal-5.1."  That's where it also says, "If left blank, a random password will be generated for you."  It was that random password that caused the upgrade problem for me.

Note that you need to fully remove Drupal and its configuration files before trying to reinstall it:

```
$ sudo apt-get remove --purge drupal-5.1
```

Otherwise, you just get stuck with the same error when trying to reinstall.  I can delete (drop) the drupal51 database because I put all my actual Drupal sites into other MySQL databases, so the default drupal51 database is never used on my system (except for installing and removing the package).

John Neffenger

---

### Post by Pumalite on 2007-09-08
Thank you for the explanation. I understand the problem better, but that also leads me to recognize that I cannot help you. Patience; someone will chime in.

---

### Post by johann_p on 2007-09-08
OK, this is odd - I could run/use Drupal just fine but that postinstallation script kept complaining. I guess this is a bug or something not really thought out too well.

Since I had Drupal installed just for testing, I gave up and removed it to avoid all the hassle.

---

### Post by ivomans on 2007-10-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/drupal/+bug/106689](https://bugs.launchpad.net/ubuntu/+source/drupal/+bug/106689) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				A simple workaround to get rid of the message:

Edit the file /var/lib/dpkg/info/drupal-5.1.postinst line 56. 

Edit the part 
```
   grep "Drupal installation complete" 
```into
```
   egrep "Drupal installation complete|Drupal already installed"
```

---

### Post by marcw on 2007-11-10
> **ivomans said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/drupal/+bug/106689](https://bugs.launchpad.net/ubuntu/+source/drupal/+bug/106689) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				A simple workaround to get rid of the message:

Edit the file /var/lib/dpkg/info/drupal-5.1.postinst line 56. 

Thanks a million!  That did the trick for me.  I've been living with that goofy error message for way too long...

---

### Post by Pumalite on 2007-11-10
I'll book mark it.

---

