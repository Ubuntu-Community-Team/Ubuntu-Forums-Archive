---
title: "Can not upgrade  to 12.04 from 11.10"
date: 2012-04-14
forum: Installation &amp; Upgrades
---

### Post by closbar on 2012-04-14
I was updating 11.10 to 12.04 and my net book crashed (I  was having problems before crashes all the time and i decide to update I though than can help me with the crashes and i did but another chrash) and after that when i try to run the partial upgrade it show me this
Can not upgrade 
 "an upgrade from 'precise' to 'oneiric' is not supported with this tool
 I need help to solve this, I'm not an expert and don't know what to do 
I really appreciate any help
Thanks

---

### Post by darkod on 2012-04-14
First of all, 12.04 is still in development, it will be released towards the end of the month.

When you boot the computer, if you select to boot the ubuntu recovery mode, can you boot it?

If you can, it might be able to finish the packages installation (if all of them were downloaded before the crash), with:
sudo dpkg --reconfigure -a

---

### Post by closbar on 2012-04-14
Thanks for your help but still the same I dont know if I'm doing right the boot at the recovery mode I cant  select recovery mode it dont gave me  that option I know that i had downloaded already almost 200 packages but not upgraded yet, and the last release of ubuntu will come soon .
thanks for your help if you can give more details of to  do it Thanks

---

### Post by darkod on 2012-04-15
Do you get a grub2 boot menu when you boot or not?

If you have only ubuntu the menu is not shown by default. You will need to hit Shift during boot to get the menu to show. After the POST is finished, before is starts loading the OS, hit Shift.

---

