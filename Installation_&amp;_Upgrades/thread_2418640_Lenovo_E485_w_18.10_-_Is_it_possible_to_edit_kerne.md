---
title: "Lenovo E485 w/ 18.10 - Is it possible to edit kernel on USB before installation?"
date: 2019-05-09
forum: Installation &amp; Upgrades
---

### Post by RockOut on 2019-05-09
I am interested in installing Ubuntu 18.10 onto my Lenovo E485.

I found this article explaining how to do so: [https://medium.com/@jthegedus/ubuntu-18-04-lts-on-lenovo-thinkpad-e485-15e1d601473f](https://medium.com/@jthegedus/ubuntu-18-04-lts-on-lenovo-thinkpad-e485-15e1d601473f)

However, if this is a known issue... is it at all possible I can make these changes IN THE CODE ON THE USB STICK **BEFORE **I begin installation?

If anyone at all has any insight on this I would be very excited.

---

### Post by mikewhatever on 2019-05-09
It's possible, but why do you write in all caps ...?

---

### Post by RockOut on 2019-05-09
If its possible, *how *do I accomplish this?

I posted elsewhere but folks misunderstood the order of code editing/installation I am hoping to achieve. 

I want to edit the code BEFORE loading 18.10 onto a USB stick for installation. All caps and **bold **text emphasize the order in which things, I hope, should occur.

---

### Post by cruzer001 on 2019-05-09
So you want to create your own customize .iso?

Since I have not done this lately, I cannot recommend any particular software.  There are several ways to do this.  Do a browser search on "*create build custom iso ubuntu linux*" and see if this is what your after.

---

### Post by mikewhatever on 2019-05-09
I think creating a custom iso is a huje overkill for what you want, which is boot from the installation media once, add some boot options, and install Ubuntu. It might take, ...don't know how long to accomplish the task, not to mention, that most howtos assume you already have an installed Linux distro somewhere, and will use it to follow instructions. Anyway, since there is no other way, here is a howto: [https://help.ubuntu.com/community/InstallCDCustomization#Modify_installer_behaviour_using_a_Preseed_file](https://help.ubuntu.com/community/InstallCDCustomization#Modify_installer_behaviour_using_a_Preseed_file). Good luck.

PS: I've not used any caps or bold, hope you can understand it ok.

---

### Post by mörgæs on 2019-05-09
Have you tried installing 19.04? Do you know if the boot options are still necessary?

---

### Post by cruzer001 on 2019-05-09
Hi  mörgæs

Found this

Tested kernel versions: 4.15, 4.19, 5.0, 5.1-rc7

[https://bugzilla.kernel.org/show_bug.cgi?id=203519](https://bugzilla.kernel.org/show_bug.cgi?id=203519)

---

### Post by RockOut on 2019-05-09
lol,thanks.

i have  new laptop with Windows 10 pre-installed, and i desperately want it off of it. i also have a desktop with ubuntu 18.04 running.

i'll take a stab at that tutorial and see if I can get a smooth install.

---

