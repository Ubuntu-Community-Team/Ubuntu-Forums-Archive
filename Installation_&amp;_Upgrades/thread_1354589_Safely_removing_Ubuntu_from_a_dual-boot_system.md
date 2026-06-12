---
title: "Safely removing Ubuntu from a dual-boot system"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by ChrisBlizzard on 2009-12-14
Hi there

I had Win 7 installed. Used Wubi to install Ubuntu in the spare space after the WIndows partition.

Want to get rid of it now - how can I safely remove it, and GRUB, and put my system back to normal please?

Many thanks

---

### Post by bigsmitty64 on 2009-12-14
The first time I loaded Ubuntu,I did it with wubi also. If I remember correctly,while in Windows,browse to the ubuntu folder, and there should be an uninstall. It was THAT simple. And it was really quick!

---

### Post by darkod on 2009-12-14
wubi is removed from add/remove programs like any windows app. Don't worry about grub because you don't have it. Wubi is virtual ubuntu, you have no grub. Using the add/remove programs should remove the ubuntu entry from windows bootloader too.

---

### Post by ChrisBlizzard on 2009-12-15
In which case I was incorrect with my first statements - Ubuntu is not installed within Windows but on a separate partition, and GRUB is there etc.

I thought Wubi was the installer only - my bad.

I ran the Ubuntu DVD from within WIndows and ended up with Ubuntu installed - thought that was what Wubi was.

Ok, so who can tell me how to safely get Ubuntu off my PC. I had Win 7 installed first, then put Ubuntu on, now want it off

---

### Post by darkod on 2009-12-15
> **ChrisBlizzard said:**
> In which case I was incorrect with my first statements - Ubuntu is not installed within Windows but on a separate partition, and GRUB is there etc.

I thought Wubi was the installer only - my bad.

I ran the Ubuntu DVD from within WIndows and ended up with Ubuntu installed - thought that was what Wubi was.

Ok, so who can tell me how to safely get Ubuntu off my PC. I had Win 7 installed first, then put Ubuntu on, now want it off

What I said still counts. If you put the ubuntu cd/dvd from within windows and the install started, you have wubi. The only way to install full ubuntu is booting from the cd and selecting Install Ubuntu in the menu. One more indications, just check your add/remove programs (or just called programs in control panel now), if you have Ubuntu entry under U, then you have wubi. Just select that entry and select Uninstall like you remove any windows app.
It should uninstall everything for you. In case you don't have ubuntu entry in there, let us know, the procedure is different.

---

### Post by ChrisBlizzard on 2009-12-15
Sorry if it wasn't clear. No entry. I DO NOT have Wubi. I have Ubuntu.

---

### Post by darkod on 2009-12-15
OK, sorry.
You can basically format the ubuntu partition(s) as ntfs and use them for windows. That's it. You would probably want to combine both root and swap partitions in which case you can delete them and in that space just create single ntfs partition. Up to you.
As for getting rid of grub, use your win7 dvd with the Repair This Computer option (after the language selection screen, look at the bottom options).
In case you don't have win7 install dvd, you can get just a repair image that you can put on cd too (it's small) here:
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

