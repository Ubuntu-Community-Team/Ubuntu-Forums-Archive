---
title: "uname gives wrong kernel release?"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by jome on 2007-04-15
I have been trying to install new drivers for my wireless (ieee80211, ipw2200) and webcam (gspcav1). To do this I need to install linux-headers-'uname -r'. But 'uname -r' on my laptop returns 2.6.12-10-686. This package is apparently obsoleted.  I have now installed linux-source-2.6.15 and linux-headers-2.6.15-28.686, but this means I have to change manually every Makefile.
What is wrong with the kernel release and/or uname?

---

### Post by mgmiller on 2007-04-15
Whatever  uname -r returns, is the kernel you are running.  This is an old kernel.  Even the newer one you tried to install is old.  What version of Ubuntu are you running?  I suspect you do not have the kernel meta package installed.  Run Synaptic and search on the architecture you need linux-k7 or linux-686 or linux-generic and install that.  High lite the package name and read the information on it.  If it says you probably don't want to install it directly, then it's not the meta package.   Once done correctly, it should upgrade all the other kernel packages at the same time and make sure they all stay in synch automatically.  The current metapackage for Edgy is linux-generic.  This has replaced all the other ones (k7, 386, 686) It will give you the 2.6.17 kernel.  After this upgrade, you may have to install the kernel headers separately, I don't do any compiling, so I never installed those.

Good luck.

---

### Post by mikewhatever on 2007-04-15
That actually might really be your kernel, since it says Kubuntu 5.10 in your info. I don't think it is supported any longer, beginning from April 2007.
[http://www.ubuntu.com/news/Ubuntu-5.10-end-of-life](http://www.ubuntu.com/news/Ubuntu-5.10-end-of-life)

---

### Post by mgmiller on 2007-04-15
> That actually might really be your kernel, since it says Kubuntu 5.10 in your info.

I missed that.  Yup.  Time to consider an upgrade.  You could go the 5.10>6.06>6.10>7.04 route, but that may give just a  tad bit of trouble.  Probably better at this point to back up stuff you need and do a clean install of Feisty when it comes out in a few days.

---

### Post by jome on 2007-04-16
> **mgmiller said:**
> I missed that.  Yup.  Time to consider an upgrade.  You could go the 5.10>6.06>6.10>7.04 route, but that may give just a  tad bit of trouble.  Probably better at this point to back up stuff you need and do a clean install of Feisty when it comes out in a few days.

OK. that sounds like a very good idea. it might solve my wireless problem as well. Do you have information on how to install Feisty when it comes? The previous installation was done by a friend and I think it is better if I know how to do it myself.

---

### Post by mgmiller on 2007-04-16
1st, make sure you have backed up whatever documents, pictures, etc. you want to keep to a thumb drive or external hard drive or dvd, etc. 

On April 19, Ubuntu is releasing Feisty, I am not sure of the release date for Kubuntu, but it won't be much beyond that.  
1) Download the live CD  .iso from the Kubuntu site.
2) Put a blank CD in your burner and right click the .iso file and select "Write to disk".
     This will create the bootable CD.
3) Boot your computer off the CD.
     This will give you a quick hardware compatibility check for things like wireless  networking and sound.  
Don't worry about your screen resolution at this point.

4) There will be an icon on the desktop to install the operating system to your hard drive.  Just click it and follow the prompts.  When you get to the part about how much of your hard drive to use, tell it to use the whole drive, overwriting everything that is there.  It will warn you that all data on the drive will be lost.  That is why you backed up your stuff first.  Proceed with the install.

5) After the install, restore the stuff you backed up to your home directory.

6) Consider keeping up with the upgrades every 6 months.
     (Although there are some people who advocate a clean install rather than an upgrade, I have not had many issues doing upgrades because I tend to only install things using synaptic from the Ubuntu repositories.)

You are using Kubuntu, which uses a different packaging system than synaptic, I have no real experience with Kubuntu, so you will probably need your friends help again after the install.  I can tell you that installing audio and video codecs and upgrading the video drivers is almost trivially easy in Feisty.  You really don't need automatix any more for this kind of stuff.  Only installing the DVD movie playing codec still requires a little expertise.  

You could try a beta live CD now without doing the install just to see how your wireless works, etc.. and to play with the compiz 3d desktop and other new features.  You don't have to install it.

I have been running the Feisty beta on one of my machines for about a week and it works quite well.  This will automatically upgrade itself to the final release when it comes out.  If you are impatient, you could install the current beta of Kubuntu.  There will be many daily upgrades,  and things will probably break and get fixed a lot. so if you don't have a fast internet connection, or are a little less adventurous, you may want to wait till the final comes out to do the actual install.

---

### Post by mgmiller on 2007-04-16
One final thought.  As you seem to be happy with a system attitude of "if it aint broke, don't fix it",  you might consider just upgrading your current installation to Dapper (6.06).  This is an LTS release and will have support for a few more years.  The LTS or long term support releases have a 3 year cycle on the desktop and 5 years on the server instead of 18 months for the desktop for the regular releases.  The advantage here is that you can upgrade your current install to it, keeping all your installed software and settings.  I would still do a back up before, just in case.  As I recall,  I had a few minor glitches going from 5.10 to 6.06, but they weren''t too bad.  You could just go on a schedule of upgrading from LTS to LTS every few years and potentially have a more stable system as a result, at the expense of the newest software and neatest eye candy.

As I mentioned in my last post, you could try a live CD of 6.06 to check for hardware compatibility, etc. before installing it.  If you decide you like it, and want to upgrade, don't install it from the CD.  Use the upgrade instructions for Kubuntu to do it over the internet.  I know how to do this for Ubuntu, but not for Kubuntu, a quick check of the forums, will give you the commands you need to do this.  I believe it can be done from within your package management system and should not need you to manually edit xorg.conf or anything like that.  I do know you need to make sure your current Kubuntu 5.10 is up to date and has the complete Kubuntu-desktop meta package installed before doing the upgrade.

Good Luck

---

### Post by mgmiller on 2007-04-16
OK, last post for now.  IF you want to just upgrade from Breezy to Dapper, follow these instructions:

[https://help.ubuntu.com/community/DapperUpgrades]("https://help.ubuntu.com/community/DapperUpgrades")

To do it the easy way, you will have to install the gnome update manager package first.
Do a search for the package  update-manager   and install that using your kubuntu package management system.  Then you can follow the instructions in the first part of the link I gave you.

From what I have experienced, you will get a better upgrade doing it that way, rather than using the manual method listed below it.

---

### Post by jome on 2007-04-17
I probably don't have Kubuntu as I can use synaptic and when I type sudo apt-get update I see a lot of dapper coming by. But I can't find which version. If I remember correctly my friend installed normal Ubuntu with GNOME as the window manager and I prefer KDE. So probably only the window manager is KDE.

---

### Post by mgmiller on 2007-04-17
It sounds like you have an Ubuntu (possibly dapper) install with the kde-desktop metapackage installed on top of it.  If you log off and then select sessions on the log in screen, you should have a choice of gnome or kde or ubuntu and kubuntu, you get the idea.  Log back in with gnome.  At the top of the screen, select System>About Ubuntu and you will see which version you have.  There is probably a similar method in KDE, but I don't know what it is.  If you are going to do the system upgrade, rather than the clean install, do it from the Ubuntu side.  Make sure the ubuntu-desktop meta package is up to date and after the install, you can do the kubuntu-desktop meta pacakage as well.  Another quick way to look would be to examine your /etc/apt/sources.list and see which release it is pointing to, but I have seen instances where this file was modified by the owner and only some of the entries point to the right release.  This can also be examined in synaptic itself, by looking at the repositories as listed in Settings>repositories.  (That is where it is currently, I forget if it was in a slightly different spot earlier, but if you look around a bit, you will find it.)

---

### Post by zvacet on 2007-04-17
To find out wich version you are runing
```
lsb_release -a

```

---

### Post by jome on 2007-05-01
allright I upgraded to 6.10 with a lot of trouble. I forgot to turn on the plug where my adapter was plugged in, and the upgrade was interupted in the middle of removing xserver-xorg. It took me two days to figure out how to remove it completely and then reinstall it. Then the grub loader made my kernel panic, I think by changing to UUID's. Anyway when I type uname -r I still get 2.6.12-10-686 and I expected that to change to 2.6.17-10-something after the upgrade. Is there some command I have to type? I used 'sudo update-manager -c' to do the upgrade.

I want to upgrade to feisty later, but my CD-player is not detected in both linux and windows, so I think hardware problem. Downloding feisty will take me between 3 hours and 2 days and I want to know on which end I am before I start.

---

### Post by mgmiller on 2007-05-01
Take a look in /etc/apt/sources.list and make sure all your entries now point to edgy.  If they don't, change them so they do.   Next try running update manager and click on the "Check" button to see if anything shows up.  You may also want to try running Synaptic package manager and click the reload button and then apply upgrades.  If all else fails, from a command line try:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

You might need to run one or more of these updaters several times before all changes are made.

Finally, if you are having a hardware problem, it might be best to resolve that before going much further.  CD/DVD drives are very inexpensive,  I can buy a dual layer DVD burner at microcenter warehouse for under US $35.00.  I haven't seen any CD drives in a while, but DVD drives will also play CD's and they are routinely around US $15.00 for OEM versions.

---

### Post by jome on 2007-05-01
> **mgmiller said:**
> Take a look in /etc/apt/sources.list and make sure all your entries now point to edgy.  If they don't, change them so they do.   Next try running update manager and click on the "Check" button to see if anything shows up.  You may also want to try running Synaptic package manager and click the reload button and then apply upgrades.  If all else fails, from a command line try:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

You might need to run one or more of these updaters several times before all changes are made.


everything points to edgy, all breezy has been commented out
they are all agreeing that there are no more updates.  I noticed, however, that the headers and source of 2.6.17-11-generic have been installed.

> 
Finally, if you are having a hardware problem, it might be best to resolve that before going much further.  CD/DVD drives are very inexpensive,  I can buy a dual layer DVD burner at microcenter warehouse for under US $35.00.  I haven't seen any CD drives in a while, but DVD drives will also play CD's and they are routinely around US $15.00 for OEM versions.

I have a CD/DVD writer that was replaced soon after I bought the laptop because it would not read faster than 2x. It happened before that the drive wasn't detectable, but it came back after a few days. But I think this time it has been gone for a few weeks already. Windows kept complaining about a mobile device not being connected, which I thought was my old mobile phone, but I think now it is the CD/DVD drive. Maybe the shop can fix it cheap.

---

### Post by jome on 2007-05-01
in my /boot directory there is only config-2.6.12-10-686, System.map-2.6.12-10-686, abi-2.6.12-10-686, initrd.img-2.6.12-10-686, vmlinuz-2.6.12-10-686, memtest86+.bin and grub

---

### Post by mgmiller on 2007-05-03
Sorry, I didn't realize you had a laptop.   That could be a bit more expensive to fix.  

As far as the kernel is concerned, make sure you have the meta package installed for the new kernel.  It is called linux-image-generic.  This will make sure all the other parts of it, (kernel, headers, restricted bits) stay properly synchronized.  If need be , do a reinstall of linux-image-generic.

Hope this heips.

---

### Post by jome on 2007-05-04
I copied a 2.6.17 kernel from another computer and also the modules. I can now boot it. I downloaded a iso image for Feisty and when I get my CD writer to work I will make a feisty CD and install it.

Thanks for all the help.

---

