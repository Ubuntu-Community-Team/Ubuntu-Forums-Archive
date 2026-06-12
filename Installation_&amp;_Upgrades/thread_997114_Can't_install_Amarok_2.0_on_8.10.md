---
title: "Can't install Amarok 2.0 on 8.10"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by - 000 - on 2008-11-29
I am trying to install amarok 2.0 RC1 on Kubuntu intrepid ibex, and I am getting an error message on synaptic.

I added the following URL to my repositories:

> deb [http://ppa.launchpad.net/project-neon/ubuntu](http://ppa.launchpad.net/project-neon/ubuntu) hardy main

This is the error message:

> Could not mark all packages for installation or upgrade.

The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.

amarok-nightly:
 Depends: amarok-nightly-kdebase but it is not going to be installed
 Depends: amarok-nightly-kdelibs but it is not going to be installed

---

### Post by Mze on 2008-11-29
[http://www.kubuntu.org/amarok2-beta2](http://www.kubuntu.org/amarok2-beta2)

If you are using 8.10, then using Hardy (8.04) for source files would be wrong

---

### Post by - 000 - on 2008-11-29
ok, thankx

---

### Post by - 000 - on 2008-12-04
Ok, I changed the repositories, and now I'm getting this error when I try to install it:

> 
An error occured

The following details are provided:

[quote]E: /var/cache/apt/archives/amarok-nightly_20081203.7+svn892151-0neon1_i386.deb: trying to overwrite `/opt/amarok-nightly/share/kde4/servicetypes/plasma-applet.desktop', which is also in package amarok-nightly-kdelibs[/quote]

---

### Post by - 000 - on 2008-12-06
bump

---

### Post by - 000 - on 2008-12-06
bump

---

### Post by - 000 - on 2008-12-07
> **- 000 - said:**
> bump............

---

### Post by - 000 - on 2008-12-08
Anyone?

---

### Post by JakeSpeare on 2008-12-11
Looks like you have a previous Amarok install.  Remove it before installing this one.

---

### Post by DarkDemonNT on 2008-12-11
```
sudo dpkg -i --force-overwrite /path/to/amarok-nightly_20081113.7+svn883756-0neon1_i386.deb
```
10 December 2008 Amarok 2.0 was released.
Try it.

```
 deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main
```

---

### Post by - 000 - on 2008-12-17
That worked. Thanks

---

### Post by Moonfrost on 2008-12-18
> **DarkDemonNT said:**
> ```
sudo dpkg -i --force-overwrite /path/to/amarok-nightly_20081113.7+svn883756-0neon1_i386.deb
```
10 December 2008 Amarok 2.0 was released.
Try it.

```
 deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main
```

Hi, I'm having the same problem, I removed Amarok 1.5.10 (which came with Kubuntu 8.10) to make room for the new released 2.0. I copied this exact repo from somewhere else (also tried your here, the same of course) and Adept adds it with no problem but I see that when it's fetching packages a lot of packages that end with US (I'm in the US) say "failed" (can't read what they are since everything flashed by so fast), I then tried typing "amarok-kde4" (also tried without quotes) like it said on the Kubuntu site but nothing comes out, how can I install Amarok 2?

---

### Post by mind_combatant on 2008-12-18
i'm having the same proublem too... i hope someone will help us

---

### Post by Moonfrost on 2008-12-18
> **mind_combatant said:**
> i'm having the same proublem too... i hope someone will help us

I could never install it that way, but I found a forum topic (searching on google) which pointed to this link: 

[http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/pool/main/a/amarok-kde4/](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/pool/main/a/amarok-kde4/)

Download the file that says: amarok-kde4_2.0-0ubuntu1~ppa4_amd64.deb

unless you're using 32 bit, in that case replace amd64 for i386, hope that helps.

---

### Post by mind_combatant on 2008-12-18
> **Moonfrost said:**
> I could never install it that way, but I found a forum topic (searching on google) which pointed to this link: 

[http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/pool/main/a/amarok-kde4/](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/pool/main/a/amarok-kde4/)

Download the file that says: amarok-kde4_2.0-0ubuntu1~ppa4_amd64.deb

unless you're using 32 bit, in that case replace amd64 for i386, hope that helps.

thanks, although that's an alpha release! but i guess it's better than 1.4. just be prepared if it crashes!

---

### Post by mind_combatant on 2008-12-18
i found out how to get the real version now:
[http://amarok.kde.org/forum/index.php?topic=16137.msg24902](http://amarok.kde.org/forum/index.php?topic=16137.msg24902)

---

### Post by Moonfrost on 2008-12-18
> **mind_combatant said:**
> thanks, although that's an alpha release! but i guess it's better than 1.4. just be prepared if it crashes!

The one I'm using it's not an Alpha release, it's the final release. This one is build on December 16.

---

### Post by Sabar on 2009-04-10
> **DarkDemonNT said:**
> ```
sudo dpkg -i --force-overwrite /path/to/amarok-nightly_20081113.7+svn883756-0neon1_i386.deb
```
10 December 2008 Amarok 2.0 was released.
Try it.

```
 deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main
```

Tried that got this

> computer@computer:~$ sudo dpkg -i --force-overwrite /path/to/amarok-nightly_20081113.7+svn883756-0neon1_i386.deb
[sudo] password for computer: 
dpkg: error processing /path/to/amarok-nightly_20081113.7+svn883756-0neon1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /path/to/amarok-nightly_20081113.7+svn883756-0neon1_i386.deb
computer@computer:~$  deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main
bash: deb: command not found

Then I tried this
> 
Moonfrost  	
Re: Can't install Amarok 2.0 on 8.10
Quote:
Originally Posted by mind_combatant View Post
i'm having the same proublem too... i hope someone will help us
I could never install it that way, but I found a forum topic (searching on google) which pointed to this link:

[http://ppa.launchpad.net/kubuntu-mem...a/amarok-kde4/](http://ppa.launchpad.net/kubuntu-mem...a/amarok-kde4/)

Download the file that says: amarok-kde4_2.0-0ubuntu1~ppa4_amd64.deb

unless you're using 32 bit, in that case replace amd64 for i386, hope that helps. 

More errors

Some one in one of the forums said something about a key missing? anybody have any idea what that's about?

Thanks 
Sabar

---

### Post by Sabar on 2009-04-10
I went to the Amarok web site followed there directions. opened System > Administration > Software sources. then I added
Quote:
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main
When I added this and hit reload I got this error
Quote:
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9423A34CCA967634

When I then went to System > Administration > Synaptic Package Manager
and did a search for Amarok kde4 it shows that it is already installed and only gives the option to reinstall.

Can some one tell me what I am missing here? Why is there no key?
Sabar

---

