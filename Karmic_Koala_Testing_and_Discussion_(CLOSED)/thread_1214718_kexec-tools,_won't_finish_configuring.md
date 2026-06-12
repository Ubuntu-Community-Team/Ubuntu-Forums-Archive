---
title: "kexec-tools, won't finish configuring"
date: 2009-07-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-07-16
Was doing updates via Synaptic and this 'kexec-tools' would not finsh setting up. Could not shut Synaptic down, so did system restart and open terminal, did 'sudo dpkg --configure -a' and it stuck again at setting up this 'kexec-tools'.
What is this package and what is it's problem? I can not do any thing via terminal because it wants me to '--configure -a' first.
```
Setting up kexec-tools (20090000-2.0.0ubuntu10) ...
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-3-generic-pae
Found kernel: /boot/vmlinuz-2.6.31-3-generic
Found kernel: /boot/vmlinuz-2.6.31-2-generic-pae
Found kernel: /boot/memtest86+.bin


```

---

### Post by taavikko on 2009-07-16
```
aptitude show kexec-tools
```
linux-crashdump and/or makedumpfile will reel it in to the system. "apt-cache rdepends <pkg>"

System up-to-date and dependencies satisfied...
```
sudo aptitude update
sudo aptitude -f install
sudo dpkg --configure -a
```

---

### Post by DougieFresh4U on 2009-07-16
I can not do any thing as synaptic won't open as it's telling me to 'dpkg --configure -a' and terminal won't do any thing but tell me I need to 'dpkg --configure -a'.
Please, where else can I find this package and do some thing with it to get terminal working again? Would recovery from grub work to fix?
thanks```
ougie@DougiesLeanMachine:~$ sudo aptitude show kexec-tools
[sudo] password for dougie: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Package: kexec-tools
State: partially configured
Automatically installed: yes
Version: 20090000-2.0.0ubuntu10
Priority: optional
Section: admin
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 303k
Depends: libc6 (>= 2.4), debconf (>= 0.5) | debconf-2.0, debconf,
         initramfs-tools
Description: kexec tool for kexec reboots
 This tool is used to load a kernel in memory and reboot into the kernel loaded
 in memory using the kexec system call.

dougie@DougiesLeanMachine:~$ 

```

---

### Post by taavikko on 2009-07-16
aptitude show command doesn't require sudo priviledges, so let's try not to overuse them.
seems that you have some application open that is used to manage packages.
Please close all of them.

If you wish, you can start from recovery, and issue these commands.
Drop to root shell with networking

```
dpkg --configure -a
```

```
aptitude update
```

```
aptitude -f install
```

replace aptitude with apt-get if your more familiar and accustomed to it.

These commands should fix the issue, and you can then logout root console with the command
```
exit
```

---

### Post by DougieFresh4U on 2009-07-16
> **taavikko said:**
> aptitude show command doesn't require sudo priviledges, so let's try not to overuse them.
seems that you have some application open that is used to manage packages.
Please close all of them.

If you wish, you can start from recovery, and issue these commands.
Drop to root shell with networking

```
dpkg --configure -a
```

```
aptitude update
```

```
aptitude -f install
```

replace aptitude with apt-get if your more familiar and accustomed to it.

These commands should fix the issue, and you can then logout root console with the command
```
exit
```

Thanks for your time and help. :D Thanks for advice on 'sudo' and I rather use the 'aptitude' than 'apt-get'
When I drop to a shell and issue the 'dpkg --configure -a' command, I get they same as I was getting from terminal, it stops after the 'mem test' line and just goes no further. Some how I need to fix that 'kexec-tools' or get rid of it and replace it. I was able to get into System Monitor, but every time I tried to kill 'kexec' process, System Monitor crashed. I'm kind of lost at this point.
Apparently no one else is having the 'kexec-tools' issue and I wonder why as all I was doing was update via Synaptic.

---

### Post by DougieFresh4U on 2009-07-16
Please, any one, how can I get around this mess. It's basically got my system on 'lock down'. I need to kill that 'kexec-tools'

---

### Post by wayne_cat on 2009-07-16
Why do you want to keep it ... kexec is "rocket science" ... it has nothing to do with the "Karmic booting in under 10 seconds" idea.

Kexec is not a part of the default Karmic system ... you don't lose anything.

An IBM article about kexec:

[http://www.ibm.com/developerworks/linux/library/l-kexec.html](http://www.ibm.com/developerworks/linux/library/l-kexec.html)

---

### Post by DougieFresh4U on 2009-07-17
> **wayne_cat said:**
> Why do you want to keep it ... kexec is "rocket science" ... it has nothing to do with the "Karmic booting in under 10 seconds" idea.

Kexec is not a part of the default Karmic system ... you don't lose anything.

Thanks, glad to hear it's not needed.
But I still have the problem of getting rid of it as like I have stated it's got my system on 'lock-down', Synaptic, terminal, update-manager, all these things want me to 'dpkg --configure -a' but I can't do it and killing process via System monitor just crashes

---

### Post by wayne_cat on 2009-07-17
in a gnome-terminal:

```
sudo /etc/init.d/kexec stop
```is the process still there?

then this:

```
sudo mv /sbin/kexec /root/
```now reboot an try to run 

try:
```

sudo dpkg --configure -a
```in a terminal again

---

### Post by DougieFresh4U on 2009-07-17
> **wayne_cat said:**
> in a gnome-terminal:
```
sudo /etc/init.d/kexec stop
```is the process still there?
then this:
```
sudo mv /sbin/kexec /root/
```now reboot an try to run 
try:
```

sudo dpkg --configure -a
```in a terminal again

Thanks so much your assistance.But I am sorry to report that upon doing your steps, I am still getting the same result from terminal, wanting me to do 'dpkg --configure -a' and getting stopped after the mem test line.
Let me ask this, is there a way to 'force' it to configure  or die and go away?
```
dougie@DougiesLeanMachine:~$ sudo /etc/init.d/kexec stop
[sudo] password for dougie: 
dougie@DougiesLeanMachine:~$ sudo mv /sbin/kexec /root/
mv: cannot stat `/sbin/kexec': No such file or directory
dougie@DougiesLeanMachine:~$ 


```

---

### Post by wayne_cat on 2009-07-17
huh ... where is it ... try to find it:
```

sudo find / -name kexec 
```this command will run for quite a long time ... patience

---

### Post by DougieFresh4U on 2009-07-17
Here  ya go
```
dougie@DougiesLeanMachine:~$ sudo find / -name kexec
[sudo] password for dougie: 
/usr/src/linux-headers-2.6.31-1-generic-pae/include/config/kexec
/usr/src/linux-headers-2.6.31-2-generic/include/config/kexec
/usr/src/linux-headers-2.6.31-3-generic/include/config/kexec
/usr/src/linux-headers-2.6.31-3-generic-pae/include/config/kexec
/usr/src/linux-headers-2.6.31-1-generic/include/config/kexec
/usr/src/linux-headers-2.6.31-2-generic-pae/include/config/kexec
/etc/init.d/kexec
/etc/default/kexec
/root/kexec
dougie@DougiesLeanMachine:~$ 

```
Thanks, now what do I do?
I really appreciate your help

---

### Post by wayne_cat on 2009-07-17
the important part of the find result:

```
/root/kexec
```So kexec can not start ... now try:

```
sudo dpkg --configure -a
```

---

### Post by DougieFresh4U on 2009-07-17
> **wayne_cat said:**
> the important part of the find result:

```
/root/kexec
```So kexec can not start ... now try:

```
sudo dpkg --configure -a
```

Sorry for being such a pain.
Why is it still trying to configure 'kexec'?
of course terminal is 'frozen again at 'boot/memtest
```
dougie@DougiesLeanMachine:~$ sudo dpkg --configure -a
[sudo] password for dougie: 
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-3-generic
Setting up kexec-tools (20090000-2.0.0ubuntu10) ...
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-3-generic-pae
Found kernel: /boot/vmlinuz-2.6.31-3-generic
Found kernel: /boot/vmlinuz-2.6.31-2-generic-pae
Found kernel: /boot/memtest86+.bin

```

---

### Post by wayne_cat on 2009-07-17
the installation task from the kexec package is still pending.

can you kick kexec from your system?

```
sudo apt-get remove kexec-tools
```

---

### Post by DougieFresh4U on 2009-07-17
> **wayne_cat said:**
> the installation task from the kexec package is still pending.

can you kick kexec from your system?

```
sudo apt-get remove kexec-tools
```

Not heappening
```
dougie@DougiesLeanMachine:~$ sudo apt-get remove kexec-tools
[sudo] password for dougie: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
dougie@DougiesLeanMachine:~$ 

```
Can I just go 'sudo nautilus' and find the folder and move it to trash?
I am far from 'guru' and your help is much appreciated.

---

### Post by wayne_cat on 2009-07-17
come on ... be aggressive :biggrin:

```
sudo dpkg --purge kexec-tools
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by DougieFresh4U on 2009-07-17
> **wayne_cat said:**
> come on ... be aggressive :biggrin:

```
sudo dpkg --purge kexec-tools
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

Thank you very much. Up and running . When I was doing 'dist-upgrade' I saw it was 'Getting' package for 'kexec-tools', so I aborted and went to Synaptic and upgraded there after I 'unmarked' 'kexec-tools'
What is up with this 'kexec-tools' and how can I stop future upgrades to 'kexec-tools'? should I just 'lock' version of that package. I guess I was the only one with this issue.
Again, thanks so much for your help :):)

---

### Post by wayne_cat on 2009-07-17
> **DougieFresh4U said:**
> Thank you very much. Up and running . When I was doing 'dist-upgrade' I saw it was 'Getting' package for 'kexec-tools', so I aborted and went to Synaptic and upgraded there after I 'unmarked' 'kexec-tools'
What is up with this 'kexec-tools' and how can I stop future upgrades to 'kexec-tools'? should I just 'lock' version of that package. I guess I was the only one with this issue.
Again, thanks so much for your help :):)

Kexec is not a part of the default installation and it should also be not a dependency of an other package ... please try this:

```
sudo dpkg --purge kexec-tools
```Do you get this error message?

```
root@macbook:~# sudo dpkg --purge kexec-tools
dpkg: warning: ignoring request to remove kexec-tools which isn't installed.
```edit: this is what I see after installing and removing kexec-tools:

```
root@macbook:~# sudo dpkg --purge kexec-tools
dpkg: warning: ignoring request to remove kexec-tools which isn't installed.
root@macbook:~# apt-get update
Hit http://ppa.launchpad.net karmic Release.gpg                                                            
Hit http://security.ubuntu.com karmic-security Release.gpg                                                 
Get:1 http://archive.ubuntu.com karmic Release.gpg [189B]            
Hit http://ppa.launchpad.net karmic Release.gpg                         
Hit http://archive.ubuntu.com karmic-updates Release.gpg
Hit http://security.ubuntu.com karmic-security Release
Hit http://ppa.launchpad.net karmic Release                         
Hit http://ppa.launchpad.net karmic Release                                               
Get:2 http://archive.ubuntu.com karmic Release [65.9kB]                                   
Hit http://security.ubuntu.com karmic-security/main Packages             
Hit http://ppa.launchpad.net karmic/main Packages                        
Hit http://security.ubuntu.com karmic-security/restricted Packages
Hit http://ppa.launchpad.net karmic/main Packages                           
Hit http://security.ubuntu.com karmic-security/universe Packages            
Hit http://security.ubuntu.com karmic-security/multiverse Packages          
Hit http://ppa.launchpad.net karmic/main Sources                            
Hit http://archive.ubuntu.com karmic-updates Release  
Get:3 http://archive.ubuntu.com karmic/main Packages [1305kB]                                              
Get:4 http://archive.ubuntu.com karmic/restricted Packages [7357B]                                         
Hit http://archive.ubuntu.com karmic/universe Packages                                                     
Get:5 http://archive.ubuntu.com karmic/multiverse Packages [196kB]                                         
Hit http://archive.ubuntu.com karmic-updates/main Packages                                                 
Hit http://archive.ubuntu.com karmic-updates/restricted Packages                                           
Hit http://archive.ubuntu.com karmic-updates/universe Packages                                             
Hit http://archive.ubuntu.com karmic-updates/multiverse Packages                                           
Fetched 1574kB in 35s (44.1kB/s)                                                                           
Reading package lists... Done
root@macbook:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@macbook:~#
```

---

### Post by DougieFresh4U on 2009-07-17
I am working on it now again. I unchecked it in Synaptic and proceeded with upgrade via Synaptic. But I'll be darned if it some how tried to put me through it all over again and Synaptic got stuck at 'boot/memtest' again, because it tried to set up 'kexec-tools'.
I could close any thing as I was on 'lock-down' again. so I did a 'hard' shut down and when I rebooted I was presented with a login that I have never seen before, 2 choices, 'restart' or 'shutdown' in which neither one worked. so now I am booted into recovery and gonna do the steps you gave earlier again.
I am typing this via my old, old Mac machine.
This package 'kexec-tools' needs to go away from me!!

EDIT: So I tried to purge it from recovery console and this is the message I get:
dpkg: dependency problems prevent removal of kexec-tools 
linux-crashdump depends on kexec-tools.
dpkg: error processing kexec-tools (--purge):
dependency problems - not removing

---

### Post by wayne_cat on 2009-07-17
> **DougieFresh4U said:**
> I am working on it now again. I unchecked it in Synaptic and proceeded with upgrade via Synaptic. But I'll be darned if it some how tried to put me through it all over again and Synaptic got stuck at 'boot/memtest' again, because it tried to set up 'kexec-tools'.
I could close any thing as I was on 'lock-down' again. so I did a 'hard' shut down and when I rebooted I was presented with a login that I have never seen before, 2 choices, 'restart' or 'shutdown' in which neither one worked. so now I am booted into recovery and gonna do the steps you gave earlier again.
I am typing this via my old, old Mac machine.
This package 'kexec-tools' needs to go away from me!!

ok ... interesting ... a Mac ... and old Mac ... kexec only works on computers with a BIOS!

could you please post the result from:

```
sudo find / -name "*kexec*"
```btw ... I'm typing this on an Apple Macbook Pro ... an Intel system with EFI instead of a BIOS ... but with a "BIOS emulation".

So this is maybe something for a Launchpad Bug Report

edit: Important ... kexec has only changed the initrd of the 2.6.31-3 kernel ... can you boot one of the other kernels?  (if you have not removed the older versions)

---

### Post by DougieFresh4U on 2009-07-17
The machine  w/ problem is an  AMD  6400x2
Thanks
I was able to 'dpkg --configure -a using recovery console after purging bum package, and all went through and booted as usual.

```
dougie@DougiesLeanMachine:~$ sudo find / -name ""Kexec""
[sudo] password for dougie: 
dougie@DougiesLeanMachine:~$ 

```
I hope this means I am done with this 'drama'
I'm putting the 'old Mac' back to it's semi retire

---

