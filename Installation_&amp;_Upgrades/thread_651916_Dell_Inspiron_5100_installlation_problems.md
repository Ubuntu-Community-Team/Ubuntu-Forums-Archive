---
title: "Dell Inspiron 5100 installlation problems"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by mormang on 2007-12-28
I am trying to install Ubuntu 7.10 on a Inspiron 5100 from a CD, downloaded from Ubuntu, but it freeze.

I already have Ububtu 6.06 on this computer working fine, so I don't know what it could be.

help please

Cheers

G

---

### Post by mormang on 2007-12-28
when it freezes it is "detecting file system"

---

### Post by halw on 2007-12-28
Did you check the burn to make sure it was good?

---

### Post by mormang on 2007-12-28
yes I did, the CD is ok, I also burnt a new one just in case but the same thing happened

---

### Post by halw on 2007-12-28
I'm stumped. I have a dell 5150 that I had loaded with Ubuntu for a while. No problems with it.

BTW, are using live cd or alternate?

---

### Post by John Matrix on 2007-12-29
I have the very same problem. I have installed 7.10 both from the live CD and from the alternative CD. When I finally log into my account after the installation process, everything freezes shortly after the music sounds. The mouse cursor does move, but the screen is otherwise blank (light orange/brown). After a few minutes, the laptop powers itself off.
On the second attempt I do not even get this far. The system freezes before the login screen is reached, with a black screen. Again, it powers itself off after a few minutes.

Part of the problem seems to be the ati graphics driver picked by the installation program. The solution to this I found here:

[https://bugs.launchpad.net/ubuntu/+bug/146707](https://bugs.launchpad.net/ubuntu/+bug/146707)

With this fix, I was able to login without problems.

However, the system still suddenly powers itself off after a
few minites (i.e. it goes dead, no clean shut down). Still looking
for a solution to that....

---

### Post by John Matrix on 2007-12-30
Under KDE, I managed to get the power down problem under control now. I'm discussing it here
[http://ubuntuforums.org/showthread.php?p=4041796#post4041796](http://ubuntuforums.org/showthread.php?p=4041796#post4041796)

where this topic belongs.

---

### Post by FineArtist on 2008-05-12
I have a similar problem but not with a Dell laptop. 

I have been using a number of different Linux Distros over the past few years. I have enjoyed using Ubuntu 7.10 Gutsy Gibbon, Kubuntu 7.10, Linux Mint Daryna amd the KDE version. I use 64 bit mostly so hope Mint will follow suite. I have one big problem with the 8.04 series and that is Busy Box. On one computer I have no trouble but on the other I cannot load beyond a Busy Box freeze. Both computers have similar spec. Amd 939 processors on Asus Motherboards and ATI graphics cards both with 2 Gig of RAM. Up till now I have had no problems with loading any Linux distro I have tried on Laptop or Desktop. I was beginning to convert quite a few people but now I have doubts because of this Busybox issue. Has anyone had the same experience and how does one get over it? I need help as I was in the process of trying to convince a number of schools to use Linux based on the Ubuntu or Mint 8.04 series.

Will be interested to hear the solutions.

---

### Post by tylerspaska on 2008-05-12
I have a 5100 and had the same problem (I think). Ubuntu doesn't detect the right video drivers or something like that. You have to use the 'vesa' driver with 7.10. I think there is some workaround to use the ati driver, but I'm not sure what it is. You are much better off using 7.04 or upgrading to 8.04 (which works perfectly). 

If you are dead set on using 7.10 then let the system start up with the live cd or after an alternitive install. Even thought the screen goes blank it is still doing things (unless you are having a different problem entirely). After you are sure the system has started - after a few minutes - hit Ctrl+Alt+F1 and type 'sudo dpkg-reconfigure xserver-xorg' choose the vesa driver and use the simple mode to set up your monitor size/resolution. Restart X with Ctrl+Alt+Backspace.

That should fix it, but you can forget about using compiz or even screensavers (other than blank or really simple ones) with the vesa driver. As I said you are much better off with 8.04.

Edit: I just realized how old this thread is.

---

