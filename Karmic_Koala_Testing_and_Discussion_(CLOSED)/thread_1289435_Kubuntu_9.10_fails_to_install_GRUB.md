---
title: "Kubuntu 9.10 fails to install GRUB"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Wa1k3rTXRang3r on 2009-10-12
Yea. basically the title says it all.
I was installing Kubuntu 9.10 from a live cd and at about 94% it gives a message saying that it failed to install GRUB.

This is quite a problem since now my computer cannot boot.

Any help would be greatly appreciated!

---

### Post by ranch hand on 2009-10-12
Try this;

[http://grub.enbug.org/Grub2LiveCdInstallGuide](http://grub.enbug.org/Grub2LiveCdInstallGuide)

---

### Post by Wa1k3rTXRang3r on 2009-10-12
Thanks!! I'll try it out!

But I was just wondering...
Since I already have Ubuntu 9.10 Beta installed is there any I could tell the Kubuntu installation to not install a new GRUB, and instead just use the one from Ubuntu?

---

### Post by ranch hand on 2009-10-12
Have you tried to boot to the Kubuntu install from Ubuntu?

I would like to have it on both because of the ease of changing which one you are using.  That way you can set them up slightly differently and see how you want it to be.

---

### Post by VMC on 2009-10-12
> **Wa1k3rTXRang3r said:**
> Thanks!! I'll try it out!

But I was just wondering...
Since I already have Ubuntu 9.10 Beta installed is there any I could tell the Kubuntu installation to not install a new GRUB, and instead just use the one from Ubuntu?
Following Ubuntu's Ubiquity, uncheck the "Install boot loader" below:
[IMG]http://www.23hq.com/23666/2589677_e5743eb27be695070e262aef443313fc_standard.jpg[/IMG]

---

### Post by Wa1k3rTXRang3r on 2009-10-12
Oh I see.

And no i haven't tried booting to it from Ubuntu. How would I go about doing so?

---

### Post by ranch hand on 2009-10-12
If you can boot to Ubuntu.

run;
```

sudo update-grub

```
and, assuming that you are SATA and on one drive;
```

sudo grub-install /dev/sda

```
This will set your Ubuntu as boot/root and the update should have your Kubuntu written to the grub.cfg file for Ubuntu.

---

### Post by Wa1k3rTXRang3r on 2009-10-12
I managed to boot into Kubuntu using the SuperGRUB CD. However now I am trying to install GRUB using

sudo apt-get install grub

and it keeps giving me the error message

Package grub is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source.

So how exactly am I supposed to install GRUB then?

lol

---

### Post by VMC on 2009-10-12
> **Wa1k3rTXRang3r said:**
> I managed to boot into Kubuntu using the SuperGRUB CD. However now I am trying to install GRUB using

sudo apt-get install grub

and it keeps giving me the error message

Package grub is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source.

So how exactly am I supposed to install GRUB then?

lol
You don't since grub2 is already installed on your karmic.

---

### Post by Wa1k3rTXRang3r on 2009-10-12
Well I'm trying to avoid having to keeping Ubuntu if possible.

What is the command in the terminal to install GRUB because it seems to be all over the place. i.e. the error message tells me that its one package, then I try to install that package and it says that its another.

So far I've tried

sudo apt-get install grub
sudo apt-get install grub-common
sudo apt-get install grub2

No luck. Actually when I run 

sudo apt-get install grub-common it says that it is already the newest version, which I know for a fact it isn't since I didn't install GRUB.

This is incredibly confusing!

---

### Post by VMC on 2009-10-12
> **Wa1k3rTXRang3r said:**
> Well I'm trying to avoid having to keeping Ubuntu if possible.

What is the command in the terminal to install GRUB because it seems to be all over the place. i.e. the error message tells me that its one package, then I try to install that package and it says that its another.

So far I've tried

sudo apt-get install grub
sudo apt-get install grub-common
sudo apt-get install grub2

No luck. Actually when I run 

sudo apt-get install grub-common it says that it is already the newest version, which I know for a fact it isn't since I didn't install GRUB.

This is incredibly confusing!

I'm a little confused here. Straighten me out. You have both ubuntu and kubuntu installed on you pc. grub2 is assigned to karmic. Now you want to reassign grub to kubuntu. Is this right?

---

### Post by ranch hand on 2009-10-12
Let me see if I have this straight.  You booted to Ubuntu and used its grub2 to boot to Kubuntu.

Now you want to use Kubuntu to boot from so you are trying to install grub2.

If this is the case then you need to go to synaptic and check to see what in flinderation you have installed on your system before you go trying to install anymore.

You should have Grub2 (meta package for grub2), grub-common and grub-pc.  You should not have any package that has to do with grub version .97 (grub-legacy).

Get rid of those you should not have.  Reload synaptic.  The three file you should have need to be installed or reinstalled.

If this goes as it should then you need to run "sudo update-grub" and "sudo grub-install /dev/sda" or whatever should be after /dev in your box.

Reboot.  See what happens.  Good luck.  HAVE FUN

---

### Post by ranch hand on 2009-10-12
> **VMC said:**
> I'm a little confused here. Straighten me out. You have both ubuntu and kubuntu installed on you pc. grub2 is assigned to karmic. Now you want to reassign grub to kubuntu. Is this right?
My head is spinning too.  This is all part of the FUN.

Wait until the release.  I think a vacation with no internet connection until about January would be a good idea.  But not as much FUN.

---

### Post by Wa1k3rTXRang3r on 2009-10-12
I ran 

sudo grub-install /dev/sda

and the command cannot be found.

This is the problem that I have been having for 2 hours. Everywhere I look says to run these commands, and then I run them and they can't be found.

---

### Post by VMC on 2009-10-12
> **Wa1k3rTXRang3r said:**
> I ran 

sudo grub-install /dev/sda

and the command cannot be found.

This is the problem that I have been having for 2 hours. Everywhere I look says to run these commands, and then I run them and they can't be found.

Here's the deal. You need to boot up karmic then chroot to kubuntu and issue those commands.

Your title says "Kubuntu 9.10 fails to install GRUB". So you want to install grub. Now the question would be, is that grub-legacy or grub2 ?

---

### Post by ranch hand on 2009-10-12
Did you reinstall the grub2 stuff in synaptic and did you make sure that all grub-legacy stuff is gone?

If this is not done, seeing as the installer claimed it failed to install grub2, you are not going to have any real success.

---

### Post by Wa1k3rTXRang3r on 2009-10-12
Ok. Basically, what I did was after having the installer fail to install GRUB, I installed Kubuntu again but without installing the bootloader, overwriting Ubuntu in the process apparently. 

Now I'm using Kubuntu and booting it through the SuperGRUB Disk. But, the installation of Kubuntu itself has no GRUB at all.

What I want to do now is install GRUB 2.

Sorry for the confusion. I'm confused, and now everyone else is too. Hopefully this helps to clear up the situation.

---

### Post by ranch hand on 2009-10-12
So go to synaptic and look for those 3 packages.  That is what you need.

I have nothing against SGdisk but the habit, that you picked up probably by running Win Paysomemore, of using 3rd party apps is not a real good one.  I know it is hard to kick (I am recovering) there should be a 12 step program.

This is linux, you can do anything that those apps can do.  If you learn to do them and then want the simplicity of the apps that is great.  You will be a more confident user if you learn the long way around and it will come in handy anyway.

You could have done all this from your LiveCD and been done by now.

---

### Post by Wa1k3rTXRang3r on 2009-10-12
After much debate and hours of wasted time, I decided to reinstall Ubuntu since everything works fine on that.

Thanks for your help anyways.

Sorry for the headaches!!!

I'm a GNOME fan anyway, just thought it would be fun to try KDE XD (look how that turned out lol)

---

### Post by ranch hand on 2009-10-12
Well, this way you get a real file manager and synaptic.

The fact that it works for you might be a plus too.

---

### Post by VMC on 2009-10-13
> **ranch hand said:**
> I have nothing against SGdisk but the habit... of using 3rd party apps is not a real good one.  I know it is hard to kick (I am recovering) there should be a 12 step program.
I whole heartily agree. SGD is great for learning, but afterward drop it or you will find yourself depending on it and not learning anything.

> **ranch hand said:**
> This is linux, you can do anything that those apps can do.  If you learn to do them and then want the simplicity of the apps that is great.  You will be a more confident user if you learn the long way around and it will come in handy anyway.
You could have done all this from your LiveCD and been done by now. Amen to that. I'm very confident that Wa1k3rTXRang3r has "walked" away with a new sense of pride.

---

