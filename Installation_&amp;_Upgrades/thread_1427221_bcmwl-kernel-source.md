---
title: "bcmwl-kernel-source"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by Xavier1984X on 2010-03-11
lab@xiamubuntuhost:/var/cache/apt/archives/partial$ sudo apt-get purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1,970kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 186978 files and directories currently installed.)
Removing bcmwl-kernel-source ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing bcmwl-kernel-source (--purge):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
lab@xiamubuntuhost:/var/cache/apt/archives/partial$ sudo apt-get purge bcmwl-kernel-source


above is a copy of an error i get when trying to remove bcmwl-kernel-source this package/file has been causing me problems for a couple days now and i just want to remove the file and start over, this problem started after i attempted to install the broadcom wireless drivers in 9.10 the install hung up and i had to hard shutdown my system because if this i think a lock has remained on this file somewhere and i cannot find it, i am pretty used to the ubuntu environment and this one has me stumped any help would be very appreciated. 

any help on this would be appreciated
thanks
Xavier1984X

---

### Post by Xavier1984X on 2010-03-11
has anyone else encountered this error?

---

### Post by leorolla on 2010-03-11
Did you try to re-install it before uninstalling?

---

### Post by Xavier1984X on 2010-03-12
it does not matter what i try i even tried to forcibly remove it and it kept telling me it could not be removed.

---

### Post by leorolla on 2010-03-12
What does
```
$ sudo dpkg-reconfigure bcmwl-kernel-source
```
say?

---

### Post by syed.rakib.al.hasan on 2010-04-09
_**this is what i get in return**_

root@dell:~$ sudo dpkg-reconfigure bcmwl-kernel-source
/usr/sbin/dpkg-reconfigure: bcmwl-kernel-source is broken or not fully installed
root@dell:~$ 

this error is very painful.:(:(:(:(

---

### Post by leorolla on 2010-04-09
> **syed.rakib.al.hasan said:**
> _**this is what i get in return**_

root@dell:~$ sudo dpkg-reconfigure bcmwl-kernel-source
/usr/sbin/dpkg-reconfigure: bcmwl-kernel-source is broken or not fully installed
root@dell:~$ 

this error is very painful.:(:(:(:(

Could you show us the output of
```
sudo dpkg -r bcmwl-kernel-source

```?

---

### Post by syed.rakib.al.hasan on 2010-04-10
```

rakib@Rakib-DellVostro-1510:~$ sudo dpkg -r bcmwl-kernel-source
[sudo] password for rakib: 
(Reading database ... 191516 files and directories currently installed.)
Removing bcmwl-kernel-source ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing bcmwl-kernel-source (--remove):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 bcmwl-kernel-source
rakib@Rakib-DellVostro-1510:~$ 

```

---

### Post by syed.rakib.al.hasan on 2010-04-10
still no luck.......
:(:(:(:(

---

### Post by leorolla on 2010-04-11
Maybe adding --force-all after -r?

---

### Post by odinwise on 2010-04-11
hello,

I had this same issue, and did some searching online and found a fix.

in terminal type the following:

sudo rm /var/lib/dpkg/info/bcmwl-kernel-source.{postinst,prerm,postrm}
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get clean

then do:

sudo apt-get update
sudo apt-get upgrade

open synaptic package manager (system>administration>synaptic package manager) and search for bcmwl.
make sure both are installed, if they are not, mark them for install (right click>mark for installation), if they are, mark them for reinstallation.

reboot

in terminal do another:

sudo apt-get update
sudo apt-get upgrade

(not sure if this was necessary, but I did it anyway)

open hardware drivers and activate the broadcom STA wireless driver which should be there.

this worked for me, although as an additional bit: after I connected to my wireless network and it let me know, I unplugged the wired connection and my computer froze...a restart brought me back with a working wireless connection. to avoid a freeze, maybe try disconnecting from the wired connection from the menu before unplugging the cable.

hope this helps!

---

### Post by syed.rakib.al.hasan on 2010-04-11
> **leorolla said:**
> Maybe adding --force-all after -r?

this gives back the same response as i stated in my last post
:(:(:(:(

---

### Post by leorolla on 2010-04-12
Did you try odinwise's post just above?

---

### Post by anildutt on 2010-04-12
> **leorolla said:**
> Did you try odinwise's post just above?
Thanks so much [odinwise]("http://ubuntuforums.org/member.php?u=1048465") ! It solved my issue (though giving some error message regarding Cd-rom while doing "apt-get update")
I was almost about to erase ubuntu 9.10. Tried your suggestion in the last minute. 

(Ubuntu must be beware of network issues when upgrades provided, otherwise it forces users to downgrade(clean re-install) or swith off ubuntu..)

---

### Post by syed.rakib.al.hasan on 2010-04-13
hey odinwise, 

thanks for this one. it worked. but now i have another problem.

the following code works perfectly fine and i dont see the bcmwl error any more.....
> 
sudo rm /var/lib/dpkg/info/bcmwl-kernel-source.{postinst,prerm,postrm}
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get clean

then do:
sudo apt-get update
sudo apt-get upgrade

open synaptic package manager (system>administration>synaptic package manager) and search for bcmwl.

make sure both are installed, if they are not, mark them for install (right click>mark for installation), if they are, mark them for reinstallation.

reboot




but then doing another 
> 
sudo apt-get update


gives a cdrom error like what anildutt said. the error box says
```

Could not download all repository indexes
The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch http://ppa.launchpad.net/gilir/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/gilir/ubuntu/dists/karmic/universe/binary-i386/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

```

and then doing the following gives another error.
> 
open hardware drivers and activate the broadcom STA wireless driver which should be there.


the error is
```

Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

```

---

### Post by leorolla on 2010-04-13
Did you run

```
sudo apt-get upgrade
```

After that?

The error messages about the update are not that bad.

---

### Post by syed.rakib.al.hasan on 2010-04-13
what do the errors mean then?
and what about the fact that when i try to activate my device, it gives this log error?

---

### Post by leorolla on 2010-04-13
They mean what they say: that some archives couldn't be fetched. One of them is the CD. You have CD enabled as a source of packages but apt-get cannot access it.

About the error activating the device, it is not worth trying to understand errors before you upgrade your install.

---

### Post by syed.rakib.al.hasan on 2010-04-13
you mean this is not something to worry about

thanks

---

### Post by syed.rakib.al.hasan on 2010-04-13
whoever might be looking for a solution to this problem,
here is the solution
thanks to odinwise for the solution

```

sudo rm /var/lib/dpkg/info/bcmwl-kernel-source.{postinst,prerm,postrm}
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get clean

```then do:

```

sudo apt-get update
sudo apt-get upgrade

```then open synaptic package manager (system>administration>synaptic package manager) and search for bcmwl.

make sure both bcmwl entries are installed.
if they are not, mark them for install (right click>mark for installation), 
if they are, mark them for reinstallation.

reboot


[CENTER]:guitar:
:popcorn::):):):):popcorn:
:guitar:
[/CENTER]

---

### Post by leorolla on 2010-04-13
Welcome to the forum :-)

---

### Post by ghinix on 2010-07-26
I've tried this, but i'm using a Live USB and is not detecting direct Ethernet, therefore I'm attempting to get my bcm4312 to work without any internet and only using a LIVE usb and the computer with Ubuntu 10.04

please help with this issue.
Thanks in advance

---

### Post by syed.rakib.al.hasan on 2010-07-26
hey ghinix

in my experience with Ubuntu 10.04 which i installed from a Live USB, i did not face any issue with direct ethernet........ and installing my WLAN Card was a snap - all i had to do was go to System > Administration > Hardware Devices and enable my device which was listed there.

i don't know if this post has served your query - but this is the best i could suggest since i have not faced any issue with internet devices in ubuntu 10.04 installed from live USB

-v-

---

### Post by leorolla on 2010-07-26
You will need to download the .deb files directly from packages.ubuntu.com and install them if you don't have wired internet (which is really uncommon).

Look for bcmwl-kernel-source and follow its dependencies as well.

Or try the b43 firmware, it's simpler in your case, but might not work depending on your hardware (not only the wireless card): [https://wiki.ubuntu.com/Testing/Laptop/Lucid/Reports/AcerAspireOneD150](https://wiki.ubuntu.com/Testing/Laptop/Lucid/Reports/AcerAspireOneD150)

---

### Post by ghinix on 2010-07-27
I managed to get Ethernet working on the system, so was able to use .. Administration > Hardware Drivers.. to update the card. First time the updating froze the OS, 2nd time it downloaded and installed for 15 mins so i force rebooted, 3rd and last attempt says it works and is activated but.. but is not detecting any of the zillion wireless networks here.

---

### Post by leorolla on 2010-07-29
Make a fresh LiveUSB.

Boot.

Get wired connection.

Open a terminal and run
```
sudo apt-get update && sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```

---

### Post by ghinix on 2010-07-30
Thank you so much!! This worked perfectly!

---

### Post by cnu1 on 2011-05-14
> **odinwise said:**
> hello,

I had this same issue, and did some searching online and found a fix.

in terminal type the following:

sudo rm /var/lib/dpkg/info/bcmwl-kernel-source.{postinst,prerm,postrm}
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get clean

then do:

sudo apt-get update
sudo apt-get upgrade

open synaptic package manager (system>administration>synaptic package manager) and search for bcmwl.
make sure both are installed, if they are not, mark them for install (right click>mark for installation), if they are, mark them for reinstallation.

reboot

in terminal do another:

sudo apt-get update
sudo apt-get upgrade

(not sure if this was necessary, but I did it anyway)

open hardware drivers and activate the broadcom STA wireless driver which should be there.

this worked for me, although as an additional bit: after I connected to my wireless network and it let me know, I unplugged the wired connection and my computer froze...a restart brought me back with a working wireless connection. to avoid a freeze, maybe try disconnecting from the wired connection from the menu before unplugging the cable.

hope this helps!


Thanks a million, this worked like a charm for me.  I appreciate your detailed description, which helped me a lot!

---

