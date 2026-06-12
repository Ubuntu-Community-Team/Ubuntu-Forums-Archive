---
title: "nvidia-glx installation not possible to linux-image-2.6.17-10 ?!?! BUG?"
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by bernstein on 2007-01-18
I've just installed edy to my laptop over internet, added universe & multiverse repos to sources-list and wanted to install the nvidia driver. but it refuses to work with the latest generic linux kernel.... although i have an older edgy installation with the same nvidia driver running on this very kernel on this very laptop !!!! how come this is possible????

if i want to install it both at once (as i did exactly 2 month ago...) apt wants to install the 386 linux kernel and restricted modules ... but when i first install the restricted modules nvidia-glx installs as supposed to... however nvidia-glx-config refuses to enable !!! 

why?? anyone??? how do i fix this?? please!!!

here's the console output (in german) though anyone using apt-get can see that there are ZERO errors... until the point where i want to activate the driver....

```

bernstein@tablet:~$ uname -a
Linux tablet 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux
bernstein@tablet:~$ sudo apt-get install linux-restricted-modules-`uname -r`
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Reading state information... Fertig
Die folgenden zusätzlichen Pakete werden installiert:
  nvidia-kernel-common
Vorgeschlagene Pakete:
  nvidia-glx nvidia-glx-legacy avm-fritz-firmware-2.6.17-10
Die folgenden NEUEN Pakete werden installiert:
  linux-restricted-modules-2.6.17-10-generic nvidia-kernel-common
0 aktualisiert, 2 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
Es müssen noch 0B von 7687kB Archiven geholt werden.
Nach dem Auspacken werden 21.0MB Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren [J/n]? j
Wähle vormals abgewähltes Paket nvidia-kernel-common.
(Lese Datenbank ... 92906 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke nvidia-kernel-common (aus .../nvidia-kernel-common_20051028+1ubuntu7_all.deb) ...
Wähle vormals abgewähltes Paket linux-restricted-modules-2.6.17-10-generic.
Entpacke linux-restricted-modules-2.6.17-10-generic (aus .../linux-restricted-modules-2.6.17-10-generic_2.6.17.7-10.1_i386.deb) ...
Richte nvidia-kernel-common ein (20051028+1ubuntu7) ...

Richte linux-restricted-modules-2.6.17-10-generic ein (2.6.17.7-10.1) ...

bernstein@tablet:~$ sudo apt-get install nvidia-glx
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Reading state information... Fertig
Vorgeschlagene Pakete:
  nvidia-kernel-source
Die folgenden NEUEN Pakete werden installiert:
  nvidia-glx
0 aktualisiert, 1 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
Es müssen noch 0B von 4066kB Archiven geholt werden.
Nach dem Auspacken werden 12.6MB Plattenplatz zusätzlich benutzt.
Wähle vormals abgewähltes Paket nvidia-glx.
(Lese Datenbank ... 93122 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke nvidia-glx (aus .../nvidia-glx_1.0.8776+2.6.17.7-10.1_i386.deb) ...
Richte nvidia-glx ein (1.0.8776+2.6.17.7-10.1) ...

bernstein@tablet:~$ sudo nvidia-glx-config enable
Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.
bernstein@tablet:~$ 

```

---

### Post by bernstein on 2007-01-18
ok i've been able to "fix" this.... actually its dead easy :

```
dpkg-reconfigure xserver-xorg
```

so it should be possible to just change the xorg.conf  graphics driver to nvidia and adding the glx in modules section.....

TO ANYONE IN UBUNTU STAFF : this seems to be a SERIOUS packaging error, any novice linux user would not be able to fix this, as they just copy+paste code.... how could this not get noticed before??
it can NOT be that apt automatically changes the kernel from generic to 386 for nothing !

so my advice if your apt wants to change kernel is to do as i did in the post above....

---

### Post by HotFoot on 2007-01-18
Thanks for your posts.  I was having the same problem since I've changed from a 32 to 64-bit version of Ubuntu on my desktop.  That one step that was missing from the online help documentation was all I needed to make my Nvidia card work. :D

---

### Post by Amancio on 2007-01-27
I would be the aforementioned novice linux user encountering the error.  Where do I input bernstein's line of code?  I'm running Ubuntu 6.10.  Not sure what other info you'd need.

Thanks

---

### Post by bernstein on 2007-01-28
> **Amancio said:**
> I would be the aforementioned novice linux user encountering the error.  Where do I input bernstein's line of code?  I'm running Ubuntu 6.10.  Not sure what other info you'd need.

Thanks
ok just start a terminal/shell and enter those four lines: (each takes some time to run)
```
sudo apt-get install linux-restricted-modules-`uname -r`
``````
sudo apt-get install nvidia-glx
``````
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
``````
sudo dpkg-reconfigure xserver-xorg
```the last one will ask you a few questions about your screen/graphiccard. here you must choose on the first question the nvidia driver. for the rest just letting the default values did the trick for me, although you might have to select/add your screen resolution on some of the later questions.
now hit ctrl-alt-del or just reboot
note: if something goes wrong and you're stuck at a shell afterwards just run:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
``````
sudo reboot
```this will restore your old settings

---

### Post by tooCanad on 2007-01-28
Thanks for this. I found the post earlier and it simplified the install greatly. Then I screwed a bunch of stuff up and reinstalled the OS. It took me a while to find your post again.

Now that I've found it the code is now a hard copy for future mess ups. 

Thanks again.

TC

---

