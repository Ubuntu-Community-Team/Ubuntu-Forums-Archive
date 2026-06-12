---
title: "monitor dont display desktop plz help"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by Swinger7714 on 2006-06-03
hello
i m new to ubuntu and i just downloaded the kubuntu 6.06 . i booted my computer from the cd and chose install or run kubuntu. after the loading with all the "ok" when the kubuntu desktop should show up , my monitor shuts down and writes " 95.0khz / 59.8 hz    frequensy out of range try other resolutions" yet all the resolutions i tried still the same problem . only safe graphics mod works.

my proview monitor is not very old but allso not very new.

i dont care installing kubuntu on safe graphics mod. but i must be sure that there is a way to fix this problem after installing. cuz i dont wanna use low graphics mod my whole life. plz help  :confused:  .

oh and almost forgot, i googled this problem and i noticed that alot of people that have amd 64 bit have this problem, yet i have a regular pentium 4 .and i downlaoded the regular version of kubuntu(for regular computers). and i didnt understood the solution for it :S .

---

### Post by curuxz on 2006-06-03
Ok its simple enough, could you please post the file /etc/X11/xorg.conf this file controls your screen resolution and number of monitors etc. Its just a case of editing a few lines, saving rebooting and hey presto it should work fine :)

If you post that file and then say what resolution your trying to use and what type monitor you have we should be able to help you out.

---

### Post by Caraibes on 2006-06-03
I am having a display problem as well, with a ati Radeon video card, and a Dell 18¨LCD monitor.
I tried to run dapper in live -cd and the display is flickering very much...
Don´t know what to do, since it installed fine on other pc´s...
:-| :???: :neutral: :-k

---

### Post by curuxz on 2006-06-03
[QUOTE=Caraibes]I am having a display problem as well, with a ati Radeon video card, and a Dell 18¨LCD monitor.
I tried to run dapper in live -cd and the display is flickering very much...
Don´t know what to do, since it installed fine on other pc´s...
:-| :???: :neutral: :-k[/QUOTE]

Ok Caraibes try searching the forum for the settings for your monitor or googling your monitor name and the words xorg.conf then if your from the live cd there is an option to do specific video modes (press f1 when it comes up with the options to boot live disk and its in there) that should allow you to set the correct display modes to use the live cd, when you install  you will need to edit xorg.conf to make those changes permient.

---

### Post by Swinger7714 on 2006-06-03
dude... i didnt install kubuntu yet.  i tried to run it from the cd. how can i get this file if i hav'nt installed kubuntu yet?

---

### Post by curuxz on 2006-06-03
In that case, you can either safely install Kubuntu and then I can show you how to fix it once you have it installed OR you can follow the steps i suggested above looking at the boot options for the live disk :)

---

### Post by Swinger7714 on 2006-06-03
i tried all the resolutions in the boot menu from 640*800 to 1200*1600 . still the same problem.  are you sure it can fixed after installation? if so, i will bring up this threat after i l done installing. thanks for the help.

---

