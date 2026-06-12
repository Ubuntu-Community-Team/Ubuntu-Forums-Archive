---
title: "weird keyboard behaviour after upgrade from 8.04 to 8.10"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by micki on 2008-09-10
Hi,

my Ubuntu 8.04 went great but after I decided to upgrade it with

*update-manager -d*

I have some problems. Because of nvidia drivers I installed not the default kernel that comes with ubuntu 8.10 but the kernel 2.6.26.3 from kernel.org.

After logging into gnome I have only default keyboard as letters but not the arrow keys or for example <ctrl>+Fx leads to beep on console.

I checked the properties in "Keyboard Settings" and removed, added again the "German/German" Layout and tried "Generic Keyboard 101" and "Generic 105 Intl". These Settings used to be well.

Does anyone have similar experiences?

So long!
micki

---

### Post by Pumalite on 2008-09-10
Post:
uname -a

---

### Post by micki on 2008-09-10
[I]Linux jupiter 2.6.26.3 #3 SMP Wed Sep 10 08:20:07 CEST 2008 i686 GNU/Linux
[/I]

To find a solution I googled and found something about codepage things. Then I changed the default in kernel configuration to utf-8 instead of cp437 but nothing happened after reboot. Same problem as before.

Don't know if there is a connection but the settings "follow focus" in the System->Preferences->Windows does not work either. So I have to click each window to make it active. Before the upgrade the "mouse over window event" makes the window active.

Thank you for your help.

---

### Post by Pumalite on 2008-09-10
Intrepid Ibex is using kernel 27-2
??

---

### Post by cariboo on 2008-09-10
You may be better off using the latest Intrepid kernel as the kernel you are using may be compiled differently from the stock one. The latest nvidia drivers work well in alpha 5.

If you have any more questions or problems it would be best to ask them here:

[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

Jim

---

