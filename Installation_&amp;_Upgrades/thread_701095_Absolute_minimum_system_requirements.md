---
title: "Absolute minimum system requirements"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by ztechsolutions on 2008-02-19
I've been searching the Internet, this forum as well as others, for information regarding the absolute minimum requirements for Ubuntu, Kubuntu and Xubuntu. Even the websites themselves don't offer such detailed information. I find this rather silly to be honest with you. I know that different hardware will perform differently, even though specs may appear to be similar. However, it would be helpful to know what the absolute minimum hardware requirements are. At least this way you have a starting point. Different people trying different computers with different specs, then posting their results here is helpful, but only to a certain extent. You can't read through all the posts just to figure out what might work and what might not work. It's way too time consuming. To anyone's knowledge, has Canonical posted any information about absolute system requirements?

I friend of mine would like to try Linux on his IBM Aptiva, AMD K6-2 300mhz, 6GB HD, 196MB RAM, 2MB integrated graphics chip (ATI Rage Mach64).

I didn't even try Kubuntu, I'm 100% positive that the 2MB video alone is far below minimum requirements. I did get the Ubuntu LiveCD to start up, however I get error messages saying that the GNOME interface had problems. I then tried the Xubuntu LiveCD. It boots up too, no error messages, however the menu bar and task bar don't appear. Just the icons and the default wallpaper.

I don't mind trying to install it to see what happens. I know the RAM and HD are sufficient. The CPU seems to be sufficient as well. Video chip? That's another story. However, I do really want to know what the absolute minimum requirements are for these 3 distros. I'd greatly appreciate it if someone could help out.


Thanks

---

### Post by Partyboi2 on 2008-02-19
This is what I generally go by:
[ubuntu]("http://en.wikipedia.org/wiki/Ubuntu_%28Linux_distribution%29#System_requirements")
[xubuntu]("http://en.wikipedia.org/wiki/Xubuntu")
[kubuntu]("http://www.ubuntu.com/products/WhatIsUbuntu/kubuntu")

I would suggest using the alternate cd to install if you are installing on a older machine.
[ubuntu alternate cd]("http://releases.ubuntu.com/releases/7.10/")
[xubuntu alternate cd]("http://mirror.internode.on.net/pub/ubuntu/xubuntu/6.06.1/release/")
[kubuntu alternate cd]("http://ftp.mirror.sptel.com.au/pub/ubuntu/kubuntu/gutsy/")

---

### Post by wolfen69 on 2008-02-19
fluxbuntu might work good on it.

---

### Post by wolfen69 on 2008-02-19
> 
I've been searching the Internet, this forum as well as others, for information regarding the absolute minimum requirements for Ubuntu, Kubuntu and Xubuntu. Even the websites themselves don't offer such detailed information. I find this rather silly to be honest with you. 

a 2 second search on google yielded this: [http://www.ubuntu.com/GetUbuntu/releasenotes/710](http://www.ubuntu.com/GetUbuntu/releasenotes/710) google is your friend.

---

### Post by kerry_s on 2008-02-19
that's a low spec system, you should be looking at low spec distro's that are made to run on low resources. regular distro's are going to be slow.
[http://damnsmalllinux.org/](http://damnsmalllinux.org/)
[http://www.puppylinux.org/user/viewpage.php?page_id=1](http://www.puppylinux.org/user/viewpage.php?page_id=1)
[http://www.mypclinuxos.com/doku.php/tinyme:home](http://www.mypclinuxos.com/doku.php/tinyme:home)
[http://pcfluxboxos.wikidot.com/](http://pcfluxboxos.wikidot.com/)
etc...

a good place to look-> [http://distrowatch.com/](http://distrowatch.com/)

---

### Post by ztechsolutions on 2008-02-21
Hi Guys,

Thanks for all of your replies.

I do know about Puppy Linux, Damn Small Linux, etc. I've tried them out and find them very interesting. The problem is I need something more feature rich and user friendly for the average user. Those light editions are great for someone like me to tinker around with. I can't give those to the average user though. Getting printers, scanners or webcams to work is an even greater challenge than Ubuntu.

This is why I wanted to know what the absolute minimum hardware requirements are for each distro. The links you provided are pages I already visited. The only one that actually gives you better details is that one Wikipedia page with Ubuntu system requirements. However, that page only states the minimum processor speed and RAM. It doesn't state the minimum video RAM. For the other two distros there's even less information out there. 

One thing I have noticed is that you do have to be very careful with type of video card / chip you use, as well as the available video RAM. I got Ubuntu working on a system with a P2-300mhz, 384MB RAM and an ATI Rage Pro PCI 4MB. The problem I noticed is that the video RAM seems to be too little (interface crashes). I then tried Xubuntu on the same computer, but the top and bottom panels don't load (although it boots faster). I switched the video card to an old Diamond Monster with 8MB RAM. Instead of it working better, neither Ubuntu nor Xubuntu would even load. They obviously don't like this video card.

Another problem I encountered was with a computer that used RDRAM RIMM memory modules. I was able to boot up the Ubuntu LiveCD, but as soon as I tried to launch programs to test the system the OS would freeze. I rebooted the system several times, also using Xubuntu, however it always froze. I'm pretty sure the problem was caused by the memory modules. Windows XP ran perfectly on it.

I think the bottom line is that Canonical should simply state the minimum requirements on their websites for each distro so that we at least have some idea as to what the true minimums are. They should also provide a list of videos cards that they know will work, and if there are any compatibility issues with certain hardware (i.e. memory modules). As I stated in my original post, we need a starting point. That alone makes things easier. After that we can tinker around with higher or different specs to see what happens.

---

### Post by john_spiral on 2008-03-28
Hi ztechsolutions,

try:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

I suggest a bare bones sever install on the computer, followed by X server then a very light Window manager (see list below):

[http://en.wikipedia.org/wiki/X_window_manager](http://en.wikipedia.org/wiki/X_window_manager)

see what above WM are available in the repositories and their sys requirements.

My fav -  Enlightenment, even stable version 0.16 is excellent with the right theming applied. Check out an older version of Elive (GEM) had a beautiful look and feel - 3d spinning windows the lot! .

Please come back to us on your progress.

Johne

---

### Post by N1N31NCHN41L5 on 2008-03-28
> **ztechsolutions said:**
> I've been searching the Internet, this forum as well as others, for information regarding the absolute minimum requirements for Ubuntu, Kubuntu and Xubuntu. Even the websites themselves don't offer such detailed information. I find this rather silly to be honest with you. I know that different hardware will perform differently, even though specs may appear to be similar. However, it would be helpful to know what the absolute minimum hardware requirements are. At least this way you have a starting point. Different people trying different computers with different specs, then posting their results here is helpful, but only to a certain extent. You can't read through all the posts just to figure out what might work and what might not work. It's way too time consuming. To anyone's knowledge, has Canonical posted any information about absolute system requirements?

I friend of mine would like to try Linux on his IBM Aptiva, AMD K6-2 300mhz, 6GB HD, 196MB RAM, 2MB integrated graphics chip (ATI Rage Mach64).

I didn't even try Kubuntu, I'm 100% positive that the 2MB video alone is far below minimum requirements. I did get the Ubuntu LiveCD to start up, however I get error messages saying that the GNOME interface had problems. I then tried the Xubuntu LiveCD. It boots up too, no error messages, however the menu bar and task bar don't appear. Just the icons and the default wallpaper.

I don't mind trying to install it to see what happens. I know the RAM and HD are sufficient. The CPU seems to be sufficient as well. Video chip? That's another story. However, I do really want to know what the absolute minimum requirements are for these 3 distros. I'd greatly appreciate it if someone could help out.


Thanks

THE specs WILL NOT run UBUNTU. my system is stronger all the way around and it can NOT run ubuntu. I'm using xubuntu, YOU might be able to make that run for him.

---

### Post by john_spiral on 2008-03-28
> **N1N31NCHN41L5 said:**
> THE specs WILL NOT run UBUNTU. my system is stronger all the way around and it can NOT run ubuntu. I'm using xubuntu, YOU might be able to make that run for him.

N1N31NCHN41L5,

Ubuntu by default uses the GNOME desktop environment (resource hungry). Loading a lighter window manger like the one's I've suggested above will defenitely go a long way to making an older system more usable.

---

