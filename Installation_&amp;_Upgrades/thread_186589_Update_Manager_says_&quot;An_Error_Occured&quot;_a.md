---
title: "Update Manager says &quot;An Error Occured&quot; after dist-upgrade"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by Carrots171 on 2006-06-02
I've just dist-upgraded to Dapper using apt-get. Everything seems to be going pretty smoothly, but there's a problem. Now the update-manager notification icon in the system tray (okay, I know it's called the "notification area"), says that: 

> A error occured, please run Package-Manager from the right-click menu or apt-get on a terminal to see what is wrong. The error message was: 'Error; Opening the cache (E:Opening /etc/apt/sources.list -ifstream::ifstream (13 Permission denied),E:The list of sources could not be read.)' 

Everything else seems to be working fine. What does this error message mean and how do you fix it? Thanks in advance for your help.

---

### Post by Jussi Kukkonen on 2006-06-02
It is a strange error message. The instructions are still good: apt-get will probably give you more info. Open a terminal and run first
```
sudo apt-get update

```
If you see errors, paste them here. If not, run
```
sudo apt-get dist-upgrade

```
just to make sure the installation went "all the way"

---

### Post by Carrots171 on 2006-06-02
When I run "apt-get update", there are no errors. When I run "apt-get dist-upgrade", nothing new is installed. (I assume this means that the installation went "all the way"). However, the little update notifier still displays the same error message. 

EDIT: When I start up Add/Remove applications, it says: 

> Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

My "/etc/apt/sources.list" is as follows:

```


## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse






## deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ dapper free non-free


## deb http://seveas.ubuntulinux.nl/ dapper-seveas dapper-backports dapper-custom dapper-extras freenx madwifi
## deb-src http://seveas.ubuntulinux.nl/ dapper-seveas dapper-backports dapper-custom dapper-extras freenx madwifi


## created by arnieplanetremoved
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://wine.sourceforge.net/apt/ binary/

```

---

### Post by Carrots171 on 2006-06-02
Update: I tried changing my sources.list to [ubuntu_demon's recommended sources.list]("http://www.ubuntuforums.org/showthread.php?t=185758") and updating apt-get, but the same error message shows up. Synaptic works fine and I can install stuff, so I don't undestand why the update-notifier and the add/remove applications thing think the package system is broken.

---

### Post by ubuntu_demon on 2006-06-02
During dist-upgrading from Breezy to Dapper non-official repos should be uncommented.

uncomment all non-official repos :
$sudo gedit /etc/apt/sources.list

$sudo apt-get update
$sudo apt-get dist-upgrade
$sudo dpkg --configure -a

---

### Post by Carrots171 on 2006-06-02
I followed all of the above instructions. But it still gives me the same error messages. ](*,) Universe and Multiverse are official repos, right?

---

### Post by ubuntu_demon on 2006-06-02
[QUOTE=Carrots171]I followed all of the above instructions. But it still gives me the same error messages. ](*,) Universe and Multiverse are official repos, right?[/QUOTE]

yeah they are.

Take a look here :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

---

### Post by Carrots171 on 2006-06-02
Looked there. Did all of the steps. It didn't help; I'm still getting the same error messages. ](*,) 

I don't have any broken packages or unconfigured packages, and I don't think I have any broken dependencies. :-k The error message from the update-notifier says that the "list of sources could not be read", so maybe it's a different problem?

---

### Post by ubuntu_demon on 2006-06-02
> **Carrots171]Looked there. Did all of the steps. It didn't help said:**
> (*,) 

I don't have any broken packages or unconfigured packages, and I don't think I have any broken dependencies. :-k The error message from the update-notifier says that the "list of sources could not be read", so maybe it's a different problem?

It's good to first make sure it's not related to broken dependencies and the contens of your sources.list :).

I just saw this part of the error "permission denied". It's probably a permission problem.  Please post the result of :

$ ls -al /etc/apt/sources.list

The result should be :
```

-rw-r--r-- 1 root root  ......

```

If it's something else do this get the permissions right :
$ sudo chmod 644 /etc/apt/sources.list

Do this to get it owned by root :
$sudo chown root:root /etc/apt/sources.list

Also please post your ~/.xsession-errors :

$ gedit ~/.xsession-errors

---

### Post by thnogueira on 2006-06-02
I had the same error and it was solved by changing the permitions of /etc/apt/sources.list to 644, as ubuntu_demon sad. Breezy to Dapper upgrade has changed its permitions to 600 for some reason.

---

### Post by Carrots171 on 2006-06-02
I changed the permissions of /etc/apt/sources.list using your instructions... and it works!!! *Jumping up and down* Thanks a lot for your help! \\:D/

---

### Post by ubuntu_demon on 2006-06-02
[QUOTE=Carrots171]I changed the permissions of /etc/apt/sources.list using your instructions... and it works!!! *Jumping up and down* Thanks a lot for your help! \\:D/[/QUOTE]
no problem :)

---

### Post by Aielyn on 2006-06-03
[QUOTE=ubuntu_demon]It's good to first make sure it's not related to broken dependencies and the contens of your sources.list :).

I just saw this part of the error "permission denied". It's probably a permission problem.  Please post the result of :

$ ls -al /etc/apt/sources.list

The result should be :
```

-rw-r--r-- 1 root root  ......

```

If it's something else do this get the permissions right :
$ sudo chmod 644 /etc/apt/sources.list

Do this to get it owned by root :
$sudo chown root:root /etc/apt/sources.list

Also please post your ~/.xsession-errors :

$ gedit ~/.xsession-errors[/QUOTE]

I actually had a similar problem to the one that Carrots171 had. Update Manager sat in the notification area and told me that there was an error (almost the same one - except it was apt.conf rather than sources.list). Also, Add/Remove refused to even open.

It turns out that, although the sources.list file on my computer had the right permissions, /etc/apt/apt.conf did not, and that was the problem.

I just thought I'd let people know about it - sources.list isn't the only file that might have permission problems.

---

### Post by ubuntu_demon on 2006-06-03
[QUOTE=Aielyn]I actually had a similar problem to the one that Carrots171 had. Update Manager sat in the notification area and told me that there was an error (almost the same one - except it was apt.conf rather than sources.list). Also, Add/Remove refused to even open.

It turns out that, although the sources.list file on my computer had the right permissions, /etc/apt/apt.conf did not, and that was the problem.

I just thought I'd let people know about it - sources.list isn't the only file that might have permission problems.[/QUOTE]
thnx!

---

### Post by tom-ubuntu on 2006-06-04
Looks like I am not the only one with this problem. Have had exactly the same problem on one of the machines. Thanks for the solution!

---

### Post by ubuntu_demon on 2006-06-04
I've mentioned the solution here :

Having problems with installing or upgrading to Dapper? Here are some fixes
[http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)

---

### Post by Ubuntist on 2006-06-06
[QUOTE=ubuntu_demon]
$ sudo chmod 644 /etc/apt/sources.list
[/QUOTE]

This worked for me.  Thanks very much!

---

### Post by ms30290 on 2006-06-07
Thanks Ubuntu_Demon. Post 9 did the trick for me as well.

---

### Post by william_nbg on 2006-06-18
Thanks Ubuntu_Demon

After banging my head against my keyboard for 2 days I found this thread, which solved my last upgrade-to-dapper problem.

Now, after buying a new keyboard, I'll have a perfect running machine again.

---

### Post by jandi on 2006-07-15
Thanks, changing the permissions of sources.list also worked for me.  Seems it wasn't the only issue with permissions after dist-upgrading to Dapper, as I also had to do some work on Firestarter.

---

