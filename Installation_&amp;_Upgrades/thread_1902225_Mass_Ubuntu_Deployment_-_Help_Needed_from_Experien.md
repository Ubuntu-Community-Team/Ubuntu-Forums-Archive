---
title: "Mass Ubuntu Deployment - Help Needed from Experienced Sys Admis"
date: 2011-12-30
forum: Installation &amp; Upgrades
---

### Post by linux.girl on 2011-12-30
Hello everyone,

I have to make a mass ubuntu deployment at work, and words like clonezilla, FAI, puppet, cfengine, pxe, oem are all dancing around my head :)

The hardware clients will be desktops, HP and IBM.

Computers have to authenticate with the windows ad via likewise open.

If I clone a computer with certain user configurations, once I deploy the clone in the client and log in with the new user, then all configs are gone, as most of them are user specific (for example, several thunderbird add-ons carefully configure to work with MS exchange). And also, because of the likewise open authentication, I have to make sure that the client gets a new hostname, authenticates with AD, etc.

Question is: which of the above tools would be better for what I need, and which (or combination of) can make the whole process all as unattended as possible?

Any suggestions?

Thanks in advance!

linux.girl

---

### Post by cmcanulty on 2011-12-30
I run 10 Ubuntu machines at a local library. I use a separate partition for home and one for /. I copy the home the same to each machine. I also save full state of markings from synaptic and use that to restore applications (read markings after install). I use the same user name and password for each. I tried also copying the etc directory to each but that is trickier as you have to make sure the host file is changed to reflect each computer name. You can use the same name and password then after install change them to what you wish. I never get it quite as easy as I think it could be done if I was more knowledgeable.Also synaptic won't reinstall all the packages, ubuntu tweak, google earth, and  a few others I have to do manually. I hope someone replies that has a more streamlined way for multiple deployments for not advanced people.

---

### Post by linux.girl on 2011-12-31
Thanks a lot for your answer! But I think in my case I need something that would work on a larger scale - I am talking about at least 200 desktops...

I hope the experts have some ideas for me  - but I guess the answer will probably come after new year's :popcorn:

Happy new year to everyone!

linux.girl

---

### Post by Dangertux on 2011-12-31
For large deployments of this type I would recommend either Puppet or straight PXE. PXE would be easier, but if you want the install to be unattended you could create a modified iso that would install preconfigured packages necessary to achieve the connectivity you're looking for.

This is one of the big reasons I prefer RHEL for things like this (can you say satellite server? lol) 

If it were me, I would go with Puppet + systemimager, that would probably be the most straightforward way of dealing with it. Or PXE with a remastered iso, that  contains the necessary packages/configs. Just make sure nothing ends up as a 1 off, otherwise it will be hell for maintenance later.

---

### Post by linux.girl on 2011-12-31
Hi there,

Thanks :-)

What do you mean by "make sure nothing ends up as a 1 off"?

Do you know where I can find some relatively simple tutorials to learn how to make a PXE & how to properly use Puppet?

Thanks a lot,

linux.girl

---

### Post by Dangertux on 2011-12-31
> **linux.girl said:**
> Hi there,

Thanks :-)

What do you mean by "make sure nothing ends up as a 1 off"?

Do you know where I can find some relatively simple tutorials to learn how to make a PXE & how to properly use Puppet?

Thanks a lot,

linux.girl


What I meant by one off was when deployments go south sometimes a system gets missed, and if it's just one sometimes it just seems natural to set that one up yourself... Don't do that, it causes nightmares from my experience.

[https://help.ubuntu.com/10.10/serverguide/C/puppet.html](https://help.ubuntu.com/10.10/serverguide/C/puppet.html)
[https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer)
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

This should get you started.

---

### Post by linux.girl on 2011-12-31
ah, ok, now I get it :-)

thanks for the tuts, will start right now :-)

---

