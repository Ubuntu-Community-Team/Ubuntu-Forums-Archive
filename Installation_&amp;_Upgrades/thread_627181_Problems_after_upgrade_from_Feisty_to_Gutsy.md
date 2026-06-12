---
title: "Problems after upgrade from Feisty to Gutsy"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by swinard on 2007-11-29
I've been having problems in general lately with my Feisty.  I have an ATI FireGL V5000, so nothing would ever display when I booted after I first installed.  I edited xorg.cong and installed fglrx and all that which worked, but sometimes when I rebooted or something, it seemed like things would go back to the way they were.  Even though my xorg.conf was unchanged and fglrx still installed, Ubuntu wouldn't display.  Sometimes restarting again made things work, other times doing a 'depmod' (even though I'm a total noob, don't know what this does, but it was in the instructions for installing fglrx).  But then last night I upgraded to 7.10.  It was a successful upgrade, no errors.  Today, I reboot my machine and find myself with similar problems.  Not only won't it anything display (what happens is that the screen is 'washed' with white pixels, then 'washed' out to a blank screen, no graphics come up), but now I also get errors trying to start up:

Cannot allocate resource region 7 of bridge. [some memory address]
Cannot allocate resource region 8 of bridge. [some memory address]
Cannot allocate resource region 9 of bridge. [some memory address]

There is another error above those but things load too fast for me to see what it was (something with SCF or SCMF or something, I really don't know).  

Can anyone help me?  I'm really new (a week?) to Linux and I enjoyed using it when I was able, but I seem to be having a lot of problems.  I hear ATI hardware is notoriously annoying in Linux, but what can I do to have a stable system that _always_ boots? Help is much appreciated, thanks!

---

### Post by CheShA on 2007-11-29
Back up your xorg.conf, then try using Envy to reinstall your ati drivers; it will download and build relevant kernel drivers  then configure your xorg.conf automatically.  Pretty sweet :) 

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
wget  http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu1_all.deb
sudo dpkg -i envy_0.9.9-0ubuntu1_all.deb
sudo envy -t

```

---

### Post by CheShA on 2007-11-29
...that's always supposing you can get to a bash prompt?  try pressing ctrl+alt+F1 or ctrl+alt+f2     (...f3 , ...f4 etc) when your computer has gotten as far as it's getting. Does any of these get you to a text-mode login?

---

### Post by swinard on 2007-11-29
Well, if I try to boot normally, I can't do anything. Nothing shows up, and trying ctrl+alt+F1 and such doesn't do anything.  Otherwise, I can boot in the Safe Graphics mode and get a command line from there.  I tried to do the 'wget' but it seems as if I'm not connected to the internet.  I'm at my girlfriend's college right now, and they have MAC filtering (but I'm on the list. I'm able to connect in Windows no problem).  So I just get 'cannot resolve' when I try the wget.  I type ifconfig and all it shows is about my localhost (127.0.0.1), so I'm not sure what's up.  When I was first installing fglrx on Feisty when my display wouldn't work, I had an internet connection in th CL in Safe Graphics mode.

I tried downloading that file through Windows, and putting it on my FAT32 shared partition, and then running it from Ubuntu. I got a bunch of failed dependencies, and of course I can't do  apt-get -f install without an internet connection.  I feel like I'm at a loss for now.

---

### Post by CheShA on 2007-11-30
When you boot into single user mode, you usually don't get a connection automatically.  If you know what IP you're supposed to have, what your default gateway is supposed to be you can do this to get connected:

```

ifconfig eth0 up 192.168.0.0      # replace 192.etc with theIP address that you should get
route add default gw 192.168.0.250     # replace 192.etc with your default gateway

```

Be careful though, if you get either of these IPs wrong you could get in serious trouble with Uni (I work in a halls of residence network provider; we always get students assigning themselves the IP address of the DHCP server and stuff like that; wipes out a lot of people!)

Edit: If you can still boot into windoze then you can get your default gateway and IP address by doing ```
 ipconfig /all
```

---

### Post by CheShA on 2007-11-30
> **swinard said:**
>   I feel like I'm at a loss for now.

Don't get disheartened; once this is sorted, think how much you'll have learned and how satisfying it will be  to play with your phat compiz desktop ;)

---

### Post by swinard on 2007-12-03
Well, I finally got around to doing this and I must say, Envy is pretty impressive.  I'm on Ubuntu right now and things seem fine, but I still get the same problems occassionally.  Sometimes when I try to boot, I get that "washed" effect and nothing displays at all.  Other times, Ubuntu starts with no problem.  There is nothing different happening during or between any of these boots, so I'm not sure why that happens.  I still get those "bridge resource region" errors, though.

Also, when I go to visual effects, it no longer says "Composite is not enabled" or whatever, but when trying to enable "Normal" or "Extra" effects, my screen just goes white (mouse still shows up) for about 30 seconds, then reverts back to the 'None' setting.  Any way to make visual effects work?

---

### Post by CheShA on 2007-12-04
:( I've seent the white screen thing you talk about, I had something very similar when using the either of the nVidia (free or restricted) drivers provided by the standard Ubuntu repos, it used to do that when I shut down my PC.

It's likely the problem is that your graphics card is just too new to be properly supported by open drivers (?) , or even the drivers that envy is getting for you.  Have you tried installing the latest ones provided by ATI straight from their site?   They have  "automated installers", apparently,  although I haven't used these so you should check the documentation that comes with them.

32bit:  [http://ati.amd.com/support/drivers/linux/linux-firegl.html](http://ati.amd.com/support/drivers/linux/linux-firegl.html)
64bit : [http://ati.amd.com/support/drivers/linux64/linux64-firegl.html](http://ati.amd.com/support/drivers/linux64/linux64-firegl.html)

if you search their site, you may even be able to get beta drivers which are more likely to fix your problem but may also bring new (probably more minor)  problems with them.

In the meantime, you could try modifying your X server configuration
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
gksu gedit /etc/X11/xorg.conf

```

 Look for a section which reads Device: "ati". Replace "ati" with "vesa".  You should then be able to get decent resolutions (i.e. 1280x1024 at least) stably, but you won't be able to get any composite effects.  (not that you can anyway!).

You're right that ATI are "notoriously annoying" - I was surprised to see they were now doing Linux drivers straight from their site.  As you probably know, historically they have ignored Linux completely so were a nightmare to get running and community driver support was often way behind (compared to nvidia who released proprietary drivers fairly promptly, and as a knock on effect of the popularity that their proprietary drivers gained them, open community drivers usually followed fairly quickly too).   Since AMD have taken ATI over though, they have been making some moves in the right direction but there is still a long way to go.

---

