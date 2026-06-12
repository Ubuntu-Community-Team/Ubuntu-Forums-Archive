---
title: "Trouble installing Wine?"
date: 2005-05-07
forum: Installation &amp; Upgrades
---

### Post by CinciTech on 2005-05-07
I went through the instructions on [www.winehq.com](www.winehq.com) and I found the Synaptic Package Manager.  Was pretty proud of myself.  I clicked 'add' and plugged in the data it told me to.  Looked like everything was going okay.  Then I get an error when I try to mark Winetools for installation, and I don't have an option to mark Wine for install...  I get this error:

winetools:
 Depends: wine (>=0.0.20040914) but it is not installable
 Depends: xdialog  but it is not installable
 Depends: gtk-smooth-themes  but it is not installable

The repository settings I've added are:

Type: Binary
URL: [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/)
Distribution: binary/

and

Type: Source
URL: [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/)
Distribution: source/

 ](*,) What exactly am I doing wrong, and what do I need to do to get Wine installed?

---

### Post by bored2k on 2005-05-07
[QUOTE=CinciTech]I went through the instructions on [www.winehq.com](www.winehq.com) and I found the Synaptic Package Manager.  Was pretty proud of myself.  I clicked 'add' and plugged in the data it told me to.  Looked like everything was going okay.  Then I get an error when I try to mark Winetools for installation, and I don't have an option to mark Wine for install...  I get this error:

winetools:
 Depends: wine (>=0.0.20040914) but it is not installable
 Depends: xdialog  but it is not installable
 Depends: gtk-smooth-themes  but it is not installable

The repository settings I've added are:

Type: Binary
URL: [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/)
Distribution: binary/

and

Type: Source
URL: [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/)
Distribution: source/

 ](*,) What exactly am I doing wrong, and what do I need to do to get Wine installed?[/QUOTE]
 Stick with ubuntu repositories..

---

### Post by CinciTech on 2005-05-07
IT's listed on Wine's website for the correct way to set up wine on Ubuntu.  Could you post somewhere I could find the Ubuntu repositories you mentioned, that would install Wine for me?

---

### Post by bored2k on 2005-05-07
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
> 
rafael@noir:~$ sudo apt-get install wine wine-utils
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libwine
Suggested packages:
  wine-doc libwine-print
The following NEW packages will be installed:
  libwine wine wine-utils
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.4MB of archives.
After unpacking 47.2MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Have fun.

---

### Post by CinciTech on 2005-05-07
Thanks.  I made the changes that link indicates.  In Synaptic I click reload and get this error:

```
The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-amd64/Packages.gz: Unable to fetch file, server said 'Can't open /debian-marillat/dists/stable/main/binary-amd64/Packages.gz: No such file or directory  ' [IP: 62.4.17.14 21]
ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-amd64/Packages.gz: Unable to fetch file, server said 'Can't open /debian-marillat/dists/testing/main/binary-amd64/Packages.gz: No such file or directory  ' [IP: 62.4.17.14 21]
```

And then I'm getting a Warning:

```
W: GPG error: ftp://ftp.nerim.net stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: ftp://ftp.nerim.net unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: ftp://ftp.nerim.net testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907

```

But then I've installed the package wine-doc and it seems to have installed.  Now, where do I find the shortcut to run Wine?

---

### Post by bored2k on 2005-05-07
wine-doc is the documentation..
Install wine and wine-utils.

Before you do, run
```
sudo gedit /etc/apt/sources.list
``` and REMOVE the last marillat packages [all three]. then ```
sudo apt-get update ; sudo apt-get install wine wine-utils
```.

After you install them, just type in a command line
wine filename.exe to run the desired .exe

---

### Post by CinciTech on 2005-05-07
Umm, maybe I've still got something wrong?  There is no Wine or Wine-util.  When I ran the second commadn line, I got this after the "Hit" lines:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Invalid operation wine

---

### Post by bored2k on 2005-05-07
[QUOTE=CinciTech]Umm, maybe I've still got something wrong?  There is no Wine or Wine-util.  When I ran the second commadn line, I got this after the "Hit" lines:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Invalid operation wine[/QUOTE]
 You can not have synaptic nor any other application or terminal using apt at the same time. Close everything else. It doesnt look like your copy/pasting my codes..

---

### Post by CinciTech on 2005-05-07
Closing Synaptic seems to have fixed the problem.  And I actually was retyping what you posted, I didn't realize you could paste in the comand window.  After I pasted the last line, I eventually got this message:

Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

Wine is unavailable?

---

### Post by btc on 2005-05-07
Hi,

I'm getting the same error message as CinciTech..

I've updated sources.list, but "sudo apt-get install wine wine-utils" responds that wine is not available. Is another entry needed in sources.list?

Thanks!

---

### Post by crane on 2005-05-07
[QUOTE=btc]Hi,

I'm getting the same error message as CinciTech..

I've updated sources.list, but "sudo apt-get install wine wine-utils" responds that wine is not available. Is another entry needed in sources.list?

Thanks![/QUOTE]

Wasn't hte latest release of wine broken? Or has that been fixed? I installed wine from .deb packages(older version) so I could play CoD.
Just wondering.

---

### Post by CinciTech on 2005-05-10
[QUOTE=crane]I installed wine from .deb packages(older version) so I could play CoD.[/QUOTE]

Where would I go to get an older package, and how do I go about installing it, rather than using synaptic?

---

