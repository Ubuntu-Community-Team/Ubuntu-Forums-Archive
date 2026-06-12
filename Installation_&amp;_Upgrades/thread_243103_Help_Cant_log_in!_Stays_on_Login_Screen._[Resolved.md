---
title: "Help Cant log in! Stays on Login Screen. [Resolved]"
date: 2006-08-24
forum: Installation &amp; Upgrades
---

### Post by noelneuw on 2006-08-24
Hi there. 
Im new to ubuntu and havent tried linix for years.

Well Ubuntu has certainly been an adventure :D 
Never a dull moment.

I just applied the latest patch for xserver, as I had installed the buggy patch and Xserver would not start. Now
Xserver starts but when I try and log in it just brings me back to the logon screen. 
I can logon succesfully via the Terminal so its not my password

Could somemone please help.
Thanks
Noel.

May we live in interesting times!

---

### Post by noelneuw on 2006-08-24
It Seems Gnome is not working. I am able to login to KDE.
I'll search for a Gnome reinstall option
Thanks
Noel.

---

### Post by noelneuw on 2006-08-24
Latest Update!

Fixed my problem.
It seems Gnome has a problem with my highest resolution 1600*1200
on my graphics card ATI X1600 or something.

As mentioned before I managed to logon into KDE but I wasnt able to
change my resolution! it was on max which makes reading docs pretty hard.
Age getting to me :-) 

A later upgrade or something fixed it!

So I edited my /etc/X11/xorg.conf file and deleted the high resoltions
form my screen/mode sections.

And Bingo, I can log back into gnome. :-)

BTW does anybody know how to tell XServer not to default to the highest resolution.

I seem to remember a couple of years ago, that if you place a "*"
in front of the resoltion entry, then XServer would use that as its
default.

something like "1280*1024" *"1024*768" "800*600" 
where 1024 * 768 was the default.

Anyway hope this helps someone else.
Noel.

---

### Post by noelneuw on 2006-08-24
Ahhhh Bugger!.
](*,) 

That Xwindows update really screwed things up.
Just as I managed to get my system perfect I ran the update and 
bang went My XServer. 

I had managed to install the the ATI drivers, My 3d card was working 
great, i was running on the smp core. 

Now I just ran glxinfo and I'm back
to vesa mode, no 3D, and using MESA.

I have tried apt-get install according to this site in order to
get my ATI drivers back but apt get says its already installed.

SO the login problem with the high resolution on GNOME applies to
the VESA Mode not to the ATI Driver

Anybody have any hints on how to reinstall the ATI 3D drivers.

Thanks
Noel.

---

### Post by adds2one on 2006-08-24
Everything you should need to know to install your ATI driver should be here:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by noelneuw on 2006-08-25
Thanks
I had already done method 1 before the XServer upgrade mess.
I did however notice that at the bottom of the page apt-get install
has a "--reinstall" option.

I tried that on the xorg-driver-fglrx and followed the commands 
from there. 

Rebooted but was still running with the mesa driver.
fortunately it seems scripted updates to xorg.conf creates backups.
copied over xorg.conf with one of the backup config files for fglrx

if anyone is interested the backup config can be identified
by looking in the "Device" Section for a Driver "fglrx" entry.

rebooted and I had 3d back.
Thanks.

---

