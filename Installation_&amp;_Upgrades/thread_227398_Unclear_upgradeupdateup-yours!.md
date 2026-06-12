---
title: "Unclear upgrade/update/up-yours!"
date: 2006-08-01
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2006-08-01
Dear Community:

First, I've been waiting for Dapper Drake since mid-June, it arrived today, 8/1/06 --Hurray!

Second, whoever has control of:

[https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

please remove the 128-bit encryption. No passwords are needed to read that page and it would be better off, if like Wikipedia, there was a discussion-page under it for people to talk about editing it, if even necessary. Is there some frightening predator lurking around Ubuntu-Wiki? [Have Gun -- Will Travel] ahhh...never mind!

Third:

I've been reading the Ubuntu Forums boards about 6.06LTS for weeks now. And now that I have the disks, I can't seem to tell whether I'm **updating** or **upgrading**, that is, with the CD in hand.

Does it self-install? Does it know not to overwrite files in /home and below there?

If I were to upgrade will that overwrite /home, and not overwrite if I update?

Do I need to put fresh repository into into /etc/apt/sources.list ?, or is everything necessary on the CD?

I am embarrassed at asking this. I'm sure it must be somewhere made plain and simple as to what needs to be done, but after weeks of waiting and hours of reading, I'm afraid I've confused myself.

Thank you for taking your time to read this extensive and unenlightening post.

Mark
Thanking the Ubuntu Community since Jan, 2006.

---

### Post by mlind on 2006-08-01
If you're upgrading from previous install, like Breezy, you can use apt-cdrom to add the Dapper cd as a repository for files.
This should help you [https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

If you're doing a fresh install, /home will be overwriten if it's not on a separate partition I think. In this case you'll have to back it up and restore after Dapper install has finished.
If /home is on separate partition, you can choose that installer won't touch that partition.

---

### Post by aysiu on 2006-08-01
You cannot upgrade from the **Desktop CD**.

To upgrade, you need either the **Alternate CD** or a fast internet connection. If you want to add the CD as a repository, paste this command in the terminal: ```
sudo apt-cdrom add
``` Then edit your sources.list and remove all other repositories (Control-K): ```
sudo nano -B /etc/apt/sources.list
``` Save (Control-X, Y, Enter). Finally ```
sudo aptitude update
sudo aptitude dist-upgrade
``` Otherwise: [http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)

---

### Post by Mark_in_Hollywood on 2006-08-01
I have the Dapper Drake 6.06 LTS, as I said in my original post. It was sent to me from Canonical/Ubuntu. I'm now more confused, why do I need to download what was sent from them?

---

### Post by aysiu on 2006-08-01
There are three kinds of Dapper Drake 6.06 LTS CDs:

Desktop CD
Alternate CD
Server CD

All are Dapper Drake (the current release of Ubuntu), but they are tailored to different methods of installation. The Desktop CD is a live CD that can also be installed. It does not have a full set of packages available for upgrade. The Alternate CD can be used as an upgrade repository. It can also do some special installations (barebones, OEM, etc.). The Server CD installs a server version of Ubuntu.

All three version of are Dapper Drake 6.06, but you cannot upgrade with the Desktop CD or the Server CD.

---

### Post by Mark_in_Hollywood on 2006-08-01
> **mlind said:**
> If you're upgrading from previous install, like Breezy, you can use apt-cdrom to add the Dapper cd as a repository for files.

I need to know whether I'm upgrading or updating. I can't follow you here, sorry.

If you're doing a fresh install, /home will be overwriten if it's not on a separate partition I think. In this case you'll have to back it up and restore after Dapper install has finished.
If /home is on separate partition, you can choose that installer won't touch that partition.

I'm trying to NOT overwrite /home. I have Breezy Badger, fully updated, as of the day that the repositories for 5.10-Badger were "closed" and Drake "opened".

If /home is overwritten what commands are necessary to "restore" it, please?

---

### Post by Mark_in_Hollywood on 2006-08-01
> **aysiu said:**
> There are three kinds of Dapper Drake 6.06 LTS CDs:

Desktop CD
Alternate CD
Server CD

All are Dapper Drake (the current release of Ubuntu), but they are tailored to different methods of installation. The Desktop CD is a live CD that can also be installed. It does not have a full set of packages available for upgrade. The Alternate CD can be used as an upgrade repository. It can also do some special installations (barebones, OEM, etc.). The Server CD installs a server version of Ubuntu.

All three version of are Dapper Drake 6.06, but you cannot upgrade with the Desktop CD or the Server CD.

I have received what appears to be the "live CD" from Canonical. I believe this is UBUNTU (not Kubuntu or Edubuntu). I believe this is the DESKTOP version. I currently have Breezy Badger which has been fully "updated" via the Internet and is as "ready" as it can be made, as the respositories for BB closed some time ago.

If I read you write, the CD install some files and the rest must be downloaded?

---

### Post by aysiu on 2006-08-01
No, you can't upgrade at all from the Desktop CD. It does contain a very small repository of packages (*build-essential* and *ndiswrapper-utils*, for example), but you cannot upgrade from it.

Your three choices are:

1. Reinstall Ubuntu from the Desktop CD, being careful not to reformat your /home partition.
2. Upgrade over the internet by following [these instructions](http://www.psychocats.net/ubuntu/dapper).
3. Download the Alternate CD and upgrade from that. This won't save you any time over #2, but you'll have a CD for it, in case you ever want to upgrade another computer.

---

### Post by mlind on 2006-08-01
> **Mark_in_Hollywood said:**
> I'm trying to NOT overwrite /home. I have Breezy Badger, fully updated, as of the day that the repositories for 5.10-Badger were "closed" and Drake "opened".

If /home is overwritten what commands are necessary to "restore" it, please?

You didn't say if your /home is on a separate partition. If it **isn't** and you're going to do a full install (not upgrade), you need to back it up. Use tar and  switch to preserve file permissions (-p), then burn created archive on a cd for example or place it on partition that you're not going to overwrite on install process.

Personally I would probably follow aysiu's 2nd choice.

---

### Post by aysiu on 2006-08-01
Don't you mean that if it **isn't** on a separate partition, then you need to back it up?

---

### Post by mlind on 2006-08-01
> **aysiu said:**
> Don't you mean that if it **isn't** on a separate partition, then you need to back it up?

oops :rolleyes: sticky fingers..

---

### Post by Mark_in_Hollywood on 2006-08-02
> **mlind said:**
> You didn't say if your /home is on a separate partition. If it **isn't** and you're going to do a full install (not upgrade), you need to back it up. Use tar and  switch to preserve file permissions (-p), then burn created archive on a cd for example or place it on partition that you're not going to overwrite on install process.

Personally I would probably follow aysiu's 2nd choice.

I'm not sure I can follow you all. I will try to explain the "what" of this computer/Ubuntu, etc.

I had version 5.04, updated then upgraded to 5.10 via modem. As far as I can tell, the /home IS NOT a separate partition. I'm weak on partitions. So I doubt it is a separate partition. But that is so technical I can't tell, because I've used Linux/Ubuntu for about 7 months. And that only to do email and surf the 'net.

I have no idea how to: "Use tar and switch to preserve file permissions (-p), then burn created archive on a cd" And while I'm sure this is the right help, I have NO IDEA as to what you are referrring to.

Let me being again. I have Ubuntu version 5.10 (Breezy Badger). I have it through using a Hoary Hedgehog CD from Canonical to install that version on this hard disk. Once HH was up, I was able to get the modem to update to the most recent HH "updates", then with more time online, via the modem, the HH was "upgraded" to Breezy. As I have a 56Kbaud modem, it seemed smarter to get the 6.06 LTS (Dapper Drake) version from Canonical. It arrived today.

To install (is that the right word? If it's not 'to install' is it to "upgrade", and are the commands different?) does one put the CD in the drive before powering up the computer? 

Does one turn on the computer and insert the CD, while the machine is "booting"?

Does one wait for the computer to finish booting, and after giving one's user name and password does one then insert the CD?

Does the CD try to install itself? Or do I have to use Synaptic or Apt-Get for some of it? I'm trying to learn how automated the process is and to not screw things up worse.

Does one call Synaptic and then insert the CD?

Does one need to inform Synaptic that the CD is present/active or in some other way change Synaptic's settings?

Does one open a terminal and issue sudo + commands, and which ones? Or where would I find those instructions -- actually all instructions plus alternative methods. Or how do I go about determining what might be the best way to add/upgrade/update/install Dapper Drake into my current system?

I repeat: I have the Ubuntu version 6.06 LTS CD from Canonical. It is the official Dapper Drake release. I have no way to "download" the CD and have better than it in the CD from Canonical.

I have looked at the following from:

[http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)

"section [ii] :READ THIS PRIOR TO UPGRADING TO DAPPER : :
[https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)

You should close all applications during upgrading to Dapper. If you don't your system might become unresponsive.

You should also disable screen savers/lock before upgrading. See here for someone who had troubles because of it :
[http://www.ubuntuforums.org/showthread.php?t=187022](http://www.ubuntuforums.org/showthread.php?t=187022)

You should remove docbook-utils before upgrading.
$sudo apt-get remove docbook-utils
for more information see here :
[http://www.ubuntuforums.org/showpost...0&postcount=37](http://www.ubuntuforums.org/showpost...0&postcount=37)

During dist-upgrading from Breezy to Dapper non-official repos should be commented. Dist-upgrading using the update-manager tool is easy as it comments all non-official repo's automatically."


I have disabled screen savers/lock. I don't have docbook-utils as far as I can tell. My repos have no "unofficial" or "offsite" links or whatever they are called or termed.

I have read:

[https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

and followed the instructions under the heading:

"Upgrading from an Ubuntu 6.06 CD."

Following those instructions:

Upgrading from an Ubuntu 6.06 CD

   1.

      Make sure that you have the package "ubuntu-desktop" or "kubuntu-desktop" or "edubuntu-desktop" installed (depending on the distribution you are using).

**This is the ubuntu-desktop CD**

   2.

      Edit your /etc/apt/sources.list as root:
          *

            For Ubuntu/Xubuntu:

               gksudo "gedit /etc/apt/sources.list" 

[B]Issueing the above returned:

mark@lexington:~$ gksudo gedit /etc/apt/sources.list
(gedit:8010): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
mark@lexington:~$
[/B]

            or for Kubuntu:

               kdesu kate /etc/apt/sources.list 

            and change every occurrence of "breezy" to "dapper".
   3.

      either
          *

            Download the ISO image for the "Alternate Install CD", (not the "Desktop CD", which from my experience today 9th June and that of others in the [WWW] web forum is defective anyway, giving [WWW] all sorts of problems, nor the "Server install CD"), eg from [WWW] here or from [WWW] Torrents and burn it to CD, or,

**This section does not apply to me**
          *

            Order the (3) CDs to be posted out to you via [WWW] Shippit, and use the "Alternate Install CD".
   4.

      To install from a physical CD
         1.

            Run:
                *

                       sudo apt-cdrom add 

                  Insert the CD, and press enter.
         2.

            Run:
                *

                       sudo apt-get update && sudo apt-get dist-upgrade 

 
[B]I received the following after sudo-ing the above commands:

mark@lexington:~$ sudo apt-cdrom add
Password:
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
Identifying.. [d9f91a1075ce140463bf88837cc07be6-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes and 1 signatures
This disc is called:
'Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)'
Copying package lists...gpgv: Signature made Tue 30 May 2006 08:16:20 PM PDT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
Unmounting CD-ROM...Repeat this process for the rest of the CDs in your set.
mark@lexington:~$ sudo apt-get update && sudo apt-get dist-upgrade
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Temporary failure resolving 'security.ubuntu.com'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
mark@lexington:~$[/B]

Any help appreciated . . .

---

### Post by aysiu on 2006-08-02
If you have dial-up, another dist-upgrade could take forever.

I think you have two viable options are this point:

1. [Create a separate /home partition (using the Desktop CD)](http://www.psychocats.net/ubuntu/separatehome.html). Then install Dapper *over* your Breezy installation (and since your /home partition is separate, you can keep your old settings and files).

2. Download using BitTorrent (for ISO file integrity--a straight download over dial-up is likely to leave you with a corrupt file) the Alternate CD, and then do an upgrade with that.

The difference between an upgrade and a reinstall. An install wipes out what's already there and replaces it with the newer version. An upgrade just changes bits and pieces of what's already there to the newer versions.

As for how to use the Desktop CD, you just pop it in your drive and it'll automatically boot to a live session. From there, you click the install icon, and install.

For screenshots, see this:
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

---

### Post by mlind on 2006-08-02
There seems to be temporary problems with Ubuntu repositories. Try the update and upgrade command again (until you succeed)
```

sudo apt-get update && sudo apt-get dist-upgrade

```

You can modify also APT (package manager) to download required packages from mirror near your location. This usually solves problems regarding to repositories, but maybe difficult task for beginners ([http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic) helps). If you choose to generate new sources.list, don't remove the cdrom entry from the list.

---

### Post by Mark_in_Hollywood on 2006-08-06
Success!

With help from several people in different posts, I have been able to install Dapper. I was able to make a new partition for /home and the only loss was that I forgot to copy the bookmarks over to that partition. Not a great loss. What I want to know, however, is how to have upgraded from Breezy to Dapper by writing over Breezy, in the same way that Windoze 98 would have overwritten W'95, without overwriting non-OS files.

Thank you one and all for your support.

---

### Post by mlind on 2006-08-07
> **Mark_in_Hollywood said:**
> Success!

With help from several people in different posts, I have been able to install Dapper. I was able to make a new partition for /home and the only loss was that I forgot to copy the bookmarks over to that partition. Not a great loss. What I want to know, however, is how to have upgraded from Breezy to Dapper by writing over Breezy, in the same way that Windoze 98 would have overwritten W'95, without overwriting non-OS files.

Thank you one and all for your support.

If you replace breezy's repositories with dapper's in /etc/apt/sources.list and use apt-get or aptitude to do a **dist-upgrade**.
All the non-OS files are in your $HOME folder and this won't be touched on the upgrade process.

Now that you have /home on separate partition, you can safely do a install from scratch if you wish and leave /home partition unmodified. Everything in that partition will be preserved.
In windows environment it's trickier do install from scratch, because user profiles must be on the same partition where the OS is.

---

