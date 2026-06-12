---
title: "distro upgrade with apt-mirror"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by mazy haze on 2008-04-23
When I switched from edgy to feisty I created my used apt-mirror for mirroring archive.ubuntu.org on an external hard disc, updating the mirror about twice a week at my university (since I've a traffic limit at home). For some time now I have been mirroring not only the gutsy repos, but those for hardy, too for playing around with it a bit. However, I would like to upgrade for gutsy to hardy now, but "update-manager -d" is not aware of this and tries to contact the ubuntu servers instead. As there are about six computers now using this mirror (with two of them having no internet access at all) some solution would be quite useful. Maybe apt-get dist-upgrade could do the trick, but this would ignore ubuntu's update-scripts, wouldn't it? I also thought about using an alternative ubuntu cd for upgrading from cd. But maybe there's some other solution.

BTW, my configuration looks like this:

/etc/apt/mirror.list
```
############# config ##################
#
set base_path    /media/TREKSTOR/Software/APT-Mirror/
#
# if you change the base path you must create the directories below with write privlages
#
set mirror_path  /media/TREKSTOR/Software/APT-Mirror/mirror
set skel_path    /media/TREKSTOR/Software/APT-Mirror/skel
set var_path     /media/TREKSTOR/Software/APT-Mirror/var
# set cleanscript $var_path/clean.sh
# set defaultarch  i386
set nthreads     20
set tilde 0
#
############# end config ##############

deb http://archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-proposed main restricted universe multiverse
deb http://archive.canonical.com/ubuntu gutsy partner
deb http://wine.budgetdedicated.com/apt gutsy main
deb http://www.virtualbox.org/debian gutsy non-free
deb http://snapshots.ekiga.net/ubuntu gutsy main
deb http://www.telemail.fi/mlind/ubuntu gutsy fonts main
deb http://ppa.launchpad.net/woodypl/ubuntu gutsy main

deb http://archive.ubuntu.com/ubuntu gutsy main/debian-installer restricted/debian-installer
deb http://archive.ubuntu.com/ubuntu gutsy-updates main/debian-installer restricted/debian-installer
deb http://archive.ubuntu.com/ubuntu gutsy-security main/debian-installer
deb http://archive.ubuntu.com/ubuntu gutsy-proposed main/debian-installer

deb http://archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu hardy-proposed main restricted universe multiverse
deb http://archive.canonical.com/ubuntu hardy partner
deb http://wine.budgetdedicated.com/apt hardy main
#deb http://www.virtualbox.org/debian hardy non-free
#deb http://snapshots.ekiga.net/ubuntu hardy main
#deb http://www.telemail.fi/mlind/ubuntu hardy fonts main
deb http://ppa.launchpad.net/woodypl/ubuntu hardy main

deb http://archive.ubuntu.com/ubuntu hardy main/debian-installer restricted/debian-installer
#deb http://archive.ubuntu.com/ubuntu hardy-updates main/debian-installer restricted/debian-installer
#deb http://archive.ubuntu.com/ubuntu hardy-security main/debian-installer
#deb http://archive.ubuntu.com/ubuntu hardy-proposed main/debian-installer


deb-amd64 http://archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu gutsy-proposed main restricted universe multiverse
deb-amd64 http://archive.canonical.com/ubuntu gutsy partner
deb-amd64 http://wine.budgetdedicated.com/apt gutsy main
deb-amd64 http://www.virtualbox.org/debian gutsy non-free
deb-amd64 http://snapshots.ekiga.net/ubuntu gutsy main
# deb-amd64 http://www.telemail.fi/mlind/ubuntu gutsy fonts main

deb http://ubuntu.geole.info/ gutsy universe multiverse
deb-amd64 http://ubuntu.geole.info/ gutsy universe multiverse

clean http://archive.ubuntu.com/ubuntu
clean http://archive.canonical.com/ubuntu
clean http://wine.budgetdedicated.com/apt
clean http://www.virtualbox.org/debian
clean http://snapshots.ekiga.net/ubuntu
clean http://www.telemail.fi/mlind/ubuntu
```

/etc/apt/sources.list
```
deb file:///media/TREKSTOR/Software/APT-Mirror/mirror/archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb file:///media/TREKSTOR/Software/APT-Mirror/mirror/archive.ubuntu.com/ubuntu/ gutsy-security main restricted universe multiverse
deb file:///media/TREKSTOR/Software/APT-Mirror/mirror/archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse

deb file:///media/TREKSTOR/Software/APT-Mirror/mirror/archive.canonical.com/ubuntu gutsy partner
# deb file:///media/TREKSTOR/Software/APT-Mirror/mirror/wine.budgetdedicated.com/apt gutsy main
deb file:///media/TREKSTOR/Software/APT-Mirror/mirror/www.virtualbox.org/debian gutsy non-free
deb file:///media/TREKSTOR/Software/APT-Mirror/mirror/snapshots.ekiga.net/ubuntu gutsy main
deb file:///media/TREKSTOR/Software/APT-Mirror/mirror/archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe
deb file:///media/TREKSTOR/Software/APT-Mirror/mirror/www.telemail.fi/mlind/ubuntu gutsy fonts main

```

---

### Post by bryanagee on 2008-05-02
I think I can help, as I have successfully upgraded all of the workstations in our office via the local apt-mirror, but I'm not sure I understand the problem yet... 
When we did the upgrade, it was a matter of clicking the button that said "Install 8.04 LTS" at the top right of the update manager box. It then made some mention that a mirror could not be found. There was also a note in the dialog that this message could be caused by use of a local mirror. If you continued instead of cancelling as it suggests, it simply updates your sources.list by changing "gutsy" to "hardy". As long as you have all the same repos mirrored, it continues like normal from the local mirror. 
I wonder if it might have something to do with the fact that your entries are "file:///". Have you tried making the folder accessable via apache and using http:// instead?

---

### Post by tsvim on 2008-08-13
I'm looking for an answer for this as well, I'm about to setup a local repo at our university. But before I do that I'd like to know how we're going to manage dist-upgrades, we use CentOS on our servers. But most of theIT staff prefers Ubuntu or debian variants on their desktops. So the big downloads occur once every 6 months when 20+ machines start getting the most recent Ubuntu. 
A possible hint to the problem. Ubuntu's upgrade does NOT comply with proxy settings for apt. By manually defining proxy settings as environment variables and running synaptic/adept it will show you the upgrade button.
The upgrade buttion downloads a installer. I suppose this one comes straight from ubuntu's archives no matter your local repository, just once the app runs, it changes your sources in your local repo as described above by bryanagee.
If you find out anything please drop me a note

---

### Post by dzleon on 2009-10-20
I just finished investigating this and I'm now trying an update. Here's what I found. 

The problem is not that update-manager refuses to access the local mirror. The problem is that the source for the list of available versions is set in /etc/update-manager/meta-release, so if you just update the sources.list, a computer without internet access will still try to get the list of distributions from the internet, and even if you download that one and point your computers to it, that file has URLs for other files that also need to be mirrored.

Here's a script that downloads the meta-release files into var/www/ubuntu-releases, downloads the release notes and update tools, and then tweaks the meta-release files to point to these.

```
#!/bin/bash
export http_proxy="http://myproxy:8080"
export server=myserver
cd /var/www/ubuntu-releases

for i in "" -development -lts -proposed; do
 wget http://changelogs.ubuntu.com/meta-release$i -O meta-release$i.orig
done

grep -h "\(ReleaseNotes\)\|\(UpgradeTool\)" meta-release.orig meta-release-development.orig meta-release-proposed.orig meta-release-development.orig |sort |uniq |sed s/".*: //" > /var/spool/apt-mirror/var/release-url.0


wget -t 0 -r -N -l inf -o /var/spool/apt-mirror/var/release-log.0 -i  /var/spool/apt-mirror/var/release-url.0

for i in "" -development -lts -proposed; do 
 sed "s/\(\(\(ReleaseNotes\)\|\(UpgradeTool\)\).*: http:\/\)/\1\/$server\/ubuntu-releases/" meta-release$i.orig > meta-release$i
done

```

With this, a client's /etc/update-manager/meta-release file can be updated to point to your server:
```
URI = http://myserver/ubuntu-releases/meta-release
```

Apparently, something else has to be changed so that your mirror is recognized (possibly /usr/share/update-manager/mirrors.cfg), but I just ran the upgrade and answered yes when asked to continue by just changing jaunty to karmic.

---

