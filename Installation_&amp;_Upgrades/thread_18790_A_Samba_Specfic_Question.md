---
title: "A Samba Specfic Question"
date: 2005-03-08
forum: Installation &amp; Upgrades
---

### Post by dwanders on 2005-03-08
Using the Warty CD, and a fresh installation of the OS. (Note: I would like to keep this OS in its supported mode (i.e. I want to leave the apt repositories with just main & security enabled)). 

How would one go about joining a Windows NT4.0 Domain? 

I have not installed any extra packages. nor have I modified the original smb.conf file in any way. As it stands with this clean install, I can do the following: 

Click on  Computer > Network > (after some thinking) Windows Network > Where pretty quickly I see all my WorkGroups & Domains, so I click on one Domain > Which opens and I can now see all the computers in my selected Domain, so I click on one of them [one that I specifically know has a many public shares] & I get "You do not have the sufficent permissions necessary to view the contents of Windows Network: ServerName"
 
I also have not modified my network settings in: Computer > Sytem Configuration > Networking > General TAB. It is as it was after the install (Windows Networking is unchecked).

I have been searching many sources for information regarding this, and I see many ways to set up your Linux Box as a Samab Server, [which I will eventually will want to do] but for right now, all I want to do is joint this Ubuntu Workstation to the Windows NT4 Domain so I can participate in the Domain as a memeber.

Thanks in advance for any replies.

---

### Post by hndrcks on 2005-03-08
There is a problem with samba connections in Warty that is fixed in Hoary. For the time being however:

When you are on the network screen type ctrl-L

in the box type smb://servername/sharename (share name is important here)

You will then get login prompt for user password domain.

Technically, this isn't 'joining the domain'; but you can get to shares etc in this manner.

---

### Post by ubuntu_demon on 2005-03-09
[QUOTE=hndrcks]There is a problem with samba connections in Warty that is fixed in Hoary. For the time being however:

When you are on the network screen type ctrl-L

in the box type smb://servername/sharename (share name is important here)

You will then get login prompt for user password domain.

Technically, this isn't 'joining the domain'; but you can get to shares etc in this manner.[/QUOTE]
 what exactly is this problem ? because I also have problems with samba

---

### Post by dwanders on 2005-03-09
I have tried the Ctrl-L (or File > Open Location from Network Menu) and followed the instructions [smb://servername/share return - prompted for username, doamin, and password] after a very long time, it does open the share. Everything is running pretty slow though (even opening sub-directories for a share I have already connected to). I cant help but feel that if I could join the Domain it would work smoother and faster.

Thanks for the input, and that helps some, but I would still like to try and learn to join the Domain if anyone has some suggestions.

By the way, do you know where the steps above actually mount the share? So I can get to it from the console?

---

### Post by dwanders on 2005-03-09
Well, while I am waiting for any suggestions or responses I felt it was my obligation to try and find some answers to my original question, I figured I would try and look into the problem as best I can. So I started at the Samba web site (the official how-to for Samba 3) and the Unofficial Ubuntu guide. I believe I may have one of the first problems in Chapter 1 Installing and starting Samba of the official Samba-3 guide. 

The Unnofficial Guide to Ubuntu states that installing Samba consists of:
sudo apt-get install samba 
sudo apt-get install smbfs
(I also installed the recomended samba-doc with sudo apt-get install samba-doc) 

Once I finished installing those, I returned to the Samba guide and learned that in order to have a complete Samba server at boot up, we will need the daemons:

nmbd 
smbd 
winbindd

So I checked for the three daemons
whereis nmbd
nmbd: /usr/sbin/nmbd /usr/share/man/man8/nmbd.8.gz
whereis smbd
smbd: /usr/sbin/smbd /usr/share/man/man8/smbd.8.gz
whereis winbindd
winbindd:

nada on the winbindd. 

So I checked with Synaptic (easier to search) and looked for winbindd. Synaptic returned that winbind (note there was no d for daemon which I noticed) should be installed with the samba package I installed earlier:

winbind: Service to resolve user and group information from Windows NT servers

Does anyone know where winbindd is? Without it, I do not believe that the samba computer can act as a member of a Domain or AD. Which I would think would be a crucial necessity for any desktop wishing to co-exsist in a Corporate environment that is dominated by MS. 
 
Thanks again in advance - I will continue my quest.

---

### Post by gungaden on 2005-03-09
Have you carefully reviewed your smb.conf file which is located within /usr/share/samba/ ?

---

### Post by dwanders on 2005-03-09
I figured for starters I should keep the /etc/samba/smb.conf file extreamly simple and build on it. The Samba documentation, starts with the following - straight out of the samba how-to (only set to my Domains): 

# Global parameters
[global]
    workgroup = CORP_NT
    netbios name = Ubuntu
    security = share

[data]
    comment = Data
    path = /export
    read only = Yes
    guest ok = Yes

testparm works fine.

But this does not explain where the winbindd daemon is after the installation of the Debian based Samba package.

---

### Post by dwanders on 2005-03-09
After looking closer at your reply, I do not believe that /usr/share/samba/smb.conf is the file that is being used by the system for samba. I believe that it is using /etc/samba/smb.conf.

---

### Post by joshpjones99 on 2005-05-10
[QUOTE=dwanders]Using the Warty CD, and a fresh installation of the OS. (Note: I would like to keep this OS in its supported mode (i.e. I want to leave the apt repositories with just main & security enabled)). 

How would one go about joining a Windows NT4.0 Domain? 

I have not installed any extra packages. nor have I modified the original smb.conf file in any way. As it stands with this clean install, I can do the following: 

Click on  Computer > Network > (after some thinking) Windows Network > Where pretty quickly I see all my WorkGroups & Domains, so I click on one Domain > Which opens and I can now see all the computers in my selected Domain, so I click on one of them [one that I specifically know has a many public shares] & I get "You do not have the sufficent permissions necessary to view the contents of Windows Network: ServerName"
 
I also have not modified my network settings in: Computer > Sytem Configuration > Networking > General TAB. It is as it was after the install (Windows Networking is unchecked).

I have been searching many sources for information regarding this, and I see many ways to set up your Linux Box as a Samab Server, [which I will eventually will want to do] but for right now, all I want to do is joint this Ubuntu Workstation to the Windows NT4 Domain so I can participate in the Domain as a memeber.

Thanks in advance for any replies.[/QUOTE]
 Ok I am having the same issue where is winbindd?

---

