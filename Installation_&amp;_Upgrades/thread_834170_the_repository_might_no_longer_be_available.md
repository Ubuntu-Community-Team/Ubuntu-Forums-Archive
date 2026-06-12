---
title: "the repository might no longer be available"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by ethicalhacker on 2008-06-19
I get the following errors on updating using the update manager 
what do I have to do to remove them?
[http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.bz2:](http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.bz2:](http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)

---

### Post by Pumalite on 2008-06-19
They are Feisty's. Are you running Feisty?

---

### Post by ethicalhacker on 2008-06-19
yes I need to update all files before upgrading, and I want to upgrade to 8.04 LTS I have the live cd can I update to 8.04 directly keeping all softwares and settings same?

---

### Post by Joeb454 on 2008-06-19
Not from 7.04 (Fiesty) you can't.

You would need to upgrade to 7.10 (Gutsy) first, and then to 8.04 :)

---

### Post by ethicalhacker on 2008-06-19
but I cant even upgrade to 7.10 because of these errors? what do I have to dop to remove them? I also have the live cd for 7.10 can I upgrade directly using the live cd?

---

### Post by ethicalhacker on 2008-06-19
when I put the address [http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/](http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/) into my browser I see the file Packages.bz2 and its downloadable so whats wrong? is it because the address has a : at the end in the error statements or is that just the way ubuntu seperates error address from code? what do I do to remove these errors?

---

### Post by Pumalite on 2008-06-19
Remove all third parties from your /etc/apt/sources.list

---

### Post by ethicalhacker on 2008-06-19
I have nothing under third party in my /etc/apt/sources.list

---

### Post by ethicalhacker on 2008-06-19
it still doesnt work what do I do?

---

### Post by Pumalite on 2008-06-19
Tou might want to try this:
sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

---

### Post by ethicalhacker on 2008-07-02
> **Pumalite said:**
> Tou might want to try this:
sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list 

sudo apt-get update 

 The first command worked fine when I run the second command a whole lot of files get downloaded but it hangs on reading packages 73% or something... 
Is it ok to run the third command?

---

### Post by Pumalite on 2008-07-02
You have to wait to see is your new souces are ready.

---

### Post by ethicalhacker on 2008-07-08
I ran sudo apt-get update again today and 
it gave me at the end 
```
Fetched 6B in 3s (2B/s)  
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Dynamic MMap ran out of room
E: Error occurred while processing smartlist (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
```

when I open update manager i get the error 
A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

```
'E:Dynamic MMap ran out of room, E:Dynamic MMap ran out of room, E:Error occurred while processing smartlist (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'
```

---

### Post by Partyboi2 on 2008-07-08
try to Increase the size of mmap cache limit
```
sudo apt-get update -o APT::Cache-Limit=25165824
```
you can increase the limit by changing 25165824 to a higher number.

---

### Post by ethicalhacker on 2008-07-08
thanks that worked! it said Done at the end...
but I still have a problem I had once before run the  sudo apt-get dist-upgrade command
so now after I go to the update manager I get the error  
[B]Not all updates can be installed
Run a partial upgrade to install as many updates as possible
This can be caused by
- A previous upgrade which dint complete
- Unofficial software packages not provided by Ubuntu
- Normal changes of a pre release version of Ubuntu[/B]
I can click partial upgrade and it will complete the upgrade but I have a slow internet connection and I have the 7.10 Live Cd so I want to upgrade from the cd, so I wont have to download all those files....
what should I do..?

---

### Post by Pumalite on 2008-07-08
Try running:
sudo apt-get -f install

---

### Post by ethicalhacker on 2008-07-08
may I know what exactly will this do?

---

### Post by Pumalite on 2008-07-08
will resolve dependencies and install packages that may be now half installed.

---

### Post by ethicalhacker on 2008-07-08
ok I ran the command and there were three files it said were not needed and I should remove using apt-get autoremove
so I ran the command sudo apt-get autoremove
and it removed those files. Then I went to the update manager again and it still showed the same old error 
[B]Not all updates can be installed
Run a partial upgrade to install as many updates as possible
This can be caused by
- A previous upgrade which dint complete
- Unofficial software packages not provided by Ubuntu
- Normal changes of a pre release version of Ubuntu[/B]
Can I use my 7.10 Live Cd to upgrade my 7.04 ubuntu to 7.10 ?
In this post [http://ubuntuforums.org/showthread.php?t=850376](http://ubuntuforums.org/showthread.php?t=850376) it says I cant do so and I need the alternate Cd please tell me there is another way I dont want to download the alternate cd that is 700 mb my net is slow

---

### Post by Partyboi2 on 2008-07-08
The live cd does not have the upgrade feature, as mentioned you would need the alternate cd to upgrade.

---

### Post by ethicalhacker on 2008-07-08
but the altenate cd for 7.10 isnt available here [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) also after this I need to upgrade to 8.04 does that mean I will have to download that alternate cd too? cant I request a free alternate cd ?

---

### Post by ethicalhacker on 2008-07-08
how do I download 7.10 its not there on the download page, is there anyway I can use the Live CD to upgrade, like copying files or something?

---

### Post by Partyboi2 on 2008-07-08
[[COLOR=Blue]Here[/COLOR]]("http://releases.ubuntu.com/releases/7.10/") is the link to download the gusty alternate cd

> also after this I need to upgrade to 8.04 does that mean I will have to download that alternate cd too? cant I request a free alternate cd ?
Yes you would need to download the hardy alternate cd to upgrade. I don't think you can get the alternate cd through shipit.
Have you considered backing up all your important stuff and doing a clean install of hardy? This way you can order the cd and shouldn't have to download much, maybe a few updates.

---

### Post by ethicalhacker on 2008-07-08
I have considered that, I already have the hardy live cd but I have lots of data and a lot of software and projects ive been working on. I cant possibly find each data file and back it up...

---

### Post by Partyboi2 on 2008-07-08
The only other thing I can think of is if you know someone who has fast internet, if they can download the alternate cd for you, or maybe use a internet cafe. :)

---

