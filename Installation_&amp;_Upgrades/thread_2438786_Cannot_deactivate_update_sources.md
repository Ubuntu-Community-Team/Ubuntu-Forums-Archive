---
title: "Cannot deactivate update sources"
date: 2020-03-18
forum: Installation &amp; Upgrades
---

### Post by py-ohayo on 2020-03-18
Hello,
Can't uncheck "brown" boxes.
Why ?
Thanks.
[IMG]https://i.postimg.cc/pT9dWC9L/Screenshot-from-2020-03-18-09-58-52.png[/IMG]

---

### Post by TheFu on 2020-03-18
Just a guess, but have all the packages from those repos been uninstalled from the system?
i don't use any gui for package management.

---

### Post by py-ohayo on 2020-03-19
No, for the moment they are still present.
 I'm looking for a way to rid my system of NVIDIA staff (drivers, CUDA, cuDNN).
I haven't paid much attention to version compatibility and in fact my system is contaminated by NVIDIA staff.
The two last items on the image are related to either CUDA either NVIDIA driver ... I don't know yet.
For example in second from the bottom item the number **440.33.01** corresponds to NVIDIA driver version whereas **10-2** corresponds to CUDA version.
The same for bottom item: **418.87.00** - corresponds to driver, and **10-1** to CUDA.
Note that I only have CUDA 10.2 installed, but not CUDA 10.1.

---

### Post by py-ohayo on 2020-03-19
I succeeded to uninstall whole NVIDIA staff.
But the items on the image from the screenshot on my 1st message didn't disappear.
What does it mean ? The drivers aren't completely uninstalled ?
I plan to reinstall NVIDIA tools and am afraid that this will perturb installation or functionality of NVIDIA tools.
How to remove them ?

---

### Post by TheFu on 2020-03-19
All repos are configured in text files under /etc/apt/.
You can comment out the offending lines.  Do not delete them.  Make a backup of any files BEFORE you alter them.

sources.list
and any files in /etc/apt/sources.list.d/ should be checked.

After modifying, run
```
sudo apt update
```
If that finishes without error or warnings, then run:
```
sudo apt upgrade
```

Do not have any other software update tool open/running at the same time your run those commands.

If any packages from the commented out lines are still installed on the system, you'll be in "APT HELL" and updates will fail going forward due to unresolved dependencies.  In a few months, nothing will update.  So be extremely careful to only get the correct lines.

---

### Post by py-ohayo on 2020-03-19
Thanks.
There are only one text file under [FONT=courier new]/etc/apt/[/FONT]: **source.list**.
I checked it and I did not find any of the 3 items shown on the screenshot of my first message.
On the other side I've found 3 **.list** files in[FONT=courier new] /etc/apt/sources.list.d/[/FONT] that correspond to the 3 items shown on the screenshot of my first message.
So, what should I comment/modify ?

---

### Post by py-ohayo on 2020-03-20
> **TheFu said:**
> All repos are configured in text files under /etc/apt/.
You can comment out the offending lines.  Do not delete them.  Make a backup of any files BEFORE you alter them.

In the _only_ text file in the specified location (i.e. file **sources.list** located in **/etc/apt/**) there are no offending lines.
However there are files that sound like "offending". These 3 files are located in **/etc/apt/sources.list.d**:
```
pavel@ALABAMA:/etc/apt/sources.list.d$ ls -la
total 24
drwxr-xr-x 2 root root 4096 mars  11 15:24 .
drwxr-xr-x 7 root root 4096 mars  11 15:24 ..
-rw-r--r-- 1 root root   58 mars   2 14:00 cuda-10-1-local-10.1.243-418.87.00.list
-rw-r--r-- 1 root root   58 mars   2 14:00 cuda-10-1-local-10.1.243-418.87.00.list.save
-rw-r--r-- 1 root root   57 nov.  13 23:40 cuda-10-2-local-10.2.89-440.33.01.list
-rw-r--r-- 1 root root  144 mars   2 14:00 graphics-drivers-ubuntu-ppa-bionic.list

```

Should I rename or remove them ?

Thanks.

---

### Post by CatKiller on 2020-03-20
One of the ways of installing CUDA from Nvidia is to create a local repository of the CUDA packages, and then install from there. That appears to be what you've done. You can either uninstall the package that you used to set up those local repositories (you appear to have done it twice) which should also remove those files and the apt entries, or you can remove all the CUDA stuff (which you say you've done already) and then simply delete the local repositories (the /var/cuda-repo stuff) and the corresponding sources.list.d entries.

---

### Post by TheFu on 2020-03-20
> **py-ohayo said:**
>  
Should I rename or remove them ?

Thanks.

You should .... do what was suggested previously.
> comment out the offending lines. Do not delete them. Make a backup of any files BEFORE you alter them.

---

### Post by Rick St. George on 2020-03-20
As to your first question - I ran into this on a friends computer. Turns out, he was not the Administrator.
Went into Users/Groups and changed him to Administrator, Problem solved.
Did you check? Just saying!

---

### Post by py-ohayo on 2020-03-20
> **TheFu said:**
> You should .... do what was suggested previously.
As I mentioned in my previous message, there is no any related line in the **sources.list**.
And the **sources.list** is the _only_ text file in specified location.
So, nothing to comment !
On the other side, there are files whose names seem "offensive".
In other words, my case is not exactly what you described.

---

### Post by py-ohayo on 2020-03-20
> **CatKiller said:**
> One of the ways of installing CUDA from Nvidia is to create a local repository of the CUDA packages, and then install from there. That appears to be what you've done. You can either uninstall the package that you used to set up those local repositories (you appear to have done it twice) which should also remove those files and the apt entries, or you can remove all the CUDA stuff (which you say you've done already) and then simply delete the local repositories (the /var/cuda-repo stuff) and the corresponding sources.list.d entries.
I purged whole NVIDIA staff.
So, can delete these 3 files ?

---

### Post by py-ohayo on 2020-03-20
> **Rick St. George said:**
> As to your first question - I ran into this on a friends computer. Turns out, he was not the Administrator.
Went into Users/Groups and changed him to Administrator, Problem solved.
Did you check? Just saying!
[COLOR=#ff0000]*Went into Users/Groups*[/COLOR] ... how access it ?
I looked over "Settings" and didn't see Users/Groups.

---

### Post by TheFu on 2020-03-20
> **py-ohayo said:**
> I purged whole NVIDIA staff.
So, can delete these 3 files ?

You can do whatever you want.

The point was to change things until we were 100% certain that no harm was done, while keeping a backout plan.  After a week, then clean up the new changes if everything was still fine.  Was just trying to protect you from mistakes.

Do whatever you want.

---

### Post by py-ohayo on 2020-03-20
> Do whatever you want. 		

Well ... here is your previous message:
> If any packages from the commented out lines are still installed on the  system, you'll be in "APT HELL" and updates will fail going forward due  to unresolved dependencies.  In a few months, nothing will update.  So  be extremely careful to only get the correct lines.

So I put my question differently: can I delete these files without risk of transforming my system in "APT HELL" few days/weeks later ?

---

### Post by deadflowr on 2020-03-20
> **py-ohayo said:**
> [COLOR=#ff0000]*Went into Users/Groups*[/COLOR] ... how access it ?
I looked over "Settings" and didn't see Users/Groups.

Unless you're running an xubuntu or any number of non-Ubuntu desktops, it's not relevant to Ubuntu.
For users in Ubuntu go to Settings > Details. Users will be a listing there.
It doesn't show groups but it will show whether the user is the admin or non-admin user.
It might require unlocking it to see the users status better. Click on the lock icon in the top right corner of the setting window to unlock.

---

### Post by TheFu on 2020-03-20
> **py-ohayo said:**
> Well ... here is your previous message:


So I put my question differently: can I delete these files without risk of transforming my system in "APT HELL" few days/weeks later ?

if all the packages previously installed from those removed repos are removed, then there won't be any issue.  Best to wait a week, see that there aren't any issues, assuming you've backed up the files and commented out any relevant lines inside those files.

Running a full patch cycle shouldn't hurt.
```
sudo apt update
sudo apt upgrade
```
if there are any issues, best to solve them ASAP.

That's how I’d do it.

---

### Post by py-ohayo on 2020-03-20
> For users in Ubuntu go to Settings > Details. Users will be a listing there.
It doesn't show groups but it will show whether the user is the admin or non-admin user.
It might require unlocking it to see the users status better. Click on  the lock icon in the top right corner of the setting window to unlock.
Well, I've created but administrator account ...  but after created it I realized that existing account was also administrator-type although I always use sudo for critical operation.
Nevertheless I remain confused ... if I correctly understood Rick St. George message, administrator can uncheck "unwanted" items via **Software & Update** interface ?
Or I've been mistaken.

---

### Post by deadflowr on 2020-03-20
> **py-ohayo said:**
> Well, I've created but administrator account ...  but after created it I realized that existing account was also administrator-type although I always use sudo for critical operation.
Nevertheless I remain confused ... if I correctly understood Rick St. George message, administrator can uncheck "unwanted" items via **Software & Update** interface ?
Or I've been mistaken.

Perhaps your system isn't activating the password prompt required to enable/disable/add/remove settings.
When you make any action in Software and Updates it requires the admin user password to proceed.
This is a pop up window, and should always be on top of every other window.
Is no prompt showing for you?

---

### Post by py-ohayo on 2020-03-20
> When you make any action in Software and Updates it requires the admin user password to proceed.
When I click on the items that I want to uncheck in Software and Updates, nothing happens - no any pop up window.

---

### Post by deadflowr on 2020-03-20
You might be running into this, or a similarly, random bug/issue:
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1734095]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1734095")
i'm not completely sure it's the same, and do not see any easy to follow fix for it.

Maybe try reinstalling software-properties-gtk
```
sudo apt install --reinstall software-properties-gtk
```
or
to see if it is a more general issue with the desktop you can do a test for the popup window
```
pkexec test
```
does a popup dialog box show?

I think at this point we're throwing pasta at the wall.

---

### Post by CatKiller on 2020-03-20
> **py-ohayo said:**
> I purged whole NVIDIA staff.
So, can delete these 3 files ?

The three cuda-local ones, yes. You'll want to delete the local repositories as well. No point keeping them when you haven't got anything pulling packages from there.

It's a weird setup, for when you want to replicate the environment on many machines. The Nvidia site does a very poor job of explaining... well, anything, really. 

Should you wish to experiment with CUDA in the future, there's a more standard setup of pulling the CUDA stuff from a standard repository. If you want to also use the PPA driver (which you should) there's a metapackage (whose name I can't currently remember) that pulls in just the CUDA stuff but not the driver. That's the one that you'd install.

---

### Post by py-ohayo on 2020-03-20
> You'll want to delete the local repositories as well. 
Where can I locate them. Can you develop, please.

> Should you wish to experiment with CUDA in the future, there's a more  standard setup of pulling the CUDA stuff from a standard repository. 
You mean steps from here:
[URL="https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#ubuntu-installation"]https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#ubuntu-installation
[/URL]
Not entirely clear ... for example what should I put instead of 
<distro>_<version>_<architecture>

> [FONT=arial]If you want to also use the PPA driver (which you should) there's a metapackage (whose name I can't currently remember) that pulls in just the CUDA stuff but not the driver.[/FONT]
[FONT=arial]I'm not sure if I'll need PPA driver. All what I need is to assure GPU support when working with TensorFlow.
According to what I have learned so far, running TensorFlow with GPU support also requires the installation of CUDA, CUDA dev kit, NVIDIA drivers and cuDNN.
And according to my recent experience, if the versions of all these components aren't compatible, it will not work.
[/FONT]

---

### Post by CatKiller on 2020-03-20
> **py-ohayo said:**
> Where can I locate them. 

> **CatKiller said:**
> then simply delete the local repositories (the /var/cuda-repo stuff)

> I'm not sure if I'll need PPA driver. All what I need is to assure GPU support when working with TensorFlow.
According to what I have learned so far, running TensorFlow with GPU support also requires the installation of CUDA, CUDA dev kit, NVIDIA drivers and cuDNN.
And according to my recent experience, if the versions of all these components aren't compatible, it will not work.


The PPA driver is actually updated. The one in the CUDA repos is static: you need to go through the whole palaver of installing the entire CUDA stack again if you want whichever features are in the newer driver. The CUDA stack is perfectly fine with the PPA driver, *provided you aren't also trying to use the CUDA repairing repository's driver at the same time*: Nvidia's driver is terrible at coexisting with itself, but it gets particularly confused by having two different sources.

---

### Post by py-ohayo on 2020-03-23
These NVIDIA drivers is something really infernal.
I've just tried to install version **418** because it matches **CUDA 10.1** that I want to install further, which (i.e. 10.1) matches to **TensorFlow 2.1**, which is final objective.
After executing
**sudo apt-get install nvidia-driver-418**
and rebooting PC, I see the following after executing **nvidia-smi**:
```
pavel@ALABAMA:~$ nvidia-smi
NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.

```

---

### Post by py-ohayo on 2020-03-23
Indeed, although I selected NVIDIA 418

[IMG]https://i.postimg.cc/nzDjKQ14/Screenshot-from-2020-03-23-14-51-16.png[/IMG]

the driver, used by system is still Intel Graphics:

[IMG]https://i.postimg.cc/4y2DJnr0/Screenshot-from-2020-03-23-14-51-41.png[/IMG]

---

