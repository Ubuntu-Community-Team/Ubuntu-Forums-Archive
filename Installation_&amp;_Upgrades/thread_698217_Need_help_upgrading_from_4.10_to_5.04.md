---
title: "Need help upgrading from 4.10 to 5.04"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by artti on 2008-02-16
I try to upgrade my Ubuntu. But  there comes error:
[I]
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz:) 404 Not Found
[http://archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz:) 404 Not Found
[/I]

I will be thankful for any help. =)

---

### Post by Partyboi2 on 2008-02-16
If you are trying to upgrade to the lastest I would suggest backing up your files and doing a clean install.
hoary is not supported anymore.

---

### Post by artti on 2008-02-16
Hmm... clean install. I have no CD. Can i do it through web or something like that?

---

### Post by Partyboi2 on 2008-02-16
have a look [here]("https://help.ubuntu.com/community/Installation") at some other install methods. You might find one that works for you.

---

### Post by artti on 2008-02-16
Can you recommend? I know that i can't use floppy, i can't write on cd. And I have 300MB free space on memorystick.

---

### Post by zvacet on 2008-02-16
Try [this.](https://help.ubuntu.com/community/Installation/Netboot)

---

### Post by artti on 2008-02-16
apt-get install dnsmasq atftp atftp gives me error

[i]Reading Package Lists... Done
Building Dependency Tree... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package dnsmasq[/i]

---

### Post by PmDematagoda on 2008-02-16
Why don't you simply obtain a Live CD of Ubuntu 7.10 via [ShipIt]("https://shipit.ubuntu.com/")?

---

### Post by PmDematagoda on 2008-02-16
> **artti said:**
> apt-get install dnsmasq atftp atftp gives me error

[i]Reading Package Lists... Done
Building Dependency Tree... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package dnsmasq[/i]

Did you do:-
```
sudo apt-get update
```
as suggested?

---

### Post by artti on 2008-02-16
Now there is: *E: Couldn't find package dnsmasq*

---

### Post by Partyboi2 on 2008-02-16
can you open a terminal and post the output to
```
cat /etc/apt/sources.list
```

---

### Post by artti on 2008-02-16
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe

# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted

---

### Post by PmDematagoda on 2008-02-16
I do not think you could upgrade Ubuntu 4.10 to Ubuntu 7.10 directly, you would have to upgrade next release by next release. In any case this would be very risky and has a high chance of breaking the OS.

But if you still want to upgrade, then open the sources.list file for editing using:-
```
gksudo gedit /etc/apt/sources.list
```
and make the file look like this:-
```
# deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hoary universe
deb-src http://archive.ubuntu.com/ubuntu/ hoary universe

deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ hoary-security main restricted
```
and do:-
```
sudo apt-get update
```
But I think it may be to no avail since the Warty repositories may have been moved along with the Hoary ones.

---

### Post by zvacet on 2008-02-16
```
gsudo gedit /etc/apt/sources.list
```

Replace** archive.ubuntu.com** to **old-releases.ubuntu.com**

It should look like this

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) hoary main restricted


Of course you will replace all lines in source list.

---

### Post by artti on 2008-02-16
Well, i got upgraded to 5.04. I took 2 hours. So... about 10 hours and i should be gutsy. :P

---

### Post by zvacet on 2008-02-17
Maybe I write this too late,but you don&#729;t have to upgrade to Gutsy(you can if you want to).Stay on Dapper,because in april Hardy will be out and you will be able to upgrade directly from Dapper to Hardy.But  if you want to see how Gusy looks and work continue with upgrades.

---

### Post by artti on 2008-02-17
Well i stay then on Dapper. Thanks.

---

### Post by artti on 2008-02-17
I heard that it is possible to disable Ubuntu desktop upgrade, so i could make upgrades to 5.10 and 6.04 faster? Later i activate again.

---

### Post by artti on 2008-02-17
I find command aptitude update and aptitude upgrade, those were faster. It took about hour(maybe less) to get to 5.10. :)

---

