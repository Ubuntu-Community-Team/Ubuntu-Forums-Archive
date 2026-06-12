---
title: "Dpkg interrupted, endless loop"
date: 2011-07-13
forum: Installation &amp; Upgrades
---

### Post by cj.surrusco on 2011-07-13
Hello, I was trying to install the program "NoIP" for my server (package name: noip2), and I'm getting stuck in a loop that won't allow me to install the program, or use dpkg at all. 

Basically, it gets to a part of the installation where it asks me to select a network interface, and when I choose one, it hangs up. The only way I can get out is to kill apt-get. Then when I try to use apt-get again, it tells me that dpkg was interrupted and that I need to run 'sudo dpkg --configure -a'. That just brings me back to the installation of NoIP, where it hangs up again when I choose the interface.

I have the terminal output here:

```
Welcome to SERVER-P4 SSH (Ubuntu 10.04).
Linux SERVER-P4 2.6.32-30-server #59-Ubuntu SMP Tue Mar 1 22:46:09 UTC 2011 x86_64 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to the Ubuntu Server!
 * Documentation:  http://www.ubuntu.com/server/doc

  System information as of Wed Jul 13 18:11:43 EDT 2011

  System load:  0.03               Users logged in:       0
  Usage of /:   26.5% of 14.42GB   IP address for eth1:   192.168.1.110
  Memory usage: 34%                IP address for eth0:   10.42.43.1
  Swap usage:   0%                 IP address for virbr0: 192.168.122.1
  Processes:    127

  => There is 1 zombie process.

  Graph this data and manage this system at https://landscape.canonical.com/

89 packages can be updated.
52 updates are security updates.

Last login: Thu Jun 30 22:02:05 2011 from 10.42.43.10
servio@SERVER-P4:~$ sudo apt-get upgrade
[sudo] password for servio: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
servio@SERVER-P4:~$ sudo dpkg --configure -a
Setting up libpolkit-gobject-1-0 (0.96-2ubuntu0.1) ...

Setting up libslp1 (1.2.1-7.6ubuntu0.1) ...

Setting up libpolkit-agent-1-0 (0.96-2ubuntu0.1) ...

Setting up linux-libc-dev (2.6.32-31.61) ...
Setting up logrotate (3.7.8-4ubuntu2.1) ...
Setting up libkrb5support0 (1.8.1+dfsg-2ubuntu0.9) ...

Setting up noip2 (2.1.9-3) ...

Auto configuration for Linux client of no-ip.com.

Multiple network devices have been detected.

Please select the Internet interface from this list.

By typing the number associated with it.
0	eth1
1	eth0
2	virbr0
1


```

At this point, I don't care if I don't install NoIP, but I need to be able to use dpkg to update my computer and install programs. 

Thanks in advance,

CJ

---

### Post by cj.surrusco on 2011-07-14
Found a solution.

[http://ubuntuforums.org/showthread.php?t=843690](http://ubuntuforums.org/showthread.php?t=843690)

---

