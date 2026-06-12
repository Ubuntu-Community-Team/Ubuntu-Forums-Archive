---
title: "Installation and Xorg configuring questions."
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by Mol_Bolom on 2008-10-30
I know I shouldn't post two questions in one place, but eh, I figure they both have something to do with configures during installation.

First off I downloaded Ubuntu 8.04 liveCD to try to entice my wife into trying it out.  I used it first on our newer machine with a dual core processor, which it ran beautifully.  She did like how the windows wobbled, however, compiz although running didn't have anything to configure it.

So I tried installing it onto my older computer with a 2.0g processor which is running Zenwalk 5.2.  Now, I'm used to using fdisk and another partition manager and have had no problems with those, but when I first tried using the manual partitioning in the Ubuntu install, right before I selected Next to complete the installation, it stated it was going to do something to sda, which I had explicitely set up sdc3 as being the root partition for Ubuntu.  The second time I installed it I just installed it completely onto my 3rd disk, so now it at least runs.  Before I actually go on to attempt to install Ubuntu alongside Vista, I'd like to know why it said it was going to mess with the first disk when I had setup the 3rd partition on the 3rd disk for installation.

The next question is about xorg.conf.  Whenever I installed either Zenwalk, Vector Linux, Puppy, etc, etc when I was testing the different distros all I had to do was edit xorg.conf and add Device "i810" into them, but the layout of xorg.conf is very different. Also, not to mention I can't edit the file anyway.  It say's I don't have permission to do so.  I'm guessing that I only setup a user and not the root, so what would the general root password be so I can configure all these problems?

Note:  I have figured out how to use apt-get from the shell which I downloaded mc I haven't figured out how to use vi yet, and I had already downloaded and installed the xorg intel drivers before I made the mistake of changing the screen size to which I only get a black screen now. All editing I can do will either be from the shell or from Zenwalk...

Thanks for any help...

---

### Post by 080729jk on 2008-10-30
:  &#25554;&#19978;&#20132;&#25442;&#26426;&#30340;&#30005;&#28304;&#65292;&#23558;&#32593;&#32447;&#19968;&#31471;&#36830;&#25509;&#36335;&#30001;&#22120;&#30340;LAN&#21475;&#65292;[**&#21271;&#20140;&#32593;&#32476;&#30005;&#35805;**](http://www.51noder.com)&#21478;&#19968;&#31471;&#36830;&#25509;&#20132;&#25442;&#26426;UPLINK&#21475;&#12290;      4&#12289;[**&#21271;&#20140;&#32593;&#32476;&#30005;&#35805;**](http://www.51noder.com)&#35805;&#26426;&#25110;&#32773;&#32593;&#20851;&#24590;&#26679;&#19982;&#20132;&#25442;&#26426;&#30456;&#36830;&#65311;  &#31572;&#65306;&#25554;&#19978;&#35805;&#26426;&#25110;&#32773;&#32593;&#20851;&#30005;&#28304;**&#65292;**[**&#21271;&#20140;&#32593;&#32476;&#30005;&#35805;**](http://www.51noder.com)&#23558;&#35805;&#26426;&#25110;&#32773;&#32593;&#20851;&#30340;LAN&#21475;&#19982;&#20132;&#25442;&#26426;&#30340;&#20854;&#23427;&#21475;&#30456;&#36830;&#12290;    5&#12289;&#19968;&#26465;&#23485;&#24102;&#33021;&#35013;&#22810;&#23569;&#37096;&#32593;&#32476;&#30005;&#35805;&#65311;  &#31572;&#65306;&#25105;&#20204;&#32593;&#32476;&#30005;&#35805;&#35821;&#38899;&#32534;&#30721;&#21344;&#24102;&#23485;&#20026;6.3k[**&#21271;&#20140;&#32593;&#32476;&#30005;&#35805;**](http://www.51noder.com)**,**&#20877;&#26681;&#25454;&#20320;&#30340;&#24102;&#23485;&#38500;&#20197;6.3k,[&#21271;&#20140;&#32593;&#32476;&#30005;&#35805;](http://www.51noder.com)&#23601;&#26159;&#20320;&#33021;&#25509;&#30340;&#32593;&#32476;&#30005;&#35805;&#25968;&#37327;&#12290;

---

### Post by Partyboi2 on 2008-10-30
> First off I downloaded Ubuntu 8.04 liveCD to try to entice my wife into trying it out. I used it first on our newer machine with a dual core processor, which it ran beautifully. She did like how the windows wobbled, however, compiz although running didn't have anything to configure it.You can configure compiz by installing compizconfig-settings-manager
from a terminal (Applications>Accessories>Terminal)
```
sudo apt-get install compizconfig-settings-manager 
``` Then you can launch it from System>Pref>compizconfig-settings-manager.
Here is a [[COLOR=Blue]howto[/COLOR]]("http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion") for compiz.
> 
I'd like to know why it said it was going to mess with the first disk when I had setup the 3rd partition on the 3rd disk for installation. I have never seen this happen, I guess all you can really do is make sure everything is set correct before you commit to the changes.
> 
Also, not to mention I can't edit the file anyway. It say's I don't have permission to do so. I'm guessing that I only setup a user and not the root, so what would the general root password be so I can configure all these problems?To gain admin rights to modify the file you will need to use sudo.  So from a terminal you could open the file by
```
sudo nano /etc/X11/xorg.conf
``` (you can replace nano with vi if you prefer)or if you prefer using a gui text editor you can use gedit, you can open that with admin rights by
```
gksu gedit /etc/X11/xorg.conf
``` You can read more about sudo [[COLOR=Blue]here[/COLOR]]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Mol_Bolom on 2008-10-30
I had pretty much stuck on using su, havne't tried sudo yet except for some installing of files on Vector 5.9 std when I was trying it out...

I'll give it a try and see what happens. Thanks...

---

### Post by Mol_Bolom on 2008-10-30
Well, I'll be.  It works, rather jumpy on this old machine, but eh, I've got no plans on keeping it.  Will be interesting to see my wifes reaction, ha ha...

As for the graphics card, hoo boy was that a pain.  I had first tried just editing the xorg.conf, that didn't work, but when rebooting, it said that there was no graphics card found.  So I selected one thing, I can't remember which, to get the i810 working, that didn't work.  Then I tried copying over the device, monitor, and screen settings in my Zenwalk xorg.conf file, again, no graphics driver found, so this time I selected from a set of drivers, and changed the monitor type, and voila, it worked.  Only after reboot though, before the monitor and keyboard went dead...

Thanks for your help. Wado, ksdelvhvi.

---

