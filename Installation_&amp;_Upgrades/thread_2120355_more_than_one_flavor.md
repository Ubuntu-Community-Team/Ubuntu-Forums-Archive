---
title: "more than one flavor"
date: 2013-02-26
forum: Installation &amp; Upgrades
---

### Post by mayagrafix on 2013-02-26
I have a dual core laptop with one gig of RAM that runs Ubuntu 12 LTS with Unity okay but I would like to try Lubuntu on it. In case I dont like Lubuntu, I would like to go back to Ubuntu. How should I proceed? is there a way to have both versions installed?

Thanks for any help. -:KS

---

### Post by JLeon85 on 2013-02-26
Lubuntu works great as a persistent live USB. You could try that with no worries.

---

### Post by MAFoElffen on 2013-02-26
> **mayagrafix said:**
> I have a dual core laptop with one gig of RAM that runs Ubuntu 12 LTS with Unity okay but I would like to try Lubuntu on it. In case I dont like Lubuntu, I would like to go back to Ubuntu. How should I proceed? is there a way to have both versions installed?

Thanks for any help. -:KS

Yes you can.  Ubuntu, Kubuntu, Xubuntu, Lubuntu... are all the same core Linux system under the hood with different desktop environments over it. Just like for Ubuntu, itself, you could install the Gnome 3 desktop, just to show the same suite of applications with a different looking desktop display and menu system. 

You could just install multiple desktops on top of that core, for example the lubuntu-desktop on top of Ubuntu...

I installed all the desktops on a test box and here's what it does and the the trade offs... You have each desktop, which looks different, but each suite also has it own suite of applications that are bundled with each. Some are the same <> Some are different.

When you install an additional desktop, it installs that desktop and all it's bundled applications. The applications from both desktop's bundles suites, show in the menus of both desktop environments...

So, in the case of Lubuntu, you will see "heavier" Ubuntu applications installed that are not installed into Lubuntu by default. In the case of KDE, some KDE app's will show in other Desktops, even though they don't display right running in those other environments.

The upside is you have variety and access to differing applications. If you are familiar with what apps came bundled with what desktop, then if one fails to "act right" when displayed or running in a non-native environment...

The downsides- Well first, more disk space. Second, if you run a full featured, heavier Ubuntu app in Lubuntu, it will run a little faster because of less overhead... But since it is heavier, you might get the idea that it doesn't run any faster (which is not fair to Lubuntu). Next, if you uninstall a desktop later, then if there was any shared app's it going to uninstall that shared app away from that other desktop. This might cause you to have to reinstall that other desktop or app.

It's do-able. It's variety. As long as you understand the tradeoff's and that it is not going to look like a "isolated" native install of that desktop.

Picking one from the other... Is at bootup when you log in. Your enter your password, selct the icon to the right of your name and select the Desktop Environment you want to start... Off you go.

There is 3 alternatives...

One is too install "Test Drive An Ubuntu ISO" which let you try Ubuntu branch distro's easily within Ubuntu from a virtual machine using VirtualBox. This let you try a LiveCD's Live Image as a Virtual Machine without having to burn it to a CD or DVD disk. This will not be as fast as installed straight to disk.

Or you could download the ISO and run it straight from the grub menu, manual custom entry... That will run faster than from a CD drive or under a Virtual machine, but will still just be the Live Image.

Or you could partition off a 5GB partition and install to that partition, straight to disk and share the swap partition. Do not install the boatloader, but update Grub from the previous Ubuntu install to find and add it to it's Grub Menu. That would give you a test area, to try it out. That would also give you a realistic experience of what it "really" looks like as a native install and how it would run on your hardware.

I know, a novel right? I could have just said yes, but you deserve hearing the whole story.

---

### Post by JLeon85 on 2013-02-26
That sounds really great. How do you install them on the same core without using different partitions?

---

### Post by sudodus on 2013-02-26
```
sudo apt-get install lubuntu-desktop
``` and/or
```
sudo apt-get install xubuntu-desktop
```

and you get rid of them according to this link (or get rid of Unity)

[[COLOR="Red"]http://www.psychocats.net/ubuntu/index[/COLOR]]("http://www.psychocats.net/ubuntu/index")

I have such an installation too, and I find myself running Lubuntu 90% of the time.

Good luck :-)

---

### Post by Frogs Hair on 2013-02-26
If you want to just try the LXDE session and not the Lubuntu desktop use the following. There are a lot fewer packages to install and remove.  ```
sudo apt-get install lxde
```

---

### Post by mayagrafix on 2013-02-27
Thanks everybody for all the great help. I was able to download and install Lubuntu alongside Ubuntu and switch from to another with no problem. Yayy!

The lubuntu is great cause it only uses 13% of RAM to run and thus keeps the use of SWAP disk to a minimum (almost null). However, I really like Ubuntu with Unity and like having it around for those heavier apps.

Again, thank you for the great info and support.-:KS-

---

