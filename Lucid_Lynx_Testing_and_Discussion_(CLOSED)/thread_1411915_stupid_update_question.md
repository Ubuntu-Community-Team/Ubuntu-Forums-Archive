---
title: "stupid update question"
date: 2010-02-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mick222 on 2010-02-20
I am running updates for lucid and grub is being replaced, the installer asks me where to install grub . How do i check the box in the terminal for where i want to put it. I think it should be in /dev/sda1 as this is my lucid partition but should i also put it on my other drive which has suse on it.

---

### Post by Bachstelze on 2010-02-20
You should install it on the MBR of the drive your BIOS boots from, so just type for example /dev/sda.

---

### Post by mick222 on 2010-02-20
thx that clears that up but it's giving me check boxes in the terminal and i cant seem to select any of them.My computers been offline for a few weeks and update manager was offering a partial upgrade so i used sudo apt-get update && sudo apt-get upgrade to do a safer upgrade.

---

### Post by ranch hand on 2010-02-20
Space bar will do the check.  Up and down keys for navigation.  Tab key to get to "OK".  Hit enter.

---

### Post by mick222 on 2010-02-21
thx ranch hand tried every key but the spacebar .Went ahead and done the update without changing grub will it update next time.

---

