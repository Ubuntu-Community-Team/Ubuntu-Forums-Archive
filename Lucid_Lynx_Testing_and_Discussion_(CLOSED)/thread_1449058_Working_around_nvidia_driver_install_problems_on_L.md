---
title: "Working around nvidia driver install problems on Lucid Beta 2"
date: 2010-04-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rliegh on 2010-04-07
Hi. I had a smooth experience with Lucid/i386 when I ran the beta 1 cd, installing the proprietary nvidia drivers went smoothly. 

However, when I downloaded and installed the amd64 version of Beta 2, I was unable to install the proprietary drivers. Both times I kept getting an error that it was unable to complete the installation, and to check /var/log/jockey.log

When I would restart, I would be thrown into console mode -but running startx or gdm manually would work. 

Checking the logs, it appeared that the nvidia kernel module wasn't loading.

This is a complete hack, but it got my system working. I googled to find out if other people had this problem. I read that either the nouveau and/or the vga16fb modules interfered with the nvidia module loading. 

I ran the System->hardware drivers wizard again and it failed again. Then I added the following to my /etc/modprobe.d/blacklist.conf
vga16fb
nouveau

and ran 

update-initramfs -u

And now the nvidia driver shows up as being installed, and X works just fine.

I'm not sure what the right thing to do was, but for now, this works (for me).

---

### Post by Lutin on 2010-04-07
Thanks for that, got my system back working properly.

Only blacklisted vga16fb and nouveau, forgot the other step - update-initramfs -u

But the system is now happy with the nVidia driver again.

Thanks

---

### Post by naudster on 2010-04-07
thanks a lot rliegh for these clear instructions. This thread came up second in a google search, so my nvidia problem was very quickly and easily resolved.

---

### Post by tokyobadger on 2010-04-07
@OP: out of interest, do you have a link for that Beta 2 ISO?

---

### Post by trulan on 2010-04-07
Thanks for the tip!  I had the nvidia drivers working here, and yesterday's updates broke them.  I wasn't expecting that since I don't think there were any nvidia related updates, but blacklisting nouveau and vga16fb got things working again.  Might as well blacklist nouveau here - when I boot the live cd, or boot a fresh install, my screen just says goodbye and powers off.  Ubuntu has never liked my video card...but it's workable, and thanks again for the work-around!

---

### Post by rliegh on 2010-04-07
> **tokyobadger said:**
> @OP: out of interest, do you have a link for that Beta 2 ISO?

You can find the link in this thread -> [Ubuntu 10.04 Beta 2 ISO Testing](http://ubuntuforums.org/showthread.php?t=1447973):guitar:

I'm happy to have helped. :)

---

### Post by tokyobadger on 2010-04-07
weird - I just posted a reply to say thanks and it's not there...

---

### Post by SilverWave on 2010-04-10
Thanks for the workaround this was bugging me.

sudo gedit /etc/modprobe.d/blacklist.conf

Added to bottom of list:
vga16fb
nouveau

I then installed recommended driver.

The wizard downloaded and installed then reported an error
[[Lucid] Jockey gives message that it failed to install nvidia hardware driver]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/552653")

I rebooted and all is working :D

---

### Post by dannyboy79 on 2010-04-10
> **SilverWave said:**
> Thanks for the workaround this was bugging me.

sudo gedit /etc/modprobe.d/blacklist.conf

Added to bottom of list:
vga16fb
nouveau

I then installed recommended driver.

The wizard downloaded and installed then reported an error
[[Lucid] Jockey gives message that it failed to install nvidia hardware driver]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/552653")

I rebooted and all is working :D
the above worked excellent for me also! hurray

---

### Post by CoolGoose on 2010-04-11
You rock!

---

### Post by zenarcher on 2010-04-11
And, I'll add my thanks for your tip!  Worked great for me, as well!

Cheers,
zenarcher

---

### Post by chriss on 2010-04-11
Hi,

i installed the nvidia-current driver, too.

But the bootsplash of ubuntu doesn't come with the resolution of my display. Instead of 1280x1024 it shows perhaps 640x480...

Is there a workaround?

---

### Post by zenarcher on 2010-04-11
> **chriss said:**
> Hi,

i installed the nvidia-current driver, too.

But the bootsplash of ubuntu doesn't come with the resolution of my display. Instead of 1280x1024 it shows perhaps 640x480...

Is there a workaround?

This worked for me.....
[http://ubuntuforums.org/showthread.php?t=1446132&highlight=zenarcher](http://ubuntuforums.org/showthread.php?t=1446132&highlight=zenarcher)

Cheers,
zenarcher

---

### Post by nackless on 2010-04-11
Hi, i tried the above solution but i am still getting the problem.. Seemingly i am able to install the driver but it is not working.. Compositing is not working and when i try to change the appearance settings to extra, it stops responding. the window just freezes..

---

### Post by cariboo on 2010-04-11
Try running:

```
nvidia-xconfig
```

at the prompt, to see if that helps.

---

### Post by nackless on 2010-04-14
tried nvidia-xconfig.. Get following response


nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

ERROR: Unable to write to directory '/etc/X11'.

---

### Post by a-user on 2010-04-14
ofocurse you must run it as root. do "sudo nividia-xconfig"

---

### Post by Eddie Wilson on 2010-04-14
Don't know if this will be useful or not but after a fresh install of beta 2 I was going to install the nVidia driver and started the restricted drivers application The application said that the driver was already installed. I knew it wasn't. I clicked the remove button and after that the restricted drivers application offered to install and activate the nVidia driver. I chose install and everything worked properly. I'm not sure what happened. It could have even been something I did.

---

### Post by GigEther on 2010-04-16
> **Eddie Wilson said:**
> Don't know if this will be useful or not but after a fresh install of beta 2 I was going to install the nVidia driver and started the restricted drivers application The application said that the driver was already installed. I knew it wasn't. I clicked the remove button and after that the restricted drivers application offered to install and activate the nVidia driver. I chose install and everything worked properly. I'm not sure what happened. It could have even been something I did.

This  worked for me.  Excellent!

---

