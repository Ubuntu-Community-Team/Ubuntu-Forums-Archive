---
title: "Ubuntu 9.10 - karmic koala + HP DV6700 = Blackscreen"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by biscoito1r on 2009-10-13
I updated my HP DV6700 laptop to 9.10 from the 9.04 version, after the update I got the evil black screen, is there any hope ?

---

### Post by garvinrick4 on 2009-10-14
If you are going into an unstable version that is still in beta I would download a .iso
to desktop and then burn it to cd so it will take as short as time as possible to reinstall
and getting GUI inshape with repositorys and keys included down to as quick a time as
you can get it. Sometimes a fresh install is just best. Testing is OK if you got time and if
you are doing or going to do daily upgrades expect the worse soon as you think it is fantastic. It is interesting to use your forums and google including launchpad to try to fix
the problems but sometimes just reinstall latest version. Do not get an .iso of Jaunty if you want to test Karmic beta just takes way to long to do upgrade from dist.
 Just have fun with it. You will make a quick learning curve to say the least. USE YOUR FORUMS  there are nice folk out their who want to help you and no question is a dumb question.

---

### Post by biscoito1r on 2009-10-14
[garvinrick4]("http://ubuntuforums.org/member.php?u=899097")
Thanks for the tip chief.
Is there anything that can be done regarding the blackscreen ? The Ubuntu logo loads and then all I see is the evil black screen :(.

---

### Post by Havage on 2009-10-14
Hey, I had a similar problem with this using the NVidia 185 driver on a fresh install of 9.10.

Check this thread:
[http://ubuntuforums.org/showthread.php?t=1290656&page=2]("http://ubuntuforums.org/showthread.php?t=1290656&page=2")

The fix for me was to boot using a live CD, and mount the HDD then sudo gedit the xorg.conf file in the etc/X11 directory and change the driver name to "nv".

Hope this helps.

---

### Post by biscoito1r on 2009-10-14
Thanks, it worked :)

---

