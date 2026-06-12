---
title: "VM Additions in Ubuntu - How to....."
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by Loki-uk on 2007-05-05
OK this was a bit of a misison, I'm a linux newbie so this took me a couple 
of weeks to figure out. This is how to install the VM Additions for Linux into Ubuntu under Virtual PC. 

First you need the following packages installed (and their dependancies) - 

alien
build-essential
fileutils
linux-headers-2.x.xx-xx-386 where the xx's are oyur kernel version
(you can find your kernel version by using 'uname -r' in the terminal)
linux-image-2.x.xx-xx-386 - should already be installed
linux-restricted-modules-2.x.xx-xx-386
linux-source-2.x.xx

Reboot once these are installed

Download chkconfig from [http://www.fastcoder.net/downloads/](http://www.fastcoder.net/downloads/)

from a terminal unpack it using 'tar xvf chkconfig-1.3.30a.tar.bz2'

Then use the following commands to build it

sudo -i
enter your user password when prompted
cd /home/YOUR USER NAME/ANY OTHER FOLDERS/chkconfig-1.3.30a
./configure --enable-ntsysv
make
make install
ln -fs /usr/local/sbin/chkconfig /usr/bin
ln -fs /usr/local/sbin/ntsysv /usr/bin
ln -fs /usr/local/sbin/chkconfig /sbin

mount the vm additions iso and then you need to change to your cdrom 

cd /media/cdrom

sudo -i
enter your user password when prompted

rpm -ivh vmadd-full-0.0.1-1.i386.rpm --force --nodeps

Then to start the vmadd service type 

/etc/init.d/vmadd start

Then 

/etc/init.d/vmadd-SERVICENAME start

You will need to add 'vmadd start' and the 'vmadd-servicename start' to 
modules to start them automatically each time ubuntu boots.

Loki-uk

---

### Post by jonfitt on 2007-11-07
Couple of comments:

I needed to mkdir /var/lock/rpm(?can't recall exactly) before it would let me run the rpm command.

I'm having trouble getting them to start on boot. Are you saying I need to add /etc/init.d/vmadd-SERVICENAME start to /etc/modules?

What packages can i remove after doing all of this (alien/linux-headers etc.)? I'd like to remove as much as possible to get it back to nearer the size it was before the install.

Thanks.

---

### Post by avanha on 2007-11-07
I just tried this with VM Additions 2.0 (released a couple of weeks ago I think) on a Debian Etch release and much to my surprise it worked without any problems.  I didn't notice any improvements in X performance, but at least the clock is in sync.

Thanks for the directions Loki

---

### Post by Bq32 on 2007-11-29
I've already tried installing VM Additions, but then it went into recovery mode, and when i logged in, i went to the login screen (GUI)! I tried again and again, and it does the same thing!I'm stuck at the installing the rpm part

---

### Post by puntahacharts on 2008-04-10
Hi,

I am running Ubuntu Server 7.04 as a virtual guest machine on MS Virtual Server 2005 R2.

I went through the above instructions and it worked fine.
Although, I am still not able to use the mouse in the GNOME desktop.
I am able to use the keyboard and therfore log in; however, I can not move the mouse around.

Could you/somebody please help me as I am trying to learn this Linux stuff?


Thanks you very much in advance,
@ndyP

---

### Post by Damien Kane on 2008-05-15
I don't know about 7.04, but I know how to get the mouse working under 7.10

1. The following steps assume 7.10 is installed and booted
2. Hold Ctrl-Alt-F1 for terminal
3. Enter your username and password from when you installed
4. Type: sudo nano /boot/grub/menu.lst and press Enter
5. Enter your password again
6. Go near the bottom of the file where it states:
## ## End Default Options ##
7. Under the title which ends with the word generic, put your cursor on the word 'Kernel' and press the end key
8. The end of the line should say ro quiet splash. At the end of this line, add i8042.noloop clock=pit to fix the mouse and a reported fix
9. Save it by holding down the Ctrl key and pressing O (oh, not zero)
10. The filename appears. Press enter, then Ctrl and X to exit the file. Click in the VM and the mouse should work. If not, reboot. If it still doesn't work, then I dunno!

---

### Post by HobbesPDX on 2008-05-28
My mouse stopped working after I attempted to install the Additions, as described here, in Virtual PC 2007 SP1, running on Vista SP1, installing Ubuntu 8.04.

I'm not even going to try to solve it -- I'm just going to delete the machine & reinstall.
( This link is really helpful for that! -- [http://blogs.technet.com/seanearp/archive/2008/05/13/installing-ubuntu-8-04-hardy-heron-in-virtual-pc-2007.aspx](http://blogs.technet.com/seanearp/archive/2008/05/13/installing-ubuntu-8-04-hardy-heron-in-virtual-pc-2007.aspx) )

Just a warning to anyone else who happens to read this post.....

---

