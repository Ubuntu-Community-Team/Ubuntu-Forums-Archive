---
title: "HAL cursor speed gripes"
date: 2010-04-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Joh_ on 2010-04-26
About half a year ago, I installed 9.10 and my mouse suddenly went in lightning speed. GNOME was ignoring my mouse settings, and after an hour of googling I had found several people with the same issue but no solution. To find the solution took me half a day extra. As it turned out, HAL was now in use (since 9.04 afaik, but I hadn't used ubuntu in a while) and GNOME did not change HAL's settings when dragging the mouse speed slider. To change mouse speed, I had to create a .fdi profile file, put all my guessed proper values in it and store it in a cryptic system folder, as root. All in all it took me a whole day to find the solution, modify the .fdi file to work with my mouse (my mouse does not turn up with having input.mouse capabilities) and to tweak the values.

Aside from forcing everyone to get used to my mouse settings, all was well. Until today when I upgraded to pre-release Lynx. My mouse is once again going at lightning speed and my .fdi file is being ignored from the looks. The GNOME mouse speed slider **still** does absolutely nothing and googling gives me nothing. I'm currently working on a project for uni and do not have time to spend another full day trying to get my mouse to be usable, so this will have to wait for now.

Would it be too much to ask that GNOME's mouse properties work as intended? Or to be able to change the most fundamental usage properties on a per-user basis rather than a per-system basis? Or that changes in the most core functionalities of the system be "upgraded" so they work in the way the user would expect? HAL might be a superior backend for input devices, but currently even "learning" to change mouse cursor speed feels like running headlong into a brick wall.

---

