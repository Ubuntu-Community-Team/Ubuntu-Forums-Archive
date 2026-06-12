---
title: "system tray icons"
date: 2010-02-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by descendent87 on 2010-02-26
Haven't used ubuntu for a long time, decided to try alpha 3 last night and now using it as my main os, it's shaping up to be a great release.
One thing I really like is the icons in the system tray, I installed x-chat  and it uses the normal system tray icon which looks out of place. I didn't think anything of it as I assumed those icons were only for pre-installed apps. I then opened tomboy and found it was also using the normal sys tray icon so I looked in the icons folder and found humanity-dark which is the icon theme the system tray icons use and found there is an icon for both x-chat and tomboy.
Is this a bug that they're not using the humanity-dark icon theme or is there something I should set?

---

### Post by kahumba on 2010-02-26
x-chat etc are "standalone" applications and are supposed to come with their own icons (Gnome's theme(s) can't provide icons for all the apps in the world). Being Humanity-like is welcome but not a must. The Ubuntu devs might cherry pick and patch some apps to make their icons "better", it's really subjective and discrete.
Also, in case it matters, a theme can inherit/extend another theme and the root of every theme is the one called "hicolor". Example: Humanity extends Gnome which in turn extends Hicolor.

---

### Post by descendent87 on 2010-02-26
Yes I know they're standalone apps but what I'm saying is there's an icon for them in the humanity-dark icon theme (the theme that all the other icons in the system tray use) but it's not being used

---

### Post by ranch hand on 2010-02-27
You should be able to change the Icon being used by the app to that in the folder.  The app determines the Icon.

---

### Post by Keyper7 on 2010-02-27
The humanity icon theme exposed a limitation of many apps, which is not allowing separate theming of the tray icons. Some apps simply hardcode their icons (ex: aMule) and others make the tray icon be the same as the shortcut icon. It is possible that some apps you are referring to need some patching before being able to use separate icons for the shortcut and the tray icon, and that's why the icons are not being used yet, despite existing.

---

### Post by QwUo173Hy on 2010-03-24
Apparently there's a [fix released]("https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/531533") which is also [reported here]("http://www.omgubuntu.co.uk/2010/03/lucid-starts-to-get-some-updated-icons.html") -  but I'm still not seeing it in my updates.

---

### Post by kurros on 2010-03-24
> **jarlath said:**
> Apparently there's a [fix released]("https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/531533") which is also [reported here]("http://www.omgubuntu.co.uk/2010/03/lucid-starts-to-get-some-updated-icons.html") -  but I'm still not seeing it in my updates.

That bug report describes the situation that Keyper7 explained. Fix Released refers to the icon theme now released having the new icon, but Tomboy still needs to be patched to not hard code its own icon. It is in Fix committed state for Tomboy which means the patch is done and should be included in a future package update.

---

### Post by QwUo173Hy on 2010-03-24
Thanks for explaining what Fix Committed means kurros.

---

