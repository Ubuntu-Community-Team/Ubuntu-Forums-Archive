---
title: "Installing Downloading Software"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by Gbleaney on 2011-04-29
I'm downloading a CMS (wordpress, [http://wordpress.org/download/](http://wordpress.org/download/)). Unfortunately I'm extremely new to linux, and I'm not sure where the proper place to extract the files is? Should it go in the lib folder? I really am fairly clueless.

---

### Post by mörgæs on 2011-04-29
Hi, welcome to the fora.

You should almost never download anything in Ubuntu. For Wordpress installation, see the link in my signature.

---

### Post by Blasphemist on 2011-04-29
Downloads default to the Downloads directory under your home directory. The download is a tarball. Just open it in the archive manager. In the top level directory see the install html file. Here is something I copied from it.

> Installation: Famous 5-minute install

Unzip the package in an empty directory and upload everything.
Open wp-admin/install.php in your browser. It will take you through the process to set up a wp-config.php file with your database connection details.
If for some reason this doesn't work, don't worry. It doesn't work on all web hosts. Open up wp-config-sample.php with a text editor like WordPad or similar and fill in your database connection details.
Save the file as wp-config.php and upload it.
Open wp-admin/install.php in your browser.
Once the configuration file is set up, the installer will set up the tables needed for your blog. If there is an error, double check your wp-config.php file, and try again. If it fails again, please go to the support forums with as much data as you can gather.
If you did not enter a password, note the password given to you. If you did not provide a username, it will be admin.
The installer should then send you to the login page. Sign in with the username and password you chose during the installation. If a password was generated for you, you can then click on 'Profile' to change the password.

---

### Post by Gbleaney on 2011-04-29
Thanks for the replies, they were informative, but not quite what I'm looking for. I'm wondering where I should put the directory I extract the files to. Is there some equivalent of a program files? Does it have no effect, but some place is simply good form?

---

### Post by Blasphemist on 2011-04-30
The default is /var/www as shown in this post.

[http://www.ubuntugeek.com/installing-wordpress-3-0-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/installing-wordpress-3-0-on-ubuntu-10-04-lucid-lynx.html)

What this describes isn't limited to 10.04 ubuntu.

---

### Post by mörgæs on 2011-05-01
Again, downloading strange stuff from here and there on the web is a bad Windoze habit. Installing Wordpress goes like this:

[http://ubuntuguide.org/wiki/Ubuntu:Natty#WordPress](http://ubuntuguide.org/wiki/Ubuntu:Natty#WordPress)

---

