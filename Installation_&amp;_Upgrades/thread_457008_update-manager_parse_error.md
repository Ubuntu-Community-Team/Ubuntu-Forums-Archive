---
title: "update-manager parse error"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by Nachtengel on 2007-05-28
On running the last batch of updates for Feisty, something went wrong and now my update-manager. apt-get aind aptitude don't work properly.  This is the error message:

[IMG]http://img.photobucket.com/albums/v67/Nachtengel/Forum/Screenshot-update-manager.png[/IMG]

I have already tried to 

```
sudo apt-get install -f 
```

but to no avail.

 Attached to this post is my /var/lib/dpkg/status file.

---

### Post by theaxis69 on 2007-05-28
I ran

```
sudo apt-get update
```

from the command line, and this cleared the Update Manager error

---

### Post by Nachtengel on 2007-05-28
I ran and got this:

```
~$ sudo apt-get update
Password:
Get:1 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Get:2 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:3 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com feisty-security Release
Get:4 http://us.archive.ubuntu.com feisty-backports Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release
Hit http://security.ubuntu.com feisty-security/main Packages        
Hit http://us.archive.ubuntu.com feisty-updates Release
Hit http://us.archive.ubuntu.com feisty-backports Release           
Hit http://security.ubuntu.com feisty-security/restricted Packages  
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://us.archive.ubuntu.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/main Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Sources
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://us.archive.ubuntu.com feisty-backports/main Packages
Hit http://us.archive.ubuntu.com feisty-backports/restricted Packages
Hit http://us.archive.ubuntu.com feisty-backports/universe Packages
Hit http://us.archive.ubuntu.com feisty-backports/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-backports/main Sources
Hit http://us.archive.ubuntu.com feisty-backports/restricted Sources
Hit http://us.archive.ubuntu.com feisty-backports/universe Sources
Hit http://us.archive.ubuntu.com feisty-backports/multiverse Sources
Fetched 4B in 1s (4B/s)
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing scim-modules-table (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

```

---

### Post by Nachtengel on 2007-06-17
Solved in another thread with inspiration from Roffy: [http://ubuntuforums.org/showthread.php?t=447121&page=2]("http://ubuntuforums.org/showthread.php?t=447121&page=2")

---

