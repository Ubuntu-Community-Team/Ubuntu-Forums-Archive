---
title: "Complete greenhorn, doesn't know how to install programs"
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by radmon on 2008-09-05
Hey guys, I have been lurking around xubuntu/ubuntu forums all night without any luck, so here's my problem.

I need to install network manager, I'm currently using windows to access the internet, so I downloaded network manager then put it on a usb then fired up xubuntu. I unpacked the zip file, but now I have no idea what to do? How do I install things on xubuntu.

---

### Post by ad_267 on 2008-09-05
What is in the zip package, where did you download it from? Can you not get on to the internet to use synaptic/apt etc to install packages?

There was a good article at [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) but it doens't seem to be up anymore.

This is a brief overview: [http://martin.ankerl.com/2007/04/19/how-to-install-anything-in-ubuntu-condensed/](http://martin.ankerl.com/2007/04/19/how-to-install-anything-in-ubuntu-condensed/)

---

### Post by radmon on 2008-09-05
Downloaded it from [here]("http://linux.softpedia.com/get/System/Networking/NetworkManager-6451.shtml").

The contents of the zip package looks like this [http://s5.photobucket.com/albums/y151/infinate_ammo/?action=view&current=Untitled-9.jpg](http://s5.photobucket.com/albums/y151/infinate_ammo/?action=view&current=Untitled-9.jpg)

I can't get on the internet from Xubuntu, so I need to download stuff in windows then transfer it over.

---

### Post by ad_267 on 2008-09-05
That looks like source code which you need to compile. You probably need to install build-essential from the cd first so put in the ubuntu cd and make sure the cd is checked as a source of packages in synaptic then click reload and install build-essential.

Then you need to open a terminal by going to applications - accessories - terminal and then you can use these commands to compile the source code and install it:
```

cd "/path/to/extracted/files/"
./configure
make
sudo make install

```

---

### Post by rocknrolf77 on 2008-09-05
That pcakage is propably source code. You need to get the deb package from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) for your version of *buntu

Then you can install it just by double clicking it. Source code you have to compile.

---

### Post by radmon on 2008-09-05
I'm sorry but you have both lost me, ad_267, I have no idea how to check if the CD is checked as a source of packages in synaptic, I have no idea what reload is, I have no idea where I go to install build essential. 

rocknrolf77, I follow the link you gave me, go to my version of xubuntu, go to the debian installer, then I am confronted with [this]("http://packages.ubuntu.com/hardy/debian-installer/").

I appreciate the help, but can you be a little less vague?

---

### Post by ad_267 on 2008-09-05
> **radmon said:**
> I'm sorry but you have both lost me, ad_267, I have no idea how to check if the CD is checked as a source of packages in synaptic, I have no idea what reload is, I have no idea where I go to install build essential. 

rocknrolf77, I follow the link you gave me, go to my version of xubuntu, go to the debian installer, then I am confronted with [this]("http://packages.ubuntu.com/hardy/debian-installer/").

I appreciate the help, but can you be a little less vague?

On that package site you can search for package names. I searched for network manager and got this: [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=network+manager](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=network+manager)

I think the ones you want are [http://packages.ubuntu.com/hardy/network-manager](http://packages.ubuntu.com/hardy/network-manager) and [http://packages.ubuntu.com/hardy/network-manager-gnome](http://packages.ubuntu.com/hardy/network-manager-gnome) You want to download the .deb file for i386 unless you have 64bit xubuntu.

---

### Post by rocknrolf77 on 2008-09-05
You need this package (i386) : [http://packages.ubuntu.com/hardy/network-manager-gnome](http://packages.ubuntu.com/hardy/network-manager-gnome) 

The packages listed under are the dependencies, but most of them are probably installed. Maybe you need the network-manager too : [http://packages.ubuntu.com/hardy/network-manager](http://packages.ubuntu.com/hardy/network-manager)

Don't you have a cable to use for internet to install the packages?

---

### Post by orpheus07 on 2008-09-05
> **radmon said:**
> Downloaded it from [here]("http://linux.softpedia.com/get/System/Networking/NetworkManager-6451.shtml").

The contents of the zip package looks like this [http://s5.photobucket.com/albums/y151/infinate_ammo/?action=view&current=Untitled-9.jpg](http://s5.photobucket.com/albums/y151/infinate_ammo/?action=view&current=Untitled-9.jpg)

I can't get on the internet from Xubuntu, so I need to download stuff in windows then transfer it over.

Is this a fresh installation?

---

### Post by Sef on 2008-09-05
> There was a good article at [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) but it doens't seem to be up anymore.

It has often gone down this time of year for a few weeks.

Instead Read [Psychocats Insatalling Software]("http://www.psychocats.net/ubuntu/installingsoftware").

---

