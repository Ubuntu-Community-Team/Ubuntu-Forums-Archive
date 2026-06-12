---
title: "Problems with Unity (I guess)"
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by mac67 on 2011-06-19
Hi,

I just upgraded from version 10.10 to 11.04. I have regularly upgraded since 8.04, so I am confident I did not do any mistake. Although I have Kubuntu, I use GNOME.

The system works, but... I do not see either the new taskbar, or the four desktop panels, or the Trash. I can run applications only by clicking on their files. When I reduce an application to icon, it disappears from screen.

Can anybody help me?

---

### Post by nrundy on 2011-06-19
I'm not sure I'm understanding what your describing. four panels? taskbar, do you mean Launcher?

Can you post a screenshot?

---

### Post by mac67 on 2011-06-19
> **nrundy said:**
> I'm not sure I'm understanding what your describing. four panels? taskbar, do you mean Launcher?

Can you post a screenshot?

Hi, thanks. 

I do not see either the Launcher in the upper part of the screen, or the new Unity icons on the left (not even when I put the mouse pointer there), or the Trash, or the four workspaces. I cannot post a screenshot, all I can do is right-click on the desktop and open any file on the desktop or in the external HD. And open a terminal with ctrl+alt+T.

---

### Post by mac67 on 2011-06-19
Hi, I sort of solved it.

I switched to Unity 2d after installing it, now it works fine. I see the Launcher, the Unity icons, everything.

nrundy, thanks for taking care.

---

### Post by nrundy on 2011-06-19
unity 2d?

are you running 11.10 alpha? 

If you're running the alpha, this might explain your problems. It's not stable yet. Far as i know, unity 2d is only available in 11.10. There might be a PPA though, are you using that?

---

### Post by mac67 on 2011-06-21
Hi,

I upgraded from kubuntu 10.10 to 11.04 and I got the problems mentioned int he first post: no Launchbar, no applications dock on the left. Then, before writing username and password at login, I chose unity 2d and logged in. I could this way make it work. Though, I still have some minor problem. No idea about 11.10.

One more thing: I read this solution from another thread: after getting a termina I wrote:

sudo add-apt-repository ppa:unity-2d-team/unity-2d-daily
sudo apt-get update
sudo apt-get install unity-2d-default-settings

and then chose unity 2d before logging in.

If you have suggestions that can improve the situation they are greatly appreciated.

---

