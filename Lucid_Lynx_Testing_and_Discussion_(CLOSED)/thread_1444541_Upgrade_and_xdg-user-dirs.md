---
title: "Upgrade and xdg-user-dirs"
date: 2010-04-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tom.swartz07 on 2010-04-01
Hi all, 

I have a pressing question. I recently ran through the updates to Lucid, and Im stuck. During the upgrade, I got the error 

```
E: /var/cache/apt/archives/xdg-user-dirs_0.12-0ubuntu1_amd64.deb: unable to stat `./usr/share/locale/be/LC_MESSAGES/xdg-user-dirs.mo' (which I was about to install)
```

and then the distribution updater quit. 

Now, when I try to update the remainder of the packages from Synaptic, I keep getting the same error when it hits the xdg package.


What can I do to solve this conundrum? Any help is greatly appreciated!!

---

### Post by tom.swartz07 on 2010-04-02
Bump?

---

### Post by tom.swartz07 on 2010-04-02
If it makes any difference, I CANNOT remove or re-install the package xdg-user-dirs. It keeps throwing an error. 

Any idea as to what is causing this?

```
tom@karmic-laptop:~$ sudo apt-get upgrade 
[sudo] password for tom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  xdg-user-dirs
The following packages have been kept back:
  gstreamer0.10-plugins-bad
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 1,008kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 296497 files and directories currently installed.)
Removing xdg-user-dirs ...
dpkg: error processing xdg-user-dirs (--remove):
 cannot remove `/usr/share/locale/be/LC_MESSAGES/xdg-user-dirs.mo': Input/output error
Errors were encountered while processing:
 xdg-user-dirs
E: Sub-process /usr/bin/dpkg returned an error code (1)
tom@karmic-laptop:~$ 

```

---

### Post by Reiger on 2010-04-02
You can probably use dpkg with a --force- parameter to rectify xdg thing. That, however is not such a good idea if you are upgrading from 9.10 to 10.04; in that case it is much better to back up your old files from 9.10 and wipe that install in favour of 10.04.

FWIW: the XDG package is a package that provides applications/desktop environments with a way to recognize default locations for various file types. By default it specifies the directories ~/Documents ~/Music ~/Videos and so on.

---

### Post by tom.swartz07 on 2010-04-03
> **Reiger said:**
> You can probably use dpkg with a --force- parameter to rectify xdg thing. That, however is not such a good idea if you are upgrading from 9.10 to 10.04; in that case it is much better to back up your old files from 9.10 and wipe that install in favour of 10.04.

FWIW: the XDG package is a package that provides applications/desktop environments with a way to recognize default locations for various file types. By default it specifies the directories ~/Documents ~/Music ~/Videos and so on.

Ill try to force it.
See, the thing is- Im fully upgraded to 10.04, the only broken package is this xdg one. All of my other packages and applications are working amazingly well!

Ill post back with any changes after I force it.

---

### Post by tom.swartz07 on 2010-04-03
EDIT: Upon investigating further, apt wants to fully REMOVE xdg. I tried to force-yes, and it still threw the error.

I tried to force version from synaptic to upgrade it to the Lucid version, but it still returns the same error mentioned above. 

Perhaps sitting on the update for a few weeks will allow itself to iron out when other updates are built up around it?

---

### Post by seeker5528 on 2010-04-03
> **tom.swartz07 said:**
> 
```
dpkg: error processing xdg-user-dirs (--remove):
 cannot remove `/usr/share/locale/be/LC_MESSAGES/xdg-user-dirs.mo': Input/output error

```

Having an 'Input/output' would typically lead me to suspect the hard disk, and do some disk checking, before moving on to other things.

Usually I would start with the HDD testing utility from the company that put out the hard drive, usually available as a download from their web site, if it doesn't identify a problem, then boot from the Ubuntu live CD and run fsck from there.

Later, Seeker

---

### Post by tom.swartz07 on 2010-04-03
> **seeker5528 said:**
> Having an 'Input/output' would typically lead me to suspect the hard disk, and do some disk checking, before moving on to other things.

Usually I would start with the HDD testing utility from the company that put out the hard drive, usually available as a download from their web site, if it doesn't identify a problem, then boot from the Ubuntu live CD and run fsck from there.

Later, Seeker

SON OF A BEESTING!

so, are you telling me that my replacement drive (for one that failed before) is beginning to go out, or is it that the sector just stuck?

---

### Post by seeker5528 on 2010-04-05
> **tom.swartz07 said:**
> SON OF A BEESTING!

so, are you telling me that my replacement drive (for one that failed before) is beginning to go out, or is it that the sector just stuck?

It's possible that it could be something bad that happened to the file or file system and not a hardware error. If you have messed with partitions, cloning, resizing, etc.. and somehow ended up with a situation where the system things the file system is bigger than the partition, that could do it.

So while I am highly suspicious of the hardware when I see any kind of input/output errors, it shouldn't automatically be taken to mean that.

Also hard drives have spare good sectors in reserve, so when a sector goes bad one of the spares gets mapped in, but this only happens on a write operation, so it could just be a situation where it needs this write operation to map out a bad sector and then it would be fine again.

Sometimes the utility from the maker of the HDD will provide a function to to fix errors, which can be used, then running the test again will tell you if the drive is OK or not. Usually I only use try these fix options if the number of bad sectors is in the single digits.

If there is not an option to fix in the utility from the disk maker, and the number of bad sectors is low enough to thing a write might fix it, you might do an fsck, copy the directory and/or files in question, then move them back, then run the test utility again. Usually my preference is to copy the hdd with ddrescue (ddrescue /source /destination)

```
ddrescue /dev/sda /dev/sdb
```

Then wipe the disk with [dban](http://www.dban.org/download), which is also available as a boot option on [System Rescue CD](http://www.sysresccd.org/Download)

Then test again.

Then copy the stuff back again if it tests OK.

There is always potential to lose stuff, so it is always good to back up stuff that is important to you before attempting these things.

Later, Seeker

---

### Post by tom.swartz07 on 2010-04-06
> **seeker5528 said:**
> It's possible that it could be something bad that happened to the file or file system and not a hardware error. If you have messed with partitions, cloning, resizing, etc.. and somehow ended up with a situation where the system things the file system is bigger than the partition, that could do it.

So while I am highly suspicious of the hardware when I see any kind of input/output errors, it shouldn't automatically be taken to mean that.

Also hard drives have spare good sectors in reserve, so when a sector goes bad one of the spares gets mapped in, but this only happens on a write operation, so it could just be a situation where it needs this write operation to map out a bad sector and then it would be fine again.

Sometimes the utility from the maker of the HDD will provide a function to to fix errors, which can be used, then running the test again will tell you if the drive is OK or not. Usually I only use try these fix options if the number of bad sectors is in the single digits.

If there is not an option to fix in the utility from the disk maker, and the number of bad sectors is low enough to thing a write might fix it, you might do an fsck, copy the directory and/or files in question, then move them back, then run the test utility again. Usually my preference is to copy the hdd with ddrescue (ddrescue /source /destination)

```
ddrescue /dev/sda /dev/sdb
```

Then wipe the disk with [dban](http://www.dban.org/download), which is also available as a boot option on [System Rescue CD](http://www.sysresccd.org/Download)

Then test again.

Then copy the stuff back again if it tests OK.

There is always potential to lose stuff, so it is always good to back up stuff that is important to you before attempting these things.

Later, Seeker

Its all good, I regularly back up my entire system onto several different drives using rsync. I was just more frustrated about the fact that it would be the 2nd drive in under 6 months that borked.



I was able to work around the difficulty by simply re-installing. I had some major tweaks from Karmic that were causing problems in Lucid, so I decided to split the difference and re-install.


NOTE: Before I re-installed, I was able to get rid of the package when the automatic fsck ran. It caught the bad sector there and got rid of the problem. I still re-installed after that, but its good to note.


And with that; all thats left is my signature. ):P

---

