---
title: "Synaptic"
date: 2005-10-29
forum: Installation &amp; Upgrades
---

### Post by AllanP on 2005-10-29
Get this message in Synaptic package manager: The following problems were found on your system:

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by Xian on 2005-10-29
The Breezy Backports are not active.
Just remove those entries from your /etc/apt/sources.list.

Then do another '$ sudo apt-get update' session.
Or click the Reload button in Synaptic.

---

### Post by AllanP on 2005-10-29
Thanks.
The only line I see that resembles this is the last which I ## out.
I seem to be having a fair degree of problems. Another related one is that I am unable to add Repositories: Community maintained (Universe) and Non-free (Multiverse) even after editing Sources.list. They don't stay checked.
Here is my sources list.:

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy multiverse universe main restricted
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted

---

### Post by Ameet on 2005-11-05
I am having a similar problem.  I selected Breezy Universe in the list of repositories, then tried to update ("Reload" button) in Synaptic, and got the following message:

```
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz: Sub-process gzip returned an error code (1)
http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz: Sub-process gzip returned an error code (1)
http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz: Sub-process gzip returned an error code (1)
http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz: Sub-process gzip returned an error code (1)


```

... which was followed by a notice window stating this:

```
The following problems were found on your system:
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)


```

Any suggestions?  I am a relative newbie so please "spell it out" if possible.  Thank you.

---

### Post by cbg on 2005-11-05
same issue here, perhaps its just a matter of the server being down.

---

### Post by nolan43 on 2005-11-08
Hi, I tried to update my repo's now my Applications>Add Applications is BLANK:( 
E: Malformed line 38 in source list /etc/apt/sources.list (dist parse)
is what I'm getting back, what do I do from here.

---

### Post by seatea on 2005-11-08
I don't know if my problem is exactly the same as yours, but it seems more than coincidental that, after updating Ubuntu yesterday, I can no longer find the  "Add Applications" sub-menu. I had some other peculiarities appear like the inability to start the  "Help" guide from  the  menu bar. I have not been able to find  out how to add the "add Applications" back.

---

### Post by Ameet on 2005-11-08
[QUOTE=seatea]I don't know if my problem is exactly the same as yours, but it seems more than coincidental that, after updating Ubuntu yesterday, I can no longer find the  "Add Applications" sub-menu. I had some other peculiarities appear like the inability to start the  "Help" guide from  the  menu bar. I have not been able to find  out how to add the "add Applications" back.[/QUOTE]


Seatea, did you try to Right-Click on the Applications Menu, then select "Edit Menus".  From there you get an interface that lets you select and unselect entries from the menu.  "Add Applications" is one of them.

---

### Post by seatea on 2005-11-08
I did. As far as I can tell, the "Add Applications" entry  is  gone  from there too.

---

### Post by Ameet on 2005-11-10
OK, I think I solved my problem.  This may help AllenP and cbg and others as well.

1) I fixed my /etc/apt/sources.list as described by Aysiu in another thread.  The details are at [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

2) I commented out the last line in sources.list which is about retrieving breezy-backports as several vets have said that is not up and active at this time.  Commenting that is done using gedit (like in step 1), and adding "##" at the front of the last line.

3) I trashed the old listings in /var that were confusing apt-get.

```

cd /var/lib/apt
sudo mv lists lists_backup
sudo mkdir lists
sudo mkdir lists/partial
sudo apt-get update

# when the above works error-free, you can do the next line:
sudo rm -r lists_backup

```

After this, I ran Synaptic package manager and it worked like a charm! :D

---

### Post by linuxted on 2005-11-10
[QUOTE=Ameet]OK, I think I solved my problem.  This may help AllenP and cbg and others as well.

1) I fixed my /etc/apt/sources.list as described by Aysiu in another thread.  The details are at [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

2) I commented out the last line in sources.list which is about retrieving breezy-backports as several vets have said that is not up and active at this time.  Commenting that is done using gedit (like in step 1), and adding "##" at the front of the last line.

3) I trashed the old listings in /var that were confusing apt-get.

```

cd /var/lib/apt
sudo mv lists lists_backup
sudo mkdir lists
sudo mkdir lists/partial
sudo apt-get update

# when the above works error-free, you can do the next line:
sudo rm -r lists_backup

```

After this, I ran Synaptic package manager and it worked like a charm! :D[/QUOTE]


How do you get it to run error free?  I get the following error:
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
  Sub-process bzip2 returned an error code (2)


Thanks

---

### Post by AllanP on 2005-11-10
Ameet: I had a big mess up with Windows and wound up re installing Ubuntu; since then everything has been a/ok. Even got Java working. If I didn't have my Chessmaster game I would trash Windows.

Regards, Allan:)

---

### Post by rlong26 on 2005-11-19
I am having the same problem with adding the community and non-free multiverse repositories. When I attempt to through synaptic I receive the following error.

[COLOR="Red"]Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first.[/COLOR]

I reinstalled and stalled and still got the same error, so It seems to be a bug in breezy.  Also this is causing a real problem with getting the JRE update for Firefox. Anyone else getting the same error? If so how did you fix it?:confused:

---

### Post by aysiu on 2005-11-19
Are you sure you don't actually have another instance of apt-get going?
That error appears when you're trying to use apt-get update while Synaptic is open, for example.

---

### Post by thierryg on 2005-11-20
Hi all,

first post here, so I may have a few things wrong.

I had the same errors: random gzip/bzip errors when using synaptic to update. Could dowload the relevant files by wget. Tried with apt-get update directly. Same errors.

Found an option in man apt.conf: Acquire::http::Pipeline-Depth to compensate for non-conformant proxy servers (such as squid says the man pages). I am behind a squid proxy so tried:

sudo apt-get -o Acquire::http::Pipeline-Depth=0 update

and... no errors anymore.

Anybody knows how to set that up in synaptic?

Thierry

---

