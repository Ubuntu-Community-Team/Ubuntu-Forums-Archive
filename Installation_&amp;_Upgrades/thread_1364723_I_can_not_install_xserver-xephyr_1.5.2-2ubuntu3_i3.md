---
title: "I can not install xserver-xephyr_1.5.2-2ubuntu3_i386.deb ,please help me."
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by cnhujin on 2009-12-26
I want to install Maemo on ubuntu v9.0,but firstly I must install xserver-xephyr,but
why not install xserver-xephyr_1.5.2-2ubuntu3_i386.deb on ubuntu V9.0 
That says: Can't find the software xserver-xephyr_1.5.2-2ubuntu3_i386.deb ,but I do download this software from [http://packages.ubuntu.com/hu/intrepid/i386/xserver-xephyr/download](http://packages.ubuntu.com/hu/intrepid/i386/xserver-xephyr/download).
Please help me
my email: [email]ad@china-3net.com[/email]
-----------
The following is my operation:
root@hujin-desktop:/tmp/maemo# sudo apt-get install xserver-xephyr_1.5.2-2ubuntu3_i386.deb 
&#27491;&#22312;&#35835;&#21462;&#36719;&#20214;&#21253;&#21015;&#34920;... &#23436;&#25104;
&#27491;&#22312;&#20998;&#26512;&#36719;&#20214;&#21253;&#30340;&#20381;&#36182;&#20851;&#31995;&#26641;       
&#27491;&#22312;&#35835;&#21462;&#29366;&#24577;&#20449;&#24687;... &#23436;&#25104;       
[COLOR=Red]**E: &#26080;&#27861;&#25214;&#21040;&#36719;&#20214;&#21253; xserver-xephyr_1.5.2-2ubuntu3_i386.deb**[/COLOR]

root@hujin-desktop:/tmp/maemo# sudo apt-get install ./xserver-xephyr_1.5.2-2ubuntu3_i386.deb 
&#27491;&#22312;&#35835;&#21462;&#36719;&#20214;&#21253;&#21015;&#34920;... &#23436;&#25104;
&#27491;&#22312;&#20998;&#26512;&#36719;&#20214;&#21253;&#30340;&#20381;&#36182;&#20851;&#31995;&#26641;       
&#27491;&#22312;&#35835;&#21462;&#29366;&#24577;&#20449;&#24687;... &#23436;&#25104;       
E: &#26080;&#27861;&#25214;&#21040;&#36719;&#20214;&#21253; .

---

### Post by taurus on 2009-12-26
If you downloaded it, then it was saved in ~/Desktop.  So, open a terminal and install it by hand.

Applications -> Accessories -> Terminal
```
cd ~/Desktop
sudo dpkg -i **filename**.deb
```
Replace the filename with the actually name of the program that you want to install.

---

### Post by cnhujin on 2009-12-26
Thank you.
I have installed it.

root@hujin-desktop:/tmp/maemo# sudo dpkg -i xserver-xephyr_1.5.2-2ubuntu3_i386.deb 
&#36873;&#20013;&#20102;&#26366;&#34987;&#21462;&#28040;&#36873;&#25321;&#30340;&#36719;&#20214;&#21253; xserver-xephyr&#12290;
(&#27491;&#22312;&#35835;&#21462;&#25968;&#25454;&#24211; ... &#31995;&#32479;&#24403;&#21069;&#24635;&#20849;&#23433;&#35013;&#26377; 130346 &#20010;&#25991;&#20214;&#21644;&#30446;&#24405;&#12290;)
&#27491;&#22312;&#35299;&#21387;&#32553; xserver-xephyr (&#20174; xserver-xephyr_1.5.2-2ubuntu3_i386.deb) ...
&#27491;&#22312;&#35774;&#32622; xserver-xephyr (2:1.5.2-2ubuntu3) ...


root@hujin-desktop:/tmp/maemo# dpkg -l | grep xephyr
ii  xserver-xephyr                       2:1.5.2-2ubuntu3                           nested X server

---

### Post by cnhujin on 2009-12-26
> **taurus said:**
> 
```
cd ~/Desktop
sudo dpkg -i **filename**.deb
```Replace the filename with the actually name of the program that you want to install.

But I typeed  
sudo apt-get install xserver-xephyr why it can install it?

---

### Post by taurus on 2009-12-26
Are you using Ubuntu 9.04 or 9.10 because there is no v9.0?  Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by cnhujin on 2009-12-26
> **taurus said:**
> Are you using Ubuntu 9.04 or 9.10 because there is no v9.0?  Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```


The next step, I want to install maemo, and I install scratchbox,and maemo-sdk,but I met the wrong message when I installed the scratchbox,please help me.
root@hujin-desktop:/tmp/maemo# sh ./maemo-scratchbox-install_5.0.sh -u root /scratchbox
This script will install Scratchbox 1.0.14 'apophis' release to your computer.

Install options
---------------

Install from packages=apt
Scratchbox install path=/scratchbox
Scratchbox group=sbox
armel compiler=cs2007q3-glibc2.5-arm
i386 compiler=cs2007q3-glibc2.5-i386
armel devkits=perl:debian-etch:qemu:doctools:svn:git
i386 devkits=perl:debian-etch:doctools:svn:git
armel CPU transparency=qemu-arm-sb

Checking for prerequisites
--------------------------

Running as user root... yes
Not running as user root inside fakeroot... yes
Running outside of scratchbox... yes
Scratchbox installation existing... no
Running on Linux kernel... yes
Running on i386 architecture... yes
Host kernel binfmt_misc support... yes
Host kernel VDSO support... no
E: Host kernel VDSO support is incompatible with scratchbox.
E: You can disable VDSO support for this session with
E: 'echo 0 > /proc/sys/vm/vdso_enabled' as root
E: For a permanent solution you may add 'vm.vdso_enabled = 0'
E: to /etc/sysctl.conf and run 'sysctl -p' as root

---

### Post by cnhujin on 2009-12-26
> **taurus said:**
> Are you using Ubuntu 9.04 or 9.10 because there is no v9.0?  Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

Yes,the version is 9.10

root@hujin-desktop:/etc/apt# cat sources.list
#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

---

### Post by taurus on 2009-12-26
I have xserver-xephyr in my repos.  Maybe try to remove the # in front of backports & Canonical's.

---

### Post by cnhujin on 2009-12-26
> **taurus said:**
> I have xserver-xephyr in my repos.  Maybe try to remove the # in front of backports & Canonical's.

Now I type:

echo 0 > /proc/sys/vm/vdso_enabled

and for a permanent solution you may add 'vm.vdso_enabled = 0' to /etc/sysctl.conf

type sysctl -p as root

but I met the wrong when I type follows:
please help me.

root@hujin-desktop:/tmp/maemo# sh ./maemo-scratchbox-install_5.0.sh -u root /scratchbox
This script will install Scratchbox 1.0.14 'apophis' release to your computer.

Install options
---------------

Install from packages=apt
Scratchbox install path=/scratchbox
Scratchbox group=sbox
armel compiler=cs2007q3-glibc2.5-arm
i386 compiler=cs2007q3-glibc2.5-i386
armel devkits=perl:debian-etch:qemu:doctools:svn:git
i386 devkits=perl:debian-etch:doctools:svn:git
armel CPU transparency=qemu-arm-sb

Checking for prerequisites
--------------------------

Running as user root... yes
Not running as user root inside fakeroot... yes
Running outside of scratchbox... yes
Scratchbox installation existing... no
Running on Linux kernel... yes
Running on i386 architecture... yes
Host kernel binfmt_misc support... yes
Host kernel VDSO support... yes
No host kernel SELinux extensions... yes
Host kernel local IPv4 port range... yes
No conflicting binfmt_misc interpreter... yes
Scratchbox user names... root yes

Everything seems to be ok.
[COLOR=Red]E: can't get the lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: can't lock the status dir
E: Running apt-get update failed.
E: Please correct the problem with apt and try again.
E: Or try an alternative installation method.[/COLOR]

---

### Post by taurus on 2009-12-26
If you have synaptic or software sources open, close it.

---

