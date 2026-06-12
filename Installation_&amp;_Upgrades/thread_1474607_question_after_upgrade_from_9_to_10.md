---
title: "question after upgrade from 9 to 10"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by unix1adm on 2010-05-06
so this time I got smart and cloned my drive using acronis and put the image on another drive i use for this purposes. 

I went and did the update on the new clone (verified everything worked fine etc. )

Update went fine but said some stuff was not supported or 3rd party stuff was turned off etc. I expected that from seeing before. 

Os booted both win xp and ubuntu OK. 

When in winxp i can see my 40G data partition. 
But when I go into ubuntu now I don't see a way to mount it. It use to show up under Places.

I have 3 partitions. 
1 xp
2 ubuntu
3 data (shared from ubuntu/xp) 

all this use to work fine. 

But now I cannot mount my xp or my data drives from the menu.


I do see the CD/floppy Pictures etc but not the 2 40G drives. 
What do I need to do? 

I am still checking this out to see what else might be broken. I noticed that virtual box broke again but I should be able to resolve that. 

I noticed the menu bars are different now too. I am not sure I like the placement of the close box on the left side.  I am use to them being in the upper right. 

Can I put them back on the right?

---

### Post by dino99 on 2010-05-06
install and tweak MountManager

sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by unix1adm on 2010-05-06
> **dino99 said:**
> install and tweak MountManager

sudo apt-get install -f
sudo dpkg --configure -a

can you explain more on this? 
Not familiar whats this is. 

Thank you

---

### Post by unix1adm on 2010-05-06
Why do i get this. Looks like my ssh is broken too

apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libjline-java libvncserver0 libyaml-0-1 rhino sdparm
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 2,023kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 244053 files and directories currently installed.)
Removing rhino ...
Removing libjline-java ...
Removing libvncserver0 ...
Removing libyaml-0-1 ...
Removing sdparm ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Setting up openssh-server (1:5.3p1-3ubuntu3) ...
invoke-rc.d: unknown initscript, /etc/init.d/ssh not found.
dpkg: error processing openssh-server (--configure):
 subprocess installed post-installation script returned error exit status 100
dpkg: dependency problems prevent configuration of ssh:
 ssh depends on openssh-server; however:
  Package openssh-server is not configured yet.
dpkg: error processing ssh (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 openssh-server
 ssh
E: Sub-process /usr/bin/dpkg returned an error code (1)


I tried to remove it and it wont let me.

I was able to remove it but cannot install it. Also the commands above did nothing for my partition mounting issue i originally had.

---

### Post by unix1adm on 2010-05-06
apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  language-pack-gnome-en
The following packages will be upgraded:
  libkpathsea5
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 130kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main libkpathsea5 2009-5ubuntu0.1 [130kB]
Fetched 130kB in 2s (49.1kB/s)       
(Reading database ... 243979 files and directories currently installed.)
Preparing to replace libkpathsea5 2009-5 (using .../libkpathsea5_2009-5ubuntu0.1_i386.deb) ...
Unpacking replacement libkpathsea5 ...
Setting up libkpathsea5 (2009-5ubuntu0.1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@clt:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  language-pack-gnome-en
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

---

### Post by unix1adm on 2010-05-06
apt-get install -f openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  rssh molly-guard openssh-blacklist openssh-blacklist-extra
The following NEW packages will be installed:
  openssh-server
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/285kB of archives.
After this operation, 778kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package openssh-server.
(Reading database ... 243979 files and directories currently installed.)
Unpacking openssh-server (from .../openssh-server_1%3a5.3p1-3ubuntu3_i386.deb) ...
Processing triggers for ureadahead ...
Processing triggers for ufw ...
Processing triggers for man-db ...
Setting up openssh-server (1:5.3p1-3ubuntu3) ...
invoke-rc.d: unknown initscript, /etc/init.d/ssh not found.
dpkg: error processing openssh-server (--configure):
 subprocess installed post-installation script returned error exit status 100
Errors were encountered while processing:
 openssh-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by unix1adm on 2010-05-06
This seemed to work for my ssh issue but I still have the orginal issue of the mounting 

sudo dpkg --purge ssh
sudo dpkg --purge openssh-server
sudo apt-get install ssh

---

### Post by unix1adm on 2010-05-06
So I got mount manager to install now have to figure it out. 

But my real quewstion is what doesnt this work like it did in 9.10? 
I really dont want to have to launch another program to get my disk to mount. It was so simple before.

---

### Post by unix1adm on 2010-05-06
so i made some progress. Now when I go to the Places menu and look at the Computer is shows my 2 disks. I can double click on them and open them.

I can unmount the data disk fine.
But when I try to unmount the xp partition it says i am not root and I cannot unmount it. 

When I was in U9.4 it would ask me for the root passwd before it would mount the drive. I liked that so I could not accidentally mount it. 

Now I dont get asked for a passwd but I cannot unmount one of them. 

Seems strange.

if i login to an xterm and su to root i can unmount the drive fine.

---

### Post by unix1adm on 2010-05-07
ok may be i need a new topic as no one is responding

---

### Post by unix1adm on 2010-05-10
No one has any idea why this is happening? 
so i made some progress. Now when I go to the Places menu and look at the Computer is shows my 2 disks. I can double click on them and open them.

I can unmount the data disk fine.
But when I try to unmount the xp partition it says i am not root and I cannot unmount it.

When I was in U9.4 it would ask me for the root passwd before it would mount the drive. I liked that so I could not accidentally mount it.

Now I dont get asked for a passwd but I cannot unmount one of them.

Seems strange.

if i login to an xterm and su to root i can unmount the drive fine.

---

