---
title: "Installed server from CD, but doesn't boot"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by kwilliam on 2006-06-03
This quote is from a different thread: [http://ubuntuforums.org/showthread.php?t=186424&highlight=install+server+boot](http://ubuntuforums.org/showthread.php?t=186424&highlight=install+server+boot)

[QUOTE=Bender NZ]I'm seeing a similar problem - I was installing a new server today (fresh install), everything installed fine and it rebooted and grabbed the packages, updated the kernel (2.6.15 i386) and then when it rebooted it would load the kernel and then sit and do nothing.

The only way I can get it to boot is with 2.6.12. I tried installing the 2.6.15 i686 version but that didn't get me anywhere either.

I've seen this on two other servers last week too - but I can't really find any decent info to file a bug report because it just hangs :/[/QUOTE]
My problem is exactly as described above: I did a clean install of Ubuntu Server (Dapper 6.06) and will get all the way through the installation process (albeit in "Low Memory mode").  However, when I tried to boot, Grub would start, count down for 2 seconds, briefly print one or two statements of output to the screen (It disappears quicly, but I think the last line was just "boot") and then the screen would go black: no terminal, no response to the keyboard. I had started setting up a small Apache server over the past few weeks, using Breezy 5.10 (the desktop version, not the server), and I wanted to take advantage of Dapper's "Install LAMP Server" option. I've tried multiple times, trying different options on the install screen: ran the memory test, verified that the CD is not damaged, did a regular install (the first option), but the end result was unchanged.

Since it wasn't working, I tried installed Ubuntu Server 5.10 over it, and that worked. **My question is:** Why won't my Dapper Server boot? (I checked, and although the computer is old, it falls within the [system requirements](http://www.ubuntu.com/download/releasenotes/606).)

In the mean time, I'll try installing a LAMP server on 5.1 with XAMPP.

System:
8 year old IMB
300 MHz
64 MB memory

One other thing: why isn't their and Ubuntu Server prefix?  There's prefixes for Kbuntu, and Edbuntu, etc, but not Server.

---

### Post by confused57 on 2006-06-03
I had a problem booting up from the Dapper 6.06-server-i386, my computer would just reboot instead of starting the kernel.

I did a Breezy server install and dist-upgraded to Dapper with no problems.

1.)sudo nano /etc/apt/sources.list
2.)sudo apt-get update
3.)sudo apt-get dist-upgrade

I changed all references from breezy to dapper in #1.

Also, you can do a server install from the Dapper6.06-alternate  CD.

---

### Post by kwilliam on 2006-06-03
[QUOTE=confused57]I had a problem booting up from the Dapper 6.06-server-i386, my computer would just reboot instead of starting the kernel.[/QUOTE]
Thank you for responding!  I figured out how to do that eventually, but is there a way to get the "Install LAMP server" functionality?  I installed XAMPP, but it didn't appear to include apache2-utils (I wanted htpasswd and htdigest) and for some reason, the computer refuses to install them via apt-get, even after I run apt-get update.

This may be a rhetorical question, but I'm curious from a knowledge perspective more than anything: Why did it reboot instead of starting the kernel?  Is that a bug in Ubuntu, or the kernel, or is that not unusual?

---

### Post by confused57 on 2006-06-03
See if the wiki instructions may help you:

[https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

I believe there may be a bug with the Dapper-server install CD, I've seen several other posts mentioning the same types of problems.

---

### Post by Joao Moura on 2006-06-04
[QUOTE=kwilliam]This quote is from a different thread: [http://ubuntuforums.org/showthread.php?t=186424&highlight=install+server+boot](http://ubuntuforums.org/showthread.php?t=186424&highlight=install+server+boot)


My problem is exactly as described above: I did a clean install of Ubuntu Server (Dapper 6.06) and will get all the way through the installation process (albeit in "Low Memory mode").  However, when I tried to boot, Grub would start, count down for 2 seconds, briefly print one or two statements of output to the screen (It disappears quicly, but I think the last line was just "boot") and then the screen would go black: no terminal, no response to the keyboard. I had started setting up a small Apache server over the past few weeks, using Breezy 5.10 (the desktop version, not the server), and I wanted to take advantage of Dapper's "Install LAMP Server" option. I've tried multiple times, trying different options on the install screen: ran the memory test, verified that the CD is not damaged, did a regular install (the first option), but the end result was unchanged.

Since it wasn't working, I tried installed Ubuntu Server 5.10 over it, and that worked. **My question is:** Why won't my Dapper Server boot? (I checked, and although the computer is old, it falls within the [system requirements](http://www.ubuntu.com/download/releasenotes/606).)

In the mean time, I'll try installing a LAMP server on 5.1 with XAMPP.

System:
8 year old IMB
300 MHz
64 MB memory

One other thing: why isn't their and Ubuntu Server prefix?  There's prefixes for Kbuntu, and Edbuntu, etc, but not Server.[/QUOTE]
My problem is the very same. I've installed the 6.06 Server (fresh install) and as soon as the machine reboots, the last word I can see printed on screen is "boot". after that, the machine reboots again in one endless cycle.

---

### Post by Endwin on 2006-06-04
I get the same problem Server 6.06, LAMP install. It installs fine, then reboots on an endless cycle. I am using the same hardware I have used for a server for years. 

AMD K6 300 MGHTZ
192 MB RAM
20 GB WD HD

Really odd that it is doing this.

---

### Post by kwilliam on 2006-06-05
I wonder if the problem is specific to computers with 300 MHz processors, or just old computers?  Both mine and Edwin's servers are 300 MHz.  Just in case, how fast is your computer Joao Moura?

---

### Post by fhoffer on 2006-06-05
I had the same problem, on a machine with limited memory (256 MB with an AGP card, which uses memory). I tried the server install on a machine with 2GB and it worked fine. I tried the "alternate" set on the small machine and it worked fine. My guess is that by the time you get everything you need for a LAMP install in the kernel image, it runs out of memory trying to uncompress the kernel. That is the message I blew up on. You just can't get 6 pounds of anything into a 5 pound sack.

---

### Post by tabdelgawad on 2006-06-05
[QUOTE=fhoffer]I had the same problem, on a machine with limited memory (256 MB with an AGP card, which uses memory). I tried the server install on a machine with 2GB and it worked fine. I tried the "alternate" set on the small machine and it worked fine. My guess is that by the time you get everything you need for a LAMP install in the kernel image, it runs out of memory trying to uncompress the kernel. That is the message I blew up on. You just can't get 6 pounds of anything into a 5 pound sack.[/QUOTE]

I don't think it's a memory/cpu issue.  I have the exact same problem - LAMP install followed by infinite reboots - and I'm using an 800 MHz processor and 512 Megs of RAM.

Tamer

---

### Post by jtholmes on 2006-06-05
when grub fails to load the kernel, or it cant find the  MBR it will sometimes
do funny things.

if you can boot from live cd, whatever, then mount  
/dev/hdaX  or whatever your root (/) fs is and edit
/boot/grub/menu.lst

in the Kernel section of where you want to boot from put
the following in the front  of  /boot/...
(hd0,0)/boot/...

hd0 is physical disk ONE
,0  is first slice/partition of  hd0

do the same for the  initrd  entry

try booting again.

I found that  6.06 server got confused when I had two drives
that were Linux and bootable and it hosed up the  grub menu.
jt

---

