---
title: "Menú contextual en Nautilus | Context menu in Nautilus"
date: 2018-04-05
forum: Installation &amp; Upgrades
---

### Post by EGKaltenmeier on 2018-04-05
Hola a todos, saludos.
  Recientemente actualicé mi distribución de 16.04 LTS a 17.10, y ahora no funciona el menú contextual cuando oprimo la tecla "Menú" del teclado, teniendo seleccionado un elemento en Nautilus (en otras aplicaciones funciona correctamente).
  Intenté buscando personalizar algún atajo de teclado, pero no lo he logrado. Aclaro que probé usando (Ctrl + F10), (Shift + F10) y (Super + F10), pero ninguna me dió resultado.
  Sólo puedo ver las opciones del archivo si navego con el cursor hasta seleccionar el elemento (no funciona tampoco cuando lo selecciono navegando con las flechas del teclado) y abriendo recién allí el menú contextual, pero con el botón derecho del touchpad.
  Si Nautilus ha perdido esa opción, igualmente me interesa establecer algún atajo de teclado para poder seguir usando la tecla "Menú". Esto no sé cómo personalizarlo: me ayudaría si me dijeran cómo debo configurar el comando de desplegar el menú contextual de un elemento seleccionado.
  Información técnica: SO Ubuntu 17.10 64bits, versión de GNOME 3.26.2, versión de Nautilus (creo) 3.26.0. Equipo: Lenovo G470 (del año 2012 pero a la que le quedan varias batallas por delante...)
  Desde ya, muchas gracias! Saludos!
____________________
[ENGLISH version (?)]
  Hello everyone, greetings.
  Recently I updated my distribution from 16.04 LTS to 17.10, and now the context menu doesn't work when I press the "Menu" key on the keyboard, having an item selected in Nautilus (in other applications it works proprertly).
  I tried to personalize some keyboard shortcuts, but I havn't any success. Yes, I tried using (Ctrl + F10), (Shift + F10) and (Super + F10), but none of them gave me any results. They open other menus from Nautilus, but not of the selected file.
  I can only see the options of the file if I first navigate with the cursor and select the element (it doesn't work either when I select the file with the arrows on the keyboard), and open the contextual menu there but with the touchpad's right button.
  If Nautilus has lost that option, I am also interested in costumize a keyboard shortcut to continue using the "Menu" key. But I don't know how do it: it would help me if anybody told me how to configure the command to display the contextual menu of a selected element.
  Technical information: Ubuntu OS 17.10 64bits, GNOME version 3.26.2, Nautilus version (I guess) 3.26.0. Computer: Lenovo G470 (year 2012, but with so many battles ahead...)
  Thanks in advance. Regards!

---

### Post by vanadium on 2018-04-06
This is normal current behaviour of nautilus, I am afraid. When you first start up "Files", focus is on the "Home" in the left bar. Accordingly, the context menu you obtain with the menu key is that of these "Places". With the right arrow, you move selection to the files pane, however no file is selected, although the dashed border is around the first file there: you there get the context menu of an empty spot. Arrow down then selects the file, i.e., makes it coloured. Only then you obtain the context menu of the file.

---

### Post by EGKaltenmeier on 2018-04-06
> **vanadium said:**
> This is normal current behaviour of nautilus, I am afraid. When you first start up "Files", focus is on the "Home" in the left bar. Accordingly, the context menu you obtain with the menu key is that of these "Places". With the right arrow, you move selection to the files pane, however no file is selected, although the dashed border is around the first file there: you there get the context menu of an empty spot. Arrow down then selects the file, i.e., makes it coloured. Only then you obtain the context menu of the file.

Thanks! I don't remember that was the behaviour in 16.04, I just used always the "Menu" key. But now it don't work. About your reply, when I use the arrow down, it selects the file but the context menu is still showing the menu of an empty spot. Only when I move the cursor to the file and press the right key of the touchpad it show the context menu of the selected file.

Do you know if I can customize a shortcut for that command (show the context menu of a selected file)?

---

### Post by vanadium on 2018-04-07
That is not what I am experiencing: when a file is selected with the keyboard, the correct context menu comes up, not the one for an empty spot. As a matter of fact, one a file is selected, I do not see how you can unselect to have the "Empty spot" right-click menu with the keybord. However, I found out that you can reveal the "Empty spot" menu at any time using Ctrl+F10.

You are using 16.04, I am using 17.10 which has a more recent version of nautilus. That would seem a possible explanation for the differences in behaviour we experience.

There is no build-in way to customize right-click menus. However, the tool "nautilus actions" still works to add any custom right-click menu, where you can very specifically determine the context (I actually find the program quite difficult to learn). I use it for one single "Empty spot" context item, i.e., moving the files from "Downloads" to the current folder.

A build-in possibility to access scripts from the right-click menu is "Nautilus Scripts". These are scripts that can appear in the right-click menu. Easy to set up (just copy your scripts in .local/share/nautilus/scripts, see [https://help.ubuntu.com/community/NautilusScriptsHowto](https://help.ubuntu.com/community/NautilusScriptsHowto)), but not "granular": the items appear (under a sub menu) in any right-click menu.

---

### Post by EGKaltenmeier on 2018-04-07
> **vanadium said:**
> That is not what I am experiencing: when a file is selected with the keyboard, the correct context menu comes up, not the one for an empty spot. As a matter of fact, one a file is selected, I do not see how you can unselect to have the "Empty spot" right-click menu with the keybord. However, I found out that you can reveal the "Empty spot" menu at any time using Ctrl+F10.

Yes, but my problem is that once I have a selected file, and without unselect it, it show me the "empty spot" context menu. And I want the menu from this selected file.

> **vanadium said:**
> You are using 16.04, I am using 17.10 which has a more recent version of nautilus. That would seem a possible explanation for the differences in behaviour we experience.

I used 16.04 until Wednesday. There I updated to 17.10. And this problem appeared, only in Nautilus.

I'll try working with the scripts...

---

