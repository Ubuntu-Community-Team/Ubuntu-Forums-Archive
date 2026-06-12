---
title: "need help with installing new printer"
date: 2021-09-29
forum: Installation &amp; Upgrades
---

### Post by teabutterfly2047 on 2021-09-29
Hello fellow Ubunters,

I'm using xubuntu. Here are the specifics:

```
utilisateur@utilisateur-TravelMate-P253:~$ hostnamectl
   Static hostname: utilisateur-TravelMate-P253
         Icon name: computer-laptop
           Chassis: laptop
        Machine ID: 46037e7c1388fbb5aa7bdbe0525587dd
           Boot ID: 4a76e79c9e2449f381a11cf5b717078c
  Operating System: Ubuntu 18.04.5 LTS
            Kernel: Linux 4.15.0-122-generic
      Architecture: x86-64
```

Anyways, I just bought a brand new printer, it is an HP 6000 series Envy all in one printer/scanner.

The printer is turned ON and connected to the laptop by a type B  USB cable.

I followed the manufacturer's instructions and dowloaded the HPLIP software for linux (the tar.gz package). I upgraded the HPLIP to the latest version using the Synaptic software. I used the visually graphic version of Synaptic, though I suspect a sudo synaptic command in a terminal might be more effective. Anyways, I followed the step by step instructions of the help section of Synaptic and I suspect there was a problem with the HPLIP upgrade and would love to get help troubleshooting the situation through commandsz typed in a terminal.

After the HPLIP software upgrade and the installation of the printer, I tried to print a test page but got an error message. No test page was printed. I tried to scan a page, and my simpleScan software doesn't recongize my new printer for some reason (there's a missing link soemwhere, I suspect).

Lastly, in a terminal, I tried the lprm and the lpq commands and the name of my former printer appeared, instead of the new one.

> lprm

> lpq

so here am I stuck with this new printer. Thank you kindly for your help.

I checked and rechecked, can't find what's wrong. This is driving me nuts. Please HELP. ](*,)

---

### Post by TheFu on 2021-09-29
[https://docs.xubuntu.org/1804/user/C/printing-scanning.html](https://docs.xubuntu.org/1804/user/C/printing-scanning.html) does that not work?

---

### Post by ajgreeny on 2021-09-29
Just out of interest, what output do you get in terminal when running command ***driverless list***?

---

### Post by teabutterfly2047 on 2021-09-29
Thanks for replying.

No, I've been on this webpage before and followed the step by step instructions. It still does NOT work.

I must say my system is in French and those instructions are in English. At some point, it is instructed to do the following:

> Select your printer and click **Forward**

the thing is there is no French equivalent to "forward" in French ythat I could identify. This may be the missing link. Talk about being lost in translation!

I'll come back here with screenshots from my desktop, maybe it will be clearer.

---

### Post by TheFu on 2021-09-29
**ippfind** was the most useful, but only when avahi was running. I had to enable avahi, wait 30sec, then run ippfind to get a list of printers and scanners. Generally, I disable and mask avahi.

great stuff ajgreny!  Taught me something new.
I'd been using system-config-printer  - which is probably the GUI app in most flavors.

---

### Post by teabutterfly2047 on 2021-09-29
@TheFu never heard of avahi, don't know if I have it in my system.
How do i enable/disable avahi? Thanks

---

### Post by TheFu on 2021-09-29
Please don't use images for text.  You can copy/paste the text alone.  500B vs 20KB - same information.

The page where you ran sudo didn't have correct commands.  Details matter.  

Why was "driverless list!" used?  That was not the command requested.

Here's what I get from the correct command:
```
$ **driverless list**
DEBUG: Started ippfind (PID 417966)
DEBUG: Started post-processing (PID 417967)
ippfind: Unable to use Bonjour: Daemon not running
DEBUG: PID 417967 (Post-processing) exited with no errors.
DEBUG: PID 417966 (ippfind) stopped with status 2!
```

and with ippfind:
```
$ **ippfind** 
ippfind: Unable to use Bonjour: Daemon not running
```

Bonjour is the Apple name of the service similar to ZeroConf.  Apple has been running the "CUPS" project for years.  On Linux, the ZeroConf protocol is implemented by avahi.  I think all desktop versions of Ubuntu install and enable it by default.  

If I enable avahi, then run those commands again ...
```
$ driverless list
DEBUG: Started ippfind (PID 12065)
DEBUG: Started post-processing (PID 12066)
DEBUG: PID 12065 (ippfind) stopped with status 1!
DEBUG: PID 12066 (Post-processing) exited with no errors.

$ ippfind 
ipp://romulus.local:631/printers/BRFAX
ipp://romulus.local:631/printers/MFC240C
ipp://romulus.local:631/printers/Samsung_ML-1740
ipp://romulus.local:631/classes/laser
ipp://romulus.local:631/printers/scx4100

```
Romulus is my print server on the network.  It has a Samsung laser printer and a Brother MVC all-in-one device connected.  The romulus.local is proof that avahi is being used.  {hostname}.local is how avahi makes accessing local systems possible for people who don't run an internal DNS or modify all the /etc/hosts files on all their systems. That's a name resolution thing.

---

### Post by teabutterfly2047 on 2021-09-30
@TheFu

thanks for the detailed answer.

> Please don't use images for text.  You can copy/paste the text alone.  500B vs 20KB - same information.

OK. I must say I tried to copy/paste the text from the terminal and it didn't work (OK, I solved that, now I can copy/paste from terminal, it's no longer an issue). Plus, having Asperger's and tired eyes, I am more visually oriented. It's time for me to magnify the text here in this forum, because the font size by default is too small for me to read and then I misread the command suggested by @ajgreeny.

Of course, details matter. Please bear with me I'm burnt out and exhausted. Anyways, now that I'm fully rested and caffeinated, here is what I get :

> DEBUG: Started ippfind (PID 5141)
DEBUG: Started post-processing (PID 5142)
DEBUG: PID 5141 (ippfind) stopped with status 1!
DEBUG: PID 5142 (Post-processing) exited with no errors.



I guess I have avahi enabled by default. I didn't enable it on purpose, as I don't even know how to do that! do I enable/disable avahi through the Synaptic software?

here's what I get with ippfind

> utilisateur@utilisateur-TravelMate-P253:~$ ippfind
utilisateur@utilisateur-TravelMate-P253:~$ 




So enabling avahi seems to be the key here. I've never used avahi before, never had to. How do I enable/disable it?

any suggestions welcome.

PS: I edited all my previous posts and deleted unnecessary images.

hello there,

it's me again.

I just used 
> system-config-printer
as suggested and went to the help/debug section and followed instructions. I was told to type the following in a terminal:


> su -c 'journalctl -u cups.service --since="None" --until="2021-09-30 09:17:15"' > troubleshoot-logs.txt

then I was asked to authenticate, I entered my password and the authentication was denied as follows:
> utilisateur@utilisateur-TravelMate-P253:~$ su -c 'journalctl -u cups.service --since="None" --until="2021-09-30 09:17:15"' > troubleshoot-logs.txt
Mot de passe : 
su : Échec d'authentification
utilisateur@utilisateur-TravelMate-P253:~$ su -c 'journalctl -u cups.service --since="None" --until="2021-09-30 09:17:15"' > troubleshoot-logs.txt
Mot de passe : 
su : Échec d'authentification
utilisateur@utilisateur-TravelMate-P253:~$ 


let me translate here: "Mot de passe" means "password" in French
"Échec d'authentification" means "authentification/login failed"
could it possibly be that I don't have administrator rights on my own computer? My laptop was first set up by an ex-boyfriend... It is possible that he has an admin password different from my user/login password.

When I use, for example, this command:

> sudo synaptic

and I am asked to anthenticate, I enter my password and it works.

So now I'm doubtful: are there two different passwords? Do I have only user rights, and no admin rights?

I went through the whole help/debug process and ended with a message saying "sorry! there is no answer/solution to your problem, you may report a bug". :(

Any input/advice welcome here.

---

### Post by ajgreeny on 2021-09-30
What output do you see from command ***groups***

---

### Post by teabutterfly2047 on 2021-09-30
@ajgreeny

command groups:
> utilisateur@utilisateur-TravelMate-P253:~$ groups
utilisateur adm cdrom sudo audio dip video plugdev fuse lpadmin netdev scanner sambashare divers
utilisateur@utilisateur-TravelMate-P253:~$ 


utilisateur = user
divers = miscellanea

---

### Post by T6&amp;sfpER35% on 2021-09-30
if it's any conciliation , i could never get my printer/scanner to work in over a hundred years .
tried everything except making love to it .
sold the damn thing eventually .

life's so much simpler now 

):P

---

### Post by TheFu on 2021-09-30
> **teabutterfly2047 said:**
> this situation is a real mystery...

*su -* commands don't work on Ubuntu without some addition setup which is discouraged.
You are a member of the adm and sudo groups.  YOU ARE and admin.

Avahi is a daemon. There's no GUI.  In general, just having the daemon running is sufficient for it to work.
To see the status for **any** OS daemon, use
```
systemctl status avahi
```
Usually, there will be a journalctl command to see more details. Sadly, the output with those details is usually cryptic.  Take the error message, and put that into a google search - copy/paste.  See what comes up - often it will be the solution.

To start any OS daemon, use
```
sudo systemctl start avahi
```

To stop, use
```
sudo systemctl stop avahi
```

Different options provide different information. To get a list of all services, timers, sockets, etc ... 
```
sudo systemctl -a
``` 

I'm not really a printing guru.  

HP is known for being well supported and usually doesn't need any extra drivers installed these days.
My Samsung laser printer has been plug and play since 2010.  The Brother device I haven't used as a printer since the first ink dried out.  I got it only for the automatic sheet feed on the scanner and for the fax machine.  It is well supported on Linux too, but needs about 20 steps of drivers installed to work.  The Brother company has nearly working instructions, but they do things in an odd way.  I much prefer the Samsung setup. All the drivers are provided with the OS and usually the system-config-printer just shows the model in a list. And that's it for setup.  Both my printers are USB connected. Cheap printers with networking or wifi connections seem too hard to get working, if they don't "just work".

Wifi on my laptops also "just works" and I've never needed to struggle to get it working. It comes back to picking the right hardware, not just buying on a whim, without research.  Just because a box at the store claims "Supports Linux", that doesn't mean too much.  I bought a RAID card with that on the outside.  Turned out the kernel drivers provided were over 3 yrs old and there were no updates.  So, either I could run a 3 yr old kernel or not use the card as intended.

I'll ignore the welfare state stuff, other than to say I disagree. You shouldn't feel bad for working and contributing to your village, city, state, and country. The more you have, the more you spend, which helps others.

---

### Post by ajgreeny on 2021-09-30
And as a final thought, it is now such a very long time since I used a printer connected by USB, and my network connected printer, an HP Envy 4752 was detected and usable without any action at all from me.  I do have hplip installed but generally it is not used for anything.

I do wonder if you might find a wireless network connection easier to set up and use, but as I don't use USB any more I have no way to compare the two methods.

---

### Post by oldfred on 2021-09-30
You said in the beginning you downloaded the HPLIP file directly from HP, but then upgraded with synaptic.
Typically the version you download from HP is newer that the default version in the Ubuntu repository. Unless new HP, either version should work, but HP's may have some updates. 

Not sure if you then uninstalled one version or created a version conflict. 

I might have started over removed/purged all HP drivers and only used latest HPLIP from HP.

---

### Post by teabutterfly2047 on 2021-09-30
@TheFu

> utilisateur@utilisateur-TravelMate-P253:~$ systemctl status avahi
Unit avahi.service could not be found.

indeed I've thought of a version conflict. I may try to uninstall HPLIP, then install the latest version from HP. I did skip the uninstall the older version (I followed the instructions to upgrade, so I supposed the older version would be then overwritten, no uninstall needed).


Anyway this is really too much trouble, headache and stress for a mere printer.

@oldfred thanks for the tips.

I'll go read them. And breathe deeply.

---

### Post by TheFu on 2021-09-30
> **teabutterfly2047 said:**
> @TheFu

Might want to install it and ensure it is running.  In theory, avahi is just for convenience and after the printer is installed, it shouldn't be needed anymore for non-networked printers.

[https://www.linuxbabe.com/ubuntu/set-up-cups-print-server-ubuntu-bonjour-ipp-samba-airprint](https://www.linuxbabe.com/ubuntu/set-up-cups-print-server-ubuntu-bonjour-ipp-samba-airprint) seems a reasonable how-to. I've used her guides before, but not this, specific, guide. You don't need the samba stuff, even if you have Windows clients, but it can be convenient to have Windows automatically install the drivers on Windows-clients and samba is needed for that to work.

---

### Post by teabutterfly2047 on 2021-09-30
In French there's a saying (when something bad happens, even a very traumatic event, or when s*it hits the fan: "Better laugh about it than cry".

Using humour when facing adversity is a well-known defense mechanism. ;-)

So yeah, @TheFu you did make a comment I probably should have ignored (but hey, I felt hurt, so said it), which doesn't mean I'm not grateful for the useful tips. Let's focus on that.

Positivity is a choice, or so I"ve heard.

(I read that being a person - we're full grown humans beings, folks! - with Asperger's comes with a lot of negativity and constant complaining. So bear with me. I am trying my best to change my natural neurological wiring, if that's even possible.

I did go to the printershop for a walk, a print and some fresh air. So this is actually a good day. :-)

Back to computer issues. I now know for sure I have a more serious issue than installing a printer. I bought my current laptop in 2013 and it is not aging gracefully. I have a number of issues and error messages that I've ignored for months, since for the most part, the computer still worked fine. So it is very possible that the issue comes from lack of debugging of my laptop system, not the new printer which is probably fine.

I should probably list my OS issues in a new thread, since they are not printer-related. Oh boy. More work to do when I'm already feeling overwhelmed.

One obvious issue is that using the Synacptic software in its graphic version does not work, lots of error messages and bugs. 

Time to switch back to:

> apt-get

OK, deep breath.

I'm now reading carefully this as suggested:

[https://www.linuxbabe.com/ubuntu/set-up-cups-print-server-ubuntu-bonjour-ipp-samba-airprint](https://www.linuxbabe.com/ubuntu/set-up-cups-print-server-ubuntu-bonjour-ipp-samba-airprint)

[https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by T6&amp;sfpER35% on 2021-09-30
some reading about apt and apt-get 
[https://itsfoss.com/apt-vs-apt-get-difference/](https://itsfoss.com/apt-vs-apt-get-difference/)

---

### Post by teabutterfly2047 on 2021-09-30
@3nd thanks.

I'm now reading this: [https://ubuntuforums.org/showthread.php?t=1011078](https://ubuntuforums.org/showthread.php?t=1011078)

I run the apt-get command in a terminal and got a red flag. You know, a round red circle with an exclamation point in the middle. Time to take those warning signs seriously and report bugs if needed. I clicked on the read button and got a warning message suggesting I run apt-get in a terminal. I won't copy/paste the result here.

First, I have quite a lot of reading to do. Let's put the kettle on.

Thanks again everyone.

---

### Post by T6&amp;sfpER35% on 2021-09-30
> [COLOR=#000000]I run the apt-get command in a terminal and got a red flag[/COLOR]
> [COLOR=#000000]warning message suggesting I run apt-get in a terminal[/COLOR]

i'm officially lost

what system are you on ? What's the output of```
inxi -Fxzd
```

---

### Post by T6&amp;sfpER35% on 2021-09-30
> [COLOR=#000000]I have a number of issues and error messages that I've ignored for months[/COLOR]

may i suggest you run the following commands 
```
sudo apt-get autoclean
```
```
sudo apt-get clean
```
```
sudo apt-get autoremove
```
```
rm -rfv ~/.cache/thumbnails
```
```
sudo du -sh /var/cache/apt
```
```
sudo apt-get update -y
```
```
sudo apt upgrade
```
```
sudo apt autoremove --purge
```
```
sudo systemd-resolve --flush-caches
```

also go to *settings* - *software&updates* and see if your'e stuff look like this

---

### Post by TheFu on 2021-09-30
We are all here wanting to be helpful. Everyone gets frustrated. That's fine.
Filing bugs is good, but not really a way to get a solution in the short-term.  Also, nearly all bugs aren't.

As for getting errors from the package managers (apt, apt-get, aptitude, synaptic, Software, etc.), that is something we all don't like, but it happens from time to time.  All of these tools use the same back-end libraries and safely can be used to install/remove software.
In 2011, I wrote an article about maintaining an Ubuntu Desktop that was published on a popular website.  Here's that article, updated over the years: [https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)  The main thing is to stay patched, run only a currently support release and to have versioned backups.

If APT (generic term for the Ubuntu/Debian package system) is having troubles, they don't magically go away and they don't get better over time. If there are any APT errors, never attempt a release upgrade. It won't get better and can leave a system that won't boot.

If you don't find a solution, you might look for an online linux user group meeting.  Lots of these groups have moved online due to COVID and many will be happy to help with any issues.  My group has 2 meetings a week and 

Should mention that in the last few years, different package types have been pushed by different organizations.  These don't interact with the APT system.  They are snap packages, flatpaks, and AppImages.  How those impact an ubuntu system differs, but it is good to be aware of them.  Snaps can be installed on Ubuntu without your explicit permission. They will be updated without your permission too.  That can be excellent or terrible.  Just be aware.  You won't won't accidentally get any flatpaks or AppImages installed.

To see which snaps are on your system now, run
```
snap list
```

---

### Post by teabutterfly2047 on 2021-10-02
@3nd to answer your question:

```
utilisateur@utilisateur-TravelMate-P253:~$ inxi -Fxzd
System:    Host: utilisateur-TravelMate-P253 Kernel: 4.15.0-122-generic x86_64 bits: 64 gcc: 7.5.0
           Desktop: Xfce 4.12.3 (Gtk 2.24.31) Distro: Ubuntu 18.04.5 LTS
Machine:   Device: laptop System: Acer product: TravelMate P253 v: V2.15 serial: N/A
           Mobo: Acer model: BA51_HC_CR v: Type2 - Board Version serial: N/A
           UEFI [Legacy]: Insyde v: V2.15 date: 03/11/2013
CPU:       Dual core Intel Core i3-3120M (-MT-MCP-) arch: Ivy Bridge rev.9 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9976
           clock speeds: max: 2500 MHz 1: 1197 MHz 2: 1197 MHz 3: 1197 MHz 4: 1197 MHz
Graphics:  Card: Intel 3rd Gen Core processor Graphics Controller bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.6 ) drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.01hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 4000 (IVB GT2)
           version: 4.2 Mesa 20.0.8 Direct Render: Yes
Audio:     Card Intel 7 Series/C216 Family High Def. Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.15.0-122-generic
Network:   Card-1: Broadcom and subsidiaries NetLink BCM57785 Gigabit Ethernet PCIe
           driver: tg3 v: 3.137 bus-ID: 02:00.0
           IF: eth0 state: down mac: <filter>
           Card-2: Qualcomm Atheros AR9485 Wireless Network Adapter driver: ath9k bus-ID: 03:00.0
           IF: wlan0 state: up mac: <filter>
Drives:    HDD Total Size: 500.1GB (82.2% used)
           ID-1: /dev/sda model: WDC_WD5000LPVX size: 500.1GB temp: 40C
           Optical-1: /dev/sr0 model: MATSHITA DVD-RAM UJ8E1 rev: 1.00 dev-links: cdrom,cdrw,dvd,dvdrw
           Features: speed: 24x multisession: yes
           audio: yes dvd: yes rw: cd-r,cd-rw,dvd-r,dvd-ram state: running
Partition: ID-1: / size: 455G used: 380G (88%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 4.10GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 52.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 210 Uptime: 8:15 Memory: 1761.5/3764.8MB Init: systemd runlevel: 5 Gcc sys: 7.5.0
           Client: Shell (bash 4.4.201) inxi: 2.3.56 
utilisateur@utilisateur-TravelMate-P253:~$ 


```

Hope this helps.

@3nd I just run all the commands you suggested and in the said order (clean, autoclean, autoremove, etc...). Here's what I get:

pasted/shortened version: [https://paste.ubuntu.com/p/pYXxz59ZPR/](https://paste.ubuntu.com/p/pYXxz59ZPR/) - I hope you can get to the information, as this is the first time I use [https://paste.ubuntu.com/ ]("https://paste.ubuntu.com/")

When going to settings/software and updates, I get your thumbnail "3.png".

Any help/suggestions welcome.

@TheFu thanks for the useful info and the helpful attitude. :)

I'm off to read your article.

From command ```
snap list
``` I get:

```
utilisateur@utilisateur-TravelMate-P253:~$ snap list
Nom                Version    Révision  Suivi          Éditeur        Notes
core               16-2.51.7  11743     latest/stable  canonical&#10003;     core
core18             20210722   2128      latest/stable  canonical&#10003;     base
core20             20210702   1081      latest/stable  canonical&#10003;     base
hplip-printer-app  1.0        70        latest/edge    openprinting&#10003;  -
riseup-vpn         0.21.6     172       latest/stable  leapsnaps      classic
```

Also of note, despite running ```
 apt --fix-broken install 
``` as suggested by my terminal after running all the commands suggested by @3nd in said order, I still get messages about at least 1 broken file, several version conflict, and packages that are necessary (including for the printer to run properly) not installed. To be more specific, I get this:

```
utilisateur@utilisateur-TravelMate-P253:~$ sudo apt upgrade
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Vous pouvez lancer « apt --fix-broken install » pour corriger ces problèmes.
Les paquets suivants contiennent des dépendances non satisfaites :
 printer-driver-postscript-hp : Dépend: hplip (>= 3.17.10+repack0-5) mais il n'est pas installé
 systemd : Est en conflit avec: systemd-shim mais 9-1bzr4ubuntu1 est installé
           Casse: systemd-shim (< 10-3~) mais 9-1bzr4ubuntu1 est installé
 systemd-sysv : Est en conflit avec: systemd-shim mais 9-1bzr4ubuntu1 est installé
E: Dépendances non satisfaites. Essayez « apt --fix-broken install » sans paquet
   (ou indiquez une solution).
utilisateur@utilisateur-TravelMate-P253:~$ sudo apt autoremove --purge
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Vous pouvez lancer « apt --fix-broken install » pour corriger ces problèmes.
Les paquets suivants contiennent des dépendances non satisfaites :
 printer-driver-postscript-hp : Dépend: hplip (>= 3.17.10+repack0-5) mais il n'est pas installé
 systemd : Est en conflit avec: systemd-shim mais 9-1bzr4ubuntu1 est installé
           Casse: systemd-shim (< 10-3~) mais 9-1bzr4ubuntu1 est installé
 systemd-sysv : Est en conflit avec: systemd-shim mais 9-1bzr4ubuntu1 est installé

```

Trying my best to stay calm here. Bear with me.

I just bought an external drive in order to have a backup of this old, outdated system (that still works somehow). I only have til October 4th in order to return printer if I want a refund.

Worst case scenario: if I really can't find help online (I tried using IRC for help before logging in here but got no answer), then I'll bring the poor ol' machine to a professional for repair.

One last piece of info: I run a search using catfish and found out I had both a .hplip (with a dot) version from 2014 and a recent hplip version I just downloaded but doesn't seem to be fully installed for some unknown reason.

Any help welcome. Thanks.

---

### Post by teabutterfly2047 on 2021-10-02
Printer is working. HOORAY. 

(I still have system error issues, but that's for another thread).

Thanks everyone for your help, good advice and patience.

---

### Post by TheFu on 2021-10-02
I've been using Linux since 1965!  [https://en.wikipedia.org/wiki/Xubuntu#History](https://en.wikipedia.org/wiki/Xubuntu#History), fyi.
Support for Xubuntu 18.04 ended last April. Passed time to move to 20.04.  

Xubuntu LTS releases get 3 yrs of support, last time I checked. [https://en.wikipedia.org/wiki/Xubuntu#Table_of_releases](https://en.wikipedia.org/wiki/Xubuntu#Table_of_releases)
Am I the only person who assumed this entire thread was about 20.04?

Moving to 20.04 will be harder now that 18.04 support is ended. Packages have been moved.

---

### Post by bm72 on 2021-10-07
OK, @TheFu

if this is too difficult, I may bring my laptop for update to a professionnal. This is beyond my skill/competence.

Also, I had a login problem and had no other choice but to create a new Ubuntu One account. Is there a way to merge my former teabuterfly2047 account with the current one? Thanks moderators if you can do this.

Thanks again all Ubuntu community for helpful insights and positive attitude!

---

### Post by bm72 on 2021-10-07
or I'll read this: [https://ubuntu.com/blog/how-to-upgrade-from-ubuntu-18-04-lts-to-20-04-lts-today](https://ubuntu.com/blog/how-to-upgrade-from-ubuntu-18-04-lts-to-20-04-lts-today)

and follow instructions.

---

### Post by oldfred on 2021-10-07
We cannot merge accounts.
We can change name if requested, but you have to give 3 choices or confirm (via PM) that you are you.
That typically is providing email of old account (not in request). 
Forum account is tied to Single Sign on only via email.

Single Sign On
[https://help.ubuntu.com/community/SSO/FAQs/Delete_SSO_Account](https://help.ubuntu.com/community/SSO/FAQs/Delete_SSO_Account)
Login now by means of Ubuntu One SSO only - sticky  thread
[http://ubuntuforums.org/showthread.php?t=2230004](http://ubuntuforums.org/showthread.php?t=2230004)

For an Admin or moderator to make any changes to your account you have to request here:
[https://ubuntuforums.org/forumdisplay.php?f=123](https://ubuntuforums.org/forumdisplay.php?f=123)

---

