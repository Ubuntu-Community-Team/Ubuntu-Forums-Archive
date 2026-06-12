---
title: "Fix graphic issues or move apps and setting over"
date: 2024-11-11
forum: Installation &amp; Upgrades
---

### Post by Chrisfs on 2024-11-11
Hi, 
I have used Ubuntu for quite a while but I'm also not an expert. I can get to the command line but don't know about the directory structure or settings, drivers etc. 

I have a Dell Optiplex 755. I upgraded to 24.04.01 LTS.  The first upgrade, I choose 'Use third party drivers'  and when I rebooted, I got a login window with a text area. But when I try to type in the text area, no text shows up.  There was an  < on the left of the screen and a > on the right  and a drop down on the top of the screen. When I click on any of these, the entire screen starts flicking rapidly until I move my mouse away. 

So I tried a second install (not replacing the first, along side it). I chose not to use 3rd party drivers. This install went well, but it's a completely fresh install. It has Firefox as the browser. I was using chromium before and had lots bookmarks and passwords stored. I also had apps like discord that don't appear in the new install. 

How can I fix the first install (and get my original set up back), I don't even know how to bot that install right, the pc just boots into the good install automatically. 
 or move everything from that install to my new one, so getting my settings and apps back. 

I recognize this is probably a multi step process with more info needed, but I really appreciate help people can give to help me get my pc back to a usable state. 

Thanks, 

Chris S

---

### Post by grahammechanical on 2024-11-12
> but it's a completely fresh install. It has Firefox as the browser. I  was using chromium before and had lots bookmarks and passwords stored. I  also had apps like discord that don't appear in the new install.

This is how it should be for a fresh install. You can always install those applications that you want and are not part of the default Ubuntu installation. But, more importantly, how do you access all your data?

There is a ray of sunshine in all of this. You now have two installs of Ubuntu on your machine. Now, when you boot the machine you should see a Grub boot menu. At the top of the menu is the word "Ubuntu." Click on that and you will load into new Ubuntu.

Further down the Grub menu you will see another Ubuntu 24.04.1 LTS. That is the old Ubuntu that is broken. Underneath that line you will see Advanced Options for Ubuntu. Select Advanced Options and a list of Linux kernels will appear. Select one that has recovery mode in brackets. That will load the Recovery Menu. Select Resume. That should load to a login screen and a working desktop environment using an open source video driver. You now have access to your data and chosen applications.

Open Software and Updates>Additional Drivers tab and disable the proprietary video driver. You need to be connected to the internet to for this to work. Now you can load into Old Ubuntu 24.04 LTS whenever you like.

You now have choices.

1) Continue using new Ubuntu 24.04.1 LTS and install Chromium and Discourse and also find a way to transfer all your data over.

2) Use old Ubuntu 24.04.1 LTS and make it the default OS to load from the Grub menu. This means putting the old Ubuntu 24.04.1 at the top of the Grub menu under the label of "Ubuntu," There is a way to do this. It is a question for another thread in this forum. We shall need to know the layout of all your partitions in order to give accurate advice.

Regards

---

