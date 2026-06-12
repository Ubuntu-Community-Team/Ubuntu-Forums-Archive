---
title: "Repair failed upgrade from 16.04 LTS to 18.04.1 LTS"
date: 2018-08-29
forum: Installation &amp; Upgrades
---

### Post by abergo on 2018-08-29
Hi all. My upgrade from 16 to 18.04.1 LTS failed. The install got broken off at the point where it asked me which file to keep for Configuration file '/etc/sysctl.conf'
After it dropped I tried re-upgrade but it was already far enough along that it now looks like the OS is installed. However I had to force restart, and now it the boot screen blinks, and the screen itself is black apart from me seeing the mouse pointer. 

I tried using a USB with 18.04 on it, but no option to repair shows. Only to install 18.04.1 alongside 18.04.1 

I do not want to lose my docs, configs and installs so repairs is the best thing for me if possible. I could install alongside then. 






Configuration file '/etc/sysctl.conf'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.

---

### Post by Bashing-om on 2018-08-29
abergo; Ouch -
Bad things can happen.

What can you boot in the install to ?
What results in attempting to boot a recovery console (advanced options) from grub's boot menu ?

else, well, see what can be done from that liveUSB; as we have to get a terminal - somehow.

[INDENT][INDENT]all we can do is try
[/INDENT][/INDENT]

---

### Post by abergo on 2018-08-30
Yup, I can get to Recovery menu fine. 
If I boot to liveUSB I get the option to install a new version of of the same but not repair it. In live USB it all seems fine. I am at a loss as this is beyond my skill level.

---

### Post by abergo on 2018-08-30
I've ran through most of the options in the recovery menu, except failsafex doesn't seem to work. 
When trying to boot normal, its as if it just doesn't pop-in right. I can see the little load screen first, then the screen goes black and I can see the mouse pointer only.

---

### Post by oldfred on 2018-08-30
UEFI or BIOS system? What video card/chip?
Did you uninstall any proprietary drivers like video or wireless before upgrade? They often cause issues.
Did you comment out any ppa's as they do not always have newer versions and then trying to load them crashes update.

If you can get to recovery mode terminal chroot not required for repairs.
If you have to use live installer, you normally have to chroot and run repairs.

Older chroot instructions do not show the required mount of the ESP - efi system partition that newer UEFI systems have. This one does:
[https://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](https://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)

Some of the repair commands, you may or may not need these or even additional ones.
If you did not uninstall proprietary drivers or comment out ppa, you should check that first.
If errors post command & error & if longer use code tags with # in Forum's advanced editor.

       #Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get autoremove
# fix Broken packages -f 
apt-get -f install
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
dpkg --configure -a 
   sudo update-initramfs -k all -c
sudo update-grub 
   # repair commands in recovery mode dpkg option
dpkg --configure -a
apt-get update
apt-get install -f
apt-get dist-upgrade 
  
  # reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop

---

### Post by abergo on 2018-08-30
Ok I got to terminal by the ctrl alt f1, and could log in from there. I also suspect the video card driver. Its a NVIDIA, and I've had a ton of crap with the proprietary driver. I think the drivers got uninstalled in the upgrade. 
Its UEFI as far as i know. I did not comment out any PPAs
I think the install failed at a ctrl -c instead of ctrl-shift c (don't get me started on the design of those two commands). 
I will try to run the commands you suggested.

---

### Post by abergo on 2018-08-30
Can see all folders fine, but no networking so far to the apt-get updates fails. Trying to figure out how to enable it.

---

### Post by abergo on 2018-08-30
Weirdly enough the WiFi card seems to work and it seems to connect while running iwconfig it first shows error: lo no wirless connection, then wl_dev_invar_get : error and wl_cfg80211_get_tx_power: error but the wlp6s0 shows it connected to the right ESSID?


....but it can't really download anything or ping anything. I'm not sure how to read this.

---

### Post by abergo on 2018-08-30
I can ping IP addresses but not domain names. 
I can tether via USB and its the same results so somewhere my DNS settings are fubared. 
I am reading that now the new DNS on 18.04 is located in /etc/netplan. Is that the same for desktop because the /etc/netplan does not exist on my install?

---

### Post by Bashing-om on 2018-08-30
abergo; Hey -

Let's backup and regroup to oldfred's post #5 and look at this as a graphic's driver issue.
At the login screen activate the F2 console ( ctl+alt+F2) and execute - on a wired internet connection:
- here the GUI graphic's driver is not a factor -
```

ping -c3 ubuntu.com

```
with a positive response ( 3 packets transmitted, 3 received, 0% packet loss )
execute the commands from post #5 so we know we have a clean base.
Advise if any errors ( post them ! ).

Once we are clean we look at the driver issue.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by abergo on 2018-08-30
Hi I do not have a NIC on the laptop. I can connect via USB tho, and the same results occur. No way to ping a web address, but fine pinging an IP address. I really appreciate the answers. I tried to find a way to set dns but it seems that Ubuntu 18 has changed the way to set DNS. 
When I try to do an nslookup it times out. 
I've tried restarting and resetting NetworkManager
Tried to set [COLOR=#242729][FONT=Consolas]dns=dnsmasq in NetworkManager.conf
Reset the resolv.conf symlink
[/FONT][/COLOR]systemctl status resolvconf does not give an error

sudo resolvconf -u does not give an error
On netstart -i I can see my adapter

I do not know if this is relevant for the 18.04.1 desktop version, but /etc/netplan does not exist.

---

### Post by Bashing-om on 2018-08-30
abergo; yukkie - on me -

As I too have no familiarity with the new networking arrangement.
However, my 18.04 desktop:
> 
sysop@x1804mini:~$ ls -al /etc/netplan
total 12
drwxr-xr-x   2 root root 4096 Apr  3 00:47 .
drwxr-xr-x 114 root root 4096 Aug 27 13:33 ..
-rw-r--r--   1 root root  104 Apr  3 00:47 01-network-manager-all.yaml
sysop@x1804mini:~$

If that directory does not exist on  your ( not a server install ) desktop system I am at a loss how to proceed.

[INDENT][INDENT]A know it all I am not
[/INDENT][/INDENT]

---

### Post by abergo on 2018-08-31
Just a follow-up. This can be closed. I am just updating in case someone else ends up in the same situation. 

I could not manually install netplan to continue my installation, which means my working network card simply could not find a DNS and therefore not find the web addresses. 

Instead, I reinstalled 18 on top of the old upgrade. So I spent most of the day backing up my stuff. While installing on top I chose to install on top of the old install without formatting the disks. So all my stuff in the /home folder was left alone (same username and password). Everything else was deleted. Tons of Git Projects in /var/www (my fault). I had to reinstall most programs manually, but in most cases the settings were left alone. Then I did all the clean up routines. It works now and I am pretty stoked about the upgrades.

Edit: Btw I used my phone USB connection to install a driver for the broadcom card.

---

### Post by oldos2er on 2018-08-31
> **abergo said:**
> Just a follow-up. This can be closed. 

If you meant to say "Solved," you can mark your own threads solved under the Thread Tools menu at the top of the page. Thank you!

---

