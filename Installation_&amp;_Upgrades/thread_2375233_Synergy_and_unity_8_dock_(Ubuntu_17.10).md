---
title: "Synergy and unity 8 dock (Ubuntu 17.10)"
date: 2017-10-23
forum: Installation &amp; Upgrades
---

### Post by evdbovenkamp on 2017-10-23
I just upgraded from Ubuntu 17.04 to 17.10 and I experience the following problems with Synergy;
[SIZE=1]*([COLOR=#545454][FONT=arial][COLOR=#6A6A6A]**Synergy**[/COLOR] by Symless is a type of KVM software for sharing one keyboard and mouse between multiple computers. It works on Linux, macOS and Windows.)[/FONT][/COLOR]*[/SIZE]

I have on the left side my W10 computer and on my right my Ubuntu 17.10 computer.
Normaly I can switch without any problems from/to my windows machine and back.
But since the upgrade to Ubuntu 17.10 (which includes Unity 8....) it is not possible anymore to switch.

When I move the mouse to the left, it just sticks. It does to move to the other screen anymore.
I found a solutions, by changing the config of Synery. Now Synergy thinks the windows computer is on the right (where there is no dock).

If there a way to solve this? So I can move my mouse to the left again...?

I will also post this problem on the forum with Symless.
[COLOR=#545454][FONT=arial]
[/FONT][/COLOR]

---

### Post by roundand on 2017-10-23
> **evdbovenkamp said:**
> 
[...] When I move the mouse to the left, it just sticks. It doesn't to move to the other screen anymore.
I found a solution, by changing the config of Synergy. [...][COLOR=#545454][FONT=arial]
[/FONT][/COLOR]

I have the same problem with the upgrade from Ubuntu 17.06 to 17.10 breaking my Synergy setup. Please could you share your solution, even if it doesn't do the complete job?

---

### Post by roundand on 2017-10-23
I see from [http://www.omgubuntu.co.uk/2017/10/ubuntu-17-10-release-features](http://www.omgubuntu.co.uk/2017/10/ubuntu-17-10-release-features) that "The GNOME Display Manager 3 (GDM3) takes over login and lock screen duties from LightDM and the Unity Greeter."

---

### Post by gpff on 2017-10-23
Exact same problem here. Had to configure my left computer to be on the bottom, not ideal.

---

### Post by slickymaster on 2017-10-23
*Thread moved to **Installation & Upgrades**.*

---

### Post by revoddball on 2017-10-23
I am running into this as well. This however was a clean install. I will try the bottom of the screen trick.

---

### Post by revoddball on 2017-10-23
I can confirm that setting the display to be at the bottom works. Additionally if you have dual displays on your main machine it may not attach to the bottom of the main display, but the bottom of the secondary display.

---

### Post by ted.mielczarek on 2017-10-26
There's a note from the Synergy author about this, apparently synergy doesn't work with Wayland yet and Ubuntu 17.10 defaults to Wayland: [https://symless.zendesk.com/hc/en-us/articles/115004721927-Wayland-support-on-Linux](https://symless.zendesk.com/hc/en-us/articles/115004721927-Wayland-support-on-Linux)

I was able to select "XOrg" by clicking the settings icon on the login screen before logging in, and synergy works again in this configuration.

---

### Post by gpff on 2017-11-08
This seems to be fixed with the last update of the ubuntu dock. I can enter my second computer on the left again.

Edit: actually not... I was under an xorg session

---

