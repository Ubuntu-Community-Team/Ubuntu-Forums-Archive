---
title: "Forcing a new version with apt-get"
date: 2017-09-07
forum: Installation &amp; Upgrades
---

### Post by david503 on 2017-09-07
This is kind of just a fundamental question- I come from the redhat world (centos), apt-get is new to me,

I'm on 16.04, running gnome (original install was unity, but now I'm gnoming haha),

On vlc's web site it says the latest version is 2.2.6

I have 2.2.2.  I want to upgrade it.  

apt-get claims:

vlc is already the newest version (2.2.2-5ubuntu0.16.04.4).

so.... I can't run 2.2.6?  How do I force it to upgrade it to 2.2.6? 

(The real point at which this becomes an issue is if this happens in php or python or postgresql, etc, where I might *need* the newest version because the rest of  the team has it, I'm just using vlc as an example.) 

Thanks,

sq

---

### Post by ian-weisser on 2017-09-07
The whole point of an LTS release like 16.04 is that the software doesn't change --beyond security patches and a couple other exceptions-- for the life of the release.

If you need newer software, than an LTS might not be the right release for you. Consider upgrading to a newer release of Ubuntu. 17.04 has 2.4.4. Ubuntu 17.10 has 2.2.6.
Or install a snap of the latest VLC, if one is available. Or a PPA.

You cannot 'force' apt to upgrade using the 16.04 repositories - 2.2.6 isn't in the 16.04 repos.
You CAN add different sources that do include newer versions of VLC...but beware - that path may be risky.

---

### Post by david503 on 2017-09-07
That's..... completely absurd.  I have to upgrade the entire install to get so much as... one decimal revision that I might need.  This is ridiculous.    I apparently can't develop in ubuntu. And I'm a fairly typical developer (albeit advanced). 

(Is debian/apt like that in general? on the server side too? Or is this just a ubuntu absurdity...)

 I don't understand how LTS's have "5 years of support". if I can't get new versions of applications, etc, how is that considered "support"?   Totally different situation than yum/centos.  I had my old 6-line CentOS lan server since 2007 and never had a problem upgrading anything until 2010, that only the 7 line could support. And that was only one thing, once.   Is there such a thing as a "non-LTS release"? 

Hell, I don't know what to do...  I may as well go back to windows and run a lan server centos on like I used to I guess.  Well or I guess I could run CentOS as a desktop OS.... but there's not as much support for it or any other distro as a desktop. Or wait- Mandriva,  that's based on the (apparently superior) redhat line... hmm. 

Wow, thanks, a big eye-opener here,

Oh hey wait- ok, a PPA means a .deb file, like an .rpm file right? So my options are to either install a deb file or add repositories, and either one is "dangerous", right?   

Anyway none of this stupidity is your fault! Thanks for informing of the poison! Thanks, 

sq

---

### Post by ian-weisser on 2017-09-08
Ah, you have clearly been developing on Windows.
Observations like those are common among Windows power-users who are new to Ubuntu.
Linux is different. See [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm) for a good primer on the important differences...like how support works.

You have *many* options to install the latest VLC on your older version of Ubuntu.
The complexities and risks of each option seem pretty clear.

---

### Post by grahammechanical on 2017-09-09
With Ubuntu we get a new Ubuntu release every six months (April & October). With each release we get a newer Linux kernel which will include software for newer hardware. We also get some newer versions of some of the default applications.

Every 2 years the April release of Ubuntu is designated a Long Term Support (LTS) with five years support for security fixes. Included will be newer Linux kernels & firmware (hardware driver/modules).

The releases of Ubuntu that we receive in between the LTS releases are designated Standard and are supported for only 9 months. These releases get the latest Linux kernels and firmware about 6 months in advance of the LTS releases. They are useful for people with the latest hardware but they are also the place where Ubuntu developers move the distribution forward.

For example, Ubuntu is in the process of changing from the Unity user interface to the Gnome 3 shell user interface. That work is taking place in the development version of Ubuntu 17.10 and Gnome 3 shell will be the default user interface in Ubuntu 17.10. And that will be 6 months before Gnome 3 shell becomes default in the next Ubuntu LTS. which will be 18.04. So, there will be 6 months to iron out the creases.

The watchword for Ubuntu developers is stability. Even the pre-release development version of Ubuntu is developed to be a stable platform. Another thing to consider is the need to make sure the software repositories contain software that is not only safe to install but also bug free. That cannot be achieved if software is simply copied into the repositories as soon as an application's developers produce a newer versions of their applications.

Regards

---

### Post by mörgæs on 2017-09-10
> **david503 said:**
> I apparently can't develop in ubuntu. And I'm a fairly typical developer (albeit advanced). 


The typical, and especially the advanced Buntu developer will be developing in the development release which is 17.10 as of now.

---

### Post by yoshii on 2017-09-11
Although it's risky, I have found that a lot of Debian .deb files work just fine if installed using gdebi package manager.  gdebi complains if it's incompatible and blocks the install.  But if it's compatible, it just installs.  This is because Ubuntu is a derivative of Debian and still has a lot in common with it.  However, the structures of Debian and Ubuntu are not exactly the same, so there's always the possibility of issues.  

Nonetheless, a lot of the actual normal software releases for Debian are the exact same .deb files as for Ubuntu.  So the risk is often not as bad as it might seem.  
I downloaded the more recent debian version of VLC from the VLC website and it works in Lubuntu 17.04 ...I can't remember if it was from Debian Testing or Debian Stable, but either way, it's more recent.  

Also, OpenShot in the Ubuntu repos is really old, but you can download a single executable App file from the OpenShot website instead of using the repos.  I find this to be a lot more efficient.  Most of the time when I have Linux bugs, it's not coming from the non-system software; it's coming from system software design flaws.  Other than that, I get bugs from running some stuff via Wine that's just not fully compatible yet.  

As much as I love Ubuntu Studio, the release model seems slightly flawed in terms of trying to get up to date softwares.  I get overloaded with downloads of security patches, but no new features even after years go by.  This is almost backwards.  Most of the security patches don't seem to affect me either way, and I get a lot of security patch download updates for softwares that I don't even want to use, like samba or mail.  I DO want updates for Gimp and LMMS and Rosegarden and Qtractor, etc.  I DONT want 1024 fonts!!!!!!! (yes Ubuntu Studio comes with several hundred fonts!!!!... that's font bloatware).  It's actually kind of difficult to reduce those fonts.  

Anyways, I've been testing freeware for several decades and most of the time there's really no big problem.  I think if the devs had more of a barrier between system software development and user software development it would be easier.  I mean kernel bugs are way different than a bug in leafpad.  The simplicity ethos of Linux is getting lost in some of these types of issues.  I agree with the OP.

---

