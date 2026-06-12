---
title: "Possible fixes to stop Hardy from Freezing"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by whatever69 on 2008-05-17
Hi,

I had spend 5 days trying to get a 6.06 machine running upgraded to 8.04.  Had too many issues.  Did a fresh install of 8.04 Hardy but still had a very unstable system.  Here are some of the things I tried.

1.  Ram memtest to eliminate the obvious.  After 6 hours, not a single error.  So RAM is fine.

2.  Checked the logs.  They are in /var/log and there are some subdirectories like samba (/var/log/samba)

Noticed that I was getting some crashes which I found in my log.192.x.y.z log:```

  ===============================================================
[2008/05/09 15:24:16, 0] lib/fault.c:fault_report(42)
  INTERNAL ERROR: Signal 11 in pid 6383 (3.0.28a)
  Please read the Trouble-Shooting section of the Samba3-HOWTO
[2008/05/09 15:24:16, 0] lib/fault.c:fault_report(44)
  
  From: http://www.samba.org/samba/docs/Samba3-HOWTO.pdf
[2008/05/09 15:24:16, 0] lib/fault.c:fault_report(45)
  ===============================================================
[2008/05/09 15:24:16, 0] lib/util.c:smb_panic(1633)
  PANIC (pid 6383): internal error
[2008/05/09 15:24:16, 0] lib/util.c:log_stack_trace(1737)
  BACKTRACE: 12 stack frames:
   #0 /usr/sbin/smbd(log_stack_trace+0x2d) [0x828a92d]
   #1 /usr/sbin/smbd(smb_panic+0x5d) [0x828aa5d]
   #2 /usr/sbin/smbd [0x82752da]
   #3 [0xb7f86420]
   #4 /usr/sbin/smbd(volume_label+0x54) [0x809b2a4]
   #5 /usr/sbin/smbd(handle_trans2+0x25a) [0x80ecb1a]
   #6 /usr/sbin/smbd(reply_trans2+0x69c) [0x80f35dc]
   #7 /usr/sbin/smbd [0x810f89e]
   #8 /usr/sbin/smbd(smbd_process+0x89b) [0x8110cfb]
   #9 /usr/sbin/smbd(main+0xa18) [0x835e8f8]
   #10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7b9d450]
   #11 /usr/sbin/smbd [0x80942c1]
[2008/05/09 15:24:16, 0] lib/util.c:smb_panic(1638)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 6383]
[2008/05/09 15:24:16, 0] lib/util.c:smb_panic(1646)
  smb_panic(): action returned status 0
[2008/05/09 15:24:16, 0] lib/fault.c:dump_core(181)
  dumping core in /var/log/samba/cores/smbd
[2008/05/09 15:24:16, 0] lib/util_sock.c:write_data(562)
  write_data: write failure in writing to client 192.168.0.106. Error Connectio
n reset by peer
[2008/05/09 15:24:16, 0] lib/util_sock.c:send_smb(769)
  Error writing 4 bytes to client. -1. (Connection reset by peer)
[2008/05/09 15:24:16, 1] smbd/service.c:make_connection_snum(1033)
  windowspc (192.168.0.106) connect to service raid initially as user roy (uid=
1000, gid=1000) (pid 6398)
```


Also was getting this repeating a lot in the log.nmbd log:

```
[2008/05/16 22:26:06, 0] lib/interface.c:load_interfaces(229)
  WARNING: no network interfaces found
```

I went into /etc/smb.conf and enabled 

```
interfaces = eth0
```

where eth0 if your network interface.  I still get that message, but it doesn't repeat, and it eventually turns into this:
```

[2008/05/17 16:35:38, 0] nmbd/nmbd.c:main(711)
  Netbios nameserver version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/05/17 16:35:38, 0] lib/interface.c:load_interfaces(229)
  WARNING: no network interfaces found
[2008/05/17 16:35:38, 0] nmbd/nmbd_subnetdb.c:create_subnets(190)
  create_subnets: No local interfaces !
[2008/05/17 16:35:38, 0] nmbd/nmbd_subnetdb.c:create_subnets(191)
  create_subnets: Waiting for an interface to appear ...
[2008/05/17 16:35:43, 0] lib/interface.c:load_interfaces(229)
  WARNING: no network interfaces found
[2008/05/17 16:41:36, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396)
  *****
  
  Samba name server UBUNTUSERVER is now a local master browser for workgroup PEANUTS on subnet 192.168.0.101
  
  *****
```
 
I also discovered that Ubuntu was having problems with NetworkManager:
```

May 16 14:09:41 ubuntuserver avahi-daemon[5020]: Joining mDNS multicast group o
n interface eth0.IPv4 with address 192.168.0.101.
May 16 14:09:41 ubuntuserver avahi-daemon[5020]: New relevant interface eth0.IP
v4 for mDNS.
May 16 14:09:41 ubuntuserver avahi-daemon[5020]: Registering new address record
 for 192.168.0.101 on eth0.IPv4.
May 16 14:09:41 ubuntuserver NetworkManager: <info>  DHCP daemon state is now 4
 (reboot) for interface eth0 
May 16 14:09:41 ubuntuserver NetworkManager: <info>  Activation (eth0) Stage 4 
of 5 (IP Configure Get) scheduled... 
May 16 14:09:41 ubuntuserver NetworkManager: <info>  Activation (eth0) Stage 4 
of 5 (IP Configure Get) started... 
May 16 14:09:41 ubuntuserver dhclient: bound to 192.168.0.101 -- renewal in 269
584 seconds.
May 16 14:09:42 ubuntuserver dhcdbd: message_handler: message handler not found
 under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
May 16 14:09:42 ubuntuserver dhcdbd: message_handler: message handler not found
 under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
May 16 14:09:42 ubuntuserver dhcdbd: message_handler: message handler not found
 under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
May 16 14:09:42 ubuntuserver dhcdbd: message_handler: message handler not found
 under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
May 16 14:09:42 ubuntuserver NetworkManager: <info>  Retrieved the following IP
4 configuration from the DHCP daemon: 
May 16 14:09:42 ubuntuserver NetworkManager: <info>    address 192.168.0.101 
May 16 14:09:42 ubuntuserver NetworkManager: <info>    netmask 255.255.255.0 
May 16 14:09:42 ubuntuserver NetworkManager: <info>    broadcast 192.168.0.255 
May 16 14:09:42 ubuntuserver NetworkManager: <info>    gateway 192.168.0.1 
May 16 14:09:42 ubuntuserver NetworkManager: <info>    nameserver 192.168.0.1 
May 16 14:09:42 ubuntuserver dhcdbd: message_handler: message handler not found
 under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
May 16 14:09:42 ubuntuserver NetworkManager: <info>  Activation (eth0) Stage 5 
of 5 (IP Configure Commit) scheduled... 
May 16 14:09:42 ubuntuserver NetworkManager: <info>  Activation (eth0) Stage 4 
of 5 (IP Configure Get) complete. 
May 16 14:09:42 ubuntuserver NetworkManager: <info>  Activation (eth0) Stage 5 
of 5 (IP Configure Commit) started... 
May 16 14:09:42 ubuntuserver avahi-daemon[5020]: Withdrawing address record for
 192.168.0.101 on eth0.
May 16 14:09:42 ubuntuserver avahi-daemon[5020]: Leaving mDNS multicast group o
n interface eth0.IPv4 with address 192.168.0.101.
May 16 14:09:42 ubuntuserver avahi-daemon[5020]: Interface eth0.IPv4 no longer...

...

May 16 14:09:53 ubuntuserver kernel: [   87.750561] eth0: no IPv6 routers present
May 16 14:10:04 ubuntuserver NetworkManager: <info>  Updating allowed wireless network lists. 
May 16 14:10:04 ubuntuserver NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: or
g.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
```


I don't have any wireless networks and I don't know why it's enabled.  So I decided to go into the computer BIOS and disable the onboard NIC in favour of my Intel NIC.  This way there's no weirdness going on.  Just for the heck of it, I also disabled the onboard sound.  It worked fine but I just wanted to make sure.

Next I went through all the services using sysvconfig

```
sudo apt-get install sysvconfig
``` 

I disabled CUPS, CPU Frequency Manager, Bluetooth, nvidiakernel (as I have nothing that is nvidia), pulseaudio (only for the heck of it), xserver-xorg-input-wacom (for tablet pc stuff), etc...basically anything I could disable, I did.

I then went in and double checked my /etc/hosts file:

```
127.0.0.1 ubuntuserver localhost
127.0.1.1 ubuntuserver
192.168.0.101 ubuntuserver
192.168.0.100 macbook
192.168.0.107 windowspc

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Looking in my /var/log/messages, I used to have 

```
May 17 16:35:49 ubuntuserver dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
May 17 16:35:49 ubuntuserver dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
May 17 16:35:49 ubuntuserver dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
```

repeat quite a bit.  Now it doesn't as much.  It seems harmless enough, as eth0 is functioning just fine.

Bascially, I found that the NetworkManager was causing a lot if instability since it affected Samba and connecting to the Internet, and downloading torrents.  I was using Transmission and  the computer was freezing.  Had to do a hard reset.

I also found some pam module errors in samba:

```
May  9 14:05:51 ubuntuserver sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  9 14:05:51 ubuntuserver sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared ob
ject file: No such file or directory]
May  9 14:05:51 ubuntuserver sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
```


I had to 

```
sudo apt-get install pam_smbpass
``` 

in order to have that not repeat in the /var/log/auth.log file.

Also, it took me a few days to be able to get the via driver to work with my Unichrom IGP (CLE266) with my Samsung 40" A530.  All I could get was 1024x768.  1920x1080 or 1280x720 don't show up in my resolutions drop down list.  Here's a functional xorg.conf file should you want to use it:

xorg.conf:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"us"
	Option		"XkbOptions"	"us"
EndSection

Section "Files"
        ModulePath   "/usr/lib/xorg/modules/"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "A2"                        # [<bool>]
        #Option     "NoAccel"                   # [<bool>]
        #Option     "HWCursor"                  # [<bool>]
        #Option     "SWCursor"                  # [<bool>]
        #Option     "ShadowFB"                  # [<bool>]
        #Option     "Rotate"                    # [<str>]
        #Option     "UseBIOS"                   # [<bool>]
        #Option     "VideoRAM"                  # <i>
        #Option     "ActiveDevice"              # [<str>]
        #Option     "LCDDualEdge"               # [<bool>]
        #Option     "BusWidth"                  # [<str>]
        #Option     "Center"                    # [<bool>]
        #Option     "PanelSize"                 # [<str>]
        #Option     "TVDotCrawl"                # [<bool>]
        #Option     "TVType"                    # [<str>]
        #Option     "TVOutput"                  # [<str>]
        #Option     "TVVScan"                   # [<str>]
        #Option     "TVHScale"                  # [<str>]
        #Option     "TVEncoder"                 # [<str>]
        #Option     "Refresh"                   # <i>
        #Option     "DisableVQ"                 # [<bool>]
        #Option     "NoDDCValue"                # [<bool>]
        #Option     "Cap0Deinterlace"           # [<str>]
        #Option     "Cap1Deinterlace"           # [<str>]
        #Option     "Cap0FieldSwap"             # [<bool>]
        #Option     "DRIXINERAMA"               # [<bool>]
        Identifier  "Card0"
        Driver      "via"
        VendorName  "Via"
        BoardName   "cle266"
        BusID       "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Samsung"
        ModelName    "LN40A530"
        HorizSync    30.0 - 60.0
        VertRefresh  60.0 - 75.0
EndSection

Section "Module"
        Load  "extmod"
        Load  "dri"
        Load  "dbe"
        Load  "record"
        Load  "xtrap"
        Load  "glx"
        Load  "type1"
        Load  "freetype"
	Load  "vbe"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
	DefaultDepth 16
        SubSection "Display"
                Viewport   0 0
                Depth     16 
		Modes     "1920x1080" "1280x720" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
        Screen      0   "Screen0" 0 0
EndSection

Hope that helps some people out there.  I know it did for me because I couldn't even browse the Internet for no more than 3 minutes without Firefox crashing or the system freezing.

Enjoy.

---

