---
title: "Xserver-xorg not installed after Dapper -&gt; Edgy upgrade"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by Jæd on 2006-10-27
Hi,

While updating from dapper -> edgy I had a problem with X not coming back up after reboot. 

I tried a "sudo dpkg-reconfigure xserver-xorg" and was told that xserver-xorg wasn't installed correctly. So I installed it, rebooted and all was well...

Just in case this helps anyone...!

---

### Post by zumbi77 on 2006-10-27
I seem to have the same problem. Being quite a noob I have a question: 

How do  I install xserver-xorg from the command line?

---

### Post by Jæd on 2006-10-27
> **zumbi77 said:**
> 
How do  I install xserver-xorg from the command line?

```
sudo apt-get install xserver-xorg
```

Then reboot with: 

```
sudo shutdown -r now
```

---

### Post by kolesarm on 2006-10-27
> **Jæd said:**
> ```
sudo apt-get install xserver-xorg
```
even better:
```
 sudo apt-get install --reinstall xserver-xorg
```


also had to do it - just managed to log in about an hour ago - hopefully you still do have internet access

---

### Post by WrathofthePenguin on 2006-10-27
> **kolesarm said:**
> even better:
```
 sudo apt-get install --reinstall xserver-xorg
```


also had to do it - just managed to log in about an hour ago - hopefully you still do have internet access

Alright - I've found that xserver-xorg is broken or not fully installed after my upgrade. However, when I try to reinstall it I found that I no longer have internet access on that system.

Can I download the iso image for edgy, burn it and install it from there? Or is there a command to initalize the nic and get internet access?

Thanks!

---

### Post by 8oluf7 on 2006-10-27
I've tried the xserver-xorg reinstall and ...

[INDENT]Setting up flashplugin-nonfree (7.0.68~ubuntu3) ...
Downloading...
[/INDENT]
and there it hangs!

What do I do now?

---

### Post by lesliem on 2006-10-27
Jaed,
Your fix for xorg during bootup works fine.
MANY THANKS
:)

---

### Post by 8oluf7 on 2006-10-27
To answer my own question - leave it and go and have a meal. If you're lucky, it'll have sorted itself out when you get back!

---

### Post by Jæd on 2006-10-27
> **lesliem said:**
> Jaed,
Your fix for xorg during bootup works fine.
MANY THANKS
:)

:D Glad it worked... The first time it happened it was a bit of a heart stopper...! Not sure about the flash thing though... Have some dinner and hopefully someone clever will come along...!

---

### Post by tombott on 2006-10-27
ok guys first off thanks for all the info posted. i have tried all of above - instsll and reinstall and on both i get the errror:

Sub-process /usr/bin/dpkg returned an error code (1)

anybody got any ideas?

---

### Post by gobbluth on 2006-10-28
It seems like I am very close to fixing my problem by simply instaliing xserver-xorg. The problem is this, and I have seen a similiar problem in other threads: When I attempt to install or reinstall, it says that it has unmet dependencies, and there are many errors concerning open-office.org. If this helps the diagnosis at all: when I attepmted to --reinstall xserver-xorg-core, it was able to reinstall. 

These boards have saved me before, I pray they can do so once again!

---

### Post by Simon Nuttall on 2006-10-28
> **kolesarm said:**
> even better:
```
 sudo apt-get install --reinstall xserver-xorg
```


also had to do it - just managed to log in about an hour ago - hopefully you still do have internet access

Yes, that sorted the problem for me too. Just sudo reboot afterwards and it seems fine.

---

### Post by tombott on 2006-10-28
well i am still struggling here.
i just get a blank screen now when xserver is starting, back to the drawing board!

---

### Post by jaegen on 2006-10-28
Thanks for this - even if I didn't have a second computer nearby, I'm sure I would have found it in lynx sooner or later.  I can never remember the exact command to reconfigure the X server.

Jaegen

---

### Post by s_h_a_d_o_w_s on 2006-10-29
After upgrading i also cannot login. Stupidly, i did a sudo apt-get remove xserver-xorg and now i can't reinstall it.

---

### Post by s_h_a_d_o_w_s on 2006-10-29
HOw do i forc install xserverxorg?

---

### Post by kelean on 2006-10-29
login under safe mode and then reinstall xsever-xorg

---

### Post by s_h_a_d_o_w_s on 2006-10-29
Tried it gives me same output: It dpeends on balblabla (oppenoffice tc) but they won't be installed and it won't install. :-(

---

### Post by RaiSuli on 2006-10-29
Had the same problem, solved it (not very elegantly) by installing Xubuntu and then choosing Gnome-Desktop as the default option on the startup screen. It now says "Xubuntu" instead of "Ubuntu", but all the xorg and dependency issues have disappeared. There's probably an easier way, but this worked for me.

---

### Post by s_h_a_d_o_w_s on 2006-10-29
I just need a way to make ubuntu install xserver-xorg from terminal. There has to be a way! MAybe unknown dependancies. Please help!!!!!

---

### Post by s_h_a_d_o_w_s on 2006-10-29
I realised i have no more internet, how can i set it up? I don't have the username/password for my internet connection.

---

### Post by gobbluth on 2006-10-29
> **gobbluth said:**
> It seems like I am very close to fixing my problem by simply instaliing xserver-xorg. The problem is this, and I have seen a similiar problem in other threads: When I attempt to install or reinstall, it says that it has unmet dependencies, and there are many errors concerning open-office.org. If this helps the diagnosis at all: when I attepmted to --reinstall xserver-xorg-core, it was able to reinstall. 

These boards have saved me before, I pray they can do so once again!

^^^^Just quoting my original post for context. I'm posting this from Edgy, so I was able to get it to work, and for some reason, all it took was the reinstall of xserver-xorg the OP mentioned. Only problem now is that I have no ubuntu splash screen displayed when everything is booting up, and also a few errors are being thrown when things are booting up.

---

### Post by Jæd on 2006-10-30
> **gobbluth said:**
> ^^^^Just quoting my original post for context. I'm posting this from Edgy, so I was able to get it to work, and for some reason, all it took was the reinstall of xserver-xorg the OP mentioned. Only problem now is that I have no ubuntu splash screen displayed when everything is booting up, and also a few errors are being thrown when things are booting up.


I got this as well.. I had to reinstall usplash to get  it working. I rarely reboot my computer so it wasn't something urgent... :D

---

### Post by Dafydd on 2006-10-31
somehow this did not work for me. also someone suggested "sudo apt-get install xserver-xorg-video-i810", but for some reason the package was not found (neither was "xserver-xorg-video-intel".

but after googling for the package i found a long list of ubuntu alternatives and just downloaded with:

 wget [http://nl.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-i810/xserver-xorg-video-i810_1.6.5-0ubuntu3_i386.deb](http://nl.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-i810/xserver-xorg-video-i810_1.6.5-0ubuntu3_i386.deb)

then i did:

 sudo dpkg -i xserver-xorg-video-i810_1.6.5-0ubuntu3_i386.deb

and finally: 

 sudo dpkg -i xserver-xorg-video-i810_1.6.5-0ubuntu3_i386.deb


Great! After 2 days of complete nightmare, I now have ubuntu back again. The worst thing was that ubuntu went while i was trying to write articles to a tight deadline. I had to rush out and buy a livecd (Suse10.1). Still, have convinced myself that Suse 10.1 is still bulky and slow...

Dafydd

---

