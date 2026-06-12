---
title: "Network menu item missing"
date: 2008-07-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Gina on 2008-07-13
I have just installed Intrepid Alpha 2 on my AMD64 desktop and installed the nVidia driver.  I've also installed the updates using Update Manager.  I then went to set up the wireless but there was no **Network** menu item in the **System > Administration** menu.  I tried the menu editor and there's no **Network** menu item there to enable.  

There seems nowhere else in the GUI to set up wireless so I used **sudo iwconfig** from the command line which worked until a reboot.  The setting had then reverted to the default (no essid set and wrong channel etc.) and I had to use iwconfig to set it again.  Fortunately the Terminal history meant I didn't need to type it all in again.

Anyone else found this? - not seen it mentioned.

---

### Post by ronacc on 2008-07-13
you are right , no network menu entry ! I did notice that network tools shows my wireless as configured and active ( I also have a wired connection on that box) so the upgrade picked up the previous settings .

---

### Post by klange on 2008-07-13
I can also confirm that the menu item is missing, which had me freaking out a bit as my wireless *wasn't* working.

---

### Post by wilbur.harvey on 2008-07-14
True, no network menu item.

The network manager seems to be finding my wired network ok.

If I don't have network manager installed, and hard code a fixed IP address in the interfaces file, the values in resolv.conf always get reset every time I boot.

---

### Post by Nullack on 2008-07-14
Has someone bugged it yet. Can I say it would be better for all us enthusiasts if we make a conscious act in our posts to clarify if its been bugged or not yet.

---

### Post by plun on 2008-07-14
It is..  triaged and a rank.

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/248163](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/248163)

---

### Post by Gina on 2008-07-14
Funny...  I posted here that I had reported the bug in Launchpad but my post has disappeared (from here).  Fortunately my LP post stayed and has been acted upon as has been said.  Ranked as of High importance.

---

### Post by xebian on 2008-07-14
> **Gina said:**
> Funny...  I posted here that I had reported the bug in Launchpad but my post has disappeared (from here).  Fortunately my LP post stayed and has been acted upon as has been said.  Ranked as of High importance.

Is this just a missing menu item, or the applet itself is missing?

---

### Post by tim1 on 2008-07-14
You probably haven't installed the gnome-network-admin package.

---

### Post by xebian on 2008-07-14
> **tim1 said:**
> You probably haven't installed the gnome-network-admin package.

You mean to install it manually?   Shouldn't it be part of the distro release?  OR is it part of the gnome policy of taking away all the user config from the user?

---

### Post by tim1 on 2008-07-14
This is the development release. They probably just didn't update the meta packages yet, calm down.

---

### Post by Gina on 2008-07-14
The bug has been given a high priority so I expect to see it fixed pretty quickly.  Breakages are expected during development.

---

### Post by cariboo on 2008-07-14
Has anyone else noticed that the network icon in the top panel flickers annoyingly. it seems to flicker for no reason. I though it might have something to do network activity, but it does it when I don't have any network apps open.

Jim

---

### Post by Gina on 2008-07-14
Tim Fuchs has posted in Launchpad > You have to install the gnome-network-admin package.
  Following that the bug has been demoted to Wishlist.  Of course, the package should be installed by default hence Wishlist rather than fixed.  I'm waiting to see if there is any response to that as I personally feel this is rather more important than "Wishlist" and will say so if nobody else does.

---

### Post by Nullack on 2008-07-14
So do I, wishlist is nonsense unless Intrepid has blueprints for another mechanism to configure networking.

---

### Post by olskar on 2008-07-14
Doesnt it have to do with the fact that they hope to switch to NM 7.0 in Intrepid?

---

### Post by Gina on 2008-07-15
Yes, I believe it does.  I guess the thought is that with a temporary fix posted it's not worth sorting it out ATM.

---

### Post by ruik on 2008-07-15
> **cariboo907 said:**
> Has anyone else noticed that the network icon in the top panel flickers annoyingly. it seems to flicker for no reason. I though it might have something to do network activity, but it does it when I don't have any network apps open.

Jim

Yeah, it flickers here too.

---

