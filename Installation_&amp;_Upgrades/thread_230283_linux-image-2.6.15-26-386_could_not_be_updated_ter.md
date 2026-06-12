---
title: "linux-image-2.6.15-26-386 could not be updated: terminal message from Synaptic"
date: 2006-08-05
forum: Installation &amp; Upgrades
---

### Post by john_d_mchenry on 2006-08-05
[I posted a previous thread Aug 4 with limited diagnostics. This is 
 a more complete version.]

All hell broke loose when I tried to update the kernel to linux-image-2.6.15-26-386  
following Synaptic's software-update prompt.

The terminal error was as follows:

	Setting up linux-image-2.6.15-26-386 (2.6.15-26.46) ...
	There was a problem running depmod.  This may be benign,
	(You may have versioned symbol names, for instance).
	Or this could be an error.
		depmod exited with return value 0
		depmod got a signal 11
	Since this image uses initrd, I am not deleting the file
	/lib/modules/2.6.15-26-386/modules.dep. However, there is no
	guarantee that the file is valid. I would strongly advice
	you to either abort and fix the errors in depmod, or
	regenerate the initrd image with a known good modules.dep
	file. I repeat, an initrd kernel image with a bad modules.dep
	shall fail to boot.
	Would you like to abort now? [No] Yes
	dpkg: error processing linux-image-2.6.15-26-386 (--configure):
	 subprocess post-installation script returned error exit status 1
	Errors were encountered while processing:
	 linux-image-2.6.15-26-386
	E: Sub-process /usr/bin/dpkg returned an error code (1)

Now I can't get 
	apt-get update 
to work, nor 
	apt-get install foo 
nor can I get Synaptic to install anything new: The above error message just recurs.

A modules.dep file was, however, placed in /lib/modules/2.6.15-26-386, and the kernel
has been updated (/boot/grub/menu.lst reflects the change):

	root@ubuntu:~# l /lib/modules/2.6.15-26-386/modules.dep
	-rw-r--r-- 1 root root 312039 Aug  3 01:09 /lib/modules/2.6.15-26-386/modules.dep

	root@ubuntu:/tmp# uname -r
	2.6.15-26-386 

The problem does seem to be with depmod.

The previous kernel was 2.6.15-23-386 and depmod works just fine, e.g.:

	root@ubuntu:/tmp# depmod -n -v 2.6.15-23-386 | head -10
	/lib/modules/2.6.15-23-386/madwifi-ng/new_wlan_xauth.ko needs "new_ieee80211_authenticator_register": /lib/modules/2.6.15-23-386/madwifi-ng/new_wlan.ko
	/lib/modules/2.6.15-23-386/madwifi-ng/new_wlan_xauth.ko needs "new_ieee80211_authenticator_unregister": /lib/modules/2.6.15-23-386/madwifi-ng/new_wlan.ko
	/lib/modules/2.6.15-23-386/madwifi-ng/new_wlan_wep.ko needs "new_ieee80211_crypto_register": /lib/modules/2.6.15-23-386/madwifi-ng/new_wlan.ko
	/lib/modules/2.6.15-23-386/madwifi-ng/new_wlan_wep.ko needs "new_ieee80211_crypto_unregister": /lib/modules/2.6.15-23-386/madwifi-ng/new_wlan.ko
	/lib/modules/2.6.15-23-386/madwifi-ng/new_wlan_wep.ko needs "new_ieee80211_note_mac": /lib/modules/2.6.15-23-386/madwifi-ng/new_wlan.ko
	/lib/modules/2.6.15-23-386/madwifi-ng/new_wlan_tkip.ko needs "ether_sprintf": /lib/modules/2.6.15-23-386/madwifi/wlan.ko
	/lib/modules/2.6.15-23-386/madwifi-ng/new_wlan_tkip.ko needs "new_ieee80211_note": /lib/modules/2.6.15-23-386/madwifi-ng/new_wlan.ko
	/lib/modules/2.6.15-23-386/madwifi-ng/new_wlan_tkip.ko needs "new_ieee80211_notify_michael_failure": /lib/modules/2.6.15-23-386/madwifi-ng/new_wlan.ko
	/lib/modules/2.6.15-23-386/madwifi-ng/new_wlan_tkip.ko needs "new_ieee80211_crypto_register": /lib/modules/2.6.15-23-386/madwifi-ng/new_wlan.ko
	/lib/modules/2.6.15-23-386/madwifi-ng/new_wlan_tkip.ko needs "new_ieee80211_notify_replay_failure": /lib/modules/2.6.15-23-386/madwifi-ng/new_wlan.ko

but depmod fails for the current version of the kernel 
	root@ubuntu:/tmp# uname -r
	2.6.15-26-386 

	root@ubuntu:/tmp# depmod -n -v 2.6.15-26-386
	Segmentation fault

It looks like apt-get and Synaptic use depmod while performing updates,
but depmod fails on 2.6.15-26-386, and so the update bombs.

Does anyone know what is wrong with depmod and 2.6.15-26-386?

Thanks,

Jack.

---

### Post by john_d_mchenry on 2006-08-05
By the way, when I boot into the previous kernel:

root@ubuntu:~# uname -r
2.6.15-23-386

and run 

apt-get install foo

I get the same error message:


root@ubuntu:~# apt-get install texinfo
Reading package lists... Done
Building dependency tree... Done
texinfo is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up linux-image-2.6.15-26-386 (2.6.15-26.46) ...
There was a problem running depmod.  This may be benign,
(You may have versioned symbol names, for instance).
Or this could be an error.
        depmod exited with return value 0
        depmod got a signal 11
Since this image uses initrd, I am not deleting the file
/lib/modules/2.6.15-26-386/modules.dep. However, there is no
guarantee that the file is valid. I would strongly advice
you to either abort and fix the errors in depmod, or
regenerate the initrd image with a known good modules.dep
file. I repeat, an initrd kernel image with a bad modules.dep
shall fail to boot.
Would you like to abort now? [No] Yes
dpkg: error processing linux-image-2.6.15-26-386 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.15-26-386
E: Sub-process /usr/bin/dpkg returned an error code (1)


How come apt-get still thinks that it needs to update the kernel to
2.6.15-26-386 when I booted into the previous version, 2.6.15-23-386?  
Can I clobber some file somewhere that's telling it to install linux-image-2.6.15-26-386?

Thanks, 

Jack.

---

### Post by wbmj on 2006-08-05
There are two things you can try that I find very helpful.

1. sudo dpkg -configure -a  (This will try tofix the install problem)
2. sudo apt-get clean (This should remove the kernel deb file from the aptcache so the next time you use apt it won't show an error)

If these don't do the trick, you can also do sudo dpkg -P linux-image-2.6.15-26-386

Remember though that the last command will purge the image and any associated configuration files

---

### Post by john_d_mchenry on 2006-08-05
HI wbmj,

Thanks for your reply.

The APT HOWTO suggests something similar to what you're suggesting:

	apt-get -f install  

followed by

	dpkg --configure -a

...neither of which worked.

I ended up doing:

	root@ubuntu:/tmp# strace apt-get -f install  >& /tmp/apt-get.txt

to find out what apt-get was doing. This led me to 
/var/lib/dpkg (which, I think, apt-get relies on anyway)
I changed two lines in /var/lib/dpkg/status (I saved it first to /var/lib/dpkg/status%):

	root@ubuntu:/var/lib/dpkg# diff status status%
		17405c17405
		< Status: install ok installed
		---
		> Status: install ok half-configured
		17412a17413
		> Config-Version: 2.6.15-26.45

and then:

	root@ubuntu:/var/lib/dpkg# apt-get -f install
	Reading package lists... Done
	Building dependency tree... Done
	0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

	root@ubuntu:/var/lib/dpkg# dpkg --configure -a

which I think means that everything is back to normal :-o ?
For example, apt-get update works just fine (I booted into the older 
kernel version 2.6.15-23)

Any ideas on why all of this happened? Is there really a problem with 
depmod? I'm reluctant to try to install linux-image-2.6.15-26 again in 
case another nightmare ensues.

Thanks,

Jack.

---

