---
title: "Install tar.bz2 program"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by Benchrest on 2010-06-14
Sunbird has been dropped from the repositories for Lucid Lynx.  I need to install for my most critical customer (little woman) . I have downloaded sunbird-1.0b1.tar.bz2 , extracted the files and put the sunbird folder in .mozilla where it should be.  The program works if I double click on the shell script. 
However how do I get the system to know of this program? How do I get it into the Applications list so it can be started easily?

---

### Post by lechien73 on 2010-06-14
[LIST=1]
[*]Right click on the **Applications** menu, and select **Edit Menus**.

[*]Click on the parent folder (I selected **Accessories**), then choose **New Item**.

[*]Give it a name (i.e.: Sunbird), and type in the full path to the executable. For me it would be ```
/home/lechien/sunbird/sunbird
```

[*]If you want to give it a nice icon, then click on the existing icon in the **New Item** dialog. It will open a browser window. I browsed to the **icons** subdirectory under the **sunbird** directory, and chose *mozicon128.png*
[/LIST]

---

### Post by Benchrest on 2010-06-14
That worked! thankyou

---

### Post by Benchrest on 2010-06-15
That fix was only for half my problem. I have the program Sunbird in Applications/Office But the program requires the directory for it to be found. Now other programs such as Open Office do not have the directory information. 

It would seem to me somewhere in the system all installed programs might be listed along with their directory information so you don't need to give the directory when executed. 

The problem I am experiencing is I am using Alltray with Sunbird. In my previous system, 9.04 sunbird was installed with synaptic package manager and in Startup Applications I have "alltray sunbird" and the world is good. But that doesn't work with sunbird installed the way I did it. I have tried "alltray /.mozilla/sunbird/sunbird" in Startup applications  and that doesn't work either. 

So by extracting the tar.bz2 file to .mozzila which give me the sunbird  subfolder . Again I can execute sunbird from that folder.

---

### Post by Benchrest on 2010-06-15
alltray /home/userid/.mozilla/sunbird/sunbird  works.  I still am not sure I should have to have the sunbird directory information.  I did not need it on 9.04 where it was installed through synoptic package manager

---

### Post by jre6 on 2010-06-16
> **Benchrest said:**
> alltray /home/userid/.mozilla/sunbird/sunbird  works.  I still am not sure I should have to have the sunbird directory information.  I did not need it on 9.04 where it was installed through synoptic package manager

There is a difference in installing a tar.bz2 (I will refer to it as [tarball]("http://en.wikipedia.org/wiki/Tar_%28file_format%29") from now on) program and installing a program through Synaptic.

The tarball contains all the necessary files, and when you extract it, and click on the Sunbird script (or execute the script through the terminal), the program does not get installed (it is just there but not registered as installed, although you can run it). When you install it through the manager, it downloads the .deb packages, extracts and installs. Then the package management system knows that it is installed. So, you need to know the directory info for the former but not for the latter.

---

