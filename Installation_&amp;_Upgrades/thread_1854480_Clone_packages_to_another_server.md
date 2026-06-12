---
title: "Clone packages to another server"
date: 2011-10-04
forum: Installation &amp; Upgrades
---

### Post by sropensrc on 2011-10-04
Hi,

I'm wanting to clone packages from one server to another.  Here's is what I've tried:
_From source 10.04.2_
[SIZE=2]dpkg --get-selections > pkginstalled_source
copy pkginstalled_source file to destination server
[/SIZE]_From destination 10.04.3_
[SIZE=2]sudo dpkg --set-selections && dselect install <      ./pkginstalled_source
I ran "dpkg-l | wc -l" command and number of packages increased from 379 to 384 that's it.  Source has 771 packages.  

Is the problem do to versions diff, or I'm doing something wrong?

Thanks



[/SIZE]

---

### Post by zvacet on 2011-10-04
Why don&#729;t you transfer deb files form one server to another?If you want to do that then

```
aptitude --display-format '%p' search '?installed!?automatic' > ~/my-packages 
```

Then post that file to your self and put it in second server and run

```
sudo xargs aptitude --schedule-only install < my-packages
sudo aptitude install
```

---

### Post by tgalati4 on 2011-10-04
Don't for get to update the repositories on the new machine:

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

Also, did you or another installation script add additional repositories?  Compare /etc/apt/sources.list on both machines.

Some packages add a repository or PPA and then install from there.  So you would need to update and upgrade a few times to get all of the packages.

You are showing different base installations between machines (10.04.02 vs .03) that could explain the differences.  Some packages may have been "rolled up" for .03 release and that could explain the reduction in number of packages.

---

### Post by sropensrc on 2011-10-05
ZVACET,

I copied the deb files to new server.  I ran the command to create the "my-packages" file and moved it to new server. 

On new server, when I ran the "sudo xargs aptitude ..." I received a lot of "No candidate version found for _packagename_".  When I ran command "sudo aptitude install", it didn't install or upgrade any packages.  

Also, when I ran the "sudo apt-get update" I get a lot of errors
"Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
  Connection failed [IP: 91.189.92.170 80]"
"W: Failed to fetch [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) ..."

I apologize for being ignorant but I'm new to ubuntu.  I'm sure I'm not following the instruction correctly, help.

Thanks

---

### Post by sropensrc on 2011-10-31
Sorry for not updating sooner.

The apt-get error "Connection failed... " was due to our Websense firewall.  The server was added to Websense whitelist and I was able to clone the packages.

Thank You

---

