---
title: "Software updates fail after fresh install"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by brianerickson on 2006-06-08
During install of Ubuntu 6.06 from desktop i386 cd, an error message comes up "Cannot access security updates".  I continue with the install, and reboot.

Directly after installing Ubuntu and rebooting into the newly installed system, Ubuntu Software Updates shows 11 software updates available.

Attempting to install updates first warns that the updates can't be authenticated, then fails with 11 messages like the one below, see "failed updates.txt" for the complete messages.

[INDENT]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/app-install-data_0.1.33_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/app-install-data_0.1.33_all.deb)
  The HTTP server sent an invalid reply header [IP: 85.133.25.8 80]
[/INDENT]

Network connectivity looks good.  I have no problem downloading the .deb files from the urls in the error messages.

If I try installing the .deb files that I downloaded, there are more complaints about the packages not being authenticated.

I have run through this sequence several times, and the same thing happens every time.  I have even tried re-downloading and burning the install CD in case it was somehow corrupt, but I get the exact same errors. 

Any ideas?

---

### Post by sherlock-holmes on 2006-06-08
[QUOTE=brianerickson]During install of Ubuntu 6.06 from desktop i386 cd, an error message comes up "Cannot access security updates".  I continue with the install, and reboot.

Directly after installing Ubuntu and rebooting into the newly installed system, Ubuntu Software Updates shows 11 software updates available.

Attempting to install updates first warns that the updates can't be authenticated, then fails with 11 messages like the one below, see "failed updates.txt" for the complete messages.

[INDENT]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/app-install-data_0.1.33_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/app-install-data_0.1.33_all.deb)
  The HTTP server sent an invalid reply header [IP: 85.133.25.8 80]
[/INDENT]

Network connectivity looks good.  I have no problem downloading the .deb files from the urls in the error messages.

If I try installing the .deb files that I downloaded, there are more complaints about the packages not being authenticated.

I have run through this sequence several times, and the same thing happens every time.  I have even tried re-downloading and burning the install CD in case it was somehow corrupt, but I get the exact same errors. 

Any ideas?[/QUOTE]

would you post you /etc/apt/sources.list as it is please..

---

### Post by brianerickson on 2006-06-08
Here is the contents of sources.list:


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by markh on 2006-06-09
Check for a proxy entry in /etc/apt/apt.conf , somebody else with the same problem reported a bogus entry in there.

---

### Post by brianerickson on 2006-06-09
[QUOTE=markh]Check for a proxy entry in /etc/apt/apt.conf , somebody else with the same problem reported a bogus entry in there.[/QUOTE]

My /etc/apt/apt.conf has the single line
[INDENT]Acquire::http::Proxy "false";
[/INDENT]

---

### Post by brianerickson on 2006-06-23
I got it to work.  Thanks for everyone's help.

Here's what I did.  I removed single line from /etc/apt/apt.conf, the file is now empty, I also uncommented the lines that the installer commented in sources.list.

```

...
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
...

```

---

### Post by Samuli on 2006-07-08
I had the same problem and removing the line from apt.conf worked wonders :)

I suppose I got this problem because I didn't configure network before install.

---

