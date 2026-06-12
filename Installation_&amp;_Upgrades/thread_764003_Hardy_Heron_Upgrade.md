---
title: "Hardy Heron Upgrade"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by The New Guy on 2008-04-23
Im going to upegrade to Ubuntu 8.04 tomorrow, and I was wondering if I have to uninstall or back up anythng or wverything in my computer. Do I need to remove Compiz or XGL server? Can anyone give me some tips for the upgrade. Thanks.

---

### Post by Oldsoldier2003 on 2008-04-23
> **The New Guy said:**
> Im going to upegrade to Ubuntu 8.04 tomorrow, and I was wondering if I have to uninstall or back up anythng or wverything in my computer. Do I need to remove Compiz or XGL server? Can anyone give me some tips for the upgrade. Thanks.
It is always good to backup before any major change.

Make sure you have one of the desktop metapackages installed

Make sure if you used envy to set up your restricted drivers you remove the restricted drivers before you upgrade.

before attempting the upgrade and after completing those steps do  
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
then carry on with the update.

---

### Post by Dai777 on 2008-04-23
> **Oldsoldier2003 said:**
> 

Make sure if you used envy to set up your restricted drivers you remove the restricted drivers before you upgrade.

before attempting the upgrade and after completing those steps do  
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
then carry on with the update.

Could you explain why we would need to remove the restricted drivers.
What about things like printer drivers that I've had to get from Epson will they be lost when I upgrade. I have an XP installation in VirtualBox what will happen to that?

Is there a guide to doing the upgrade.

---

### Post by analoog on 2008-04-23
> **Dai777 said:**
> 

Is there a guide to doing the upgrade.
[https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

---

### Post by Oldsoldier2003 on 2008-04-23
> **Dai777 said:**
> Could you explain why we would need to remove the restricted drivers.
What about things like printer drivers that I've had to get from Epson will they be lost when I upgrade. I have an XP installation in VirtualBox what will happen to that?

Is there a guide to doing the upgrade.

If you used envy you want to remove the restricted drivers to avoid potential conflicts during the upgrade. (its recommended by the author of Envy, in the future this step won't be required, but for Ubuntu versions prior to hardy it is recommended)

Upgrading will break virtual box, but the first time you run it it will tell you how to fix it. Just paste the command into a terminal and it will recompile your kernel modules to support VirtualBox. This just isn't for a Hardy upgrade, the Vbox kernal modules will need to be recompiled any time you update your kernel. Your XP install inside of virtual box will be just fine.

---

### Post by FakeOutdoorsman on 2008-04-23
> **Oldsoldier2003 said:**
> Just paste the command into a terminal and it will recompile your kernel modules to support VirtualBox.

Show me this, "the command".

---

### Post by The New Guy on 2008-04-24
Well I couldn't wait until tomorrow so I already upgrade to Hardy Heron it took about 6 hours, I do not know why I guess it was the download part, and everything seems just a few problems here and there.

1.- The Advanced Desktop Effects are running a little bit slow.

2.- I cannot change the screen resolution, this appear, see the attachment at the bottom.

3.- Also Mozilla is a little bit slow when I browse on pages.

Can please someone help me on this. Thanks

PS just forget about the reply at the bottom. Sorry

---

### Post by The New Guy on 2008-04-24
Well I couldn't wait until tomorrow so I already upgrade to Hardy Heron it took about 6 hours, I do not know why I guess it was the download part, and everything seems just a few problems here and there.

1.- The Advanced Desktop Effects are running a little bit slow.

2.- I cannot change the screen resolution, this appear 

3.- Also Mozilla is a little bit slow when I browse on pages.

Can please someone help me on this. Thanks

---

### Post by ptcbus on 2008-04-24
Ubuntu servers are extremely crowded. You will be better off using torrents. SEe [http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html]("http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html")

---

### Post by drsaamah on 2008-04-24
When you go to System->Preferences->Screen Resolution does it NOT let you change the resolution or does it not give you the option for the correct resolution?
Also, I'm personally not a big fan of FF3 (at this stage of development) so maybe you want to compare it with FF2.  In a terminal type 'sudo apt-get install firefox-2" and that will install FF2 for you (without removing firefox 3 beta 5).  If this seems to fix your web browsing speed issue, then you can go ahead and un-install FF3 using "sudo apt-get remove firefox-3.0"  Hope Hardy treats you well!  So far I'm a big fan.

---

### Post by The New Guy on 2008-04-26
No when I click Screen and Resolution a little window appears 

"The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available."

and don't give me any other option.

---

### Post by mathenge on 2008-04-26
> **Oldsoldier2003 said:**
> It is always good to backup before any major change.

Make sure you have one of the desktop metapackages installed

Make sure if you used envy to set up your restricted drivers you remove the restricted drivers before you upgrade.

before attempting the upgrade and after completing those steps do  
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
then carry on with the update.

This doesn't seem to have solved my problem. I removed the NVidia restricted driver and still couldn't get past the "Distribution Upgrade" dialog where it's setting up the new software channels. Just seems to hang there. Took me almost 40 minutes to get my video back in Gutsy.

I'm still looking for a solution to this problem. I don't think that it's because the servers are too busy.

---

### Post by FakeOutdoorsman on 2008-04-26
> **mathenge said:**
> This doesn't seem to have solved my problem. I removed the NVidia restricted driver and still couldn't get past the "Distribution Upgrade" dialog where it's setting up the new software channels. Just seems to hang there. Took me almost 40 minutes to get my video back in Gutsy.

I'm still looking for a solution to this problem. I don't think that it's because the servers are too busy.

You can use a repository mirror.  I'm using one now that is in the same state I live in and speeds are excellent: [Official Ubuntu Archive Mirrors]("https://launchpad.net/ubuntu/+archivemirrors").  You can choose a new mirror easily with System -> Administration -> Software Sources (I think that is how to get there in Gnome, I don't remember) or:
```
gksu software-sources-gtk
```
Ubuntu Software Tab -> Download From: -> Other...
You can optionally choose "Select Best Server" which will give you the server with the best ping.

---

### Post by reg4c on 2008-04-26
> **The New Guy said:**
> Well I couldn't wait until tomorrow so I already upgrade to Hardy Heron it took about 6 hours, I do not know why I guess it was the download part, and everything seems just a few problems here and there.

1.- The Advanced Desktop Effects are running a little bit slow.

2.- I cannot change the screen resolution, this appear, see the attachment at the bottom.

3.- Also Mozilla is a little bit slow when I browse on pages.

Can please someone help me on this. Thanks

PS just forget about the reply at the bottom. Sorry
Are you using the Media version of Ubuntu?
Concluded from the icon of the Applications menu
If you are, could you englighten how to get it?

And if you are not, then could anyone enlighten how to get the media version of Ubuntu?
I forgot what its called.

Cheers

---

### Post by The New Guy on 2008-04-27
Is that Ubuntu Server? if that is the case no Im not, that is just  Ubuntu Studio theme.

---

