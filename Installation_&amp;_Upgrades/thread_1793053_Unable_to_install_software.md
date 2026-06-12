---
title: "Unable to install software"
date: 2011-06-28
forum: Installation &amp; Upgrades
---

### Post by ExTruckie on 2011-06-28
I just reinstalled 10.04LTS on my server box. while trying to install mdadm I got the following error below.


[B]Previous installation hasn't been completed

The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software.[/B]  

How do I go about repairing the install???

---

### Post by zvacet on 2011-06-29
Try with 

```
sudo dpkg --configure -a 
sudo apt-get -f install
```

---

### Post by nomko on 2011-06-29
> **ExTruckie said:**
> I just reinstalled 10.04LTS on my server box. while trying to install mdadm I got the following error below.

 
Did you do a fresh, fully new install or did you reinstalled the new installation over the old installation? You might get this message if you overwrite the existing installation with the new installation and encounter some files which are newer (due to updates) then the ones off the new setup.

---

### Post by ExTruckie on 2011-06-29
> **nomko said:**
> Did you do a fresh, fully new install or did you reinstalled the new installation over the old installation? You might get this message if you overwrite the existing installation with the new installation and encounter some files which are newer (due to updates) then the ones off the new setup.

I did an install of 9.04 then upgraded to 9.10 then to 10.04.2LTS. I did download and burn both the 10.04.2LTS and 11.04 from the website and when I tried to install from the disk I would get an error of " No kernel found" This was true fro 11.04.  

I tried zvacet's suggestion and all I get is this error, 
mark@Fileserver:~$ sudo dpkg --configure -a 
dpkg: parse error, in file '/var/lib/dpkg/updates/0000' near line 0:
 newline in field name `

I found an older disk I had burnt of 10.04. I'll Try to install that over the weekend.

---

### Post by nzjethro on 2011-06-29
> I tried zvacet's suggestion and all I get is this error, 
mark@Fileserver:~$ sudo dpkg --configure -a 
dpkg: parse error, in file '/var/lib/dpkg/updates/0000' near line 0:
newline in field name `

Hi there, to resolve this, you need to clear your updates folder, as it has a partially installed package in it which would be causing you trouble. Try:

```
sudo rm /var/lib/dpkg/updates/0000
dpkg --configure-a
apt-get update
```

Then install whatever it was you were installing.

---

### Post by ExTruckie on 2011-06-29
Well nzjethro I did as you suggested and had to do the first line about 8 times before I got this 
[B]root@Fileserver:~# sudo rm /var/lib/dpkg/updates/0013
rm: cannot remove `/var/lib/dpkg/updates/0013': Input/output error
[/B]I cannot go any further. I can wait until the weekend to do a reinstall. I think that is my best bet.  
Thanks.

---

### Post by nzjethro on 2011-06-29
OK, so it sounds as though you have more than one partial package in there. Try deleting and recreating the entire /.../updates folder. Run:
```
sudo rmdir /var/lib/dpkg/updates
sudo mkdir /var/lib/dpkg/updates
```

Then try again to configure dpkg with:
```
dpkg --configure-a
```

Then install your packages:
```
sudo apt-get update
sudo apt-get install mdadm
```

Hopefully purging the entire directory then recreating it will stop the issue.

---

### Post by mörgæs on 2011-06-29
Creating a root user is not recommended:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ExTruckie on 2011-06-30
Well I cant rmdir since it is not empty and since it is read only I am unsure how to do it

I tried the following and I am confused

[B]root@Fileserver:~# sudo rmdir /var/lib/dpkg/updates
rmdir: failed to remove `/var/lib/dpkg/updates': Directory not empty[/B]

[B]root@Fileserver:~# chmod 777 /var/lib/dpkg/update
chmod: cannot access `/var/lib/dpkg/update': No such file or directory
[/B]
What is confusing me is I cannot remove the directory because it is not empty of read only files and if I try to change the file permissions it says the directory does not exist. 

I read that chmod 777 isnt recomended but I want to wipe it out anyway so it dont matter. :P

---

