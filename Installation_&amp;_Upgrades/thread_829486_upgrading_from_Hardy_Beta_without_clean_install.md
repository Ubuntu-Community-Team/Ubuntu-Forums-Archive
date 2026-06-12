---
title: "upgrading from Hardy Beta without clean install"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by BetterSense on 2008-06-14
I have a virtualbox installed on a machine that is still running an old Beta version of Hardy. It has 600 some available updates! I would just do a clean install with a disk, because it doesn't take very long, but I don't want to lose my virtualbox. 

If I do a clean install (leaving home directory intact), could I possibly just reinstall virtualbox and have my virtual machine stay intact (hopefully the imporant stuff is stored in /home)?

If a clean install will splode my virtualbox, will apt-get upgrade bring me up to date with the current Hardy, or is the stable release effectively a new 'version' and I have to do something else (as if I was upgrading from Gutsy to Hardy)?

What are the chances of my computer sploding?:)

---

### Post by Partyboi2 on 2008-06-14
> If a clean install will splode my virtualbox, will apt-get upgrade bring me up to date with the current Hardy, or is the stable release effectively a new 'version' and I have to do something else (as if I was upgrading from Gutsy to Hardy)?
Yes, all you would need to do is upgrade as you are currently running hardy release, just out of date with updates.
Backing up your virtualbox you could try [[COLOR=Blue]this[/COLOR]]("http://www.derekhildreth.com/blog/how-to-properly-backup-a-virtualbox-machine-vdi/")

---

### Post by BetterSense on 2008-06-14
Thanks, I will probably try to run apt-get upgrade. If that fails and I have to do clean install anyway, well I didn't lose anything but time.

That VirtualBox backup thing made it sound like all the virual machine stuff lives in .Virtualbox/ . If that's the case than is it true a virtual machine can survive a clean install?

---

