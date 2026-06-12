---
title: "Samba few issues"
date: 2017-04-24
forum: Installation &amp; Upgrades
---

### Post by sp40140 on 2017-04-24
What I have done so far:
First I tried GADMIN-SAMBA. But I found it too complicated. And it added way too many parameters in the config file. So, I reverted to default config and started over using this page: "https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated%2C%20Simple%20and%20Brief%20Way!"

I created a new user in ubuntu called : smbguest. and set-up both passwords (samaba and account).

Symptoms:
On a different Ubuntu laptop, I can't even see the samba server.
On win7 I can't see it in network but I can put the server and the shared directory on address bar but can't log-in with samba user (smbguest). I get access denied error.
I can see the server and the shared directory on ipad apps / android apps. But I can't open the directory. I don't get any errors here.

My smb.conf file without comments:

```

  1 [global]
  2 
  3    workgroup = workgroup
  4     server string = %h server (Samba, Ubuntu)
  5     dns proxy = no
  6     name resolve order = lmhosts host wins bcast
  7 
  8     ntlm auth = no
  9     lanman auth = no
 10     client ntlmv2 auth = yes
 11 
 12     log file = /var/log/samba/log.%m
 13     max log size = 1000
 14     panic action = /usr/share/samba/panic-action %d
 15     server role = standalone server
 16     passdb backend = tdbsam
 17     obey pam restrictions = yes
 18     unix password sync = yes
 19     passwd program = /usr/bin/passwd %u
 20     passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
 21     pam password change = yes
 22     map to guest = bad user
 23 
 24 [printers]
 25    comment = All Printers
 26    browseable = no
 27    path = /var/spool/samba
 28    printable = yes
 29    guest ok = no
 30    read only = yes
 31    create mask = 0700
 32 
 33 [print$]
 34    comment = Printer Drivers
 35    path = /var/lib/samba/printers
 36    browseable = yes
 37    read only = yes
 38    guest ok = no
 39 
 40 [DELL-M]
 41         comment = DELL-M
 42         path = /media/dell/DELL-M
 43         read only = no
 44         writeable = yes
 45         valid users = smbguest
 46        browseable = yes

```


I did have samba working on 16.10 but I did fresh install of 17.04 and now struggling with this.
Help.

---

### Post by sp40140 on 2017-04-25
@Mods
Kindly move this thread to networking & wireless.

---

### Post by sp40140 on 2017-04-25
I got this working but that's not the set-up I want.
I have isolated the issue to the "user".
So, I had created a new user for samba called : smbguest. I had set-up password for it as well using smbpasswd command (infact I used sudo smbpasswd -a smbguest) to create the user and set samba password.
That didn't work.
So, on a hunch, I set the samba password for the main user for the computer (called "dell"). And that worked. I can access the shares if I use "dell" account the it's password.
However, I do not want to use that id. I'd rather use the dedicated user which I created. 
And I can't find anything special which needs to be done for that user to work on internet.
Please help.
Quick Edit:
There is "smbusers" file in /etc/samba. It contains:
```

# Unix_name = SMB_Name1 SMB_Name2 ...
root = administrator
nobody = guest smbguest pcguest

```

---

### Post by Morbius1 on 2017-04-25
>  So, on a hunch, I set the samba password for the main user for the  computer (called "dell"). And that worked. I can access the shares if I  use "dell" account the it's password.
It's because of this:
> [DELL-M]
 41         comment = DELL-M
 42         [COLOR=#0000cd]**path = /media/dell/DELL-M**[/COLOR]
 43         read only = no
 44         writeable = yes
 45         valid users = smbguest
 46        browseable = yes
/media/$USER ( in this case /media/dell ) is created by the system not you and it's created such that only $USER ( dell ) can get past that folder to what is under it. This is by design.

One way to fix this is to make "smbguest" look like "dell":
> [DELL-M]
 41         comment = DELL-M
 42         [COLOR=#0000cd]**path = /media/dell/DELL-M**[/COLOR]
 43         read only = no
 44         writeable = yes
 45         valid users = smbguest
      [COLOR=#0000cd]**force user = dell**[/COLOR]
 46        browseable = yes
"valid users" will still reject all users except smbguest but once his credentials are accepted everything he does will be as "dell" - at least for that share.

---

### Post by sp40140 on 2017-04-25
Ohh..ok. I don't think i want to force the user as I want to have two different sets of privilegs fo both of the dell and smbuser.
What other place is good idea to mount these drives?

---

### Post by Morbius1 on 2017-04-25
One level up: /media/DELL-M

---

### Post by sp40140 on 2017-04-25
I have been looking around. i don't think that dell under media is system created. in fact i have added entries in fstab for these three drives and added the location. i can simply change it to something else.
i think something else is doing it.

---

### Post by Morbius1 on 2017-04-25
If dell is a user name /media/dell is created by the system automatically. It does that so you have a mount point for inserted usb storage devices for example or if you have internal partitions not defined in fstab

---

### Post by sp40140 on 2017-04-25
Ok. I will try to create a folder along side of dell and mount the drivers there.
I guess that should fix it.
I thank you for your help.

---

### Post by sp40140 on 2017-04-25
@morbius1
BIG Thank you. It worked. I just created a new folder under /media (same level as user "dell") and changed the fstab to mount the drives there and it worked.

Now while I have you helping me, one more question.
As you already know, I have two users 1] dell (admin) 2] smbguest (guest).
I want to provide smbguest with READ-ONLY. "dell" needs to be read & write.
From the config I have I am not sure how do I do that. 
I know that I can add users in "valid users" tag separated by space like "valid users = smbguest dell" but how do I manage different privileges for same share?
```

[DELL-M]
        comment = DELL-M
        path = /media/DATA/DELL-M
        writeable = yes
	valid users = smbguest
        browseable = yes

```

---

### Post by Morbius1 on 2017-04-26
You have a couple of options:

**[1] Use the "write list" option**

> [DELL-M]
        comment = DELL-M
        path = /media/DATA/DELL-M
        [COLOR=#0000cd]**writeable = no**[/COLOR]
        [COLOR=#0000cd][B]valid users = smbguest, dell
      write list = dell[/B][/COLOR]
        browseable = yes
By default this will be a read only share - except to dell.

**[2] Make two different shares of the same folder - one admin one not:**

For Guests:
> [DELL-M]
        comment = DELL-M
        path = /media/DATA/DELL-M
        [COLOR=#0000cd]**writeable = no**[/COLOR]
        valid users = smbguest
        browseable = yes

For Admin:
> [[COLOR=#0000cd]**DELL-M-Admin**[/COLOR]]
        comment = DELL-M
        path = /media/DATA/DELL-M
        [COLOR=#0000cd]**writeable = yes**[/COLOR]
        [COLOR=#0000cd]**valid users = dell**[/COLOR]
        browseable = yes
You can even set the [DELL-M-Admin] share to "broseable = no" so that no one can see it when they browse your machine. The dell user will have to specify it explicitly to gain access.

---

### Post by sp40140 on 2017-04-26
Thank you Morbius1.
I will try with fine tuning later. 
Marking this SOLVED as I have working share now.

Cheers,

---

