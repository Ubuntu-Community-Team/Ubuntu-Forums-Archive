---
title: "Ugly Ubuntu logo on login screen"
date: 2010-04-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zaphod777 on 2010-04-05
Is it just me or should the color of the Ubuntu logo be white or something instead of Orange. 

You know this is going to be a great distribution when that is all I have to nit pick about. The Wireless even seams to be rock solid now which is more than I could say about 9.10. 

I still find myself moving my mouse to the right for the buttons but I am sure I will get the hang of it soon.

---

### Post by jrothwell97 on 2010-04-05
This, I believe, is intentional: the original artwork was the glowing-white from Karmic, which was barely visible against the Ambiance theme that GDM is now using (along with the rest of the desktop.)

---

### Post by zaphod777 on 2010-04-05
Thats too bad the color is a little too much in your face if you ask me but oh well you only look at it for a sec anyway. Overall way better looking than in 9.10.

---

### Post by wmcbrine on 2010-04-05
Orange and brown have always been the Ubuntu colors. White was the aberration. :)

---

### Post by zaphod777 on 2010-04-05
I know I was never much of a fan of the orange so I was hopping to rid the last of it.

---

### Post by Megaptera on 2010-04-05
Along with the new theme, the shift in Min/Max/Close buttons from the right corner to the left has caused quite a bit of grumbling from users. While Ubuntu does not currently (as of Beta 1) provide a simple way to reverse this, it can be done from the command line with:

gconftool-2 --set "/apps/metacity/general/button_layout" --type string "menu:maximize,minimize,close"

From here:  [http://maketecheasier.com/quick-review-what-you-should-expect-for-ubuntu-10-04/2010/03/28](http://maketecheasier.com/quick-review-what-you-should-expect-for-ubuntu-10-04/2010/03/28)

---

### Post by dino99 on 2010-04-05
one of the best i ever seen is the Jaunty's one: nice design.
cant understand what we have now with Lucid, seem that ubuntu team miss real designer.

---

### Post by zipperback on 2010-04-28
> **Megaptera said:**
> 
gconftool-2 --set "/apps/metacity/general/button_layout" --type string "menu:maximize,minimize,close"


I created a modified version of Ambiance called Ambiance_R (Ambiance Right Side).

This will give people the option of switching back and forth between the versions without having to edit anything.

It's available on gnome-look.org

Here is the link.
[http://gnome-look.org/content/show.php/Ambiance_R+%28Ambiance+Right+Side%29?content=123927](http://gnome-look.org/content/show.php/Ambiance_R+%28Ambiance+Right+Side%29?content=123927)

- zipperback
:popcorn:

---

### Post by djchandler on 2010-04-29
Everyone is entitled to an opinion, but a couple of you are a little harsh IMO. It could be that the guy paying the bills had something to say about the branding and artwork. :oops:

If you want to help with the art and design, there's always room for more volunteers.;)

[https://wiki.ubuntu.com/Artwork](https://wiki.ubuntu.com/Artwork)

---

### Post by slooksterpsv on 2010-04-29
I like Kubuntus its blue and white.

---

### Post by ToxicBurn on 2010-04-29
10.4 Lucid is one of the best looking Distros out 
 
the new default colors are just what was needed all we need now is some updated icons.
 
the thing is you look at your pc everyday and Brown is just darn UGLY and not easy on the eyes 
 
my wish is for a blue colored ubuntu sort of like Fedora now thats a hot looking gnome setup they have.

---

### Post by djchandler on 2010-04-29
> **Megaptera said:**
> Along with the new theme, the shift in Min/Max/Close buttons from the right corner to the left has caused quite a bit of grumbling from users. While Ubuntu does not currently (as of Beta 1) provide a simple way to reverse this, it can be done from the command line with:

gconftool-2 --set "/apps/metacity/general/button_layout" --type string "menu:maximize,minimize,close"

From here:  [http://maketecheasier.com/quick-review-what-you-should-expect-for-ubuntu-10-04/2010/03/28](http://maketecheasier.com/quick-review-what-you-should-expect-for-ubuntu-10-04/2010/03/28)
This has been addressed multiple times within the Lucid development forum. There's no need to go anywhere besides ubuntu.com or ubuntuforums.org for answers to your questions.

Using a theme other than Ambiance or Radiance, such as Dust or NewWave, should  put the buttons back on the left.

You can also edit the /apps/metacity/general/button_layout key in gconf-editor, also called Configuration Editor under Applications>System Tools menu (if you enable it first using System>Preferences>Main Menu) . Otherwise, strike "Alt-F2" and enter gconf-editor in the command box.

---

### Post by coffeecat on 2010-04-29
> **djchandler said:**
> You can also edit the /apps/metacity/general/button_layout key in gconf-editor, also called Configuration Editor under Applications>System Tools menu (if you enable it first using System>Preferences>Main Menu) . Otherwise, strike "Alt-F2" and enter gconf-editor in the command box.

Before anyone dives into gconf-editor, have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1463878](http://ubuntuforums.org/showthread.php?t=1463878)

There's a very good reason **not** to use gconf-editor for re-ordering the buttons in Lucid (explained in the OP of that thread). Although that thread is in Forum Feedback, it does tell how to use the Appearance settings instead or there's a link to a tar.gz for the Light themes modified with buttons on the right.

---

### Post by Digikid on 2010-04-29
I agree that the older Karmic one looks a thousand times better than the Lynx one.

Thankfully you can change it.

---

