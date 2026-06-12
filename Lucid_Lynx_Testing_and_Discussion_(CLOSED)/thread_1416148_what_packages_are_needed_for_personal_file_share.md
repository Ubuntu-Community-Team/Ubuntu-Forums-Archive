---
title: "what packages are needed for personal file share?"
date: 2010-02-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lime4x4 on 2010-02-25
I want to have a folder shared among all my computers. But when i got to personal file share it tells me that the packages aren't installed

---

### Post by cariboo on 2010-02-25
I just tried this, earlier today, Samba and libpam-smbpass are installed, at least on my system. I had to change the workgroup name in /etc/samba/smb.conf, as I don't use the default WORKGROUP.

Just in case I created a samba password using the following commands:

```
smbpasswd -L -a <user>
```

to add the user, and

```
smbpasswd -L -e <user>
```

to enable the user. You'll probably get a bunch of errors about converting the database, but just ignore them, as on the last line it should say added <user> to the database.

---

### Post by nanog on 2010-02-26
If you want to share the easiest approach is to just right click on the folder and select sharing options. Follow instructions and don't tick the two options and its reasonably secure. I personally don't use samba as its too slow for my use cases. Kerberos NFS rocks.

---

### Post by emarkay on 2010-02-26
I just tried to do so again today, for the first time in a while.  Nope, nothing.

Oh, do a search, I haven't gotten Ubuntu to network for years - and my attempts at solving this, including getting 2 fresh Karmic PC's to test were ignored.

My detailed bug report was* turned into a question*; purged from Launchpad!

I am not a computer genius, but have been around them since the AppleII and I know enough to continue to blame the Ubuntu OS's configuration for networking (relying on third party apps)  and the incomplete and abhorrent documentation (I volunteered to help with that, too!)

So anyway, good luck - I'll be monitoring this thread to see how it goes...
MRK

---

### Post by cariboo on 2010-02-26
Getting samba to work is fairly simple, in most cases you have to have the basics down first before setting up samba.

Make sure the computers on the network can see each other first, they all have to be in the same netblock. I use 192.168.1.1 - 192.168.1.254. Next make sure you can ping all the systems on the network. To use ping on Windows you have to open the command shell, and type for example ping 192,168.1.100. While using Ubuntu you can doit at least two different ways, from the command line or from System->Administration->Network Tools->Ping. Once you done that, make sure all the systems are in the same workgroup.

You change change the workgroup in Windows XP by going to Start->Control Panel->System->Computer Name. In Ubuntu again there is at least two ways of changing the workgroup name:

[list=1]
[*] manually edit /etc/samba/smb.conf
[*] system-config-samba
[/list]

Once you have done the above, you will have to set up shares properly on your Windows system, and you can use system-config-samba to set up the shares on your Ubuntu computer.

Once finished setting things up just reboot all the systems and you should be good to go.

---

### Post by nanog on 2010-02-26
You should be able to see your share on places ==> network ==> Windows Network. Or you can just browse to smb:/// in nautilus. If your share shows up there but is still inaccesible in windows you need to make sure that windows and ubuntu are using the same workgroup/subnet (see cariboo's post).

---

