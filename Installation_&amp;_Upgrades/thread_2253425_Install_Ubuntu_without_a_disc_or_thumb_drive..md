---
title: "Install Ubuntu without a disc or thumb drive."
date: 2014-11-19
forum: Installation &amp; Upgrades
---

### Post by it-is-possible007 on 2014-11-19
It seems to me that since Ubuntu is a free to download OS, some of the smart people working for Canonical, who were able to develop an Ubuntu Phone, should be able to come up with a way to allow new users to install the GUI desktop without the use of such antique devices as discs and thumb drives.

is there no Linux command that can be typed in a terminal, that will allow the device it's on to install the latest version without any media at all?  It just seems to make sense to allow that.

---

### Post by Mark Phelps on 2014-11-19
You can install Ubuntu from a local network -- but I've never done it.

Read through the attached info about Network installations: [https://help.ubuntu.com/community/Installation]("https://help.ubuntu.com/community/Installation")

---

### Post by matt_symes on 2014-11-19
Hi

> **it-is-possible007 said:**
> It seems to me that since Ubuntu is a free to download OS, some of the smart people working for Canonical, who were able to develop an Ubuntu Phone, should be able to come up with a way to allow new users to install the GUI desktop without the use of such antique devices as discs and thumb drives.

is there no Linux command that can be typed in a terminal, that will allow the device it's on to install the latest version without any media at all?  It just seems to make sense to allow that.

As Mark said, you can install over a local network by PXE booting but you need a PXE server on your local network to do it.

The basic idea is to set up the PXE server with a TFTP server to serve the Lan bootloader. 

It also needs a DHCP server to serve an IP address to the client machine and to tell the client machine where to get the lan bootloader. 

You can also set up an nfs server or an Apache server on the PXE server to server the ISO or the majority of an extracted iso.

you need a menu for the client machine to display telling it what ISOs it can boot and where to find either the ISO if copying the entire ISO to memory or the kernel and initramfs file if the rest of the ISO is being server over nfs or Apache. This is also served by the TFTP server.

Finally you need to enable PXE booting in the BIOS of the client machine.

As stated, this is over the local lan, not the Internet, and requires a server already set up.

I have set one up on my local lan.

I don't understand the your question about the Internet though as you need some kind of OS on the PC (or live cd/USB) running to be able type in commands to install a new OS anyway.

EDIT: if the hard drive was in a different PC, you could use debootstrap, install a minimal Ubuntu OS over the Internet and build up your installation that way but it still requires the hard drive (or USB stick) to be in a machine with an OS on it.

Kind regards

---

### Post by yancek on 2014-11-19
> t seems to me that since Ubuntu is a free to download OS, some of the  smart people working for Canonical, who were able to develop an Ubuntu  Phone, should be able to come up with a way to allow new users to  install the GUI desktop without the use of such antique devices as discs  and thumb drives.


It has been years since I have used the 'primitive' CD/DVD/flash drive to install an operating system.  All you need is the Grub bootloader, either Legacy or Grub2 can do this with the iso or extracted iso on a partition with no need for any other medium.

If you don't want to go through the trouble of installing, you can buy a computer with Ubuntu pre-installed, much the same way that almost all windows/apple users get theirs.  Can a windows/apple system be installed this way?  I don't use either so...?    I'm not sure what the incentive would be for canonical.

---

### Post by it-is-possible007 on 2014-11-20
Thanks Yancek;  you seem to get my meaning.  Now here's the back story.
I'm not connected to a network.  I have an IBM Thinkpad (T43) which I purchased a year ago with Xubuntu 12 preinstalled.  3 days ago, I decided to upgrade, using terminal commands, to 14.  Then, PACKLUI!  I destroyed it.  The operating system boots up fine.  The F command keys work fine.  I still even have cursor ability, but I don't have a GUI desktop, just a wallpaper background.

i searched around for commands to install the GUI image using my iPhone as a USB hotspot.  No luck.  I even tried using my iPhone as a stick, to passively transfer the iso to my computer; but obviously my phone resists the download.

Ubuntu, and the other "untus" are leading edge programs.  It just seemed there should be a way to pull a GUI desktop from the kernel, so that it could just get it going without having to Nuke it, or saddle up the horses to go into town to buy a disc or other media.

<scratching my head>

---

### Post by it-is-possible007 on 2014-11-20
My screen shows the xubuntu logo on start up, then after login, I'm left looking at nothing but a screen saver and a curser, but no GUI desktop.  This is all happening with the flash drive inserted.

---

### Post by yancek on 2014-11-20
I'm not sure I'm understanding what the problem is.  You indicate you aren't connected to a network but in the same sentence indicated you tried to upgrade.  Do you mean you have no local network?  You couldn't upgrade without an internet connection.  Your last post seems to indicate that the XFCE Desktop environment is gone or non-functional.  Is that the problem, but you can still login and use the system from a terminal?  Is what they are talking about at the link below what you mean?  The link refers to 12.04 and the page date is 2+ years old, not sure which release you are using.

[http://www.webupd8.org/2012/05/install-xfce-410-in-xubuntu-1204.html](http://www.webupd8.org/2012/05/install-xfce-410-in-xubuntu-1204.html)

The link below (right side of the page) explains a simple method to install XFCE, it is specific to Ubuntu but the only difference should be the how to open a terminal as Xubuntu has no Dash. Looks pretty simple and Xubuntu uses Ubuntu repositories as far as I know so it should work.

 [https://sites.google.com/site/easylinuxtipsproject/alternative](https://sites.google.com/site/easylinuxtipsproject/alternative)

---

### Post by it-is-possible007 on 2014-11-24
> **yancek said:**
> I'm not sure I'm understanding what the problem is.  You indicate you aren't connected to a network...Is what they are talking about at the link below what you mean?
[http://www.webupd8.org/2012/05/install-xfce-410-in-xubuntu-1204.html](http://www.webupd8.org/2012/05/install-xfce-410-in-xubuntu-1204.html)


Thanks Yancek!   Sorry for the confusion in my explanation, but what I meant by "I'm not  connected to any network", was that I was not connected to a LAN.  I am  however connected to the Internet via my iPhone's USB Hotspot.


I followed your suggestion and looked at the websites included in your link.  Yay!!!! It worked.  I typed these commands in the terminal:

```

sudo add-apt-repository ppa:xubuntu-dev/xfce-4.10
sudo apt-get update
sudo apt-get dist-upgrade
```

after about an hour or so, my problem was fixed.  I now not only have a GUI desktop,
but my Ubuntu was also updated to 14; which is all I wanted in the first place.  Also, it
answers my initial question in that it was updated without the use of a disc or
thumb drive:  Proving that it is possible.  I knew it could be done, but I could not have
succeeded without your help.  Thank you for your patience and assistance.
I can now mark this thread as completed.  Mission accomplished!

---

