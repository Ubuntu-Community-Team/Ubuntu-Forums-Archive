---
title: "Ubuntu 17.10 Beta 2 server and no dns"
date: 2017-10-19
forum: Installation &amp; Upgrades
---

### Post by jbruyet on 2017-10-19
Hey all I just installed Ubuntu 17.10 Beta 2 server with a static address and DNS isn't working. I can ping network addresses but I can't resolve the addresses. 

When I did the installation I configured a static address for the server. I've tried reinstalling the server a couple of times with two different ISO images but no joy. Googling this issue hasn't produced anything useful because the instructions are for using the GUI. 

Cat /etc/resolv.conf gives me this: 

```
jobee@NeDi:~$ cat /etc/resolv.conf
# This file is managed by man:systemd-resolved(8). Do not edit.
#
# 127.0.0.53 is the systemd-resolved stub resolver.
# run "systemd-resolve --status" to see details about the actual nameservers.
nameserver 127.0.0.53

jobee@NeDi:~$ 
```

Cat /etc/network/interfaces gives me this:

```
jobee@NeDi:~$ cat /etc/network/interfaces
# dns-* options are implemented by the resolvconf package, if installed

auto ens160
iface ens160 inet static

address 192.168.2.32
netmask 255.255.255.0
gateway 192.168.2.1

dns-nameservers 192.168.2.90 192.168.1.26 192.168.3.28
dns-search link.com
jobee@NeDi:~$ 
```

Again, I can ping network addresses but I can't resolve any of them. This is the first time I've used a new version of Ubuntu server. All other times I manually changed interfaces and resolv.conf and life was fine.

My question -- how do I configure  a static address and still have DNS work for me? 

Thanks,

Joe B

---

### Post by Kirboosy on 2017-10-20
Welcome to the forums! :D

You installed Beta 2 last night, but you might want to reinstall again since 17.10 has been officially released into the wild!

I'm not sure if there is some weird issue with having to many DNS servers. Try removing one of the DNS servers from your configuration.

If that still doesn't fix it then try to set it to Google's DNS servers temporarily.
```
dns-nameservers 8.8.8.8 8.8.4.4
```

```
sudo systemctl restart networking
```

Hope that helps!
~Caboose

---

### Post by clifford64 on 2017-10-20
I have done a complete clean install of 17.10. The first thing I did was set a static address

auto ens160
iface ens160 inet static
              address x.x.x.x
              netmask x.x.x.x
              ...
              dns-nameservers 8.8.8.8 8.8.4.4


I can ping the addresses just fine, but I cannot ping domain names. DNS is not working. I have restarted the networking service and I have restarted the VM. Once I add a nameserver to /etc/resolv.conf of 8.8.8.8 I can resolve just fine, but this gets wiped out on restarts. What should I do? This is a completely fresh install and the only thing I have done is set static IP, but DNS does not work.

---

### Post by Kirboosy on 2017-10-20
[FONT=arial][SIZE=2]I totally had a brain fart. Sorry! Did you disable Network Manager?

```
sudo systemctl stop NetworkManager.service[/SIZE][/FONT][FONT=arial]sudo systemctl disable NetworkManager.service
```

Make sure you have your gateway in the config then restart networking using command posted earlier. Network Manager doesn't get along with static IPs.  [/FONT]

---

### Post by xiphosurus on 2017-10-23
had the same problem, and found it was due to broken symlink. fixed it using these commands in terminal:

> sudo rm /etc/resolv.conf
sudo ln -s /run/resolvconf/resolv.conf /etc/resolv.conf
systemctl restart resolvconf

source: [https://askubuntu.com/questions/966870/dns-not-working-after-upgrade-17-04-to-17-10](https://askubuntu.com/questions/966870/dns-not-working-after-upgrade-17-04-to-17-10)

---

