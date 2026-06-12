---
title: "Ubuntu 10.04 Alpha To Beta 1 Update Problem"
date: 2010-03-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tomcatjosh on 2010-03-18
Hello All, I was trying to upgrade to Ubuntu 10.04 From Alpha 3 To Beta 1, by doing the "update-manager -d" Thingy (I know, w/o quotation Marks) But It is just going to the normal upgrader, no "New Release" Message.. Can anyone please help?

Thanks,
Josh

---

### Post by Fred the Penguin on 2010-03-18
I had the same problem.  I just noticed a post that the beta1 release is delayed till tomorrow. It should work then.

---

### Post by tomcatjosh on 2010-03-18
oh, opps, lol. well, i guess something didnt go as plan. Guess its better to delay than for my computer to delay.. thanks :)
Let's Hope Its Good :D

---

### Post by ~Las~ on 2010-03-18
Are you sure about need to runupdate-manager -d?I think running normal updates (Synaptic or apt-update / apt upgrade) takes you all the way from alphas to final product...

---

### Post by Fersure on 2010-03-18
> **~Las~ said:**
> Are you sure about need to runupdate-manager -d?I think running normal updates (Synaptic or apt-update / apt upgrade) takes you all the way from alphas to final product...

Quite. You don't need to update Ubuntu that way until the next development release (10.10).

Just getting the normal updates via update manager should upgrade you to Beta1.

Regards, David.

---

### Post by tomcatjosh on 2010-03-19
Wait, so the normal Update Manager will take me straight into Ubuntu 10.04 beta 1, no need for a "Clean" Upgrade?

---

### Post by oldos2er on 2010-03-19
> **tomcatjosh said:**
> Wait, so the normal Update Manager will take me straight into Ubuntu 10.04 beta 1, no need for a "Clean" Upgrade?

Assuming you already have 10.04 installed, yes.

---

### Post by markbuntu on 2010-03-19
Using the regular update manager will take you all the way to the release and beyond. Unless you are testing the installers there is no need to upgrade or reinstall if you are running alpha, just get the regular updates. You will get no updates around the time of the Beta due to a package freeze.

Beta is just all the packages with their most recent updates, a sort of check point in the release schedule where packages have become mostly stabilized and no big heartbreaks are expected. In general the release of Beta is an invitation to a wider audience for more hardware and upgrade testing to report/squash bugs before the final release.

For sure there more people jumping in here, my torrents are seeding way more than with the alphas. (18GB up in two hours with ~300 other seeders just for the 386 and 64 desktops)

---

### Post by tomcatjosh on 2010-03-19
Alright, Thank You All :D

---

### Post by zulli1942 on 2010-03-20
I upgraded, but I have no taskbar so far in 10.04 Beta 1, just the desktop. Aptitude says I need to install ubuntu-desktop. I go to install it and it doesn't install. So I don't have a working box here.

---

### Post by Sef on 2010-03-20
Moved to Lucid.

---

### Post by alienexplorers on 2010-03-20
Updated from Alpha3 to Beta1 and ran all updates and system still functions normally.  Don't know why everybody is having problems.

---

### Post by Gadgetech on 2010-03-20
> **zulli1942 said:**
> I upgraded, but I have no taskbar so far in 10.04 Beta 1, just the desktop. Aptitude says I need to install ubuntu-desktop. I go to install it and it doesn't install. So I don't have a working box here.

I'm having the same problem in my virtual machine. I've booted into recovery mode and selected "dpkg fix broken packages" and it's downloading a bunch more updates. Hopefully this works. I was unable to [Alt]+[F2] or [Ctrl]+[Alt]+[F2] to get to a terminal.

Just finished the updates. Still no joy.

---

### Post by Gadgetech on 2010-03-20
Tried deleting .gconf, .gnome2, etc. Still no luck. Off to do a fresh install with the new iso.

Edit: Just saw the sticky on the front page - [http://ubuntuforums.org/showthread.php?t=1434160](http://ubuntuforums.org/showthread.php?t=1434160)
DON'T UPDATE!

---

### Post by zulli1942 on 2010-03-20
I am on my 2nd fresh install, I haven't done the updates after the install, due to last nights no taskbar problem. I ended up going into bash and trying to update to no avail. I was doing the 'aptitude full-upgrade -y' update, apparently 10.04 was angry with itself and decided not to cooperate :-). I saw that others had tried to remove some gnome files, ill try to update again and see what happens, and then see of some of the fixes i find in here work. FYI - I am installing 64 bit alternate install, I have the home directory on a software raid array (raid 0). / , /boot, and swap are separate partitions, on a separate drive. I have a dual core 5200 intel chip on an nvidia board. Alpha 2 and 3 were running fine.

---

