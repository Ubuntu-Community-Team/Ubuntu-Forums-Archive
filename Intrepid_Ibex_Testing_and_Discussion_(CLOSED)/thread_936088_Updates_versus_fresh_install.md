---
title: "Updates versus fresh install"
date: 2008-10-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by QwUo173Hy on 2008-10-02
I´ve read in a thread that if you´ve been updating your alpha 6, then you won´t need to install the beta when it comes out as you will effectively have it already. Is this always the case?

I remember putting a Hardy alpha on a friends laptop and some hardware detection problems we could never resolved, but when he installed the Beta, it worked great.

I thought he was updating but I could be wrong.

Can anyone put me straight?

---

### Post by bobnutfield on 2008-10-02
I will only speak from my own experience.  I installed Hardy as Alpha and continued on updating through all the bugs to the stable release.  Hardy never did perform very well for me and continued to feel buggy even after the stable release.  I have just installed the Alpha 6 Intrepid and updated to Beta and it is already far more stable than Hardy ever was for me.

So, in essence, if you can take my experience as any guide, install the most recent version you can

---

### Post by bobnutfield on 2008-10-02
Sorry, double post

---

### Post by zoomy942 on 2008-10-02
> **jarlath said:**
> I´ve read in a thread that if you´ve been updating your alpha 6, then you won´t need to install the beta when it comes out as you will effectively have it already. Is this always the case?

I remember putting a Hardy alpha on a friends laptop and some hardware detection problems we could never resolved, but when he installed the Beta, it worked great.

I thought he was updating but I could be wrong.

Can anyone put me straight?


i was wondering the same thing

---

### Post by QwUo173Hy on 2008-10-02
Thanks bobnutfield, but what I´d need to know is if you did a clean install of Hardy - how did it compare to following the upgrade path through the Alphas as you did?

I´m insterested in how the same software compares when installed from stable versus upgraded from an alpha.

---

### Post by bobnutfield on 2008-10-02
I suppose I was confusing in my post.  What I meant to say is that installing straight from Beta or Stable versus Alpha is, in my opinion, always going to give you a better result.  I have not done this on Ubuntu, but I have in Fedora 9.  On one laptop, I installed the Alpha and followed the updates through to the stable release.  The other, I installed straight from the stable release, and there was no comparison:  the stable release was just that - stable.

The point is, I installed Intrepid in Beta, where I had install Hardy in early Alpha following the updates.  Intrepid, having installed at a much later release than I did with Hardy, is already better for my machine.

---

### Post by Kow on 2008-10-02
Alpha's, betas, etc are just cherry-picked "snapshots" of the current repositories. Once you upgrade to the development branch you don't need to keep upgrading to newer alphas, betas, etc. In fact, from a testing standpoint it may be better to not do fresh installs every time so Ubuntu can get more feedback on package upgrades (and dist upgrades). You'll notice a lot of upgrade-related bug fixes just after a distribution release because they do not get tested well enough beforehand. That being said, when you do upgrade from a released distribution to the current development via update-manager the nice thing to know is you'll be immediately upgrading to the latest version of the development tree.

---

### Post by nanog on 2008-10-02
> Intrepid, having installed at a much later release than I did with Hardy, is already better for my machine.

I have several boxes that have gone through upgrade all the way from dapper. They are running tight. If you do not clutter your box with 3rd party debs or binaries there is typically no difference between an upgrade and fresh install. If you do use 3rd party software its not a bad idea to test for complete removal in virtualbox before you install.

---

### Post by Grimhound on 2008-10-02
How would I go about upgrading from the standard 8.04 to the 8.10 beta?

---

### Post by ktp on 2008-10-02
> **Grimhound said:**
> How would I go about upgrading from the standard 8.04 to the 8.10 beta?

Upgrading from Ubuntu 8.04

To upgrade from Ubuntu 8.04, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '8.10' is available. Click Upgrade and follow the on-screen instructions.

---

### Post by Sef on 2008-10-02
>  	Quote:
 	 	 		 			 				 					Originally Posted by **Grimhound** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=5895425#post5895425") 				
 				*How would I go about upgrading from the standard 8.04 to the 8.10 beta?*
 			 		 	 	 
Upgrading from Ubuntu 8.04

To upgrade from Ubuntu 8.04, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '8.10' is available. Click Upgrade and follow the on-screen instructions.

**Back up** your data first.   There is no 100% guarantee that all will go well.

---

### Post by wilsong on 2008-10-02
I tried to update through the internet from 8.04 to the ALPHA 6 of 8.10 , this caused me very painful issues.. 

I would recommend if your going to make the jump to download the latest iso if 8.10

Once on 8.10 ive had no issues going from Alpha 6 to Beta, since the updates are just coming down... 



I would highly recommend if you cannot wait to back up all your data and dive in! But if you dont enjoy trying to tinker with things and fix errors and find out more about your system it might be best to wait for the release of the 8.10 its just about a month away!

---

