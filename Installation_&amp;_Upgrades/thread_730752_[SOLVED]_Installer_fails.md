---
title: "[SOLVED] Installer fails"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by stalkingwolf on 2008-03-21
Yesterday I tried to upgrade my Landlords computer ( 7.04 > 7.10) .  It downloaded
all the updates/upgrades then I got an error message " installer failed to load".

How can I fix this?  Appearantly all I need to do is install the packages that were downloaded.

---

### Post by stalkingwolf on 2008-03-22
anyone?

---

### Post by banewman on 2008-03-22
What did you do to try and upgrade?

---

### Post by stalkingwolf on 2008-03-22
clicked the UPGRADE TO 7.10 button at the top of the update manager.

I had just finished installing this new computer.  I got the notice that updates were available.
opened the update manager , then decided to upgrade him to 7.10.  Clicked the upgrade to
7.10 button, it downloaded the necessary packages.  Then could not install them. Got Installer failed.

---

### Post by banewman on 2008-03-22
My guess is that 7.04 has had a lot of updates and a dependency isn't being met.
Can you boot into it at all?
If so in a terminal type -
sudo apt-get update && sudo apt-get upgrade
If you can't boot can you boot into the recovery kernel- the second option at the boot prompt?

---

### Post by stalkingwolf on 2008-03-22
I will try this later today. I have to leave for work now.

sudo apt-get update && sudo apt-get upgrade

should this be one line or two?

sudo apt-get update 
sudo apt-get upgrade

---

### Post by banewman on 2008-03-22
The && is so it will be one command instead of waiting for the updates to happen then typing the next command.
:)

---

### Post by black3ug on 2008-03-22
I'd say you're better off making a clean install. The accumulated stuff installed in your old setup is bound to cause some sort of conflict with your upgrade. Just backup your important files. 

It's also a good idea to create a different *Home* partition so that you don't have to keep on copying files to other devices every time you need to do a clean install. This is something which I recently learned, :lolflag:.

---

### Post by stalkingwolf on 2008-04-02
yep that is what I finally had to do.  reinstalled and off he went.

---

