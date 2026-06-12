---
title: "What's new in Lucid Lynx?"
date: 2010-02-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Cam! on 2010-02-21
Besides the revamped Software Center/Package Manager, what are some cool new things that are to be added in 10.04?

---

### Post by gjoellee on 2010-02-21
> **Cam! said:**
> Besides the revamped Software Center/Package Manager, what are some cool new things that are to be added in 10.04?

Plymouth

---

### Post by NightwishFan on 2010-02-21
Check out this page:
[http://www.omgubuntu.co.uk/](http://www.omgubuntu.co.uk/)

Sounds like a good release, but perhaps Plymouth is too much for a LTS.

---

### Post by Luke has no name on 2010-02-21
Deja vu?

-Nouveau drivers for nvidia hardware = better 2D drivers. Also the improved manager for nvidia drivers.
-KMS for a lot more graphics cards = better graphical boot and faster screen-resolution switch
-Updated software, of course. I assume FF 3.6, kernel 2.6.32, GNOME 2.30, OOo 3.2, etc.
-Removal of HAL, replaced by DeviceKit (right?)
-Renewed interest in LXDE as a lightweight, sponsored spin of Ubuntu
-Removal of GIMP from default install
-Server: UEC improvements, lots of other things. I'll post some later.



What I WANT to see, among other things:

With the upcoming LTS release, please hire documenters, pay volunteers for quality documenting work, SEND PROGRAMMERS TO DOCUMENTING SCHOOL. I don't believe I'm the first to say that quality, thorough documentation of all tools and use cases of a piece of software is as critical to the usability of software as the quality of the software itself. 

Community/volunteer documentation can be handy and cheap. But, I believe this LTS cycle (and the first year post-release) is an excellent time to stabilize, update, and expand on all official documentation. Everything in the following list should be documented accurately and thoroughly. Test every line of instruction!

    * Installing Ubuntu Server in every way possible
    * Customizing installation ISOs for server and alternative installs to meet an enterprise's needs (Preset network configuration, packages, etc.)
    * Package management (e.g. pinning packages in a custom-deployed install) as well as setting up and modifying a custom repository/package mirror
    * Deploying Ubuntu over the network (Installation)
    * Securing Ubuntu using ufw/AppArmor (though FireHOL > ufw, had to say it)
    * Using important core programs present in Ubuntu that aren't present in many other distros at the moment, such as GRUB 2. Upstart, which is supposed to entirely take over for SysV, has very poor documentation, and it's a critical thing for Sysadmins to understand! I don't care if the syntax is developing. If it's in the LTS, GET IT DOCUMENTED.
    * Common uses of Ubuntu Server and detailed configurations of each (Web, Java App Server, Email, DNS, Load Balancing, DHCP, etc.)

I know some of this is already fairly well documented. I know some of this is usually left to upstream documentation, or to the community, or to skilled authors like Kyle Rankin and Benjamin Mako Hill (The Official Ubuntu Server Book). However, Ubuntu is useless by itself. Software is useless if businesses of any size cannot figure out how to set up and configure the software and distribute it easily. If you want small/medium businesses with semi-skilled IT workers, and large enterprises with RHEL or Microsoft-accustomed IT staff to be able to deploy Ubuntu Server (so you can make money), you need to make it clear that your ease-of-use is not questionable, and that Ubuntu Server fits the job better than the competition you clearly have.

---

### Post by Cam! on 2010-02-21
> **gjoellee said:**
> Plymouth

What exactly is Plymouth?

---

### Post by NightwishFan on 2010-02-21
Plymouth is a graphical boot system created by the Fedora operating system.
[http://www.youtube.com/watch?v=A5aJyzgPAzo](http://www.youtube.com/watch?v=A5aJyzgPAzo)

Ubuntu is adopting it, hopefully they do something subtle and nice with it. The Solar theme from Fedora is awesome.

---

### Post by Cam! on 2010-02-21
> **NightwishFan said:**
> Plymouth is a graphical boot system created by the Fedora operating system.
[http://www.youtube.com/watch?v=A5aJyzgPAzo](http://www.youtube.com/watch?v=A5aJyzgPAzo)

Ubuntu is adopting it, hopefully they do something subtle and nice with it. The Solar theme from Fedora is awesome.

Wow! It looks nice. Are there any other vids of Plymouth boots?

---

### Post by dragonblader44 on 2010-02-21
It has got a cooler name! :D

---

### Post by Arthur_D on 2010-02-21
And it fixes my sound issues. :D

---

### Post by earthpigg on 2010-02-21
> **NightwishFan said:**
> Plymouth is a graphical boot system created by the Fedora operating system.
[http://www.youtube.com/watch?v=A5aJyzgPAzo](http://www.youtube.com/watch?v=A5aJyzgPAzo)

Ubuntu is adopting it, hopefully they do something subtle and nice with it. The Solar theme from Fedora is awesome.

i may have to switch to fedora just for that great looking boot screen!

---

### Post by cariboo on 2010-02-21
Plymouth isn't really worth it, on my system it's only on screen for about 2 seconds. I guess it's ok if you don't mind waiting quite a while for your system to start.

---

### Post by chriswyatt on 2010-02-21
> **earthpigg said:**
> i may have to switch to fedora just for that great looking boot screen!

I was thinking the same thing.

Goodbye Ubuntu, it's been nice knowing you.

):P

---

### Post by Cam! on 2010-02-21
I was also told that there's support for transparent windows/panels. Is this true?

---

### Post by akand074 on 2010-02-21
> **Cam! said:**
> I was also told that there's support for transparent windows/panels. Is this true?

I have transparent windows/panels right now in Karmic :) Using compiz fusion opacity feature

---

### Post by gjoellee on 2010-02-21
> **cariboo907 said:**
> Plymouth isn't really worth it, on my system it's only on screen for about 2 seconds. I guess it's ok if you don't mind waiting quite a while for your system to start.

It is a bug that is not fixed yet

---

### Post by Cam! on 2010-02-21
> **akand074 said:**
> I have transparent windows/panels right now in Karmic :) Using compiz fusion opacity feature

I was actually talking about a built-in GTK feature.

---

### Post by cariboo on 2010-02-21
My average boot time according to bootchart is ~25 seconds, there isn't enough time for plymouth to do it's thing. :)

---

### Post by sgosnell on 2010-03-07
Plymouth does its thing on my laptop.  It gradually took over.  Initially it just flashed, and now it stays forever.  I can't even boot, the Solar screen just stays there, with the solar flares going continually.  I need to find a way to disable it, because Lucid is now useless.

---

### Post by RiceMonster on 2010-03-07
> **cariboo907 said:**
> My average boot time according to bootchart is ~25 seconds, there isn't enough time for plymouth to do it's thing. :)

Seems like a bug. Fedora boots in about 20-30 seconds for me, and plymouth is there the whole time. Maybe, of course, I'm misunderstanding you, though.

---

### Post by swoll1980 on 2010-03-07
Broken font rendering in Firefox makes my eyes bleed.

---

### Post by cariboo on 2010-03-07
> **RiceMonster said:**
> Seems like a bug. Fedora boots in about 20-30 seconds for me, and plymouth is there the whole time. Maybe, of course, I'm misunderstanding you, though.

It is a bug, plymouth doesn't play nice with closed source nvidia drivers. When using the open source nouveau drivers, I get the correct display on both boot and shutdown.

---

