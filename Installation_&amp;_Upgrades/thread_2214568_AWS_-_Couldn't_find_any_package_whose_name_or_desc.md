---
title: "AWS - Couldn't find any package whose name or description matched &quot;freenx&quot;"
date: 2014-04-02
forum: Installation &amp; Upgrades
---

### Post by abundance2 on 2014-04-02
On Amazon Web Services, I am trying to install freenx for the UI. And get the below error messages. I am new to Linux. Do I have to run the commands in a special directory?

**sudo apt-get install freenx-server**
[I]Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package freenx-server
[/I]
**sudo aptitude install -y freenx**
[I]Couldn't find any package whose name or description matched "freenx"
Couldn't find any package whose name or description matched "freenx"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 28 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
[/I]

---

### Post by steeldriver on 2014-04-02
Hello and welcome to the forums

I don't think freenx is currently available from any repository - you probably need to add the team ppa

[https://launchpad.net/~freenx-team/+archive/ppa](https://launchpad.net/~freenx-team/+archive/ppa)

There are Ubuntu-specific instructions here --> [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by abundance2 on 2014-04-02
thanks... i shall try first.

---

### Post by abundance2 on 2014-04-08
hi,

I am new to linux and following the instructions here:
[http://michaelhallsmoore.com/blog/Desktop-Ubuntu-in-Amazon-EC2-The-Right-Way](http://michaelhallsmoore.com/blog/Desktop-Ubuntu-in-Amazon-EC2-The-Right-Way)

[B]Unpack the file and move it to the NX installation directory.  Finally, change the ownership of the file to the root user and install  it:
[/B]
[B]tar zxvf nxsetup.tar.gz
sudo mv nxsetup /usr/lib/nx/nxsetup
sudo chown root:root /usr/lib/nx/nxsetup
sudo /usr/lib/nx/nxsetup --install
[/B]
at 
**sudo mv nxsetup /usr/lib/nx/nxsetup**
there is an error saying no such directory and when I tried going to the directory, it appears that I do not have the rights.

so i create the directory in my downloads folder
and ran sudo mv nxsetup /nx/nxsetup/
The error message is Not a directory.

Can anyone help? Thanks.

---

### Post by steeldriver on 2014-04-08
Did you try the team ppa route in the link I posted? it's generally simpler and more maintainable than installing from source (especially if you are just getting started)

---

