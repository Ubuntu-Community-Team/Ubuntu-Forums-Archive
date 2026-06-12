---
title: "Ndis Installation Corrupting File System?"
date: 2005-06-17
forum: Installation &amp; Upgrades
---

### Post by Noggin on 2005-06-17
I'm not sure I should put this here as I think this forum is intended for OS installation, but this is very soon after I installed the OS so here it goes....

Hardware:
Compaq presario 1245 laptop
333 MHz AMD K6-2
96 MB Ram
PCMCIA Linksys EtherFast 10/100 wired ethernet card, used to do a network install
PCMCIA Netgear WG511 Chinese v3, does not work with Prism54, requires NDIS wrapper

I'm a linux newb, and I just finished installing Ubuntu for the second time.  The first time was a few weeks ago.  That same night I got it installed, I also installed several applications most notably being a lower memory intensive desktop (XFCE or something like that, memory isn't good there), Eagle cad program, and ndiswrapper.  After installing all of this I rebooted the machine to ensure that prism54 was blacklisted and that my wireless card would operate properly.  Immediately following POST I got a Grub error 17.  As far as I can tell Grub does not recognize the partition table or file system.  I have not been able to recover from this error.

I reinstalled Win98 two days later after giving up.  Last night I installed Ubuntu again.  After installing Ubuntu, I immediately set up my ndiswrapper again.  After ensuring that it was working, I rebooted.  This time I got a PAM failure and could not log in as root (which came as no suprise) or using my usual user name.  I rebooted again, and I get Grub 17.  

I don't know what to do.  I'm a Linux newb and this is now the 6th failed linux install overall... Slackware, Mandrake 9, Mandrake 10, Debian, and Ubuntu twice.  

From memory, this is what I did:
* I used the package manager to install NDIS after selecting universe repositories.
* ndiswrapper -i windows_driver_for_wg511
* Blacklisted prism54
* Put ndiswrapper in a module list under the /etc/ directory, don't recall file name
* set up essid and encryption key

And then I rebooted.  This is insane....  Before installing the ndiswrapper, I rebooted at least 6 times with no error.

---

### Post by Noggin on 2005-06-18
Well this is what I'm doing right now.   Using Lilo bootloader

- Just finished network reinstall of Ubuntu
Reboot successful

- Used synaptic packet manager to install ndis-utilities (did not change repositories)
Reboot successful

-  Added prism54 to /etc/hotplug/blacklist
Reboot successful 

- sudo ndiswrapper -i netwg511.inf
- sudo ndiswrapper -m
- sudo modprobe ndiswrapper
Reboot successful

- sudo iwconfig wlan0 essid <networkname>
- sudo iwconfig wlan0 key <encryption key>
- sudo dhclient
Reboot successful

I don't think its a coincidence that Grub failed both times I installed the ndiswrapper utilities the first two times I installed linux.  Lilo is working, for now, so I'll stick with it.  Thanks for taking the time to look at this post.

---

### Post by kalel on 2006-01-13
I' use the same machine but i have 160mb ram, :)

---

