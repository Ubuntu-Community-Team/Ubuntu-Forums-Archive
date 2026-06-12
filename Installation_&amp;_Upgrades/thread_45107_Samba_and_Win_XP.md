---
title: "Samba and Win XP"
date: 2005-06-28
forum: Installation &amp; Upgrades
---

### Post by edacsac on 2005-06-28
Hi all,

I'm trying to connect to my Ubunto 5.04 machine from XP. I can browse and open all of my windows machines from Ubuntu, but I cannot hit Ubuntu from my windows XP macnines. I see the Ubuntu server in my workgroup, but when I try to access it, it asks for ID and password repeatedly without success. 

I followed the installation instructions via the ubuntuguide, and went the through SettingUpSamba wiki guide over and over again. The only thing that failed in the wiki guide, was the part about mounting a share - (32237: session setup failed access denied), the example was for smbmount //myserver/myshare  /home/yourusername/mnt, and in where it explains configuring your computer, there is no "windows networking" under system->administration->networking->general tab. Everything else is set as the guides say. The smbusers file I added system_username = "username" (with the quotes like the guide stated, but my own user), edited smb.conf according to the guide, and added my user via smbpasswd many times. 

***EDIT
I've also found the shared folder settings under adminstration and found the general windows sharing settings to be correct as well.

I'm out of ideas, I've been working on this for 4 days now, and very frustrated. I'm at the point of delete/reinstall. Please help!

---

### Post by sonny on 2005-06-28
Try this and then report the results cuse I'm not 100% sure this is your problem:

1.- Add a user that is within your group in your ubuntu machine, set password and everything.
2.- Then create a samba-user for the account you've just made:
> code:
$ sudo smbpasswd -a 'whoami'
3.- Go to your smb.conf file (it's located in /etc/smb/smb.conf), find the folder you're trying to share (ussualy at the end of the file), and add the following lines:
> browseable = yes
writable = yes (if you want users to read and write, if not, don't use this line)

That would be all... I hope this will help you.

---

### Post by edacsac on 2005-06-28
Thanks sonny,

New user added, and setup for samba with smbpasswd. Now it looks like I authenticate with the new user, but I get a path not found. I know the path is right, so I guess I can move on to troubleshooting something else now!

***EDIT

I can get there through my network neighborhood equivilent in XP, so I'm good there, Thank you! I noticed my sudo user that was setup when I installed ubuntu (which I was using for smb) was in a group of the same name as the user. I thought that was odd. But, I can't map a drive. First it was path not found, now, without any changes, it doesn't authenticate. Whats up with that?

BTW, if you have any suggestions for the path not found, I'd be happy to hear them!

Thanks again!

---

### Post by sonny on 2005-06-29
[QUOTE=edacsac]Thanks sonny,

New user added, and setup for samba with smbpasswd. Now it looks like I authenticate with the new user, but I get a path not found. I know the path is right, so I guess I can move on to troubleshooting something else now!

***EDIT

I can get there through my network neighborhood equivilent in XP, so I'm good there, Thank you! I noticed my sudo user that was setup when I installed ubuntu (which I was using for smb) was in a group of the same name as the user. I thought that was odd. But, I can't map a drive. First it was path not found, now, without any changes, it doesn't authenticate. Whats up with that?

BTW, if you have any suggestions for the path not found, I'd be happy to hear them!

Thanks again![/QUOTE]
I don't understand what you mean with mapping a drive; wich drive are you talking about? your harddrive, your floppy, or CD-rom?? Cuz I'm not sure what you meant.

---

### Post by edacsac on 2005-06-29
I guess mapping a drive is windows speak. Better wording would be mounting a share, or attaching the share to a drive letter in windows. Although that is working now. The only thing I can't do at the moment is to access the share from the run line in windows. I get a path not found. But that doesn't matter right now.

Thanks again for your help sonny!

---

