---
title: "failed to download repository information in ubuntu 16.04"
date: 2017-06-09
forum: Installation &amp; Upgrades
---

### Post by manjunathkm on 2017-06-09
i updated ubuntu 16.04 last week, and i am facing this problem.

There have been several suggestion to run [FONT=Courier New][COLOR=#0000FF]sudo apt-get update[/COLOR][/FONT]  at the terminal.  But that had a few failures. While the entire output  of that command is attached, I wanted to include the error lines here:

```
Ign:1 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial InRelease
Ign:7 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial Release
Ign:8 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 Packages
Ign:9 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main i386 Packages
Ign:10 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main all Packages
Ign:11 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en_IN
Ign:12 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en
Ign:13 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:14 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:8 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 Packages
Ign:9 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main i386 Packages
Ign:10 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main all Packages
Ign:11 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en_IN
Ign:12 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en
Ign:13 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:14 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:8 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 Packages
Ign:9 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main i386 Packages
Ign:10 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main all Packages
Ign:11 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en_IN
Ign:12 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en
Ign:13 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:14 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:8 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 Packages
Ign:9 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main i386 Packages
Ign:10 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main all Packages
Ign:11 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en_IN
Ign:12 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en
Ign:13 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:14 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:8 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 Packages
Ign:9 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main i386 Packages
Ign:10 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main all Packages
Ign:11 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en_IN
Ign:12 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en
Ign:13 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:14 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main DEP-11 64x64 Icons
Err:8 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 Packages
  404  Not Found
Ign:9 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main i386 Packages
Ign:10 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main all Packages
Ign:11 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en_IN
Ign:12 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en
Ign:13 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:14 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main DEP-11 64x64 Icons
Reading package lists... Done
W: The repository 'http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://ppa.launchpad.net/colingille/freshlight/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/colingille/freshlight/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
```


any suggestions ,

Thanks

---

### Post by wildmanne39 on 2017-06-09
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by howefield on 2017-06-09
Try opening the Software & Updates application and change to the main server.

---

### Post by manjunathkm on 2017-06-09
howefield.. still i am getting same error even after changing server..

---

### Post by deadflowr on 2017-06-09
Your output is rather odd as a whole.
Firstly though, there is no archive for that ppa for xenial.
So you'll need to remove it.
You can do so in the same place howefield pointed to, but go to the Other Software section and uncheck the freshlight archive.
 
Not really sure why the whole output reads like that though...

---

