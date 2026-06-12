---
title: "Problems with cd mounting FEISTY"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by aliennet on 2007-04-22
Hi,
    this is my first post, I'm a big reader :-)
The upgrade to Feisty was fine and smooth.
Just a couple of little and annoying problem.
I report the first just in case.
The first with network manager and wi-fi I solved it commenting the line referring to 

#iface eth1 inet dhcp
#wireless-essid ****
#wireless-key ****

in the file /etc/network/interfaces.

The second no way to find a solution reading the forum so here I am.
If I put a cd in my cdrom it starts and I can read it. However I can't find an icon in my desktop and neither in my computer archive.
I thought it would be connect with the change in fstab but I can't find a solution.

My fstab is:
/dev/scd0	/media/cdrom	udf,iso9660	user,auto	0	0

It's not a big problem but it is very annoying.
Any ideas?

---

### Post by omegamormegil on 2007-04-22
I seem to have the same problem on a fresh install of Feisty.  The disk is mounting.  I can browse contents of the DVD through /media/cdrom. I checked gconf-editor and I have apps/nautilus/desktop volumes_visible checked and my flash drive DOES display an icon on the desktop when it is inserted.  I can watch my DVD if I tell VLC to open /media/cdrom etc.  

Thanks for any help.

PS - The CDROM icon is also not showing in the places menu.

My fstab:

# /dev/sda1
UUID=970d8a36-9d33-400b-8253-9bf2bd2afdf3 /               ext3    defaults,erro$
# /dev/sda5
UUID=c2ea2cd9-3f8b-45aa-92e0-e3705309b755 /home           ext3    defaults     $
# /dev/sda2
UUID=0ee99e4f-bfe3-442d-b3e4-c5bbd7ad2c7c none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by aliennet on 2007-04-22
> **omegamormegil said:**
>  [...]  my flash drive DOES display an icon on the desktop when it is inserted.  I can watch my DVD if I tell VLC to open /media/cdrom etc.  

Also in my box, the usb pendrives works properly (better than in edgy)

I start thinking that a lot of people have the same problem...

---

### Post by Dude_Rodgers on 2007-04-23
I have the exact same problem. The cdrom is correctly mounted and readable but there is no icon on the desktop or in places. This is really annoying since i've got never such problems in edgy. I don't know if this has something to do with it but I do have unmount problems with my external usb hdd which has  something to do with hal...
I hope there will be a solution soon for this.

---

### Post by hayim on 2007-04-24
where has my icon gone?!

I had it in edgy, and dapper. it was a drive on the desktop, and if i double clicked it, it mounted the cd (if present, and auto mount off), and then a little cd icon appeared with the cd label... 

now i have nothing :(

there is serious LACK of documentation about how the desktop icons, desktop configuration files, etc work.

help?
thx

---

### Post by aliennet on 2007-04-25
I'm still working around but I haven't find any solution...
Dive all the web but nothing. 
The only thing sure is that it is connected with the new sd* system in place of hd*.

---

### Post by RawMustard on 2007-04-30
Add me to the missing DVD/CD drive icon list.  Exactly the same problems as above!

---

### Post by Argus on 2007-05-05
I'm in this boat as well. I only get an icons on my desktop with audio CDs, 

Sean

---

### Post by aliennet on 2007-06-18
BUMP!
Any news?

EDIT
The problem disappear today (2007/06/21)
It was solved (or rather I think it depends on the kernel upgrading) from 2.6.20-16-386 kernel. Try it.

---

