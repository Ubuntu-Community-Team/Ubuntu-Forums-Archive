---
title: "[SOLVED] Having some package error issue."
date: 2016-02-23
forum: Installation &amp; Upgrades
---

### Post by shahzaibmuneeb on 2016-02-23
I'm having some package error issue and I can't seem to figure out what it is, I cannot resolve it with apt-get install -f.


Here is my 

command result 
```
sudo dpkg --configure -a
```


```
dpkg: dependency problems prevent configuration of linux-image-generic-lts-vivid: linux-image-generic-lts-vivid depends on linux-image-3.19.0-51-generic; however:
  Package linux-image-3.19.0-51-generic is not installed.


dpkg: error processing package linux-image-generic-lts-vivid (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-3.19.0-51-generic:
 linux-image-extra-3.19.0-51-generic depends on linux-image-3.19.0-51-generic; however:
  Package linux-image-3.19.0-51-generic is not installed.


dpkg: error processing package linux-image-extra-3.19.0-51-generic (--configure):
 dependency problems - leaving unconfigured
Setting up phpmyadmin (4:4.0.10-1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package phpmyadmin (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-generic-lts-vivid:
 linux-generic-lts-vivid depends on linux-image-generic-lts-vivid (= 3.19.0.51.36); however:
  Package linux-image-generic-lts-vivid is not configured yet.


dpkg: error processing package linux-generic-lts-vivid (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-generic-lts-vivid
 linux-image-extra-3.19.0-51-generic
 phpmyadmin
 linux-generic-lts-vivid



```


and 

for  ```
sudo apt-get install -f
```

 ```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  dkms esound-common libaudiofile1 libesd0 libgraphicsmagick3 libnatpmp1
  librabbitmq1 libsoxr0 libsvga1 libtar0 libvidstab1.0 libvncclient0
  libvorbisidec1 libx265-59 libxine1-bin libxine1-ffmpeg libxine1-gnome
  libxine1-misc-plugins libxine1-plugins libxine1-x linux-headers-3.13.0-66
  linux-headers-3.13.0-66-generic linux-headers-3.13.0-71
  linux-headers-3.13.0-71-generic linux-headers-3.19.0-25
  linux-headers-3.19.0-25-generic linux-headers-3.19.0-31
  linux-headers-3.19.0-31-generic linux-headers-3.19.0-39
  linux-headers-3.19.0-39-generic linux-image-3.19.0-25-generic
  linux-image-3.19.0-31-generic linux-image-3.19.0-39-generic
  linux-image-extra-3.19.0-25-generic linux-image-extra-3.19.0-31-generic
  linux-image-extra-3.19.0-39-generic psensor-common python-amqp
  python-anyjson python-billiard python-cl python-dateutil python-kombu
  python-mailer python-memcache python-pyparsing python-tz python-yaml
  transmission-common vlc-plugin-pulse
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.19.0-51-generic
Suggested packages:
  fdutils linux-lts-vivid-tools
The following NEW packages will be installed
  linux-image-3.19.0-51-generic
0 to upgrade, 1 to newly install, 0 to remove and 2 not to upgrade.
4 not fully installed or removed.
Need to get 0 B/16.8 MB of archives.
After this operation, 47.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 584743 files and directories currently installed.)
Preparing to unpack .../linux-image-3.19.0-51-generic_3.19.0-51.57~14.04.1_amd64.deb ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.19.0-51-generic_3.19.0-51.57~14.04.1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.19.0-51-generic_3.19.0-51.57~14.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



```


Thank you :)

---

### Post by Bashing-om on 2016-02-23
shahzaibmuneeb; Hello;

The advisory :
> 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ..

is a new one on me, and has my interest and attention.
Let's see if we can find out what has the lock on the file.
What returns :
```

lsof /var/cache/debconf/config.dat
ps -aux |grep /var/cache/debconf/config.dat

```

and for a safety net, what kernel is presently booted ? - must not mess around with this one !
```

uname -r

```

See then what it will take to get the -3.19.0-51 kernel installed.

[INDENT][INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT][/INDENT]

---

### Post by shahzaibmuneeb on 2016-02-23
[IMG]https://i.gyazo.com/e606d2be6f26b8b3cf45747a2e902771.png[/IMG]

Thank you for looking into this :)

---

### Post by Bashing-om on 2016-02-23
shahzaibmuneeb; Hummmm ..

That says that presently there is noting with a lock on the control file .
What now results:
```

sudo apt update
sudo apt upgrade

```
please put these outputs between code tags. promotes readability and maintaining the formatting :
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

as a place to start looking further.

[INDENT][INDENT]it's a process
[INDENT][INDENT][INDENT]we can get the better of it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by shahzaibmuneeb on 2016-02-23
update was fine.

upgrade did this:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 linux-image-extra-3.19.0-51-generic : Depends: linux-image-3.19.0-51-generic but it is not installed
 linux-image-generic-lts-vivid : Depends: linux-image-3.19.0-51-generic but it is not installed
E: Unmet dependencies. Try using -f.



```

---

### Post by Bashing-om on 2016-02-23
shahzaibmuneeb; Uh huh ...

Let's see what results with giving the package manager a gentle push .
```

sudo apt install linux-image-3.19.0-51-generic

```

Depending on what the package manager says/does is what we do next .

[INDENT][INDENT]maybe all there is to it 
[/INDENT][/INDENT]

---

### Post by shahzaibmuneeb on 2016-02-23
:(

```

shahzaib@thinkpad:~$ sudo apt install linux-image-3.19.0-51-generic
[sudo] password for shahzaib: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dkms esound-common libaudiofile1 libesd0 libgraphicsmagick3 libnatpmp1
  librabbitmq1 libsoxr0 libsvga1 libtar0 libvidstab1.0 libvncclient0
  libvorbisidec1 libx265-59 libxine1-bin libxine1-ffmpeg libxine1-gnome
  libxine1-misc-plugins libxine1-plugins libxine1-x linux-headers-3.13.0-66
  linux-headers-3.13.0-66-generic linux-headers-3.13.0-71
  linux-headers-3.13.0-71-generic linux-headers-3.19.0-25
  linux-headers-3.19.0-25-generic linux-headers-3.19.0-31
  linux-headers-3.19.0-31-generic linux-headers-3.19.0-39
  linux-headers-3.19.0-39-generic linux-image-3.19.0-25-generic
  linux-image-3.19.0-31-generic linux-image-3.19.0-39-generic
  linux-image-extra-3.19.0-25-generic linux-image-extra-3.19.0-31-generic
  linux-image-extra-3.19.0-39-generic psensor-common python-amqp
  python-anyjson python-billiard python-cl python-dateutil python-kombu
  python-mailer python-memcache python-pyparsing python-tz python-yaml
  transmission-common vlc-plugin-pulse
Use 'apt-get autoremove' to remove them.
Suggested packages:
  fdutils linux-lts-vivid-tools
The following NEW packages will be installed
  linux-image-3.19.0-51-generic
0 to upgrade, 1 to newly install, 0 to remove and 2 not to upgrade.
4 not fully installed or removed.
Need to get 0 B/16.8 MB of archives.
After this operation, 47.5 MB of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 584743 files and directories currently installed.)
Preparing to unpack .../linux-image-3.19.0-51-generic_3.19.0-51.57~14.04.1_amd64.deb ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.19.0-51-generic_3.19.0-51.57~14.04.1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.19.0-51-generic_3.19.0-51.57~14.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by Bashing-om on 2016-02-23
shahzaibmuneeb; Yuk !

I hate when this happens, but I do not know !
If there is no pressing need for a resolution, let's sit here a spell and see what others here can advise.
I just can not fathom where that lock condition could originate from.

Else, well I do have a dirty thought.

[INDENT][INDENT]what to do,
[INDENT][INDENT][INDENT]what to do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by shahzaibmuneeb on 2016-02-23
I can't really install anything else with this issue at hand and I'm a developer so it's pretty pressing! :( I think it surfaced during a  part way installation of phpmyadmin (which you can see from my original post as a result of my command [COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg --configure -a).

[/FONT][/COLOR]Why can I not remain with kernel 49 without this error?[COLOR=#000000][FONT=Ubuntu Mono]


[/FONT][/COLOR]

---

### Post by QDR06VV9 on 2016-02-23
I have on occasion had to use this
```
sudo \rm -v /var/cache/debconf/*.dat
```
But wait for Bashing-om to see.

---

### Post by ian-weisser on 2016-02-23
The error is that a lockfile is present.
Look for it in /var/lock. If there, rm the lockfile...if you are really, really, really sure that dpkg isn't running.

See [http://ubuntuforums.org/showthread.php?t=1495612](http://ubuntuforums.org/showthread.php?t=1495612) for a similar situation a few years ago.

---

### Post by Bashing-om on 2016-02-23
shahzaibmuneeb; K;

Let's go with your thought - even though there is no other instance of it raising it's head - :
```

sudo dpkg-reconfigure phpmyadmin

``` to make sure phpmyadmin is not an issue.

> 
Why can I not remain with kernel 49 without this error?

because: if the package manager is not happy, nobody is happy

[INDENT][INDENT]maybe a step forward
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-02-23
shahzaibmuneeb; Hey ...

Still with us ?
Ian's directive is apt:
```

sysop@1404mini:~$ ls -al /var/lock
lrwxrwxrwx 1 root root 9 May 19  2013 /var/lock -> /run/lock
sysop@1404mini:~$ ls -al /run/lock
total 0
drwxrwxrwt  2 root root  40 Feb 23 11:33 .
drwxr-xr-x 17 root root 540 Feb 23 11:37 ..
sysop@1404mini:~$

```
and as well that of runrickus, when we know what the lock condition is .

[INDENT][INDENT]together we can
[/INDENT][/INDENT]

---

### Post by QDR06VV9 on 2016-02-23
*****This is just informational*****
ian-weisser gives very wise advice with _being very sure that dpkg is not running!!_
Never being one to tell someone to run commands blindly>>>
Here is what Bashing-om's output returns for me on fresh install of Xenial(16.04), Plus running my first post command..
```
[me@me-Lenovo-B570 ~]$ ls -al /var/lock
lrwxrwxrwx 1 root root 9 Feb 23 12:22 /var/lock -> /run/lock
[me@me-Lenovo-B570 ~]$ ls -al /run/lock
total 4
drwxrwxrwt  4 root     root     100 Feb 23 16:09 .
drwxr-xr-x 28 root     root     880 Feb 23 19:34 ..
-rw-r--r--  1 root     root      22 Feb 23 16:09 asound.state.lock
drwxr-xr-x  2 root     root      40 Feb 23 16:09 subsys
drwxr-xr-x  2 whoopsie whoopsie  60 Feb 23 16:09 whoopsie
[me@me-Lenovo-B570 ~]$ sudo \rm -v /var/cache/debconf/*.dat
[sudo] password for me: 
removed '/var/cache/debconf/config.dat'
removed '/var/cache/debconf/passwords.dat'
removed '/var/cache/debconf/templates.dat'
[me@me-Lenovo-B570 ~]$ ls -al /run/lock
total 4
drwxrwxrwt  4 root     root     100 Feb 23 16:09 .
drwxr-xr-x 28 root     root     880 Feb 23 19:34 ..
-rw-r--r--  1 root     root      22 Feb 23 16:09 asound.state.lock
drwxr-xr-x  2 root     root      40 Feb 23 16:09 subsys
drwxr-xr-x  2 whoopsie whoopsie  60 Feb 23 16:09 whoopsie
[me@me-Lenovo-B570 ~]$ 
```.
It would be good advice to reboot after for a clean session.

---

### Post by shahzaibmuneeb on 2016-02-24
I have ran these commands:

Should I run runrickus's command?

```

shahzaib@thinkpad:~$ sudo dpkg-reconfigure phpymyadmin
[sudo] password for shahzaib: 
dpkg-query: package 'phpymyadmin' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: phpymyadmin is not installed.

```

```

shahzaib@thinkpad:~$ ls -al /var/lock
lrwxrwxrwx 1 root root 9 Oct 28 19:32 /var/lock -> /run/lock
shahzaib@thinkpad:~$ ls -al /run/lock
total 0
drwxrwxrwt  4 root     root       80 Feb 24 07:35 .
drwxr-xr-x 31 root     root     1080 Feb 24 07:35 ..
drwxr-xr-x  2 www-data root       40 Feb 24 07:34 apache2
drwxr-xr-x  2 whoopsie whoopsie   60 Feb 24 07:34 whoopsie
shahzaib@thinkpad:~$ ^C
shahzaib@thinkpad:~$ 

```

---

### Post by shahzaibmuneeb on 2016-02-24
Okay! Woo! I follow Ian's link ([http://ubuntuforums.org/showthread.php?t=1495612](http://ubuntuforums.org/showthread.php?t=1495612)) and that helped cancel my partway phpmyadmin installation. Then after that I ran 

```
sudo apt-get -f install
```

and that seemed to fix it.

Thank you guys :)

---

### Post by Bashing-om on 2016-02-24
shahzaibmuneeb; :)

Outstanding work .

I say again
[INDENT][INDENT]ain't 'buntu wonderful
[INDENT][INDENT][INDENT]together we can
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

