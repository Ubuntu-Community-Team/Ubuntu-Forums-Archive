---
title: "Xserver crashes after upgrade to Dapper"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by rpalyvoda on 2006-06-01
Hi,

I just upgraded from Ubuntu 5.10 to Dapper. Everything was Ok, but when I rebooted my PC, xserver crashed.

Has anyone else experienced this problem?

Is it possible that it it's all because of my video card? I use Nvidia GeForce 4 420 on Toshiba Satelite laptop. I recall I had the same problem a few monthes ago when I decided to install the latest Nvidia driver from  ([http://ubuntuforums.org/showthread.php?t=139264&highlight=nvidia+drivers](http://ubuntuforums.org/showthread.php?t=139264&highlight=nvidia+drivers))

Can someone help me?

---

### Post by matrooswolf on 2006-06-01
Try changing Nvidia to nv or vesa in your Xorg.conf, and installing the nvidia driver from the repostories afterwards. 
Hope it helps.
```
sudo gedit /etc/X11/xorg.conf
```
section "device"
driver "nv" or "vesa" instead of "Nvidia"

---

### Post by tonyr on 2006-06-01
This is happenning to a lto of people.  I haven't seen anything definitive on the
right way to do it.  This is suggested a lot:

After X crashes and you are left at a console, login and
```

sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg 
sudo dpkg-reconfigure gdm
sudo /etc/init.d/gdm start

```

I'm assuming you are using Ubuntu(Gnome).  Substitute **kdm** if you are
using Kubuntu(KDE).

EDIT:  The suggestion from **matrooswolf** is a good one, too.

---

### Post by th3gh05t on 2006-06-01
[QUOTE=tonyr]This is happenning to a lto of people.  I haven't seen anything definitive on the
right way to do it.  This is suggested a lot:

After X crashes and you are left at a console, login and
```

sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg 
sudo dpkg-reconfigure gdm
sudo /etc/init.d/gdm start

```[/QUOTE]

When I normally boot up, a login is trying to be displayed, but there are inbound and outbound connections flying across the screen and it makes me unable to login.

I can use the computer if I use the "Recovery Mode" kernal.

---

### Post by tonyr on 2006-06-01
[QUOTE=th3gh05t]When I normally boot up, a login is trying to be displayed, but there are inbound and outbound connections flying across the screen and it makes me unable to login.

I can use the computer if I use the "Recovery Mode" kernal.[/QUOTE]

Have you tried CTL-ALT-F2 to get a second console?

---

### Post by brady on 2006-06-01
To upgrade I changed my sources to all dapper, then:

sudo apt-get update
sudo apt-get upgrade

Thought, wow, this is fast.  Reboot, Xserver crash.  Some PCMCIA errors.  Thought...wait, I need to:

sudo apt-get dist-upgrade

Waiting for that to finish and hoping it fixes my probs.

---

### Post by th3gh05t on 2006-06-01
[QUOTE=tonyr]Have you tried CTL-ALT-F2 to get a second console?[/QUOTE]

Yea, but that doesn't help.

I get this error when I run "sudo dpkg-reconfigure gdm":

> 
invoke-rc.d:initscriptgdm, action "reload" failed.
install-menu: Warning: Unknown identifier 'removemenu' on line 47 in file /etc/menu-methods/xdp-desktop-entry-spec-apps. Ignoring.
install-menu: Warning: Unknown identifier 'removemenu' on line 51 in file /etc/menu-methods/xdp-desktop-entry-spec-apps. Ignoring.


---

### Post by brady on 2006-06-01
success with 

sudo apt-get dist-upgrade

---

### Post by th3gh05t on 2006-06-01
Hi, 

I have figured out the problem.

I was running programs while the dist-upgrade was running the first time. This caused the problem, and also a combination of myself selecting one of the wrong options when running "sudo apt-get dist-upgrade".

There is a part in the upgrade where it completely stops and ask for your interpertation. The stop will reflect changes made to the gmd conf file or something. It will say that you the default selection is "N". ([default=N])

YOU DONT WANT TO SELECT "N". 

You want to select selct "Y" (yes) to over irde the file that is currently being used in the Breezy Badger. 

This will solve all of you rprobelms!

th3gh05t

---

### Post by rpalyvoda on 2006-06-02
Thanks for your help!

Finally, I followed Tonyr's advice, and it worked, and I'm now enjoying Dapper ;o)



[QUOTE=tonyr]This is happenning to a lto of people.  I haven't seen anything definitive on the
right way to do it.  This is suggested a lot:

After X crashes and you are left at a console, login and
```

sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg 
sudo dpkg-reconfigure gdm
sudo /etc/init.d/gdm start

```

I'm assuming you are using Ubuntu(Gnome).  Substitute **kdm** if you are
using Kubuntu(KDE).

EDIT:  The suggestion from **matrooswolf** is a good one, too.[/QUOTE]

---

### Post by heffo_j on 2006-06-02
Thank you all. I used a combination of all of the above to solve the problem. I now have my screen up.

Best regards
John
(I'll ow shut this windows box down)

---

