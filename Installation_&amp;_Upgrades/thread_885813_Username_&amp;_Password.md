---
title: "Username &amp; Password"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by jdavid21 on 2008-08-10
:confused::confused:I have just completing installing Ubuntu, and the only screen i get is a username and password. 
I have never added a username or password, is there a temp username & password?
If not do i need to delete and reinstall?

---

### Post by Pumalite on 2008-08-10
In the process of installing you are ALWAYS asked for a username and a password. Maybe you made a mistake.

---

### Post by jdavid21 on 2008-08-10
If I did i don't recall, is there any way to remove what is there?

---

### Post by lukjad on 2008-08-10
Yes, you can do this.

The username should be easy enough to find out. In a live CD go to the /home folder and look at the names of the files that are there. one of them should look familiar, i.e. janesmith and that, most likely will be your username to use in this next step.

For the record, I have never tried this next step. However, since you really have nothing to loose and much to gain, try it out. This should reset your password.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by phuchu on 2008-11-02
PUMALITE:

NO! I installed Ubuntu as well and was NEVER asked to choose a username or password. I choose the "Install Ubuntu without making any changes to your computer"

I was never asked ANYTHING about choosing a username and passwrd and was presented with a username: screen. Cannot login. VERY LAME!!!

I've spent the last 30 minutes trying to find out the default username / password and gave up. I have just tossed the disk in the trash and am moving on to the next distro.....

---

### Post by Pumalite on 2008-11-02
A Live CD should never ask you for a username and password.
Burn a new CD. Do md5sum on iso, burn at 4x or less. Do not use CD-RW
Download ImgBurn:
[http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
Install it.
Go to Mode>ISO>Burn
Select 1x as the speed of burn. Clean the lens in your burner

---

### Post by phuchu on 2008-11-02
Ok. I'll give that a shot right now and report back. 

Thanks.

---

### Post by phuchu on 2008-11-02
Any idea what the hash should be. Can't find it anywhere.

---

### Post by phuchu on 2008-11-02
Found it... 

24ea1163ea6c9f5dae77de8c49ee7c03

---

### Post by Pumalite on 2008-11-02
ea6d44667ea3fd435954d6e1f0e89122 *ubuntu-8.10-alternate-amd64.iso
f9e0494e91abb2de4929ef6e957f7753 *ubuntu-8.10-alternate-i386.iso
f9cdb7e9ad85263dde17f8fc81a6305b *ubuntu-8.10-desktop-amd64.iso
24ea1163ea6c9f5dae77de8c49ee7c03 *ubuntu-8.10-desktop-i386.iso
8d35fea8c16597a6f4dd07f8e18e2166 *ubuntu-8.10-mid-lpia.img
e3028a105a083339be8e5af5afbe7444 *ubuntu-8.10-server-amd64.iso
a2ec9975a91e1228c8292ed9799dc302 *ubuntu-8.10-server-i386.iso
2796c696ab368415a30fddc8278e08b0 *wubi.exe

---

