---
title: "Keyboard setup problems"
date: 2021-04-04
forum: Installation &amp; Upgrades
---

### Post by janvi2 on 2021-04-04
For a while (approx begin of year) I experience problems with my keyboard setup. This shows blocked cursor keys. I can reproduce this, if num-lock in the num keyfield is active. All other keys include num field work but not the cursors. It is also possible to block the delete and cursor keys with following method: Selecting a text with shift-cursor then release the shift key. Cursor keys without shift now stop working. Delete key cannot delete selected text and all other characters to write are blocked. To exit this state, press shift and cursor again and change selection of one or more characters  of the the one already selected and everything is ok again. There may be other methods to go in and out non functional states but I did not examine. I assume this is not the ordinary IBM CUA style of GNOME ?

My keyboards are old IBM style german map (without windows key). I have several species of same or similar model and all behave same at focal 20.04.2 LTS. Same keyboards behave well if connected to a W10 system. For test, I used [https://www.w3.org/2002/09/tests/keys.html](https://www.w3.org/2002/09/tests/keys.html) Cursor shows codes 37-40 and numlock is 144. After numlock, a cursor key is doing anything (screen flickers for update) but there is no code indicated on this webpage and no reaction at any other applications window on the desktop. Therefore I assume, the reason depends from system.

I already tried to reset all keyboard shortcuts and language setup what seems correct. Are there any other hidden setups possibly changed by accident ?

---

