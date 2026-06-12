---
title: "Unable to Upgrade."
date: 2011-04-06
forum: Installation &amp; Upgrades
---

### Post by kadak.chocho on 2011-04-06
Please pardon me for i am a noob and new to ubuntu - but willing to learn. I have been unable to upgrade for a few days now. When i start the upgrade manager or the synaptic i get the following message. i am using the ubuntu 10.04 with windows vistadual boot.

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'W: duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages), W: duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages), W: duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages), W: duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-i386_Packages), W: duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_main_binary-i386_Packages), W: duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_restricted_binary-i386_Packages), W: duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_universe_binary-i386_Packages), W: duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_multiverse_binary-i386_Packages), W: duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-i386_Packages), W: duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-i386_Packages), W: duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages), W: duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_multiverse_binary-i386_Packages), W: duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_main_binary-i386_Packages), W:duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_restricted_binary-i386_Packages), W: duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_universe_binary-i386_Packages), W: duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_multiverse_binary-i386_Packages), **E: dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf), E:Error occurred while processing wine (NewVersion1), E: problem with MergeList /var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_intrepid_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'**

---

### Post by Dutch70 on 2011-04-06
Is this a Wubi install? If not, you may want to clean your system and delete your cache. If you don't know how, Ubuntu Tweak or Bleachbit is a good program to do it for you. 

Also, please run the following command & post your sources.list from gedit between ```
and[ /CODE] tags, by clicking the "#" symbol in the toolbar. 
[CODE]gksudo gedit /etc/apt/sources.list
```

Give this a read while your waiting for responses.
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1580857[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1580857")

---

### Post by mörgæs on 2011-04-06
What? It reads 'dapper'. I don't remember when I have seen one of these latest.

Dapper Drake is Ubuntu 6.06. If you originally installed this one, you should reinstall a new Ubuntu from scratch. Such a long path of upgrades is not healthy.

---

### Post by kadak.chocho on 2011-04-06
Ok .... i am done cleaning the duplicate sources and removing the old ones.

NOw i need only to solve this

E: Dynamic MMap ran out of room. Please increase the size of APT:: Cache-Limit. Current value: 25165824. (man 5 apt.conf), E:Error occurred while processing kscreensaver-xsavers (NewVersion1), E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_lucid-updates_universe_binary-i386_Packages, E: The package lists or status file could not be parsed or opened.

Thank you for your invaluable help

---

### Post by ecofinn on 2011-04-06
I just had the same or a very similar problem.

apt-get update gave me:

```

Reading package lists... Error!
E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)
E: Error occurred while processing gufw (NewFileVer1)
E: Problem with MergeList /var/lib/dpkg/status
W: Unable to munmap
E: The package lists or status file could not be parsed or opened.

```I edited /etc/apt/apt.conf.d/70debconf 

and added 
```
APT::Cache-Limit "50331648"; 
```to the end, so the file now reads:

```
// Pre-configure all packages with debconf before they are installed.
// If you don't like it, comment it out.
DPkg::Pre-Install-Pkgs {"/usr/sbin/dpkg-preconfigure --apt || true";};

APT::Cache-Limit "50331648";
```apt-get update is happy again now!

---

### Post by mörgæs on 2011-04-06
It seems like the cache was running full. Rather than increase the limit you could try 

```
sudo apt-get clean
```

---

