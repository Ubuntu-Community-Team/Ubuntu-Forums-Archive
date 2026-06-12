---
title: "New Components for Fn Key Handling: Testing Needed"
date: 2009-05-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by 23meg on 2009-05-08
As part of the migration from HAL to DeviceKit / udev-extras, Martin Pitt has recently been working on the transition from hal-setup-keymap, which is the component that makes special (Fn) keys (brightness, volume, shortcut keys etc.) on keyboards work, to a set of udev rules and keymaps, and he could use some testing, especially from people who have laptop keyboards with tricky configurations (Sony laptops and ThinkPads in special).

A testing PPA is available, and you'll find the testing instructions at [his blog post]("http://martinpitt.wordpress.com/2009/05/08/devicekit-update-future-handling-of-fn-key-maps/"). Please post test results **as comments to the blog post** (or send them via e-mail) as he has requested.

Packages are available for Ubuntu 9.04 as well.

---

### Post by aamukahvi on 2009-05-08
edit: well, i'll just try those instructions one day...

How about the slim Apple Keyboard? Would it be possible to test its unrecognized brightness keys? On jaunty, using 'xev' they only give FocusOut/FocusIn/KeyMapNotify events as opposed to other keys which yield KeyPress/Release events.

---

### Post by Nullack on 2009-05-08
Thanks for that 23meg. I dont have such keyboards on my test systems but it certainly is great to see this sort of functionality getting some love as clearly these things should just work for laptop users. This is a core part of bringing the quality of Ubuntu up to where it should be.

---

### Post by ghindo on 2009-05-08
Thanks for this, 23meg.

---

### Post by Martje_001 on 2009-05-09
Great great great! Finally we'll be rid of HAL :)

---

### Post by 23meg on 2009-05-09
Thanks to all who posted testing results. Martin has reported that the changes are now in [udev-extras upstream]("http://git.kernel.org/?p=linux/hotplug/udev-extras.git;a=summary").

---

### Post by maheshasolkar on 2009-05-09
I followed the steps on Sony Vaio VGN-T140P laptop.

  [http://esupport.sony.com/US/perl/model-documents.pl?mdl=VGNT140PL](http://esupport.sony.com/US/perl/model-documents.pl?mdl=VGNT140PL)

The brightness control keys (Fn+F5 and Fn+F6) that used to work, now don't work anymore. Special media buttons (DVD, Play/Pause, Stop, volume control etc.) have never worked for me so I am not too worried about them - although it will be awesome if they start working with this new mechanism.

I am attaching the udev.log here. I could not find Martin Pitt's email address on the blog post and I did not want to pollute the comments with a lengthy log.

Hope this data is helpful.

---

### Post by 23meg on 2009-05-09
Please post the log to [a pastebin]("http://ubuntu.pastebin.com/") and provide a link to it in the comments.

---

