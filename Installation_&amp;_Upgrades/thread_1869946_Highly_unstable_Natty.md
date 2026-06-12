---
title: "Highly unstable Natty"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by Unterseeboot_234 on 2011-10-26
Not sure what to do... I have always loved Ubuntu until I added wireless to an existing Natty that had ethernet cables. The HowTos for Ubuntu wireless all used to say 'build ndswrapper for your platform'. And now I see the wireless docs saying natty comes with ndiswrapper pre-installed.

ndiswrapper does NOT work on the AMD64 Phenom-II hexacore. Period. I would doubt it would work with the Bulldozer octo either.

I'm trying to make an AMD64 single-core run any version of Ubuntu.

Maybe I have a dual-ndiswrapper conflict? A hard drive format and Re-install with LiveCD and the same wireless network selection is still there. You can not boot LiveCD to run Ubuntu from the CD drive.

Some installed programs stopped working. A constant dialogue box keeps coming up saying a Serious System error occurred. Send Error Report?

The programs that won't launch from the menus do show an error report when launched from terminal. Most errors have to do with python.

if ran the following command (Souftware-center won't launch at all and the USserver does not have Natty packages for download)
```
sudo apt-get update && sudo apt-get upgrade
```

I get the following errors

```
Errors were encountered while processing:
 software-center
 python-problem-report
 python-apport
 apport
 apport-gtk
 gwibber-service
 gwibber
 gwibber-service-facebook
 gwibber-service-identica
 gwibber-service-twitter
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

How???? do I kill ndiswrapper? Or, should I blame ndiswrapper?

---

### Post by madjr on 2011-10-26
natty has always been pretty unstable for me too, why dont you try 11.10 on an cd/usb stick and see if it works better?

---

### Post by Unterseeboot_234 on 2011-10-26
Thanks, MadJR

At least 11.10 does let me boot LiveCD (I'm using it now). Natty dims the 'Try Ubuntu' button after I reinstalled, booted HD version, restart to LiveCD. Odd experience for me. I verified that Natty LiveCD won't work for me. I suspect because I built ndiswrapper and installed it that I have a conflict in Natty's version of ndiswrapper.

I'm blanking my hard drive, trying 11.10 install, and will re-post my experiences.

---

### Post by Unterseeboot_234 on 2011-10-27
Oneiric ( "of or pertaining to dreams" ) Ocelot was a smooth install on a blanked hard drive. Because I had the USB-wifi adapter plugged in, wifi was completely transparent to ndiswrapper, no manufacturer drivers needed.

The only difficulty was locating the 'real' oracle/sun-java to install NetBeans. So much politics, but the hardware makers are paying Microsoft to use Android. The law courts will have to decide how to divide up the java pie and who gets to use java. Oracle java-netbeans bundle will NOT install because it smells the Iced-tea java plug-in. No sun-java in the Ocelot repositories.

I will probably try installing Ocelot on our hexacore AMD64 sometime later. wifi works on the Windows side, but not the ndiswrapper that I built for the Natty boot.

---

### Post by madjr on 2011-10-27
you could try this for java:

[http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)

---

### Post by Unterseeboot_234 on 2011-10-27
I did use that link to install sun-jdk6-jre64. 
```
http://ppa.launchpad.net/ferramroberto/java/ubuntu
```

roberto's ppa works as advertised, not the one listed in the discussed, linked blog. The download puts java into the ubuntu File System. You can then run / compile / appletviewer on the desktop and from the Terminal.

From there, download oracle-jdk7.1. Installed into a Home folder (for programming). Download the NetBeans IDE, installed into a Home folder.

The oracle-netbeans/jdk bundle will NOT work in Linux. More and more, Oracle treats Linux as a stepchild while it tries to encircle Microsoft and gut Google.

IcedTea is fine for web pages.

---

