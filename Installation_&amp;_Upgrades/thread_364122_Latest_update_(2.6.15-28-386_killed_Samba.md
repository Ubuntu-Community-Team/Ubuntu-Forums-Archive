---
title: "Latest update (2.6.15-28-386 killed Samba"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by picker77 on 2007-02-17
Until now I've had no trouble with Ubuntu updates using Synaptic through the various kernel releases. The newest one, though, updated everything no problem EXCEPT Samba, and it appears to have killed my Samba. One Samba file refused to update and Synaptic returned this error:

[COLOR="Blue"]E: /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb: subprocess new pre-removal script returned error exit status 102[/COLOR]

So I tried again to do the update via the terminal using "update-manager -c", and it said I needed to run "apt-get install -f" first to fix a broken file. Running that command gave the following:

[COLOR="Blue"]sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/2845kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 83644 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.1 (using .../samba_3.0.22-1ubuntu3.2_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]


Now I'm wandering in the woods. My router access still works (I can get to the router and the internet) but when I go to PLACES/NETWORK SERVERS it finds my Windows Network, but there's nothing there when I open the Windows Network icon...  ???  

Apparently I have a broken file in Samba but it won't let me delete the busted file or remove/reinstall Samba. I just get the same error each time.

I'd hate to have to strip the whole thing and start over just because of one Samba file corruption. Thanks in advance for anything you can point me to.

---

### Post by picker77 on 2007-02-18
Thanks to Jory, the following seems to have worked:

cd /etc/rc2.d
sudo rm S91samba
sudo ln -s ../init.d/samba S91samba
sudo apt-get -f install


I still can't get into my Windows network, but at least I'm not getting the Synaptic "broken package" notification any more,and the updater shows no pending updates now. 

Now all I have to do is figure out how to make this thing talk to the other machines on my Windows network again.

---

### Post by andrea_wwubuforum on 2007-02-18
Hi,
I had the same problem with the file K09samba instead of your S91Samba.

After i had executed the procedure you've indicated the synaptic was ok (as you indicate) but I had the same problems with windows network.

I've solved the problem by this way:
1) in synaptic I've marked to re-install samba pakages and its related components (shearch for samba in synaptic and look what packages are installed in your system) and I've performed the samba re-installation

2)I've re-defined the workgroup and the shared parameters in system-administration-shared folders (select shared folder, properties-general windows sharing settings)

3)finally, I've make a network connection via remote server, instead of network-servers icon, choosing "windows share" as server type and performing Browse Network action.
After first connection, I reach the windows network also via network-servers icon.

I hope this way can help you...
:) 

Andrea

---

