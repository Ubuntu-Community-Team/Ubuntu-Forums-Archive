---
title: "Problem creating an bootable USB drive for installing Ubuntu 11.04"
date: 2011-08-21
forum: Installation &amp; Upgrades
---

### Post by leopoldbirkholm on 2011-08-21
Dear follow members,

I have an netbook, a small Asus Eee PC model 1001 PX running Ubuntu 10.04 LTS. It don't have an optical drive so I wish to make an bootable installation disk with an USB flash drive.

I followed the guide on Ubuntus homepage ([http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) -> How to make an USB drive).

But it did not work. I have an standard 4 GB USB flash drive which is plugged in. I have formatted it to FAT. And it is now empty.

I went to System > Administration -> opened 'Startup Disk Creator'.

I pushed in all the options. But then the system asked for a password. No worries, I thought. It must be my own. But it was not.

So my problem is that I am missing a password in order to authorized the installation of Ubuntu 11.04 on the USB drive.

My question is if this is a know problem? And if so, what are A. the proper search phrase for it? and B. what are the solution?

Kind regards
Leopold
):P

---

### Post by sanderd17 on 2011-08-21
It should be your password, if you're able to become root.

Are you able to install software on that Ubuntu system?

---

### Post by leopoldbirkholm on 2011-08-21
> **sanderd17 said:**
> It should be your password, if you're able to become root.

Are you able to install software on that Ubuntu system?

So, I need to be a root in order to create this USB flash startup disk?

Yes, I am able to install other software on my system with my password.

---

### Post by dino99 on 2011-08-21
unetbootin is easier

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://wiki.geteasypeasy.com/How_to:_Using_Unetbootin](http://wiki.geteasypeasy.com/How_to:_Using_Unetbootin)

---

### Post by sanderd17 on 2011-08-21
> **leopoldbirkholm said:**
> So, I need to be a root in order to create this USB flash startup disk?

Yes, it's because the USB startup disk creator can use some partition commands that require root.


You can try Unetootin as Dino said.

---

