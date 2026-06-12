---
title: "Upgrade 17.04 to 17.10 without GNOME Shell/Wayland?"
date: 2018-01-05
forum: Installation &amp; Upgrades
---

### Post by csdgbas on 2018-01-05
Sorry if this has been asked before.  I couldn't find anything about it, and I am quite prepared to believe that I'm the lone weirdo.

Is the question in the thread title possible? I tried 17.10 with what I assume was the GNOME Shell, and it was so slow it was unusable. In addition, I heartily dislike Unity, and so run Openbox instead (I'm not interested in any kind of advocacy here, so just please don't), and keep Unity around as an alternative for when I need to do admin or configuration tasks (for one, the different look to Openbox when I am using Unity reminds me that I am not doing something "normal", so I tend to be more "careful", and second, almost all the advice out there on how to do X explains it in Unity terms, so it is simply easier).  Openbox does not, and as far as I am aware, never will, run with Wayland.

So, I want to keep my nice Openbox, please, and also (possibly) keep Unity as well.  Possible?  I don't really want to have to do admin tasks using a GUI that is as slow as GNOME Shell is for me.

---

### Post by grahammechanical on 2018-01-05
The upgrade from Ubuntu 17.04 to Ubuntu 17.10 will add Gnome 3 shell. Unity will not be removed. You will find additional login options. The Ubuntu option will be Gnome 3 shell & we can log in on Wayland or the X Server. The Unity option will be ... You guessed it.

A fresh install of 17.10 or 18,04 will not include Unity 7. At the moment Unity 7 is still in the Ubuntu repositories. So, it can be installed afterwards. We need to install not only Unity 7 but also Unity Control Center & Unity Session. Otherwise we will be lacking few desktop Utilities. There is Ubuntu Desktop which is not the same as Ubuntu Gnome Desktop. I have both installed on this hybrid system which started out as Ubuntu gnome 17.04 and is now Ubuntu 18.04 development branch + Unity.

I notice that there is a ubuntu-unity-desktop package which might be just all that is needed. I used Synaptic Package Manager to install the Unity packages because that will bring in all the other packages that are dependent with Unity.

I am not sure how long Unity will remain in the Ubuntu repositories.

Regards.

---

### Post by vasa1 on 2018-01-05
"Upgrade 17.04 to 17.10 without GNOME Shell/Wayland?". AFAIK, you can't make such changes *at the time* of upgrading.

If you want a lighter system with Openbox, do a clean install of Lubuntu. That should provide a GUI for "I need to do admin or configuration tasks".

---

### Post by csdgbas on 2018-01-07
> **grahammechanical said:**
> The upgrade from Ubuntu 17.04 to Ubuntu 17.10 will add Gnome 3 shell. Unity will not be removed. You will find additional login options. The Ubuntu option will be Gnome 3 shell & we can log in on Wayland or the X Server. The Unity option will be ... You guessed it.
Okay, thank you.  The system I tested G3S on was a fresh install; I wasn't aware that an upgrade would give me something different.

> **vasa1 said:**
> "Upgrade 17.04 to 17.10 without GNOME Shell/Wayland?". AFAIK, you can't make such changes *at the time* of upgrading.
It's okay, @grahammechanical pointed out that Unity wouldn't be removed anyway, so as long as I will still have X I can still use that.

> If you want a lighter system with Openbox, do a clean install of  Lubuntu.
Why would I want to erase what works fine as is?  Nuking the entire system just to get to a currently supported version of the OS is, IMO, an insane thing to do.

---

