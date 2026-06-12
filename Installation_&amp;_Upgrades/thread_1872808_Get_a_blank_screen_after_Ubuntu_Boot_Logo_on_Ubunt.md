---
title: "Get a blank screen after Ubuntu Boot Logo on Ubuntu 11.10"
date: 2011-10-31
forum: Installation &amp; Upgrades
---

### Post by samjad51 on 2011-10-31
Hi,

I did a clean upgrade of Ubuntu 11.10 onto a 2nd hard drive, 1st hard drive is running Windows 7.

Straight after installation, I had to reboot, so i could get out of the live cd. After I had rebooted, i logged in, and installed all updates, and installed the Nvidia Restricted Drivers.

Requiring a reboot, i did, after which i have been having problems.

Straight after I get the Ubuntu GUI for the Boot, my monitor just goes Flashes Analog, and then Digital, as in its searching for input. However it just sits there. So basically, I have a blank screen, however, I can still type, and log in, as I can hear the Welcome sounds.

For the restricted drivers, i picked the Nvidia 173 (Recommended)

I'm running it on an old computer, but here are the specs:
- Pentium 4 2.6GHZ HT
- 1GB Ram
- Nvidia GeForce 6300 (256MB)(AGP 8x)
- Connected to monitor through DVI

I don't think its a problem with the graphics card or monitor, as it works perfectly with windows 7.

Thanks in advance :)

---

### Post by raja.genupula on 2011-10-31
Hi man

 sometimes graphics card are gonna be problem....

[http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html](http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html)


PLease provide me the output of 
 ```
lsmod | grep video
```
all the best

---

### Post by wshruti on 2011-10-31
Reference: [http://uksysadmin.wordpress.com/2011/10/14/upgrade-to-ubuntu-11-10-problem-waiting-for-network-configuration-then-black-screen-solution/](http://uksysadmin.wordpress.com/2011/10/14/upgrade-to-ubuntu-11-10-problem-waiting-for-network-configuration-then-black-screen-solution/)



Have you just upgraded to Ubuntu 11.10 Oneiric Ocelot and now getting  the “Waiting for network configuration” message followed by “Waiting up  to 60 seconds more for network”? This then might be accompanied by a  black blank screen.
 **[update] **I’ve updated this post to reflect the copy  step mentioned in the bug post below is surplus as /run is mounted tmpfs  – the refined steps are below. The fix is removing the old /var/run and  /var/lock then pointing those old locations to /run and /run/lock  respectively. I’m suspecting this bug only comes about after an upgrade  from your existing session (e.g. apt-get dist-upgrade) where it must  have trouble removing these directories because existing services have  files needed in there.
 The bug is here ([https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/858122](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/858122)) and the fix is based on this: [https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441/comments/24](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441/comments/24) :
 
[LIST=1]
[*]Hit Ctrl+Alt+F1 at the blank screen to get you to a non-X terminal (tty1)
[*]Login in with your username and password
[*]Change to root with: sudo -i and enter your password
[*]mkdir -p /run /run/lock
[*]rm -rf /var/run /var/lock
[*]ln -s /run /var
[*]ln -s /run/lock /var
[*]reboot
[/LIST]
 You should have 11.10 back again.

---

### Post by MAFoElffen on 2011-10-31
> **samjad51 said:**
> Straight after installation, I had to reboot, so i could get out of the live cd. After I had rebooted, i logged in, and installed all updates, and installed the Nvidia Restricted Drivers. Requiring a reboot, i did, after which i have been having problems.

Straight after I get the Ubuntu GUI for the Boot, my monitor just goes Flashes Analog, and then Digital, as in its searching for input. However it just sits there. So basically, I have a blank screen, however, I can still type, and log in, as I can hear the Welcome sounds.

For the restricted drivers, i picked the [COLOR=Red]Nvidia 173[/COLOR] (Recommended)

I'm running it on an old computer, but here are the specs:
- Pentium 4 2.6GHZ HT
- 1GB Ram
- Nvidia GeForce 6300 (256MB)(AGP 8x)
- Connected to monitor through DVI

Wit respect to the other 2 previous posts... post 2 was on the right track, but gave you the wrong commandline argument / although not needed as your post already gave what video card you had (brand & model). Post 2, although handy if you had a wireless card and received one of those messages or not getting wireless, is not the case you described... and since it was a clean install, you were not a canidate for that.

*** What you described was a normal login without any graphics (at all).  You have an Nvidia Geoforce 6300.

If you are booted and pressed <cntrl><alt><F2> and can get to a TTY terminal session (tty2)... If not follow these instructions in this post:
**[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][[B]Temporalrily Booting Into a TTY Text Console**]("http://ubuntuforums.org/showpost.php?p=11383888&postcount=715")[/SIZE][/COLOR][/SIZE][/COLOR][/B]
- Then
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old.173

```If you then followed the instructions in this post:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][B][Finding the Right NVidia Driver from the Card ID]("http://ubuntuforums.org/showpost.php?p=10910784&postcount=284")
[/B]You'd find that the nvidia-173 is not the series driver recommended for your card, rather the nvidia-current is...  And you now ant to make sure that since you installed the wrong driver that all residual pieces of that driver or any previous drivers are gone before you install the correct driver, SO:
[/SIZE][/COLOR][/SIZE][/COLOR]```

sudo apt-get update
sudo nvidia-installer --uninstall
sudo apt-get remove nvidia-*
sudo apt-get install --reinstall linux-headers-'uname -r'
sudo apt-get install nvidia-current  
sudo nvidia-xconfig  
sudo apt-get upgrade
sudo shutdown -r now

```Note that some of the commands above may report that there where no files found. That is okay.  Just making sure they are not there.

Please tell me how it goes...

---

### Post by samjad51 on 2011-11-01
> **MAFoElffen said:**
> Wit respect to the other 2 previous posts... post 2 was on the right track, but gave you the wrong commandline argument / although not needed as your post already gave what video card you had (brand & model). Post 2, although handy if you had a wireless card and received one of those messages or not getting wireless, is not the case you described... and since it was a clean install, you were not a canidate for that.

*** What you described was a normal login without any graphics (at all).  You have an Nvidia Geoforce 6300.

If you are booted and pressed <cntrl><alt><F2> and can get to a TTY terminal session (tty2)... If not follow these instructions in this post:
**[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][[B]Temporalrily Booting Into a TTY Text Console**]("http://ubuntuforums.org/showpost.php?p=11383888&postcount=715")[/SIZE][/COLOR][/SIZE][/COLOR][/B]
- Then
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old.173

```If you then followed the instructions in this post:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][B][Finding the Right NVidia Driver from the Card ID]("http://ubuntuforums.org/showpost.php?p=10910784&postcount=284")
[/B]You'd find that the nvidia-173 is not the series driver recommended for your card, rather the nvidia-current is...  And you now ant to make sure that since you installed the wrong driver that all residual pieces of that driver or any previous drivers are gone before you install the correct driver, SO:
[/SIZE][/COLOR][/SIZE][/COLOR]```

sudo apt-get update
sudo nvidia-installer --uninstall
sudo apt-get remove nvidia-*
sudo apt-get install --reinstall linux-headers-'uname -r'
sudo apt-get install nvidia-current  
sudo nvidia-xconfig  
sudo apt-get upgrade
sudo shutdown -r now

```Note that some of the commands above may report that there where no files found. That is okay.  Just making sure they are not there.

Please tell me how it goes...
Hi, thanks for your advice


I did as you said, and was able to go to the command line by pressing alt+ctrl+F2

I typed in the codes and everything went fine, but when I rebooted,  It was still the Same problem as before. I even reinstalled, and selected driver current

Please advise, thanks in adv

---

### Post by samjad51 on 2011-11-02
Thank you all for your help,

It turned out to be that it was getting extended to me TV by default. So just had to change settings on which monitor to make primary. Thanks again

---

