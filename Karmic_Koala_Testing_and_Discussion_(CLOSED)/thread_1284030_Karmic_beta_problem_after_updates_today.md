---
title: "Karmic beta problem after updates today"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by eekfonky on 2009-10-06
After I installed the updates today the Network Manager freezes all the time and now the GUI desktop isn't working. When I start up the computer I get the command line! Please help. I am using the beta live CD to write this, is there a command I can use to access the internet and maybe get an update to fix this?

---

### Post by kimda on 2009-10-06
You can edit the interfaces file in /etc/network/ below is an example. Change the settings.  

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.1.16
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.1.6
	dns-search yourhostingdomain.com 

then you can restart by doing: 
sudo /etc/init.d/networking restart

---

### Post by bpickel on 2009-10-06
We could manually edit the setting but..... Is this persisting for anyone else. It matter not how many times I restart. It seems however to only be my wireless connection that has gone kaplooyee

---

### Post by eekfonky on 2009-10-06
I only have a mobile broadband connection. I cannot see anything no matter how many times I restart. I only get command line. how do I restore the desktop?

---

### Post by Spc on 2009-10-06
This is an already known bug: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/444181](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/444181)

The fix is already committed, but if you don't want to wait, you can download and install new version of network manager from this PPA: [https://launchpad.net/~network-manager/+archive/trunk/+packages](https://launchpad.net/~network-manager/+archive/trunk/+packages)

It fixed the problem for me.

---

### Post by pulpo69 on 2009-10-06
how can i get my line working (without downloading anything),
because i've no line for downloads. (i'm writing this from my work).

---

### Post by Spc on 2009-10-06
I think the simplest solution would be to start your computer from LiveCD and download the updates using it, save them to a folder on the hdd, then reboot and install them.

---

### Post by Longinus00 on 2009-10-06
> **Spc said:**
> I think the simplest solution would be to start your computer from LiveCD and download the updates using it, save them to a folder on the hdd, then reboot and install them.

It's even easier to use a livecd to chroot in and apply the updates from there.

[http://ubuntuforums.org/showthread.php?t=1156240&highlight=chroot](http://ubuntuforums.org/showthread.php?t=1156240&highlight=chroot)

---

### Post by pulpo69 on 2009-10-06
i solved it for now, with two lines in /etc/network/interfaces

auto eth0

iface eth0 inet dhcp


the panel applet don't work, but now i can do the update and i hope when the
panel applet will work.

---

