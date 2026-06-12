---
title: "Upgrade 8.04 to 8.10 menu.list"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by thane on 2008-11-07
I am not sure where or how to post this but here is some information that you may or may not have found yet in a google search.

When you upgrade from Hardy to Intrepid, I am pretty sure there is a dialog that asks you if you want to keep your current menu.list or accept the developer's menu.list.

If you choose to keep your current menu.list, when you reboot after upgrading, you will still boot into the older kernel. One potential problem with this is that not only do you not get access to the new kernel and its features, if you intend to use a proprietary Nvidia driver e.g. 173xxx or 177xxx, the driver will not work!

Either you need to accept the developers menu.list when you upgrade, or manually go in and edit your /boot/grub/menu.list to use the new kernel. When you boot into the new kernel you should be able install and activate the Nvidia driver.

Note! This probably will not work with another, older? Nvidia driver, only the 173xxx or 177xxx drivers. The information is in the release notes.

My question to the forum's moderator, if my suggestion is correct and sufficiently helpful, is there a way to get this info into the release notes, or at least update the upgrade procedure for the next version of Ubuntu to default to updating the menu.list to use the new kernel?

If someone has a better suggestion for upgrading or if I am wrong, please jump in and update this thread!

Cheers!

/Thane :)

---

### Post by meindian523 on 2008-11-07
You are sufficiently correct,but the new kernel need not always run everyone's hardware.Therefore,IMHO,it should not be default to update the menu.lst.The current arrangement,I believe,is quite fine,as the user decided what to do with the menu.lst.

---

### Post by dazzlindonna on 2008-11-07
As a relative newbie to the upgrade process, I'd like to thank Thane for that info.  I've been holding off on the upgrade because I'm worried about my Nvidia drivers.  That one piece of information might make the whole process a LOT less of a problem.

meindian523, while what you say may be true, I think at least some documentation in the release notes would be advisable.  I know for sure that "this user" wouldn't have had a clue as to "what to do with the menu.lst" when asked the question.  A little guidance never hurts.

---

### Post by thane on 2008-11-07
I agree that it is a good idea for the user to decide what they want to do with the menu.list, but the vast majority of relatively new users will not know the advantages and disadvantages of upgrading their kernel.

In many cases they probably would want to boot using the new kernel. And, if the menu.list is upgraded they will have the option to either boot into the new kernel, or boot into the previous kernel if something does not work.

However, if the user chooses to keep the current menu.list, at least for me, the new kernel will not even show up in the menu.list. It cannot be used unless the menu.list is updated by root with gedit or whatever.

So for an experienced user, your answer is best. But for a relatively new user, I still think what I am suggesting might result in fewer help requests?

---

