---
title: "Future upgradability questions."
date: 2014-08-19
forum: Installation &amp; Upgrades
---

### Post by Tommy_de_Neef on 2014-08-19
Hi everyone,

i have a couple of questions about my Ubuntu experience. :)

I am running Ubuntu 14.04 right now, but i am worried about future updates.
The migration to the "ubuntu next" desktop and the touch friendly interface.

Will there be a desktop friendly side of this "ubuntu next" too?
And if there will be, will the upgrade from 14.04 to the new release be seemless?

Thanks in advance. :)

---

### Post by overdrank on 2014-08-19
Hi and welcome, maybe this can help [_UnityNextSpec_]("https://wiki.ubuntu.com/UnityNextSpec")

---

### Post by Tommy_de_Neef on 2014-08-19
Thank you for the answer.

I have another question though,
When Ubuntu next arrives in 14.10 (?) will i be able to upgrade to the new desktop seemlessly? or will i have to do a fresh install?

Thank you.

---

### Post by grahammechanical on 2014-08-19
Keep in mind that 14.04 is an LTS release and it is supported for the next 5 years. I have not heard of any intention to backport Mir, Unity 8 and the converged phone/tablet code into 14.04.

I am running Utopic Unicorn (14.10) daily and it is still using the Xserver, Lightdm, Compiz and Unity 7. Unity next (now called Unity 8) is not going to be in 14.10.

It is intended that convergence be complete for the release of Ubuntu 16.04. The developers do not want to mess up 14.10, 15.04 and 15.10 by converging the code on the go. So, the developers have created a parallel code branch and that is where convergence is taking place. There is even an ISO image that we can download and install. This code branch is called Unity-Desktop-Next.

I have installed Unity-Desktop-Next. I cannot get past the login screen because I have a Nvidia graphic adapter and there is a problem. I have heard that it works better on Intel graphics but Unity-Desktop-Next is still very much a phone/tablet user interface and not so much a desktop user interface. But all that is yet to come.

Remember, the aim is for one Ubuntu that will come pre-installed on phones and tablets and can also be installed on laptops and desktops with a user interface appropriate for each type of device that it is installed upon.

You have nothing to worry about except the usual worries that come with upgrading from one Ubuntu release to the next. Which is why some of us recommend a fresh install instead of an upgrade.

> [COLOR=#333333][FONT=Ubuntu Beta]The goal is to ramp up the quality of the unity8 desktop, without destabilizing our current environmenent. For that we are going to keep an unity7 image and add a new one for unity8 on the desktop, that new iso should become the default one by 16.04.[/FONT][/COLOR]

[https://wiki.ubuntu.com/Unity8DesktopIso](https://wiki.ubuntu.com/Unity8DesktopIso)

Regards.

---

### Post by ian-weisser on 2014-08-19
> **Tommy_de_Neef said:**
> Will there be a desktop friendly side of this "ubuntu next" too?

Yes. The entire point of Unity next is that it's desktop-friendly, tablet-friendly, and phone-friendly.
Ubuntu is not turning its back on the desktop.


> **Tommy_de_Neef said:**
> will the upgrade from 14.04 to the new release be seemless?

Yes, as long as you haven't uninstalled the ubuntu-desktop metapackage.

---

### Post by Tommy_de_Neef on 2014-08-20
This explains enough for me. Thank you for the help everyone :)

[SIZE=1]*Should i now close the thread? or keep it open for further discussion?*[/SIZE]

---

