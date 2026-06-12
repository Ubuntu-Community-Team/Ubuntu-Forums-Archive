---
title: "Strange suspend problem"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by erbedo on 2006-06-01
Hi all
     just upgrade to dapper and it's great! But i have a problem with suspend. Suspend mode: if i click on the panel to suspend, it works. But if i move down the lid it doesn't work and gave me blankscreen.

---

### Post by pellgarlic on 2006-06-07
hi - as issues with laptop "hibernation" vary from device to device, the best place to start looking for an answer is here: 

[https://wiki.ubuntu.com/LaptopTestingTeam/](https://wiki.ubuntu.com/LaptopTestingTeam/)

look for the make and model of your laptop - there are individual pages for each one. as far as i can remember, making modifications to what happens when you close the laptop lid involves editing a file called "lid.sh", although i'm not sure where that file is located, or what changes need to be made. perhaps a quick google for "lid.sh" and your laptop model will provide results?

---

### Post by erbedo on 2006-06-08
[QUOTE=pellgarlic]hi - as issues with laptop "hibernation" vary from device to device, the best place to start looking for an answer is here: 

[https://wiki.ubuntu.com/LaptopTestingTeam/](https://wiki.ubuntu.com/LaptopTestingTeam/)

look for the make and model of your laptop - there are individual pages for each one. as far as i can remember, making modifications to what happens when you close the laptop lid involves editing a file called "lid.sh", although i'm not sure where that file is located, or what changes need to be made. perhaps a quick google for "lid.sh" and your laptop model will provide results?[/QUOTE]

Sorry but on that page there isn't my notebook. And also searching lid.sh fj3s on google provide no results :(

---

### Post by pellgarlic on 2006-06-08
ok, the file that contains the actions to perform when closing and opening the laptop lid is this one: /etc/acpi/lid.sh you could have a look in that to see if anything presents itself.

also, i'm pretty sure there are still problems with the built-in hibernate/suspend feature in ubuntu - at least, the one in breezy didn't work flawlessly (it would appear to suspend ok, but would not start up again properly), so many people installed "suspend2", which worked better. it may be that the same problem still exists in dapper.

you could try that and see if it makes a difference. i think you'll probably have to do a bit setting up as well (make the "close lid" default to suspend2 instead of the built-in suspend, and so on). search these forums for "suspend2" - you'll get plenty of hits, and most of them will be people trying to sort out laptop hibernation issues.

---

### Post by ckgreenman on 2006-06-08
[QUOTE=erbedo]Hi all
     just upgrade to dapper and it's great! But i have a problem with suspend. Suspend mode: if i click on the panel to suspend, it works. But if i move down the lid it doesn't work and gave me blankscreen.[/QUOTE]


If your setup is any thing like mine, you'll probably have to do some fiddling in /etc/acpi.  All my default lid.sh does is fire up xscreensaver.  I had to rename lid.sh and copy sleep.sh to lid.sh.  Now the lid button works great.

Now if I can just figure out why the ALT button appears to be locked on after resume...

Hope this helps.

---

