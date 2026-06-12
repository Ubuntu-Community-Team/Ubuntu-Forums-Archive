---
title: "Package download failed - 1.4.6-5ubuntu1.3"
date: 2011-11-06
forum: Installation &amp; Upgrades
---

### Post by AppleWiz on 2011-11-06
Hi Folks,

Using Kubuntu 11.04 on Samsung Q320. I want to install a PPA but it gives a 404 not found. The KPackageKit refuses to do anything, and says "package download failed" 404 not found. So there is a network problem somewhere.

I really don't want to reinstall Kubuntu, it wrecks Windows7. The network adaptor is a Marvell Yukon 88E8057, which probably needs a Linux driver installed. Windows7 runs perfect on the Samsung. Web browsing works in Kubuntu, but little else.    

Can anyone advise what is best to do? 
 1. Install the Marvell Yukon driver (complicated)  
2. Try to install the "1.4.6-5ubuntu" file (more complicated)    

Thanks, 
Rob.

---

### Post by subehsharma on 2011-11-10
Best method to getaway from this problem is to install fix404. You can read about it more here:

Under Ubuntu, the APT package index is a database containing all packages of repositories (PPAs) defined in the /etc/apt/sources.list file. To update this database after adding some repositories, we need to use this command from the Terminal:

sudo apt-get update

Sometimes, when running the command given above, we get error messages (404 Not Found) that are the result of wrong PPAs, which may slow down the update process via the Terminal. In fact, this 404 Not Found error messages are not harmful at all, but you can use Fix404 to detect and remove these PPAs.

To install Fix404 on Ubuntu 11.04, launch the Terminal and run these commands:

sudo apt-add-repository ppa:lkjoel/fix404
sudo apt-get update
sudo apt-get install fix404

To install on Ubuntu 10.10/10.04, download this deb package here.

To start using Fix404, run this command (root privileges required):

sudo fix404

Then follow displayed instructions to disable PPAs causing the 404 Not Found Error.

---

### Post by AppleWiz on 2011-11-11
Thanks for your assistance...

Just before your post came in, I updated to 11.10. Perhaps this will solve these strange package download erros of itself, but I followed your instructions anyway.

At "sudo apt-get install fix404"
it reports E: Unable to locate fix package fix404

I type it all in twice from the start and got the same answer. Anyway I see the launchpad.net page for fix404 so will look through that.

Regards,
Rob.

---

### Post by subehsharma on 2011-11-11
check this site :

[http://www.upubuntu.com/2011/07/remove-ubuntu-ppas-that-cause-404-not.html](http://www.upubuntu.com/2011/07/remove-ubuntu-ppas-that-cause-404-not.html)

---

### Post by AppleWiz on 2011-11-13
OK,

Have done all it it seems to have sorted it out.

Thanks agn for assistance!

~Rob

---

