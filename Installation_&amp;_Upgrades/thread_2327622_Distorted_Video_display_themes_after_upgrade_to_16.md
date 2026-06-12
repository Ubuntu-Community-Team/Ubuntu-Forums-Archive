---
title: "Distorted Video display /themes after upgrade to 16.04"
date: 2016-06-12
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2016-06-12
Right now, the only theme that displays correctly on my PCs is highcontrast.  Ambiance will give a distorted display.  Please view the attachments.  These are screenshots of the top part of synaptic.  Please note that the one for highcontrast has the spacing for the text of the drop-down menus spaced correctly.  On the other hand, the image for ambiance shows the text all compressed.  Furthermore, the drop-down boxes are incorrect.  This occurs on my desktop PC that use the Intel i7-4770K process with Haswell graphics as well as on my DELL Vostro 3500 laptop that uses nVidia graphics.  Reinstalling 16.04 does not help.  Changing the graphics drivers on the laptop does not help.  This problem affects other applications software such as LibreOffice and evolution e-mail.

This is a very serious problem for me.  My main application is evolution e-mail.  Themes other than highcontrast not only affect drop down boxes but do not show vertical scroll bars.  The problem with highcontrast is that applications such as evolution e-mail, use white as a highlighted text color.  I have previously posted to evolution and Gnome help lists and have not gotten a response.

The ambiance theme used to work correctly for all applications before the upgrade to 16.04.

Thank you for reading,

John

---

### Post by vasa1 on 2016-06-12
> **cigtoxdoc said:**
> ..., the image for ambiance shows the text all compressed.  Furthermore, the drop-down boxes are incorrect.

... Themes other than highcontrast not only affect drop down boxes but do not show vertical scroll bars. ...


Hi, I'm using the Openbox session of Lubuntu 16.04 on a low-spec Dell laptop (core2Duo, integrated graphics, no GPU). I don't see what you see when I open Synaptic or LibreOffice with Ambiance regarding the menu items being squeezed together. For me, they're properly spaced out except that the menu items in LibreOffice are nearly invisible until I click on one; then that one becomes visible.

Could you explain a bit on the dropdown boxes?

Re. scrollbars, if you've moved straight from 14.04 to 16.04, a lot has changed in their behavior. For some gtk3 applications, the scrollbars become visible  in a "legacy" sense only when you hover over the scrollbar area. [SUP]***[/SUP]

I don't use High Contrast but Adwaita is the flag-bearer for GNOME. An application such as Evolution *should* work with Adwaita. Have you tried it? It should be available by default on your system.

[SUP]***[/SUP]I have some links on the "improved" scrollbars and will dig them out if you're interested.

---

### Post by cigtoxdoc on 2016-06-15
This problem appears to be related to the nVidia graphics in my laptop and the Intel Haswell graphics in my desktops.

Attached screenshot came from a hp/compaq dx2200 minitower (standard vga graphics)  that I have just upgraded to 16.04 and added the Gnome3 and Gnome3-staging to get latest release of evolution e-mail (3.20.3).  Theme is ambiance.  Please note that graphics are sized correctly, and there is a vertical scroll bar (on the pane with folders).  Also, dropdown menus show correct font and spacing.

So, how does one get a version of ambiance that works with more advanced graphics systems.

John

---

