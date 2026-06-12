---
title: "Unable to upgrade to Edgy from Dapper"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by LeighT on 2006-11-16
I am having trouble upgrading from Dapper to Edgy.
I have tried "gksu "update-manager -c"" and  gksu "sh /cdrom/cdromupgrade" using the alt inst CD.
Both return the error message "can't find DistUpgradeViewGtk" then exits.
Synaptic doesn't seem to know about this program.
Any ideas?](*,)

---

### Post by Jussi Kukkonen on 2006-11-16
It's a bug: [https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/66376](https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/66376)

Install python-vte to get by it:
```
sudo aptitude install python-vte
```
then try the upgrade again.

---

### Post by LeighT on 2006-11-16
> **Jussi Kukkonen said:**
> It's a bug: [https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/66376](https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/66376)

Install python-vte to get by it:
```
sudo aptitude install python-vte
```
then try the upgrade again.

Jussi
Thanks for the info, I thopught that it would be somthing like this, but didn't know what was required. 
Leigh

---

### Post by Skinn3r on 2006-11-26
I have python-vte installed and stilll the same error.

Any ideas?

---

### Post by bulldog on 2006-11-26
> **Skinn3r said:**
> I have python-vte installed and stilll the same error.

Any ideas?

I don't like the upgrade,it ruined my Dapper.
Just do a clean Edgy install if possible,it should be faster and more reliable.

If you have the space make a separate Edgy install to try things out.
If it runs well and you like it,you can always remove dapper and add space to your Edgy.
I do it this way and it's much safer if Edgy isn't doing well for you.
Just some advice though.

---

