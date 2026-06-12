---
title: "How do I boot ubuntu from seperate partion?"
date: 2011-09-26
forum: Installation &amp; Upgrades
---

### Post by jordinf on 2011-09-26
Okay I installed ubuntu into a separate partion and when i started my computer it would only boot ubuntu then i used some program inside ubuntu to boot windows 7 when my machine first starts.

MY question is how do I boot ubuntu instead of windows 7 again?

I apologize if this is in the wrong section.

---

### Post by SecretCode on 2011-09-26
It's not quite clear how your computer is set up but it sounds like you have GRUB as the bootloader, but set not to show the menu.

Hold down the Shift key while booting - as soon as the screen comes on, before any windows logo appears - this should force the GRUB menu to display. It should list both Ubuntu and Windows.

If this is how it's set up, then we can change GRUB so that it displays the menu for 10 seconds to allow you to choose.

---

### Post by matt_symes on 2011-09-26
Hi

Press the shift key (and keeping pressing) when you start your PC. That should display the grub menu and give you the choice to boot Ubuntu.

If not you might have to reinstall or update grub. It depends on what you did.

Kind regards

---

### Post by jordinf on 2011-09-26
Okay so shift does nothing and now only ubuntu starts when I turn my machine on what is the name of the program that I download via synaptic package manager to change where it boots from?

---

### Post by jordinf on 2011-09-26
Okay so now when i start my computer only ubuntu boots there is no option or screen to choice windows ever.....How do I boot from windows then back to ubuntu?

---

### Post by oldfred on 2011-09-26
I think we need to see what is installed where. You should not have had to download anything from synaptic to boot Windows.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

