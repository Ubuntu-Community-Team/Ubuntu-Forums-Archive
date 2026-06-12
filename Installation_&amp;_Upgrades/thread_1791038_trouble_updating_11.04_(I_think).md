---
title: "trouble updating 11.04 (I think)"
date: 2011-06-26
forum: Installation &amp; Upgrades
---

### Post by johanneatscoffee on 2011-06-26
Maybe I have the beta, I'm really not sure, but when I try to update with sudo apt-get update I get the following:

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with Merglelist /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened

When I open the software center, whenever I click on any icons it just loads without ever loading.  I've seen this same exact situation posted elsewhere, but I either didn't understand the solution or one wasn't really given.  Super noob, you may have to break it down for me....

---

### Post by mörgæs on 2011-06-26
Hi, welcome to the fora.

Try to boot the computer and run this:

```
sudo apt-get clean
sudo rm /var/lib/apt/lists/*
sudo apt-get update
sudo apt-get upgrade
```

Please post the error messages, if you get any.

---

### Post by johanneatscoffee on 2011-06-26
rm: cannot remove 'var/lib/apt/lists/partial': Is a directory

So far as I can tell sudo apt-get clean either doesn't do anything or doesn't tell me it does anything

:(

---

### Post by s9032g@comcast.net on 2011-06-26
try this series:

Clean up your package installation

If you have installed and uninstalled a lot of applications, chances are your system is infected with a lot of dependencies files that you have absolutely no use for. Here are some useful commands to get rid of any partial package and remove any unused dependencies:
Cleaning up of partial package:
sudo apt-get autoclean

Cleaning up of the apt cache:
sudo apt-get clean

Cleaning up of any unused dependencies:
sudo apt-get autoremove

A good practice to avoid any left behind is to use the autoremove command whenever you want to uninstall an application.
sudo apt-get autoremove application-name

---

### Post by johanneatscoffee on 2011-06-26
That seemed to do it!  Thanks a lot!

---

### Post by mörgæs on 2011-06-26
Actually I think that the rm-command did the trick. The directory warning is not important; what matters are the other lists deleted.

I am not saying this in order to pat myself on the back, more to help others who might read this thread.

The apt commands posted by s9032g are a good way of keeping an Ubuntu system tidy,  but I doubt that they can open a locked update process.


By the way, no matter whether you initially installed the beta or the system as of release day, you will have a fully updated system when applying the standard updates. An alpha or a beta will automatically grow into the 'real' release.

---

### Post by johanneatscoffee on 2011-06-27
Well in that case, thanks both of you!

---

### Post by chamira on 2011-08-22
Thank you, this saved the day for me just now.:popcorn:

---

### Post by arsh.singh on 2011-10-02
Yep mörgæs is correct ... the rm command did the trick :popcorn:

---

