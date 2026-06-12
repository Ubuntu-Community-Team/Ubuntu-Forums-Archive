---
title: "GRUB2 - How to change the Boot Order"
date: 2010-07-18
forum: Installation &amp; Upgrades
---

### Post by u2rcrazy on 2010-07-18
I'm running a Dual Boot system with Ubuntu 10.04 64bit and Windoes 7 64bit.  I want to change the default OS that loads.  Currently it loads Ubuntu automatically and I would like it to load Windows.  I looked up information on Grub2, but honestly, it didn't make much sense.  I thank you in advance for your help.

Sincerely,
Bob :p

---

### Post by Rubi1200 on 2010-07-18
> **u2rcrazy said:**
> I'm running a Dual Boot system with Ubuntu 10.04 64bit and Windoes 7 64bit.  I want to change the default OS that loads.  Currently it loads Ubuntu automatically and I would like it to load Windows.  I looked up information on Grub2, but honestly, it didn't make much sense.  I thank you in advance for your help.

Sincerely,
Bob :p

To change the order you need to edit GRUB like this:

```
sudo gedit /etc/default/grub
```The file should look something like this:

> GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash&#8221;
GRUB_CMDLINE_LINUX=&#8221;"
 # Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console
 # The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo&#8217;
#GRUB_GFXMODE=640×480
 # Uncomment if you don&#8217;t want GRUB to pass &#8220;root=UUID=xxx&#8221; parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true
 # Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY=&#8221;true&#8221;
You need to change this:

> GRUB_DEFAULT=0to this:

> GRUB_DEFAULT=1Exit and save then run this:

```
sudo update-grub
``` Windows should be the default the next time you reboot.

---

### Post by Bluesan on 2010-07-18
Or, use this...

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

---

### Post by cbowman57 on 2010-07-18
> **u2rcrazy said:**
> I'm running a Dual Boot system with Ubuntu 10.04 64bit and Windoes 7 64bit.  I want to change the default OS that loads.  Currently it loads Ubuntu automatically and I would like it to load Windows.  I looked up information on Grub2, but honestly, it didn't make much sense.  I thank you in advance for your help.

Sincerely,
Bob :p

The simplest way is to install startupmanager through synaptic.  Editing grub works too, as was already suggested but the gui is pretty foolproof.

---

### Post by rjrcooper on 2011-04-03
It should be said that GRUB_DEFAULT should be set to the number of the line that you want to use to boot minus 1. So the default is the first line (1-1=0!). 

I had to set my GRUB_DEFAULT to 5 as my Windows 7 boot option is on line 6 in my boot menu.

---

### Post by frank cox on 2011-07-24
Hi:

  I have been beating my head against the wall with this. I have several Ubuntu installs + rarely used XP and wish to boot from Natty. Recently I have added 10.10 server and it always comes up first. After editing /etc/default/grub nothing changes. There is a different default in etc/default/grub but the only difference is it takes longer to boot into sever 10.10.
When I checked the version it said 1.99 but on the boot screen it says 1.98.
This error comes up:


(gedit:2276): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.GAH0YV': No such file or directory

(gedit:2276): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2276): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.G9T4YV': No such file or directory

(gedit:2276): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

Have same problem on laptop w/ Linuxmitt Natty and Lubuntu 10.10. I changed the default from 0 to 1 and it still boots Mint. 

Any advice would be appreciated

---

### Post by drs305 on 2011-07-24
I highly recommend Grub Customizer. It's an app written for Grub 2 and can easily do a lot of Grub 2 maintenance. Click the link in my signature line (Customizer).

StartUp-Manager had limited Grub 2 capabilities but with Grub 1.99 (Natty)  and the introduction of submenus it pretty much is broken for selecting menu entries.

---

### Post by 3602 on 2011-07-25
Those errors *should *be harmless. I get them *all the time* when I *gedit* something.

---

### Post by gnu-buntu on 2011-07-26
*This is the best way to change grub2 boot order*:

[INDENT][http://danielsmedegaardbuus.dk/2011-01-31/changing-grub2-boot-order-the-right-way/](http://danielsmedegaardbuus.dk/2011-01-31/changing-grub2-boot-order-the-right-way/) [/INDENT]

I just ran the procedure, and it works perfectly. It also makes sense. Follow the instructions exactly and be sure to run $ sudo update-grub .

(If you change /etc/default/grub, you'll have problems the next time the o/s upgrades.)

Quick summary, assuming you want a foreign o/s, e.g., Windows to be first in the list and run as default:
[INDENT]you@yourhost:~$ sudo mv /etc/grub.d/30_os-prober /etc/grub.d/07_os-prober
you@yourhost:~$ sudo update-grub[/INDENT]

---

### Post by Quackers on 2011-07-26
> **frank cox said:**
> Hi:

  I have been beating my head against the wall with this. I have several Ubuntu installs + rarely used XP and wish to boot from Natty. Recently I have added 10.10 server and it always comes up first. After editing /etc/default/grub nothing changes. There is a different default in etc/default/grub but the only difference is it takes longer to boot into sever 10.10.
When I checked the version it said 1.99 but on the boot screen it says 1.98.
This error comes up:


(gedit:2276): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.GAH0YV': No such file or directory

(gedit:2276): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2276): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.G9T4YV': No such file or directory

(gedit:2276): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

Have same problem on laptop w/ Linuxmitt Natty and Lubuntu 10.10. I changed the default from 0 to 1 and it still boots Mint. 

Any advice would be appreciated

This line run in the terminal stops those error messages ```
sudo mkdir -p /root/.local/share
```

After the above is run open the edited file again (/etc/default/grub) and save the file again. This time no error messages should appear and the updated grub menu should show after running ```
sudo update-grub
```

---

### Post by gnu-buntu on 2011-07-28
> **gnu-buntu said:**
> *This is the best way to change grub2 boot order*:

[INDENT][http://danielsmedegaardbuus.dk/2011-01-31/changing-grub2-boot-order-the-right-way/](http://danielsmedegaardbuus.dk/2011-01-31/changing-grub2-boot-order-the-right-way/) [/INDENT]

I just ran the procedure, and it works perfectly. It also makes sense. Follow the instructions exactly and be sure to run $ sudo update-grub .

(If you change /etc/default/grub, you'll have problems the next time the o/s upgrades.)

Quick summary, assuming you want a foreign o/s, e.g., Windows to be first in the list and run as default:
[INDENT]you@yourhost:~$ sudo mv /etc/grub.d/30_os-prober /etc/grub.d/07_os-prober
you@yourhost:~$ sudo update-grub[/INDENT]

I posted the above in a thread elsewhere and got this response:
Quote:
Originally Posted by Mark Phelps  
...
First, if you replace the default "number" of the stanza you want launched with the text line, it won't change in the future.

Second, GRUB v1.99RC uses nested menus, meaning that only the most current kernel shows by default, the others are pushed down into a submenu. This means that the relative numbering of the other entries does not change when new kernel lines are added (as with updates).
*End quote*.

Yes, I did notice a line in the GRUB menu that refers to prior linux verions. So maybe the method I cited isn't "the best" but rather, "another" way.

---

