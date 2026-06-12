---
title: "Intrepid beta doesn't even work"
date: 2008-10-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Polygon on 2008-10-04
So i tried to boot up the intrepid beta live cd on my laptop, and it doesn't even work.

When i select 'try before installing", it goes to the loading splash screen, but unless i hold down a keyboard key (wtf?) it doesn't boot up

and then it takes forever to boot up, and when it does, it drops me down to the terminal and then boots up failsafe gnome and says its in failsafe mode because of "(EE) No devices found"

so....yeah. Ubuntu hardy heron works perfectly with my laptop so obviously something is screwing up or regressing.

It is a Compaq presario f767NR laptop, and attacked is an aida32 log of my computer.

i want to report this as a bug but i dont know exactly what the problem is so....saying 'it doesn't work' doesn't really help anyone

---

### Post by waspbr on 2008-10-04
I think I have the same problem as you, my computer will not boot intrepid normally, apparently it had something to do with my motherboards nforce agp contronllers or something like that. 

Since I have intrepid installed alongside with linuxmint elyssa(hardy) I copied my hardy xorg into intrepid and substituted the fglrx by vesa, and now it finally boots (hurray for me). but I still I cannot install the display drivers, the problem should be sorted out once the kernel is updated, (2.26.27-rc8). Now we play the waiting game.

---

### Post by Perpetual on 2008-10-04
> **Polygon said:**
> So i tried to boot up the intrepid beta live cd on my laptop, and it doesn't even work.

When i select 'try before installing", it goes to the loading splash screen, but unless i hold down a keyboard key (wtf?) it doesn't boot up

and then it takes forever to boot up, and when it does, it drops me down to the terminal and then boots up failsafe gnome and says its in failsafe mode because of "(EE) No devices found"

so....yeah. Ubuntu hardy heron works perfectly with my laptop so obviously something is screwing up or regressing.

It is a Compaq presario f767NR laptop, and attacked is an aida32 log of my computer.

i want to report this as a bug but i dont know exactly what the problem is so....saying 'it doesn't work' doesn't really help anyone

There is already a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247") open for this.  I have mentioned in other posts that it seems there are issues with 2.6.27 kernels and nvidia or amd or something else.  I can not boot any distributions that are currently shipping the 2.6.27 kernel.  Huge regressions and I feel that the developers early on that were hesitant about shipping 2.6.27 kernels were spot on.  The 2.6.27 kernel may have new hardware support but it's failing with hardware that worked fine under the 2.6.26 kernels.  I am currently realizing that I may not be using any new distributions until 2009 when these problems are sorted out.

---

### Post by bigbear2350 on 2008-10-04
Or just compile a 2.6.26 kernel on intrepid

---

### Post by Perpetual on 2008-10-04
> **bigbear2350 said:**
> Or just compile a 2.6.26 kernel on intrepid

How would I do that if I can't install 8.10?

---

### Post by Sef on 2008-10-04
> the problem should be sorted out once the kernel is updated, (2.26.27-rc8). Now we play the waiting game.It will be 2.6.27-5.8.  The bug is fixed in that one.  It will be released within a few days.

---

### Post by Perpetual on 2008-10-04
> **Sef said:**
> It will be 2.6.27-5.8.  The bug is fixed in that one.  It will be released within a few days.

Sef, thanks for responding.  Will this show up in the Ubuntu daily builds in the near future?

---

### Post by jerrylamos on 2008-10-04
Tried kernel 2.6.26-1-rt with no go.  Still get black screen with pointer, The pointer moves, so Xwindows is still up, but nothing on the keyboard works except power off.  See bug 277344.  .xsession-errors still can't find gnome-wm. 

So I installed xfce4 which does work.  Odd combination, all the Ubuntu Gnome stuff is there, just gnome desktop won't come up.

I'm keeping this updated since update manager and synaptic and ... work with xfce4.

Jerry

---

### Post by inportb on 2008-10-04
You could specify "ati" instead of "vesa" and get slightly better graphics support in the interim...

---

### Post by Sef on 2008-10-04
> Sef, thanks for responding.  Will this show up in the Ubuntu daily builds in the near future?

It will be there and in the updater in a few days.

---

### Post by Polygon on 2008-10-05
> **Sef said:**
> It will be 2.6.27-5.8.  The bug is fixed in that one.  It will be released within a few days.

wait, if the bug is fixed, the how come the bug report is still 'triaged'? or has no one just gotten around to updating it yet

---

### Post by forcecore on 2008-10-06
Looks like i have similar bug with Esprimo v5535 with SiS mirage 3+ graphics that shows same Gnome failsafe message.

---

### Post by Polygon on 2008-10-06
if you have the exact same symptoms as me (having to hold a key down to boot) then go to the bug report and provide the logs that they are asking for so it can get fixed faster

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247)

---

### Post by forcecore on 2008-10-06
no it just loads until same exactly Gnome safe mode message appeared, provided bug report but i cannot get logs out of laptop and it wont display drives where to save, just i do not have skills to save logs with other way.

---

### Post by Polygon on 2008-10-06
seems like a different bug, but here are the console commands to save the logs to a usb key.

sudo mkdir /media/USB
sudo mount -t vfat /dev/sdb1 /media/USB
uname -a > /media/USB/uname-a.log
cat /proc/version_signature > /media/USB/version.log
dmesg > /media/USB/dmesg.log
sudo lspci -vvnn > /media/USB/lspci-vvnn.log
sudo umount /media/USB

i myself had to do a 'sudo su' to switch to the super user because it kept giving me 'permission denied' if i tried to save the logs to my usb key, even if i used sudo.

---

### Post by forcecore on 2008-10-07
FOUND ANSWER for Esprimo v5535, i used sudo nano xorg.conf to enter driver "vesa" and it loaded desktop SO all developers please make vesa default driver if no devices found. BUG SOLVED and developers can fix that.

Some developer just forgot to insert default driver automatic force loading if no devices.

i used Ubuntuforums rbmorse help (how strange that solution from other type bug worked)

cd /etc/X11<enter>      <---note the uppercase "X"
sudo nano xorg.conf<enter>

Section "Device"
    Identifier    "Configured Video Device"
    Driver         "vesa"
EndSection

---

### Post by Polygon on 2008-10-07
the bug is not fixed. it says no devices were found, but on my laptop and yours, there SHOULD be a device that is found.

---

### Post by forcecore on 2008-10-07
it showed same Gnome failsafe EE no device message but this fixed and loaded desktop, do you tried this?

---

### Post by Perpetual on 2008-10-12
As of October 12, 2008 32 bit daily build issue still exists.  I attached my logs to the [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247").  Hope this gets fixed.

---

