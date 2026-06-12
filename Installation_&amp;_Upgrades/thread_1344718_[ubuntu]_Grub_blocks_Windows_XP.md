---
title: "[ubuntu] Grub blocks Windows XP"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by Antoine_de_Bock on 2009-12-03
Hey y'all,

I'm new to Ubuntu and I nearly know nothing about it. 
Here's the thing, when I start or reboot my computer GRUB automaticilly starts which is as supposed to be, when it's started you get this choice menu of which OS you want to start. It says I need to use up and down arrows to choose one. But next, when I press one nothing happens and Ubuntu, thank god, starts itself after a while. See, if this wouldn happen I couldn have done anything and I could go to a computer expert. But now there's a new problem, like I said I can't choose my operating system which makes me unable to start the computer in Windows XP. It's kind of freaking me out because I really need, for school, to start some programms which don't run on Ubuntu. Besides that I think I should be able to  start any OS I want. If this will continue I might consider removing both GRUB and Ubuntu. Is there any solution to this problem? If not, please tell me how to remove Ubuntu and GRUB.

Thank you for your time, I apreciate it.

Antoine de Bock

---

### Post by darkod on 2009-12-03
Are you sure your keyboard is working correctly? Like you said, it should work fine. And since grub is booting ubuntu that means it's not just frozen there.
Use the arrows on the keyboard between the letters and the numeric keys. The arrows on the numeric keys only work if NumLock is off.
Try few options. If you don't succeed and since you need the XP, it's easy to restore the XP MBR back on the hdd. There is not even need to remove ubuntu at this point.

PS. Do you have the option to try with another keyboard?

---

### Post by presence1960 on 2009-12-03
Are you using a USB keyboard? If so you need to go into BIOS and make sure your keyboard is set for USB or USB Legacy support.

Try another keyboard to rule out that it is the keyboard.

---

### Post by Antoine_de_Bock on 2009-12-03
> **darkod said:**
> Are you sure your keyboard is working correctly? Like you said, it should work fine. And since grub is booting ubuntu that means it's not just frozen there.
Use the arrows on the keyboard between the letters and the numeric keys. The arrows on the numeric keys only work if NumLock is off.
Try few options. If you don't succeed and since you need the XP, it's easy to restore the XP MBR back on the hdd. There is not even need to remove ubuntu at this point.

PS. Do you have the option to try with another keyboard?

No, I'm not sure it is. The joke is that I can start the bios at ALL TIME by pressing f2, and the boot menu with f11. These two options allways work. Next when GRUB starts it fails to work, and when I logged in it will work again :S. Sometimes while I'm typing it also quits working.. 

I'm going to try the bios thing like describes above and will come back to the forum after.

Thanks for help so far.

---

### Post by Antoine_de_Bock on 2009-12-03
Yep, seemed it worked. But when GRUB starts it says I have 5 seconds to choose an operating system. How can I change this time to, like, 30 seconds?

---

### Post by darkod on 2009-12-03
In terminal do:
sudo gedit /etc/default/grub

Change the timeout value from 5 or 10 to 30. Save and close the file. Then run:
sudo update-grub

It should be done.

---

