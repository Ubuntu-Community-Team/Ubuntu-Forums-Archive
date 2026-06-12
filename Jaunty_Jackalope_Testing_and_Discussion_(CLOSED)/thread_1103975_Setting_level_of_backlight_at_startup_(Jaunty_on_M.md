---
title: "Setting level of backlight at startup (Jaunty on MacBookPro 5.2)"
date: 2009-03-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by valmar on 2009-03-23
Dear All,

       I am Valerio from Switzerland. I recently bought a macbook pro (model 5.2, I think) and following the instructions on the mactel pages, I was able to set up everything properly, except for a few things. 

In particular, I got the LCD backlighting and the keyboard backlighting working using the mbp_nvidia_bl and pomme drivers respectively. However, when I boot ubuntu (kubuntu, actually), the level of both backlightings is maximum, and especially the screen is very very bright. Of course once I log in I can change the levels manually using  gpomme

I was wondering, however, if there was a way of to set the level of backlighting automatically when the computer starts, maybe using a bash script that is executed at start up.

Thank you in advance for your help.

      Valerio

PS: I alse noticed that not all the drivers required for the touchpad to work are in the mactel repositories for jaunty yet. In particular usbhid is missing. Can someone please point me to a place when I can find the source code for the drivers, so I can compile them myself? Thank you again

---

### Post by cyberdork33 on 2009-03-23
> **valmar said:**
>  PS: I alse noticed that not all the drivers required for the touchpad to work are in the mactel repositories for jaunty yet. In particular usbhid is missing. Can someone please point me to a place when I can find the source code for the drivers, so I can compile them myself? Thank you again
you can get the code on the ppa page in launchpad.

the usbhid dependency should now be fixed though (usbhid isn't required in jaunty).

If you check this thread:
[http://ubuntuforums.org/showthread.php?t=977558](http://ubuntuforums.org/showthread.php?t=977558)
I think there is some discussion on getting the backlight to set to the last used level each time.

PS pommed should not be used anymore. It is depreciated.

---

### Post by valmar on 2009-03-23
Thanks!! 

I removed pommed and I followed the discussion in the thread. 

Here is the problem that I now have:

When the module mbp_nvidia_bl is loaded, I can change the brightness of the lcd only from the terminal by piping a value in the correct /sys/file. The function keys don't work.

I am using Kubuntu, so the power manager is likely to be powerdevil. Has someone been able to make it work? Or should I write some bash script and assign them to the function keys using keyboard bindings?

Thank you again. This is really helpful!

      Valerio

EDIT: I want to make this clearer. First, I discovered that I have a Mac 5.1, not a 5.2. Second: I am using Kubuntu with KDE 4.2.1. Third: the mbp_nvidia_bl and the applesmc drivers work perfectly. I have control of both the keyboard and screen backlights from the terminal using echo. I also have control of the lcd from the power managet icon in KDE system settings (using the sliders). It is only the F1, F2,etc. keys that are not working.

---

### Post by inphektion on 2009-03-23
After i installed mbp-nvidia-bl my lcd function keys worked fine.  I can't get the function keys working for the keyboard backlight still.
If you make any progress please update the wiki I've been trying to keep it current. 
[https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty)

edit: to be entirely accurate i installed  mbp-nvidia-bl-dkms  and nvidia-bl-dkms from the jaunty ppa and then the function keys for lcd backlight worked fine.

---

### Post by valmar on 2009-03-24
Hello! But you loaded both modules into the kernel at the same time? If you google on the forums, you find messages saying you should not do it!

      Valerio

---

### Post by buntuLo on 2009-03-24
> **valmar said:**
> I am using Kubuntu, so the power manager is likely to be powerdevil. Has someone been able to make it work?

Valerio, I'm running kde too (still 4.1 in here). i was exactly at your point, able to control both backlight levels through terminal and display backlight level with the sliders in the kde power manager. then i removed the kde manager (the correct name is guidance-power-manager) and installed the gnome-power-manager from the Mactel PPA and... voila', f-keys working for both display and keyboard backlight control! a big thanks to the Mactel guys :~)
let me know if it works for you, ciao, Lo.

---

### Post by cyberdork33 on 2009-03-24
> **buntuLo said:**
> Valerio, I'm running kde too (still 4.1 in here). i was exactly at your point, able to control both backlight levels through terminal and display backlight level with the sliders in the kde power manager. then i removed the kde manager (the correct name is guidance-power-manager) and installed the gnome-power-manager from the Mactel PPA and... voila', f-keys working for both display and keyboard backlight control! a big thanks to the Mactel guys :~)
let me know if it works for you, ciao, Lo.
this probably needs fixed in the kde power manager application (or removed from gnome-power-manager and put somewhere different... ) I would file a bug. The Mactel-Support packages target the regular Ubuntu release only.

---

### Post by buntuLo on 2009-03-24
> **cyberdork33 said:**
> this probably needs fixed in the kde power manager application
in this case the bug should be filed against the kde application guidance-power-manager.
> **cyberdork33 said:**
> or removed from gnome-power-manager and put somewhere different...
while in this case i don't know.
what do you suggest me? greetings, Lo.

btw, if in the meantime Valerio confirms that the gnome manager works for him too, i can update the wiki page to help other kde users till the issue is not fixed.

---

### Post by inphektion on 2009-03-24
how did you install gnome-power-manager for jaunty?  
did you just install the intrepid .deb or did you add the intrepid repo to sources.list as well?

---

### Post by buntuLo on 2009-03-24
sorry for the misunderstanding, i run kde on intrepid, as in my signature.
it is the only jaunty package still missing in the ppa: do we just have to wait or are there specific problems with it of which i'm not aware?

---

### Post by cyberdork33 on 2009-03-24
> **inphektion said:**
> how did you install gnome-power-manager for jaunty?  
did you just install the intrepid .deb or did you add the intrepid repo to sources.list as well?
it's the mactel ppa.

EDIT: I will check on this.

---

### Post by valmar on 2009-03-25
Dear All! I am back here/

I tried what was suggested, but it only partially worked.

Let me explain. I din not have to uninstall the guidance power manager, as it was not installed. I installed the Intrepid deb package from the Mactel PPA as there is no package for Jaunty.

However, I have a proglem. When I launch the gnome-power-manager, an icon quickly flashes in the system tray, then it is gone. I think it is crashing.

Let me put forward a theory, however: KDE 4.2 has an internal power manager. It is in the System Settings panel. This is what I use to control the backlight with the sliders. When gnome-power-manager crashes, I can still control the backlight with this manager. I think that the KDE power manager might not be letting the gnome one take control.

Somehow, I once crashed the KDE power manager. And then the gnome one started and the keys were working. This would support my theory. But I don't know how that happened!

I am curious how other dealt with this problem.

            Valerio

PS. Only the lcd backlight keys work, not the keyboard ones. Is there a way to make them work? With pomme they were working. what is there of wrong in using it? Why is it deprecated?

---

### Post by inphektion on 2009-03-25
I'm hoping we just need gnome-power-manager built for jaunty, then problem solved.

---

### Post by cyberdork33 on 2009-03-25
> **inphektion said:**
> I'm hoping we just need gnome-power-manager built for jaunty, then problem solved.
well it may be that the gnome-power-manager in Jaunty already has the patches... I am still waiting for a reply about it.

pommed is depreciated because the functionality that pommed enabled has been added to the base packages that control the hardware (Linux kernel, hal, etc). running pommed in addition to this only leads to conflicts. 

If you can get everything working the way you want with pommed, then go for it, but If there are issues, it would be best to fix the packages that are taking over, rather than find workarounds for a depreciated piece of software.

---

### Post by valmar on 2009-03-26
Yes, I agree, I did not want to appear aggrssive with that comment about pommed. Anyway, I think we must find a way to disable powerdevil. I can do it in the following wa, but it is just a proof of concept.

1) Install guidance-power-manager.

2) This (I think) takes control over powerdevil

3) Close guidance

4) Launch gnome-power-manager

Anyone knowns if the keyboard backlight is supposed to work with the gnome power manager?

                 Valerio

---

### Post by inphektion on 2009-03-26
> **cyberdork33 said:**
> well it may be that the gnome-power-manager in Jaunty already has the patches... I am still waiting for a reply about it.


Well from what I can tell in intrepid, if you installed the mbp-nvidia-bl, and then the gnome-power-manager, both keyboard and screen backlights were controllable via the Fn buttons.  In jaunty just the screen works.  So I'm going to assume that the gnome power manager as it currently stands in jaunty doesn't have all the patches it might need.

---

### Post by buntuLo on 2009-03-26
> **valmar said:**
> I can do it in the following wa, but it is just a proof of concept.
1) Install guidance-power-manager.
2) This (I think) takes control over powerdevil
3) Close guidance
4) Launch gnome-power-manager

Valerio, i guess you already tried removing the package with apt-get, didn't you?
anyway, might the keyboard backlight control fault be caused by the intrepid/jaunty mix?

---

### Post by _mario_ on 2009-03-27
> **valmar said:**
> 
Anyone knowns if the keyboard backlight is supposed to work with the gnome power manager?

```

# apt-cache policy gnome-power-manager
  Installed: 2.24.2-2ubuntu7
  Candidate: 2.24.2-2ubuntu7
  Version table:
 *** 2.24.2-2ubuntu7 0
        500 http://de.archive.ubuntu.com jaunty/main Packages
        100 /var/lib/dpkg/status
     2.24.0-1mactel4 0
        500 http://ppa.launchpad.net intrepid/main Packages

```

even if adding the intrepid PPA sources line, apt will still install the jaunty version because it is newer. and i can confirm the jaunty version doesn't really support changing keyboard backlight (the notification icon appears without scale and nothing happens). display backlight does work running GNOME.

ciao,
Mario

---

