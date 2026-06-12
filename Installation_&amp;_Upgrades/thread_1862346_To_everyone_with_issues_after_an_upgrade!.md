---
title: "To everyone with issues after an upgrade!"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by youngunix on 2011-10-16
Ubuntu 11.10 just came out, and a lots of people ran into a variety of problems after the upgrade (and I'm one of them) especially when I upgraded from 10.10 to 11.04. 
My point is that I hope everyone would find the list below useful and to give the Developers some time to work on the issues, until then please do the following (if you want or can):

1. determine the problem/bug
2. try to fix it or find a work around it
3. if it's something that really needs to get fixed right away or you couldn't find a solution, 
please post it on the forums as always

Here is the issue I'm dealing with at the moment: 
at the login screen , the "Ubuntu Classic" session is missing. Therefore, I'm unable to login to that session. (we all know how easy it is to find things when using it :)).

---

### Post by Megaptera on 2011-10-16
I don't think "classic" is included with 11.10. I think 11.04 was its last hurrah.

---

### Post by lnxusr351 on 2011-10-16
I want to go back to 11.04. 11.10 has more limitations.

---

### Post by youngunix on 2011-10-16
> **Megaptera said:**
> I don't think "classic" is included with 11.10. I think 11.04 was its last hurrah.

I think that makes more sense now, 'cuz I'm going nuts searching throughout the system and online.

---

### Post by youngunix on 2011-10-16
> **lnxusr351 said:**
> I want to go back to 11.04. 11.10 has more limitations.

sucks to hear that but what limitations are referring to? 

I know they've removed some options which is kind of a downer, but the issues I had were with Unity. 
It crashed a couple of times, the third time was actually the charm; all I got was a black log screen saying that some services started and what not, and that was it no login screen after several minutes. 
I did find a way around it but it was too much of a hassle so I went with a fresh install.

---

### Post by nheer on 2011-10-16
> **youngunix said:**
> Ubuntu 11.10 just came out, and a lots of people ran into a variety of problems after the upgrade (and I'm one of them) especially when I upgraded from 10.10 to 11.04. 
My point is that I hope everyone would find the list below useful and to give the Developers some time to work on the issues, until then please do the following (if you want or can):

1. determine the problem/bug
2. try to fix it or find a work around it
3. if it's something that really needs to get fixed right away or you couldn't find a solution, 
please post it on the forums as always

Here is the issue I'm dealing with at the moment: 
at the login screen , the "Ubuntu Classic" session is missing. Therefore, I'm unable to login to that session. (we all know how easy it is to find things when using it :)).
I solved the Unity desktop problem by downloading the Classic Gnome desktop.  Just give the command:

sudo apt-get install gnome-session-fallback

You'll be able to switch to it when you log on.

My problem is that mlterm (multi lingual terminal) keeps crashing.  It worked perfectly in 11.04.  Ubuntu needs to supply mlterm 3.0.8 instead of 3.0.6-1.

---

### Post by youngunix on 2011-10-16
> **nheer said:**
> I solved the Unity desktop problem by downloading the Classic Gnome desktop.  Just give the command:

sudo apt-get install gnome-session-fallback

You'll be able to switch to it when you log on.

My problem is that mlterm (multi lingual terminal) keeps crashing.  It worked perfectly in 11.04.  Ubuntu needs to supply mlterm 3.0.8 instead of 3.0.6-1.

You beat me to it lol! I've actually found it in Synaptic package manager and install it from there.
as for mlterm, I have no idea when will they update it yet, but you can get the latest stable version 3.0.8 from here (Note: you'll need to extract the .tar.gz file then install it)
[http://mlterm.sourceforge.net/](http://mlterm.sourceforge.net/)

---

### Post by juliancam on 2011-10-16
> **Megaptera said:**
> I don't think "classic" is included with 11.10. I think 11.04 was its last hurrah.

:confused:  Then what is the "Gnome Classic" (? my system is broken at the moment so I can't check if that is the exact wording) option in the user logon screen bottom left where "Ubuntu" shows by default?

Julian

---

### Post by youngunix on 2011-10-16
> **juliancam said:**
> :confused:  Then what is the "Gnome Classic" (? my system is broken at the moment so I can't check if that is the exact wording) option in the user logon screen bottom left where "Ubuntu" shows by default?

Julian

Gnome Classic is formerly known as Ubuntu Classic. It is recommended for people who are having problems running Unity due to hardware issues.

---

### Post by jimbo99 on 2011-10-16
Zing.

---

### Post by nheer on 2011-10-17
> **youngunix said:**
> You beat me to it lol! I've actually found it in Synaptic package manager and install it from there.
as for mlterm, I have no idea when will they update it yet, but you can get the latest stable version 3.0.8 from here (Note: you'll need to extract the .tar.gz file then install it)
[http://mlterm.sourceforge.net/](http://mlterm.sourceforge.net/)

Thanks for the information on the latest version of mlterm.  After I extract the .tar.gz will Ubuntu 11.10 have the dependencies necessary?  I'm afraid that  certain libraries needed by mlterm may have been upgraded or deleted in 11.10.

---

### Post by youngunix on 2011-10-18
> **nheer said:**
> Thanks for the information on the latest version of mlterm.  After I extract the .tar.gz will Ubuntu 11.10 have the dependencies necessary?  I'm afraid that  certain libraries needed by mlterm may have been upgraded or deleted in 11.10.

no problem. 

I'm not sure about the dependencies' question cuz i don't use mlterm. 
But if you don't want to take the risk of installing it, i suggest you use a virtual machine **(windows=vmware station, ubuntu=virtualbox**). 
Install ubuntu 11.10 on a it and do all the installations you might need and see how it works. 
Just FYI, in most cases people that installed ubuntu 11.04+ has had problems with Unity (including myself) so just try to find a workaround in case you run into the same issue.

now if you don't want to do that, you can try cloning your stable(working state) of ubuntu 11.10 onto a **separate hard drive** and then use one of them to install whatever software you want.

i hope that helps.

---

### Post by nheer on 2011-10-20
Thanks for all the information.  I think the easiest solution for me is just to be careful when using mlterm and never use the bidi function when I'm using an editor.  But I hate this new upgrade of Ubuntu.  I don't think I'll be making any more upgrades.  I wish I had stayed with 11.04.  Everything was working perfectly with the classic desktop.  This new Unity desktop really sucks.  I think it was designed for smartphones and tablets not for real computers.  At least I don't have to use it now that I've downloaded the gnome classic desktop. 


> **youngunix said:**
> no problem. 

I'm not sure about the dependencies' question cuz i don't use mlterm. 
But if you don't want to take the risk of installing it, i suggest you use a virtual machine **(windows=vmware station, ubuntu=virtualbox**). 
Install ubuntu 11.10 on a it and do all the installations you might need and see how it works. 
Just FYI, in most cases people that installed ubuntu 11.04+ has had problems with Unity (including myself) so just try to find a workaround in case you run into the same issue.

now if you don't want to do that, you can try cloning your stable(working state) of ubuntu 11.10 onto a **separate hard drive** and then use one of them to install whatever software you want.

i hope that helps.

---

