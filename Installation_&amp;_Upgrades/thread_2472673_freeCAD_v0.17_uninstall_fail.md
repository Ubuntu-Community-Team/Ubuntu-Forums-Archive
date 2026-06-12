---
title: "freeCAD v0.17 uninstall fail"
date: 2022-03-08
forum: Installation &amp; Upgrades
---

### Post by codolom on 2022-03-08
Hi,
I have to install a newer version of freeCAD (because of bug).  Version 0.17 is installed on my ubuntu 20.04. At the package list you can actually found v.018. This cannot simply upgrade v0.17, complete uninstall and install needed.

```
$ sudo apt remove/purge freecad
```


..."freecad" package isn't installed on your system, blah-blah.

I've checked ubuntu repositories, and there is no v0.17. It might cause the problem, I think.

How can I uninstall this app?

Thanks for answers.

---

### Post by MAFoElffen on 2022-03-08
The Command you posted should have been 
```

sudo apt remove --purge freecad

```
Did you try that?

---

### Post by codolom on 2022-03-08
"freecad" package is not installed...

---

### Post by deadflowr on 2022-03-08
How did you install it in the first place? Do you remember?
Freecad is available as a deb/apt package, a snap package, a flatpak package, and an appimage package on/for Ubuntu.

---

### Post by codolom on 2022-03-08
> **deadflowr said:**
> How did you install it in the first place? Do you remember?
Freecad is available as a deb/apt package, a snap package, a flatpak package, and an appimage package on/for Ubuntu.

Normal way, from package list.
```
$ sudo apt install freecad
```

---

### Post by deadflowr on 2022-03-08
Look at what dpkg shows
```
dpkg -l | grep freecad
```
also look at what current apt policy shows
```
apt policy freecad
```

Since you state the package is saying not installed I expect the dpkg output to be empty,
but the the apt policy output should show something maybe useful.


Edit: Was this an upgraded release from an earlier version of Ubuntu?

---

### Post by codolom on 2022-03-08
> **deadflowr said:**
> Look at what dpkg shows
```
dpkg -l | grep freecad
```
also look at what current apt policy shows
```
apt policy freecad
```

Since you state the package is saying not installed I expect the dpkg output to be empty,
but the the apt policy output should show something maybe useful.


Edit: Was this an upgraded release from an earlier version of Ubuntu?

I've tried, but:
```

$ sudo dpkg -l | grep freecad
null result
$ sudo apt policy freecad
installed: no

```

There is no available v0.17 package in package list.

---

### Post by codolom on 2022-03-08
> **deadflowr said:**
> Look at what dpkg shows
```
dpkg -l | grep freecad
```
also look at what current apt policy shows
```
apt policy freecad
```

Since you state the package is saying not installed I expect the dpkg output to be empty,
but the the apt policy output should show something maybe useful.


Edit: Was this an upgraded release from an earlier version of Ubuntu?

For last question: Maybe it was upgraded to this version one time. Not sure, cause I don't check every upgrade. Sometimes I've just aggree (for example: oh, there is new version of browser. OK, leave me alone).

---

### Post by MAFoElffen on 2022-03-08
If you ran the UbuntuForums 'system-info' script in my signature line... It would show us all your repo's and PPA's in your sources.list and sources.d... Then at the end, will list all manually installed packages... That is why this tool exists, to help helpers see what they are recommending solutions for... Please help us to be able to help you.

There is also a description for it in the ["New To Ubuntu" Section]("https://ubuntuforums.org/forumdisplay.php?f=326") > ["Sticky: "Suggestions to get your support questions answered as quickly as possible."]("https://ubuntuforums.org/showthread.php?t=1422475")

@DeadFlower -- I'm still finishing the Sticky for it in the Test Forum... Feedback is welcomed please.

---

### Post by codolom on 2022-03-08
> **MAFoElffen said:**
> If you ran the UbuntuForums 'system-info' script in my signature line... It would show us all your repo's and PPA's in your sources.list and sources.d... Then at the end, will list all manually installed packages... That is why this tool exists, to help helpers see what they are recommending solutions for... Please help us to be able to help you.

OK, I didn't share mí sources.list, cause I didn't change:

```

more /etc/apt/sources.list | grep ^[a-z]
deb http://hu.archive.ubuntu.com/ubuntu/ focal main restricted
deb http://hu.archive.ubuntu.com/ubuntu/ focal-updates main restricted
deb http://hu.archive.ubuntu.com/ubuntu/ focal universe
deb http://hu.archive.ubuntu.com/ubuntu/ focal-updates universe
deb http://hu.archive.ubuntu.com/ubuntu/ focal multiverse
deb http://hu.archive.ubuntu.com/ubuntu/ focal-updates multiverse
deb http://hu.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu focal-security main restricted
deb http://security.ubuntu.com/ubuntu focal-security universe
deb http://security.ubuntu.com/ubuntu focal-security multiverse

more /etc/apt/sources.list.d/deadsnakes-ubuntu-ppa-bionic.list.distUpgrade | grep ^[a-z]
deb http://ppa.launchpad.net/deadsnakes/ppa/ubuntu bionic main ## for what? maybe nothing

more /etc/apt/sources.list.d/google-chrome.list.distUpgrade | grep ^[a-z]
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main ## google chrome: not relevant

more /etc/apt/sources.list.d/skype-stable.list.distUpgrade | grep ^[a-z]
deb [arch=amd64] https://repo.skype.com/deb stable main ## I never use skype

```

---

### Post by MAFoElffen on 2022-03-08
Since you didn't run the Forum's 'system-info' support script on the other questions we need to see, I'll just post the code as single line commands to answer those...
```

manually_installed=$(mktemp /tmp/ManuallyInstalled-XXXXX)
default_installed=$(mktemp /tmp/DefaultInstalled-XXXXX)
user_installed=$(mktemp /tmp/UserInstalled-XXXXX)
    
# Use apt-mark to list all packages marked as manually installed. 
apt-mark showmanual | sort -u > $manually_installed

# Check to see if default installed list exists. For prebuilt system images, it does not exist
if [ -f /var/log/installer/initial-status.gz ]; then gzip -dc /var/log/installer/initial-status.gz 2> /dev/null | sed -n 's/^Package: //p' | sort -u > $default_installed; else touch $default_installed; fi
 
# Use compare, to exclude those defaults that are unique, AND exclude defaults that are presently marked as manually installed. (Those 'may' have been changed.)  
comm -23 $manually_installed $default_installed > $user_installed

# Print the list in two columns
awk 'NF' $user_installed | pr -2T  # You can remove the pr filter on this to keep output in a single column...

# Remove the temporary files
rm -f $manually_installed
rm -f $default_installed

# Optional to either remove or copy this file somewhere (before removing it) for your records...
# This information is handy if you want to migrate clean, and install what you had... Or have to resurrect your system after a crash.
rm -f $user_installed

```
This will display two columns of all the packages that you have marked as manually installed since the system was installed...

On a release upgrade from earlier
```

if [ -f /var/log/dist-upgrade/apt.log ]; then drg_date=$(sudo egrep -m 1 'Log Time' /var/log/dist-upgrade/apt.log | awk '{"Do-Release-Upgrade Date: "$3 }' ); echo -e "This system was upgraded from an earlier release on: $drg_date"; else echo -e "Do-Release-Upgrade Date: This system may have not had a 'Release Upgrade' through 'do-release-upgrade'"; fi

```
That will show if it ever had a do-release-upgrade and if so, on what date.

---

### Post by codolom on 2022-03-09
> **MAFoElffen said:**
> Since you didn't run the Forum's 'system-info' support script on the other questions we need to see, I'll just post the code as single line commands to answer those...
```

manually_installed=$(mktemp /tmp/ManuallyInstalled-XXXXX)
default_installed=$(mktemp /tmp/DefaultInstalled-XXXXX)
user_installed=$(mktemp /tmp/UserInstalled-XXXXX)
    
# Use apt-mark to list all packages marked as manually installed. 
apt-mark showmanual | sort -u > $manually_installed

# Check to see if default installed list exists. For prebuilt system images, it does not exist
if [ -f /var/log/installer/initial-status.gz ]; then gzip -dc /var/log/installer/initial-status.gz 2> /dev/null | sed -n 's/^Package: //p' | sort -u > $default_installed; else touch $default_installed; fi
 
# Use compare, to exclude those defaults that are unique, AND exclude defaults that are presently marked as manually installed. (Those 'may' have been changed.)  
comm -23 $manually_installed $default_installed > $user_installed

# Print the list in two columns
awk 'NF' $user_installed | pr -2T  # You can remove the pr filter on this to keep output in a single column...

# Remove the temporary files
rm -f $manually_installed
rm -f $default_installed

# Optional to either remove or copy this file somewhere (before removing it) for your records...
# This information is handy if you want to migrate clean, and install what you had... Or have to resurrect your system after a crash.
rm -f $user_installed

```
This will display two columns of all the packages that you have marked as manually installed since the system was installed...

On a release upgrade from earlier
```

if [ -f /var/log/dist-upgrade/apt.log ]; then drg_date=$(sudo egrep -m 1 'Log Time' /var/log/dist-upgrade/apt.log | awk '{"Do-Release-Upgrade Date: "$3 }' ); echo -e "This system was upgraded from an earlier release on: $drg_date"; else echo -e "Do-Release-Upgrade Date: This system may have not had a 'Release Upgrade' through 'do-release-upgrade'"; fi

```
That will show if it ever had a do-release-upgrade and if so, on what date.

I've checked all of theese. freeCAD isn't installed, but is in the menu, I can run and use. THERE IS NO INSTALLED VERSION IN MY SYS. Nowhere. 

[https://paste.ubuntu.com/p/KVzVhS49TZ/](https://paste.ubuntu.com/p/KVzVhS49TZ/)

Maybe it can be deleted by hand... I mean if I delete icon, from menu and all of program directories, than I get rid of this buggy program.

---

### Post by MAFoElffen on 2022-03-09
If you can run it, it's installed somehow.

I read the report.Thank you. I didn't see anything out the the ordinary, but... I'm the author of that for the Forum... And I am the Admin it's repo's at the Forum's GitHub Repo's... I am very familiar with what it says, asks, and what it doesn't...

When I wrote it, I filtered out Snaps loop devices, because they cluttered things up, and my testers didn't think that Showing Snaps apps was relevant... LOL. In your case it might be. Since it was not a packaged installation, there are only a few other ways it could be installed. I will check into it on their website and on Snaps...

Those ways left, would be that it was installed through a script that compiled and installed it, that is was downloaded and can run standalone from wherever it was unarchived, or as a Snap App...

EDIT: Of my educated guesses in the previous paragraph, it cam in 4 forms: As a repo package (which you do not have). As an executable app image, downloaded form their website. As a Snap app form the Snap Store. As a F;at[ack app, which is not likely how you got it.

1:30 AM here now, Let me look at those two methods to see what the next path to determine which of those two ways you have it and the easiest way to remove it for those to methods.

FYI- You installed from the 18.04.1 ISO on November 1, 2018. They say they have been using AppImages since sometime before July 7, 2019... Since that date, they say they recognized that downloading from their website took some patience.

---

### Post by codolom on 2022-03-09
> **MAFoElffen said:**
> If you can run it, it's installed somehow.

I read the report.Thank you. I didn't see anything out the the ordinary, but... I'm the author of that for the Forum... And I am the Admin it's repo's at the Forum's GitHub Repo's... I am very familiar with what it says, asks, and what it doesn't...

When I wrote it, I filtered out Snaps loop devices, because they cluttered things up, and my testers didn't think that Showing Snaps apps was relevant... LOL. In your case it might be. Since it was not a packaged installation, there are only a few other ways it could be installed. I will check into it on their website and on Snaps...

Those ways left, would be that it was installed through a script that compiled and installed it, that is was downloaded and can run standalone from wherever it was unarchived, or as a Snap App...

I've checked snap also before and it was not installed by. 
But I had an idea before this answer. I remember I've used apt, but it is possible I had to use alternative way... I use apt at first ALMOST all the time, but sometimes I get a useless app. Than other way needed. In my file system I've found a downloaded file. It is called FreeCAD-0.17.13541.9948ee4.glibc2.17-x86_64.AppImage Wow! I've checked menu icon settings: points directly this file. This must be the reason. But I DO NOT REMEMBER, that I've added program icon to my main menu by hand... Strange. Perhaps I've just forgotten the installation method, but anyway I'm thinking I do not remember I have installed menu icon by hand any time.

What do you think?

---

### Post by MAFoElffen on 2022-03-09
That is the AppImage... You found it!!! Remove the menu item, then move that file to your trash... If all goes well, then delete forever. 

That was downloaded from their website as an AppImage. (standalone executable.) Since it is self-contained and standlaone, there is nothing else connected to it,in the way of dependencies or other things.

---

### Post by sebtec100 on 2023-02-27
Hi 
I know this topic is already marked as 'Solved' but maybe someone will find this info useful.

When it comes to FreeCAD AppImage, all versions can be found on their official github repo here:
[https://github.com/FreeCAD/FreeCAD/releases](https://github.com/FreeCAD/FreeCAD/releases)

Same with LibreCAD:
[https://github.com/LibreCAD/LibreCAD/releases](https://github.com/LibreCAD/LibreCAD/releases)

---

