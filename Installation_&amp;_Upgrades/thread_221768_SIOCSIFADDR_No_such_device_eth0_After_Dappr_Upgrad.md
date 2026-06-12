---
title: "SIOCSIFADDR: No such device eth0 After Dappr Upgrade"
date: 2006-07-24
forum: Installation &amp; Upgrades
---

### Post by Sir_Brizz on 2006-07-24
Well, I did a dist-upgrade to Dapper about two months ago (or whenever Dapper finally came out) and my NIC card wouldn't come up. There were absolutely zero configuration differences between the two installations, the only difference was the kernel (in fact, dropping back to the Breezy kernel worked fine). However, I was getting sick of the newer kernels not working, so today I dug in and figure out how to fix the problem.

The solution was not cool.

First, the diagnosis was that ifconfig would not show eth0 at all. lspci and dmesg reported no errors, really, and obviously modprobe was useless. ifup reported some strange errors like:

SIOCSIFADDR: No such device eth0
eth0: ERROR while getting interface flags: No such device

Google didn't find anything useful on any search, until I came across this dude's blog who was getting an identical error in a totally different situation.

[http://www.pletscher.org/blog/?p=29](http://www.pletscher.org/blog/?p=29)

WOOHOO!

I ran 'ifconfig -a' and it found an eth1 for some reason (though 'ifup eth1' also had no effect) which had a MAC address in it. I hopped into '/etc/iftab', changed the MAC address on eth0 to the MAC that was attached to eth1 in ifconfig and rebooted. VOILA! Network up and running!

Hope this helps someone.

---

### Post by VstarAl on 2006-10-11
Thank you! :)  It helped me.  I created an Ubuntu server on a Dell GX1.  I wanted to get more performance, so I moved the hard drive to a Dell GX150.  After that I could not connect to my network.  If I ran the Ubuntu installation CD, I was able to connect.  So after following the solution you found, I was able to connect.

---

### Post by akame on 2006-10-24
Thanks - you saved me a huge headache. I too just upgraded to Dapper and BAM - no network. Your solution worked like a treat.

---

### Post by GrrFkIT on 2006-11-20
Thanks very much for your posting - it fixed my problem, which was slightly different to yours:

* Install Ubuntu server 6.1 on a clean machine
* Install and configure VMWare Server 
* Install and configure a new, fresh Ubuntu 6.1 Server in a VMWare virtual machine. 
* Test. Works. (Yay!)
* Shut the VMWare machine down
* Copy the VM files into a new directory, and creat a new VM machine.
* NO networking! SIOCSIFADDR Error!
* Search Google, swear a lot.
* Find your post
* Happy camper again!

Thanks to [this guy]("http://www.howtoforge.com/ubuntu_vmware_server") for the VMWare stuff.

---

### Post by Czar on 2007-02-17
> **Sir_Brizz said:**
> I ran 'ifconfig -a' and it found an eth1 for some reason (though 'ifup eth1' also had no effect) which had a MAC address in it. I hopped into '/etc/iftab', changed the MAC address on eth0 to the MAC that was attached to eth1 in ifconfig and rebooted. VOILA! Network up and running!

Hope this helps someone.

Indeed and thanks for the post Sir_Brizz.  Your *tip* helped configure ubuntu:edgy ethernet (running in a Windows VMPlayer session.)

---

### Post by saycat on 2007-06-11
This suggestion was spot on. This is the sequence of steps - from the creation, detection, debugging and resolution of the problem:
[LIST]
[*]When I first created a VMWare image and installed Ubuntu on it, the installation must've setup **/etc/iftab** Subsequently I made a replica of the origial image simply copying all the VMware files
[*]I did not ever shutdown and restart my VMs. As such each VM when started separately seemed to work fine.
[*]However, when started together of the 2 VMs whichever was started first would have a working networking system. The other would not
[*]Using vmnetsniffer.exe I found that when I pinged my host from the working VM, the pings came through ok but on the other one there were ARP request replies - no ICMPs and for although the incoming IP addresses were as expected, it always seemed to be from a MAC address I had no clue about
[*]Suspecting a possible MAC address collision (although VMware vmx files seemed to have perfectly different MAC addresses in the respective **.vmx** files) I shutdown and restarted each VM. Now neither of the VMs would start eth0. I started getting SIOCSIFADDR: ERROR no such device eth0 errors from both VMs when I tried to run **/etc/init.d/networking restart**
[*]Finally realizing from this post that although VMWare was providing a new MAC address Ubuntu was possibly sending the same one (and hence an incorrect one with respect to the real VM provided MAC address) I updated by /etc/iftab and Voila - my problem too was fixed[/LIST]Thanks, Saycat

---

### Post by mjukr on 2007-08-26
Thanks! Solved my problem!

---

### Post by ryanl on 2007-08-28
for hours I have been trying to solve this issue! THANK YOU!!! I found my NIC under eth2 and had to update my /etc/network/interfaces file using pico /etc/network/interfaces and update the old eth1 that used to be to eth2.

All this happened when I needed to replace my mobo, it was the same one but had a different NIC / therefore a different MAC address.

Thank you again!:)

---

### Post by jsa13 on 2007-09-21
SOLVED  - Remove the entry in /etc/iftab for ethX and it will be recreated on next restart.  That will fix the issue and you can now use ethX again.  Iftab tracks interfaces by MAC address so they do not jump around as cards are added or removed.

---

### Post by zefram144 on 2007-10-25
I got the exact same problem with Debian. Maybe somebody will find this helpful:

The problem started after I cloned a virtualbox os, and gave the box a new mac.

There is no /etc/iftab file anywhere, so I looked for all files in /etc containing the old mac with a "rgrep -i 08:00 *"

The only file that contained the mac was: /etc/udev/rules.d/z25_persistent-net.rules

Problem resolved after deleting the file, and rebooting.

---

### Post by nicko7i on 2007-11-18
Gutsy also has no /etc/iftab.  I disabled this behavior in two steps:
(1) Edit /etc/udev//rules.d/70-persistent-net.rules
(1.1) comment out or delete all the lines beginning with SUBSYSTEM=="net"
(2) Edit /etc/udev/rules.d/75-persistent-net-generator.rules
(2.1) comment out or delete these two lines:
  ACTION=="add", SUBSYSTEM=="net", KERNEL=="eth*|ath*|wlan*|ra*|sta*" \
        NAME!="?*", DRIVERS=="?*", GOTO="persistent_net_generator_do"

Deleting these two files would probably work, but I haven't tried that myself.

This solved a vexing problem with vmware virtual machines, where eth0 would "mysteriously" disappear and then later re-appear.

---

### Post by framp_No2 on 2008-01-23
Frankly I'm used to use SuSE but I'm keen to get familiar with other Linux OS so I  used VMWare to install ubuntu Gutsy and got the same problems when I cloned the VMWare image.
I just modified /etc/udev//rules.d/70-persistent-net.rules, deleted the definitions for eth0 and changed the definitions for eth1 to use eth0. That's it ;-)

---

### Post by benow on 2008-02-04
Awesome.  <blink>*THANKS*</blink>.  This had been annoying me for a while.  Still shows up in 7.10 :(

---

### Post by TigerWolf on 2008-03-06
Thanks for the help.
I did something slightly different and did ifconfig -a and found eth1 and then set a static ip for eth1

---

### Post by grittyminder on 2008-03-27
I just want to add my thank you too. This quick fix saved my bacon ;)

---

### Post by kcnnc on 2008-05-12
Thanks for this info! Works in Hardy with coping vmware files to a new folder.

---

