---
title: "Apache2 Installation Errors"
date: 2011-04-23
forum: Installation &amp; Upgrades
---

### Post by jstvincent on 2011-04-23
I am new to Ubuntu (and Linux) as I have had it running for 3 days now, and want to get down with my plan for my home Intranet. I am trying to install Apache2 via the "sudo apt-get install apache2" command and I get the following errors:
 
missing dependencies:
 
apache2-mpm-worker
apache2-mpm-prefork
apache2-mpm-event
apache2-mpm-itk
apache2-2-common
 
All of them end with (=2.2.14-5ubuntu8.4)
 
I need help figuring out what is going wrong and how to fix it.
 
Thanks,
 
jstvincent

---

### Post by cantormath on 2011-04-23
do you get any errors when you run the following in terminal?
:~$ sudo apt-get update

Have you done all the upgrades?
:~$ sudo apt-get update
:~$ sudo apt-get upgrade && sudo apt-get dist-upgrade

---

### Post by jstvincent on 2011-04-23
I am not connected to a LAN or Wi-Fi, as I do not have a long enough ethernet cable, so the update that checks through Internet to Ubuntu won't work. I will try anyway just to see if they work. I will find out in about 10 minutes, if you're still online.

---

### Post by Blasphemist on 2011-04-23
I don't know what your plans are for your home intranet but I'm guessing from you installing apache that you may want to do some development. I am including a link to the complete way to do that for a complete development environment. This in itself is a good learning tool. [http://vmirgorod.name/11/1/20/drupal-development-environment-based-ubuntu-1010](http://vmirgorod.name/11/1/20/drupal-development-environment-based-ubuntu-1010)

This is a link to the Apache config files page. [http://httpd.apache.org/docs/2.1/configuring.html](http://httpd.apache.org/docs/2.1/configuring.html)

I think you're already on to installing apache but that is included in the information on the first link.

---

### Post by jstvincent on 2011-04-23
I have now connected to a LAN and ran these:

sudo apt-get update
sudo apt-get upgrade && sudo apt-get dist-upgrade

I got most of the downloads, minus this:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

I need to know what I can do to fix this. Apache will still not install (same errors) through the Terminal and I even tried through the Software Center. Just for extra info, I am using Lucid Lynx 10.04.2 LTS.

Sadly I don't have the time to do the full developer install like the other suggestion, I only need to be aple to load HTML pages, so nothing big developer-wise.

---

