---
title: "Apache broken after upgrade"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by usacomp2k3 on 2007-04-24
So I upgraded my web server from 6.10 to 7.04 last weekend. (I did the update-manager thing as detailed in the sticky). It went ok, except that Apache wasn't working right. For some reason, it didn't want to set the server root as /ext/www instead of the default /var/www No matter what I did to the /etc/apache2/apache2.conf, the server root didn't change. I know that that was the right .conf file, since I tested it by changing the ports.conf reference in apache2.conf to ports2.conf and it errored out saying it couldn't find ports2.conf 
I could make it work by setting a symlink of /ext/www as /var/www and that sort of worked, but links and images got all funky, so I knew that that couldn't be a permanent solution.
Anyway, so I thought I'd reinstall apache2. Here's the steps I took:
*backed up apache2.conf
*apache2ctl stop
*apt-get remove apache2
*rm -rf /etc/apache2
*apt-get install apache2

It didn't error out (went back to the prompt after doing the fetch/selecting/reading/unpacking/setting up thing)
So, I do an 'apache2ctl start' and:
"apache2: Could not open configuration file /etc/apache2/apache2.conf: No such file or directory"
I look in /etc, and there is no apache2 folder. Why didn't it recreate it?

So my question is, how do I install apache2 and get it to recreate the folder structure in /etc/apache2?

---

### Post by usacomp2k3 on 2007-04-25
So I went through syanptic and did a complete removal of apache2 (plus a few other dependencies) and then did a reinstall, and finally it got apache working again. Then I realized where my stupidity lay: I had to edit the sites.conf file to give the server root again *sigh* Who would have thought. Hopefully this helps someone else out if they are having issues.

---

### Post by R.Bucky on 2008-04-30
yup, my server broke too. I can view it on localhost, but the apache portion is dead. i have searched all over the place. where in the heck is the sites.conf file?

---

