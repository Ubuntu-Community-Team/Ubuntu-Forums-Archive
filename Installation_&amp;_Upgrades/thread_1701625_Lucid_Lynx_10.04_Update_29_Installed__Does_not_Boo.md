---
title: "Lucid Lynx 10.04 Update 29 Installed | Does not Boot"
date: 2011-03-06
forum: Installation &amp; Upgrades
---

### Post by deceaseddolphin on 2011-03-06
Hi,

Caught totally off-guarded by an Ubuntu update. I had this problem of 'partial upgrade' which wouldn't complete no matter how many times i tried. I followed a suggestion to 'mark all upgrades in synoptic manager' posted in this forum. All updates installed fine but when system started booting, it wouldn't boot. I used gdb command in recovery mode to get back in GUI mode. Please check the boot error [here]("http://ideasandbeyond.blogspot.com/2011/03/ubuntu-boot-error.html").

Not only this, the network manager notifications is not displayed at the top panel. I tried to right click and add notification area but network connections are not displayed (volume, dropbox and google desktop icons are visible). I tried to edit network connections under
System -> preferences -> network..... but couldn't find network option there.

I tried to use internet using a wired connection, didn't work!

Any help will be much appreciated. Struck by this boot error derailing my research work!

---

### Post by dirty_harry on 2011-03-06
Assuming you have access to another working machine:

First of all I would make a backup using clonezilla. At least copy your important files to another disk/usb... To prevent greater loss.

Afterwards try to get your wired connection working:
[https://help.ubuntu.com/9.10/serverguide/C/network-configuration.html](https://help.ubuntu.com/9.10/serverguide/C/network-configuration.html)

Form here on I only have suggestions form what I found googling:```


$: sudo apt-get update
$: sudo dpkg –configure -a
$: sudo apt-get upgrade –fix-broken
```

good luck

---

### Post by deceaseddolphin on 2011-03-06
Thank you for the reply harry!

I will take the back-up and try your suggestion.

Thanks!

---

### Post by deceaseddolphin on 2011-03-06
I included two lines in /etc/network/interfaces

auto eth0
iface eth0 net dhcp

and wired internet started working!

problem with wireless internet remains though.

---

### Post by dirty_harry on 2011-03-06
I think it is time to hit shutdown for me and go to bed. This is the second time I misunderstood what was the going. Actually I thought you're fighting with a broken update and I was worried that I might not know enough to help you with an utterly broken system.

But I'm happy that I could help you.

good night :smile:

---

### Post by deceaseddolphin on 2011-03-06
yeah looking back, I think my message didn't convey enough but it's fixed now. even i was preparing for the worst!

good part is wireless is back again after I rebooted, yay!

thanks!

---

### Post by mörgæs on 2011-03-06
Good you got it solved.


Regarding partial upgrades: The short answer is "don't go there unless you are experienced".

[http://ubuntuforums.org/showthread.php?t=1641400](http://ubuntuforums.org/showthread.php?t=1641400)

---

### Post by deceaseddolphin on 2011-03-06
I now understand why there are partial upgrades. however important services like network manager must not be removed in any kind of upgrades!

thanks for your insights, you've been helpful!

Cheers!

---

