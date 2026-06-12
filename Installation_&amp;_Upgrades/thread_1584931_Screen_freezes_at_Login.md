---
title: "Screen freezes at Login"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by santana007 on 2010-09-29
I recently upgraded from Lucid to the latest beta of Maverick. Everything went fine. Today, Update Manager came on with *updates are available*. Started update, went OK until "Applying Changes" stopped at about 3/4 of way through. The Indicator Applet Session Icon went [COLOR=Red]RED[/COLOR]  showing Restart required to complete updates. Restarted but stops at  login screen but no login available. Have coloured background with white  rectangle in centre with the name I gave to computer (touchubuntu) and  white bar at bottom with current date and time. Mouse cursor is frozen  and keyboard doesn't work. Must do a manual reset. Recovery selection  and previous kernels do not work. Recovery halts part way through. Would  like to recover Home folder, emails and Firefox Bookmarks. Tried Live  CD but  Home folder has a X on it, says do not have necessary  permissions to view contents of file. Is there anyway to fix the Login  situation or recover Home folder, etc?

---

### Post by scotty boy on 2010-09-30
I had the exact same problem and the following worked:

1. - Download/grab a live cd.

2. - Start live cd and when it loads the desktop open a gnome-terminal.

3. - Create this dirs:
```

sudo mkdir /media/lucid
sudo mkdir /media/lucid/proc /media/lucid/dev /media/lucid/etc
```

4. - Mount your linux partition (for me sda1, yours may be different):

```
sudo mount /dev/sda1 /media/lucid
```

5. - Bind the dirs:

```
sudo mount -o bind /proc /media/lucid/proc
sudo mount -o bind /dev /media/lucid/dev/
sudo mount -o bind /dev/pts /media/lucid/dev/pts
```

6. - Copy this file

```
sudo cp /etc/resolv.conf /media/lucid/etc/resolv.conf
```

7. - Update your real linux partition with chroot:

```
sudo chroot /media/lucid apt-get update
```

8. - Reconfigure everything with chroot:

```
sudo chroot /media/lucid dpkg-configure -a
```

9. - If you have some broken package:

```
sudo chroot /media/lucid apt-get -f install
```

10. - Reboot and voilá! Fixed for me.

---

### Post by santana007 on 2010-10-01
> **scotty boy said:**
> I had the exact same problem and the following worked:

1. - Download/grab a live cd.

2. - Start live cd and when it loads the desktop open a gnome-terminal.

3. - Create this dirs:
```

sudo mkdir /media/lucid
sudo mkdir /media/lucid/proc /media/lucid/dev /media/lucid/etc
```4. - Mount your linux partition (for me sda1, yours may be different):

```
sudo mount /dev/sda1 /media/lucid
```5. - Bind the dirs:

```
sudo mount -o bind /proc /media/lucid/proc
sudo mount -o bind /dev /media/lucid/dev/
sudo mount -o bind /dev/pts /media/lucid/dev/pts
```6. - Copy this file

```
sudo cp /etc/resolv.conf /media/lucid/etc/resolv.conf
```7. - Update your real linux partition with chroot:

```
sudo chroot /media/lucid apt-get update
```8. - Reconfigure everything with chroot:

```
sudo chroot /media/lucid dpkg-configure -a
```9. - If you have some broken package:

```
sudo chroot /media/lucid apt-get -f install
```10. - Reboot and voilá! Fixed for me.

Thank you. Sorry for the delay in responding but I was out of town for a couple of days(medical reasons). I found these commands which allowed me to access the *HOME* folder from the Live CD.

1) Open a Terminal
2) sudo mount /dev/sda5 /mnt (sda5 is my Linux partition, dual boot with XP)
3) gksu nautilus (or sudo nautilus)
4) Open Filesystem in left hand pane in Nautilus window and open mnt folder on Live CD
5) Open *home *folder and select View->Show Hidden Files to see everything

Now I need to backup the *Home* folder  before I go any further or try anything else I wish to backup to my other computer(laptop) over my home network which dual boots Vista and Lucid and to a USB drive (in the desktop having problems with).Investigating the best way to do this. Not sure if drag&drop to the USB drive is good enough

---

### Post by santana007 on 2010-10-03
You are an officer and a gentleman. Your instructions worked like a charm. The only thing different I had to do was to change the reconfigure line to: *dpkg --configure -a*
I think I lost the option to boot in Windows XP in the grub menu but my Windows partition is still there. I'm sure I can find out how to fix this. This is an old computer with a Pentium III and doesn't run very fast in Windows anyway. That's why I run Ubuntu. 
I have to admit that I don't really understand what all these lines of code actually do but it worked. Something else to study. The learning never stops. Thanks again.

---

### Post by schworak on 2010-11-28
> **scotty boy said:**
> I had the exact same problem and the following worked:

1. - Download/grab a live cd.

2. - Start live cd and when it loads the desktop open a gnome-terminal.

3. - Create this dirs:

(other steps not quoted)





YOU ROCK!

I am still learning Linux and you saved my bacon on this one. I was just about to do a full install from scratch and these steps (with minor variations) helped me save my current install and got me back up and running. 

THANK YOU! THANK YOU! THANK YOU!

Thanks for the 5 star answer!   :KS:KS:KS:KS:KS

---

### Post by santana007 on 2010-11-28
> **schworak said:**
> YOU ROCK!

I am still learning Linux and you saved my bacon on this one. I was just about to do a full install from scratch and these steps (with minor variations) helped me save my current install and got me back up and running. 

THANK YOU! THANK YOU! THANK YOU!

Thanks for the 5 star answer!   :KS:KS:KS:KS:KS

Yes,this procedure is extremely valuable. Did a full install of Maverick to an 8 GB usb stick and same thing happened after an update. Used a  1 GB live usb stick and the above procedure and rescued the system.:cool::D

---

### Post by Penguin=) on 2010-11-28
Great stuff!

---

### Post by LeonardoDaInvinci on 2010-11-29
This procedure sounds to me a promising hope. Here is what my problem is:

* I had an excellently running Ubuntu (with KDE as well) 10.04 lucid lynx.

* Recently I tried to upgrade to Kubuntu 10.10

* It did, and asked me to reboot, there starts the problem; I see nothing working, no login, only blank screen.

* I tried with Live CD, live cd didnt work either. That might be problem with my hardware/drivers etc.

However, I want to land back on Luncid Lynx, since my Live CD of 10.04 (lucid lynx) boots well and I can access desktop as usual.

I would appreciate your response, if you could guide me, or if this procedure you have mentioned works for me to revert.

thanks,
Leo.

---

### Post by geek6oy on 2010-12-19
Did a fresh install on an old Toshiba Pentium III notebook with an S3 graphics adapter using a downloaded 10.10 final release iso image.  The install went fine, but after performing and update via update-manager I had the same problem - stuck at the login screen, unresponsive keyboard and mouse.

This procedure worked for me.  Thanks a lot!

---

### Post by Payteer on 2011-01-06
Hello this saved my bacon  on the dpkg-configure -a that should be dpkg --configure -a, as this what worked for me
again thanks for your help on this.

---

### Post by RussellEngland on 2011-01-12
Brilliant!!! Thank you!!!

Like the others are saying, I just need to change [I]dpkg --configure -a

[/I]Cheers, Russ

---

### Post by RussellEngland on 2011-01-12
Brilliant!!! Thank you!!!

Like the others are saying, I just need to change [I]dpkg --configure -a

[/I]Cheers, Russ

---

### Post by alex86 on 2011-04-28
I nice solution to this problem, which I had a week ago, is to plug in a USB keyboard at the apparently frozen login. Actually, it is not, you can see the clock is working. Then execute 

apt-get -f install

and everything returns to normal! At least it worked for me

---

