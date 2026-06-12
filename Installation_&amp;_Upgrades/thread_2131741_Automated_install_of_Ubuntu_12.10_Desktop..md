---
title: "Automated install of Ubuntu 12.10 Desktop."
date: 2013-04-02
forum: Installation &amp; Upgrades
---

### Post by arto7177 on 2013-04-02
I am trying to setup a Flash drive to preseed an installation for Ubuntu 12.10 Desktop. I an unclear how to get Ubiquity to load the preseed file. With the Alternate cd you could just add a menu option to load the preseed. I have edited txt.cfg to add a menu option (to the f6 text menu) which will allow me to select automatic installtion (loading the preconfig.cfg) or have the other options still available. 

```

label preseed
menu label ^Preseed Ubuntu 
kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true file=/cdrom/preseed.cfg boot=casper only-ubiquity initrd=/casper/initrd.lz quiet splash --
```

The  new option shows up in the menu but when selected the installer starts but does not preseed any options.

---

### Post by launchpad-nomoreheroes on 2014-03-11
Did you, or anyone else, ever work out what needed to be done?

I'm trying to use preseed alongside Vagrant and Packer to do some automated provisioning of virtual machines. 
Server editions are no bother, but I cannot fathom how to do similar for Desktop editions of Ubuntu.

---

### Post by coffeecat on 2014-03-12
Since 12.10 is soon to be end-of-life and is a dead-end now as far as release upgrades are concerned, I've closed this thread.

@launchpad-nomoreheroes, I see that you have started your own thread with this same question. Please do not cross-post the same question in different parts of the forum. 

Thread closed.

---

