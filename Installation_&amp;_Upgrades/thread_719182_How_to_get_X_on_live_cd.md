---
title: "How to get X on live cd?"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by popatopalous on 2008-03-08
I have an on board nVidia graphics card. Since Ubuntu went to live cd installers I have a terrible time installing. I want to install Hardy Heron x86_64. What do I add to boot options so I can have a xserver? I need for it to use vesa instead of nv.

---

### Post by Rocket2DMn on 2008-03-08
The LiveCD doesn't work for a lot of people because of exactly this reason.  You can still install with the alternate install disc which doesn't have a live session, just a text based installer.  It is intuitive, easy to use, and you can download it here by checking the box at the bottom for the alternate cd - [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by popatopalous on 2008-03-08
> **Rocket2DMn said:**
> The LiveCD doesn't work for a lot of people because of exactly this reason.  You can still install with the alternate install disc which doesn't have a live session, just a text based installer.  It is intuitive, easy to use, and you can download it here by checking the box at the bottom for the alternate cd - [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

I'm afraid in Hardy there is a more severe problem:

[http://kubuntuforums.net/forums/index.php?topic=3092158.0](http://kubuntuforums.net/forums/index.php?topic=3092158.0)

In Hardy xorg.conf is apparently quite different than Gutsy. As you will see in that post I have installed Hardy from alternate cd but I have no X and no easy way yet found to fix it. I think a bug report is in order. If an operating system detects a nvidia card it should by default configure the vesa driver NOT the nv driver as the nv driver doesn't work  for a LOT of us. Then the user can easily change to nv or nvidia driver at their desecration.

---

### Post by Rocket2DMn on 2008-03-08
Yeah, Hardy is using a newer version of X I think - remember that Hardy is still in alpha.  We can try again to uninstall any existing proprietary drivers and reinstall them:

```
sudo apt-get remove nvidia-glx nvidia-new-glx
sudo rm /lib/linux-restricted-modules/.nvidia_new_installed
```
^^ignore any file not found errors ^^

Then you can install the drivers from KDE (under vesa) following the directions here - [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) - using the 7.10 directions I suppose.

The alternate option is to try and install from nvidia's website.  I have directions on how to do that, but I don't know if they work under Hardy.  Let me know if you're interested in trying.

---

### Post by popatopalous on 2008-03-08
> **Rocket2DMn said:**
> Yeah, Hardy is using a newer version of X I think - remember that Hardy is still in alpha.  We can try again to uninstall any existing proprietary drivers and reinstall them:

```
sudo apt-get remove nvidia-glx nvidia-new-glx
sudo rm /lib/linux-restricted-modules/.nvidia_new_installed
```
^^ignore any file not found errors ^^

Then you can install the drivers from KDE (under vesa) following the directions here - [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) - using the 7.10 directions I suppose.

The alternate option is to try and install from nvidia's website.  I have directions on how to do that, but I don't know if they work under Hardy.  Let me know if you're interested in trying.

Ok. I have no X in Hardy. It does not recognize my monitor, mouse, or video card. I have no internet in Hardy. On my system the Hardy installer is installing an unusable system at this point. 

The question of this thread is not how to fix my existing install [from alternate cd] of Hardy. It is how can I get a xserver on live dc so I can reinstall using the desktop cd installer. This may be as easy as adding boot options to force the live cd to use vesa instead of nv driver. Does any one know what those boot options are? I have been Scroogle searching but haven't found what I'm looking for.

---

### Post by Rocket2DMn on 2008-03-08
I think the kernel option to add is "xforcevesa", but there should also be an option to boot into Safe Graphics Mode (you might have to hit F6) on the LiveCD.  Without internet however, it might prove tricky to install restricted drivers once you get the system installed.

If you aren't able to get that to work, you may need to go make a new post under the subforum that is specifically for Hardy Heron - [http://ubuntuforums.org/forumdisplay.php?f=305](http://ubuntuforums.org/forumdisplay.php?f=305)
You can navigate there from ubuntuforums.org by clicking the Development & Programming under the Other Community Discussions subheading, then proceeding to "Development (Hardy Heron)" (the 3rd option).
You should link them to this thread and your kubuntu forum post as well.

---

### Post by popatopalous on 2008-03-09
Yeah, that old fart popatopalous can be an idiot sometimes. On the Gutsy live cd Safe Graphics Mode is in the main menu. Now on the Hardy live cd it is hidden under F4 Modes. Problem solved.

---

