---
title: "Broken 12&gt;14 upgrade"
date: 2014-09-10
forum: Installation &amp; Upgrades
---

### Post by welefort on 2014-09-10
I run 12.04 server edition under Virtualbox.  It hosts a tiny service I use for hosting some site.  I decided to run the upgrade to 14  and just did the simple 

sudo do-release-upgrade.

Everything look ok.. No errors that I saw,  but after the reboot I get the (initramfs) prompt.

During the boot up,  I have the option to select recovery mode.  That works,  but a normal boot doesn't.

---

### Post by ian-weisser on 2014-09-10
Any errors in /var/log/syslog?

---

### Post by oldfred on 2014-09-10
Did you install any proprietary drivers? 
Particularly video drivers, those should be uninstalled before upgrade and reinstalled after. 

I also have this in my notes:

 "If the &#8220;apt-get upgrade&#8221; does not successfully complete then a flag is set and update-initramfs does not get to run, hence grub gets all messed up. You should be able to boot using the old kernel and then run the sudo update-initramfs &#8211;u -k command. Then run sudo dpkg &#8211;reconfigure. That should clear the upgrade flags and fix any broken packages."

---

### Post by welefort on 2014-09-10
No special drivers that Im aware of.  This was installed under  virtualbox as a VM..so it might have..but I dont know.  The syslog shows  no errors.  

But the boot.log does have one error

/scripts/local-top/cryptroot: line 1: can't open /dev/mapper/tinyboard--vg-root$root: no such file.

---

