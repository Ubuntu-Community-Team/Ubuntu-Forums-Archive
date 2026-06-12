---
title: "Updating and Upgrading"
date: 2012-01-04
forum: Installation &amp; Upgrades
---

### Post by paddyjoe on 2012-01-04
I have bought The Official Ubuntu Book Sixth Edition and would like to update from 10.04 to 11.04. On page 108 the paragraph Moving to the Next Ubuntu Release says the book has been revised to the latest version - 11.04. 
The next paragraph Doing the Actual Upgrade says when a new release is available the Upgrade Manager tells you when a new  version of Ubuntu is available and walks you through the upgrade process. I don't remember ever seeing the alert that the New Ubuntu release 11.04 is available. The book says all you need to do is click on the upgrade button to start the process. I opened the Upgrade manager but there is no Upgrade button. I installed the updates anyway but I am still in 10.04.
What is the difference (if any) between an update and an upgrade?
Do I need to get a new CD for version 11.04 in order to do the update/upgrade?:confused:

PaddyJoe

---

### Post by Cookieh on 2012-01-04
not used to older versions of ubuntu but try this first...
In terminal write:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get update
sudo apt-get upgrade -y

If this doesnt work then just download it and burn it on a disc..

---

### Post by snowpine on 2012-01-04
Hi paddyjoe, your question is answered in detail on the Ubuntu website:

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by grahammechanical on 2012-01-04
An updated version of Ubuntu is released every six months. Each Ubuntu release comes with a minimum of 18 months support for security fixes and other stuff.

To give business owners some assurance of continued support some Ubuntu releases are designated Long Term Support (LTS). The gap between designated LTS releases at the moment is 2 years. Ubuntu 10.04 is such an LTS release. For your desktop version you have 3 years support. The server edition has 5 years support.

Why am I telling you this? You can set Update Manager to inform you of the next release or the next Long Term support release. If Update Manager is set to only notify you of the next LTS release then it just will not offer you the button to upgrade to 10.10 but only to 12.04 which is the next designated LTS release and it will not be released until April 1204. Therefore you will not get the button to upgrade to 12.04 until the last week of April 1204.

If you wish to upgrade you need to open Update Manager and look for Settings or find something called Software Sources. I cannot explain in detail how to do this as I stopped using 10.04 years ago.

Once you have the utility loaded open the Updates tab and look for the drop-down menu called Notify me of a new Ubuntu release version (or something like that) and change it from For Long Term Support Versions to For any new Version.

And see what happens. You just might see a button giving you an option to upgrade to 10.10. Once you have upgraded to 10.10 you will immediately get an option to upgrade to 11.04 and from there you can get to 11.10.

Provided that you are on-line at that time.

That is how it works.

Regards.

---

### Post by paddyjoe on 2012-01-05
> **snowpine said:**
> Hi paddyjoe, your question is answered in detail on the Ubuntu website:

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
graham,

Many thanks for your very useful pointer. I am working on it.

PaddyJoe
Athlone
Ireland

---

### Post by paddyjoe on 2012-01-05
> **grahammechanical said:**
> An updated version of Ubuntu is released every six months. Each Ubuntu release comes with a minimum of 18 months support for security fixes and other stuff.

To give business owners some assurance of continued support some Ubuntu releases are designated Long Term Support (LTS). The gap between designated LTS releases at the moment is 2 years. Ubuntu 10.04 is such an LTS release. For your desktop version you have 3 years support. The server edition has 5 years support.

Why am I telling you this? You can set Update Manager to inform you of the next release or the next Long Term support release. If Update Manager is set to only notify you of the next LTS release then it just will not offer you the button to upgrade to 10.10 but only to 12.04 which is the next designated LTS release and it will not be released until April 1204. Therefore you will not get the button to upgrade to 12.04 until the last week of April 1204.

If you wish to upgrade you need to open Update Manager and look for Settings or find something called Software Sources. I cannot explain in detail how to do this as I stopped using 10.04 years ago.

Once you have the utility loaded open the Updates tab and look for the drop-down menu called Notify me of a new Ubuntu release version (or something like that) and change it from For Long Term Support Versions to For any new Version.

And see what happens. You just might see a button giving you an option to upgrade to 10.10. Once you have upgraded to 10.10 you will immediately get an option to upgrade to 11.04 and from there you can get to 11.10.

Provided that you are on-line at that time.

That is how it works.

Regards.
grahmmechanical,

Many thanks for your clear explanation.  I am working on it.

PaddyJoe
Athlone
Ireland

---

### Post by paddyjoe on 2012-01-05
> **snowpine said:**
> Hi paddyjoe, your question is answered in detail on the Ubuntu website:

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
Snowpine,
Sorry I got your name wrong in my previous post. I got mixed up with another poster!

PaddyJoe

---

### Post by mastablasta on 2012-01-05
but oyu shoul dknow that upgrades can go wrong. and that you need to disable any PPA's you mgith have and remove any proprietary drivers before upgrade.
 
it is also best to download new version first and give it a try via live session, to see if and how well it works. 
 
Also note that 11.04 and 11.10 are very different from 10.04 as they include a new Unity interface that is hardware accelerated by default (means a weak GPU might have issues with default). If you are interested in Unity it is best to use the latest version where Unity is a bit more polished.

---

### Post by paddyjoe on 2012-01-05
> **Cookieh said:**
> not used to older versions of ubuntu but try this first...
In terminal write:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get update
sudo apt-get upgrade -y

If this doesnt work then just download it and burn it on a disc..
Cookieh,
Thanks very much for your help. I am a newbie in Ubuntu and am not (yet!) familiar with the use of the terminal. I will try using the other responses in this thread.
Anyhow, I appreciate your reply and your interest.
I may get back to using your method on the terminal when I get a bit more experience.

Paddyjoe
Athlone
Ireland

---

### Post by paddyjoe on 2012-01-09
> **mastablasta said:**
> but oyu shoul dknow that upgrades can go wrong. and that you need to disable any PPA's you mgith have and remove any proprietary drivers before upgrade.
 
it is also best to download new version first and give it a try via live session, to see if and how well it works. 
 
Also note that 11.04 and 11.10 are very different from 10.04 as they include a new Unity interface that is hardware accelerated by default (means a weak GPU might have issues with default). If you are interested in Unity it is best to use the latest version where Unity is a bit more polished.
Mastablasta,
Thanks for your advice. 
Unity does not work for me although I am now on 11.04. Obviously my graphics card  is not up to it. Do you have any suggestions for replacing the graphics card?

Thanks,

PaddyJoe
Athlone 
Ireland

---

### Post by dino99 on 2012-01-09
which graphic card is installed ?

into a terminal:
sudo rm /etc/X11/xorg.conf
sudo dpkg-reconfigure -phigh -a
 (can take a while, dont stop it before it ended itself)

then:

sudo reboot

---

