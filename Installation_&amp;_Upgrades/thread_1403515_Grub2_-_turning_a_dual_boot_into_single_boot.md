---
title: "Grub2 - turning a dual boot into single boot"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by kwildman on 2010-02-10
I recently got a netbook and setup as dual boot between win7 starter and 9.10 (64bit).   Win 7 starter is not impressive so i want to nuke it and give the space all to my /USR partion.     I am comfortable working with Gparted and assume that i can launch using my gparted live usb and delete the windows partion and then resize the /usr partion.

My question is what changes do i need to make w/ Grub2?   I would prefer not to see the Grub menu at all and have it load right the main kernel if possible.     Also, if this is possible is there a way to get to the Grub menu during boot should i need to select a different kernel?

As always thanks in advance for any help!

---

### Post by darkod on 2010-02-10
With grub2 you don't need to do anything special. After you plan everything, and you delete the win7 partition(s), just run sudo update-grub and because there will be no win7 to detect any more, it will simply delete it from its list.
With ubuntu being the only OS I think it automatically goes into mode to load the main kernel right away so you should see no menu.
You can get the menu by pressing Esc but you have to time it correctly, after BIOS finishes and before ubuntu starts to load actually.

---

### Post by kwildman on 2010-02-10
awesome.  I actually just found this on another site.   i remember doing this with the old grub and it was not as straight forward.

Thanks for the help!

---

