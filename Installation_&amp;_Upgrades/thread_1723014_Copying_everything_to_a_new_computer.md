---
title: "Copying everything to a new computer"
date: 2011-04-06
forum: Installation &amp; Upgrades
---

### Post by Townley89 on 2011-04-06
Hey team,

Just curious: I have config settings on one computer that I like (spent a lot of time writing up easystroke commands, rating songs in Banshee, saving a bunch of wireless network configurations... etc etc.) 

So much stuff that I might just like to copy my entire harddrive and all of my folders to an external hard drive and then replace everything on my new computer from there. 

Any idea how I could go about doing that? 

Many thanks!

---

### Post by admkbc on 2011-04-06
You can create a image disk and restore it on new hard disk but system mightn't stable.

---

### Post by Townley89 on 2011-04-06
Thanks for the reply!

Where might I access all of these files? I tried copying every folder in my "File system" folder but it gives me symbolic link issues, and also estimates file size at 120TB (which seems unlikely given my computer's 320GB hard drive)

Also, what software might I use to make such an .iso and will the USB creator work on it?

---

### Post by SeijiSensei on 2011-04-06
Usually copying /etc and /home will save most important configuration data, unless you put things in unusual places outside your home directory.  When backing up you need to run any copying commands with sudo to avoid any permission issues.

---

### Post by oldfred on 2011-04-06
If you have installed a lot of applications you may want to do this also:

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

List Packages
dpkg --get-selections > ubuntu-files
Reinstall
sudo dpkg --set-selections < ubuntu-files && sudo apt-get dselect-upgrade

If going to a new version it will install the newer package as this is just a long list of packages. You may want to houseclean first and/or manually edit list. You do not need to reinstall old kernels and with 11.04 Open Office will not be installed but LibreOffice will be. You would not want both (normally). Other apps may be the same.

---

### Post by lister king of smeg on 2011-04-06
you might not necessarily want to upgrade to 11.04 if you are someone who likes to just use the LTS editions though. then swaping office suites is not a issue unless you perfer libera office.

---

### Post by C.S.Cameron on 2011-04-07
You can put your new HDD into the old computer, boot the live CD then use:
```
dd if=/dev/sda of=/dev/sdb
```
Where sda is the drive you wish to clone and sdb is the target.
sdb needs to be larger than sda.
dd takes a while and there are no flashing lights or speedometer.
everything on the new drive will be the same as on the old one.

---

### Post by spcwingo on 2011-04-07
You can try this:

[Clonezilla]("http://clonezilla.org/")

and have the same exact install on you new HDD.  :popcorn:

---

### Post by scottme on 2011-05-02
Thanks a lot for this tip. I knew there had to be an easy way to do this!

---

