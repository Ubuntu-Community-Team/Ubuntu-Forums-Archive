---
title: "Upgrade from Breezy to 6.10"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by ExemplarUbuntu on 2007-02-28
I would like to upgrade from Breezy to 6.10. When I start Update Manager it offers an easy way to upgrade. I've had lots of problems upgrading Ubuntu in the past so I am not expecting this to be any easier.

The box is a VIA mini-ITX unit.

I started the Update and it began but failed saying I should report the bug in "Update Manager" and referred to the files in /var/log/dist-upgrade.  The release notes directed me to a page in LaunchPad that doesn't exist so I am reporting it here.

There are 3, apt.log, main.log and term.log which is empty, the other two are quite large.

EDIT:
[
main ends with:

2007-02-28 11:12:08,591 DEBUG Installing 'hpijs' (hpijs quirk upgrade rule)
2007-02-28 11:12:08,704 DEBUG no {ubuntu,edubuntu,kubuntu}-desktop pkg installed2007-02-28 11:12:08,705 DEBUG guessing 'ubuntu-desktop' as missing meta-pkg
2007-02-28 11:12:09,397 DEBUG The package 'linux-image-2.6.10-5-386' is marked for removal but it's in the removal blacklist
2007-02-28 11:12:17,985 ERROR Dist-upgrade failed: 'An essential package would have to be removed'
]

I could do the update manually but if the Update Manager can't do it then I am worried it will break the system again and leave me with another weeks work trying to get it to boot again.

The 2.6.10 kernel is the only one that will currently boot there are two newer ones don't boot.

---

### Post by mikewhatever on 2007-02-28
Can you skip a release and upgrade from Breezy to Edgy? I think you have to upgrade to Dapper fist and only then to Edgy.

---

### Post by ExemplarUbuntu on 2007-02-28
I assumed from the banner heading urging me to do the upgrade that it was safe to do it.

---

### Post by Thiesen on 2007-02-28
You can't skip releases. You have to update to the next following release.
 
Ie Warty > Breezy > Dapper > Edgy > Future Feisty.
 
I know I have seen something about it but I don't know where I saw it. It might have been on the wiki though.

---

### Post by ExemplarUbuntu on 2007-02-28
Thanks.

I will modify sources.list to user Dapper and go through that route.

---

