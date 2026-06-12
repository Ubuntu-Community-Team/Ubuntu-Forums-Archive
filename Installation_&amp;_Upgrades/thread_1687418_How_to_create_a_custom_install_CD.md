---
title: "How to create a custom install CD?"
date: 2011-02-13
forum: Installation &amp; Upgrades
---

### Post by Shiryu on 2011-02-13
Hello.
I need to create a custom Kubuntu (KDE) alternate CD to install on multiple computers. I do not want a live CD.

I need to:
-remove some useless packages
-add some useful packages
-remove other languages texts and packages
-add the rest of my local language packages that the system asks to install when it starts at first time
-add more repositories
-run a bash script after everything be installed

Thanks

---

### Post by Jguy on 2011-02-13
> **Shiryu said:**
> Hello.
I need to create a custom Kubuntu (KDE) alternate CD to install on multiple computers. I do not want a live CD.

I need to:
-remove some useless packages
-add some useful packages
-remove other languages texts and packages
-add the rest of my local language packages that the system asks to install when it starts at first time
-add more repositories
-run a bash script after everything be installed

Thanks

I too would like some assistance with this. Is there any good resources online anywhere that will help me/us accomplish this goal?

Along the same lines, is there a way that I can make the installer skip all the questions and go straight to installing? Like..the timezone, partitioning, Keyboard selections, and sudo user/password information? All I really need to customise between machines is the host name. I need to install the same exact thing on like..36 PC's (so far) and I don't/won't have a whole lot of time or manpower to do it.

After installation, upon first boot, I want to run a bash script that will install the packages we need, add the non-sudo user and set some settings in firefox and other applications to do certain things. The script doesn't have to run automatically, but if it could be ran during installation, that would be super nifty.

If you can provide any help, that would be terrific. I am not using kubuntu, I am using xubuntu 32 bit 10.04.

Again, thanks for any help!

---

### Post by inobe on 2011-02-13
hey guys, remastersys?

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

it's been a long time since i used it, i'm sure it's a lot easier to use now.

---

### Post by kn0w-b1nary on 2011-02-13
Check this out:
[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

---

### Post by lepadatu.lucian on 2012-02-06
The 2 suggested methods work very well. 

With remastersys you can create a live iso image using an existing installation. You can include the settings of an user as the default settings for new users to be created. You can read more on the site in the link above (provided by inobe) and you don't really need to use the live option of the image so this is one choice. But you won't have the characteristics of an alternate CD (such as LVM and stuff).

Using a preseed file (as suggested in the second link from kn0w-b1nary)you can run a bash script after everything be installed and can give all the answers of the installer to be automatically filled in. You can automatically install or remove packages. This is however a little more time consuming (to create the preseed file I mean).

There is a third choice, using Ubuntu Customization Kit but i didn't use it myself so i can't say what it is capable of (I tested the first 2 and they work really well).

---

### Post by isandor on 2012-04-25
Hi,

I too have a problem doing customization. I followed the route described at [https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization) but having problems removing packages. 
Let's have a 'simple' example:
I want to make an install CD (no, not Live CD) that has OpenOffice.org as an install option. I would make an office-desktop task, that would be similar to ubuntu-desktop but with OpenOffice.org instead of LibreOffice (which is now the default office suite). 
This way, when the users try to install my distro, they can choose to install either LibreOffice (choosing ubuntu-desktop) or OpenOffice.org (choosing office-desktop). 
I was able to create the task, but that can only be installed when the operating system is already on the machine, not at initial install. As a workaround, I could remove LibreOffice and install OpenOffice.org instead during install time, but in that case the install time would be longer. 
Anyway, this is not the solution I am seeking.

During initial install there are a number of tasks to choose from and this list is further extended after the system is installed. 
Basically what I would like to do is customize the list and contents of the tasks displayed during system installation.

Can you point to any sources where this is properly described?

Thanks in advance for the help.

Imre

---

