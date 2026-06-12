---
title: "Display problem when installing NVIDIA drivers on ubuntu 14.04"
date: 2014-11-07
forum: Installation &amp; Upgrades
---

### Post by christos5 on 2014-11-07
[SIZE=3]_Back story_[/SIZE]:
I have **ubuntu 14.04** installed on my laptop and I had also installed the NVIDIA  with CUDA 6.0. After an update a few days ago, I reboot ubuntu and then, when I logged in I noticed that there was no side bar and menus on the top. In addition the resolution was changed and I could not do anything. I enter the tty1 and then uninstalled the NVIDIA drivers with: 
```

sudo apt-get remover --purge nvidia*

``` 
After rebooting the system was running again and the display was ok, but I was using the Nouveau driver. In addition, there were **5 dialog boxes about errors that occurred **asking me whether I want to report them or not (of course I reported them).

[SIZE=3]_Problem_:[/SIZE]
For my work, I need to install **NVIDIA drivers and CUDA** (version 6.0 or 6.5) for my **NVIDIA GT540M** graphics card, but whatever I do, after installing the NVIDIA driver and then rebooting, the system starts into the same situation (changed resolution, no side bar, no menu, and the only possible action is to start a tty - [FONT=courier new]Ctrl[/FONT] + Al[FONT=courier new]t[/FONT] + [FONT=courier new]F1[/FONT]). I am thinking that maybe a package that was updated might cause that problem. 


[SIZE=3]_Information_[/SIZE]:
Here are the** packages that were updated** before the initial problem happend:

[IMG]http://i.imgur.com/BctwX5L.jpg[/IMG]


Here are the **drivers that I tried to uninstall and then install or re-install**, (but after rebooting the system resulted always in the same situation):

[IMG]http://i.imgur.com/31Bduwd.jpg[/IMG]

After installing NVIDIA 340.29 and then rebooting, I go to tty1 to uninstall the driver, and before I do anything, the terminal has this information already written:
```

* Starting NVIDIA Persistenced Daemon                  [OK]
* Stopping NVIDIA PRIME Power Saving Mode              [OK]
* Starting NVIDIA Persistenced Daemon                 [fail]
* Starting LightDM Display Manager                     [OK]
* Stopping Send an event to indicate plymouth is up    [OK]

```

Is it possible that the installation of another package may have caused this problem? Can I uninstall the update of some package that might caused the problem? Or will a clean (re)install of ubuntu 14.04 solve the problem? What are my options here?

Thank you in advance! It might be a hard to counter problem but I really need to have ubuntu + NVIDIA + CUDA for my work!

---

### Post by christos5 on 2014-11-11
I have just installed the following updates and then tried to install the nvidia-340 driver. Even though it did not work again, it did not show any errors when I am logging in. Sadly, the problem remains; no interaction with the ubuntu and nor the icons neither the menus are shown on the screen.

In the new packages installed, there was one mentioning firmware updates and another one mentioning some "hardware updates".

Any idea whether my problem might be fixed soon or whether I should do something else? My problem is that there are no error shown, and I cannot "report" anything, even though the system is not working as it was supposed to work.

---

