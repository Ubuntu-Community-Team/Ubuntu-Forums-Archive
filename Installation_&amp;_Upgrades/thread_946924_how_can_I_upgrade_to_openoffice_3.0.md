---
title: "how can I upgrade to openoffice 3.0?"
date: 2008-10-13
forum: Installation &amp; Upgrades
---

### Post by yinglcs2 on 2008-10-13
Hi, 

I am using Ubuntu 8.04.1.
And openoffice 3.0 is release. 
What is the easiest way for me to upgrade to it?

The [http://www.openoffice.org/](http://www.openoffice.org/) has a DEB download, but what should I do so that my old copy is safely removed and new copy is installed with all dependencies?

Thank you.

---

### Post by keltose on 2008-10-13
I am looking for the same answer.  I really don't understand the tar.gz stuff in linux.  I hate to do the comand cd, why can't it just install?

---

### Post by Partyboi2 on 2008-10-13
> **yinglcs2 said:**
> Hi, 

I am using Ubuntu 8.04.1.
And openoffice 3.0 is release. 
What is the easiest way for me to upgrade to it?

The [http://www.openoffice.org/](http://www.openoffice.org/) has a DEB download, but what should I do so that my old copy is safely removed and new copy is installed with all dependencies?

Thank you.
Open up synaptic package manager and  search for the old oo packges and removed them. Then install the new version.

---

### Post by Partyboi2 on 2008-10-13
> **keltose said:**
> I am looking for the same answer.  I really don't understand the tar.gz stuff in linux.  I hate to do the comand cd, why can't it just install?
You would need to extract the tar.gz file so that you had a folder with the deb package(s)
You can do that by right clicking on it and choosing to extract.

---

### Post by disastraus on 2008-10-13
Keltose if you really don't want to use command line then just hang out for a while and wait to see if any good person comes up with a solution for you.  You might have to be patient though as solutions don't always come on the first day of release!

---

### Post by go2dell on 2008-10-13
Debs are available from [another thread]("http://ubuntuforums.org/showpost.php?p=5955617&postcount=145").

**edit:**  These are still RC4; it will take some time before the final release is available.  You can monitor status [here]("https://launchpad.net/~openoffice-pkgs/+archive").

---

### Post by sweet_mackerel on 2008-10-14
follow the steps of this tutorial with the additional step 6

[Tutorial] Installing OOo on Ubuntu, Debian and Co.
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)
Postby Hagar de l'Est 


3. Extract the tarball in your home directory (or any other directory you want)

Open a terminal (you should be directly in your home directory) and :

Code: Select all   Expand viewCollapse view
    tar -vxzf filename
 filename = OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz

You should see a new folder, say OOo_inst_folder.
 OOo_inst_folder = OOO300_m9_native_packed-1_en-US.9358

4. Install the created .debs

Code: Select all   Expand viewCollapse view
    cd OOo_inst_folder/DEBS
    sudo dpkg -i *.deb


5. Update the Gnome menu
Go to the desktop integration subfolder.

Code: Select all   Expand viewCollapse view
    cd desktop-integration

6. go to synaptic package manager and search for and remove package openoffice org core


Run again the previous installation command.

Code: Select all   Expand viewCollapse view
    sudo dpkg -i *.deb

---

### Post by xaviel on 2008-10-14
Thanks, these steps work great! Except the package to remove in step 6 is openoffice.org-base-core. 

> **sweet_mackerel said:**
> 

6. go to synaptic package manager and search for and remove package openoffice org core



---

### Post by xRes on 2008-10-19
sweet_mackerel - Excellent work, Thank you!

---

### Post by bmeacham on 2009-06-09
When I ran the commands
   cd OOo_inst_folder/DEBS
   sudo dpkg -i *.deb
I got the following error message (actually, this is one of many similar):
   dpkg: error processing ooobasis3.1-base_3.1.0-11_i386.deb (--install):
   package architecture (i386) does not match system (lpia)

What does this mean?  How can I install OO 3.1 on my Dell Vostro A90 (same as Dell Mini 9) running Ubuntu 8.04.02?

---

### Post by Partyboi2 on 2009-06-10
> **bmeacham said:**
> When I ran the commands
   cd OOo_inst_folder/DEBS
   sudo dpkg -i *.deb
I got the following error message (actually, this is one of many similar):
   dpkg: error processing ooobasis3.1-base_3.1.0-11_i386.deb (--install):
   package architecture (i386) does not match system (lpia)

What does this mean?  How can I install OO 3.1 on my Dell Vostro A90 (same as Dell Mini 9) running Ubuntu 8.04.02?
Hi, you can add a 3rd party repo that has lpia packages and install open office 3.1. To do this open a terminal and
```
echo deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) hardy main | sudo tee -a /etc/apt/sources.list
```
```
sudo apt-get update && sudo apt-get upgrade
```

---

