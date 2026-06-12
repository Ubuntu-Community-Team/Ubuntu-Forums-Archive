---
title: "Ubuntu 11.10 - Cannot Install Synaptic Due to Unmet Dependencies"
date: 2011-12-07
forum: Installation &amp; Upgrades
---

### Post by UbuNewbie123 on 2011-12-07
I tried to install Synaptic in the Ubuntu Software Central:

The following packages have unmet dependencies:

synaptic: Depends: libapt-inst1.2 but it is a virtual package
          Depends: libapt-pkg4.10 but it is a virtual package
          Depends: libatk1.0-0 (>= 1.12.4) but 2.2.0-0ubuntu1 is to be installed
          Depends: libc6 (>= 2.4) but 2.13-20ubuntu5 is to be installed
          Depends: libcairo2 (>= 1.2.4) but 1.10.2-6ubuntu3 is to be installed
          Depends: libfontconfig1 (>= 2.8.0) but 2.8.0-3ubuntu2 is to be installed
          Depends: libfreetype6 (>= 2.2.1) but 2.4.4-2ubuntu1.1 is to be installed
          Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.1-9ubuntu3 is to be installed
          Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.24.0-1ubuntu1 is to be installed
          Depends: libglib2.0-0 (>= 2.14.0) but 2.30.0-0ubuntu4 is to be installed
          Depends: libgtk2.0-0 (>= 2.18.0) but 2.24.6-0ubuntu5 is to be installed
          Depends: libpango1.0-0 (>= 1.14.0) but 1.29.3+git20110916-0ubuntu1 is to be installed
          Depends: libstdc++6 (>= 4.5) but 4.6.1-9ubuntu3 is to be installed
          Depends: libvte9 (>= 1:0.24.0) but 1:0.28.2-0ubuntu2 is to be installed
          Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu3 is to be installed

I tried to reboot to recovery mode by holding the left shift key. I selected the recovery option but it did not display a menu to fix broken packages like some previous versions.

I researched online to find all the apt-get commands to fix my packages but none of them worked.

Any idea how to fix this error? I have spent hours on this.

I also have problems installing Skype due to a similar problem.

---

### Post by BC59 on 2011-12-07
> **UbuNewbie123 said:**
> I tried to install Synaptic in the Ubuntu Software Central:

The following packages have unmet dependencies:

synaptic: Depends: libapt-inst1.2 but it is a virtual package
          Depends: libapt-pkg4.10 but it is a virtual package
          Depends: libatk1.0-0 (>= 1.12.4) but 2.2.0-0ubuntu1 is to be installed
          Depends: libc6 (>= 2.4) but 2.13-20ubuntu5 is to be installed
          Depends: libcairo2 (>= 1.2.4) but 1.10.2-6ubuntu3 is to be installed
          Depends: libfontconfig1 (>= 2.8.0) but 2.8.0-3ubuntu2 is to be installed
          Depends: libfreetype6 (>= 2.2.1) but 2.4.4-2ubuntu1.1 is to be installed
          Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.1-9ubuntu3 is to be installed
          Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.24.0-1ubuntu1 is to be installed
          Depends: libglib2.0-0 (>= 2.14.0) but 2.30.0-0ubuntu4 is to be installed
          Depends: libgtk2.0-0 (>= 2.18.0) but 2.24.6-0ubuntu5 is to be installed
          Depends: libpango1.0-0 (>= 1.14.0) but 1.29.3+git20110916-0ubuntu1 is to be installed
          Depends: libstdc++6 (>= 4.5) but 4.6.1-9ubuntu3 is to be installed
          Depends: libvte9 (>= 1:0.24.0) but 1:0.28.2-0ubuntu2 is to be installed
          Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu3 is to be installed

I tried to reboot to recovery mode by holding the left shift key. I selected the recovery option but it did not display a menu to fix broken packages like some previous versions.

I researched online to find all the apt-get commands to fix my packages but none of them worked.

Any idea how to fix this error? I have spent hours on this.

I also have problems installing Skype due to a similar problem.

Did you update-upgrade before? Maybe there are ready packages to be upgraded. Then try with sudo dpkg --configure -a and sudo apt-get -f install to unblock the dpkg.

---

### Post by BC59 on 2011-12-07
The last resource could be to force the installation

sudo dpkg --force-all -P synaptic

---

### Post by beew on 2011-12-07
Don't need to  go into recovery mode. Open a terminal and type

```
sudo dpkg --configure -a 
``` should fix your broken packages.  The question is what causes the problem in the first place. Did you upgrade? Did you add repositories from other releases?

---

### Post by UbuNewbie123 on 2011-12-07
I did upgrade my Ubuntu 11.10 with the Update Manager.

sudo dpkg --configure -a does not work for me. In fact, I have done all the suggestions above. Nothing works.

What else can I do. I think I should reinstall Ubuntu 11.10. This is so frustrating.

---

### Post by UbuNewbie123 on 2011-12-07
sudo dpkg --configure -a
Returns nothing

sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

vince@ubuntu:~$ sudo dpkg --force-all -P synaptic
dpkg: warning: there is no installed package that matches synaptic

---

### Post by BC59 on 2011-12-07
But if those 2 commnands give you nothing as you said, then your system is working well.

Try to install synaptic through Ubuntu Software Center.

---

### Post by UbuNewbie123 on 2011-12-07
> **BC59 said:**
> But if those 2 commnands give you nothing as you said, then your system is working well.

Try to install synaptic through Ubuntu Software Center.

The error I posted in my initial post was the error I got from installing synaptic in Ubuntu Software Center.

---

### Post by BC59 on 2011-12-07
I think I know what is happening. 

Could you please post your sources.list?

```
sudo gedit /etc/apt/sources.list
```

I think your repositories are messed.

---

### Post by UbuNewbie123 on 2011-12-07
# /etc/apt/sources.list

deb [http://dl2.foss-id.web.id/ubuntu/](http://dl2.foss-id.web.id/ubuntu/) oneiric main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security main restricted universe multiverse
deb [http://dl2.foss-id.web.id/ubuntu/](http://dl2.foss-id.web.id/ubuntu/) oneiric-updates main restricted universe multiverse

=====

You could be right but I'm not sure how to tell. Thanks a lot.

---

