---
title: "Resolving DNS and more"
date: 2004-12-28
forum: Installation &amp; Upgrades
---

### Post by pupsa on 2004-12-28
Hi!

I am new to Ubuntu and Linux in general.
After few tries in installing Ubuntu I managed to have it running.
Here is a list of problems I found and how I fixed them. They might not be top FAQ but they might help some other newbie like me and save them some time.

1) Normal CD install failed (hang) when installed network with DHCP. I got a blue screen and a white bottom bar

Solved. Started the installation in "expert" mode ( where there is F1 for help or Enter to boot, I typed "expert" then Enter ). When asked for DHCP I said "no" and typed my network static IP address 192.168.10.103. sub mask 255.255.255.0 my gateway 192.168.10.200 my ISP DNS IP 196.25.1.11 and 196.43.1.11 and for good measure also my router address 192.168.10.200
The installation then continued this time.

2) After installation, during the loading of the system, I got stuck on the synchronization of the time on the ntp.ubuntu.org the machine just hang there.

Solved. One way is to press Cntr-C when is stuck there, so can continue with the loading. Another way was to eliminate the clock syncro altogether.
I went to the root command prompt (root terminal) and typed:
sudo update-rc.d -f ntpdate remove <Enter>
Now it is gone.

3) In FireFox all I got was a Resolving address... error and no page to display.
Solved. I went to edit the file /etc/resolv.conf file as "root" and now looks like this:
search 192.168.10.200           " my router ADSL IP "
nameserver 196.25.1.11         " my ISP DNS IP "
nameserver 196.43.1.11                   "
nameserver 192.168.10.200    " my router ADSL IP"

I also did the IPV6 disabling as per others suggested:
type about:config on the address bar of firefox
go down to network.dns.disableIPv6 and set it to "true"
After this I restart firefox and I can now browse.

The only problem looks like that when i reboot the /etc/resolv.conf file is back to the wrong settings and I cannot browse.

Maybe someone can help her and tell me how to permanently save the changes

ciao

---

### Post by nikopol on 2005-01-01
[http://www.ubuntuforums.org/showthread.php?t=6704&highlight=DNS](http://www.ubuntuforums.org/showthread.php?t=6704&highlight=DNS)

Does this help? If not, I've found that switching to static IP sometimes works. Worth a try I guess

---

### Post by arctic on 2005-01-01
a simple way is the following:

open a terminal and type "sudo gedit /etc/resolv.conf"
now enter your password. once gedit displays the resolv.conf file, edit it. add some valid dns-entries for it like

nameserver 217.237.150.225

now save the document and exit gedit. when you are back at the terminal, type "sudo chattr +i /etc/resolv.conf". your resolv.conf file will be locked now so that it cannot be overwritten. that's all. :)

---

### Post by AndyGates on 2005-01-24
> sudo chattr +i /etc/resolv.conf
chattr: Inappropriate ioctl for device while reading flags on /etc/resolv.conf

Um..?

---

