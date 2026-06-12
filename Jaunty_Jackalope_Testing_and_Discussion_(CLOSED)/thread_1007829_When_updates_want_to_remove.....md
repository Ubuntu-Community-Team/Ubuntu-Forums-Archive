---
title: "When updates want to remove...."
date: 2008-12-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2008-12-10
Usually when an update wants to remove some thing, I do not let it as some times the update wasn't complete and removed package was actually needed.
This evening, update wanted to remove 'mbr'. Synaptic describes package as IBM-PC compatible and is the 'master boot record'. I have had enough drama today pertaining to 'booting' (issue with lilo earlier).  Would 'mbr' be safe to remove as my machine is a DELL? 
Also just a note: updates also were for 'thunderbird 3.0', but I am using the thunderbird shredder.

---

### Post by autocrosser on 2008-12-10
I would wait--my system has mbr installed on it & nothing has requested to remove it---waiting for updates to resolve is a good plan......see what happens tomorrow.

I have Shredder in my system also--hand-installed to my /home & I keep the repo thunderbird due to the gnome compat files.

---

### Post by pferraro on 2008-12-10
The only package in the repo with a dependency on mbr is lilo.
There was a lilo update recently - perhaps that was to blame?
[http://launchpad.net/distros/ubuntu/jaunty/+source/lilo/1:22.8-7ubuntu1](http://launchpad.net/distros/ubuntu/jaunty/+source/lilo/1:22.8-7ubuntu1)

---

### Post by ronacc on 2008-12-10
I agree with autocrosser  hold off a while , I also just updated and it did not want to remove MBR , it may just be that the repo ou are using isn't fully sync'd right now . As to your DELL it is an "IBM-compatible" that is an old term for the x86 architecture or more specificly the ISA architecture.

---

### Post by DougieFresh4U on 2008-12-11
> **pferraro said:**
> The only package in the repo with a dependency on mbr is lilo.
There was a lilo update recently - perhaps that was to blame?
[http://launchpad.net/distros/ubuntu/jaunty/+source/lilo/1:22.8-7ubuntu1](http://launchpad.net/distros/ubuntu/jaunty/+source/lilo/1:22.8-7ubuntu1)
I removed 'lilo earlier today after updates to 'lilo' caused machine to do some 'bitchin' about rebooting drama. I had made a thread about it titled:
   	[B]
[SOLVED] Strange warning messege during updates[/B]

you might want to have a look at that thread as I posted what terminal had to say :confused:

---

### Post by autocrosser on 2008-12-11
OK---I looked at my Intrepid install (Fresh install for backup use) & mbr is not installed by default--I would agree that lilo installed it as part of it's install-- The man page with mbr---

.SH DESCRIPTION
.B install\-mbr
installs and configures a Master Boot Record manager on a device.  The
behaviour of the boot manager is determined by the options given on
the command line.
.RI < target >
is the path specifying the device (or file) that the boot manager
should be installed onto.

mbr installs a Master boot record where there is not one before--as far as I know, grub installs a mbr & boot loader--so if you can boot your system---you already have a mbr.....I'll remove mbr from my system & post back, but I think that it is very safe to do so--as pferraro noted:

"The only package in the repo with a dependency on mbr is lilo."

I looked & can confirm that, so I'll check it out.

---

### Post by autocrosser on 2008-12-11
Yes--no problem--as suspected, mbr INSTALLS a master boot record, so if yours is already there---no problem---And as far as I know grub will do that in one shot without needing a "helper" like lilo--I remember that lilo was created long before grub, so Debian using lilo makes sense :)

I deleted mbr & rebooted without drama-----

---

### Post by Gina on 2008-12-11
Ah...  So mbr in this case is NOT the MBR itself but the installer - a very significant difference.  Obviously one would not want to remove the Master Boot Record or NO BOOT!  Thanks autocrosser :)

I've not seen this myself - but OTOH I've not updated Jaunty yet this morning - I'm currently using my "safe" machine, the P4 with Intrepid rather than Jaunty.

---

### Post by autocrosser on 2008-12-11
It seems to me that we went thru this the last time with Intrepid--happened early as now--just something that slipped in with the Debian sync.

---

