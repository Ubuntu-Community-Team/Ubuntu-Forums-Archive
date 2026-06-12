---
title: "dpkg error with vmplayer"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by ew_jim on 2006-10-29
Hi,
So, i have upgraded my ubuntu, and everything worked fine. after the reboot the only thing to update was the vmplayer. So i tried to updated it and my update manger froze. Therefore i rebooted my system and tried to uninstall my vmplayer but i can't. Then I reinstalled Automatix because i thought this would manage my problem. but it didn't.
So everytime i trie to update i  i got some error so i tried  dpkg --configure -a

and this is my output:
Richte vmware-player ein (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.144.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] yes

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] yes

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install 
already exists.  Overwrite? [yes] yes

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.18.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] yes

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] yes

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: Fehler beim Bearbeiten von vmware-player (--configure):
 Unterprozess post-installation script gab den Fehlerwert 1 zurück
Fehler traten auf beim Bearbeiten von:
 vmware-player

I can't uninstall vmplayer via apt-get everytime i trie i get the same error. and what is worst i can't do any update because my apt-get collaps.

thanks for help

mfg
peter

ps.:2.6.17-10-386 i686

---

