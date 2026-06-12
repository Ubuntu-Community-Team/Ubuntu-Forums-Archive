---
title: "Install with RAID"
date: 2020-05-05
forum: Installation &amp; Upgrades
---

### Post by steven43 on 2020-05-05
So, you can't install Ubuntu (XUbuntu) 20.04 onto an mdadm RAID?

Or am I missing something?

---

### Post by TheFu on 2020-05-05
You can install into LVM, then mirror the LVs onto another disk for raid1 using lvconvert.
  Convert LV to type mirror (also see type raid1),```

  lvconvert --type mirror LV
        [ -m|--mirrors [+|-]Number ]
        [ -I|--stripesize Size[k|UNIT] ]
        [ -R|--regionsize Size[m|UNIT] ]
        [ -i|--interval Number ]
        [    --stripes Number ]
        [    --mirrorlog core|disk ]
        [ COMMON_OPTIONS ]
        [ PV ... ]
```

i haven't done this, but use LVM extensively.  Reading the manpage is required to understand the caveats.

---

### Post by steven43 on 2020-05-05
So apparently RAID is only supported during install times with Ubuntu Server?

This would seem to be a huge miss by Ubuntu.  Any particular reason why mdadm and RAID was not included as part of the installer?  Just because it's there doesn't mean everyone has to use it.

Admittedly I come mostly from a server background, CentOS.  I install that all the time, and mdadm raids during the installation process is easy to do.  I assumed the process would be at least similar with installing Ubuntu desktop.  But there's no option to create a RAID during the install process.  And using the Try Ubuntu, mdadm isn't even included.

I suppose I can use just one of the SSD drives to install Ubuntu.  I was going to include some large platter disks to put most of my stuff anyway, in a RAID1.  But I always knew I could do that after installing.  If the SSD drive crashes, I'll just have to reinstall, most of the stuff will be on the RAID1 platter disks anyway.

Still... disappointed that in 2020, Ubuntu doesn't provide a way to setup a software RAID during installation.

---

### Post by TheFu on 2020-05-05
>  So apparently RAID is only supported during install times with Ubuntu Server?
Who said that?  You appear to have taken a question specifically about installation, gotten an option specifically about installation, then misinterpreted that answer to be general when it was not.

CentOS disk configuration at installation time far exceeds that has been possible using the delivered installer for Ubuntu Server. They have different customers, so that makes sense.  Ubuntu isn't CentOS or RHEL and more than RHEL Server is MS-Windows Server.

I assume you found this [https://ubuntu.com/server/docs/installation-advanced](https://ubuntu.com/server/docs/installation-advanced) and read it?

Desktop installs for Ubuntu use completely different installers, designed to make relative non-admin types happy.  You can use a pre-seed file to create whatever storage setup you want.  20.04 has vastly changed how that works.  I'd probably look at Cobbler if I had that need, but we tend to deploy onto VMs and the underlying storage is already setup for the redundancy level we want using either RAID or Sheepdog.  Xubuntu is NOT a server install. It is a desktop install designed for lower-end GPUs. The team behind it worries less about server aspects and more about GUI experiences for typical Ubuntu end-users.

> Still... disappointed that in 2020, Ubuntu doesn't provide a way to setup a software RAID during installation. 
A method was provided and the link above provides more.  Google found it easily "ubuntu server guide raid". 

BTW .... 

```
$ more /proc/mdstat 
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid1 sdf2[1] sde2[0]
      1338985536 blocks [2/2] [UU]
      
md1 : active raid1 sdc3[3] sdd3[2]
      1943010816 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>

```  That RAID setup was initially created for 10.04 Server so it appears that in 2010, Ubuntu had a method to create RAID disks. I know the array was RAID5 initially, has been moved to at least 3 different physical servers, and was migrated to 2xRAID1 configs when the installed disks got larger.

Feel free to open a bug with the Xubuntu team.  Almost nobody in these forums works for Canonical, so we concentrate on solutions to issues. We have ZERO impact on policy or future direction.  Many decisions Canonical has and continues to make don't make me completely happy either.  RAID is pretty low on the list, however.  Everyone has their different touch point issues.

---

### Post by steven43 on 2020-05-05
> **TheFu said:**
> Who said that?

Well... I mean... the link - [https://ubuntu.com/server/docs/installation-advanced](https://ubuntu.com/server/docs/installation-advanced) - refers to Ubuntu server.

So um... yea... *So apparently RAID is only supported during install times with Ubuntu Server?* ... the answer to that seems to be yes.

I'm a little confused because I'm not sure if you're agreeing with me or disagreeing with me on this.



> **TheFu said:**
> Desktop installs for Ubuntu use completely different installers, designed to make relative non-admin types happy.

Well, my point was - I think the option to configure RAID should be present in the installer.  Just like it is with CentOS and Fedora.  It can definitely be true that Ubuntu is geared more towards non-admin types.  I get that.  But just because something is available in the installer doesn't mean it has to be used.  So even if 99% of the people that install Ubuntu have no idea what a RAID is or what the benefits of setting one up are, having the ability there for the 1% I think would be worth it.

I really just thought all modern Linux distributions would have support for creating mdadm arrays at install time.

> **TheFu said:**
> Almost nobody in these forums works for Canonical, so we concentrate on solutions to issues. We have ZERO impact on policy or future direction. Many decisions Canonical has and continues to make don't make me completely happy either. RAID is pretty low on the list, however. Everyone has their different touch point issues.

This is good to know.  I'll admit this was a venting post for me.  I didn't really mean to ruffle any feathers.  I was just shocked that it wasn't part of the installer.  I guess I just assumed that a RAID setup like this was more common than it really is.  I was all ready to bring up a new system using a RAID1 system like we use on all of our servers.  And then get to the installer and find it's not there.  I guess I should have researched this topic a bit more before I started ordering all of the components, but again I just thought it was common place.

---

### Post by TheFu on 2020-05-05
RAID is supported during install and post-install for Ubuntu Server using either mdadm or LVM.

RAID for Desktops using LVM is supported during and post-install.  The trick, if you want to call it that, is to install a single-disk LVM setup, then add the mirroring to another disk post-install.

Canonical has been trying to simplify the installer the last 10 yrs, so that grandma isn't intimidated or confused with too many options.  It is a design choice. However, not all Ubuntu-desktop flavors are created by Canonical, so we cannot really complain to them about something a volunteer team does.  
Every different DE flavor of Ubuntu takes expertise and a team to create. Testing each isn't cheap either.  I suppose of you charge $750/yr for your server, then you might have more resources to throw at issues like these?  Canonical gives away their server, the patches, and the multitude of desktop flavors they release.

I suppose we could just say that features important to Redhat aren't necessarily important to Canonical. The differences in the resulting distributions certainly shows those different priorities.

---

### Post by oldfred on 2020-05-05
The desktop has not supported RAID.

Back with 12.04, there was an alternative desktop installer that included RAID & LVM. The alternative installer was phased out and they said they would add those functions to standard desktop installer. Took multiple years before LVM added and many users mistaking clicked on the install option LVM full drive install that offers easy partition changes. For Windows users a drive was one partition, not entire drive which is what LVM is. Many unhappy Windows users. 
Installer is now a bit more clear on LVM, but many Windows users do not understand partitions.

Raid still not supported in Desktop installer. I think it now sees RAID, but grub does not install.
But desktop installer & server installer both install same basic system with different default packages.
Server installer has tasksel. You can choose not to install any server apps and just install desktop of choice. Then you have desktop install.

Used by Server install to choose what you want
sudo apt install tasksel
sudo tasksel
sudo apt install ubuntu-server
[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

---

### Post by steven43 on 2020-05-05
Yea, I'm weighing my options.

Never used the LVM mirroring option.

I'm very familiar with mdadm.

I used FakeRAID once years ago, and hated it.  And I suppose that's why I have reservations about the LVM mirroring.

Doing the server install is an option I've considered.

The good thing about it... it's a blank system, so I can always scuttle it.  I can test it out and see how it operates and if the new system operates on par.

I guess my gripe is just that I wasn't expecting this.  I guess I should have done more research on this, then I wouldn't have been so surprised by this.  Maybe I can take comfort in knowing that maybe if someone else out there is thinking about install Ubuntu on their system in RAID, they'll find this thread during their planning phase and know before hand.

---

### Post by TheFu on 2020-05-06
We never expect things that catch us unawares. ;)

There isn't just 1 Ubuntu. There are 10+.  The Server and Desktops are completely different from an install perspective, though you can add packages from other with little concern.  But if you do a base server install, that will not include the pretty "GUI" stuff that most end-users have come to expect.  Expect to manage the system using config files, not a GUI.  Some times that is exactly what I want.  Other times, it is a slight hassle.  

For example, I ZERO use for anything network-manager related on any of my systems, but on a laptop being able to easily control access to wifi networking is missed. Almost all my systems use static IPs, locally set and managed.  Been burned by DHCP failures a few too many times in corporate environments.  Having 400 servers refuse to get onto a network due to some DHCP failure is unacceptable.

You will certainly run into some other differences between the different Ubuntu Desktops and what you've come to expect from Fedora.  Ubuntu tries to be approachable by non-technical people.  For people like us, sometimes we're better off just clicking next-->next-->next with the defaults.  Overthinking things can get in the way, just like with Windows.  There's a reason new users don't pick Fedora or CentOS.

FakeRAID has all the HW issues of a real RAID, but none of the good things.  LVM is more like mdadm, but with volume management included. Provided that LVM is configured on a disk, pretty much everything can be changed later to what you want with certain limitations.  Don'e expect to convert RAID0 into RAID10.  It is possible to convert RAID0 into RAID01, but nobody should.  Too many nasty failure modes with RAID01.  RAID10 has to be configured from the beginning.  I don't know about support for RAID5/6 under LVM. 

Anyway, seems we've beaten this thread down.  I've always found the easy way to try new LVM things is to setup a VM with a few small virtual disks to try things out.  10 minutes of that in a play VM makes all the difference for understanding.

---

