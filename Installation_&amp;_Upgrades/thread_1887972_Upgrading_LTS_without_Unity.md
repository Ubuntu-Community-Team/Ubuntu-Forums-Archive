---
title: "Upgrading LTS without Unity"
date: 2011-11-28
forum: Installation &amp; Upgrades
---

### Post by blahsnr on 2011-11-28
I'm doing some forward planning here. I have just installed 10.04 on this EeePC due to a failed update of 10.10. I realise that support for 10.04 will cease sometime in the spring of 2013 and I am wondering what the possible upgrade paths are. My starting position is that I am happy with the Gnome 2.xx interface on 10.04. I also have another frugal install of Xubuntu 10.10 on a second flash drive in the machine and Xubuntu would also be a possibility for an upgrade. I've tried Unity and really can't get on with it.

Note, I don't want to start another "Unity or not" debate so please don't try to convince me of the virtues of Unity. I am  just looking for the possibilities to stay with Ubuntu without Unity once 10.04 ceases  to be supported.

1) Is there a way to install the next LTS version of Ubuntu without including the Unity desktop and other apps such as Thunderbird that I wish to avoid? Or is it a case of install everything, then add the window manager of my choice and strip out the stuff I don't want

2) Would  it possible to continue to upgrade 10.04 piecemeal after the end of the long term support period? That is say with new kernels and security bug fixes? If so, is there an easy to use mechanism to identify critical security updates?

3) Before I gave up on my 10.10 install, I installed the Xfce desktop on my Ubuntu install. However, when I booted into it I could not get the panels to behave like they do in the current Xubuntu distributions. I guess there are various plugins used in Xubuntu to allow the placing of icons and elements on the panels. So it looks like it would be a fair amount of work to get everything set up as i want it by installing the Xfce desktop. Is there a simple way to get Xubuntu installed without doing a complete new install?

4) Can you upgrade across Ubuntu versions, that is from vanilla Ubuntu to Xubuntu?

Thanks in advance

---

### Post by mastablasta on 2011-11-28
yeah you can install XFCE desktop (this will give you xubuntu), then log into it and you remove the GNOME (so you don't have double programmes). Then you upgrade to latest version of LTS :-)
 
here is how u install xfce:
[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)
 
then you remove Gnome (ubuntu) :
[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)
 
as i know XFCE has two desktops that is XFCE (which is basic XFCE) and Xubuntu (which is a bit more Ubuntu customised desktop). at leats the LTS had it like that.
 
you could also give Kubuntu a try.... :-)

---

### Post by blahsnr on 2011-11-28
> **mastablasta said:**
> yeah you can install XFCE desktop (this will give you xubuntu), then log into it and you remove the GNOME (so you don't have double programmes). Then you upgrade to latest version of LTS :-)
 
here is how u install xfce:
[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)
 
then you remove Gnome (ubuntu) :
[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)
  [snip]
Thanks. I'll have a go at installing xubuntu-desktop. The worst that can happen is that I have to re-install from scratch :D 

I think what I did last time was just to install the Xfce desktop rather than xubuntu-desktop. I searched on xfce in Synaptic rather than xubuntu.

---

### Post by ajgreeny on 2011-11-28
It is worth bearing in mind that installing just the xfce4 desktop will give you a system with a lot of what you are used to in ubuntu 10.04 missing.

If you install the xubuntu-desktop to ubuntu 10.04, and then remove all the gnome packages that are not dependencies of xubuntu-desktop, you will get a fully fledged system with just about all you need.  Xubuntu is not really the low resource requiring system that it used to be, but it is a very capable, and very configurable desktop system that will possibly pick up a lot of users who like the ubuntu system and setup, but like you (and me) can not get to grips with unity.

---

### Post by blahsnr on 2011-11-28
It worked a treat, or at least installing Xubuntu desktop did. I have not yet been brave enough to purge the gnome desktop from the system. I guess I had better do that before I do any more customisation.

---

### Post by blahsnr on 2011-11-28
> **ajgreeny said:**
> It is worth bearing in mind that installing just the xfce4 desktop will give you a system with a lot of what you are used to in ubuntu 10.04 missing.
.
[snip]
The only problems with Xubuntu that I have found are minor but make this version of Ubuntu somewhat less polished than the Gnome version. However I find the issues are less severe than the "Unity issue".

I had to install Mplayer and the Gecko Mplayer plugin to get most streaming video content to work and had to edit fstab to ensure that all (linux format) drives on the machine are mounted at startup. I am still a little irritated by the fact that you have to first start up network drives in Gigolo before you can view them in Thunar. I have seen a few posts about the shortcomings of Thunar and I guess it isn't a high priority to solve the (network) drive handling problems inherent in Xfce.

Now I have done these things again, I must remember to note down what I did to get Xubuntu to do what it should do out of the box. It will come in useful the next time I do an Xubuntu install. I also should make a note of the Wifi fix required for an EeePC 901 when installing 10.04 just in case I need to reinstall.

---

### Post by coffeecat on 2011-11-28
@blashnr, let me suggest another option for you to consider.

When the next LTS, 12.04, is released, it will not come with classic gnome as default but it will be possible to configure it to look and behave very much like the gnome 2 desktop that you prefer. Have a look at these two threads. This is in the Ubuntu +1 (12.04) subforum:

[http://ubuntuforums.org/showthread.php?t=1873765](http://ubuntuforums.org/showthread.php?t=1873765)

And this is for Oneiric/11.10 (at the moment) in the Desktop Environments forum:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

In essence, you install the gnome-session-fallback package (gnome3) from the Unity desktop, log out and in to the classic desktop to make that your default and then apply as many of the customisations as you want. You may prefer that to running Xfce as this will still be gnome, albeit gnome 3, and a desktop that you will be familiar with.

---

### Post by blahsnr on 2011-11-29
@coffeecat
Thanks for the links. My problem with this alternative solution is that it requires a considerably greater amount of customisation to get a suitable desktop UI than simply installing Xubuntu, choosing a theme and then making the three changes I made. The more you customise, the more likely that things will get broken by the next (LTS) release.

The situation would be considerably easier if Ubuntu were to consider bundling the M[ATE Desktop environment]("https://github.com/Perberos/Mate-Desktop-Environment") (a fork of Gnome 2) with 12.04. As 12.04 will no longer fit on a single CD anyway there are fewer reasons not to do this. The other advantage is that LTSers happy with Gnome 2.xx will have an upgrade path that offers them a predictable UI without them having to shift desktop environment or install yet another package and then customise their desktop.

IMHO LTS should not just be about continuity of technical support but also continuity of UI experience.

---

### Post by vasa1 on 2011-11-29
> **blahsnr said:**
> ... if Ubuntu were to consider bundling the M[ATE Desktop environment]("https://github.com/Perberos/Mate-Desktop-Environment") (a fork of Gnome 2) with 12.04....
Sorry, I very doubt that will happen.

---

### Post by blahsnr on 2011-11-29
> **vasa1 said:**
> Sorry, I very doubt that will happen.
I know, hence my interest in Xfce and Xubuntu ;) 

Even Win7 include a theme that  looks and behaves like the NT4/Win98  GUI. Which, for me, makes the  transition from earlier versions of  Windows to Win7 somewhat easier. I think it is important to reduce the UI/UX learning curve to a minimum when upgrading. I hope that Xfce and Xubuntu will continue to improve until 12.04 without completely changing the UX (or, at the very least, giving a simple to use option of a more traditional look and feel).

---

### Post by vasa1 on 2011-11-29
On a lighter note, they might figure that those who aren't happy have left and as time goes on, there'll be less and less incentive to retain legacy stuff.

---

### Post by blahsnr on 2011-11-29
@mastablasta
I've just purged Gnome from the install and rebooted without any obvious problems. I had to re-install Mplayer and the Gecko plugin as I expected but also had to install a bluetooth manager one thing I couldn't find in Xubuntu. 

Thanks for the advice. I'm now on the right track and hopefully I'll be able to upgrade to 12.04 version of Xubuntu in a couple of years time.

---

