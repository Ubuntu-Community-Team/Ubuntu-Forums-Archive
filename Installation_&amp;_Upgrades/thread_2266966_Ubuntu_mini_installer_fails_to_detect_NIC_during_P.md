---
title: "Ubuntu mini installer fails to detect NIC during PXE/kickstart install"
date: 2015-02-26
forum: Installation &amp; Upgrades
---

### Post by nesretep2 on 2015-02-26
I am trying to get a PXEboot/kickstart installation of Ubuntu 14.04 LTS working for a large scale deployment of Ubuntu at work.  I can get my test station to PXEboot, but when the debian-installer begins the keyboard doesn't work and it stops at a screen the reads:

[ATTACH=CONFIG]260231[/ATTACH]

```
[CENTER][SIZE=3]No network interfaces detected[/SIZE][/CENTER]
[SIZE=3]No network interfaces were found.  The installation was unable to find a network device.
You may need to load a specific module for your network card, if you have one.  For this, go back to the network hardware detection step.[/SIZE]
```

If you try to select the option to either "Go Back" or "Continue" using the keyboard, nothing happens.  The keyboard is completely unresponsive.  You can't even turn on NumLock or CapsLock even though it work prior to the installer starting.  I know the NIC works because it just booted and began reading my kickstart file from the network to even get this far.  

Here is my kickstart:
```
# System language
lang en_US


#language modules to install
langsupport en_US


#System keyboard
keyboard us


#System mouse
mouse


# System timezone
timezone America/Denver --isUtc --ntpservers=ntp.cs.byu.edu,ntp2.cs.byu.edu


# Root password
rootpw --iscrypted $6$88zLS9gl6K7/Mwlx$WMVU3Ub1ItFygibQRv9KBx5fOZCLzS1Y9odcebO4CEhKTBXmaMD78cTjD2igYlL9y3F3mAhxctCfFjAWDA6ka/


# Reboot after installation
reboot


# Install Ubuntu instead of doing an update/upgrade
install


# Use HTTP installation media
#nfs --server=something --dir=the path to the stuff  //try this?
url --url http://mirrors.cs.byu.edu/ubuntu/releases/14.04/x86_64/os/isolinux


# Don't run firstboot after installation
firstboot --disable
ignoredisk --only-use=sda


# Clear the Master Boot Record
zerombr yes


# Clear all partitions from the disk
clearpart --all --initlabel


# Partitioning Information
part /boot --fstype="ext4" --ondisk=sda --size=800
part pv.01 --fstype="lvmpv" --ondisk=sda --size=1 --grow
volgroup vg_root pv.01
logvol swap  --fstype="swap" --size=7936 --name=swap --vgname=vg_root
logvol / --fstype=ext4 --fsoptions="noatime,discard" --vgname=vg_root --size=2000 --grow --name=lv_root


# Network information
# Use DHCP networking, specify link settings
network  --bootproto=dhcp --device=eth0 --ipv6=auto --activatecd


#System authorization information (Use Kerberos for auth and LDAP for user info)
auth --enablekrb5 --krb5realm=CS.BYU.EDU --krb5kdc=kerberos.cs.byu.edu --krb5adminserver=kerberos.cs.byu.edu --enableldap --ldapserver=ldap.cs.byu.edu --ldapbasedn=dc=cs,dc=byu,dc=edu --enablecache


#SELinux configuration
selinux --disabled


#Services to run (or not run) at startup
#Syntax: services --enabled a,b,c --disabled d,e,f
#sservices --enabled="chronyd" --disabled="bluetooth,ip6tables,pcscd"


# X Window system Configuration information
xconfig --startxonboot

%packages
@ubuntu-desktop
%end

```
If you need to see anything else let me know.  Any and all help is appreciated, as I am totally stuck on this right now.  Thanks!

---

