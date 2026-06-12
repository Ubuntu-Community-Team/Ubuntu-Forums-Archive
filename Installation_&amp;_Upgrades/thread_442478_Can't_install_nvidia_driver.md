---
title: "Can't install nvidia driver"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by doclamb on 2007-05-13
Having downloaded the nVidia driver and trying to install with the command: sudo sh "drivername" i get a prompt for password. I use my userspecified password, but nothing gets typed and the operation is not computed. I need to reboot to get to the password prompt again. I really would like to enable my dualdisplay in Ubuntu. How do I install the nVidia driver?

---

### Post by The Muttster on 2007-05-13
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

Go to the above and take a look at the Envy package. Weirdly, you may need to run it twice...

---

### Post by RTrev on 2007-05-13
> **doclamb said:**
> Having downloaded the nVidia driver and trying to install with the command: sudo sh "drivername" i get a prompt for password. I use my userspecified password, but nothing gets typed and the operation is not computed. I need to reboot to get to the password prompt again. I really would like to enable my dualdisplay in Ubuntu. How do I install the nVidia driver?

The nVidia (I'm never sure how to capitalize that word) drivers are in the repositories.  Just use the System | Administration | Restricted Drivers Manager, or simply go into Synaptic itself and look for it using a search on Nvidia.  The install takes place automatically then.  I don't know what Envy is, or why people use Automatix for this.. it's so easy to find and install it directly like you would anything else in Synaptic.  I went to the nvidia site to make sure, and it always seems like we have the latest drivers in the repos.. and the one the Restricted Drivers Manager installs works just as well but is one version behind, I believe, since it's been proven to be stable.

HTH,
Bob

---

### Post by The Muttster on 2007-05-14
I didn't have much success with what's in the repositories and came across Envy whilst looking for a solution. I have an old GeForce 3 card which I suspect was the problem.

Basically, Envy is a small package that scripts the whole nVidia installation procedure as to nVidia's instructions. It pulls down the latest appropriate driver for your card plus anything else, builds everything you need and changes your Xorg.conf, etc., etc. Other than having to run it twice, it works a treat. I suspect it tries to call something that hasn't been created yet but I can live with the knowledge I can redo the drivers if necessary.

---

### Post by RTrev on 2007-05-14
> **The Muttster said:**
> I didn't have much success with what's in the repositories and came across Envy whilst looking for a solution. I have an old GeForce 3 card which I suspect was the problem.

Basically, Envy is a small package that scripts the whole nVidia installation procedure as to nVidia's instructions. It pulls down the latest appropriate driver for your card plus anything else, builds everything you need and changes your Xorg.conf, etc., etc. Other than having to run it twice, it works a treat. I suspect it tries to call something that hasn't been created yet but I can live with the knowledge I can redo the drivers if necessary.

If you go into Synaptic and search on nvidia, you'll see in the description which driver you need based on the card you have.  Mine is a GeForce 7300 GT, and I found the GeForce 7-series listed under the "new" driver.

I'll tell you how I always do it, and maybe this will help someone.  If not, no harm done.

The very first thing I do after installing and booting to the hard drive is to go into Synaptic, set my preferences, reload, and then exit.

They I call up the Restricted Drivers Manager and enable the new driver.  It downloads it and installs it for me.

Usually at about this point I get the notification that updates are available, so I go and grab them.

Then I run a series of very simply commands.  You can leave out the one about twinview unless you're running multiple monitors:

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

Here, I choose the nvidia driver, and then the screen resolutions I want to have available.

```

sudo nvidia-glx-config enable
sudo nvidia-xconfig --twinview

```

That's about it.  Everything works now.  I usually go into xorg.conf to add a couple options, like turning the Nvidia logo off, and enabling Coolbits.  I clean it up a bit, by removing the references to the devices I don't have.

I've also created a couple of simple scripts to let me over-clock the graphics or set it back to normal.. but I only do the slight over-clock prior to watching movies or doing something in 3d.  If Compiz/Beryl ran on this machine, I'd probably leave the card over-clocked.

I think part of the key to this is going in initially and setting up Synaptic.  Then, later, when I install the new driver, and when I tell the clock to use NNTP to keep the time straight, they have no problem connecting and getting what they need.  I've heard a lot of people say the Restricted Driver Manager doesn't work for them, and I suspect this may be why.

Regards,
Bob

---

