---
title: "LibreOffice will not start"
date: 2011-11-27
forum: Installation &amp; Upgrades
---

### Post by Leo Reijnen on 2011-11-27
I hope someone can help with this. I upgraded to Ubuntu 10.10 in three steps from Koala and have problems with LibreOffice. To keep it short, I purged OpenOffice and followed the instructions on [http://news.softpedia.com/news/How-to-Install-LibreOffice-in-Ubuntu-10-10-and-Ubuntu-10-04-177762.shtml](http://news.softpedia.com/news/How-to-Install-LibreOffice-in-Ubuntu-10-10-and-Ubuntu-10-04-177762.shtml)

Unfortunately, the command [COLOR=#008080]*apt-get install libreoffice libreoffice-gnome language-support-en*[/COLOR]

[[IMG]http://i1-news.softpedia-static.com/images/extra/LINUX/small/libreofficeubuntu-small_005.png[/IMG]]("http://i1-news.softpedia-static.com/images/extra/LINUX/large/libreofficeubuntu-large_005.jpg")
did not work, so I stripped the "language-support-en" bit and it installed.
Now I have all the LibreOffice icons in Unity, but when I try to launch any of the apps, simply nothing happens.

I also installed Java anew: openjdk-7-jre.

It's driving me nuts!
Final remark: during upgrade to 10.10 I got a lot of error messages about 'error installing ssl-certificates' stuff, but I don't know whether this is relevant.

Leo Reijnen

---

### Post by BC59 on 2011-11-27
Just execute on a terminal

```
sudo dpkg --configure -a
```

and 

```
sudo apt-get -f install
```

to see if everything is ok with the upgrade.

---

### Post by BC59 on 2011-11-27
and then try to fix the missing packages

```
sudo apt-get dist-update --fix-missing
```

---

### Post by Leo Reijnen on 2011-11-27
I get:

root@leo-laptop:/home/leo# dpkg --configure -a
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 51857 package 'virtualbox-3.1':
 error in Version string '3.1.0-55467_Ubuntu_karmic': invalid character in revision number

and 

root@leo-laptop:/home/leo# sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Leo Reijnen on 2011-11-27
and

root@leo-laptop:/home/leo# sudo apt-get dist-update --fix-missing
E: Invalid operation dist-update

---

### Post by BC59 on 2011-11-27
I think you should uninstall Virtualbox from Ubuntu software center because is not installed correctly.

---

### Post by Leo Reijnen on 2011-11-27
Thanks, I'll try that! Don't use it anyway...
Will get back here with the results and hope you will monitor this thread.
Leo

---

### Post by Leo Reijnen on 2011-11-27
> **Leo Reijnen said:**
> Thanks, I'll try that! Don't use it anyway...
Will get back here with the results and hope you will monitor this thread.
Leo
I removed VirtualBox and rebooted, but alas... no change...

---

### Post by BC59 on 2011-11-27
Now go again to Ubuntu software center and install the Libre Office or uninstall and install it again if it looks installed. Then reboot.

---

### Post by Leo Reijnen on 2011-11-27
> **BC59 said:**
> Now go again to Ubuntu software center and install the Libre Office or uninstall and install it again if it looks installed. Then reboot.
Alas! I even "purged" libreoffice, rebooted, installed it again, rebooted, but no dice.

This now comes back clean:
root@leo-laptop:/home/leo# dpkg --configure -a
root@leo-laptop:/home/leo# 

I see that the 'reboot required' icon top right is red again, so I'll try another reboot...

---

### Post by Leo Reijnen on 2011-11-27
> **Leo Reijnen said:**
> Alas! I even "purged" libreoffice, rebooted, installed it again, rebooted, but no dice.

This now comes back clean:
root@leo-laptop:/home/leo# dpkg --configure -a
root@leo-laptop:/home/leo# 

I see that the 'reboot required' icon top right is red again, so I'll try another reboot...
Still nothing, although after I try to start Calc, the restart icon goes red, requiring a "restart to complete updates". That's weird, isn't it?

---

### Post by BC59 on 2011-11-28
Try this

```

sudo add-apt-repository ppa:libreoffice/ppa

sudo apt-get update

sudo apt-get install --reinstall libreoffice 

sudo apt-get install libreoffice-gnome

sudo apt-get install language-support-en


```

---

### Post by vasa1 on 2011-11-28
Is it possible that you also need to delete (or at least rename) [FONT="Fixedsys"].libreoffice[/FONT] in your home folder? Purging won't remove this folder, IIRC.

---

### Post by Leo Reijnen on 2011-11-28
> **BC59 said:**
> Try this

```

sudo add-apt-repository ppa:libreoffice/ppa

sudo apt-get update

sudo apt-get install --reinstall libreoffice 

sudo apt-get install libreoffice-gnome

sudo apt-get install language-support-en


```
apt-get update says, among a lot of 'get' and 'hit':

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                      
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                
  404  Not Found

and ends with: 
W: Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

apt-get install --reinstall libreoffice  gives a W:Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) oneiric/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages)

I continued anyway.


getting libregnome seems to work, but also says: 
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 57543 package 'virtualbox-3.1':
 error in Version string '3.1.0-55467_Ubuntu_karmic': invalid character in revision number

Strange, since I purged VirtualBox.

 apt-get install language-support-en gives:
Package language-support-en is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'language-support-en' has no installation candidate

---

### Post by BC59 on 2011-11-28
Well let's see now what to do, because with all this, your system is confused.

Go to **Software Sources**, which in 10.10 are (if I remember well) part of Update Manager. From there in the tab **Other Software**, try to edit the repositories of Oneiric to your version, which is Maverick.

So click once on each on of the repositories

[http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources
[http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages 

and then from the menu below click **Edit**.
From the new menu on the position **Distribution** change Oneiric to Maverick

Then uncheck each one of the repositories

[http://ppa.launchpad.net/openoffice-...source/Sources](http://ppa.launchpad.net/openoffice-...source/Sources)
[http://ppa.launchpad.net/openoffice-...-i386/Packages](http://ppa.launchpad.net/openoffice-...-i386/Packages)

Then click OK and close.

After that write on a terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Leo Reijnen on 2011-11-28
Thanks BC59 for hanging in there for me! It is much appreciated. I'll try this out tonight; have to do some 'real' work now, but will report the results. - Leo

---

### Post by Leo Reijnen on 2011-11-28
BC59, you are a genius! LibreOffice is working like a charm now!

I did get this warning after running the second instance of:
sudo apt-get update && sudo apt-get upgrade
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) oneiric/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

The first time I got more errors, but then I edited the "Maverick" to "maverick".

So, thanks again for helping me solve this one. I'll be posting my next problem in the "Networking section". My mounts in fstab no longer work; I think because my username is now my full name - including a space, always a bad idea - and mount wants to see user leo who is no longer there.

---

### Post by BC59 on 2011-11-28
This is good news!

Please now mark the thread as solved from the thread tools.

---

