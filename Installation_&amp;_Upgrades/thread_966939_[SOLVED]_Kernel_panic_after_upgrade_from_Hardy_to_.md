---
title: "[SOLVED] Kernel panic after upgrade from Hardy to Intrepid"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by cparker on 2008-11-01
Hello all,

I'm not having much luck with my upgrade from 8.04 to 8.10. I followed the directions for upgrading **over the Internet** at [https://help.ubuntu.com/community/IntrepidUpgrades/Kubuntu](https://help.ubuntu.com/community/IntrepidUpgrades/Kubuntu)

After the upgrade finished, I rebooted my machine as requested. When the system started booting back up, I got a message from GRUB saying the splash screen couldn't be loaded. Not a problem. I pressed a key, then let GRUB load using the new kernel. I was then presented with the following:

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

This happens every time I try to boot with the new kernel.

Booting with my previous kernel starts up GDM (instead of my previous default KDM). After booting into KDE 4.1 (which I had installed previously through launchpad ppa), I notice my wallpaper has changed, my favorite applications in the KDE menu have been reset, all plasmoids have been reset, and all of my notes that I had posted on my desktop are gone and have been replaced with a single default note. I also can't get online anymore (my eth0 device is gone, and reconfiguring it in /etc/network/interfaces is ineffective), so I'm having to post this from my wife's machine.

If it makes a difference, the machine experiencing these problems is a [Gateway Solo 5300]("https://support.gateway.com/s/manlib/Notebooks/Solo5300/8508144/8508144.htm").

Any ideas?

---

### Post by cparker on 2008-11-03
On a side note, I do have access to a CD burner at work, so I could just burn an installation disc to try to fix this issue, but I'd rather find a direct solution instead (especially if simply reinstalling won't fix the problem). Chances are, my situation isn't unique (although I couldn't find any other reports of this issue), so a direct solution could benefit others.

Could this problem (kernel panic) be caused from a bad parameter in menu.lst? I can post my menu.lst if requested.

---

### Post by cparker on 2008-11-05
I decided to try booting in recovery mode, and here's the last 6 messages I got (timestamps omitted):

> BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
EDD information not available
input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
VFS: Cannot open root device "UUID=47ad1fc0-8930-4438-88f3-6885465921c1" or unknown-block(0,0)
Please append a correct "root=" boot option; here are the available partitions:
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

I ran "sudo update-grub" using my previous kernel before rebooting and getting this message. I did notice there isn't an initrd line for the new 2.6.27 kernel entries in menu.lst after running update-grub, but other than that, there's no discernable difference.

Does anyone know what could be causing my problem? If not, what else should I be looking at? I'll try re-installing the 2.6.27 kernel by booting into the previous kernel and hoping my apt cache wasn't cleared, but I'm doubting that will fix the problem.

---

### Post by halfmanhalfbug on 2008-11-05
Hi cparker
It sounds like the upgrade set the wrong value for root in your menu.lst. Could you post your menu.lst?
Try the following:
1) boot in your old kernel or in recovery mode
2) open /boot/grub/menu.lst in a text editor
3) look at the values after "root " and "root=" for each kernel...are they the same? They should be. Do you have (hd0,0) or just (0,0)? I think it should be something like (hd0,0).
Here are my values for example:
```
title		Ubuntu 8.04, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=9ecb103d-bf9d-4969-8f80-735d37fefcb8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9ecb103d-bf9d-4969-8f80-735d37fefcb8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
```
Note that the values for root are the same for the kernels (though I haven't upgraded to Intrepid).
Hope this helps. If not I'm stumped (and somebody please correct me if I'm wrong),
hmhb

---

### Post by cparker on 2008-11-05
Hi, halfmanhalfbug.

I thought I'd try adding the initrd line to my 2.6.27 kernel entry in menu.lst. I did this directly through GRUB (with initrd.img-2.6.27-7-generic, of course), so my changes aren't permanent. However, once I did this, the kernel panic went away. I can now boot using the new kernel.

Strange that update-grub didn't add the initrd line even though it's required to boot. Bug?

Now that I'm booted up into Intrepid with the 2.6.27 kernel, I've noticed that the changes to my Plasmoids appear to be permanent, and I still can't get online. I'll document my progress on getting my internal NIC working again in this thread, since the issue is also related to my Intrepid upgrade.

Thanks again for your reply, halfmanhalfbug. I appreciate it.

---

### Post by halfmanhalfbug on 2008-11-05
Thanks for your update. Now I know too. ;)

---

### Post by cparker on 2008-11-05
Some interesting bits from dmesg:

> christopher@cparkerlt:/dev$ sudo dmesg | grep e100
[    3.076541] pci 0000:00:0d.0: Firmware left e100 interrupts enabled; disabling
[    6.413869] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[    6.413881] e100: Copyright(c) 1999-2006 Intel Corporation
[    7.522759] e100 0000:00:0d.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
[    7.523035] e100: 0000:00:0d.0: e100_eeprom_load: EEPROM corrupted
[    7.523059] e100 0000:00:0d.0: PCI INT A disabled
[    7.523077] e100: probe of 0000:00:0d.0 failed with error -11

This NIC was working fine before the upgrade. Could it be a coincidence that this happened during my upgrade to Intrepid?

---

### Post by cparker on 2008-11-05
I Googled *e100 eeprom* and got this as the first result: [http://www.ubuntugeek.com/fix-for-intel-cards-with-broken-eeprom-e100-driver.html](http://www.ubuntugeek.com/fix-for-intel-cards-with-broken-eeprom-e100-driver.html)

This page instructs you to add the following line to /etc/modprobe.d/options:

> options e100 eeprom_bad_csum_allow=1

I did so, then ran the following:

> christopher@cparkerlt:/dev$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.27-7-generic

Before rebooting, I added the initrd lines to my menu.list for 2.6.27. Then I re-ran update-grub, re-checked menu.lst, and noticed the initrd lines were still there. Interesting...

The following boot took a little longer than usual. As soon as GDM came up, I switched to tty6 and tried to ping my router... and nothing. This is what happens when I restart networking:

> christopher@cparkerlt:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process                                              
Internet Systems Consortium DHCP Client V3.1.1                                  
Copyright 2004-2008 Internet Systems Consortium.                                
All rights reserved.                                                            
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)                              

Listening on LPF/eth0/00:00:00:00:00:00
Sending on   LPF/eth0/00:00:00:00:00:00
Sending on   Socket/fallback           
DHCPRELEASE on eth0 to 192.168.10.254 port 67
send_packet: Network is unreachable          
send_packet: please consult README file regarding broadcast address.
SIOCSIFFLAGS: Cannot assign requested address                       
SIOCSIFFLAGS: Cannot assign requested address                       
Internet Systems Consortium DHCP Client V3.1.1                      
Copyright 2004-2008 Internet Systems Consortium.                    
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
Listening on LPF/eth0/00:00:00:00:00:00
Sending on   LPF/eth0/00:00:00:00:00:00
Sending on   Socket/fallback
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
RTNETLINK answers: Network is down
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2
 * Stopping NTP server ntpd
   ...done.
 * Starting NTP server ntpd
   ...done.
                                                                         [ OK ]

Observations:

[LIST]
[*]My router's IP address from when the NIC was working (192.168.10.254) is mentioned when ifdown is invoked.
[*]The MAC address for the NIC is listed as 00:00:00:00:00:00.
[/LIST]

---

### Post by cparker on 2008-11-05
Problem solved! I'm back online. I ended up resetting the NIC's MAC address, using its original address I retrieved from the expired leases on my router (custom-built Debian etch box):

> sudo ifconfig eth0 hw ether NN:NN:NN:NN:NN:NN

(where NN:NN:NN:NN:NN:NN is the NIC's original MAC address)

I'm probably going to have to make this a permanent setting so this sticks after I reboot, but at least now I know what to do in order to get things back to "normal". Then there are some other annoyances that came along with the upgrade, such as having GDM set up as my default display manager instead of KDM (*sudo dpkg-reconfigure kdm* fixes this), and having to re-setup all of my Plasmoids, although these are minor--not show-stoppers. (It's a good thing my notes I stored using the Notes Plasmoid instances I added weren't vitally important!)

After all is said and done, it seems like some part of the upgrade procedure really got hosed. I just removed the grub splash images package (don't really need them, and the GRUB error message was getting annoying) and got this:

> christopher@cparkerlt:~$ sudo aptitude remove **kubuntu-grub-splashimages**
Reading package lists... Done                                          
Building dependency tree                                               
Reading state information... Done                                      
Reading extended state information                                     
Initializing package states... Done                                    
Writing extended state information... Done                             
The following packages will be REMOVED:                                
[B]  akonadi-server{u} discover1-data{u} festival{u} festlex-cmu{u} festlex-poslex{u} festvox-kallpc16k{u} kdebase-plasma-kde4{u} 
  kubuntu-grub-splashimages libdbd-mysql-perl{u} libdbi-perl{u} liblzo2-2{u} libnet-daemon-perl{u} libplrpc-perl{u} libpoppler-qt2{u} 
  libqt4-gui{u} libtidy-0.99-0{u} mysql-client-5.0{u} mysql-server-5.0{u} ocrad{u} openssh-blacklist{u} pidgin-festival{u} poster{u}  
  tidy{u}                                                                                                                             [/B]
0 packages upgraded, 0 newly installed, 23 to remove and 1 not upgraded.                                                              
Need to get 0B of archives. After unpacking 140MB will be freed.                                                                      
Do you want to continue? [Y/n/?] Y                                                                                                    
Writing extended state information... Done                                                                                            
(Reading database ... 251556 files and directories currently installed.)                                                              
Removing akonadi-server ...                                                                                                           
Reloading AppArmor profiles /sbin/apparmor_parser: Unable to replace "/usr/share/gdm/guest-session/Xsession".  Profile version not supported by Apparmor module                                                                                                                             
 Profile /etc/apparmor.d/gdm-guest-session failed to load                                                                                     
/sbin/apparmor_parser: Unable to replace "/usr/lib/cups/backend/cups-pdf".  Profile version not supported by Apparmor module                  
 Profile /etc/apparmor.d/usr.sbin.cupsd failed to load                                                                                        
/sbin/apparmor_parser: Unable to replace "/usr/sbin/mysqld".  Profile version not supported by Apparmor module                                
 Profile /etc/apparmor.d/usr.sbin.mysqld failed to load                                                                                       
/sbin/apparmor_parser: Unable to replace "/usr/sbin/mysqld-akonadi".  Profile version not supported by Apparmor module                        
 Profile /etc/apparmor.d/usr.sbin.mysqld-akonadi failed to load                                                                               
: Failed.                                                                                                                                     
invoke-rc.d: initscript apparmor, action "force-reload" failed.                                                                               
Unknown media type in type 'all/all'                                                                                                          

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Removing discover1-data ...
Removing pidgin-festival ...
Removing festvox-kallpc16k ...
Removing festlex-poslex ...   
Removing festlex-cmu ...      
Removing festival ...         
Removing kdebase-plasma-kde4 ...
dpkg - warning: while removing kdebase-plasma-kde4, directory `/usr/lib/kde4/share/kde4' not empty so not removed.
dpkg - warning: while removing kdebase-plasma-kde4, directory `/usr/lib/kde4/share' not empty so not removed.     
Removing kubuntu-grub-splashimages ...                                                                            
Your old /boot/grub/menu.lst file will be saved as /boot/grub/menu.lst.081105195117                               
Removing mysql-server-5.0 ...                                                                                     
 * Stopping MySQL database server mysqld                                                                                               [ OK ] 
Removing mysql-client-5.0 ...
Removing libdbd-mysql-perl ...
Removing libdbi-perl ...
Removing liblzo2-2 ...
Removing libplrpc-perl ...
Removing libnet-daemon-perl ...
Removing libpoppler-qt2 ...
Removing libqt4-gui ...
Removing tidy ...
Removing libtidy-0.99-0 ...
Removing ocrad ...
Removing openssh-blacklist ...
Removing poster ...
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done

Current status: 8271 new [-1].

This is despite the fact that I opted to Remove obsolete packages during the upgrade procedure. It seems like this would indicate an interrupted cleanup stage, even though there was nothing to indicate anything of the sort before I clicked the "Reboot" button when prompted to do so.

I then ran update-grub again, just to be sure:

> christopher@cparkerlt:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
**Searching for splash image ... none found, skipping ...**
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/vmlinuz-2.6.20-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

At least this provided me with a learning experience. Hopefully someone will be able to benefit from my issues and their resolutions.

Thanks for reading!

---

### Post by Ahrk on 2008-11-11
Hi, I'm having the same problem on my laptop after upgrading to 8.10. I tried adding the initrd.img-2.6.27-7-generic line to my menu.lst, but then I get an error saying that the file was not found. I checked /boot, and indeed there is no such file, although there are the abi, config, system.map, vmcoreinfo and vmlinuz files for 2.6.27-7-generic. 
Is there any way to obtain the missing initrd.img file?

---

