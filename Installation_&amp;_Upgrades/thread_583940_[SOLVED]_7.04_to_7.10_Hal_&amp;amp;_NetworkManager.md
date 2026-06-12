---
title: "[SOLVED] 7.04 to 7.10: Hal &amp;amp; NetworkManager got killed"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by vnevoa on 2007-10-20
I see a lot of people are having problems with HAL in Gutsy, wether in fresh install or upgrade.
I've surfed dozens of threads and a few launchpad bugs (including the ["Failed to initialize hal"]("https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931")), but nothing produced any difference in my case.

Symptoms:
1 - while I had Feisty, the NetworkManager never worked properly; I always had to put the DNS server address by hand in order to get Inet connection.
2 - after upgrading to Gutsy, the NetworkManager stopped working completely. It sits there and says "no network connection". However, I do have eth0 working just fine (with DNS and all, which is already a step up from Feisty).
3 - Now, every time I log in after booting, I get the "Failed to initialize Hal" message.
4 - my USB devices no longer are automaticaly powered and discovered.
5 - I found that the "hal" service cannot be started successfuly.
6 - I reinstalled the "hal" and "dbus" packages, but nothing changed. The hal package always fails configuration because the service won't start.
7 - I investigated the upgrade logs and found these two little gems:
```
/var/log/dist-upgrade/term.log:A instalar hal (0.5.9.1-6ubuntu5) ...
/var/log/dist-upgrade/term.log:A instalar nova versão do ficheiro de configuração /etc/udev/rules.d/95-hal.rules ...
/var/log/dist-upgrade/term.log:A instalar nova versão do ficheiro de configuração /etc/hal/fdi/policy/preferences.fdi ...
/var/log/dist-upgrade/term.log: * Starting Hardware abstraction layer hald
/var/log/dist-upgrade/term.log:**invoke-rc.d: initscript hal, action "start" failed.**
/var/log/dist-upgrade/term.log:A instalar hal-device-manager (0.5.9.1-6ubuntu5) ...
/var/log/dist-upgrade/term.log:A instalar hal-cups-utils (0.6.13+svn83-0ubuntu1) ...

```
```
/var/log/dist-upgrade/apt.log:Installing libhal-storage1 as dep of gnome-keyring
/var/log/dist-upgrade/apt.log:Installing libhal1 as dep of gnome-keyring
/var/log/dist-upgrade/apt.log:new important dependency: hal-cups-utils
/var/log/dist-upgrade/apt.log:Installing hal-cups-utils as dep of ubuntu-desktop
/var/log/dist-upgrade/apt.log:Installing hal-info as dep of hal
/var/log/dist-upgrade/apt.log:Investigating hal-device-manager
/var/log/dist-upgrade/apt.log:**Package hal-device-manager has broken dep on python-gnome2**
/var/log/dist-upgrade/apt.log:  Considering python-gnome2 350 as a solution to hal-device-manager 1
/var/log/dist-upgrade/apt.log:  Removing hal-device-manager rather than change python-gnome2

```
It is obvious that HAL failed right during the upgrade, but I have no idea how to relate the suposed dependency problem.

I followed the hints in the launchpad bugs and reconfigured the order of service launch with:
```
sudo update-rc.d -f dbus remove
sudo update-rc.d dbus multiuser 12 20
sudo /etc/init.d/dbus restart

```
but this didn't change the outcome.

My /etc/init.d/rc already had "CONCURRENCY=none", so it's not even an issue of init script concurrency.

It apears that Gutsy's HAL is broken.
Anyone got a working solution?

My system:
 AMD64 dual-core, 4GB RAM, nVidia PCI-x card with restricted driver.

---

### Post by Strid on 2007-10-21
Does this work?:

When you boot up, open a termial in gnome, type

 sudo /etc/init.d/dbus restart

then hit Ctrl+Alt+Backspace to restart GDM. Should work, though it's tedious to have to do it everytime you boot up your computer.

---

### Post by vnevoa on 2007-10-21
Nope, everything is exactly the same after Xorg reloads and I login.
This is expected, since hal will never start (as you can see below):
```
vasco@thechair:~$ sudo /etc/init.d/dbus restart
[sudo] password for vasco:
 * Stopping DHCP D-Bus daemon dhcdbd                                     [ OK ] 
 * Stopping Avahi mDNS/DNS-SD Daemon avahi-daemon                        [ OK ] 
 * Stopping ConsoleKit daemon console-kit-daemon                         [ OK ] 
 * Stopping Hardware abstraction layer hald                              [ OK ] 
 * Stopping System Tools Backends system-tools-backends                  [ OK ] 
 * Stopping network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Stopping network connection manager NetworkManager                    [ OK ] 
 * Stopping system message bus dbus                                      [ OK ] 
 * Starting system message bus dbus                                      [ OK ] 
 * Starting network connection manager NetworkManager                    [ OK ] 
 * Starting network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Starting System Tools Backends system-tools-backends                  [ OK ] 
[B] * Starting Hardware abstraction layer hald                                     invoke-rc.d: initscript hal, action "start" failed.
[/B] * Starting ConsoleKit daemon console-kit-daemon                         [ OK ] 
 * Starting Avahi mDNS/DNS-SD Daemon avahi-daemon                        [ OK ] 
 * Starting DHCP D-Bus daemon dhcdbd                                     [ OK ]
```

I'd realy like to debug this, but I can't find any log files that have an explanation for "hald"'s failure...
Can you point me to the place to get runtime info on hal?

---

### Post by vnevoa on 2007-10-21
Hmm... I went to the hal project page and they show us how to make a bug report.
So I grabbed their console launch command and captured the daemon's output from syslog:
*sudo hald --daemon=yes --verbose=yes --use-syslog*

```
Oct 21 16:46:39 thechair hald[10155]: 16:46:39.371 [I] hald.c:529: hal 0.5.9.1 
Oct 21 16:46:39 thechair hald[10155]: 16:46:39.371 [I] hald.c:538: Will daemonize 
Oct 21 16:46:39 thechair hald[10155]: 16:46:39.371 [I] hald.c:539: Becoming a daemon 
Oct 21 16:46:39 thechair hald[10156]: 16:46:39.373 [I] hald_dbus.c:4807: local server is listening at unix:abstract=/var/run/hald/dbus-GDedVsW496,guid=1369e3dc8d0263f932971c0047
1b745f 
Oct 21 16:46:39 thechair hald[10156]: 16:46:39.377 [I] hald_runner.c:299: Runner has pid 10157 
[B]Oct 21 16:46:39 thechair hald[10156]: 16:46:39.378 [W] ci-tracker.c:200: Could not get uid for connection: org.freedesktop.DBus.Error.NameHasNoOwner Could not get UID of name 'org.freedesktop.DBus': no such name 
Oct 21 16:46:40 thechair hald[10156]: 16:46:39.378 [E] hald_dbus.c:4462: Cannot get caller info for org.freedesktop.DBus[/B]
Oct 21 16:46:40 thechair hald[10156]: 16:46:39.380 [I] hald_runner.c:180: runner connection is 0x6536b0 
Oct 21 16:46:40 thechair hald[10156]: 16:46:39.382 [I] mmap_cache.c:161: Regenerating fdi cache.. 
Oct 21 16:46:49 thechair hald[10156]: 16:46:49.388 [I] mmap_cache.c:137: In regen_cache_cb exit_type=1, return_code=0 
**Oct 21 16:46:49 thechair hald[10156]: 16:46:49.388 [E] mmap_cache.c:190: fdi cache regeneration failed!**
Oct 21 16:46:49 thechair hald[10156]: 16:46:49.388 [I] mmap_cache.c:193: fdi cache generation done 
Oct 21 16:46:49 thechair hald[10156]: 16:46:49.388 [I] mmap_cache.c:251: cache mtime is 1192868046 

```

Anyone make heads or tails out of this? I don't know HAL or DBUS well enough to know what this is about...

---

### Post by alagu on 2007-10-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi,
Isn't there a solution for this? My box is almost useless without network. And my network device won't detect if Hald doesn't startup.

---

### Post by yann-pleiades on 2007-10-25
vnevoa, did you post the entire hald log ?

---

### Post by vnevoa on 2007-10-28
Yann:
Yes, I posted all the output that hald wrote in syslog, from the starting point. AFAIK, there is no hald log, and even then I had to launch hald in that special way to make it write verbosely in syslog.
 
Guess what? I just downloaded and installed Xubuntu (light, xfce-based ubuntu) 7.10 in an old computer (pentium II), and it's got the same problem!!! "Failed to initialize HAL"!!!
There is absolutely nothing in common between my two instalations... one is an AMD64 dual-core with diskless booting in which I did the upgrade from 7.04, and the other is a plain PentiumII with normal disk setup, in which I did a fresh install... They both got no HAL?!?!?....

There's definitely something wrong with HAL in Gutsy...

---

### Post by vnevoa on 2007-10-28
Good news, folks!
Got my main system working!
Did "**sudo mv /var/cache/hald/fdi-cache~ /var/cache/hald/fdi-cache**" and restarted the PC, and now it looks alright!!!
See bug [#139155]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/139155") for more info.
Haven't tried the PentiumII with xubuntu yet, but I will let you know when I do.

Edit:
The xubuntu system also recovered, using the command below (in my next reply).

---

### Post by vnevoa on 2007-10-28
Actualy, the correct way to do it seems to be:
**sudo /usr/lib/hal/hald-generate-fdi-cache**
(see [bug #146812]("https://bugs.launchpad.net/bugs/146812"))

---

### Post by vnevoa on 2007-10-28
Wow!... this specific problem appears in 18 different bugs!... no wonder it is so difficult to locate a solution...

---

### Post by Six_Digits on 2007-10-28
Worked for me too, vnevoa. All the other soloutions failed...

---

### Post by computer_user_au on 2007-11-01
Am wondering... Did you guys have to change the runlevel priorities for dbus and hal in /etc/rc2.d
e.g: hal from s12 to s13 and dbus from s50 to s12

---

### Post by vnevoa on 2007-11-01
Implicitly, yes, I did. In despair, I had already reinstalled HAL and DBUS after the upgrade... and that corrected the RC links. BTW, my system is booting just fine with rcscript concurrency, after the fixes.

---

### Post by kyfho23 on 2007-11-01
vnevoa...
   first, hats off...this was a hard one to diagnose for me. i've done about 25+ installs, blaming everything from synaptic/adept to a bad ethernet cord, and still no joy until i tried doing my setup tweaks one by one. and even then, setting concurrency=shell was about the last thing i'd suspected was killing my dsl connection.

   second, just to make sure i understand: if you issue the command sudo /usr/lib/hal/hald-generate-fdi-cache , you CAN set concurrency=shell?

   again, take some time to feel triumphant! squashing this one wasn't easy.

chris

---

### Post by vnevoa on 2007-11-01
First:
Hey, the credit is not mine, I got the answer from one of the many launchpad bug threads I read!... :) Nice place to get info, just a little disorganized... :(

Second:
The answer is yes, at least in my systems. Concurrency=shell.

Glad I could be of help! :)
My only credit here is to make this issue as clear as possible to the community, because the info is so damn scattered and confusing!... ;)

---

### Post by willdex on 2007-11-18
Hey, guys. Just to add my 2 cents: the *sudo /usr/lib/hal/hald-generate-fdi-cache* didn't work for me, nor did the *CONCURRENCY=shell* changing to *CONCURRENCY=none* thing or whatever. I honestly thought that I'd need to reformat the whole HD after reading about what a trouble it is to downgrade back to 7.04. One problem with that besides the intellectual one: my BIOS doesn't see the CDROM drive :( Wtf? Yeah, that's what I thought. Keeps saying that the *Secondary SATA is not installed*. Don't understand that part. Any suggestions are welcome.
What worked for me was this: *sudo dpkg --configure -a*. Now the Device Manager works normally. I did it after reading about a [PDF-editor]("http://ubuntuforums.org/showthread.php?t=272982") that I needed: went to the Terminal -> *sudo apt-get install pdfedit* -> and he's like "you'll have configure the **dpkg** manually -> so I go ahead and do the *dpkg --configure -a* thing. 6 minutes of *setting up* this and *setting up* that -> two last lines:
[I]Processing triggers for libc6 ...
ldconfig deferred processing now taking place[/I]
after which everything works fine. I'm sure there *will be* problems later on b/c this one is not a solution. Seems to be fine anyway...

---

### Post by helmingstay on 2007-11-26
> **vnevoa said:**
> First:
Hey, the credit is not mine, I got the answer from one of the many launchpad bug threads I read!... :) Nice place to get info, just a little disorganized... :(

Second:
The answer is yes, at least in my systems. Concurrency=shell.

Glad I could be of help! :)
My only credit here is to make this issue as clear as possible to the community, because the info is so damn scattered and confusing!... ;)


Indeed, thanks so much for the work!  With your help, it took me only :) 4 hours of googling, trying, googling, etc. :)
"sudo hald --daemon=no --verbose=yes" showed me some hints with a message about mmap not opening /var/cache/hald/fdi-cache, but wasn't exactly helpful...  

So, what exactly does  "/usr/lib/hal/hald-generate-fdi-cache" do, since "man hald-generate-fdi-cache" shows no useful information?  What was wrong to start with???

---

### Post by USFMD82 on 2008-01-11
GREAT IT WORKED FINALLY!!

The hal is no longer showing error at startup!! now I need to get my USB and SD card reader/Wireless  working

---

### Post by ingo on 2008-01-26
I had the same problem and [this]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/139155") bug report helped me get it working again - all happened after a wubi update...

---

