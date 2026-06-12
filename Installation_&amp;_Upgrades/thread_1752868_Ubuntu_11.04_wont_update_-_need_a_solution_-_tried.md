---
title: "Ubuntu 11.04 wont update - need a solution - tried a lot of things already"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by redber20 on 2011-05-08
I installed Ubuntu 11.04 with no problems.

However, when i tried to update it, this message appears in the terminal in the end every time:

'E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.'


- already tried removing all the files in /var/lib/apt/lists and start the update over and over again. Still, this happens each time

- tried changing the server from the Philippine Server to the Main Server and updated again: didn't do any good

Sometimes when I try to update through Synaptic Manager when I reload...this happens:

W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security InRelease: The following signatures were invalid: NODATA 1 NODATA 2

...

and then this happens again:

'E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.'


Please help. Thanks in advance guys :)

---

### Post by amin007110 on 2011-05-08
Try this:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

---

### Post by thebackground on 2011-05-08
Same thing happen to me... maybe problems with the philippine server? 

[I]Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

FYI : this seems doesn't work 
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

[/I]Please help the philippine users... 

thanks

---

### Post by redber20 on 2011-05-09
> **amin007110 said:**
> Try this:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

I tried that once but it didn't work...

Let's see...hmm i'll try to do a clean install again and update again...if the problem strikes again...i'll try sudo rm /var/lib/apt/lists/* -vf once more...

I'l let you guys know if it works...

---

### Post by percyhahn on 2011-05-09
> **amin007110 said:**
> Try this:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
  thats just worked for me, thanks!!

---

### Post by redber20 on 2011-05-23
SOLVED IT!!! 

after...

**sudo rm /var/lib/apt/lists/* -vf**

...

;) I tried the command...
[B]
sudo apt-get clean[/B]

before

**sudo apt-get update**

---

### Post by sgtryan on 2011-05-24
Same here, same error, same file. I have done all the methods and the errors are still there. Could it be the Philippine server?
Please help!


> **thebackground said:**
> Same thing happen to me... maybe problems with the philippine server? 

[I]Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

FYI : this seems doesn't work 
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

[/I]Please help the philippine users... 

thanks

---

### Post by sgtryan on 2011-05-24
Solved also! The problem is my internet connection. Files were downloaded successfully. Thanks for the info, guys.

> **sgtryan said:**
> Same here, same error, same file. I have done all the methods and the errors are still there. Could it be the Philippine server?
Please help!

---

### Post by hoy_pogi on 2011-05-26
Hi,

I'm having exactly the same problem. My internet provider is Sun broadband. I haven't tried downloading using another provider, but I tried in the morning when my download speed is 100KB/s on average, and I still get the same error. It seems that the server's copy of the internationalization file is corrupted. The problem is, even during installation, the installer attempts to download this file, crashing the installer.

I have tried manually clearing the apt cache (apt-get clean, rm ...) but when it tries to download that file again, the installer crashes and synaptic won't start unless I manually clear the cache again.

I've also tried clicking on "update this installer" but that hasn't done anything in my experience.

If the cause is the corrupted file in the Philippine server, is there any way I can tell the installer to use another source (main?)

I'm gonna try to disconnect my vm from the network, see if installation works without an internet connection.

@sgtryan - how did you know it was your internet connection? shouldn't it be robust enough to attempt to download the file again in the event of corruption, and why does it happen for this specific file and not on something else?

---

