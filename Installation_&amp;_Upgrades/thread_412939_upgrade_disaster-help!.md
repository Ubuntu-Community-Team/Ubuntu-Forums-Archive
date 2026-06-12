---
title: "upgrade disaster-help!"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by dimeotane on 2007-04-18
All was going well on my upgrade from edgy to feisty.  Unfortunately I closed the lid on my laptop and it went into sleep mode during the install (why?).  I had to power off and reboot... and now it freezes 2 seconds after during booting ubuntu.

Recovery mode gets as far as "Begin: Waiting for root file system..."
In the other kernel boot option listed, I get as far as "* Configuring network interfaces..." 

So what should I do?  Is there a way to resume the upgrade where I left off somehow?

 Should I reinstall from the feisty CD over top  using the same partitions and mount points as before ?  Then reconfigure my setup from scratch?  My /home directory is in another partition, so I'm pretty sure that's safe. 



Any suggestions?

---

### Post by floke on 2007-04-18
try pressing ctrl-c when it gets to network interfaces - it should skip that section
when it does you can edit the file --

(first backup)
sudo cp /etc/network/interfaces /etc/network/interfaces_backup

(to restore simply reverse the above)

then -- 

sudo gedit /etc/network/interfaces

comment out (add # at beginning of line) to all entries except 'lo' - note - if this doesn't work then you might have to uncomment out the relevant entries to get your network up and running again (you need to reboot each time you change this).

Mine for instance is this..

steve@steve-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

# auto eth0
# iface eth0 inet dhcp

# auto eth1
# iface eth1 inet dhcp

# auto eth2
# iface eth2 inet dhcp

# auto ath0
# iface ath0 inet dhcp

# auto wlan0
# iface wlan0 inet dhcp

This will speed up the network interfaces part of the boot

Once you have a boot that is acceptably fast, you can then

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

to compete the process

Hope this helps

* EDIT * If this fails - or takes too long for you - then reload the liveCD as you suggested - that will work fine, but it is always good to try and fix first (just for fun!)

---

### Post by frogotronic on 2007-04-18
Don't close your lid?

Seriously:  Try downloading the LiveCD and boot from that.  Back-up your data and do a fresh install of Feisty Fawn.

- CH


:guitar:

----------------------------

EDIT: try the above post first

---

### Post by floke on 2007-04-18
Even if you do a reinstall - the above steps re: network/interfaces are still a very useful tweak - my bootup time has gone from around 90sec to around 30!

---

### Post by dimeotane on 2007-04-18
Update:  I found a recovery method in the forums.  If your install died and got messed up, and can't reboot properly there is a solution!  

[[COLOR="Red"]READ HERE[/COLOR]]("http://ubuntuforums.org/showthread.php?t=306424")

basically you boot a live cd and mount your root partition (where the upgrade failed)

then you chroot into it 

$ sudo chroot /media/feisty su

and run your apt-get update, upgrade and dist-upgrade


:guitar: wow...  so cool!

---

