---
title: "DHCP Problem"
date: 2006-05-26
forum: Installation &amp; Upgrades
---

### Post by alanphil on 2006-05-26
I'm running a current beta of Dapper Drake on a Thinkpad x30 laptop, and having some issues getting DHCP to work properly. I've run hardware diagnostics and the laptop hardware doesn't seem to be the problem. I've also tried multiple network cables and different networks. The only way I can get online with this machine is to assign a static IP. Then everything works fine.

I'm new to troubleshooting DHCP issues. Below is the output from dhclient at the command line. Please let me know what other details would be helpful to troubleshoot this -- and thanks in advance for any help! :D 

sudo dhclient eth0 
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP]("http://www.isc.org/products/DHCP")

Listening on LPF/eth0/00:09:6b:60:d0:79
Sending on   LPF/eth0/00:09:6b:60:d0:79
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPNAK from 140.220.250.35
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by cskeide on 2006-05-26
Maybe a silly question, but are you running a firewall?```
sudo iptables -L
```

---

### Post by alanphil on 2006-05-26
No firewall running (to my knowledge!):

sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by h3h_timo on 2006-05-26
wow.. im having the same exact problem.. until i upgraded to dapper drake.. from the update manager in breezy... it all worked fine.. now i cant get anything

---

### Post by BoucherieSanzot on 2006-05-26
Hello,
DHCP is not working any more for me, for LAN, using pump our dhcpclient, with latest kernel or with previous wan.
But setting manualy network works.

---

### Post by Familyguy on 2006-05-26
Same problem after upgrading Dapper.

---

### Post by alanphil on 2006-05-26
Interesting to see other people with the same problem. I was going nuts trying to fix this and it's a relief to see other people running into the same issue. What do we do to troubleshoot this further? ](*,)

---

### Post by Sgood1971 on 2006-05-26
I had weird DHCP problems all day with Dapper at work. The wireless manager would not connect at all It would only connect if I opened a terminal and did..

```
sudo ifdown eth1
```

then

```
sudo ifup eth1
```

Then it would randomley loose it's connection at different points throughout the day.

---

### Post by makrothumeo on 2006-05-27
I got the exact same problem, does anybody have the answer?

Appears to be something new in dapper if it happens by upgrading. I see the wireless signal for my network, but it simply won't connect.

Isn't wlan0 suppose to be connected to if(up, down)? I don't know if this will help at all, but this is what my terminal says when I try to ifdown the wireless connection:

[INDENT]david@dms-E1705:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
[/INDENT]

Normal?

I'm just trying to throw something out there. Hope someone comes up with the fix soon.

---

### Post by alanphil on 2006-05-27
A workaround? :rolleyes: 

1. Setup a static IP address, connect to the network. 
2. Then setup for DHCP and issue a request for a new IP address (using the dhclient command, shown below). 

This works on my home network now. It was not working all week -- but I've been downloading Dapper updates every day, so it's a moving target. It would be interesting to see if other people can get their DHCP working following these steps. 

sudo dhclient eth0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:09:6b:60:d0:79
Sending on   LPF/eth0/00:09:6b:60:d0:79
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.104 -- renewal in 37408 seconds.

---

### Post by jvictor on 2006-05-27
I guess this has been there prior to dapper.

Hoary, Badger all needed static IP.. I thought it was a problem with my router, but now began doubting if the DHCP thingy in Ubuntu is fine coz many are facing the same problem.

---

### Post by makrothumeo on 2006-05-27
Alanphil...
I think I love you.

Your workaround worked, and it wasn't even a hassle to go through.

My laptop is FINALLY fully working with linux now :-D 

Goodbye XP!

---

### Post by alanphil on 2006-05-28
I found one other tweak worth mentioning in this thread. Later in the day after I thought I had all of my DHCP issues resolved, I had a friend visiting with a laptop. They were not able to get an IP address from the router. 

After digging into the details, I discovered that my Linksys router was setup to only allow five DHCP clients. I had set this up back in 2001 and forgotten about the details. I think this setting may  account for some of the problems I was having with my Ubuntu laptop. If the Linksys router had already given out five IP addresses and my Ubuntu requested the sixth, the Linksys appears to leave the sixth client hanging until it times out waiting for an IP address. ](*,) 

The best approach may be to simplify your network as much as possible if you need to troubleshoot DHCP, wireless, or other network issues. I would have saved many hours of trial and error testing if I had taken a look at the router settings earlier.

---

### Post by Slim Odds on 2006-05-28
[QUOTE=alanphil]
The best approach may be to simplify your network as much as possible if you need to troubleshoot DHCP, wireless, or other network issues. I would have saved many hours of trial and error testing if I had taken a look at the router settings earlier.[/QUOTE]

Yes, I think way too many people are thinking Ubuntu has problems with DHCP, when so many times it's really something else.

I have a Windows XP system that I can NOT get to work with DHCP on my Netgear router. All the Ubuntu machines are fine.

---

### Post by fabiomb on 2006-05-28
i have updated my kubuntu today, have the same problem.

1.- After start my PC, the network doesn't work


fabio@willywonka:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.102 icmp_seq=2 Destination Host Unreachable
From 192.168.1.102 icmp_seq=3 Destination Host Unreachable
From 192.168.1.102 icmp_seq=4 Destination Host Unreachable


192.168.1.1 is my router , my other PC works perfectly, Breezy, Hoary too, but i updated to Dapper today

2.- unplug the ethernet cable and plugged it again, it works! WFT? yes, a quick unplug-replug and the net works again, i have DHCP in this network, the same problem.

¿Electrical problem? not, because this is the same machine, the same eth card, an OS update broken my eth? no, i started with windoze and it works! So, Dapper is the problem.

3.- sudo dhclient eth0 don't work for me, it never gets a new IP address again, simply don't work, look at this:

> 
fabio@willywonka:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

çListening on LPF/eth0/00:80:ad:79:ea:6f
Sending on   LPF/eth0/00:80:ad:79:ea:6f
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
Trying recorded lease 192.168.1.101
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.


if i unplug the network cable and run again:

> 
fabio@willywonka:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:80:ad:79:ea:6f
Sending on   LPF/eth0/00:80:ad:79:ea:6f
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.101 -- renewal in 268386 seconds.
fabio@willywonka:~$    



4.- now i reconfigured my router (WiFi-LAN router from Encore), now i disabled the DHCP, and it have THE SAME PROBLEM! 

5.- i unplug again, and the net is here!

64 bytes from 192.168.1.1: icmp_seq=147 ttl=127 time=0.713 ms
64 bytes from 192.168.1.1: icmp_seq=148 ttl=127 time=0.673 ms
64 bytes from 192.168.1.1: icmp_seq=149 ttl=127 time=0.805 ms
64 bytes from 192.168.1.1: icmp_seq=150 ttl=127 time=0.728 ms


6.- ok, something "broke" the connection between my Eth0 and my Router, only a few minutes after my "manual fix".

What i can do? i have no DHCP actually, only manual config, and the problem persists
If i want to update, it's impossible :s if i want to send this message i must to restart "manualy" the connection
Somebody knows how to report a bug? i'm a newbie on this...
(Sorry for my english, it's not my language :p)

---

### Post by fabiomb on 2006-05-28
update:

i am using iptraf to see what come and what goes from the eth0 interface, my ethernet receives data, but don't send, no outgoing packets.

a driver problem?

---

### Post by MadMan2k on 2006-05-28
try if running "sudo dhclient" manually has the same effect as unplugging the cable.
I'm having a very similar issue with a wrong assigned ip on first try...

/edit:
man if I only had 1000 more beans, I would be leet!11

---

### Post by fabiomb on 2006-05-28
i disabled DHCP, this command doesn't work

i do this:
> 
fabio@willywonka:~$ sudo ifconfig eth0 down
fabio@willywonka:~$ sudo ifconfig eth0 up


and nothing happens, i still need to unplug the cable to make the connection work... only a minute and it's broken...

---

### Post by Familyguy on 2006-05-28
I have Breezy ,Dapper , and Win98 on the same PC.
As I posted eariler I can not access the internet after the upgrade if I boot to Dapper.
But if I boot into Breezy or Win98 I can access the internet.

---

### Post by fabiomb on 2006-05-28
[QUOTE=Familyguy]I have Breezy ,Dapper , and Win98 on the same PC.
As I posted eariler I can not access the internet after the upgrade if I boot to Dapper.
But if I boot into Breezy or Win98 I can access the internet.[/QUOTE]

the same problem, but no answers :confused:

---

### Post by fabiomb on 2006-05-29
nobody at home? :(

How many days for the Dapper Release?

---

### Post by Xavi pintant on 2006-05-31
I have a similar problem. 

The eth0 (ethernet cable) now is named eth1, and the eth1 (wireless) is named eth2. The new eth1 works, but the new eth2 never connects. I cannot unplug and replug because it's PCMCIA and i don't want to hurt my PC.

---

### Post by TimJ on 2006-06-01
There were a lot of threads about wireless problems like this in the Dapper development forum. There was also a thread (I now can't find as I need to get back to work) for those not using wireless with the same problem. It seems to be a regression for people who had things working in Breezy and upgrade to find their connection is brokent.

I get connectivity for 5-10 seconds after booting up and then it breaks, I had connectivity fine under Breezy (I upgraded to Dapper and then did a clean install of Dapper to see if that solved it). I get this from sudo dhclient eth0:

[SIZE="1"]sudo dhclient eth0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:08:a1:0b:8d:19
Sending on   LPF/eth0/00:08:a1:0b:8d:19
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/SIZE]

If I try the work around suggested above (change eth0 to static IP, then back to dhcp and do suco dhclient eth0) I get the same output.

I tried removing the router between my pc and cable-modem. This got me a replication of the short connectivity I get on bootup. So first I get:

[SIZE="1"]sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:08:a1:0b:8d:19
Sending on   LPF/eth0/00:08:a1:0b:8d:19
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 10.181.64.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.181.64.1
bound to 82.35.248.10 -- renewal in 34490 seconds.[/SIZE]

But then within a few seconds the connection drops and I get:

[SIZE="1"] sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:08:a1:0b:8d:19
Sending on   LPF/eth0/00:08:a1:0b:8d:19
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
Trying recorded lease 82.35.248.10
PING 82.35.248.1 (82.35.248.1) 56(84) bytes of data.

--- 82.35.248.1 ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.[/SIZE]

I therefore guess that it is a Ubuntu Dapper issue and not my router, though if someone sees something else give me a clue. All the wireless threads were about ndiswrapper and the right linux driver but I'm not sure whether that applies to non-wireless (non-usb too) or what to do about it if it did.

If anyone has any suggestions I'm happy to go and try them, I'd love to get this working as I'm working of winXP again now and thinking about either another distro or going back to Breezy.

---

### Post by nkbj on 2006-06-01
Looks alot like this bug report: [https://launchpad.net/distros/ubuntu/+bug/47026](https://launchpad.net/distros/ubuntu/+bug/47026)

Have you tried to boot from the live (desktop) CD?

Regards,
Niels Kristian

---

### Post by TimJ on 2006-06-01
Thanks, that does look close to this problem. I'll go post a link there in case this info helps.

I tried booting from live cd and net connection worked fine. I checked the settings I know about and couldn't see any different. It made me wonder if something left over from Breezy was interfering. I reformatted my / and /swap partitions but left /home so that all my documents etc. would just be sitting there waiting for me. But it does remember Breezy in some ways, such as setting my old theme; I wonder if it's remembering some dhcp setting but don't know enough to work that out. I may have to go reformat /home in an installation to check.

Anyone with any ideas?

---

### Post by RRS on 2006-06-01
Try rebooting router/modem.

Computer off, router off, modem(if seperate device) off.

Restart in reverse order, waiting between devices till appropriate LED indications shown.

Though cause was different (my own mistake) the symptoms and readouts were similar to those reported here and the above worked when all configuration changes and resets failed.

---

### Post by TimJ on 2006-06-01
Thanks for the suggestions RRS, it didn't work though. I had rebooted everything but not in the exact order you suggested, but even doing it again the way you suggest the same fault occurs. I also reformated my /home partition on another reinstall but it didn't help either. I'm back to Windows now until I can find another way forward.

---

### Post by djbjrca on 2006-06-01
I believe I am having the exact same issue.  I can get it from the liveCD, but not the HDD install.  I get 10-20 seconds of connectivity.  I do not have the luxury of removing the router in the middle and directly connecting, but it seems it would not work anyway.  Any help would be great.  My outputs to abve commands are identical.

EDIT:  I guess I could live on the 20 seconds between unplugging and replugging.

---

### Post by daveg2 on 2006-06-01
All, I had problems after upgrading from breezy.  My "CNET Pro200WL PCI Fast Ethernet Adapter" works with either the tulip driver or the dmfe driver under breezy.  I found that both were loaded after the dapper upgrade.  modprobe -r tulip or modprobe -r dmfe resolved the problem.  Tulip only worked for a short period of time before it failed, so I stuck with dmfe.  I blacklisted and renamed tulip---maybe overkill.

Run lsmod to list all loaded modules.  Verify that you have only the correct driver loaded.

I'm afraid I'm too much of a newbie to be able to tell you what the possible NIC drivers are or what driver to use with which NIC, but hopefully this will point you down the correct path.

---

### Post by apollyonis on 2006-06-02
I don't know if this will help, but I'm posting the dhclient.conf and dhclient-script from the live CD since I can't verify it on my own machine - DHCP works fine with Dapper on mine.

/etc/dhcp3/dhclient.conf

```
# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

```

/etc/dhcp3/dhclient-script

```
#!/bin/bash

# dhclient-script for Linux. Dan Halbert, March, 1997.
# Updated for Linux 2.[12] by Brian J. Murrell, January 1999.
# Modified for Debian.  Matt Zimmerman and Eloy Paris, December 2003
# Modified to remove useless tests for antiquated kernel versions that
# this doesn't even work with anyway, and introduces a dependency on /usr
# being mounted, which causes cosmetic errors on hosts that NFS mount /usr
# Andrew Pollock, February 2005
# Modified to work on point-to-point links. Andrew Pollock, June 2005
# Modified to support passing the parameters called with to the hooks. Andrew Pollock, November 2005

# The alias handling in here probably still sucks. -mdz

make_resolv_conf() {
    if [ -n "$new_domain_name" -o -n "$new_domain_name_servers" ]; then
        # Find out whether we are going to mount / rw
        exec 9>&0 </etc/fstab
        rootmode=rw
        while read dev mnt type opts dump pass junk; do
            [ "$mnt" != / ] && continue
            case "$opts" in
                ro|ro,*|*,ro|*,ro,*)
                   rootmode=ro
                   ;;
                 esac
         done
         exec 0>&9 9>&-
 
        # Wait for /etc/resolv.conf to become writable
        if [ "$rootmode" = "rw" ]; then
            while [ ! -w /etc ]; do
                sleep 0.1
            done
        fi

        local new_resolv_conf=/etc/resolv.conf.dhclient-new
        rm -f $new_resolv_conf
        if [ -n "$new_domain_name" ]; then
            echo search $new_domain_name >>$new_resolv_conf
        else # keep 'old' search/domain scope
            egrep -i '^ *[:space:]*(search|domain)' /etc/resolv.conf >> $new_resolv_conf
        fi
        if [ -n "$new_domain_name_servers" ]; then
                   for nameserver in $new_domain_name_servers; do
                       echo nameserver $nameserver >>$new_resolv_conf
            done
        else # keep 'old' nameservers
            sed -n /^\w*[Nn][Aa][Mm][Ee][Ss][Ee][Rr][Vv][Ee][Rr]/p /etc/resolv.conf >>$new_resolv_conf
        fi
        chown --reference=/etc/resolv.conf $new_resolv_conf
        chmod --reference=/etc/resolv.conf $new_resolv_conf
        mv -f $new_resolv_conf /etc/resolv.conf
    fi
}

run_hook() {
    local script="$1"
    local exit_status
    shift	# discard the first argument, then the rest are the script's

    if [ -f $script ]; then
        . $script "$@"
    fi


    if [ -n "$exit_status" ] && [ "$exit_status" -ne 0 ]; then
        logger -p daemon.err "$script returned non-zero exit status $exit_status"
        save_exit_status=$exit_status
    fi

    return $exit_status
}

run_hookdir() {
    local dir="$1"
    local exit_status
    shift	# See run_hook

    if [ -d "$dir" ]; then
        for script in $(run-parts --list $dir); do
            run_hook $script "$@" || true
            exit_status=$?
        done
    fi

    return $exit_status
}

# Must be used on exit.   Invokes the local dhcp client exit hooks, if any.
exit_with_hooks() {
    exit_status=$1

    # Source the documented exit-hook script, if it exists
    if ! run_hook /etc/dhcp3/dhclient-exit-hooks "$@"; then
        exit_status=$?
    fi

    # Now run scripts in the Debian-specific directory.
    if ! run_hookdir /etc/dhcp3/dhclient-exit-hooks.d "$@"; then
        exit_status=$?
    fi

    # notify dhcdbd on success
    if [ -n "${dhc_dbus}" -a $exit_status -eq 0 ]; then
        /usr/bin/dbus-send \
            --system \
            --dest=com.redhat.dhcp \
            --type=method_call \
            /com/redhat/dhcp/$interface \
            com.redhat.dhcp.set \
            'string:'"`env | /bin/egrep -v '^(PATH|SHLVL|_|PWD|dhc_dbus)\='`";
    fi

    exit $exit_status
}

set_hostname() {
    local current_hostname=$(hostname)
    if [ -z "$current_hostname" -o "$current_hostname" = "(none)" ]; then
        hostname "$new_host_name"
    fi
}

if [ -n "$new_broadcast_address" ]; then
    new_broadcast_arg="broadcast $new_broadcast_address"
fi
if [ -n "$old_broadcast_address" ]; then
    old_broadcast_arg="broadcast $old_broadcast_address"
fi
if [ -n "$new_subnet_mask" ]; then
    new_subnet_arg="netmask $new_subnet_mask"
fi
if [ -n "$old_subnet_mask" ]; then
    old_subnet_arg="netmask $old_subnet_mask"
fi
if [ -n "$alias_subnet_mask" ]; then
    alias_subnet_arg="netmask $alias_subnet_mask"
fi
if [ -n "$new_interface_mtu" ]; then
    mtu_arg="mtu $new_interface_mtu"
fi
if [ -n "$IF_METRIC" ]; then
    metric_arg="metric $IF_METRIC"	# interfaces(5), "metric" option
fi


# The action starts here

# Invoke the local dhcp client enter hooks, if they exist.
run_hook /etc/dhcp3/dhclient-enter-hooks
run_hookdir /etc/dhcp3/dhclient-enter-hooks.d

# Execute the operation
case "$reason" in
    MEDIUM|ARPCHECK|ARPSEND)
        # Do nothing
        ;;
    PREINIT)
        # The DHCP client is requesting that an interface be
        # configured as required in order to send packets prior to
        # receiving an actual address. - dhclient-script(8)

        if [ -n "$alias_ip_address" ]; then
            # Bring down alias interface. Its routes will disappear too.
            ifconfig $interface:0- inet 0
        fi
        ifconfig $interface inet 0 up

        # We need to give the kernel some time to get the interface up.
        sleep 1
        ;;
    BOUND|RENEW|REBIND|REBOOT)

        set_hostname
        
        if [ -n "$old_ip_address" -a -n "$alias_ip_address" -a \
             "$alias_ip_address" != "$old_ip_address" ]; then
            # Possible new alias. Remove old alias.
            ifconfig $interface:0- inet 0
        fi

        if [ -n "$old_ip_address" -a \
             "$old_ip_address" != "$new_ip_address" ]; then
            # IP address changed. Bringing down the interface will delete all routes,
            # and clear the ARP cache.
            ifconfig $interface inet 0

        fi

        if [ -z "$old_ip_address" -o "$old_ip_address" != "$new_ip_address" -o \
            "$reason" = "BOUND" -o "$reason" = "REBOOT" ]; then

            ifconfig $interface inet $new_ip_address $new_subnet_arg \
                $new_broadcast_arg $mtu_arg

            for router in $new_routers; do
                route add default dev $interface gw $router $metric_arg
            done
        fi

        if [ "$new_ip_address" != "$alias_ip_address" -a -n "$alias_ip_address" ];
            then
            ifconfig $interface:0- inet 0
            ifconfig $interface:0 inet $alias_ip_address $alias_subnet_arg
            route add -host $alias_ip_address $interface:0
        fi

        make_resolv_conf

        ;;

    EXPIRE|FAIL|RELEASE|STOP)
        if [ -n "$alias_ip_address" ]; then
            # Turn off alias interface.
            ifconfig $interface:0- inet 0
        fi

        if [ -n "$old_ip_address" ]; then
            # Shut down interface, which will delete routes and clear arp cache.
            ifconfig $interface inet 0
        fi

        if [ -n "$alias_ip_address" ]; then
            ifconfig $interface:0 inet $alias_ip_address $alias_subnet_arg
            route add -host $alias_ip_address $interface:0
        fi

        ;;

    TIMEOUT)
        if [ -n "$alias_ip_address" ]; then
            ifconfig $interface:0- inet 0
        fi

        ifconfig $interface inet $new_ip_address $new_subnet_arg \
            $new_broadcast_arg $mtu_arg

        set -- $new_routers
        first_router="$1"

        if ping -q -c 1 $first_router; then
            if [ "$new_ip_address" != "$alias_ip_address" -a \
                -n "$alias_ip_address" ]; then
                ifconfig $interface:0 inet $alias_ip_address $alias_subnet_arg
                route add -host $alias_ip_address dev $interface:0
            fi
	    
	    # point to point
	    if [ "$new_subnet_mask" == "255.255.255.255" ]; then
	    	for router in $new_routers; do
	    	    route add -host $router dev $interface
	    	done
	    fi

            for router in $new_routers; do
                route add default dev $interface gw $router $metric_arg
            done

            make_resolv_conf
        else
            # Changed from 'ifconfig $interface inet 0 down' - see Debian bug #144666
            ifconfig $interface inet 0
            exit_with_hooks 2 "$@"
        fi

        ;;
esac

exit_with_hooks 0

```

---

### Post by Daiver on 2006-06-02
[QUOTE=alanphil]A workaround? :rolleyes: 

1. Setup a static IP address, connect to the network. 
2. Then setup for DHCP and issue a request for a new IP address (using the dhclient command, shown below). 

This works on my home network now. It was not working all week -- but I've been downloading Dapper updates every day, so it's a moving target. It would be interesting to see if other people can get their DHCP working following these steps. 

sudo dhclient eth0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:09:6b:60:d0:79
Sending on   LPF/eth0/00:09:6b:60:d0:79
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.104 -- renewal in 37408 seconds.[/QUOTE]

This worked!  I guess I'm good to go.  Thanks!

---

### Post by Familyguy on 2006-06-02
[http://www.ubuntuforums.org/showthread.php?t=184152]("http://www.ubuntuforums.org/showthread.php?t=184152")

Reading the above post, it seems the problem might be the Davicom ethernet adapter.
I have tried setting a static IP address and restarting dhcp and neither worked.

I think I have confirmed a problem with the Davicom adapter.
I plugged a usb to ethernet adapter in to the USB port and connected it the the router.Then in networking I activated the usb adapter and set it to use dhcp.I was then able to access the internet.:p

---

### Post by mcbane on 2006-06-02
Something that may help some people....

A lot of consumer routers (D-Link, Linksys, etc.) cannot correctly interpret the IPv6 network stack, leading to DHCP/DNS problems with Linux (and now Vista, believe it or not). That is also the reason Windows XP and prior work well, as they do not implement IPv6!

So, disable IPv6 and see if it helps. Two ways of doing it:

1. In /etc/modprobe.d/aliases, change the line

```
alias net-pf-10 ipv6
```

to

```
alias net-pf-10 off
```

Reboot!

OR.....

2. Rename the kernel module. This will only work until the next upgrade of the kernel, then you'll have to do it again

```
cd /lib/modules/`uname -r`/kernel/net/ipv6
mv ipv6.ko ipv6.ko_backup
```

Reboot!

NOTE: This may help some of you with home routers. In any case, by simplifying your network stack it will most likely lead to increased speed of browsing and DNS lookups. If it doesn't do anything for you, simply reverse the changes.

---

### Post by Familyguy on 2006-06-02
I found a solution to my problem in this post,
[http://www.ubuntuforums.org/showthread.php?t=186430]("http://www.ubuntuforums.org/showthread.php?t=186430")
It seems the tulip driver is causing a problem with the Davicom adapter.
I hope this helps some of you.

---

### Post by InsanePenguin08 on 2006-06-02
[QUOTE=Familyguy]I found a solution to my problem in this post,
[http://www.ubuntuforums.org/showthread.php?t=186430]("http://www.ubuntuforums.org/showthread.php?t=186430")
It seems the tulip driver is causing a problem with the Davicom adapter.
I hope this helps some of you.[/QUOTE]

This soultion worked for me as well, it must be the Davicom's problerm.

---

### Post by djbjrca on 2006-06-02
[QUOTE=InsanePenguin08]This soultion worked for me as well, it must be the Davicom's problerm.[/QUOTE]

IT WORKED FOR ME, TOO!

Yay.

Thank you so much.  I can now start REALLY using my ubuntu box again!

---

### Post by smallphox on 2006-06-04
Just dropped by to mention the davivon/tulip workaround which worked for me, but I see you guys already found it. Congrats to everyone and thanks to h3h timo for the fix! =D

---

