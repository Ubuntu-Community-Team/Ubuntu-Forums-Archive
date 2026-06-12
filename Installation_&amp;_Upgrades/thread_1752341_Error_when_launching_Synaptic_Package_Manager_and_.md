---
title: "Error when launching Synaptic Package Manager and Ubuntu Software Center"
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by Ksig on 2011-05-07
Hi everybody,

Ubuntu 11.04 was working fine and then when I went to open Synaptic, I got the following error:

An error occured

The following details are provided:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/viewizard.com_linux_debian_en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

I get this error when I try to load Synaptic.  In addition to that, the Ubuntu Software Center does not work when I try to search for and/or look at applications.  Can somebody please help me out?

---

### Post by drs305 on 2011-05-07
Try moving the offending file to your Desktop so it isn't referenced. Once things are working again you can delete it.
```

sudo mv /var/lib/apt/lists/viewizard.com_linux_debian_en ~/Desktop/viewizard.com_linux_debian_en
sudo apt-get update
```

If it works, then remove the bad file with:
```
sudo chown <yourusername> ~/Desktop/viewizard.com_linux_debian_en
rm ~/Desktop/viewizard.com_linux_debian_en
```

---

### Post by Ksig on 2011-05-07
Thank you for your quick response!

I moved it to the desktop with the first command, tried to launch Synaptic again and got the same error.

---

### Post by drs305 on 2011-05-07
> **Ksig said:**
> Thank you for your quick response!

I moved it to the desktop with the first command, tried to launch Synaptic again and got the same error.

Did "sudo apt-get update" work? If not, let's first put the file back.
```
sudo mv ~/Desktop/viewizard.com_linux_debian_en /var/lib/apt/lists/viewizard.com_linux_debian_en
```

Please post the contents of your /etc/apt/sources.list file and we can try to disable the problem repository(s).

You could also try to use the older status file if it is the status file causing the error:
```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update
```

---

### Post by Ksig on 2011-05-07
No, the sudo apt-get update did not help either.  I still have the same problem.  I just put the file back.

Now please forgive me because I am newer to Ubuntu/Linux... I have a sources.list and a sources.list.save file, which one do you want?  And also, how do I put text into the new text blocks like the terminal code of yours is in?

---

### Post by drs305 on 2011-05-07
> **Ksig said:**
> No, the sudo apt-get update did not help either.  I still have the same problem.  I just put the file back.

Now please forgive me because I am newer to Ubuntu/Linux... I have a sources.list and a sources.list.save file, which one do you want?  And also, how do I put text into the new text blocks like the terminal code of yours is in?

Let's start with the sources.list file. You might also look in the /etc/apt/sources.list.d folder and see what is lurking therein.

When creating the post, you press the # icon in the post's menubar. That generates [noparse]```
 
```[/noparse] tags. You paste the contents between the two tags. Thanks for asking.  ;-)

---

### Post by Ksig on 2011-05-07
Ok thanks!  (I am assuming I am doing this right).  When I click on the file, it asks for authentication and then opens the software sources window with the tabs: Ubuntu Software, Other Software, Updates, Authentication, Statistics.  So I right clicked on it and opened it as a text file and copied the text and pasted below.

```
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main
## Viewizard Games repository
deb http://viewizard.com/linux debian/
```

---

### Post by drs305 on 2011-05-07
> **Ksig said:**
> Ok thanks!  (I am assuming I am doing this right).  When I click on the file, it asks for authentication and then opens the software sources window with the tabs: Ubuntu Software, Other Software, Updates, Authentication, Statistics.  So I right clicked on it and opened it as a text file and copied the text and pasted below.


Ok, I used your sources.list file and it didn't generate any errors. Since you found a way to open Software Sources, on each page untick all the entries then reselect them after a moment or two. Each time you deselect one, it removes the entry from your system. When you select it again, that repository is added back in. It should clear any errors. Once you have accomplished this in each tab of Software Sources and close the tabs. If you can, RELOAD, or run "sudo apt-get update".

**Added:**
If the problem persists, the next step is to completely remove /var/lib/apt/lists, which we can do by renaming it. It will be regenerated when you run the second command:
```
sudo mv /var/lib/apt/lists /var/lib/apt/lists.bad
sudo apt-get update
```

---

### Post by Ksig on 2011-05-07
Ok I opened the Software Sources and and ticked/ticked everything and then clicked "reload" when I closed it.  It did some work and then after it finished, I got the following error message:
```
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.


GPG error: http://packages.medibuntu.org natty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783GPG error: http://viewizard.com debian/ InRelease: The following signatures were invalid: NODATA 1 NODATA 2Failed to fetch http://ppa.launchpad.net/tulatrix/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found
Failed to fetch http://ppa.launchpad.net/tulatrix/ppa/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead.

```

After I clicked Ok or whatever it said, the next error message came up:

```
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/viewizard.com_linux_debian_en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
```

I then tried Synaptic again, but with the same error message.  After that, I used the terminal to rename and update and tried Synaptic, but got the same error message again.

---

### Post by matt_symes on 2011-05-07
Hi

Try this

```
sudo rm -f /var/lib/apt/lists/*
```

Enter your password. It will not be echoed to the screen.

Then type

```
sudo apt-get update
```

to regenerate your list info.

Kind regards

---

### Post by Ksig on 2011-05-07
Hi Matt,

I copied that into the terminal and got this error:

```
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory

```

---

### Post by matt_symes on 2011-05-07
Hi

Not a problem. Try

```
sudo apt-get update
```

Kind regards

---

### Post by Ksig on 2011-05-07
No, I still have an error when starting Synaptic after updating.

---

### Post by matt_symes on 2011-05-07
Hi 

What's the error now with synaptic ? Did you get any errors after the apt-get command ?

Kind regards

---

### Post by Ksig on 2011-05-07
Hey guys,

I just fixed it.  I went back to the "Other Software" tab in the Software Sources and deselected "http://viewizard.com/linux debian/".  I can now get into Synaptic and Software Center.

Do you think this could be because in that file/source, it says "/linux debian/" and is not working right because there is a space between "linux" and "debian"?  I am somewhat new to Linux, but do know that I can't really have spaces in file names when working around in the terminal or else it doesn't work.

---

### Post by Ksig on 2011-05-07
Matt,

It was the same error I had been getting from the beginning.

---

### Post by matt_symes on 2011-05-07
Hi

> **Ksig said:**
> Hey guys,

I just fixed it.  I went back to the "Other Software" tab in the Software Sources and deselected "http://viewizard.com/linux debian/".  I can now get into Synaptic and Software Center.

Do you think this could be because in that file/source, it says "/linux debian/" and is not working right because there is a space between "linux" and "debian"?  I am somewhat new to Linux, but do know that I can't really have spaces in file names when working around in the terminal or else it doesn't work.

If you are trying to get here 

[http://viewizard.com/linux/debian/](http://viewizard.com/linux/debian/)

then yes. Remove the space and add a /. They are Debian packages mind.

Kind regards

---

### Post by drs305 on 2011-05-08
You can clean up the message about medibuntu by importing the security key with this command:
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0C5A2783

```

When you don't have any more issues with this matter, please mark the thread SOLVED via the thread tools link at the top right of the first post.

Happy Ubuntu-ing !

---

