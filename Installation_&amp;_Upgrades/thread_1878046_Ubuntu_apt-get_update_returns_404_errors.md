---
title: "Ubuntu apt-get update returns 404 errors"
date: 2011-11-09
forum: Installation &amp; Upgrades
---

### Post by asljung on 2011-11-09
Hi!

I recently tried to update apt-get, but it just returned a lot of 404 Not Found errors. I've checked the links in a web browser and they work. I also tried wget the files from the server with the same 404 Not Found result. It doesn't matter if I change addresses to another server. I still get the same error. It seams like I can wget the index.html file of the root of a webpage, but not get any other file or get anything from a subfolder. There are no problems connecting to the server with either http, ftp, vpn or ssh. I'm currently using Ubuntu 10.04.1 so there shouldn't be any problem there. I've tried searching the Internet for a similar problem, but all solutions I found didn't work. 

Here is the output from apt-get update:

```
Ign http://se.archive.ubuntu.com lucid Release.gpg
Ign http://se.archive.ubuntu.com/ubuntu/ lucid/main Translation-sv_SE
Ign http://se.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-sv_SE
Ign http://se.archive.ubuntu.com lucid-security Release.gpg
Ign http://se.archive.ubuntu.com/ubuntu/ lucid-security/main Translation-sv_SE
Ign http://se.archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-sv_SE
Ign http://se.archive.ubuntu.com lucid-updates Release.gpg
Ign http://se.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-sv_SE
Ign http://se.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-sv_SE
Ign http://se.archive.ubuntu.com lucid Release
Ign http://se.archive.ubuntu.com lucid-security Release
Ign http://se.archive.ubuntu.com lucid-updates Release
Ign http://se.archive.ubuntu.com lucid/main Packages
Ign http://se.archive.ubuntu.com lucid/restricted Packages
Ign http://se.archive.ubuntu.com lucid/main Sources
Ign http://se.archive.ubuntu.com lucid/restricted Sources
Ign http://se.archive.ubuntu.com lucid-security/main Packages
Ign http://se.archive.ubuntu.com lucid-security/restricted Packages
Ign http://se.archive.ubuntu.com lucid-security/main Sources
Ign http://se.archive.ubuntu.com lucid-security/restricted Sources
Ign http://se.archive.ubuntu.com lucid-updates/main Packages
Ign http://se.archive.ubuntu.com lucid-updates/restricted Packages
Ign http://se.archive.ubuntu.com lucid-updates/main Sources
Ign http://se.archive.ubuntu.com lucid-updates/restricted Sources
Ign http://se.archive.ubuntu.com lucid/main Packages
Ign http://se.archive.ubuntu.com lucid/restricted Packages
Ign http://se.archive.ubuntu.com lucid/main Sources
Ign http://se.archive.ubuntu.com lucid/restricted Sources
Ign http://se.archive.ubuntu.com lucid-security/main Packages
Ign http://se.archive.ubuntu.com lucid-security/restricted Packages
Ign http://se.archive.ubuntu.com lucid-security/main Sources
Ign http://se.archive.ubuntu.com lucid-security/restricted Sources
Ign http://se.archive.ubuntu.com lucid-updates/main Packages
Ign http://se.archive.ubuntu.com lucid-updates/restricted Packages
Ign http://se.archive.ubuntu.com lucid-updates/main Sources
Ign http://se.archive.ubuntu.com lucid-updates/restricted Sources
Fel http://se.archive.ubuntu.com lucid/main Packages
  404  Not Found
Fel http://se.archive.ubuntu.com lucid/restricted Packages
  404  Not Found
Fel http://se.archive.ubuntu.com lucid/main Sources
  404  Not Found
Fel http://se.archive.ubuntu.com lucid/restricted Sources
  404  Not Found
Fel http://se.archive.ubuntu.com lucid-security/main Packages
  404  Not Found
Fel http://se.archive.ubuntu.com lucid-security/restricted Packages
  404  Not Found
Fel http://se.archive.ubuntu.com lucid-security/main Sources
  404  Not Found
Fel http://se.archive.ubuntu.com lucid-security/restricted Sources
  404  Not Found
Fel http://se.archive.ubuntu.com lucid-updates/main Packages
  404  Not Found
Fel http://se.archive.ubuntu.com lucid-updates/restricted Packages
  404  Not Found
Fel http://se.archive.ubuntu.com lucid-updates/main Sources
  404  Not Found
Fel http://se.archive.ubuntu.com lucid-updates/restricted Sources
  404  Not Found
W: Misslyckades med att hämta http://se.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

W: Misslyckades med att hämta http://se.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz  404  Not Found

W: Misslyckades med att hämta http://se.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz  404  Not Found

W: Misslyckades med att hämta http://se.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz  404  Not Found

W: Misslyckades med att hämta http://se.archive.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz  404  Not Found

W: Misslyckades med att hämta http://se.archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz  404  Not Found

W: Misslyckades med att hämta http://se.archive.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz  404  Not Found

W: Misslyckades med att hämta http://se.archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz  404  Not Found

W: Misslyckades med att hämta http://se.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz  404  Not Found

W: Misslyckades med att hämta http://se.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz  404  Not Found

W: Misslyckades med att hämta http://se.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz  404  Not Found

W: Misslyckades med att hämta http://se.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz  404  Not Found
```

What could the problem be? Could there be some port or firewall problems?

I would be grateful for any help.

---

### Post by asljung on 2011-11-09
I've now solved the problem. The nameserver of my ISP had changed ip and that hadn't changed on the ubuntu server. I think there was some kind of error in resolve.conf so I edited it and now it works.

---

### Post by TedinOz on 2011-11-09
> **asljung said:**
> I've now solved the problem. The nameserver of my ISP had changed ip and that hadn't changed on the ubuntu server. I think there was some kind of error in resolve.conf so I edited it and now it works.

I would be grateful if you could explain what you mean here please. I'm having the 404 errors with apt-get update also but I don't understand what you mean by editing 'resolve.conf' ?

---

### Post by subehsharma on 2011-11-10
> **TedinOz said:**
> I would be grateful if you could explain what you mean here please. I'm having the 404 errors with apt-get update also but I don't understand what you mean by editing 'resolve.conf' ?

Best method to getaway from this problem is to install fix404. You can read about it more here:

Under Ubuntu, the APT package index is a database containing all packages of repositories (PPAs) defined in the /etc/apt/sources.list file. To update this database after adding some repositories, we need to use this command from the Terminal:

sudo apt-get update

Sometimes, when running the command given above, we get error messages (404 Not Found) that are the result of wrong PPAs, which may slow down the update process via the Terminal. In fact, this 404 Not Found error messages are not harmful at all, but you can use Fix404 to detect and remove these PPAs.

To install Fix404 on Ubuntu 11.04, launch the Terminal and run these commands:

sudo apt-add-repository ppa:lkjoel/fix404
sudo apt-get update
sudo apt-get install fix404

To install on Ubuntu 10.10/10.04, download this deb package here.

To start using Fix404, run this command (root privileges required):

sudo fix404

Then follow displayed instructions to disable PPAs causing the 404 Not Found Error.

---

### Post by TedinOz on 2011-11-10
@subehsharma

Thank you so much for your comprehensive reply and help. The 404 errors were slowing down the apt-get-update process for sure  and your fix worked a treat with everything working fine now. 

I have been using Ubuntu for 12 months now and loving it, especially for the opportunity it gives to learn and know my computer. That just wasn't available for a novice using Windows and although I will be learning forever now on Ubuntu, the last 12 months have been very rewarding with this system and the support and information freely given here on the forums is just amazing!

Thank you again! :)

---

