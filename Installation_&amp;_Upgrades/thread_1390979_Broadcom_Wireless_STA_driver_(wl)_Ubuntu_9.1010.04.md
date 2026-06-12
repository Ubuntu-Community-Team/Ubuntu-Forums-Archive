---
title: "Broadcom Wireless STA driver (wl) Ubuntu 9.10/10.04"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by owhno on 2010-01-26
Problem using Broadcom Wireless in Ubuntu 9.10/10.04 because it is not supported by b43 driver ?

Assuming you have tried all normal installation procedures like using the Hardware Drivers tool and you still do not have a working WiFi setup this is what you must do:

   1. Download the Broadcom drivers: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
   2. Unpack and modify the &#8216;src/wl/sys/wl_linux.c&#8216;:
      Line 35 (after #include <linux/etherdevice.h>) add: 
[INDENT]#include < linux/sched.h >[/INDENT]
   3. Compile the code with: make
   4. Copy the new driver: sudo mv wl.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless
   5. Update dependencies: sudo depmod -a
   6. Modify the blacklist to include the &#8216;b43&#8242; and &#8217;ssb&#8217; drivers /etc/modprobe.d/blacklist.conf (Add below the bcm43xx blacklist)

The part above you probably have seen a few times while googling for the answer. But there is a small problem, as you would have noticed, the &#8216;ssb&#8216; driver cannot be blacklisted. It is included in the initrd as I remember from the ubuntuforums. To solve this issue modify the /etc/rc.local to include before the exit(0):

```
rmmod ssb
modprobe wl
```

Now on startup the ssb gets removed and after that the new wl gets inserted. Adding wl to the /etc/modules will not help because the removing needs to be done first.
So with the /etc/rc.local modification everything happens in the correct order for perfect WiFi.

This was tested multiple times on a MacBook Pro with the Broadcom 4328 chipset and should work for all chipsets not supported by the b43 drivers.

**Update:**
Not all systems include the 'linux/sched.h' file. Install the 'linux-headers-generic' package if you get errors. The generic package is a meta package that should install the propper package for your kernel. If it isn't working install with
```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by bwell1211 on 2010-01-30
Thanks! Solved my broadcom issue on Ubuntu 10.04

---

### Post by raumkundschafter on 2010-02-11
hi thanks for your help
although including linux/sched.h in wl/sys/wl_linux.c is not working for me: 
linux.c:35:27: error:  linux/sched.h : No such file or directory
do i have to add sched.h from somewhere?

---

### Post by owhno on 2010-02-16
As I'm now installing it again (daily build from 2 days ago) I see no problem with it. But as I haven't tested it with 9.10 it is probably a missing package. As sched.h is a header file the obvious answer would be that the package linux-header-generic isn't installed (or use the linux-header-$(uname -r) package. This is by default installed on testing systems so probably it is missing on 9.10.

---

### Post by Megaptera on 2010-02-16
This worked on my Dell which is not a Mini though that's what's mentioned. Very easy in _buntus 9.10 
[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

Hope it helps someone?!

---

### Post by owhno on 2010-02-16
You are true that that fixed works for most options, but this is for non supported bmcwl cards. But thanks for mentioning it, because probably someone will stumble on this with a card that works with the normal installation

---

### Post by mcmunt on 2010-02-28
Thanks very much for the fix - worked for me on a Dell D620. :D

I was particularly unhappy as the live CD of Ubuntu 10.04 had the correct wireless drivers in the Restricted Drivers app. But when I did a HDD install there was nothing there.

---

### Post by Megaptera on 2010-02-28
mcmunt,
You're welcome!

---

### Post by dnaand on 2010-03-07
Hi all,

My wireless stopped working following a kernel update to 2.6.31-20-generic-pae. Trying to activate the driver via the usual System -> Administration -> Hardware Drivers -> enable the Broadcom STA proprietary wireless driver route failed for me - an error message told me to check the /var/log/jockey.log for additional information.

When I did I saw the message below:

2010-03-07 19:26:12,459 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-03-07 19:26:12,459 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver

The solution to this for me was simply to install the kernel headers for the newly installed kernel. 

$ sudo apt-get install linux-headers-$(uname -r)

DKMS then does the rest for you building and compiling the wireless drivers for the newly installed kernel as part of the post install configuration process. Once complete my wireless was working again - without the need to grab and build the source from Broadcom... Clearly DKMS does this for you but only _ONCE_ you have manually installed the kernel headers.

NOTE: I had wireless working with this system prior to the kernel upgrade... If you did not, and get the errors I did when trying to activate the driver through the System -> Administration -> Hardware Drivers route, try installing the kernel headers first and then retry activating the driver.

Hope that helps someone out!

---

### Post by Madman on 2010-03-23
this worked great except that I have to run the insmod wl.ko command every time I log in.  How can I/what should I be doing to get the driver to be active every time I boot up?  Thanks.

---

### Post by bloodofangels302 on 2010-04-18
THANKS! this is the only thing that worked for my dell studio 1535.

---

### Post by andril on 2010-04-21
This works - I connected to the lan cable did the updates via Synaptics and the n the drivers were available for the wireless

---

### Post by Gary00 on 2010-04-30
hiya [owhno]("http://ubuntu-virginia.ubuntuforums.org/member.php?u=249202"), i have no doubt that what your saying works, but can u be a bit more detailed about what to do, i have the broadcom downloaded and i have made the mods to "wl_linux.h" but after that im so lost, Thanks for you help and efforts, and yes i am running 10.04

---

### Post by kamalkhadka on 2010-05-01
> **owhno said:**
> Problem using Broadcom Wireless in Ubuntu 9.10/10.04 because it is not supported by b43 driver ?


   3. Compile the code with: make
   

:confused::confused: How is this done?

---

### Post by Cerin on 2010-05-01
> **raumkundschafter said:**
> hi thanks for your help
although including linux/sched.h in wl/sys/wl_linux.c is not working for me: 
linux.c:35:27: error:  linux/sched.h : No such file or directory
do i have to add sched.h from somewhere?

Has anyone resolved this error? I also get this, even though I installed the linux-headers-generic package.

---

### Post by degarb on 2010-05-01
> **kamalkhadka said:**
> :confused::confused: How is this done?

 Very confusing.  Wouldn't installing the gui for ndis or win wireless wrapper, then inserting xp cd for the drivers work much easier?  And, doesn't the popular card, Belkin, use airforce broadcom drivers.   This is too confusing for a regular computer user to follow.  Even after reading the linux manual...months ago.

 The entire procedure about sums up the problem with Linux-love of complexity, the feeling of being elite.  In the windows world, the author would just write up a compiled exe that would install the drivers and works.  One click solution for every one.  Not in Linux.  No.  We must have a 20 step solution that will take an hour to figure out, which may or may not work.  It took 2 days of trying to get my belkin card to work with 9, I could not get the linux solutions to work for what ever reason.  Ndis gui was the only solution that worked.  I doubt if I will be trying this or version 10 because, no wireless card is the equivalent to no system on this laptop.  Not worth the risk or hassle, which saddens me.

Why doesn't someone who is capable, simply write a program to install the driver?  Isn't the core philosophy: usability and to help others.   I appreciate the steps given, but above 99 percent of users' heads.

---

### Post by DrAcid on 2010-05-02
> **kamalkhadka said:**
> How is this done?


Excuse me, but I'll have to agree with **kamalkhadka** on this one...

Would You be so kind and explain to us how _exactly_ is that done?

Thank You!

I have HP Pavilion DV5 1000 laptop, Ubuntu Ultimate Edition 2.5 + Win7 dualboot running...
The wireless works fine on Win7, but on Ubuntu didn't from the very moment I installed it... I am absolutely new to Linux and am VERY fond of it so far... But I can't keep on using laptop with no wireless...

The indicator/sensor on my keyboard didn't work, not turning on the wl card, i guess... A bit of research on Google told me that it could be that my BIOS gotta be updated [apparently that could be the reason why the driver wouldn't install in Ubuntu]...
Updating my BIOS bricked the laptop... Fortunately Google saved me again [YAY! Google]
I updated it successfully using a thumb drive, which got me to the point where I uninstalled and re-installed the Wireless SAT Drivers Using "Hardware Drivers", which GOT me the wanted result! :)

After a few restarts, it stopped working, and I got stuck using M$ Window$... again!

After this, Jockey gives me this error message: 
WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl
WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver

Is there a way to fix this without cable connection to the Inet?

[*whew*] any help appreciated...

P.S.(btw, GREAT forum, love it here ;) )

---

### Post by Cerin on 2010-05-02
Could someone please explain why make fails? I'm running 10.04 and have the headers installed, but I get the error:

```
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  LD      /home/myuser/Downloads/hybrid-portsrc-x86_32-v5.60.48.36/built-in.o
  CC [M]  /home/myuser/Downloads/hybrid-portsrc-x86_32-v5.60.48.36/src/shared/linux_osl.o
  CC [M]  /home/myuser/Downloads/hybrid-portsrc-x86_32-v5.60.48.36/src/wl/sys/wl_linux.o
/home/myuser/Downloads/hybrid-portsrc-x86_32-v5.60.48.36/src/wl/sys/wl_linux.c:35:27: error:  linux/sched.h : No such file or directory
make[2]: *** [/home/myuser/Downloads/hybrid-portsrc-x86_32-v5.60.48.36/src/wl/sys/wl_linux.o] Error 1
make[1]: *** [_module_/home/myuser/Downloads/hybrid-portsrc-x86_32-v5.60.48.36] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [all] Error 2

```

---

### Post by Cerin on 2010-05-02
> **raumkundschafter said:**
> hi thanks for your help
although including linux/sched.h in wl/sys/wl_linux.c is not working for me: 
linux.c:35:27: error:  linux/sched.h : No such file or directory
do i have to add sched.h from somewhere?

I think there might be a typo. Try removing the spaces from the line, e.g. "#include <linux/sched.h>".

Also, try removing the linux-headers-generic package and reinstalling. That fixed that problem for me.

Unfortunately, wireless still doesn't work, but at least it compiles...

---

### Post by Haavet on 2010-05-02
Kamalkhadka, DrAcid: From the terminal go to the folder where you saved the source code. It should be a file called "Makefile" in there, then type:
$ make

I too have followed the above instructions but the fix didn't permanently rectify the problem.

I instead used the rather crude hack below. It'll effectively hard-code access to one specified wireless network, so no good if you frequently access different networks.

Make sure wireless-tools is installed, if not:
$ sudo apt-get install wireless-tools

Verify your network devices is working and wireless networks are detected
$ iwconfig
$ sudo iwlist scan

Make sure wpa-supplicant is installed, if not:
$ sudo apt-get install wpasupplicant

Convert your WPA ASCII password to hex:
$ wpa_passphrase <ssid> [passphrase]
- <ssid> is the name of the Wireless network / router
- [passphrase] is your WPA ASCII password
- Copy down the value after “psk=” that is the hex version of your WPA ASCII password

Using dhcp and WPA here is what is added to /etc/network/interfaces

#The wireless interface
auto wlan0
iface wlan0 inet dhcp
wpa-ssid <SSID of your router>
wpa-ap-scan 1
wpa-key-mgmt WPA-PSK
wpa-psk <the PSK that you wrote down>

*note wlan0 is the name of the wireless interface in this example

Restart the network
$ sudo /etc/init.d/networking restart

Revoke read-permission from others on /etc/network/interfaces
$ sudo chmod o=-r /etc/network/interfaces

---

### Post by earthpigg on 2010-05-03
in case anyone using a **Dell Mini 9** comes across this:

i was able to get **wifi working on 10.04 without ever plugging into wired internet after installing from thumb drive**.

1) install ubuntu 10.04 from thumb drive.
2) boot normally.
3) insert the thumb drive you just installed from.
4) open the file manager, go to the thumb drive, and navigate to pool/restricted/b/bcmwl, and double click on the .deb in there. it will tell you it needs 3 dependancies - make a mental note of which three.
5) navigate back to pool/main, find those deps and install them.
6) install the .deb in pool/restricted/b/bcmwl
7) reboot

---

### Post by caffeinepill on 2010-05-05
> **earthpigg said:**
> in case anyone using a **Dell Mini 9** comes  across this:

i was able to get **wifi working on 10.04 without ever plugging into  wired internet after installing from thumb drive**.

1) install ubuntu 10.04 from thumb drive.
2) boot normally.
3) insert the thumb drive you just installed from.
4) open the file manager, go to the thumb drive, and navigate to  pool/restricted/b/bcmwl, and double click on the .deb in there. it will  tell you it needs 3 dependancies - make a mental note of which three.
5) navigate back to pool/main, find those deps and install them.
6) install the .deb in pool/restricted/b/bcmwl
7) reboot

Even this didn't work for me (Ubuntu 10.04 64 bit), although I see many people have had success with this method!. I was getting various errors when I attempted to install (and several attempts to re-install) the bcmwl-kernel-source package manually via synaptic.

Assuming you have attempted to install bcmwl-kernel-source and its dependencies manually, received errors during its install and synaptic is showing bcmwl-kernel-source as 'installed'... this may solve the problem.

[SIZE=1]Go into synaptic and[/SIZE][SIZE=2][SIZE=1]...

[/SIZE]**completely remove bcmwl-kernel-source** **AND dkms**[/SIZE]

*then**, whilst still in synaptic ***[B][SIZE=2]

install bcmwl-kernel-source[/SIZE][/B]


For me this did the trick, I'm not sure why. (removing dkms was the golden ticket). I then went back into Hardware Drivers and driver was showing as activated but not in use. All it took then was a quick reboot and :guitar:

Hope this helps someone!

---

### Post by wandalalakers on 2010-05-06
Earthpigg

XOXO

It worked for me.
I really didn't want to have to use ndis wrapper stuff.

Caffeinepill,
I put down your info for future reference also in case pigg's didn't work.
I'm usng a Dell D620 with a broadcom wireless.

---

### Post by Mike.Flintjer on 2010-05-10
> **owhno said:**
> Problem using Broadcom Wireless in Ubuntu 9.10/10.04 because it is not supported by b43 driver ?

Assuming you have tried all normal installation procedures like using the Hardware Drivers tool and you still do not have a working WiFi setup this is what you must do:

   1. Download the Broadcom drivers: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
   2. Unpack and modify the &#8216;src/wl/sys/wl_linux.c&#8216;:
      Line 35 (after #include <linux/etherdevice.h>) add:[INDENT]#include < linux/sched.h >[/INDENT]3. Compile the code with: make
   4. Copy the new driver: sudo mv wl.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless
   5. Update dependencies: sudo depmod -a
   6. Modify the blacklist to include the &#8216;b43&#8242; and &#8217;ssb&#8217; drivers /etc/modprobe.d/blacklist.conf (Add below the bcm43xx blacklist)

The part above you probably have seen a few times while googling for the answer. But there is a small problem, as you would have noticed, the &#8216;ssb&#8216; driver cannot be blacklisted. It is included in the initrd as I remember from the ubuntuforums. To solve this issue modify the /etc/rc.local to include before the exit(0):

```
rmmod ssb
modprobe wl
```Now on startup the ssb gets removed and after that the new wl gets inserted. Adding wl to the /etc/modules will not help because the removing needs to be done first.
So with the /etc/rc.local modification everything happens in the correct order for perfect WiFi.

This was tested multiple times on a MacBook Pro with the Broadcom 4328 chipset and should work for all chipsets not supported by the b43 drivers.

**Update:**
Not all systems include the 'linux/sched.h' file. Install the 'linux-headers-generic' package if you get errors. The generic package is a meta package that should install the propper package for your kernel. If it isn't working install with
```
sudo apt-get install linux-headers-$(uname -r)
```


WOO-HOO!!  This worked!!  I can't friggin believe it...IT WORKED!!

I do have to inform the group about one thing though...the par to fthe instructions that say to modify the etc/rc.local file....You cannot edit this file without having root privileges!  That means you can open it, but you cannot save the edits once you get them inserted....

If the author could post the work-around to edit that file, that would be cool...not sure if needed though, as i haven't restarted the computer a few times to check viability of all instructions....

==================================================================================
***EDIT:***
OK, after making it work once, I had to make sure it wasn't a fluke...so I uninstalled Ubuntu, wiped the partition and re-installed.  Re-did the instructions...and found a problem.  These instructions by themselves did not work.  I went and installed from the repositories the fakeroot, ndiswrapper (and the subs that go with that), ndisgtk....pretty much anything that had ANYTHING to do with networking and/or wireless LAN.  Then I re-did the instructions and rebooted the comuter...SUCCESS!!  WirelessLAN up and running, and i am typing this from inside Ubuntu and happier than a puppy with two peckers....and am now finding myself basking in my geekiness!!

GO OPEN SOURCE, GO LINUX!!

---

### Post by screamm on 2010-05-11
This worked for me on Desktop Edition 32-bit (should work on 64-bit aswell):

-Install fresh Ubuntu 10.04 LTS (I saw some errors in terminal background where wireless driver is mentioned :)

2: Updated everything everything in update manager after finished install (needed reboot)

3: Go to System -> Administration -> Hardwaredrivers

4: Broadcom B43 should show up in the list. Mark it and activate.

5: Reboot and voila.

Hope this helps some atleast.

---

### Post by temujin23 on 2010-05-12
Thanks screamm. I tried multiple fixes from this thread and others until I finally just wired the machine and completed your 5 easy steps.

---

### Post by Marite on 2010-05-14
Guys - i did it!!
This crappy STA error was bugging me  for 3 days.
As i am so green in this technical thing, first in my life i had to go  through a million of treads regarding this missing wireless thing and i  had no solution for my case.
1 - i did saw an inactive STA in System/Administration/Hardware  drivers but i couldn't activate it
2- i checked Synaptic package manager and there wasn't this  bcmwl-kernel-source, but there at least was bcmwl-modaliases
3 - i reinstalled the last one bcmwl-modaliases
4 - rebooted computer
5 - in Hardware drivers appeared B43 as already active, but wireless  wasn't working anyways
6 - though i removed B43
7 - rebooted again
8 - tried to activate STA and got message "/var/log/jockey.log"
9 - tried again and got message "Sorry, the Jockey backend crashed"
how da heck could i know, that i have to go to Synaptic manager /   Settings / Repositories / and mark a tickbox in Ubuntu softwear  "Proprietary drivers for devices (restricted) !!!??? This small step  solved all my problems
10 - bcmwl-kernel-source appeared in synaptic
11 - i acivated all of it, rebooted
12....and vuala!! Wireless was there!!

---

### Post by hashbrowns on 2010-05-20
Thanks for the answer here. Clear, detailed, and concise...the open source world needs more devs like you!

I just "rescued" my boss's inspiron 1525 that he had updated to 10.04 at my behest through the alt CD. Then he blamed me for the wifi not working :rolleyes: ah well.

Everything's good now though; didn't need to read beyond the first post. I had already tried the b43-fwcutter from another forum post but that was quite complicated and spawned so many fw versions I didn't know where to start.

Thanks again!

---

### Post by maxthegold on 2010-05-24
Does anybody else see a problem with fixes for a network/internet access problem that contain instructions install stuff with apt-get. My wireless card does not work so I do not have Linux access to the internet, how do I fix that?

---

### Post by mwildam on 2010-05-24
> **caffeinepill said:**
> 
[SIZE=1]Go into synaptic and[/SIZE][SIZE=2][SIZE=1]...
[/SIZE]**completely remove bcmwl-kernel-source** **AND dkms**[/SIZE]
*then**, whilst still in synaptic ***[B][SIZE=2]
install bcmwl-kernel-source[/SIZE][/B]

After trying this I wasn't able to re-install any of those any more.

---

### Post by jgaribay on 2010-06-05
Hi,

Thanks a lot, it worked for me, clear and easy to follow.

Some info of my environment:

Dell Studio 1537
Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
Newtwork Driver: Broadcom 802.11 Linux STA wireless

Regards,
Juan

---

### Post by miyune on 2010-06-08
> **owhno said:**
> Problem using Broadcom Wireless in Ubuntu 9.10/10.04 because it is not supported by b43 driver ?

(...)  But there is a small problem, as you would have noticed, the ‘ssb‘ driver cannot be blacklisted. It is included in the initrd as I remember from the ubuntuforums. To solve this issue modify the /etc/rc.local to include before the exit(0):

```
rmmod ssb
modprobe wl
```Now on startup the ssb gets removed and after that the new wl gets inserted. Adding wl to the /etc/modules will not help because the removing needs to be done first.
So with the /etc/rc.local modification everything happens in the correct order for perfect WiFi.



**Owhno,**

From your first post of this thread ([http://ubuntuforums.org/showthread.php?t=1390979](http://ubuntuforums.org/showthread.php?t=1390979))

I would propose the following update :

If /etc/rc.local shabang has the **option -e **(e.g #!/bin/sh -e), the following code line :

```
rmmod ssb 
modprobe wl
```**shall be replaced by :**

```
rmmod ssb || true  
modprobe wl || true
```Most of the time, "rmmode ssb" would return an error because the module would not be necessarily present (because it has been fully de-installed or never installed yet). This means that the rc.local script would stop its execution (because of option -e in shabang) before it even executes "modprobe wl" so the new module would never be loaded at startup and the wi-fi card would remain disabled.

Also it seems to be usually better to indicate full path to command in script, so the following would be even better :

```
[B]/sbin/rmmod ssb || true
/sbin/modprobe wl || true[/B]
```When script is executed with -e option, **adding "|| true" after the command indicate to explicitly ignore the error return by the command** and to continue execution of script anyway...

Also rmmod et modprobe have an handy option -s which log error via syslog, useful for debugging (error messages are made available in /var/log/syslog file) :)

I spend a lot of time believing that my /etc/rc.local was not executed at startup on Ubuntu 9.10 but it wasn't at all the case. It just this "amazing" -e option at the top of the script which caused me high pain :) 

Thank you for your post, it was a great source for resolving issues with my Broadcom wi-fi card on my Apple MacBook Pro 5,5 with Ubuntu 9.10 (64bits) by compiling and installing the driver from source following your instructions and the [README.txt]("http://www.broadcom.com/docs/linux_sta/README.txt") file available with the driver source.

I may think it would be great to have this information in your original post updated (at the top of this thread) because my post would appears far deep (at the end of it, 5 pages down) so it might be unnoticed by other user trying to resolve similar issues...

**For other users** encountering similar issue with their rc.local file, here is a functional /etc/rc.local file that I used to debug my issue and it works :

-------------------------------------
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

logfile="/tmp/rc.local.log"
/bin/sleep 10
/bin/echo 'rc.local started' > $logfile
/bin/echo `date` >> $logfile
/sbin/rmmod -vs ssb || true
/sbin/modprobe -vs wl || true
/bin/echo 'rc.local ended normally' >> $logfile
exit 0
--------------------------------

The "sleep 10" pause the script for 10 seconds before it continue to execute, allowing other element of the system to be fully initialised before it continue running.
As for the driver loading purpose it may be optional, but in other situation, for other additional startup commands that may be used in the rc.local script, it might be useful.
Others reported in other posts that a slight pause solves their issue with the rc.local script, so I thought it was worth mentioning as extra information.

To help debuging rc.local script situation, it is also always good to test that it works fine when executed manually :

$ sudo -i     // Run console as root
# cd /etc
# ./rc.local  // Manual execution of script

Then check the log file /tmp/rc.local.log and verify availability of wi-fi card in Network Manager...

Happy hacking everyone !

---

### Post by owhno on 2010-06-12
> **miyune said:**
> **Owhno,**

From your first post of this thread ([http://ubuntuforums.org/showthread.php?t=1390979](http://ubuntuforums.org/showthread.php?t=1390979))

I would propose the following update :

If /etc/rc.local shabang has the **option -e **(e.g #!/bin/sh -e), the following code line :

```
rmmod ssb 
modprobe wl
```**shall be replaced by :**

```
rmmod ssb || true  
modprobe wl || true
```


Yeah I found that out yesterday when it didn't work. Thanks for the comment. I'm currently testing the WL module for maverick, but it currently doesn't compile. Will post an update when it works so that when you all upgrade there is a how-to available.

**Update:**
For MAVERICK 10.10, or when you get this error:
```
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-2-generic'
  LD      /home/osteenbergen/wl/built-in.o
  CC [M]  /home/osteenbergen/wl/src/shared/linux_osl.o
  CC [M]  /home/osteenbergen/wl/src/wl/sys/wl_linux.o
/home/osteenbergen/wl/src/wl/sys/wl_linux.c: In function ‘_wl_set_multicast_list’:
/home/osteenbergen/wl/src/wl/sys/wl_linux.c:1434: error: ‘struct net_device’ has no member named ‘mc_list’
/home/osteenbergen/wl/src/wl/sys/wl_linux.c:1434: error: ‘struct net_device’ has no member named ‘mc_count’
/home/osteenbergen/wl/src/wl/sys/wl_linux.c:1435: error: dereferencing pointer to incomplete type
/home/osteenbergen/wl/src/wl/sys/wl_linux.c:1441: error: dereferencing pointer to incomplete type
make[2]: *** [/home/osteenbergen/wl/src/wl/sys/wl_linux.o] Error 1
make[1]: *** [_module_/home/osteenbergen/wl] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-2-generic'
make: *** [all] Error 2

```
That was easier than I thought thanks to some guys from Gentoo:
On there bug system they have an patch which needs to be applied ([http://bugs.gentoo.org/248450](http://bugs.gentoo.org/248450) > [http://bugs.gentoo.org/attachment.cgi?id=232555]("http://bugs.gentoo.org/attachment.cgi?id=232555"))

So go to the 'src/wl/sys' folder and execute 'patch < [location_of_the_diff_file]'
in my case 'patch < ~/Downloads/wl_linux.c.diff'

Then repeat the steps in post 1 and use the ' || true' as suggested in rc.local


**Update 2:**
For those who get this error:
```
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-2-generic'
  CC [M]  /home/osteenbergen/wl/src/shared/linux_osl.o
In file included from /home/osteenbergen/wl/src/shared/linux_osl.c:19:
/home/osteenbergen/wl/src/include/linuxver.h:23:28: error: linux/autoconf.h: No such file or directory
make[2]: *** [/home/osteenbergen/wl/src/shared/linux_osl.o] Error 1
make[1]: *** [_module_/home/osteenbergen/wl] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-2-generic'
make: *** [all] Error 2

```

The autoconf.h is now under generated/ instead of linux/. So edit the line in the src/include/linuxver.h file.

---

### Post by cazacugmihai on 2010-06-12
@earthpigg: Thanks!

---

### Post by Phubar1979 on 2010-06-13
```
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

This is killin me here. I have read google until my eyes bled. Everything I try is just telling me that something isnt right with bcmwl-kernel-source. I don't know what to do. I fear that trying all this different stuff has only made the matter worse.

Please help :confused:

------------------------------------------------------------------------------------------------
--My  System--Alienware--M17x------------------------------------------------------------
[FONT=Courier]**Processor(s)**[/FONT]
[LIST]
[*]Processor- 1
[LIST]
[*]CPU_Name-  Intel(R) Core(TM)2 Duo CPU T9600 @ 2.80GHz
[*]CPU_Manufacturer- GenuineIntel
[*]CPU_Caption- Intel64 Family 6 Model 23 Stepping 10
[*]CPU_CurrentClockSpeed- 2801MHz
[*]CPU_SocketDesignation- Socket 479
[/LIST]
[/LIST]
**[FONT=Courier,Arial][SIZE=3]System Memory[/SIZE][/FONT]**
[LIST]
[*]Memory  Module- 1
[LIST]
[*]Mem_Capacity- 2048MB
[*]Mem_BankLabel- DIMM #1
[*]Mem_Type- DDR3
[*]Mem_Frequency- MHz
[/LIST]
[*]Memory Module- 2
[LIST]
[*]Mem_Capacity- 2048MB
[*]Mem_BankLabel- DIMM #2
[*]Mem_Type- DDR3
[*]Mem_Frequency- MHz
[/LIST]
[/LIST]
**[FONT=Courier,Arial][SIZE=3]BIOS Information[/SIZE][/FONT]**
[LIST]
[*]BIOS_Manufacturer-  Alienware
[*]BIOS_Name- Ver A02 1.00PARTTBLZ
[*]BIOS_Version1- A02
[*]BIOS_Version2- ALWARE - 6040000
[/LIST]
**[FONT=Courier,Arial][SIZE=3]Motherboard  Information[/SIZE][/FONT]**
[LIST]
[*]MB_Manufacturer- Alienware
[*]MB_Product
[*]MB_Version- A02
[/LIST]
**[FONT=Courier,Arial][SIZE=3]Video Adapter[/SIZE][/FONT]**
[LIST]
[*]Video_Caption-  ATI Mobility Radeon HD 4870
[*]Video_AdapterRAM- 1024MB
[/LIST]

---

### Post by paul_harris on 2010-06-13
i had a failed install for broadcom sta wireless, i tried to activate but, failed.
can you tell me why this would be.
patiently waiting.
Paul, 3 day old linux user

---

### Post by paul_harris on 2010-06-13
i should mention that i went to hardware drivers and tried the install, there were 2 listings, neither worked, i noticed the dependancy that was missing and updated, loaded it and there after i had a fail while loading.
why would this happen
cheers again

---

### Post by Superdarion on 2010-06-15
Well, I just thought I'd contribute here.

I tried the original solution and it worked... until I rebooted again. Then I couldn't see the right driver in the Hardware Driver Manager and even if I repeat all the steps (and try the other solutions suggested in following comments by others) I just couldn't get it to work again.

So my solution? Since I hadn't installed anything, I just reinstalled ubuntu from the start. In the liveCD session I can see the right driver in the Hardware Drivers thing, so I selected it. After it downloaded and installed, it asked me to reboot (doing so at this point undoes everything). I didn't reboot but instead finished the installation and then rebooted.

The driver was working after reboot and after the next reboots. It even connected automatically.

---

### Post by Sepero on 2010-06-16
I solved this problem for a friend in a slighty different way. I hope this helps.


1. Add the LiveCD as a repository and Uncheck ALL other repositories.
System> Administration> Software Sources

2. Update software sources. This can be done when you close the Software Sources window, or by using Synaptic.
System> Administration> Synaptic Package Manager> Reload (button)

3. Use Synaptic to Remove bad packages if they are installed.
System> Administration> Synaptic Package Manager> Search (button)
* bcmwl-kernel-source
* b43-fwcutter
* linux-image-2.6.32-22-generic (any linux-image 2.6.32-22 or greater)

4. Use Synaptic to Lock the kernel package linux-image-2.6.32-21-generic, and lock the package linux-headers-generic to version 2.6.32-21.32. (This will prevent the problem from occurring again with future upgrades).
System> Administration> Synaptic Package Manager> Package (menu)> Lock Version

5. Reboot (restart)

6. Install the wifi driver.
System> Administration> Hardware Drivers

7. Reboot (restart)

8. Remove the LiveCD as a repository, and Recheck all the repositories that were unchecked in step #1.
System> Administration> Software Sources

---

### Post by Cthulhu_Dreams on 2010-06-17
I get this:

```
adrian@Alpha-60:~/Downloads/hybrid-portsrc-x86_64-v5.60.48.36$ make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make: *** /lib/modules/2.6.32-22-preempt/build: No such file or directory.  Stop.
make: *** [all] Error 2

```

---

### Post by Sepero on 2010-06-17
Cthulhu_Dreams,
Perhaps you could try the solution I wrote in post #39. It requires no compiling.

---

### Post by mikerev on 2010-06-17
> **Sepero said:**
> Cthulhu_Dreams,
Perhaps you could try the solution I wrote in post #39. It requires no compiling.

Excellent job sir. Spent too much time researching this ridiculous broadcom-typical nonsense until I found your fix. thanks again.

---

### Post by Cthulhu_Dreams on 2010-06-17
I don't know what the hell is going on anymore.

I was trying different things, some how my wireless started working.  However now whenever I press the physical button on my computer that turns wireless on and off, my computer freezes.   Wireless networks have stopped showing up and my computer has these weird pauses....like when I was writing this post the letters wouldn't show up for a few seconds, appear, then everything would type normal until it happened again.

---

### Post by Sepero on 2010-06-18
Cthulhu_Dreams,
It sounds like you may now require a complete reinstall. It is very valuable to keep your /home on a separate partition than the installed system. I'm sorry I cannot help you more.

---

### Post by Jessimo on 2010-06-20
Hey thanks for the how to, but I'm lost at step 3


1. Download the Broadcom drivers: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
2. Unpack and modify the ‘src/wl/sys/wl_linux.c‘:
Line 35 (after #include <linux/etherdevice.h>) add:

    #include < linux/sched.h >

3. Compile the code with: make
4. Copy the new driver: sudo mv wl.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless
5. Update dependencies: sudo depmod -a
6. Modify the blacklist to include the ‘b43&#8242; and ’ssb’ drivers /etc/modprobe.d/blacklist.conf (Add below the bcm43xx blacklist)


I get:  make: *** No targets specified and no makefile found.  Stop.

Any more detailed help? Vancouver ?

Thanks...

---

### Post by Sepero on 2010-06-27
Jessimo,
Perhaps you could try the solution I wrote in post #39. It requires no compiling.

---

### Post by cnwalk on 2010-06-30
EMERGENCY:  I have just installed Ubuntu 10.04 on my bosses computer (Acer Aspire 3000) and I cannot get it to connect to our wireless network. I have read and re-read the postings here on what to do and I am at a complete loss. Please, Please give me step by step details on how to install these drivers/fix this problem. I use Ubuntu 10.04 at home and it works great and I am trying to learn more, but I have never ran into a problem like this before. I have know idea how to configure Linux stuff, I am a reforming PC guy who wasn't very good at that... :confused:

---

### Post by Sepero on 2010-07-01
This thread is about the problem caused by upgrading the system. In an emergency case, you can just reinstall the system from LiveCD and then don't upgrade the system.

I posted simple instructions for how to fix this upgrade issue without having to compile sources in post #39.

[http://ubuntuforums.org/showpost.php?p=9467697&postcount=39](http://ubuntuforums.org/showpost.php?p=9467697&postcount=39)

.

---

### Post by thehrushi on 2010-07-03
> **dnaand said:**
> Hi all,

My wireless stopped working following a kernel update to 2.6.31-20-generic-pae. Trying to activate the driver via the usual System -> Administration -> Hardware Drivers -> enable the Broadcom STA proprietary wireless driver route failed for me - an error message told me to check the /var/log/jockey.log for additional information.

When I did I saw the message below:

2010-03-07 19:26:12,459 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-03-07 19:26:12,459 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver

The solution to this for me was simply to install the kernel headers for the newly installed kernel. 

$ sudo apt-get install linux-headers-$(uname -r)

DKMS then does the rest for you building and compiling the wireless drivers for the newly installed kernel as part of the post install configuration process. Once complete my wireless was working again - without the need to grab and build the source from Broadcom... Clearly DKMS does this for you but only _ONCE_ you have manually installed the kernel headers.

NOTE: I had wireless working with this system prior to the kernel upgrade... If you did not, and get the errors I did when trying to activate the driver through the System -> Administration -> Hardware Drivers route, try installing the kernel headers first and then retry activating the driver.

Hope that helps someone out!


Thanks a ton that worked for me. I too saw the log file but didn't know exactly where it was going wrong! :)

---

### Post by BoucherieSanzot on 2010-07-03
> **caffeinepill said:**
> 

[SIZE=1]Go into synaptic and[/SIZE][SIZE=2][SIZE=1]...

[/SIZE]**completely remove bcmwl-kernel-source** **AND dkms**[/SIZE]

*then**, whilst still in synaptic ***[B][SIZE=2]

install bcmwl-kernel-source[/SIZE][/B]


It worked for me, thanks !

---

### Post by earthpigg on 2010-07-03
> **cnwalk said:**
> EMERGENCY:  I have just installed Ubuntu 10.04 on my bosses computer (Acer Aspire 3000) and I cannot get it to connect to our wireless network. I have read and re-read the postings here on what to do and I am at a complete loss. Please, Please give me step by step details on how to install these drivers/fix this problem. I use Ubuntu 10.04 at home and it works great and I am trying to learn more, but I have never ran into a problem like this before. I have know idea how to configure Linux stuff, I am a reforming PC guy who wasn't very good at that... :confused:

my post of may 2nd was intended for clean installs such as this, not upgrades.

can you tell us what you have tried that hasn't worked?

---

### Post by seb_renaud on 2010-07-04
> **dnaand said:**
> Hi all,

My wireless stopped working following a kernel update to 2.6.31-20-generic-pae. Trying to activate the driver via the usual System -> Administration -> Hardware Drivers -> enable the Broadcom STA proprietary wireless driver route failed for me - an error message told me to check the /var/log/jockey.log for additional information.

When I did I saw the message below:

2010-03-07 19:26:12,459 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-03-07 19:26:12,459 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver

The solution to this for me was simply to install the kernel headers for the newly installed kernel. 

$ sudo apt-get install linux-headers-$(uname -r)

DKMS then does the rest for you building and compiling the wireless drivers for the newly installed kernel as part of the post install configuration process. Once complete my wireless was working again - without the need to grab and build the source from Broadcom... Clearly DKMS does this for you but only _ONCE_ you have manually installed the kernel headers.

NOTE: I had wireless working with this system prior to the kernel upgrade... If you did not, and get the errors I did when trying to activate the driver through the System -> Administration -> Hardware Drivers route, try installing the kernel headers first and then retry activating the driver.

Hope that helps someone out!
Thanks a million dnaand, your post did help me out. I switched to the -preempt kernel and that actually prevented the wl driver from loading. Installing the kernel-headers-preempt ( to match the kernel I am using ) solved my problem.

---

### Post by Sepero on 2010-07-04
SOLUTIONS
SOLUTIONS
SOLUTIONS


There are many solutions offered in this thread. Here are the current proposed solutions and what they entail.



**THEY ARE ORDERED FROM LEAST DIFFICULT (TOP) TO MOST DIFFICULT (BOTTOM).**
Requires removing a few packages
[http://ubuntuforums.org/showpost.php?p=9299776&postcount=9](http://ubuntuforums.org/showpost.php?p=9299776&postcount=9)

Requires wired connection to the internet
[http://ubuntuforums.org/showpost.php?p=9299115&postcount=27](http://ubuntuforums.org/showpost.php?p=9299115&postcount=27)

Requires wired connection to the internet
[http://ubuntuforums.org/showpost.php?p=8931286&postcount=9](http://ubuntuforums.org/showpost.php?p=8931286&postcount=9)

Requires only LiveCD
[http://ubuntuforums.org/showpost.php?p=9223467&postcount=21](http://ubuntuforums.org/showpost.php?p=9223467&postcount=21)

Requires only LiveCD (downgrades kernel and prevents kernel upgrading)
[http://ubuntuforums.org/showpost.php?p=9467697&postcount=39](http://ubuntuforums.org/showpost.php?p=9467697&postcount=39)

Requires reinstall and wired connection to the internet
[http://ubuntuforums.org/showpost.php?p=9280854&postcount=25](http://ubuntuforums.org/showpost.php?p=9280854&postcount=25)

Requires software compiling and wired connection to the internet
[http://ubuntuforums.org/showpost.php?p=8727145&postcount=1](http://ubuntuforums.org/showpost.php?p=8727145&postcount=1)



SOLUTIONS
SOLUTIONS
SOLUTIONS

---

### Post by earthpigg on 2010-07-04
Sepero,

I think my [proposed solution]("http://ubuntuforums.org/showpost.php?p=9223467&postcount=21") should be there under

"Requires installing 4 packages from LiveUSB (in a specific order). May only work on Dell Mini 9/10 or 32bit."

more difficult than the solution involving only installing one package, less difficult than the one that involves disabling kernel upgrades.

---

### Post by Sepero on 2010-07-05
There you go. Sorry about that.

---

### Post by mattsweegold on 2010-07-05
Could someone please help me with the solution *Requiring software compiling and wired connection to the internet* I do not know how to execute the make command and would appreciate a further simplification of the steps. Also, the STA driver has a read me on its site, but due to my inexperience with Linux, I do not know how to follow this guide either. I would appreciate any help configuring the STA driver, as I have spent much time on this subject and am about to buy another card altogether.

As an aside, I have downloaded the driver through the restricted drivers menu and was able to download and activate it. In spite of this however, it does not let me connect to my network even when WPA 2 is turned off. Also, I use 64 bit Lynx if it's of any insight.

---

### Post by Nick_Jinn on 2010-07-09
> **Gary00 said:**
> hiya [owhno]("http://ubuntu-virginia.ubuntuforums.org/member.php?u=249202"), i have no doubt that what your saying works, but can u be a bit more detailed about what to do, i have the broadcom downloaded and i have made the mods to "wl_linux.h" but after that im so lost, Thanks for you help and efforts, and yes i am running 10.04


Yes, the OP skipped some important steps for noobs....Im sure a lot of people know what it means to "Compile with :Make" but a lot of us are not there yet, especially the ones asking for help.


Is there an easier step by step breakdown for this?



Right now I am working on an Acer Aspire 3000 from 2005. It is my clients computer and I am going to feel like a **** if I cant get wireless working on this old machine.

---

### Post by nvjopsddhapnv on 2010-07-11
Thanks a lot! It works fine for My Vostro 3400 ... Thank you again.

---

### Post by Cableguy707 on 2010-07-13
I really hope that the team fixes this problem with 10.10... and i am a noob too, so i have no idea what compile:make means or the rest of the instructions mean as well, no offence to the ubuntu team, you guys have made a great operating system, but of course...

DAMN YOU ANTI-LINUX LAPTOPS!!!

---

### Post by Sepero on 2010-07-13
> **Cableguy707 said:**
> I really hope that the team fixes this problem with 10.10... and i am a noob too, so i have no idea what compile:make means or the rest of the instructions mean as well, no offence to the ubuntu team, you guys have made a great operating system, but of course...

DAMN YOU ANTI-LINUX LAPTOPS!!!

Have a look at post number 53
[http://ubuntuforums.org/showpost.php?p=9547955&postcount=53](http://ubuntuforums.org/showpost.php?p=9547955&postcount=53)

---

### Post by Cableguy707 on 2010-07-14
*facepalm* i should not have opened my big mouth, sry..

---

### Post by Sepero on 2010-07-15
Hey no problem cableguy. We've all been very frustrated with Linux from time to time. Sometimes it's tough going against the grain when it comes to operating systems. Personally, I often find wiki's more helpful than forums. Forums need a better way to make the posts with solutions more visible.

---

### Post by isevere08 on 2010-07-23
Hey there!

Thank you for the post.  I guess it's no surprise, but I have just the same issue with my laptop.  I've been fighting with the wifi problem for three days now and could not solve it at all.  I even tried to re-install it for four times.  Now, however, I can have wifi but only for 10-20 minutes after I shut down my computer and leave it alone for a few hours.  

Yet this does not make me happy.  Since I am a new user of linux, I can't quite understand what you did starting from the fourth step.  Could you PLEASE explain it for such dummies as I am

---

### Post by Sepero on 2010-07-23
isevere08 is another victim of a system (ubuntuforums on vBulletin), which does not make thread solutions intuitive or easy to find.

I've done all I can.
isevere08, please view post #53
[http://ubuntuforums.org/showpost.php?p=9547955&postcount=53](http://ubuntuforums.org/showpost.php?p=9547955&postcount=53)

---

### Post by ghinix on 2010-07-26
This is the process I've attempted for Dell Vostro 1400 Ubuntu 10.04. Broadcom BCM4312 rev 01.. [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43 - No Internet access]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43 - No Internet access")

Unfortunately no success, yet!

Ethernet and internet is available**(would be great to make this work too)** but is not being detected, therefore I'm unable to make all the updates necessary directly via internet access, so I'm using a LIVE USB to download and transfer what's needed and using the No Internet access process above.

p.s. I'm a complete Ubuntu UBER NOOB.
thanks in advance.

---

### Post by ghinix on 2010-07-26
ok, Wonderful! I was able to manually configure Ethernet and update ubuntu 10.04 broadcom bcm4312 drivers using System > Administration > Hardware Drivers.
Success!
Thanks so much!!! :)

p.s. is one of the greatest feeling to not have to see microsoft or mac logos LAWL :P

---

### Post by solaralchemy on 2010-07-31
Man this wireless issue has caused me to triple partition my hard drive. I am running mint 7. I tried mint 9 in live mode and encountered the broadcom sta driver fuss. So I thought if installed it on a partition and tried it out the problem would be solved,,,
nope same issue. I let it go for a while and just kept to mint 7 on my other partition. Then I thought maybe Ubuntu 10:04 would not have the same problem so installed it on a third partition and lo and behold same bull@#$^! So I have mint 7 mint 9 and ubuntu 10 on my computer! Thankfully i had the foresight to not do a complete install and I am able to still get on to the internet with mint 7.
I am also glad to see some solutions offered in #39. I do not have any access to wired internet right now and that was one of the solutions offered on the mint forum. This all has been rather frustrating but i'm sure several people have been feeling this way.
cheers

---

### Post by ikoosh on 2010-08-11
wow, awesome! this saved my wireless on a Macbook Pro 5,1 after upgrading from 9.10 to 10.4 didn't help. :KS

---

### Post by cg0191 on 2010-08-14
> **Sepero said:**
> SOLUTIONS
SOLUTIONS
SOLUTIONS


There are many solutions offered in this thread. Here are the current proposed solutions and what they entail.



**THEY ARE ORDERED FROM LEAST DIFFICULT (TOP) TO MOST DIFFICULT (BOTTOM).**
Requires wired connection to the internet
[http://ubuntuforums.org/showpost.php?p=9299115&postcount=27](http://ubuntuforums.org/showpost.php?p=9299115&postcount=27)

Requires wired connection to the internet
[http://ubuntuforums.org/showpost.php?p=8931286&postcount=9](http://ubuntuforums.org/showpost.php?p=8931286&postcount=9)

Requires only LiveCD
[http://ubuntuforums.org/showpost.php?p=9223467&postcount=21](http://ubuntuforums.org/showpost.php?p=9223467&postcount=21)

Requires only LiveCD (downgrades kernel and prevents kernel upgrading)
[http://ubuntuforums.org/showpost.php?p=9467697&postcount=39](http://ubuntuforums.org/showpost.php?p=9467697&postcount=39)

Requires reinstall and wired connection to the internet
[http://ubuntuforums.org/showpost.php?p=9280854&postcount=25](http://ubuntuforums.org/showpost.php?p=9280854&postcount=25)

Requires software compiling and wired connection to the internet
[http://ubuntuforums.org/showpost.php?p=8727145&postcount=1](http://ubuntuforums.org/showpost.php?p=8727145&postcount=1)



SOLUTIONS
SOLUTIONS
SOLUTIONS

What **IS** the defect we are fixing??
Yes, I know we attempting to activate a broadcom WiFi but what is the actual problem we are fixing??????????????

---

### Post by Sepero on 2010-08-16
> **cg0191 said:**
> What **IS** the defect we are fixing??
Yes, I know we attempting to activate a broadcom WiFi but what is the actual problem we are fixing??????????????

The solution I posted is #39 at this location:
[http://ubuntuforums.org/showpost.php?p=9467697&postcount=39](http://ubuntuforums.org/showpost.php?p=9467697&postcount=39)

I repaired this for a friend. His issue was that his wireless driver worked after install from LiveCD, but broke when he upgraded the kernel.

---

### Post by earthpigg on 2010-08-17
> **cg0191 said:**
> What **IS** the defect we are fixing??
Yes, I know we attempting to activate a broadcom WiFi but what is the actual problem we are fixing??????????????

for my dell mini 9, the problem we are fixing is that software ***already included*** in the 10.04 install cd/usb works perfectly with the dell mini 9's wireless, but ubuntu doesn't seem to know this.

so, i had to install the needed packages manually from the cd. process described in post 21. i cannot speak for other hardware, though.

---

### Post by earthpigg on 2010-08-21
[SIZE="5"]*Dell Mini 9/10v*[/SIZE] users who feel like they are going in circles:

I ignored my own advice, and instead of immediately following my own [post 21]("http://ubuntuforums.org/showpost.php?p=9223467&postcount=21") in this very thread, i played with some other packages.

after doing that, my own directions that worked perfectly before where now failing me.

it turns out, ***i had to undo the other stuff*** before applying my own fix.

detailed directions from [here]("http://ubuntuforums.org/showpost.php?p=8510764&postcount=12"):

> Here: I'll give you the complete steps to make the Broadcom STA driver work.

1. sudo rmmod b43 ssb wl

2. sudo apt-get --purge remove linux-backports-modules-karmic b43-fwcutter bcmwl-kernel-source

3. Open all the files in /etc/modprobe.d/ and make sure that all of these lines AREN'T there:
blacklist ssb
blacklist b43
blacklist wl

4. Open /etc/modules and make sure that these aren't there:
b43
ssb
wl

5. Open /etc/modprobe.d/aliases.conf (if it exists) and make sure "alias wlan0 b43" isn't there.

6. Now remove or rename the b43 folder and the b43-legacy folder (if they exist) in /lib/firmware.

7. Reboot your computer.

8. Install the Broadcom STA driver using Jockey or install the package "bcmwl-kernel-source"

9. Reboot your computer.

---

### Post by ChicagosPugh on 2010-08-21
this is probably an easy one but I'm having trouble because I'm a noob 

the live CD prompts to activate the broadcom driver and it works fine

however, I only have a wireless connection available and when I boot from the hard drive, the installed system doesn't have it so I downloaded the hybrid-portsrc-x86_32-v5.60.48.36.tar.gz

how do I install that?

thanks!

---

### Post by gfd_2 on 2010-08-22
> **owhno said:**
> Problem using Broadcom Wireless in Ubuntu 9.10/10.04 because it is not supported by b43 driver ?

Assuming you have tried all normal installation procedures like using the Hardware Drivers tool and you still do not have a working WiFi setup this is what you must do:

   1. Download the Broadcom drivers: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
   2. Unpack and modify the ‘src/wl/sys/wl_linux.c‘:
      Line 35 (after #include <linux/etherdevice.h>) add: 
[INDENT]#include < linux/sched.h >[/INDENT]
   3. Compile the code with: make
   4. Copy the new driver: sudo mv wl.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless
   5. Update dependencies: sudo depmod -a
   6. Modify the blacklist to include the ‘b43&#8242; and ’ssb’ drivers /etc/modprobe.d/blacklist.conf (Add below the bcm43xx blacklist)

The part above you probably have seen a few times while googling for the answer. But there is a small problem, as you would have noticed, the ‘ssb‘ driver cannot be blacklisted. It is included in the initrd as I remember from the ubuntuforums. To solve this issue modify the /etc/rc.local to include before the exit(0):

```
rmmod ssb
modprobe wl
```

Now on startup the ssb gets removed and after that the new wl gets inserted. Adding wl to the /etc/modules will not help because the removing needs to be done first.
So with the /etc/rc.local modification everything happens in the correct order for perfect WiFi.

This was tested multiple times on a MacBook Pro with the Broadcom 4328 chipset and should work for all chipsets not supported by the b43 drivers.

**Update:**
Not all systems include the 'linux/sched.h' file. Install the 'linux-headers-generic' package if you get errors. The generic package is a meta package that should install the propper package for your kernel. If it isn't working install with
```
sudo apt-get install linux-headers-$(uname -r)
```

This worked GREAT! THANK YOU! 

 I have been trying to setup Linux, Ubuntu, Mandriva, Puppy and other distros for the last 3 years but there was no workable way to get my Broadcom card working... from ndiswrapper through all the various forms kludgey workarounds. 

I found Lucid Puppy (Puppy 5) had wireless support so I initially installed that, then tried Ubuntu 10.04 only to find my wireless not working. 

I was tempted to bail and return to Puppy but figured I'd give these instructions a shot... viola, wireless is up and running.  

The only thing I would add is that to edit the files mentioned I had to run “sudo gedit” so I would be able to open the file as Admin.  

Now for the Linksys wireless print server...

---

### Post by naren_aj on 2010-08-31
Try this out

[http://ubuntuforums.org/showthread.php?t=1480524](http://ubuntuforums.org/showthread.php?t=1480524)

---

### Post by dmlogs on 2010-09-06
Method in the first thread worked for me on the HP 1010NR

---

### Post by omghax on 2010-09-20
Thanks for this, helped me out on my HP Mini 1012NR when I accidentally changed linux-image's when messing around with pulseaudio and ALSA 1.0.23 >.<

Thought I'd post my keywords just in case someone else runs into the same problem I did and just needed a simple `sudo apt-get install linux-headers-$(uname -r)`

:D

---

### Post by snjib on 2010-09-26
I have HP mini 1030 NR and followed the instructions of thread 1.All procedure went on smoothly, but wirelss did not work still
The problem is that there is an old wl.ko file before you move the new one. 
I used some instruction as for reinstalling the driver  from [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)


"
If you were already running a previous version of wl, you'll want to provide a clean transition from the older driver. (The path to previous driver is usually /lib/modules/<kernel-version>/kernel/net/wireless)  # rmmod wl  # mv <path-to-prev-driver>/wl.ko <path-to-prev-driver>/wl.ko.orig # cp wl.ko <path-to-prev-driver>/wl.ko # depmod # modprobe wl  The new wl driver should now be operational and your all done."
It works perfectly well

---

### Post by kevinanchi on 2010-09-26
i have a laptop and i never faced the wireless problem but the connection i am using id not secure and it does not ask for password when i am connectiong it. Can anytell me how to configure the security setting.

---

### Post by Mearis on 2010-09-28
> **caffeinepill said:**
> Even this didn't work for me (Ubuntu 10.04 64 bit), although I see many people have had success with this method!. I was getting various errors when I attempted to install (and several attempts to re-install) the bcmwl-kernel-source package manually via synaptic.

Assuming you have attempted to install bcmwl-kernel-source and its dependencies manually, received errors during its install and synaptic is showing bcmwl-kernel-source as 'installed'... this may solve the problem.

[SIZE=1]Go into synaptic and[/SIZE][SIZE=2][SIZE=1]...

[/SIZE]**completely remove bcmwl-kernel-source** **AND dkms**[/SIZE]

*then**, whilst still in synaptic ***[B][SIZE=2]

install bcmwl-kernel-source[/SIZE][/B]


For me this did the trick, I'm not sure why. (removing dkms was the golden ticket). I then went back into Hardware Drivers and driver was showing as activated but not in use. All it took then was a quick reboot and :guitar:

Hope this helps someone!

Registered just to thank you for this - I just installed Ubuntu on a new dell machine, and this was the only thing that worked!

Thank you very much.:guitar:

---

### Post by jporozcor on 2010-10-05
I feel this is the post has the answer to my problem but I cant seem to understand it.... (what a new b) 

I have a dual boot compaq f572US, 

I installed UStudio 10.04 without internet connection and skipped the network setup step. Now Ubuntu won't recognize a physical connection and it seems like it doesn't have a driver for my wlan. (broadcom 802.11 b/g)

I tried using ndisgtkr, but I can't find anyplace (web) how to get the *.inf and *.bin driver, I only found *.sys which I can't use.(when you look for the driver in devicemanager in vista it takes you where the .sys file is but not the inf nor bin).

I finally found the broadcomm drivers that you show in this post, but I don't quite understand the guide. :( 

Following another post on how to install ndisgtk, I already blacklisted some using: 
-
echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist blacklist bcm43xx, blacklist b43, blacklist b43legacy blacklist ssb
-
I'm not sure what it did, but ndisgtk seems to work OK. (although I have no driver to use and test it with).

Please help...

When you say "unpak and modify", you mean using texteditor?
and "compile using make' you mean in the terminal? (steps 2 and 3)

---

### Post by Numantikon on 2010-10-06
Thank you so much, dnaand,... your solution was so simple that it saved my day after trying everything for more than 3 hours! You rock! :guitar:

---

### Post by dzajic on 2010-10-10
> **caffeinepill said:**
> Even this didn't work for me (Ubuntu 10.04 64 bit), although I see many people have had success with this method!. I was getting various errors when I attempted to install (and several attempts to re-install) the bcmwl-kernel-source package manually via synaptic.

Assuming you have attempted to install bcmwl-kernel-source and its dependencies manually, received errors during its install and synaptic is showing bcmwl-kernel-source as 'installed'... this may solve the problem.

[SIZE=1]Go into synaptic and[/SIZE][SIZE=2][SIZE=1]...

[/SIZE]**completely remove bcmwl-kernel-source** **AND dkms**[/SIZE]

*then**, whilst still in synaptic ***[B][SIZE=2]

install bcmwl-kernel-source[/SIZE][/B]


For me this did the trick, I'm not sure why. (removing dkms was the golden ticket). I then went back into Hardware Drivers and driver was showing as activated but not in use. All it took then was a quick reboot and :guitar:

Hope this helps someone!

WOW!!! This worked for me. THANK YOU. (Dell Studio 1558, Ubuntu 10.10)

---

### Post by binarylife on 2010-10-11
> **caffeinepill said:**
> Even this didn't work for me (Ubuntu 10.04 64 bit), although I see many people have had success with this method!. I was getting various errors when I attempted to install (and several attempts to re-install) the bcmwl-kernel-source package manually via synaptic.

Assuming you have attempted to install bcmwl-kernel-source and its dependencies manually, received errors during its install and synaptic is showing bcmwl-kernel-source as 'installed'... this may solve the problem.

[SIZE=1]Go into synaptic and[/SIZE][SIZE=2][SIZE=1]...

[/SIZE]**completely remove bcmwl-kernel-source** **AND dkms**[/SIZE]

*then**, whilst still in synaptic ***[B][SIZE=2]

install bcmwl-kernel-source[/SIZE][/B]


For me this did the trick, I'm not sure why. (removing dkms was the golden ticket). I then went back into Hardware Drivers and driver was showing as activated but not in use. All it took then was a quick reboot and :guitar:

Hope this helps someone!
wow amazing !! .. It really works !! Thanks alot man !!!

---

### Post by chochies on 2010-10-15
> **owhno said:**
> Problem using Broadcom Wireless in Ubuntu 9.10/10.04 because it is not supported by b43 driver ?

Assuming you have tried all normal installation procedures like using the Hardware Drivers tool and you still do not have a working WiFi setup this is what you must do:

   1. Download the Broadcom drivers: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
   2. Unpack and modify the ‘src/wl/sys/wl_linux.c‘:
      Line 35 (after #include <linux/etherdevice.h>) add: [INDENT]#include < linux/sched.h >[/INDENT]   3. Compile the code with: make
   4. Copy the new driver: sudo mv wl.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless
   5. Update dependencies: sudo depmod -a
   6. Modify the blacklist to include the ‘b43&#8242; and ’ssb’ drivers /etc/modprobe.d/blacklist.conf (Add below the bcm43xx blacklist)

The part above you probably have seen a few times while googling for the answer. But there is a small problem, as you would have noticed, the ‘ssb‘ driver cannot be blacklisted. It is included in the initrd as I remember from the ubuntuforums. To solve this issue modify the /etc/rc.local to include before the exit(0):

```
rmmod ssb
modprobe wl
```Now on startup the ssb gets removed and after that the new wl gets inserted. Adding wl to the /etc/modules will not help because the removing needs to be done first.
So with the /etc/rc.local modification everything happens in the correct order for perfect WiFi.

This was tested multiple times on a MacBook Pro with the Broadcom 4328 chipset and should work for all chipsets not supported by the b43 drivers.

**Update:**
Not all systems include the 'linux/sched.h' file. Install the 'linux-headers-generic' package if you get errors. The generic package is a meta package that should install the propper package for your kernel. If it isn't working install with
```
sudo apt-get install linux-headers-$(uname -r)
```

Can someone please explain steps 3 through 6, I do not know how to compile code with make. I'm completely new to Linux. I installed Ubuntu 10.04 on my HP Pavillion DV9410US after having replaced a virus infected hard drive mostly because I am a broke college student & Ubuntu is free. 

Thanks,
El Choch

---

### Post by xubuntu84 on 2010-10-20
> **Marite said:**
> Guys - i did it!!
This crappy STA error was bugging me  for 3 days.
As i am so green in this technical thing, first in my life i had to go  through a million of treads regarding this missing wireless thing and i  had no solution for my case.
1 - i did saw an inactive STA in System/Administration/Hardware  drivers but i couldn't activate it
2- i checked Synaptic package manager and there wasn't this  bcmwl-kernel-source, but there at least was bcmwl-modaliases
3 - i reinstalled the last one bcmwl-modaliases
4 - rebooted computer
5 - in Hardware drivers appeared B43 as already active, but wireless  wasn't working anyways
6 - though i removed B43
7 - rebooted again
8 - tried to activate STA and got message "/var/log/jockey.log"
9 - tried again and got message "Sorry, the Jockey backend crashed"
how da heck could i know, that i have to go to Synaptic manager /   Settings / Repositories / and mark a tickbox in Ubuntu softwear  "Proprietary drivers for devices (restricted) !!!??? This small step  solved all my problems
10 - bcmwl-kernel-source appeared in synaptic
11 - i acivated all of it, rebooted
12....and vuala!! Wireless was there!!

This worked perfectly while making a clean install of Ubuntu 10.10 (Maverick Meerkat) on a MacBook Unibody (5,1).  Thanks for your post.  I kept getting the "/var/log/jockey.log" error while trying to activate the B43 driver under System > Administration > Additional Drivers.  After going to package manager and removing all b43 / bcm references, I rebooted, then re-checked bcmwl-modaliases and bcmwl-kernel-source, rebooted, and now it was activated, with wireless and WPA working flawlessly.  Thanks again.

---

### Post by jamie_fixit on 2010-10-22
Hey,

I suspect that this is the answer to my problems but I'm a bit of a novice and linux command lines. So... I wondered if there was a version of the fix for simpletons? Just for reference when I try and use the additonal drivers option to install the broadcom driveres I get a fail and this in the jockey log:

My log file reports:

2010-10-22 20:37:49,316 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f98fec>
2010-10-22 20:37:49,317 DEBUG: reading modalias file /lib/modules/2.6.35-22-generic/modules.alias
2010-10-22 20:37:49,586 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-10-22 20:37:49,599 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-10-22 20:37:49,716 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-10-22 20:37:49,720 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-10-22 20:37:49,728 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-10-22 20:37:49,732 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-10-22 20:37:49,740 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-10-22 20:37:50,400 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-10-22 20:37:50,514 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-10-22 20:37:50,515 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-10-22 20:37:50,563 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-10-22 20:37:50,564 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-10-22 20:37:50,564 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-10-22 20:37:50,646 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

Any suggestions humbly cherished.

Cheers, Jamie.

---

### Post by atulkakrana on 2010-10-23
> **benmctee said:**
> This worked perfectly while making a clean install of Ubuntu 10.10 (Maverick Meerkat) on a MacBook Unibody (5,1).  Thanks for your post.  I kept getting the "/var/log/jockey.log" error while trying to activate the B43 driver under System > Administration > Additional Drivers.  After going to package manager and removing all b43 / bcm references, I rebooted, then re-checked bcmwl-modaliases and bcmwl-kernel-source, rebooted, and now it was activated, with wireless and WPA working flawlessly.  Thanks again.

Dont work that hard

1. Remove bcmwl-kernel-source and bcmwl-modalieses using synaptic
2. Go to system > Administration > additional drivers and activate broadcom drivers
3. Enjoy and sleep

Atul Kakrana

---

### Post by joanna_ford on 2010-11-04
I'm having problems with my wireless adaptor too :(

Absolute beginner when it comes to Ubuntu so trying to figure out the solution - I tried the most recently posted (and simplest!) one and found that  bcmwl-kernel-source wasn't installed but bcmwl-modalieses was.  I marked for removal but when I clicked on 'apply' got the following message:

> W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc-dev-bin_2.11.1-0ubuntu7.2_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc-dev-bin_2.11.1-0ubuntu7.2_i386.deb)
  404  Not Found


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.32-25.44_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.32-25.44_i386.deb)
  404  Not Found


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-dev_2.11.1-0ubuntu7.2_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-dev_2.11.1-0ubuntu7.2_i386.deb)
  404  Not Found
Please can someone help?!

Thanks :)

Jo

---

### Post by sricharanch on 2011-01-09
Hi!!!! 
I am using Dell inspiron N5010 lap with core i3 processor..

I am not able to use Wi-Fi in Ubuntu 10.04. How to configure wireless driver? Actually when i am using Ubuntu through CD i am able to connect to net.

Please provide me with a better solution..

---

### Post by degarb on 2011-01-09
There needs to be some assumptions to include the largest demographic interested in this topic: The Linux testers on a machine with NO Internet, no cat5 pcmcia/pci/cables.  1. Any solution should include installing without cat5--strickly off cd or usb jump. 2. Since this is 101, assume the user knows NOTHING about linux--no permissions, passwords, what the "heck is snaptic and bash" dumb. 

Most dabblers and testers are clueless of permissions, typo prone, and how to tweak bash to fit their specs.  So, in a sentence, we might point to the 5-minute, fool-proof avenue for newbies: find Snaptic, goto options to allow installing from cd (looking first on cd and usb should be default behavior) , install windows wireless driver (ndis do-hicky, then install the gui.  Then take, 30 seconds to install the drivers off the windows CD.   

Up and running in 5 to 15 minutes--without any page of instructions. But first, you must this tool exists and how to get off cd without internet: [http://lxer.com/module/newswire/view/46385/](http://lxer.com/module/newswire/view/46385/)

---

### Post by jporozcor on 2011-01-10
I actually had to reinstall the system, after just plug a physical Ethernet  connection, then go to administration drivers and activate your driver (It should show up here). That did it for me. :) good luck.

---

### Post by bookcrazy on 2011-01-22
Lots of information in this thread so far and I really appreciate it. 
 
One question I have is where do I find my driver details in Windows? I'm dual booting so I can mount my windows partition and then move it to my home folder no problem but I can't find the .inf or .sys files. How do I locate them on my windows hard drive?

---

### Post by degarb on 2011-01-22
> **bookcrazy said:**
> Lots of information in this thread so far and I really appreciate it. 
 
One question I have is where do I find my driver details in Windows? I'm dual booting so I can mount my windows partition and then move it to my home folder no problem but I can't find the .inf or .sys files. How do I locate them on my windows hard drive?

If like me, these threads with endless command line solutions are a foreign tongue, make you spend hours trying, and seldom work. (I spent 2 days as a windows user last year trying these linux solutions.)   Then, you are talking going the winwirelessdriver way, I just got mine from the install disk that came with the card (manufactures site, you could try the system32 dir).  The hardest part was installing the gui version of this in Ubuntu.   

Another option, is install pinguyos.com or ultimate edition, since they recompiled the kernel to make the wireless cards work out of the box. They are a dressed up version of Ubuntu, without the crippling mindset of restricting things to Open-source.

---

### Post by windeguy on 2011-02-08
> **Sepero said:**
> I solved this problem for a friend in a slighty different way. I hope this helps.


1. Add the LiveCD as a repository and Uncheck ALL other repositories.
System> Administration> Software Sources

2. Update software sources. This can be done when you close the Software Sources window, or by using Synaptic.
System> Administration> Synaptic Package Manager> Reload (button)

3. Use Synaptic to Remove bad packages if they are installed.
System> Administration> Synaptic Package Manager> Search (button)
* bcmwl-kernel-source
* b43-fwcutter
* linux-image-2.6.32-22-generic (any linux-image 2.6.32-22 or greater)

4. Use Synaptic to Lock the kernel package linux-image-2.6.32-21-generic, and lock the package linux-headers-generic to version 2.6.32-21.32. (This will prevent the problem from occurring again with future upgrades).
System> Administration> Synaptic Package Manager> Package (menu)> Lock Version

5. Reboot (restart)

6. Install the wifi driver.
System> Administration> Hardware Drivers

7. Reboot (restart)

8. Remove the LiveCD as a repository, and Recheck all the repositories that were unchecked in step #1.
System> Administration> Software Sources

After trying without any luck to establish a WIFI connection on my ACER 9410Z laptop with Ubuntu Studio 10.04, I thought this might finally get me going.  However, when I try to "Add CD-ROM" as the only software source to get the working driver from the LIVE install CD,  I get the response "Error Scanning the CD".  The MD5SUM of the file was verified, the CD was burned and verified, the CD boots up in Live mode in another computer and is recognized as part of the files system in the very same  Linux laptop I am trying in which I am trying to get WIFI working!! DUH?

Any suggestions?

---

### Post by HouTex on 2011-02-22
After upgrading to 10.4 from 9.10 my wireless died--it had been working well on at least one of my wireless access points prior to the upgrade.  I went to Synaptic manager / Settings / Repositories / and unchecked a tickbox in Ubuntu softwear "Proprietary drivers for devices (restricted).  The wireless then connected with my WAP.  I'm hoping it works after a restart.

[edit]  Yes, it does work after restart.  The forum was helpful in eliminating many of the usual problems.  I made sure my card was active and that the STA driver was running.  I then found the Synaptic manager/settings/repositories fix and it worked for me.  Thanks for posting that fix.

---

### Post by metafunction on 2011-03-04
Quick question.   Where do I unpack the Broadcom driver files to?

---

### Post by metafunction on 2011-03-04
> **metafunction said:**
> Quick question.   Where do I unpack the Broadcom driver files to?

my bad, I'm new and was getting my relatives and absolutes mixed up!

---

### Post by atx on 2011-03-15
Thank you for the post! Works perfect on my MacBook!

---

### Post by kaushikkarra on 2011-05-04
Hi i am using the new version of ubuntu and when i try to install the additional drivers the Broadcom wireless sta driver it says the the same ..

Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

Can some one help me out with this issue ..

---

### Post by MyD0j0 on 2011-05-05
Sorry.  In the OP, I'm on step 'make'.

As a noob, I must ask 'make what'?

---

### Post by MyD0j0 on 2011-05-06
> **MyD0j0 said:**
> Sorry.  In the OP, I'm on step 'make'.

As a noob, I must ask 'make what'?


Ok...I didn't read enough...

But now I get an error that no one seems to have run into before, similar to others.  This is on an hp pavillion dv9000 and the broadcom driver shows active in 'additional drivers' and wireless looks dead.

```

KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  LD      /home/eric/Downloads/built-in.o
  CC [M]  /home/eric/Downloads/src/wl/sys/wl_linux.o
/home/eric/Downloads/src/wl/sys/wl_linux.c: In function ‘wl_attach’:
/home/eric/Downloads/src/wl/sys/wl_linux.c:486:3: error: implicit declaration of function ‘init_MUTEX’
make[2]: *** [/home/eric/Downloads/src/wl/sys/wl_linux.o] Error 1
make[1]: *** [_module_/home/eric/Downloads] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [all] Error 2

```

I found this [reference]("http://aur.archlinux.org/packages.php?ID=39405") to the same on the web, but don't understand what I'm supposed to do since it appears that is a different flavor of linux and there wasn't much explanation.

Thanks.

---

### Post by okplyr on 2011-05-29
on install, i got the additional h/w drivers with broadcom sta but got
the error when trying to activate.    
on macbook 3.1 with latest ubuntu.

[http://www.linuxquestions.org/questions/blog/frandalla-68463/patching-802-11-linux-sta-driver-for-kernel-2-6-37-3558/](http://www.linuxquestions.org/questions/blog/frandalla-68463/patching-802-11-linux-sta-driver-for-kernel-2-6-37-3558/)

+ the info in this thread helped me get it working.

thanks!

---

### Post by zander1013 on 2011-06-20
hi,

here is how one turns off those errors regarding "implicit declaration of function 'init_MUTEX'"...
[http://www.linuxquestions.org/questions/blog/frandalla-68463/patching-802-11-linux-sta-driver-for-kernel-2-6-37-3558/](http://www.linuxquestions.org/questions/blog/frandalla-68463/patching-802-11-linux-sta-driver-for-kernel-2-6-37-3558/)

btw. the sta driver was working perfectly for me until a user upgraded from 10.10 to 11.04. then the wireless stopped working.

i followed the instructions here and used the patch on the link to turn off the the compile errors but my wireless is still not working.

can anyone advise?


thank you.

---

### Post by zander1013 on 2011-06-20
> **MyD0j0 said:**
> Sorry.  In the OP, I'm on step 'make'.

As a noob, I must ask 'make what'?


just type 'make' in the directory that was created when you unpacked the .gz file. this command runs the Makefile that was created there when you unpacked said .gz file.

---

### Post by eotakos on 2013-04-29
Great thread.

It worked for me, by just following blindly all instructions of the first entry.

computer :  Dell latitude e6430n (2013)
OS         : ubuntu 10.04 64bit

many thanks

---

### Post by oldos2er on 2013-04-29
Old thread closed.

---

