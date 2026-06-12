---
title: "is it possible to apt-get from DVD only with working internet connection?"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by PryGuy on 2007-04-21
Good day!
I've got a postinstall script that installs stuff after the Ubuntu installation. I want to make it act in an unattended way, so no user interaction would be neccessary. One of the points is that I have many people that neglect Linux because it doesn't play (as they think) MP3s or DivX movies or something. Another piont is that I like to write a script and forget about it. 

But there's another problem, I do not have unlimited internet traffic in my town so DVD is the best way for me. I wrote something like:> sudo aptitude install -y build-essential libc6 libqt3-mt language-support-ru nvidia-glx gparted samba nfs-server ntp alien totem-gstreamer But as far as I understand it will first try to grab the files from the internet if there's an internet connection and will use Ubuntu DVD only if the first way fails. 

So, is there some way that would help me grabbing these packages from the DVD not from the internet without doing some tricks with Synaptic?

Thank you!

---

### Post by NeoTaoistTechnoPagan on 2007-04-26
Normally, put the CD or DVD in your drive and use

```
sudo apt-cdrom
```

This will index the disk and get it ready to use.

Now - that's the way it *SHOULD* work - YMMV. I had a bit of a problem getting the latest Feisty DVD to work in this manner - so here's what I did.

When I inserted the DVD the system (Kubuntu) automatically mounted it at /media/Ubuntu\ 7.04\ i386/
I thought - well - confusing, but I get it. It mounted it under /media as whatever name the disc is.

I noticed /media/cdrom is a symlink to /media/cdrom0 (this was a dual drive - a CDR and a DVD reader)

So I had to use a slight work-around to get it to work properly with apt-cdrom.

This is what worked for me:

```

sudo -s
(enter password)
cd /media
rm cdrom
ln -s /media/Ubuntu\ 7.04\ i386/ /media/cdrom
```

Now apt-cdrom will work without complaints and you can install from the disc. By default - the system will look to the disc first and get what it can from there and get whatever else from the net.

Just make sure that you delete the symlink for /media/cdrom and reset it to /media/cdrom0 when done.

---

