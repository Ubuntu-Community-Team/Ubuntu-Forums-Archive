---
title: "Upgrade to 10.10 root can't open display"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by Matt Harrison on 2010-10-12
I just upgraded from 10.04 to 10.10.
After the upgrade I can't open any GUI programs running as root.

```
matt@milhouse:~$ sudo synaptic
No protocol specified

(synaptic:3260): Gtk-WARNING **: cannot open display: :0.0
```

Or using gksu I just get the password prompt and then nothing happens.

Same thing if running from the System->Administration menu.


This is the same for all programs, not just Synaptic.

Any idea of how I can debug this issue?

---

### Post by andrewthomas on 2010-10-12
Try to open Synaptic from the menu then do 
```

sudo tail /var/log/messages
```

and post the output

---

### Post by Matt Harrison on 2010-10-12
Running it from the Menu or command line doesn't add anything to.
/var/log/messages

The last logs in /var/log/messages were from UFW, about 5 minutes before trying. (Blocking random incoming network traffic)

---

### Post by lechien73 on 2010-10-12
If you run the command **xhost** from the terminal, what output do you get?

---

### Post by andrewthomas on 2010-10-12
Try to purge and reinstall 

```
sudo aptitude purge gksu software-properties-gtk
```

then 

```
sudo aptitude update && sudo aptitude install gksu software-properties-gtk
```

---

### Post by Matt Harrison on 2010-10-12
> **lechien73 said:**
> If you run the command **xhost** from the terminal, what output do you get?

```
matt@localhost:~$ xhost
access control enabled, only authorized clients can connect
SI:localuser:matt
matt@localhost:~$ sudo xhost
No protocol specified
xhost:  unable to open display ":0.0"
```

---

### Post by Matt Harrison on 2010-10-12
Running this:

```
matt@localhost:~$ sudo aptitude purge gksu software-properties-gtk
The following packages will be REMOVED:  
  gksu{p} software-properties-gtk{p} 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 631kB will be freed.
The following packages have unmet dependencies:
  ubuntu-desktop: Depends: software-properties-gtk but it is not going to be installed.
  checkbox-gtk: Depends: gksu but it is not going to be installed.
  update-notifier: Depends: gksu but it is not going to be installed.
  network-manager-gnome: Depends: gksu but it is not going to be installed.
  gdebi: Depends: gksu (>= 2.0.0-1ubuntu3) but it is not going to be installed.
  gnome-codec-install: Depends: gksu but it is not going to be installed.
  update-manager: Depends: gksu but it is not going to be installed.
  ailurus: Depends: gksu but it is not going to be installed.
  apturl: Depends: gksu (>= 2.0.0-1ubuntu3) but it is not going to be installed.
          Depends: software-properties-gtk but it is not going to be installed.
  computer-janitor-gtk: Depends: gksu but it is not going to be installed.
The following actions will resolve these dependencies:

      Remove the following packages:                                                                            
1)      ailurus                                                                                                 
2)      apturl                                                                                                  
3)      checkbox-gtk                                                                                            
4)      computer-janitor-gtk                                                                                    
5)      gdebi                                                                                                   
6)      gnome-codec-install                                                                                     
7)      network-manager-gnome                                                                                   
8)      ubufox                                                                                                  
9)      ubuntu-desktop                                                                                          
10)     update-manager                                                                                          
11)     update-notifier                                                                                         
12)     xul-ext-ubufox                                                                                          

      Leave the following dependencies unresolved:                                                              
13)     apport-gtk recommends update-notifier                                                                   
14)     firefox recommends ubufox                                                                               
15)     gparted recommends gksu                                                                                 
16)     network-manager recommends network-manager-gnome | network-manager-kde | plasma-widget-networkmanagement
17)     software-center recommends update-notifier                                                              
18)     software-center recommends software-properties-gtk                                                      
19)     synaptic recommends gksu | kdebase-bin                                                                  
20)     synaptic recommends software-properties-gtk                                                             
21)     ubuntu-desktop recommends computer-janitor-gtk                                                          
22)     ubuntu-desktop recommends gnome-codec-install                                                           
23)     ubuntu-desktop recommends network-manager-gnome                                                         
24)     update-notifier recommends software-properties-gtk                                                      
25)     update-manager recommends software-properties-gtk (>= 0.71.2)                                           


Accept this solution? [Y/n/q/?]
```


I'm not sure I want to remove all of that, should it be fine or will it break something?

---

### Post by andrewthomas on 2010-10-12
No, I wouldn't do that.

---

### Post by lechien73 on 2010-10-12
Just to confirm it's not a permissions issue, please could you try typing:

```
xhost +
```

Which will switch off Xserver access control, and try the sudo command again.

---

### Post by andrewthomas on 2010-10-12
To get you to be able to run try and see if kdesudo works.

It shouldn't pull in too much

> andrew@790Fx:~$ aptitude show kdesudo
Package: kdesudo                         
State: installed
Automatically installed: no
Version: 3.4.2.3-2ubuntu2
Priority: optional
Section: kde
Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubuntu.com>
Uncompressed Size: 156k
Depends: kdebase-runtime, libc6 (>= 2.3.4), libgcc1 (>= 1:4.1.1), libkdecore5
         (>= 4:4.3.4), libkdeui5 (>= 4:4.3.4), libqt4-dbus (>= 4:4.5.3),
         libqt4-svg (>= 4:4.5.3), libqtcore4 (>= 4:4.7.0~beta1), libqtgui4 (>=
         4:4.5.3), libstdc++6 (>= 4.1.1), sudo
Description: sudo frontend for KDE
 KdeSudo is a graphical frontend for the sudo utility, which allows users to run
 programs as root (or another user) by giving their own password.
Homepage: [https://launchpad.net/kdesudo](https://launchpad.net/kdesudo)



---

### Post by Matt Harrison on 2010-10-12
Running **xhost +** let me run it just fine.


I wonder if this is related to the other issue I've been having since upgrade.

My hostname keep changing to localhost.localdomain
```
matt@localhost:~$ hostname
localhost.localdomain

```

Although it is set properly in /etc/hostname
```
matt@localhost:~$ cat /etc/hostname 
milhouse

```

If I run **sudo hostname milhouse** the hostname changes properly, however once I reboot it reverts to localhost.localdomain

---

### Post by lechien73 on 2010-10-12
Good stuff...we're making progress :)

Does your hostname show correctly in /etc/hosts?

For example, the first few lines of my /etc/hosts file are:

```
192.168.42.28	lechien-x
127.0.0.1	localhost.localdomain	localhost

```

---

### Post by Matt Harrison on 2010-10-12
Looks like it is a side affect of the hostname issue.

I had been manually running **sudo hostname milhouse** after each reboot to set the hostname back to what it should be (some of my networking required the hostname)

I just tried restarting and opening Synaptic and it worked fine. Then after the changing the hostname Synaptic won't load anymore. So I'm guessing the ACL is not allowing it because of the hostname issue.


So now, this turns into... How can I fix my hostname issue?



I've got this in /etc/hosts
```

127.0.0.1	milhouse
127.0.0.1	localhost
127.0.0.1	localhost.localdomain

```

---

### Post by lechien73 on 2010-10-12
Hmmmm...I assume your computer is connected to a network?

If it is, then Network Manager should automatically add a line with your IP address and hostname - like mine: 192.168.42.28 lechien-x

You could try adding it manually and seeing what happens:

Right click on the network icon on the top panel next to the clock and go to **Connection Information**

Write down the IP address.

Now edit your hosts file:

```
sudo nano /etc/hosts
```

Add your IP address, followed by a couple of spaces, and your hostname **milhouse**

Press Ctrl+X to write the file and exit. Try rebooting and see if your hostname is now correct.

---

### Post by Matt Harrison on 2010-10-12
I figured it out, root couldn't read the hosts file.
```
$ sudo stat /etc/hosts
stat: cannot stat `/etc/hosts': Permission denied
```

Went ahead and changed the permissions to root:root and 0644 which I copied from stat from my working Ubuntu Maverick machine.

Rebooted and all works fine.


Previously I had changed the hosts file so I could edit it from my normal user since I change domains in there frequently. This worked just fine on 10.04, but I guess it didn't like it on 10.10

---

### Post by lechien73 on 2010-10-12
Good stuff...glad we got there in the end :)

If everything's working ok, could you please use the **Thread Tools** menu at the top to mark the thread [SOLVED]?

Thanks

---

### Post by Matt Harrison on 2010-10-12
Thanks everyone for helping me get to the bottom of this.

---

### Post by u01p2109 on 2012-09-03
[SOLOVED] by lechien73:
```
xhost +
```

---

