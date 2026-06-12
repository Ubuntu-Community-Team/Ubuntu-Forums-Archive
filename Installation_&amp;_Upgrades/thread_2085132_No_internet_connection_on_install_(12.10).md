---
title: "No internet connection on install (12.10)"
date: 2012-11-17
forum: Installation &amp; Upgrades
---

### Post by Skatespeare on 2012-11-17
Dear Ubuntu-friends,

Today I decided to reinstall an old laptop which was running Ubuntu 9.04 or something. Anyway, when I got to the window where I choose either Try from CD or Install Ubuntu, I chose the latter. However, it said that there was no internet connection. At first I thought, well I'll figure this out after I install so I tried to move on by clicking Continue. But nothing happened for about 20 minutes.

So then I returned and entered the Try from CD option to see what was going on with the network connection. But it appeared that there was no problem whatsoever with the connection. This post is the living prove of that since I am still in the Try from CD option.

I am on an Acer Extensa 5220 laptop and I never had any troubles in the past with installing Ubuntu and malfunctioning network connections. And since the connection seems to be working fine I don't think it's a driver issues.

To sum up: I think the problem is two-fold. On the one hand, I can't continue with the installation because nothing really happens when I press Continue. On the other, the installation process thinks it is not connected to the internet. And I am not sure how, if at all, the two are related.

I really hope someone can point me in the right direction. I have been searching the web, but I can't find an answer. Any help will be greatly appreciated!

Skate
The Netherlands

---

### Post by dino99 on 2012-11-17
This issue was met at the 12.10 beginning cycle, but should not be hit with a recent iso. If you still have the old installation, then you can fix 12.10 by chrooting it. Otherwise try to boot on recovery mode, to set the network first, then using the command line to fix the installation.

note: some time ago, when nm was having troubles, i've discoved wicd, and i still prefer it (even with a wired network)

---

### Post by Skatespeare on 2012-11-17
Thank you very much for your reply! I downloaded the iso today so that can't be it.

I'm sorry but I am still somewhat of an Ubuntu newbie, unfamiliar with chrooting and the likes. Do you think installing 12.04 instead will do the trick? I just want my laptop to work again.

---

### Post by anarchticgrimm on 2012-11-17
Correct me if I'm mistaken; but can't you just install Ubuntu from LiveCD? - Since you said you can connect while you're on LiveCD.

---

### Post by Skatespeare on 2012-11-17
> **anarchticgrimm said:**
> Correct me if I'm mistaken; but can't you just install Ubuntu from LiveCD? - Since you said you can connect while you're on LiveCD.

That's exactly why I am so suprised! First there is a connection and then there is none... I tried installing from LiveCD. It opens up the window where I can first choose the language and after that it shows these "suggestions" for the best install with checkmarks. 

The only thing not checked is the internet connection. And I can also choose 3rd party software. But when I press Continue, the mouse pointer just indicates it is in progress. Nothing happens...

Again, I am not sure whether the two problems are related.

---

### Post by anarchticgrimm on 2012-11-17
Then clearly, that installation you have has a strange bug. If you haven't try that LiveCD you have on another PC or you just don't have any other available system for such operation right now; I suggest you to download Ubuntu 12.04.1 for that machine.

If installation can't see the connection which has already been established and if the same DVD/USB you have does not work on another machine, then that DVD/USB you have is corrupted somehow. Because I've already downloaded and installed an Ubuntu 12.10 on a system and no problems have been reported.

By the way, if you have a wireless network and if you've got the chance to wire it; try it that way. - A hope, at least.

---

### Post by Skatespeare on 2012-11-17
Thank you for your comment. I am going to try the 12.04 to be sure.

Concerning wifi connection. I haven't mentioned it, but the wireless wasn't working at all so I immediately tried the cable connection. When I am in the LiveCD I can't connect to the wireless either.

---

### Post by Skatespeare on 2012-11-18
I am now trying to install 12.04. Although the internet connection was not properply working here either the installation process seems to be progressing as it is supposed to. So the two problems probably are not related.

Anyway, thank you all for your support!

---

### Post by ruehara on 2013-01-06
> **dino99 said:**
> This issue was met at the 12.10 beginning cycle, but should not be hit with a recent iso. 

Soz Dino, the problem still appears to exist.

I tried to install 12.10 64-bit into a brand new PC (i7, 8Gb RAM, 1Tb HDD) from an ISO I downloaded on December 17th. Firefox won't connect to the Interweb from a wired connection.

What I would really like to do is to remove 12.10 and replace it with the 12.04 LTS. I have nothing installed worth keeping. Is this as simple as deleting everything and reinstalling from a Live CD or are there any hidden/system/boot sector files I need to know about?

Otherwise, any idea how I can connect Firefox & Thunderbird to the 'net?

Thanks.

---

### Post by UltimateCat on 2013-01-06
I'm not the expert but it seems like the 12.10 ISO file may be corrupt. I would
check that files integrity with MD5checksum-

[http://video.answers.com/how-to-check-file-integrity-in-md5-checksum-161788943](http://video.answers.com/how-to-check-file-integrity-in-md5-checksum-161788943)

After a fresh install you should be able to go online.
If not you may need a driver for you NIC; network interface card.
And if you do not have a NIC and have to use a usb adapter to communicate with your modem than you will need a driver to accommodate the adapter as well.

In some cases Ndiswrapper is needed for internet browsers to work.
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Also be sure that you have the correct file for your systems architecture and read the installation documentation. Ensure that you have a brand new CD/DVD.
 Don't touch the underside of the CD/DVD by accident like I did and had to start over.

[http://askubuntu.com/questions/219578/ubuntu-12-10-64bit-fresh-install-wireless-issue](http://askubuntu.com/questions/219578/ubuntu-12-10-64bit-fresh-install-wireless-issue)

[http://askubuntu.com/questions/214929/network-manager-connection-is-unmanageable-until-i-disable-and-enable-networking](http://askubuntu.com/questions/214929/network-manager-connection-is-unmanageable-until-i-disable-and-enable-networking)

[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)

Hope this helps

---

### Post by UltimateCat on 2013-01-06
Thought of something else.

It could be the configuration file.

With my distro I had to open the /etc/network/interfaces file and use (#) to comment out the wired argument in order for the wireless to work.

After I commented out the arguments for wired and re-started my system I was online but I had to install Ndiswrapper.

Sometimes older computers can be a little fuzzy/buggy-

---

