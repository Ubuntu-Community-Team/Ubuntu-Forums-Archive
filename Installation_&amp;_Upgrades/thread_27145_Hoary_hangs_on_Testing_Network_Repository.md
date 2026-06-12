---
title: "Hoary hangs on Testing Network Repository"
date: 2005-04-15
forum: Installation &amp; Upgrades
---

### Post by elgrego on 2005-04-15
Hi,

Im installing Ubuntu on VMWare 5.0 on my xp workstation at work.
Everything is fine until reaching "Configuring apt" - > "Testing network Repository"
I have done the same installation at home with the only differense network wice is that we use a proxy-server at work.
Can this affect the installation when testing the network repository?
I have tried waiting for a timeout, but it did not happen during the night so now Im fresh out of ideas.

Any help appreciated.


Regards // Greger

---

### Post by csanchezotero on 2005-04-15
I had this last night I believe when installing Kubuntu.  It kept hanging at 25% when configuring apt during install. I tried four times.

The only thing I can think of is that
a) Its a dodgy CD.  Not sure on this as I got past the apt stage the first time round but had to install again 'cause of a grub error.

b) The forums got updated last night (moved to a new server I think).  Would this have anything to do with it?  If the network is setup and working will it configure apt via the net.  Point a) was done before the move but I am not sure if this is a coincidence. 

I will try again 2night as I am at work at the mo.

---

### Post by arctic on 2005-04-17
take a look here. :)
[http://ubuntuforums.org/showthread.php?p=136367#post136367](http://ubuntuforums.org/showthread.php?p=136367#post136367)

---

### Post by nikos on 2005-05-04
Hello, 

I have the same Problem while installing Hoary under VMWare 5.0/WinXP Pro.

System hangs on "Testing network Repository" at 50%.
This happens during the Configuration of apt.

I do the installation in German, so the Message is: "Das Netzwerk Verzeichnis Testen".

bye
Niko

---

### Post by odyssey on 2005-06-06
It's trying to connect to the network/internet and cannot due to <whatever>. Disconnect the network cable or disable the virtual NIC.
 
You can always run *sudo apt-get update* once you have configured your network settings.

---

### Post by wate on 2005-07-26
Hello,

I had the same problem. I just turned off my software firewall (agnitium outpost) in WinXP and Installation began to proceed... (toward new problems :)

best wishes, matjaz

---

