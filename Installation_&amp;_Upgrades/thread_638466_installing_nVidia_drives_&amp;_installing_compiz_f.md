---
title: "installing nVidia drives &amp; installing compiz fusion (PROBLEMS!!! NEED HELP ASAP!!)"
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by shuarma on 2007-12-12
**First problem - Installing nVidia drivers.**
I follow the directions, 

> STEP 1: Review the NVIDIA Software License.

You will need to accept this license prior to downloading any files.

STEP 2: Download the Driver File

Download - NVIDIA-Linux-x86-100.14.19-pkg1.run

SuSE users: please read the SuSE NVIDIA Installer HOWTO before downloading the driver.

STEP 3: Install
Type "sh NVIDIA-Linux-x86-100.14.19-pkg1.run" to install the driver. NVIDIA now provides a utility to assist you with configuration of your X config file. Please see Chapter 3 of the README or run 'man nvidia-xconfig' for details on usage. Instructions for those wishing to edit their X config file by hand can also be found in the README.
But then when I try to complete step 3, I get this problem...

[IMG]http://i19.tinypic.com/82wmvt2.png[/IMG]

What am I doing wrong?

+++++++++++++++++++++++++++++++++++++++

**Second problem - Installing Compiz Fusion.** [(The installation instructions I used)]("http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml")

In the first step, I run into a problem.

[IMG]http://i5.tinypic.com/6ynvxbm.png[/IMG]

When it asks me to type in my password, I go to type it in, and none of the characters show up. I keep trying and trying, but the characters do not show up on the screen, then I press enter, and I type in my password (successfully), but it tells me my password is invalid, when I know I typed in my password correctly.


PLEASE PLEASE HELP ME!

---

### Post by PmDematagoda on 2007-12-12
Ok, here is what you must do:-

1) First you must exit the GUI, do this by doing(Keep in mind that the next commands are done in the CLI, so write them down):-

```
sudo /etc/init.d/gdm stop
```

2) Then navigate to where the fle is found, since it is on the Desktop we move to the Desktop folder:-
```

cd Desktop
```

3) Then execute the file:-
```
sudo sh NVIDIA-Linux-x86-100.14.19-pkg1.run
```

This should start the installer, after the installation is complete, configure the X-server using:-
```

sudo dpkg-reconfigure xserver-xorg
```

Select the driver as Nvidia and select any others you may need. After that is done, do:-
```
sudo /etc/init.d/gdm start
```
which should bring you back to the GUI.

---

### Post by shuarma on 2007-12-12
> **PmDematagoda said:**
> Ok, here is what you must do:-

1) First you must exit the GUI, do this by doing(Keep in mind that the next commands are done in the CLI, so write them down):-

```
sudo /etc/init.d/gdm stop
```
as soon as i type in that first one, i get the password problem.
what do i do?

---

### Post by Partyboi2 on 2007-12-12
You will not see your password being displayed as you type it when using the terminal. If you put it in wrong you will get a message saying
```
Sorry, try again.
```

---

### Post by Dristun101 on 2007-12-12
I've followed this Thread as it helped with the same problem I was having with the Nvidia drivers, yet when I get to the command line 

sh NVIDIA-Linux-x86-100.14.19-pkg1.run

It loads then says it must be loaded through Root, i'm new to Linux and Ubuntu all together so a little help would be awesome.

---

### Post by forestpixie on 2007-12-12
when you're prompted for root use sudo

sudo sh NVIDIA-Linux-x86-100.14.19-pkg1.run

---

### Post by Posterus on 2007-12-13
To install the nvidia graphics card driver you usually go to system-->admin-->restricted drivers  and try enabaling it through there.

and have you changed your password since you've installed? because sometimes some peope may have a problem where they change their log in password but the root password stays the same, if you are POSITIVE you type your password incorrectly then try previous passwords

---

