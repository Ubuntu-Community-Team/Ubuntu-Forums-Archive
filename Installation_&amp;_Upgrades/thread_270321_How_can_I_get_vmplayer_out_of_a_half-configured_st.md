---
title: "How can I get vmplayer out of a half-configured state?"
date: 2006-10-03
forum: Installation &amp; Upgrades
---

### Post by funkiwan on 2006-10-03
A couple of weeks ago I ran into a problem installing vmplayer via adept on a new installation (Kubuntu 6.06 LTS Dapper Drake). Though vmplayer actually does now work, the install is listed as failing and attempts to complete the install every time I install any software via adept, or just dpkg --configure -a. How can I get adept to ignore what it construes as problems with vmware-player install. I've tried to uninstall and purge, but since the cleanup script fails I seem stuck in this loop.

Here's the details that I see:

-- BEGIN DETAILS --

Now configuring VMware Player. (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.9.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to
Use of uninitialized value in chomp at /usr/bin/vmware-config-network.pl line 929.
install already exists. Overwrite? [yes]
Use of uninitialized value in substitution (s///) at /usr/bin/vmware-config-network.pl line 903.
Use of uninitialized value in substitution (s///) at /usr/bin/vmware-config-network.pl line 903.
The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to
Use of uninitialized value in chomp at /usr/bin/vmware-config-network.pl line 929.
install already exists. Overwrite? [yes]
Use of uninitialized value in substitution (s///) at /usr/bin/vmware-config-network.pl line 903.
Use of uninitialized value in substitution (s///) at /usr/bin/vmware-config-network.pl line 903.
The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to
Use of uninitialized value in chomp at /usr/bin/vmware-config-network.pl line 929.
install already exists. Overwrite? [yes]
Use of uninitialized value in substitution (s///) at /usr/bin/vmware-config-network.pl line 903.
Use of uninitialized value in substitution (s///) at /usr/bin/vmware-config-network.pl line 903.
The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install
Use of uninitialized value in chomp at /usr/bin/vmware-config-network.pl line 929.
already exists. Overwrite? [yes]
Use of uninitialized value in substitution (s///) at /usr/bin/vmware-config-network.pl line 903.
Use of uninitialized value in substitution (s///) at /usr/bin/vmware-config-network.pl line 903.
Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.115.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to
Use of uninitialized value in chomp at /usr/bin/vmware-config-network.pl line 929.
install already exists. Overwrite? [yes]
Use of uninitialized value in substitution (s///) at /usr/bin/vmware-config-network.pl line 903.
Use of uninitialized value in substitution (s///) at /usr/bin/vmware-config-network.pl line 903.
The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to
Use of uninitialized value in chomp at /usr/bin/vmware-config-network.pl line 929.
install already exists. Overwrite? [yes]
Use of uninitialized value in substitution (s///) at /usr/bin/vmware-config-network.pl line 903.
Use of uninitialized value in substitution (s///) at /usr/bin/vmware-config-network.pl line 903.
The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to
Use of uninitialized value in chomp at /usr/bin/vmware-config-network.pl line 929.
install already exists. Overwrite? [yes]
Use of uninitialized value in substitution (s///) at /usr/bin/vmware-config-network.pl line 903.
Use of uninitialized value in substitution (s///) at /usr/bin/vmware-config-network.pl line 903.
Starting VMware services:
   Virtual machine monitor done
   Virtual ethernet done
   Bridged networking on /dev/vmnet0 failed
   Host-only networking on /dev/vmnet1 (background) done
   Host-only networking on /dev/vmnet8 (background) done
   NAT service on /dev/vmnet8 failed
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player

-- END DETAILS --

And here's the bug I added a comment on but got no response:
[Bug post]("https://launchpad.net/distros/ubuntu/+source/vmware-player/+bug/57957")

Any ideas on how to proceed? Is there a more appropriate forum I should post to?

Thanks.

---

