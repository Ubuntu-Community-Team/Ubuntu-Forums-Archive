---
title: "booting multiple Linux distros"
date: 2012-04-24
forum: Installation &amp; Upgrades
---

### Post by d0.higgs on 2012-04-24
Hi all,

I have installed Scientific Linux 6.2 on a seperate HDD lately. SL6 is nothing but RedHat Enterprise Linux 6.
I had Ubuntu 12.04 installed on my first HDD but after the installation of SL6, grub seemed to have changed (replaced) by the one of SL6. I cannot boot to Ubuntu any more.
How may I solve this issue. After some search, there was no specific way to do this.
What makes my problem harder is that I have encrypted my home directory on the HDD which has Ubuntu12.04 and I cannot retrieve any of the files I need to work with in SL6 (SL6 is the distro for my work)

help me please, and thank you in advance,

---

### Post by techsupport on 2012-04-24
> **d0.higgs said:**
> Hi all,

I have installed Scientific Linux 6.2 on a seperate HDD lately. SL6 is nothing but RedHat Enterprise Linux 6.
I had Ubuntu 12.04 installed on my first HDD but after the installation of SL6, grub seemed to have changed (replaced) by the one of SL6. I cannot boot to Ubuntu any more.
How may I solve this issue. After some search, there was no specific way to do this.
What makes my problem harder is that I have encrypted my home directory on the HDD which has Ubuntu12.04 and I cannot retrieve any of the files I need to work with in SL6 (SL6 is the distro for my work)

help me please, and thank you in advance,

What I would do is this. You might like it, but here goes. (encypted Ubuntu can be a pain sometimes)

I would rehook the old drive that is encrypted running Ubuntu. Make it the master. Unhook Fedora. Use a resque disc of Ubuntu to reinstall the Grub again. Then after getting grub working for your encrypted Ubuntu again I would Remastersys the whole entire system. Put that image on a USB Thumb Drive to reinstall in Fedora Virtualbox or VMWare. Reinstall it virtually and run it inside Red Hat from now on. 

In Remastersys use the BACKUP option and not DIST. After you reinstall your old encrypted drive so you can boot from it again, here is how to install Remastersys Backup:

[http://debianhelp.wordpress.com/2012/04/20/how-to-install-and-use-remastersys-in-ubuntu-os/](http://debianhelp.wordpress.com/2012/04/20/how-to-install-and-use-remastersys-in-ubuntu-os/)

:guitar:

Remastersys doesn't work in Fedora, so this a one way street.

---

### Post by faizlo on 2012-04-24
Thanks for the quick reply... but I am afraid I dont have a thumbdrive for this solution... and no hdd to backup my stuff.

---

### Post by kc1di on 2012-04-24
> **d0.higgs said:**
> Hi all,

I have installed Scientific Linux 6.2 on a seperate HDD lately. SL6 is nothing but RedHat Enterprise Linux 6.
I had Ubuntu 12.04 installed on my first HDD but after the installation of SL6, grub seemed to have changed (replaced) by the one of SL6. I cannot boot to Ubuntu any more.
How may I solve this issue. After some search, there was no specific way to do this.
What makes my problem harder is that I have encrypted my home directory on the HDD which has Ubuntu12.04 and I cannot retrieve any of the files I need to work with in SL6 (SL6 is the distro for my work)

help me please, and thank you in advance,
I think you should be able to do it by installing grub 2 here's how.
[http://www.webtechquery.com/index.php/2010/04/install-grub2-from-live-cd/]("http://www.webtechquery.com/index.php/2010/04/install-grub2-from-live-cd/")

you may have to configure SL6 manually but grub 2 should be able to boot both os's shouldn't make a difference if your home directory is encrypted.

---

### Post by faizlo on 2012-04-24
Well, I tried this:

I have physicaly diconnected my SL6 HDD and tried to boot but I could not.
I also tried installing grup again through mounting the hdd which has ubuntu but did not work.

Problem is I can boot SL6 and not Ubuntu any more. And yes, the necrypted home directory has nothing to do with the problem - but it is causing me a "work" problem!

---

### Post by d0.higgs on 2012-04-24
I could solve it!
Here is what I did:
run Ubuntu from a LiveCD (any version- does not have to match the installed version)
opena  terminal and run:
```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair
```

then run boot-repair and it will fix it automatically.


Thank you guys

---

### Post by kc1di on 2012-04-25
Glad you got it going :)

---

### Post by YannBuntu on 2012-04-25
@d0.higgs: please could you click "Thread tools" and set this thread as [Solved]

---

