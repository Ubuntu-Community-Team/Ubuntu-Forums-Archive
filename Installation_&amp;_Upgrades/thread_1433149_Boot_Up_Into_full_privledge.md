---
title: "Boot Up Into full privledge"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by slowhands36 on 2010-03-18
is there a way to set ubuntu to were it boots up into full root access to everything.Iam only user and want to be able to mount other drives and stuff after bootup.

---

### Post by phillw on 2010-03-18
> **slowhands36 said:**
> is there a way to set ubuntu to were it boots up into full root access to everything.Iam only user and want to be able to mount other drives and stuff after bootup.

Hi and welcome to the forums,

you can get drives to auto-mount on boot up (by far the easiest way of doing things) using Storage Device Manager (it's under the system tab, either Administration [I'm pretty sure] or Preferences)

As for the run as root, head over here and see why it isn't done --> [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

It does take a while to get used to, but I fully understand and endorse the reasoning.

As a little helper (if it's not mentioned there), when you issue something like
```
 apt-get this_horrendously_long_list_of_programmes
```

and it says 'permission denied' - instead of putting a brick through the screen, take a breath and simply type
```
sudo !!
```

That will cause the last line to be re-issued, with sudo at the start of it :p

(I spend 1/2 my life issuing sudo !!)

Regards,

Phill.

---

