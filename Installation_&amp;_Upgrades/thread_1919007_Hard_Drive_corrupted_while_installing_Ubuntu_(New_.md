---
title: "Hard Drive corrupted while installing Ubuntu (New User)"
date: 2012-02-02
forum: Installation &amp; Upgrades
---

### Post by karthickdv on 2012-02-02
Hi All, (I am a New User to LINUX World trying to explore it)
I got a new Desktop three weeks back. Running on WINDOWS 7.
 
Wanted to install Ubuntu. Downloaded Ubuntu 11.10 Version.
In Windows7, Had 4 Drives (C, D, E, F). E was Allocated but was all Empty. It was under NTFS File System. (which I thought I will use for Linux - 100 GB)
 
Yesterday while installing I was unable to Create Sub Partition on this E while Installing Ubuntu. Teh options like Add, Update were all disabled. Then I learnt that we need
a root (/), a boot(/boot) and a Swap partition to install Ubuntu.
 
My mistake I think was. I chose partion D (NTFS - 100 GB - Had data for 35 MB in it) and created a Partition in it for /boot. After this a new Partition was shown for /boot and teh remaining part of D drive as Unused / Unusable (Not sure of exact word).
 
Thats it. After this I am not able to bring my computer up.
 
Below are all what I tried with my little knowledge:
a.  Put in Windows 7 CD and booted and chose Repair option. But It was not seeing that I have Windows 7 installed in it. I dont see any drived. I see only one 35 MB drive thatis named as BOOT (I think it should be the /boot that I created in Ubuntu)
 
b. If I boot without CD. Windows 7 cannot load because of Error '0xc000000f' The Boot Selection Failed Because the Required Resource is Inaccsible
 
c. I put Ubuntu CD and tried to boot from CD. It does not. It goes to boot from Hard Disk and same Windows Error.
 
What I assume is this.
Earlier:  Windows with 4 Drives. All were NTFS and Windows Recognised it
Now: I have 3 Drives (NTFS).. One was partioned to /boot for Linux.
 
When I boot my System, the OS that is getting loaded is Windows.But it sees only one Drive that is dedicated for /boot for Ubuntu.
 
I need any one OS working fine. I will start Intalling Ubuntu from scratc later (with an expert around :)). Can some one help me in resolving this problem. Thanks in advance.
Let me know if you need any more information to help me out.

---

### Post by mastablasta on 2012-02-02
you don't need an expert arround to install Ubutnu but you do need to read the manual how to install it (since you want to have it side by side).
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
With more pics:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
 
you issue is that you probably had 4 primary partitions set by default deleting a primary partition before and changing it into extended would help you install Ubuntu easilly.
 
i am not quite sure what you did here, but running boot info script using liveCD would help: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
 
follow the instructions on site and post the results here.
 
since you have windows 7 CD and if you don't have any important data the easiest way would be to delete all partitions and install windows form scratch.
 
you don't have to create partitions in Ubuntu, they will be created automaticly by installer. hwoever you can create them if you wish. partitions that are good to have are:
/
/home
/swap
 
others are usually not necessray unless you have some special configuration.
 
by default Ubuntu will only create:
/
/swap
 
but if you wish you can create /home during install. home is sort of like my documents in windows. it keeps all user data, so if you want ot have it separated from the OS (/) then you need to create it. you can also create it after install only it's easier to do it during install.

---

### Post by darkod on 2012-02-02
If you can boot with the win7 dvd you should also be able to boot with the ubuntu cd in live mode (Try Ubuntu option). If it starts loading but doesn't finish, it might be a video driver issue and you might need to add some boot parameter.

Is the booting with the ubuntu cd starting at all?

Can you boot win7 with success (regardless whether you have 3 or 4 partitions you can see in Computer now), or not? Does it load fine?

---

