---
title: "Vmware-player in edgy broken?"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by decker on 2006-10-30
Hey, i just installed edgy on my laptop and my vmware-player is cr4ppin out on config. It won't let me remove it either, i originally installed it with automatix2

here's what i get when i run "sudo apt-get install ettercap"

*****************

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  acroread-escript mplayer-skins libggi2 libgii1 libgii1-target-x
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ettercap-common libnet1
The following NEW packages will be installed:
  ettercap ettercap-common libnet1
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 193kB/545kB of archives.
After unpacking 1765kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe ettercap 1:0.7.3-1.1ubuntu3 [193kB]
Fetched 80.3kB in 4s (16.6kB/s)  
Selecting previously deselected package libnet1.
(Reading database ... 139801 files and directories currently installed.)
Unpacking libnet1 (from .../libnet1_1.1.2.1-2_i386.deb) ...
Selecting previously deselected package ettercap-common.
Unpacking ettercap-common (from .../ettercap-common_1%3a0.7.3-1.1ubuntu3_i386.deb) ...
Selecting previously deselected package ettercap.
Unpacking ettercap (from .../ettercap_1%3a0.7.3-1.1ubuntu3_i386.deb) ...
Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.239.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install 
already exists.  Overwrite? [yes] 

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.x.x/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] 

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libnet1 (1.1.2.1-2) ...

Setting up ettercap-common (0.7.3-1.1ubuntu3) ...
Setting up ettercap (0.7.3-1.1ubuntu3) ...
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)


*******************************

ok, so I tried to yank it with " sudo apt-get remove vmware-player"

*************************

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  vmware-player acroread-escript mplayer-skins libggi2 libgii1
  libgii1-target-x
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  vmware-player
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 32.1MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 139916 files and directories currently installed.)
Removing vmware-player ...
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--remove):
 subprocess pre-removal script returned error exit status 1
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

***********

Any tips on fixing this or do i need to go yank it out by hand?

---

### Post by rodey on 2006-10-30
I installed VMWare Server in Dapper and then upgraded to Edgy. After that, my VMWare Server wouldn't start anymore. You have to recompile some stuff I guess that is kernal specific and when you upgraded, the kernal obviously changed.

[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

If you go to the bottom of the top post, it gives you the command to fix this. 

Good luck

---

### Post by theicyj on 2006-10-31
Have you figured out how to fix this yet?  I am having the same problem!  It is driving me nuts. I also used Automatix and am running Edgy.  I get this everytime I update/install/remove anything:

> Now configuring VMware Player. (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.239.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to
install already exists. Overwrite? [yes]

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to
install already exists. Overwrite? [yes]

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to
install already exists. Overwrite? [yes]

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install
already exists. Overwrite? [yes]

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.x.x/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to
install already exists. Overwrite? [yes]

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to
install already exists. Overwrite? [yes]

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to
install already exists. Overwrite? [yes]

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
Setting up libnet1 (1.1.2.1-2) ...

Setting up ettercap-common (0.7.3-1.1ubuntu3) ...
Setting up ettercap (0.7.3-1.1ubuntu3) ...
Errors were encountered while processing:
vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

followed by an error window containing 

> E: vmware-player: subprocess post-installation script returned error exit status 1

---

### Post by theicyj on 2006-11-01
I was able to fix the problem by downloading and reinstalling vmware manually, then uninstalling it using Synaptic.

---

### Post by bengineerd on 2006-11-01
I am having the exact same problem.
I tried reinstalling vmware player manually from the downloaded tar package, but it says:
> A previous installation of VMware software has been detected.

Failure

Execution aborted.


I tried the manual uninstall as well, but it ran and basically did nothing.

I swear, upgrading to Edgy has been a nightmare.  This is far from the only thing that messed up after the upgrade.

---

### Post by dentaku65 on 2006-11-02
I fix in this way, but using the vmware server (the problem was in any case the player that wasn't starting)

Edit this file
```
/usr/lib/vmware/lib/wrapper-gtk24wrapper-gtk24.sh
```
(be careful is in read only and you must cange the permission)

Then find this line:
```
# Run "$binary" while watching its progress on its stderr.
vm_run() {
   local exitCode;

   # Append any libraries that are still missing.
   if [ "$VMWARE_USE_SHIPPED_GTK" = 'force' ]; then
      export LD_PRELOAD="$LD_PRELOAD":"`LANGUAGE=C LANG=C ldd "$binary" | vm_append_missing`"
   else
      local ldBasePath
      if [ ! -z "$LD_LIBRARY_PATH" ]; then
         ldBasePath="$LD_LIBRARY_PATH:"
      fi
      export LD_LIBRARY_PATH="$ldBasePath""`LANGUAGE=C LANG=C ldd "$binary" | vm_append_missing`"
   fi

```

and modify like this:
```
# Run "$binary" while watching its progress on its stderr.
vm_run() {
   local exitCode;

[B]# Fix for vmplayer pulling in libdbus-1.so.2 instead of .3
export LD_PRELOAD=/usr/lib/libdbus-1.so.3:$LD_PRELOAD[/B]

   # Append any libraries that are still missing.
   if [ "$VMWARE_USE_SHIPPED_GTK" = 'force' ]; then
      export LD_PRELOAD="$LD_PRELOAD":"`LANGUAGE=C LANG=C ldd "$binary" | vm_append_missing`"
   else
      local ldBasePath
      if [ ! -z "$LD_LIBRARY_PATH" ]; then
         ldBasePath="$LD_LIBRARY_PATH:"
      fi
      export LD_LIBRARY_PATH="$ldBasePath""`LANGUAGE=C LANG=C ldd "$binary" | vm_append_missing`"
   fi

```

Save and exit. Load vmware. :cool: :cool: :cool:

---

### Post by bengineerd on 2006-11-02
Thanks for the advice. I made the change.  Now Vmware-player runs, but it still tries to install/uninstall it everytime I run an update with apt-get or synaptic or any other package management tool.  Basically whenever I update any package, it also tries to uninstall vmware-player (which takes a while) and always fails.  ](*,) 

The error looks like this:

> 

Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.142.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install 
already exists.  Overwrite? [yes] 

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.84.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] 

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Setting up emacs (21-0ubuntu2) ...
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:



---

### Post by robmoore on 2006-11-02
This did the trick of removing for me:

```
sudo dpkg --remove --force-remove-reinstreq vmware-player
```

---

### Post by viper on 2006-11-02
> **robmoore said:**
> This did the trick of removing for me:

```
sudo dpkg --remove --force-remove-reinstreq vmware-player
```

robmoore ur a legend :) this fix worked for me also thanx

---

### Post by decker on 2006-11-05
worked for me! Thanks!

---

### Post by irongeek on 2006-11-06
Even the "sudo dpkg --remove --force-remove-reinstreq vmware-player" trick does not work for me. Any other ideas?

Here is my error:

```

root@irongeek-desktop:/home/irongeek# sudo dpkg --remove --force-remove-reinstreq vmware-player
(Reading database ... 145324 files and directories currently installed.)
Removing vmware-player ...
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--remove):
 subprocess pre-removal script returned error exit status 1
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
VMware Player is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/bin/vmware-config.pl.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
root@irongeek-desktop:/home/irongeek#

```

---

### Post by irongeek on 2006-11-06
Ok, after a quick reboot and a manual install robmoore's trick worked. Thanks much.

---

### Post by tehwa on 2006-11-08
The command worked for me, but only after *violently* killing any vmware processes with a ```
sudo killall vm*
```...which might explain irongeek's success after a reboot, I think you have to kill the services first.

---

### Post by cayhorstmann on 2006-11-11
The dpkg command uninstalls vmware-player, right? (That's what it did for me when I tried it.) 

But that doesn't help me. I want to keep vmware-player, but I don't want that awful post-install script after every install of unrelated software. 

vmware-player works just fine for me. (I use NAT, not bridged networking.) I'd be happy if I could just convince apt that it is installed ok. 

Thanks for any help!

---

### Post by jinxed on 2006-11-15
> **robmoore said:**
> This did the trick of removing for me:

```
sudo dpkg --remove --force-remove-reinstreq vmware-player
```

I tried that and it removed everything but the config files. I ended up using 
```
sudo dpkg --purge --force-remove-reinstreq vmware-player
``` which seemed to do the trick.

---

### Post by cayhorstmann on 2006-11-16
Just to answer my own question...if you want to **keep** the VMWare player (rather than uninstalling it) and you want to get rid of the annoying error apt-get messages, edit /var/lib/dpkg/info/vmware-player.postinst and add a line "exit 0" to the top. The next time, apt-get runs, it will skip the buggy postinst script, believe that VMWare is successfully installed, and update its database. 

Then use NAT networking in VMWare, and you are all set.

---

### Post by smalldog on 2006-11-24
> **bengineerd said:**
> I am having the exact same problem.
I tried reinstalling vmware player manually from the downloaded tar package, but it says:


I tried the manual uninstall as well, but it ran and basically did nothing.

I swear, upgrading to Edgy has been a nightmare.  This is far from the only thing that messed up after the upgrade.

I have same experience, but I never upgrade to Edgy. I only had done is upgrade kernel from i386 to k7 with same dapper installation. I am still looking for a way to install vmware, however, it does not occur when I installed with breezy before. :(

---

### Post by Ublis on 2006-11-25
> **dentaku65 said:**
> I fix in this way, but using the vmware server (the problem was in any case the player that wasn't starting)

Edit this file
<snip>
Save and exit. Load vmware. :cool: :cool: :cool:

Thanks for that, it fixed my installation too.

---

### Post by corevette on 2006-12-10
> **robmoore said:**
> This did the trick of removing for me:

```
sudo dpkg --remove --force-remove-reinstreq vmware-player
```

well i have the same problem and i tried doing the force remove and this is what came up:

```
corevette@corevette-desktop:~$ sudo dpkg --remove --force-remove-reinstreq vmware-player
Password:
(Reading database ... 144315 files and directories currently installed.)
Removing vmware-player ...
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--remove):
 subprocess pre-removal script returned error exit status 1
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
corevette@corevette-desktop:~$ 

```

---

### Post by theeren on 2006-12-17
After trying all of the following I was able to remove vmware player with synaptic after a reboot.

> 
sudo dpkg --remove --force-remove-reinstreq vmware-player
sudo dpkg --purge --force-remove-reinstreq vmware-player
sudo killall vm*


Not necessarily in the same order. But it is gone now.

Tammo

---

### Post by bomanizer on 2006-12-27
Hmm, my problem was similar, but with a weird twitch... it seems that the installation of vmware-player (with automatix2) left my wireless busted. Somehow related to the network settings? As i recall, a fresh Edgy-installation was able to use my wireless card.. but now the Network Manager Applet (see attachment) doesn't display the wireless option anymore... :( any ideas?

---

### Post by bomanizer on 2007-01-03
Bump

---

### Post by locutus42 on 2007-01-21
I too changed my default kernel to the K7 one and had problems with the VMware-Player but I was able to get it working or atleast configured without apt-get complaining anymore. here's what I did:
NOTE: What I did was on Dapper LTS but the problems mentioned are similar to what I've run across and should help in Edgy.

1) Install the VMware-player module source: 
```
sudo apt-get install vmware-player-kernel-source
```
2) unpack the source:
```
sudo tar -xjf /usr/src/vmware-player-kernel-source.tar.bz2 -C /usr/src
```
3) make the vmnet and vmmon kernel modules:
```
cd /usr/src/modules/vmware-player-kernel/vmnet-only
sudo make; sudo cp vmnet.ko /lib/modules/`uname -r`/misc
cd /usr/src/modules/vmware-player-kernel/vmmon-only
sudo make; sudo cp vmmon.ko /lib/modules/`uname -r`/misc
sudo depmod -a
sudo modprobe vmnet
```
4) Here, I then tried to get the vmware configuration to work but it still failed. BUT, the next morning I thought of one more thing and tried that. The one more thing was to enable eth0 since I remmembered the problems vmware server had with using my wireless network instead of eth0. So, even without an ethernet cable connected, I turned on eth0 with this:
```
sudo ifup eth0
```
5) Now I re-ran the config and restarted vmware-player daemons: 
```
sudo vmware-config-network.pl
sudo /etc/init.d/vmware-player restart
```

If that doesn't work, try rebooting, enabling eth0, and then re-run apt-get or dpkg-reconfigure to kick off the vmware-player config script.

---

### Post by damagedspline on 2007-02-02
> **bomanizer said:**
> Hmm, my problem was similar, but with a weird twitch... it seems that the installation of vmware-player (with automatix2) left my wireless busted. Somehow related to the network settings? As i recall, a fresh Edgy-installation was able to use my wireless card.. but now the Network Manager Applet (see attachment) doesn't display the wireless option anymore... :( any ideas?

I accidently came across your bug. to solve it u need to comment out your wireless interfaces in /etc/network/interfaces with '#'

like:

```
#iface ath0 inet dhcp
#wireless-essid asaf-router
#wireless-key s:

#auto wlan0
#iface wlan0 inet dhcp
```

restart (or kill&run NetworkManager) and there you go.

---

### Post by fu_fish on 2007-02-09
I was able to finally uninstall by editting /etc/init.d/vmware-player and adding ```
exit 0
``` in the second line.

---

### Post by Braedley on 2007-10-04
> **theicyj said:**
> I was able to fix the problem by downloading and reinstalling vmware manually, then uninstalling it using Synaptic.

THANK YOU!!!  VirtualBox was a lot less painful to install, and it actually works.  Now I don't have to worry about updates failing because vmware was screwed up.

---

