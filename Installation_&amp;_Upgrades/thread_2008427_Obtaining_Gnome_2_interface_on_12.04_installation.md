---
title: "Obtaining Gnome 2 interface on 12.04 installation"
date: 2012-06-22
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2012-06-22
I am currently doing an experimental installation of 12.04 on my other computer.

What I am wanting to know is, what (if anything) I can do after the 12.04 installation to make the Ubuntu interface the SAME as the Gnome 2 interface that is on my other main computer which is currently running Ubuntu 11.04.

I know that there are choices on the Ubuntu 12.04 login window which gives options for having interfaces other than the default 12.04 UNITY type interface, but the last time that I did an experimental installation of 12.04 and choose the Ubuntu classic interface from the login menu, I got a desktop interface which is **SOMEWHAT close** to Gnome 2 layout but not exactly the same.

Is there anyway to run (successfully) Gnome 2 interface on Ubuntu 12.04 installation (without reinventing the wheel) ???

Please, I am not asking for opinions as to whether I should use Unity or some interface other than Gnome 2, I am just wanting to know if it is possible and if so how.

Thanks.

---

### Post by oldfred on 2012-06-22
Ok, it is not exactly the same. But software does change or it gets stale. A few things are in different locations, but it is close enough for me.

gnome3 classic
sudo apt-get install gnome-panel
On login screen click on cog-wheel/star and choose 

12.04 LTS / Precise Classic (No effects) Tweaks and tricks
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

OR:
Open the Ubuntu Software Centre and search for ‘gnome-panel’, hit install and log out.
To move/add/edit panels or applets press Alt+Right Click

---

### Post by arpanaut on 2012-06-22
Check out this thread: [http://ubuntuforums.org/showthread.php?t=1966370&highlight=gnome+classic](http://ubuntuforums.org/showthread.php?t=1966370&highlight=gnome+classic)

Probably going to be as close as one can get:
although it looks a lot like "reinventing the wheel"

Or thy the Mate environment on Mint

good luck

---

### Post by garyzw on 2012-06-22
On Ubuntu 12.04 I use MATE 1.2 desktop which is a fork of gnome 2

I like it much better then gnome 3

[http://mate-desktop.org](http://mate-desktop.org)

---

### Post by garyzw on 2012-06-22
You can install MATE 1.2 without the need for Mint.

> **arpanaut said:**
> Check out this thread: [http://ubuntuforums.org/showthread.php?t=1966370&highlight=gnome+classic](http://ubuntuforums.org/showthread.php?t=1966370&highlight=gnome+classic)

Probably going to be as close as one can get:
although it looks a lot like "reinventing the wheel"

Or thy the Mate environment on Mint

good luck

---

### Post by arpanaut on 2012-06-22
> You can install MATE 1.2 without the need for Mint.

Thanks I did not know that.
Unity user here, never felt the need to research the possibility.

---

### Post by wpshooter on 2012-06-22
> **garyzw said:**
> On Ubuntu 12.04 I use MATE 1.2 desktop which is a fork of gnome 2

I like it much better then gnome 3

[http://mate-desktop.org](http://mate-desktop.org)

Gary:

Can the MATE interface / desktop be found in Synaptic ?

If not what / where is the best method for installing it ?

I think I will give it a try on the experimental computer.

Thanks.

---

### Post by Myrddin Emrys on 2012-06-22
MATE is what you want. It's the original Gnome 2 code, only slightly updated. See:

[http://ubuntuforums.org/showpost.php?p=11931784&postcount=20](http://ubuntuforums.org/showpost.php?p=11931784&postcount=20)

Edit: You can install it with Synaptic if you first add the developers' repository (it's not in the official Ubuntu repositories).

---

### Post by wpshooter on 2012-06-22
> **Myrddin Emrys said:**
> MATE is what you want. It's the original Gnome 2 code, only slightly updated. See:

[http://ubuntuforums.org/showpost.php?p=11931784&postcount=20](http://ubuntuforums.org/showpost.php?p=11931784&postcount=20)

Edit: You can install it with Synaptic if you first add the developers' repository (it's not in the official Ubuntu repositories).

How do you add the develoer's repository ?  Is this a check box in Synapic ?

Thanks.

---

### Post by Myrddin Emrys on 2012-06-22
Settings->Repositories->Other software->Add...

It may be easier just to type in the commands listed in one of the guides I reference in my previous post (see link above). But if you want to use the Synaptic GUI, you can get the relevant deb line to add and the package names to install from these guides.

---

### Post by garyzw on 2012-06-22
Add the repo to /etc/apt/sources.list via the following command:

sudo add-apt-repository "deb [http://packages.mate-desktop.org/repo/ubuntu](http://packages.mate-desktop.org/repo/ubuntu) precise main"

MATE Installation (both Oneiric/Precise)

Then run the following command to update your repositories and install MATE:

sudo apt-get update
sudo apt-get install mate-archive-keyring
sudo apt-get update
# this install base packages
sudo apt-get install mate-core
# this install more packages
sudo apt-get install mate-desktop-environment

> **wpshooter said:**
> Gary:

Can the MATE interface / desktop be found in Synaptic ?

If not what / where is the best method for installing it ?

I think I will give it a try on the experimental computer.

Thanks.

---

### Post by garyzw on 2012-06-22
What is nice is all you have to do is log out and select which desktop you want to use and log back in--Unity or MATE 1.2.

So install Mate will not remove or damage Unity in anyway.

When you re-boot your computer it will automatically go back to the last Desktop environment you last used.

> **arpanaut said:**
> Thanks I did not know that.
Unity user here, never felt the need to research the possibility.

---

### Post by wpshooter on 2012-06-23
> **garyzw said:**
> Add the repo to /etc/apt/sources.list via the following command:

sudo add-apt-repository "deb [http://packages.mate-desktop.org/repo/ubuntu](http://packages.mate-desktop.org/repo/ubuntu) precise main"

MATE Installation (both Oneiric/Precise)

Then run the following command to update your repositories and install MATE:

sudo apt-get update
sudo apt-get install mate-archive-keyring
sudo apt-get update
# this install base packages
sudo apt-get install mate-core
# this install more packages
sudo apt-get install mate-desktop-environment

Gary:

Thanks for this info, it worked perfectly and now I have an interface with 12.04 that has the same looks as Gnome 2.

On a side note, every time that I have experimented with installing Ubuntu 12.04 (including this time also) after the installation was finished and even after all the available updates were applied, I would get an error message popping up regarding something to the effect "that Ubuntu 12.04 has generated an internal system error" and asking me if I wanted to report the error.

However, strangely, after I followed your instruction for installing MATE, I have NOT received that strange pop up message regarding the occurrence of an internal system error !!!

I am going to log back in to the UNITY interface and see if the pop up comes back.

Thanks.

---

### Post by garyzw on 2012-06-23
I got the "Ubuntu 12.04 has generated an internal system error"
also but it stopped after all the Ubuntu updates but have not noticed any error messages either after MATE was installed.

> **wpshooter said:**
> Gary:

Thanks for this info, it worked perfectly and now I have an interface with 12.04 that has the same looks as Gnome 2.

On a side note, every time that I have experimented with installing Ubuntu 12.04 (including this time also) after the installation was finished and even after all the available updates were applied, I would get an error message popping up regarding something to the effect "that Ubuntu 12.04 has generated an internal system error" and asking me if I wanted to report the error.

However, strangely, after I followed your instruction for installing MATE, I have NOT received that strange pop up message regarding the occurrence of an internal system error !!!

I am going to log back in to the UNITY interface and see if the pop up comes back.

Thanks.

---

### Post by wpshooter on 2012-06-29
After installing "MATE", I notice that on some of the menu items (like the calculator, for instance) are listed TWICE.

Why is this and how do you get rid of the duplicate menu items ?

Thanks.

---

### Post by garyzw on 2012-06-29
> **wpshooter said:**
> After installing "MATE", I notice that on some of the menu items (like the calculator, for instance) are listed TWICE.

Why is this and how do you get rid of the duplicate menu items ?

Thanks.


I had the same problem just right click on the MATE start icon and click "Edit Menus" then uncheck the double ones.

---

### Post by Lyfang on 2012-06-29
Novice users might also want to check out Linux Mint 13 "Maya" with MATE installed.

---

### Post by sloany on 2012-07-03
> **oldfred said:**
> But software does change or it gets stale.

I tend to disagree. If it ain't broke, don't fix it!

---

### Post by Lyfang on 2012-07-03
> **sloany said:**
> I tend to disagree. If it ain't broke, don't fix it!
Linus Torvalds used GNOME 2.
[QUOTE=RetroX]Considering how it was Linus' wish to have a GNOME 2 fork, I'm surprised that there aren't more people that are jumping to help out with this. I think that the goal should be to eventually port GNOME 2's core applications to GTK 3, because while GNOME 3 is a step down from GNOME 2, GTK 3 is a huge step up from GTK 2. Considering how applications like nautilus and GDM are already ported to GTK 3, that should be a big help; in the case of applications like GDM, it should really be a matter of removing dependencies for the GNOME 3 Shell and Fallback Panel (or, rather, modifying the fallback panel to have GNOME 2's functionality).[/QUOTE]

Source: [https://bbs.archlinux.org/viewtopic.php?pid=980201#p980201](https://bbs.archlinux.org/viewtopic.php?pid=980201#p980201)

See also: [http://linux.slashdot.org/story/11/08/04/0115232/linus-torvalds-ditches-gnome-3-for-xfce](http://linux.slashdot.org/story/11/08/04/0115232/linus-torvalds-ditches-gnome-3-for-xfce)

---

### Post by wpshooter on 2012-07-03
> **sloany said:**
> I tend to disagree. If it ain't broke, don't fix it!

+1

My sentiments exactly !!!

---

