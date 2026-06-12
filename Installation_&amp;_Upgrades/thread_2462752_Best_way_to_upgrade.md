---
title: "Best way to upgrade?"
date: 2021-05-27
forum: Installation &amp; Upgrades
---

### Post by m-knichel on 2021-05-27
I am upgrading from 18.04 to 20.04.  I will do a fresh install (safest imho).  What I struggle with every time I upgrade is what programs I have installed.  I found apt-clone, but don't know if it is wise to blanket install everything that *was* installed or if there is a better way to handle this?

I also struggle with best way to move mysql db's.  Should I just export them (mysqldump) then import them?

Thanks in advance for advice.

J

---

### Post by ActionParsnip on 2021-05-27
```

sudo do-release-upgrade

```
should kick it off. Obviously watch for gotchas if you run any fancy services (We have no detail about the system). For example, FreeRadius is significantly different in configuration style

---

### Post by guiverc on 2021-05-27
I just completed an upgrade from *bionic* to *focal* which was done via *upgrade via re-install*.

It was a desktop, and I used the "*something-else*", selected my existing partitions & did not format, so it 

- noted my installed packages
- erased system directories
- installed new system
- added back the packages I had added to my system (*if available in Ubuntu repositories** for the new release*)
- no user file is touched (as they are in $HOME).

Okay, I didn't realize my laptop had encrypted home (*my mistake)*, so it failed, and I had to repeat the install (with package needed installed).. but I saw that as my fault for not exploring with a *live* system before hand (*I booted it normally so never noticed the encryption*).

A *release-upgrade* is normally my first choice, but it takes a long time.. The *upgrade via re-install* (*non-clean*) I find super quick & easy (*if you're not using encryption anyway.. encrypted home isn't offered anymore which I knew about; but forgot I was using*).  

This *upgrade via re-install* isn't as good with servers though; as *conf* files are often kept in system directories (thus are wiped & need to be restored..) but it's **great**for desktops!

Me, I usually *clean* my applications before the upgrade (less packages to *release upgrade* or *re-install *given how I just did it), especially if they're 3rd party.  You get an error message if any can't be restored (using *upgrade via re-install*) so I do what I can to avoid any error message(s) & need to check out what couldn't be re-installed...  (18.04->20.04, python2 is eol, Qt4 was eol already but is now gone etc).

I'd always suggest reading the [release notes]("https://wiki.ubuntu.com/FocalFossa/ReleaseNotes") first.

---

### Post by grahammechanical on 2021-05-27
I would like to add: On a system with a separate /home partition that is not going to be formatted as part of the upgrade process, do not leave the upgrade unattended. If the upgrade process asks for user input and we are not there then upgrade will pause and may even stop if sufficient time pass by. 

Regards

---

### Post by m-knichel on 2021-05-27
I usually don't have great success with the release-upgrade.  Not sure why, so I tend to install fresh.  Maybe I will give it another try.

---

### Post by TheFu on 2021-05-27
What to backup?  

Work backwards from what is needed to restore:
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
> Not that anyone cares, but I do backups a little differently for a few reasons.
* I do not backup the core OS.
* I do backup data, lists of installed packages, system and personal settings.
* My restore process begins by performing a fresh install of the OS with minimal setup (usually just an ssh-server)
* Next I restore /etc/, /home/, and any server data (DBs, websites, nextcloud, wallabag, zimbra, etc).
* Last I take a list of installed packages created just prior to making daily backups, and install those. They see the prior **settings**, accept those settings. They see the prior **data** and accept it. The restored system isn't 100% bit-for-bit identical, but the data and settings are. It also saves about 4GB of backup data per machine.

Be certain the "local_backup" is somewhere included in your backups and secure enough that you don't worry about non-admin users seeing it. To get the list of manually installed packages:
```
apt-mark showmanual | tee $local_backup/apt-mark.manual
```

To restore on the new system:
```
sudo apt-mark manual $(cat apt-mark.manual)
sudo apt-get -u dselect-upgrade
sudo apt-get -f install

```

Some of the packages won't be available anymore, but most will.

---

