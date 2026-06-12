---
title: "Need help installing smbfs package"
date: 2005-06-27
forum: Installation &amp; Upgrades
---

### Post by tod whitehurst on 2005-06-27
Hello

I’m a windows techsupport guy who is trying to learn linux so I can tell Bill Gates to go to you know where.   I hope Ubutu will allow me to migrate my computers to the linux platform.  

I’m using Ubutu 5.04 with Gnome 2.10. 

My  first problem is trying to attach to our Network Attached Storage device.  Our share has been Samba enabled so as to allow access from both Windows and Mac computers.  Through Gnome I am able to connect to the server Places-Connect to Server-Custom Location using the URI smb://skipper.cc.vt.edu/provoff.  This does allow me to view my files.  However I cannot edit them nor open them I’m not even able to copy them to the desktop.  When I try to copy them I get the error message ‘Error:  “not a directory” while copying “smb://skipper.cc.vt.edu/provoff[then my filename]’.  

I have attempted to use the instructions on your website at [https://wiki.ubuntu.com/SettingUpSamba](https://wiki.ubuntu.com/SettingUpSamba) but with no success.  I have been able to install the Samba package but not the smbfs package.  I receive the error message when I attempt to install smbfs which reads:

“Package sambfs is not available but is referred to by another package.  This may mean that the package is missing, has been obsoleted or is only available from another source”.

When I try to use the smbmount command I get a 'bad command ' error

All of my linux support people say to use a command:

mount -t smbfs -o
username=PID/HOKIES,uid=localuser //skipper.cc.vt.edu/provoff /mnt/st (replace PID with PID and localuser with a local account that you want to have access to these files.  Also, replace /mnt/st with directory for the mount to mount to)

When I use this command I get an error “wrong fs type…”

I am most certainly a linux newbie so correct me if I’m wrong but it doesn’t seem that smbfs has been installed on my box.  If someone could lend a hand I would appreciate it.  I’ve worked on it for over a week know and I’m just not figuring it out.

Thanks

Tod

---

### Post by Mr. Electric Wizard on 2005-06-27
Ok, I just went through this and have now updated my /etc/fstab to mount remote folders on startup... :) 
The only thing that I see that is wrong with this code is that:

mount -t smbfs -o
username=PID/HOKIES,uid=localuser //skipper.cc.vt.edu/provoff **_/mnt/st_** (replace PID with PID and localuser with a local account that you want to have access to these files. Also, replace /mnt/st with directory for the mount to mount to)

the underline bold text is pointing to a file.  You need to put "/" at the end of /mnt/st.  It should look like /mnt/st/ so that Linux knows that this is a directory...
Try that and see if it works.

---

### Post by tod whitehurst on 2005-06-27
Ok I tried putting a slash at the end of the command.

I still get the same error "wrong fs type..."

Did I need to make any changes in my etc/fstab?

---

### Post by Mr. Electric Wizard on 2005-06-27
This was the thread that "got me there".
Thanks vnBuddy2002!

[http://www.ubuntuforums.org/showthread.php?t=26438&highlight=mount+smb+boot](http://www.ubuntuforums.org/showthread.php?t=26438&highlight=mount+smb+boot)

---

### Post by Mr. Electric Wizard on 2005-06-27
[QUOTE=tod whitehurst]Ok I tried putting a slash at the end of the command.

I still get the same error "wrong fs type..."

Did I need to make any changes in my etc/fstab?[/QUOTE]

I think you only need to put lines in the fstab if you want the remote folders to be loaded at boot.

---

### Post by tod whitehurst on 2005-06-27
I really think the problem here is that I can't install the the smbfs package.

I've tried:
apt-get install smbfs- Failed
sudo apt-get intall smbfs - Failed

error:

“Package sambfs is not available but is referred to by another package.  This may mean that the package is missing, has been obsoleted or is only available from another source”.

---

### Post by Mr. Electric Wizard on 2005-06-27
Have you added the extra repositories yet?

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) 

I would have thought they would be in the default repository, but maybe not...
Can you ping the gateway, etc.?

---

### Post by tod whitehurst on 2005-06-27
I have not installed extra repositories I'll look into that.

I did do

apt-get update

and that seemed to work fine

---

### Post by tod whitehurst on 2005-06-27
Thanks everyone for their help

I will be leaving the office till tomorrow

T

---

### Post by tod whitehurst on 2005-06-28
Thanks everyone 

Adding the extra repositories did the trick.

Case Closed

---

### Post by Mr. Electric Wizard on 2005-06-28
Cool! :razz: 
I love it when a plan comes together...

---

