---
title: "Ubuntu&amp;WindowsXP,WindowsWon'tBoot !"
date: 2012-01-27
forum: Installation &amp; Upgrades
---

### Post by JoelMayer on 2012-01-27
For several years now I have been running Windows XP Pro SP3 and Ubuntu 10.04 on an HP Compaq 6730s lap top with Acronis OS Selector installed in windows. Just recently Windows crashed and it won't boot. I can see Windows in my Acronis OS Selector but when I select it, Acronis just spins around and returns me to it's start page. I can boot into Ubuntu from Acronis. I can see Windows on the Grub2 menu but when I try to boot into windows I get a black screen of death. Worse, I cannot get into windows through any of the safe mode options. 
 
(1) I found the boot.ini file so I could make changes in the boot.ini code if someone would tell me what needs to be done. (2) It might help to run windows chkdsk from the Ubuntu command line but I don't know how. (3) I can take screenshots in Ubuntu so if someone wants a screen shot I will be happy to post it to this thread. Thanks!

---

### Post by darkod on 2012-01-27
As you said yourself, your problem is with booting windows and is not related to ubuntu. Maybe you could get more specialized help on a windows forum.

You can't run chkdsk from ubuntu, it's a windows tool. It might be present on some custom CDs like Hirens Boot CD or similar, but I am not sure. You will need to google it around.

Do you have a XP install CD? If you do, you can boot with it, start the install and immediately the first screen after it lods bunch of files will offer to enter the Recovery Console with R.
If you are not used to working with it, you can select to Install and that screen and press Enter, but on the next screen it should detect the existing installation and offer to repair it. Be careful, if it doesn't detect it and offer to repair, don't continue with the install because that would install a completely new XP.

---

