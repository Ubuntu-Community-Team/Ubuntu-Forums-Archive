---
title: "VPNC on netbook remix (lynx)"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by cuby on 2010-04-09
I'm unable to configure any VPN connection under ubuntu netbook remix. There are no additional plug-ins through synaptic or software install...
How can I install network-manager-vpnc in the system?

---

### Post by repawn on 2010-04-09
I am running vpnc - you need to make sure you have Universe repos enabled first. You can do that through System -> Administration -> Software Sources

at the command line you can install what you need:

sudo apt-get update
sudo apt-get install vpnc network-manager-vpnc network-manager-vpnc-gnome

Hope that helps.

---

### Post by cuby on 2010-04-09
It installed alright, thanks :)

Now I'm unable to connect to the vpn server, I'll see what I can do with the cisco client itself. If I manage to get a connection I'll post the solution.

---

### Post by repawn on 2010-04-09
Do you have the gateway and the Group Name - after that I just needed my username and password. To be honest - the gateway I connect to is pretty old so if your cisco server is newer I am unsure what will happen.

---

### Post by cuby on 2010-04-13
Ok, I solved the thing.
As in other versions of Ubuntu, I believe that VPNC doesn't support IPSEC over TCP...
So after I followed the procedure in this previous post:

[http://ubuntuforums.org/showthread.php?p=8223820#post8223820](http://ubuntuforums.org/showthread.php?p=8223820#post8223820) 

The necessary modules where installed by the cisco client and...
It worked :)

---

### Post by Miguel on 2010-04-13
It's actually possible and relatively easy to build vpnc with OpenSSL support. This is not enabled by default because distributing such a binary would violate the GPL. Enabling this only involves downloading the source package, uncommenting one line in the makefile and building the package. This may sound complex, but only involves three apt-get commands and editing a single file.

Have a look here: [http://blog.fekw.de/2008/07/02/kubuntu-howto-build-vpnc-with-ssl-support/](http://blog.fekw.de/2008/07/02/kubuntu-howto-build-vpnc-with-ssl-support/)

If you get any errors while building vpnc, you may want to issue "apt-get build-dep vpnc", but this may be covered when you download the source. Please note that you may need to "hold" vpnc to prevent it being "upgraded" to an ssl-less version.

---

