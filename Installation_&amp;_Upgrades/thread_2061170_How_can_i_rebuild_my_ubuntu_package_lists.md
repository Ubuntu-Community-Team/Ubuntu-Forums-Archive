---
title: "How can i rebuild my ubuntu package lists??"
date: 2012-09-21
forum: Installation &amp; Upgrades
---

### Post by nayon0072 on 2012-09-21
In last week for a cause i need to install WIN7:(  . I did  it with dual boot. Then i lost my grub:mad:. After that using tons of tutorial I bring it back:D. But after that I cant install any software from Ubuntu software center or terminal or synaptic package manager.:(
In terminal If show this error message.
```

[sudo] password for junkyeard: 
Reading package lists... Error!
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ precise/restricted i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ precise-updates/restricted i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-i386_Packages)
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/download.opensuse.org_repositories_home:_sarimkhan_xUbuntu%5f12.04_._en
E: The package lists or status file could not be parsed or opened.


```

I think its a problem with the package list. How can i solve it.

Thanks for any help.;)

---

### Post by wojox on 2012-09-21
From the Terminal (Ctrl+Alt+T) back up your original:
```
sudo cp /etc/apt/sources.list{,.backup}
```
Now remove the original and repopulate:
```
sudo rm /etc/apt/sources.list && sudo apt-get update
```

If their is still an error run this and post it back:
```
grep ^ /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by nayon0072 on 2012-09-21
Thanks Bro.
It Works.
But i got some error with updating the list. The full list is not updated.
```

W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG A9E15C2F2B944FEE Launchpad PPA for Alex Murray
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG 6A9653F936FD5529 Launchpad PPA for atareao
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG 7274A4DAE80D6BF5 Launchpad cairo-dock
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG 1FFD34C9EB13C954 Launchpad CoverGloobus
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG D6B6DB186A68F637 Launchpad JDownloader PPA
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2836CB0A8AC93F7A
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG D530E028F59EAE4D Launchpad PPA for NoobsLab
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG 94E58C34A8670E8C Launchpad PPA for Screenlets
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG 899F0DDBB6F5D0E9 Launchpad PPA for Zach Burnham
W: Failed to fetch http://ppa.launchpad.net/vicox/syspeek/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/vicox/syspeek/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```
Why its happening and how can i fix.
Thanks for help. :)

---

### Post by wojox on 2012-09-22
```
sudo apt-get clean 
cd /var/lib/apt 
sudo mv lists lists.old 
sudo mkdir -p lists/partial 
sudo apt-get clean 
sudo apt-get update
```

---

### Post by nayon0072 on 2012-09-22
[IMG]http://i1233.photobucket.com/albums/ff387/nayon0072/Untitledwindow_004_zps75213ea7.png[/IMG]
[IMG]http://i1233.photobucket.com/albums/ff387/nayon0072/Untitledwindow_005_zpsa833ecda.png[/IMG]
This is happening when i am trying to install any soft from Ubuntu software center. Why its happening. 
What can i do for solving it??

---

### Post by wojox on 2012-09-22
run this again and see what the complete error is:
```
sudo apt-get update
```

---

### Post by tienlbhoc on 2012-09-22
apt-get clean and apt-get update.

if still error, view software sources and change repo, and authen repos need key

---

### Post by zgudino on 2013-03-14
Hello[COLOR=#000000],

I had the same problem today in our development server, which of course is running Ubuntu Server.
I managed to solve this by delete everything in the lists directory, locate /var/lib/apt/lists, and then update source packages using apt-get.

So basically it was:

sudo cp -R [/COLOR][COLOR=#000000]/var/lib/apt/lists/* ~/lists/[/COLOR][COLOR=#000000]
sudo rm -R [/COLOR][COLOR=#000000]/var/lib/apt/lists/*
sudo apt-get update
[/COLOR]
You should the lists directory fill again. Hopefully this help you.

---

### Post by Howie55au on 2013-06-21
Hello, I have had a the same problem for a week or so and tried a few suggestions, that I found on the 'net,  but without success.  Thanks wojox your code above worked a treat on Ubuntu 12.04.1.  Many thanks.

Howard.

---

