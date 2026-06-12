---
title: "can't open odt files from network after upgrading to 10.04"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by richardd73 on 2010-05-09
Hello,

Yesterday i upgraded from ubuntu 9.10 to 10.4.
Everthing went well, all works as expected. (like the new interface)

But i have one problem, i can't open odt files from my network share.

Every time i try to open an odt or ott file Openoffice displays the  following error message:
OpenOffice.org Document Recovery
Due to an unexpected error, OpenOffice.org crashed. All the files you were working on will now be saved.
The next time OpenOffice.org is launched, your files will be recovered automatically.
The following files will be recovered:

When i copy these files to the local disk, i can open them without a  problem.
Opening doc / xls / ods works fine.

The odt files are located on a samba share, and mounted in my home dir  using cifs.

Already, completly uninstalled Openoffice and reinstalled  (ubuntu)Openoffice, no luck.
Also completly uninstalled Openoffice, and installed latest OpenOffice version from  openoffice.org. (3.2.0 build 9483)

I found a post (on debian forum) with similar problem  [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=573949](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=573949)

Please help,

Thanks in advance.

---

### Post by starfish_2008 on 2010-05-10
I have had the exact same problem.  My network connection is also samba with the network mounted on my home directory using cifs (incidentally the only reason I have it locally mounted is to take advantage of google desktop).

I have uninstalled & reinstalled OOo three times.  I even did a clean reinstall of 10.04 all to no avail.

Connecting to the same network using SSH I have no problems with OOo.

Thanks for your help.

---

### Post by elfunesto on 2010-05-17
Hi,
I have a similar problem here. However, to be a bit more precise, only some ods (same thing for odt) cause problem: on the same network some ods can be open whereas others cause a crash (while I am able to open a copy on my local drive).
By deleting columns or graphs in the local copy and then copying it again in the network, I was able to re-open the file from network. However, I can't understand why those columns or graphs cause a crash, and why the crash only occur on cifs network.
Cheers

---

### Post by ridgerun on 2010-05-17
Having the same problem after upgrading to 10.4.  If I copy the file onto my
local HD then it works fine.

---

### Post by elfunesto on 2010-05-18
I would like to add that the problem occur with both oOo from the repository and the official version.

---

### Post by elfunesto on 2010-05-18
Moreover, if the ods file is converted in xls, it can be opened without any problem.
Cheers

---

### Post by elfunesto on 2010-05-18
I have just wrote a bug report in launchpad
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/582287](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/582287)
Cheers

---

### Post by elfunesto on 2010-05-19
Hi,
I solved my problem by using the nobrl when mounting the network drive 

in fstab
//machine/partition    /media/Sauvegarde    cifs    nobrl,credentials=/root/.smbcredentials,uid=1000,gid=100,rw,iocharset=utf8     0    0
 with sudo mount
 hilaire@hilaire-desktop:~$ sudo mount -t cifs  //machine/partition /media/Sauvegarde -o nobrl,uid=1000,gid=100,file_mode=0640,dir_mode=0750,iocharset=utf8,credentials=/root/.smbcredentials


 Hope that help!
Cheers

---

### Post by mdotenjr on 2010-05-19
> **elfunesto said:**
> Hi,
I solved my problem by using the nobrl when mounting the network drive 

in fstab
//machine/partition    /media/Sauvegarde    cifs    nobrl,credentials=/root/.smbcredentials,uid=1000,gid=100,rw,iocharset=utf8     0    0
 with sudo mount
 hilaire@hilaire-desktop:~$ sudo mount -t cifs  //machine/partition /media/Sauvegarde -o nobrl,uid=1000,gid=100,file_mode=0640,dir_mode=0750,iocharset=utf8,credentials=/root/.smbcredentials


 Hope that help!
Cheers
THANK YOU!!! This works perfectly! THANK YOU! THANK YOU! What a relief. I can't tell you how many times I had to copy network documents to my desktop just to work on them, and then paste them back when I was done.

Just to clarify the nobrl is what fixed my fstab.  Here is how I  implemented it.
//machine/sharename /mountdirectory/mountfolder cifs  nobrl,credentials=/etc/.smbcredentials,file_mode=0777,dir_mode=0777    0        0

---

### Post by miquel6 on 2010-06-18
Thanks also!

The workaround by elfunesto worked for me

---

### Post by mdotenjr on 2010-06-24
Just to clarify the nobrl is what fixed my fstab.  Here is how I implemented it.
//machine/sharename /mountdirectory/mountfolder cifs nobrl,credentials=/etc/.smbcredentials,file_mode=0777,dir_mode=0777    0       0.

---

