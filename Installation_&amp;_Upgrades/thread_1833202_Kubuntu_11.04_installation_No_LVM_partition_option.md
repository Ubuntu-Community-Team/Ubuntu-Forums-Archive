---
title: "Kubuntu 11.04 installation: No LVM partition option"
date: 2011-08-25
forum: Installation &amp; Upgrades
---

### Post by pchokola on 2011-08-25
I am coming from the Fedora world where everything is on one DVD and you just install it. I tried to install Kubuntu 11.04 using LVM, and I selected manual partitioning setup during the install, but there is no option for setting up LVM. Am I using the wrong version, i.e. it only works with the server edition? I saw somewhere that it may magically become available in expert mode...Is that true? Somewhere else it recommends using the alternate CD?
 
Also, maybe I am attacking this the wrong way. I want to set up a server with KDE, so what is the best method:
 
1) Install plain ubuntu, then add KDE + any server programs.
2) Install Kubuntu, then add any server programs.
3) Install Server edition, then add KDE.

---

### Post by SeijiSensei on 2011-08-25
Do you want to build a server or a desktop?

For the former, server + KDE is probably your best bet if you want to have all the obvious daemons presented to you at installation (bind, apache, db servers, etc.)  Install the server, then "sudo apt-get install kubuntu-desktop".  If you're looking for a desktop with LVM, I believe the partitioner in the alternate CD's offers that.  The downside of using a desktop version is that you'll need to install any server packages manually.

11.04 is a dicey proposition, though, especially for a server. I'd use 10.04 LTS unless there's something you really need in the 10.10+ series.  I actually prefer Kubuntu 10.10 to either 10.04 or 11.04 as a desktop distribution with my particular hardware (no KDE 4.7, though).  On a server, especially one connected over Ethernet, I'd probably stick with 10.04 LTS + kubuntu-desktop or the 10.04 alternate Kubuntu CD.  On a desktop, I'd use Kubuntu 10.10 rather than 10.04.

---

### Post by pchokola on 2011-08-26
> **SeijiSensei said:**
> Do you want to build a server or a desktop?

For the former, server + KDE is probably your best bet if you want to have all the obvious daemons presented to you at installation (bind, apache, db servers, etc.)  Install the server, then "sudo apt-get install kubuntu-desktop".  If you're looking for a desktop with LVM, I believe the partitioner in the alternate CD's offers that.  The downside of using a desktop version is that you'll need to install any server packages manually.

11.04 is a dicey proposition, though, especially for a server. I'd use 10.04 LTS unless there's something you really need in the 10.10+ series.  I actually prefer Kubuntu 10.10 to either 10.04 or 11.04 as a desktop distribution with my particular hardware (no KDE 4.7, though).  On a server, especially one connected over Ethernet, I'd probably stick with 10.04 LTS + kubuntu-desktop or the 10.04 alternate Kubuntu CD.  On a desktop, I'd use Kubuntu 10.10 rather than 10.04.

Thanks.  I kinda suspected that would be the best approach.  I just want to become familiar with Ubuntu's server offering, and only want KDE because it allows me to move around things quicker, even though I am proficient with the cli.  I have seen other recommendations of using 10.04 LTS for a server, so that with kubuntu-desktop or KDE does seem like the best bet.

---

