---
title: "Update failed due to package &amp; &quot;Check internet connection&quot; error"
date: 2014-08-16
forum: Installation &amp; Upgrades
---

### Post by gueda_Heberle on 2014-08-16
Well, that was not the beginning of it. First, the updates didn't load on Update Manager, due to a problem with packages, which I'm not quite sure I solved (I tried to remove the problem-file, and the directory, but I'm still having problems with updates).

When I try sudo apt-get update, the response is:

```
Err http://ppa.launchpad.net trusty/main i386 Packages  404  Not Found
W: Failed to fetch http://ppa.launchpad.net/conky-companions/ppa/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found
```

When I run Update Manager, it says "check your internet connection", but that is also normal.

Can anyone tell me what to do next?

---

### Post by claracc on 2014-08-16
These two ppas you have added have not a valid address.

So, you open a xterm: ctrl+alt+t

Then you open /etc/apt/sources.list file, you will have tu use sudo:

```
sudo gedit /etc/apt/sources.list
```

Then look for the lines where these two ppas appear and comment them writing a # symbol in the begining of each two forementioned lines.

save and exit

Run ```
sudo apt-get update
``` and it is all.

---

### Post by n4lbl on 2014-08-20
I think I have the same problem.  I'm trying to update from 12.10 64 bit with dual boot.  The update-manager says:
[INDENT]Failed to download repository information
Check your Internet connection.[/INDENT]

The first and last few messages are:
[INDENT]W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources)  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources)  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources)  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources)  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources)  404  Not Found [IP: 91.189.91.13 80][/INDENT]
.....
[INDENT], W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.[/INDENT]

There are ~48 404 messages.  If this is different from the problem under discussion I'll gladly open a new thread.  

Many thanks.

---

### Post by grahammechanical on 2014-08-20
@n4lbl

Your problem is different. You are trying to update a version of Ubuntu that has reached end of life and the repositories are now closed Or rather have been moved to a different location. There will beno more updates to Ubuntu 12.10.

Even upgrading to 14.04 will not be as easy as it would have been a few months ago. It can be done and you should do it. Better to do a fresh install of 14.04.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Regards.

---

### Post by n4lbl on 2014-08-21
Thanks.  I've already read that.  The machine with the problem is at 12.10 and the EOL instructions seem to be only for it's predescessors.  It says:
[INDENT]This guide consists of four main parts.

The first part will cover upgrading from 8.10 to 9.04 and up (eventually to 10.04). We will do the following upgrades, 8.10 to 9.04 to 9.10 to 10.04 LTS.

The second part will cover upgrading from 6.10 to 8.04.3 LTS. We will do the following upgrades, 6.10 to 7.04 to 7.10 to 8.04.3 LTS.

The third part covers upgrading from 6.06 LTS to 8.04.3 LTS. This is the preferred way of upgrading to 8.04.3 from 6.06. You will not need to upgrade to 7.x. At the time of writing this is not an EOL upgrade.

The fourth part will be about upgrading 4.10 to 6.06.2 LTS. We will do the following upgrades, 4.10 to 5.04 to 5.10 to 6.06.2 LTS.[/INDENT]

Have I misunderstood?  Again, thanks.

---

### Post by claracc on 2014-08-21
I think that trying to update from 12.10 --> 13.04 -->13.10 --> 14.04 is a very hard way and it is not any  sure  you are going to success ( a lot of upgrades through EOL support releases).

As it has been pointed before, you better make a fresh install of ubuntu 14.04. Previously, you back up your /home folder and after installation you can restore it to your fresh 14.04.

---

### Post by n4lbl on 2014-08-21
I've never "slammed" a new OS in a machine that is already dual-boot with Grub already there.  Reading at [http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop) at step 4 it says:

[INDENT]Use the checkboxes to choose whether you’d like to Install Ubuntu alongside another operating system, delete your existing operating system and replace it with Ubuntu, or — if you’re an advanced user — choose the ’Something else’ option[/INDENT] 

I've used the first option to build the dual-boot environment.  Will I be able to use that again when dual-boot has already been built?  I'm not an advanced user.  Will the ’Something else’ option be required?  

Thanks.

---

### Post by n4lbl on 2014-08-21
In keen anticipation for installing 14.04 I downloaded the .iso and got the md5sum.  The results were

[INDENT]119cb63b48c9a18f31f417f09655efbd  ubuntu-14.04.1-desktop-amd64.iso[/INDENT]

When I go to [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) to see if the download was error-free I can only find hashes for ubuntu-14.04-desktop-amd64.iso .  Where do I look for the hash for 14.04.1?

BTW, the release notes at [https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes) say that one can upgrade from 12.04.

---

### Post by Bashing-om on 2014-08-21
n4lbl; Hello;


Yep your md5sum is valid; per:
[http://releases.ubuntu.com/14.04/MD5SUMS](http://releases.ubuntu.com/14.04/MD5SUMS)

Upgrade from 12.04 is a fact, one may always do a LTS LTS (before EOL) direct - 12.04 and 14.04 are each LTS releases. Presently the upgrade path from 13.10 remains in place, and in reaching 14.04 one may skip the upgrade to 12.04 to reach 14.04.

My regards
[INDENT][INDENT][INDENT]happy trails to you
[/INDENT][/INDENT][/INDENT]

---

### Post by n4lbl on 2014-08-21
I think one more question will do it.  (Actually from message #7 in this thread.)  When I get to installation type (from [http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop) , step 4 ) will "install alongside win7" do?  This machine currently has 12.10 and win7 dual boot.  Will I need the "something else" option.  I'm anxious to preserve win7.  We need it one month out of the year.

Yet again,,, thanks

---

### Post by n4lbl on 2014-08-22
Many thanks for the assistance.  I made some more mistakes and fixed them.  Perhaps I even learned something.  All is well now.

Again,,, thanks!

---

### Post by Bashing-om on 2014-08-22
n4lbl; Hey !

It has been ages since I did other than the "something else" for installation.

I think in this situation, that IF you choose " install along side " what the installer will do is to install 14.04 in the presently existing 'extended' partition. That will leave Windows and as well 12.10 untouched.

Perhaps not at all what you want to see happen if you have all data backed up from the 12.10 install and are ready to move on.
What I would do ( and what I do as a matter of fact. do ) is in GParted delete the partitions for 12.10, resize and repartition to accommodate 14.04. Taking what I have learned about the system usage in 12.10 to direct the partitions/size in 14.04.

Now if you are perfectly happy with 12.10 set up the way you have it, and want the same in 14.04:
"something else" ->Make sure you are working with the partition(s) that contain ubuntu ( sudo fdisk -lu ) choose to format / and NOT to format /home, use same username and password and I expect the installer will overwrite the system files that were 12.10 with 14.04, and as well preserve your existing /home data and config files while updating /home to 14.04. 

Taking care that you know what partitions are what, and always observing what the installer is pointed to.

[INDENT][INDENT][INDENT]a walk in the park
[/INDENT][/INDENT][/INDENT]

---

