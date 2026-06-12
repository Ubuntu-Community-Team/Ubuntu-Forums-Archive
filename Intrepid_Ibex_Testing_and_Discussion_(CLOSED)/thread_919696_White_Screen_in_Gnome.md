---
title: "White Screen in Gnome"
date: 2008-09-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mudfly on 2008-09-14
Hi I have searched and browsed through the forums and in Launchpad and I can't find any related info.

I am doing some Intrepid testing on 2 completely different machines, one a Dell Latitude C610 laptop and the other a rack mounted custom server. I have installed a clean version of Hardy and ran 'sudo update-manager -d' to upgrade to the latest development version of Intrepid.

On both machines after logging into gnome the screen goes completely white. You can see the cursor, and clicking with the mouse where the applications menu appears you can even launch software, however the screen remains completely white.

Both machines have an ATI chip, but I have not enabled their proprietary drivers.

If I do a 'ctrl+alt+backspace' to restart X, you can see the gnome desktop and whatever software had been launched, but only for a second while GDM stops. 

This issue is similar to something I remember happening when compiz was first being put into the distro, though I can't quite understand why its happening now.

XFCE works with no problems.

I guess my question is, Is this compiz causing this, and what can I do to disable compiz?

---

### Post by ronacc on 2008-09-14
get a terminal while gdm is running and try < metacity --replace > that will stop compiz and replace it with metcity .

---

### Post by mudfly on 2008-09-14
ronacc, thanks! A variation of that did the trick. while you can't see anything on the screen I was able to login and then 'alt+F2' and run 'metacity --replace' and after hitting enter, I was able to use gnome again.

---

