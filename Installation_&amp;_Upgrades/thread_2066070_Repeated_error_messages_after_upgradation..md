---
title: "Repeated error messages after upgradation."
date: 2012-10-03
forum: Installation &amp; Upgrades
---

### Post by arroy_0209 on 2012-10-03
I upgraded to 12.04 from 10.04 nine days ago and also installed lxde. So far there had been two messages stating "ubuntu12.04 faced a problem..please report etc" and once that "compiz faced a problem and need to close". (There were also two other error messages; I forgot details.) On looking at the details I found that latest ubuntu problem was related to lx-panel (I noticed firefox window icon in the panel blinking endlessly). I am worried what to do about such repeated error messages. These frighten me. Is there any way to test how stable my operating system is at the moment? Should I do a fresh install of ubuntu?

I should mention that I had installed some programs like gimp, latex (documentation package), etc and have run sudo apt-get update and upgrade after installation. What else can be done?

---

### Post by jerrrys on 2012-10-03
I think a fresh install of an LTS is always a better way to go, but what you have described doesn't sound that bad.  Maybe a few commands will shed a little light on it.

sudo dpkg --configure -a

sudo apt-get install -f

---

### Post by arroy_0209 on 2012-10-04
Thanks for your suggestions.  

The output of sudo dpkg --configure -a is nothing. 

The output of sudo apt-get install -f is:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-gconf-2.0 libutouch-grail1 libgtkspell-3-0 appmenu-gtk g++-4.4 libminiupnpc8 libvncserver0 libstdc++6-4.4-dev
  telepathy-indicator libgwibber-gtk2 appmenu-qt gfortran-4.4 libgwibber2 libtelepathy-farstream2 libfreerdp-plugins-standard
  libutouch-evemu1 libutouch-frame1 telepathy-logger python-poppler cups-pk-helper libutouch-geis1 libncurses5-dev libfreerdp1
  libssh-4 libreadline5 appmenu-gtk3 gir1.2-panelapplet-4.0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

``` Although there is suggestion to remove some packages, I've not done yet. Firs of all I need to know if these can explain the problem I have stated.

Second concern is that now a days I try to keep the configuration as given to me, without changing anything drastically. I am afraid, modifying (by installing or removing packages) the system may face more problems. This may turn out to be false but am I right to follow this to be on the safe side?

---

### Post by jerrrys on 2012-10-04
I can't/won't make that call for you, but these are just orphan packages and I don't see any harm in removing them.  Also I don't see this resolving your problems either.

I have full backup on separate drives, so I would be able to play around with no worries.  So with that in mind, I would next try (at your own risk) :

sudo apt-get clean

sudo apt-get update

sudo apt-get dist-upgrade

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by arroy_0209 on 2012-10-04
Thanks for your reply. I want to clear one doubt: is the aim of using "apt-get clean" to remove all installed packages at this stage? and after using update and dist-upgrade commands, am I supposed to reinstall those packages? Then why not use something like "apt-get purge"? 

Second, will it be useful to use command like "apt-get check"? I am interested to know if there are system diagnostic tools which can identify cause of problems giving rise to messages I mentioned. Since I am a beginner, clearing such doubts will be very helpful. Thanks.

---

### Post by jerrrys on 2012-10-04
The commands I gave above are basic and am hoping it may give further error reports to help clear this problem up.

But I can also see your point so I suggest that we just wait for a while and see if others will come along with any other ideas.  Im going to be out of the house all day today so will check back this evening.

---

### Post by sigmatht on 2012-10-04
The man pages will give you a lot of information about the different commands and its usage.  Generally in your terminal you can do:  man command 

:~$ man apt-get

.
.
.
clean
           clean clears out the local repository of retrieved package files.
           It removes everything but the lock file from
           /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When
           APT is used as a dselect(1) method, clean is run automatically.
           Those who do not use dselect will likely want to run apt-get clean
           from time to time to free up disk space.
.
.
.

---

### Post by raja.genupula on 2012-10-04
> **arroy_0209 said:**
> I upgraded to 12.04 from 10.04 nine days ago and also installed lxde. So far there had been two messages stating "ubuntu12.04 faced a problem..please report etc" and once that "compiz faced a problem and need to close". (There were also two other error messages; I forgot details.) On looking at the details I found that latest ubuntu problem was related to lx-panel (I noticed firefox window icon in the panel blinking endlessly). I am worried what to do about such repeated error messages. These frighten me. Is there any way to test how stable my operating system is at the moment? Should I do a fresh install of ubuntu?

I should mention that I had installed some programs like gimp, latex (documentation package), etc and have run sudo apt-get update and upgrade after installation. What else can be done?


You are not alone . I am also facing the same issues .

that better thing we all can do is restart the application and send reports to Ubuntu . that could help us to report our issue to Ubuntu dev's .

---

