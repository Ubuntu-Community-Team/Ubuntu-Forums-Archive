---
title: "How Do I Upgrade a Kernel?"
date: 2006-07-13
forum: Installation &amp; Upgrades
---

### Post by Wasca on 2006-07-13
Hello All

I get regular emails from the Ubuntu security announcment list, just recently I got an email about there being an update to the linux kernel.

So as any good Ubuntu user would do I do an apt-get update and then apt-get upgrade (I'm using Server not Desktop) What I don't understand is why is the kernel not being upgraded through this process?

How do I upgrade the kernel after there has been a update released as per the security accouncement list?

Do I upgrade the kernel using apt-get?

Could someone please point me in the right direction?

Thanks

---

### Post by John.Michael.Kane on 2006-07-13
"sudo aptitude update"
followed by:
"sudo aptitude upgrade"

Should get you what you want.

---

### Post by koshari on 2006-07-13
or simply just click on the little orange star in the corner of the screen and let it update itself!

---

### Post by Wasca on 2006-07-13
Doing apptitude update

then

apptitude upgrade

gives me the same results. Here's what I get, remember I'm using server NOT DESKTOP.

root@mail:~# aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg [189B]                                 
Get:2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release.gpg [189B]                         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release                                       
Get:3 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release [30.9kB]  
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Packages                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Sources
Get:5 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Packages [42.8kB]
Get:6 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:7 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Sources [24.9kB]
Get:8 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Sources [14B]     
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]          
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [36.8kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [4558B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [9118B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [974B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [6951B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [902B]
Fetched 189kB in 4s (39.3kB/s)
Reading package lists... Done
root@mail:~# aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  linux-image-server 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

root@mail:~#

No where in those lines does it specify my kernel being upgraded.

My current kernel is 

linux-image-2.6.15-23-server   2.6.15-23.39 Linux kernel image for version 2.6.15 on Server Equipment

The kernel available in the security update is 

linux-image-2.6.15-26-server   2.6.15-26.44

Why does the kernel not get upgraded? Is it meant to get up graded via this method?

How do I upgrade it?

---

### Post by John.Michael.Kane on 2006-07-14
**sudo aptitude install linux-server**   will install linux-image-2.6.15-26-server and linux-image-server

If your using Bigiron **sudo aptitude install linux-server-bigiron** this will give you linux-image-2.6.15-26-server-bigiron and linux-image-server-bigiron.


In the process you should be asked do you want to update or upgrade.

---

### Post by Wasca on 2006-07-14
Thanks for the reply.

When asked "do I want to udate or upgrade?" what should I do? What's the difference?

---

### Post by HumanAnarchist on 2006-07-19
I tried to do what's been said in this thread, but with out any luck. 

```

**fredrik@bender:~$ sudo apt-get upgrade**
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-image-server
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
**fredrik@bender:~$ sudo aptitude install linux-server**
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  linux-image-server
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
**fredrik@bender:~$ sudo aptitude upgrade**
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  linux-image-server
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

Why isn't this working?

-ha-

---

### Post by FredB on 2006-07-19
sudo apt-get** dist-upgrade **is the answer. Aptitude doesn't really work for me for upgrading.

And until you modify your /etc/apt/sources.list, you won't get any new version of Ubuntu (I mean Edgy right now).

I am using dist-upgrade for every single upgrade available and no troubles with my dapper doing this since Dapper RC !

---

### Post by HumanAnarchist on 2006-07-19
Thanks for that!

This thread should be marked SOLVED

-ha-

---

### Post by Wasca on 2006-07-19
I got it to work also.

For people using Ubuntu server, I had to do this.

apt-get install linux-image-2.6.15-26-server

Then I had to reboot my server for that kernel to be used.

Just change linux-image-2.6.15-26-server to be what ever Kernel your updating to.

The cool thing also is that you can select to load the old kernel if your having problems loading with the new one.

Just hit esc while booting and you get the Grub menu, you can then select which kernel to load.

---

