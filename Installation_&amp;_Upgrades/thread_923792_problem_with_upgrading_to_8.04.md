---
title: "problem with upgrading to 8.04"
date: 2008-09-18
forum: Installation &amp; Upgrades
---

### Post by boogey on 2008-09-18
hey everybody, I'm pretty new to this all so I appologise if this is a rather stupid question:

I'm trying to upgrade my laptop to ubuntu 8.04. This is what I get:

[I]Not enough free disk space

The upgrade aborts now. The upgrade needs a total of 1411M free space on disk '/usr'. Please free at least an additional 167M of disk space on '/usr'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.[/I]

but even after I did that I still get the same message. I tried to clean my computer up but nothing helped so far.

This is my discspace:
[I]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             1.4G  604M  663M  48% /
varrun                252M   88K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  140K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-52-386/volatile
/dev/sda8              60G   26G   32G  45% /home
/dev/sda6             4.6G  3.2G  1.2G  74% /usr
/dev/sda7             2.8G  257M  2.4G  10% /var[/I]

I'm not quite sure what I can safely delete in /usr, so if someone could quickly (I guess I'm just too inexperienced - and I don't want to mess anything up) help me there, it would be really appreciated.  
cheers

---

### Post by haydnc on 2008-09-18
> **boogey said:**
> 

This is my discspace:
[I]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             1.4G  604M  663M  48% /
varrun                252M   88K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  140K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-52-386/volatile
/dev/sda8              60G   26G   32G  45% /home
/dev/sda6             4.6G  3.2G  1.2G  74% /usr
/dev/sda7             2.8G  257M  2.4G  10% /var[/I]


If you're planning on upgrading and not keeping an active version of (Dapper?) on your machine the easiest way might possibly be to just install 8.04 directly over the top of your existing installation.

I've done this a couple of times in the past without any serious issues and as long as you've not been putting data in non-standard locations as long as you don't format over the top of your /home mount point (/dev/sda8) you won't lose any of your own data.

Just treat it like a new fresh install of 8.04 rather than an upgrade, when it asks you where to install customize the mount-points the same as you've got them above and just be extra careful that you don't tell it to format the one you set up for /home.

Anyone else here have personal experience that indicates there would be a problem with doing that?

---

### Post by boogey on 2008-09-18
> **haydnc said:**
> If you're planning on upgrading and not keeping an active version of (Dapper?) on your machine the easiest way might possibly be to just install 8.04 directly over the top of your existing installation.

I've done this a couple of times in the past without any serious issues and as long as you've not been putting data in non-standard locations as long as you don't format over the top of your /home mount point (/dev/sda8) you won't lose any of your own data.

Just treat it like a new fresh install of 8.04 rather than an upgrade, when it asks you where to install customize the mount-points the same as you've got them above and just be extra careful that you don't tell it to format the one you set up for /home.

Anyone else here have personal experience that indicates there would be a problem with doing that?

thanks for the reply, I thought about that but was too scared to lose data simply because I'm not 100% knowing what I'm doing. I still am, but if that is my best bet, I guess I go with it. thanks again...

---

### Post by haydnc on 2008-09-18
You could hold off until someone else steps in with an agreement or an alternative suggestion.

Personally I've found that if you don't accidentally overwrite the hard drive partition that contains your data (usually your /home drive unles you've been putting stuff else where on purpose) then you don't lose anything by doing a clean install and only writing over / , /usr and /var which is easy enough as long as you're careful at the point where you actually partition your hard drive and define mount points. 
:)

---

### Post by boogey on 2008-09-18
I will wait (would have to get the cd first anyways), maybe knows something that allows me just to upgrade.
I feel that I could delete a few of the /usr files especially as I'm told this at one point of the upgrade (that obviously never gets finished):

[I]Support for some applications ended

Canonical Ltd. no longer provides support for the following software packages. You can still get support from the community.

If you have not enabled community maintained software (universe), these packages will be suggested for removal at the end of the upgrade.

bluez-pcmcia-support
console-common
console-data
doc-debian
evms
evms-ncurses
festlex-cmu
festlex-poslex
festvox-kallpc16k
gcj-4.1-base
gij-4.1
gnome-cups-manager
gok
gtkhtml3.8
ladspa-sdk
libcompfaceg1
libconfig-inifiles-perl
libdvdnav4
libdvdread3
libevms-2.5
libgcj7-jar
libgda2-3
libgda2-common
libglib1.2
libgnomecupsui1.0-1c2a
libgnucrypto-java
libgtk1.2
libgtk1.2-common
libjaxp1.2-java
liblzo1
libnetcdf3
libpq4
libstlport4.6c2
libxml1
libxmlsec1
libxmlsec1-nss
libxmlsec1-openssl
menu-xdg
pcmcia-cs
pmount
python-eunuchs
python-gadfly
python-htmltmpl
python-kjbuckets
python-netcdf
python-pgsql
python-soappy
python-sqlite
python-stats
python-syck
reportbug
ttf-baekmuk
vnc-common
xmms [/I]

Not quite sure if they are usr or/and var files, any idea if it would be safe to get rid of them before the upgrade?
cheers

---

### Post by kostkon on 2008-09-18
> **boogey said:**
> hey everybody, I'm pretty new to this all so I appologise if this is a rather stupid question:

I'm trying to upgrade my laptop to ubuntu 8.04. This is what I get:

[I]Not enough free disk space

The upgrade aborts now. The upgrade needs a total of 1411M free space on disk '/usr'. Please free at least an additional 167M of disk space on '/usr'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.[/I]

but even after I did that I still get the same message. I tried to clean my computer up but nothing helped so far.

This is my discspace:
[I]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             1.4G  604M  663M  48% /
varrun                252M   88K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  140K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-52-386/volatile
/dev/sda8              60G   26G   32G  45% /home
/dev/sda6             4.6G  3.2G  1.2G  74% /usr
/dev/sda7             2.8G  257M  2.4G  10% /var[/I]

I'm not quite sure what I can safely delete in /usr, so if someone could quickly (I guess I'm just too inexperienced - and I don't want to mess anything up) help me there, it would be really appreciated.  
cheers
I think you are getting this error msg because you have only 663MB available in your partition for the root folder (i.e. */*). In general, I don't think you can do an upgrade since you have such a small root partition, only 1.4GB and I don't know if you will be able to free more space.

You will need maybe about 900MB free space in */*. Obviously, during the upgrade process Ubuntu downloads the new packages in */tmp* before installing them.

If I'm wrong, please someone to correct me.

EDIT: just saw that it says you need 1400MB, so disregard the above I said about needing 900MB.

---

### Post by haydnc on 2008-09-18
I have to agree, at least in principle with kostkon. The chances of you being able to upgrade based on the amount of free space it says you need - is fairly low.

That's the main argument for installing over the top of the existing version.

But I've been wrong before. :)

---

### Post by boogey on 2008-09-18
> **kostkon said:**
> I think you are getting this error msg because you have only 663MB available in your partition for the root folder (i.e. */*). In general, I don't think you can do an upgrade since you have such a small root partition, only 1.4GB and I don't know if you will be able to free more space.

You will need maybe about 900MB free space in */*. Obviously, during the upgrade process Ubuntu downloads the new packages in */tmp* before installing them.

If I'm wrong, please someone to correct me.

EDIT: just saw that it says you need 1400MB, so disregard the above I said about needing 900MB.

Do I understand you correctly that you think there's no way to free 167M needed (as 1.2G are free)? I was thinking there are some folders containing leftover data from installations and deinstallations that I might be able to delete for example. If I only knew which...:(

---

### Post by kostkon on 2008-09-18
> **boogey said:**
> Do I understand you correctly that you think there's no way to free 167M needed (as 1.2G are free)? I was thinking there are some folders containing leftover data from installations and deinstallations that I might be able to delete for example. If I only knew which...:(
Ah, you're right! It says you need 1.4GB in */usr* and you have this folder in another partition where there is space you can free. So you need to only free another about 200MB, this is good.

Yes, you could do an
```
sudo apt-get autoclean
```
to clear the package cache but this is in
```
/var/cache/apt/archives
```
and not in */usr*, so it will not make any difference.

You could try to remove (*completely remove* from *Synaptic*) any applications that you have installed and you don't longer need (or just remove them for the upgrade. You can install them back after the end of the upgrade).

Try to avoid uninstalling any default Ubuntu applications since this may perplex the upgrade process and create problems.

---

### Post by boogey on 2008-09-19
> **kostkon said:**
> Ah, you're right! It says you need 1.4GB in */usr* and you have this folder in another partition where there is space you can free. So you need to only free another about 200MB, this is good.

Yes, you could do an
```
sudo apt-get autoclean
```
to clear the package cache but this is in
```
/var/cache/apt/archives
```
and not in */usr*, so it will not make any difference.

You could try to remove (*completely remove* from *Synaptic*) any applications that you have installed and you don't longer need (or just remove them for the upgrade. You can install them back after the end of the upgrade).

Try to avoid uninstalling any default Ubuntu applications since this may perplex the upgrade process and create problems.

Thanks for the reply. The ```
sudo apt-get autoclean
``` was actually one of the first things I tried and you are right, it didn't change anything. I also got rid of most non-default applications but back then I thought that didn't make a difference as well. But now that you say that I might get rid of skyp and stuff and see what happens then...
back in a bit

---

### Post by boogey on 2008-09-20
ok, thanks to your help I was able to upgrade after getting rid of everything possible down to open office and stuff. Nice! :)
The only things that doesn't work right now is Skype (after I downloaded it again) and the volume  is totally messed up (just not getting loud really...) but that's it so far....
If you guys come up with something for that, that would be great!
thanks again

---

