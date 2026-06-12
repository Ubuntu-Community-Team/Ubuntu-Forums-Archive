---
title: "Prevent language selection in Ubuntu 16.04 ..."
date: 2016-06-23
forum: Installation &amp; Upgrades
---

### Post by gaborgen on 2016-06-23
In 12.04 and 14.04 I made my own iso with a kickstart file, this still works in 16.04. BUT in 12.04 and 14.04 I did $(echo en > isolinux/lang) before i run mkisofs => the language selection menu did not appear, but it does in 16.04!

Any suggestions how to prevent that? Not a "problem", but it would be more nice and smooth ;-)

One more ting: I modded isolinux/txt.cfg as well and added a variable (NAME=) at the end of line starting with "append". So that when I press F6 (Expertmode) and then Esc I can enter hostnameXXX to the prompt. Does anyone have a suggestion how to make the prompt come up without F6 Esc?

---

### Post by ernestasen on 2016-07-21
> **gaborgen said:**
> In 12.04 and 14.04 I made my own iso with a kickstart file, this still works in 16.04. BUT in 12.04 and 14.04 I did $(echo en > isolinux/lang) before i run mkisofs => the language selection menu did not appear, but it does in 16.04!

Any suggestions how to prevent that? Not a "problem", but it would be more nice and smooth ;-)

One more ting: I modded isolinux/txt.cfg as well and added a variable (NAME=) at the end of line starting with "append". So that when I press F6 (Expertmode) and then Esc I can enter hostnameXXX to the prompt. Does anyone have a suggestion how to make the prompt come up without F6 Esc?

I have the same issue.. Did you solve it?

---

### Post by 360-dennis on 2016-12-11
I have the same issue here!

---

