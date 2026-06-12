---
title: "Creating my own Ubuntu version."
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by Montezuma45 on 2010-08-23
Okay, here's the story.  My bosses are bringing in 750-3000 laptops for me to setup with Linux.  So far so good, pop in disk, couple of "Yes/No" prompts and system is loaded.  Update to newest version, ready, set, go.

Snag: I need to install Skype and a couple of other programs and set Firefox home page.  A few computers, no biggie, this many will slow the process.

What I need to do is make one system as I need it and make my own Ubuntu 10.04-x version from it.  

I need detailed instructions because the first computers arrive in a week. [-o<

---

### Post by kansasnoob on 2010-08-23
If the hardware is identical look here:

[http://remastersys.sourceforge.net/index.html](http://remastersys.sourceforge.net/index.html)

If not you can do very simple post install "scripts" like I always do (in Lucid):

```
sudo chmod -x /etc/grub.d/20_memtest86+

```

That get's rid of the Memtest option in grub2.

```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close"
```

That puts my buttons back on the right side.

```
echo -e "\ndeb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt  all main" | sudo tee -a /etc/apt/sources.list > /dev/null && sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29 && sudo apt-get update && sudo apt-get install firefox-mozilla-build
```

That installs "ubuntuzilla" so I'm always running the latest stable release of Firefox.

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

That installs the medibuntu repo so I can get a few goodies like "libdvdcss2 & w32codecs".

Then:

```
sudo apt-get install abiword gnome-alsamixer gparted gphoto2 gthumb gtkam gtkam-gimp gufw hplip-gui mozilla-plugin-vlc vlc-plugin-pulse startupmanager totem-mozilla totem-plugins-extra totem-xine ubuntu-restricted-extras gnome-themes-more gnome-themes-extras shiki-colors-metacity-theme gnome-backgrounds nautilus-gksu sensors-applet desktop-base libdvdcss2 w32codecs zsync


```

You'll see that's just a list of each "package". Of course the packages you may wish to install will vary. And if a package is unavailable that will FAIL!

Additionally, if I want the same "profile" for each machine I simply create a backup of the host OS's /home and copy it to each machine. But if the username is going to be different, which it's likely to be, I only back up parts and pieces.

I'm just not sure what you intend here. You could install all with a username of "Iamtheboss" and then assign a username for each user that's going to use that computer.

OTOH that could be a real kludge. A lot of it depends on the level of security desired. I take care of about 34 computers. I can't imagine caring for 750 - 3,000.

For that matter I can't imagine someone saying, "I'm going to have you build between 750 and 3,000 computers!"

That's a wide spread. What kind of network is involved?

---

### Post by kansasnoob on 2010-08-23
> For that matter I can't imagine someone saying, "I'm going to have you build between 750 and 3,000 computers!"

Just thought to add:

"I'd literally crap myself if that happened"!

I'm still trying to sort out things with a KVM switch where I have three boxes with two monitors ................ two weeks so far and every time I think I have things sorted I find that I don't!

Honestly .............. 750 to 3,000 computers?????????????

Is this the freaking Pentagon?

---

### Post by Montezuma45 on 2010-08-23
LOL.  This will be over a 5 month time period.  The company provides laptops to the users and after completion, the user gets to keep the computer.

Last year, I cloned 400+ EMacs (50 lbs. each).  This year (thankfully), we are going with laptops.  Obviously, we are not using the top of the line laptops.  :D

I use a KVM but only one monitor, can't think of why I'd need two monitors.  I use mine with 2 Linux servers and two Windows machines.

---

### Post by Montezuma45 on 2010-09-10
After a few bad DVD's, I found out that they moved the site to [http://www.geekconnection.org/remastersys](http://www.geekconnection.org/remastersys)

With Grub2, you need to use karmic option.  After making a backup version, I was on my way.  Thanks.

---

