---
title: "Upgrade to 9.10 uses xfce - How to get GNOME back??"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by torchfire on 2009-12-07
Good morning, All.

I upgraded from 9.04 to 9.10 vie Update Manager.  (I did make the mistake of not installing the latest updates first, as recommended.  Found out about that too late. My bad.) 

So I just clicked Upgrade, and went off to do something else.

When it was finished, I now somehow have xfce, rather than Gnome. 

I don't like xfce.  How do I get Gnome back permanently? 

Any help will be appreciated.

Thanks. 
Torch

---

### Post by snowpine on 2009-12-07
> **torchfire said:**
> Good morning, All.

I upgraded from 9.04 to 9.10 vie Update Manager.  (I did make the mistake of not installing the latest updates first, as recommended.  Found out about that too late. My bad.) 

So I just clicked Upgrade, and went off to do something else.

When it was finished, I now somehow have xfce, rather than Gnome. 

I don't like xfce.  How do I get Gnome back permanently? 

Any help will be appreciated.

Thanks. 
Torch

Check out this tutorial: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by torchfire on 2009-12-07
Thanks, Snowpine, but I've checked the Synaptic Package Manager, and xubuntu is not installed, meaning none of the xubuntu-specific apps are installed. 

ubuntu-desktop is installed.  As are several (if not all) of the xfce packages.


Do you think if I remove all the xfce packages mentioned in your script, that would work?  or should I just reinstall ubuntu-desktop?  or just run your 'remove xubuntu' script in its entirety, even though many of the named packages are not installed? 

What do you think? 

Torch

---

### Post by estyles on 2009-12-07
I'm assuming you still get the gdm login screen?  At the bottom, when you log on, it should allow you to choose your session.  Make sure it's set to Gnome (or maybe Gnome failsafe) and log in.

Assuming that works properly and it actually boots into Gnome, then you can remove xfce packages.  I wouldn't remove them until you're successfully getting into Gnome, though...

---

### Post by snowpine on 2009-12-07
> **torchfire said:**
> Thanks, Snowpine, but I've checked the Synaptic Package Manager, and xubuntu is not installed, meaning none of the xubuntu-specific apps are installed. 

ubuntu-desktop is installed.  As are several (if not all) of the xfce packages.


Do you think if I remove all the xfce packages mentioned in your script, that would work?  or should I just reinstall ubuntu-desktop?  or just run your 'remove xubuntu' script in its entirety, even though many of the named packages are not installed? 

What do you think? 

Torch

Hi Torch, that script should uninstall all xfce packages on your system, then install ubuntu-desktop. The author of the script is a trusted member of these forums, I think it is safe. :)

---

### Post by torchfire on 2009-12-07
Thanks Estyles.  I set it up to ask for my credentials, and on the second try, I did see the stuff at the bottom.  (Don't know why it didn't work on the first reboot after changing the login thing.) 

I'm now in gnome.  

Snowpine, I ran the script, but it seemed to want to remove 100 packages (including ubuntu-desktop) and not install any.  Very strange.  I chose not to continue, at that point.  I did save the output, if you're interested in seeing it.  Just let me know. 

I have another question that maybe you two can help with.   I installed Mythbuntu quite some time ago, but never followed through with using it.  Is it safe to remove the Mythbuntu packages to revert back to Ubuntu? 

Thanks for all your help.  
Torch

---

### Post by snowpine on 2009-12-07
> **torchfire said:**
> Snowpine, I ran the script, but it seemed to want to remove 100 packages (including ubuntu-desktop) and not install any.  Very strange.  I chose not to continue, at that point.  I did save the output, if you're interested in seeing it.  Just let me know. 


Sorry you did not find the script useful (it's not mine so I take no credit).

If you'd followed it through to the end, you'd have seen the last step is 'sudo apt-get install ubuntu-desktop'.

---

### Post by torchfire on 2009-12-07
I guess it scared me, Snowpine.   I do appreciate your help, and if I continue to have problems with xfce being the default, I'll give it a try.

---

### Post by snowpine on 2009-12-07
> **torchfire said:**
> I guess it scared me, Snowpine.   I do appreciate your help, and if I continue to have problems with xfce being the default, I'll give it a try.

No worries. :) 

psychocats.net is a great resource that has rescued me from many a jam.

---

### Post by torchfire on 2009-12-07
Yes, it looks like a very good site.  I've made it a favorite.  Thanks for turning me on to it. 

Torch

---

