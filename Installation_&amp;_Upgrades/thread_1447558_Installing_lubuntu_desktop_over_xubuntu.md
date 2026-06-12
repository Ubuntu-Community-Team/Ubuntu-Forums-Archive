---
title: "Installing lubuntu desktop over xubuntu"
date: 2010-04-05
forum: Installation &amp; Upgrades
---

### Post by happysadhu on 2010-04-05
Hi,
I want to switch my xubuntu desktop to lubuntu desktop without having to reinstall the whole OS system. I installed lubuntu desktop with the synaptic manager, but when I rebooted the xubuntu (xfce) desktop still came up.

Any ideas?
Sam

---

### Post by phillw on 2010-04-05
Hi and welcome to the forum,

When you get the log on screen, you should see the option to select either xcfe or lxde as your system.

For lubuntu specific updates you'd need to pop on the lubuntu ppa, details of that and doing updates can be found at [http://forum.phillw.net/viewtopic.php?f=4&t=54](http://forum.phillw.net/viewtopic.php?f=4&t=54)

I am assuming that you're running the 10.04 version and not the 9.10 beta.

Regards,

Phill.

---

### Post by happysadhu on 2010-04-05
Thanks.
I was able to login to a lubuntu session, but the ppa given in the page you linked to doesn't work (can't fetch it). I am using xubuntu 9.10 as the base installation.

Is there a way of login into a new session through the command/terminal prompt?

Sam

---

### Post by phillw on 2010-04-06
> **happysadhu said:**
> Thanks.
I was able to login to a lubuntu session, but the ppa given in the page you linked to doesn't work (can't fetch it). I am using xubuntu 9.10 as the base installation.

Is there a way of login into a new session through the command/terminal prompt?

Sam

The lubuntu ppa is for Lucid (10.04), there has been a real lot of work done since 9.10 beta. If you're tied to 9.10, you have a couple of choices.
[LIST]Wait for 10.04 of Lubuntu and use that
Make a partition of about 2GB (More if you can spare it) and put the beta of 10.04 on.
[/LIST]

Whilst you would be on a test version, the entire *buntu 10.04 series has been very stable, as befits a development version for a LTS release.

I don't know how much disk space you have, but making a seperate /home partition is real handy to have and does not use any more disk space up. If you want to try out a 10.04 then I'd suggest just copying over from the 9.10 partition that which you would need for the 10.04, as opposed to linking directly just in case a 10.04 had a 'bad day' and damaged data in your /home area.

It may sound really complicated, but it is not. [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) is an excellent tutorial to get your /home moved. Whilst you are doing the 'add partition' step just add an extra little one for use by Lubuntu 10.04, and leave it there while you move your /home. The install of lubuntu (or any of the *buntu's) will note that there is a 'free area' and offer to put themselves on there as totally self contained system.

I hope that helps with some of choices / options that you have.

Regards,

Phill.

---

### Post by happysadhu on 2010-04-06
Hi,
Thanks again for the detailed replies PhillW. Very helpful!

How do I prevent the items from the Lubuntu menu appearing in the Xubuntu/Ubuntu menus?  For example, new I have two terminal and file manager choices under Applications > Accessories when viewing the Ubuntu desktop, when I only want one.

Sam

Edit: I've moved my additional question above regarding 
    
 			  	 	 	 	 		 		 			 			 				 				**Removing LXDE/Lubuntu programs** from the Ubuntu menu to the Desktop Environments forum.
[http://ubuntuforums.org/showthread.php?t=1449450](http://ubuntuforums.org/showthread.php?t=1449450)

---

