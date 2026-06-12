---
title: "Ubuntu as master, 98se as slave"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by Xezus on 2010-05-27
i currently have ubuntu 10.04 on my master drive. i want to install windows 98se on my empty slave drive. i hate windows, but i like to screw around on the most stable os that bill has to offer. anyway, i was just wandering if anyone has any suggestions on the best way to dual boot ubuntu(master) and 98se(slave)

---

### Post by jerrrys on 2010-05-27
install 98 and then install ubuntu.  the install will walk you thru the steps.  is that what you ment?

---

### Post by Xezus on 2010-05-27
> **jerrrys said:**
> install 98 and then install ubuntu.  the install will walk you thru the steps.  is that what you ment?

well, i have ubuntu set up how i like it, and i don't really want to re-install it. can i unplug my master harddrive, set my slave drive to master, install win98se, switch the jumper back to slave, and plug my master(ubuntu) drive back in? would that work with grub or something?

---

### Post by Zemblan on 2010-05-27
Your way wont work unless you want to be constantly swapping over and unplugging your drives when you want to boot the different OSes. Any reason you can't just install win98 in Virtualbox?

If you do want to install Windows on the secondary drive then grub will be overwritten, but it is not that difficult to re-install it. 
See: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

EDIT: actually your way might work for the install, but you'd still have to edit the grub config per the above link to add windows to it.

---

### Post by jerrrys on 2010-05-27
i wonder if supergrub may be the way to go...

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by confused57 on 2010-05-27
> **Xezus said:**
> well, i have ubuntu set up how i like it, and i don't really want to re-install it. can i unplug my master harddrive, set my slave drive to master, install win98se, switch the jumper back to slave, and plug my master(ubuntu) drive back in? would that work with grub or something?
This "should" work, just run "sudo update-grub" in Ubuntu after you've done the above & see if adds win98se to grub.

---

### Post by Xezus on 2010-05-27
> **Zemblan said:**
> Your way wont work unless you want to be constantly swapping over and unplugging your drives when you want to boot the different OSes. Any reason you can't just install win98 in Virtualbox?

If you do want to install Windows on the secondary drive then grub will be overwritten, but it is not that difficult to re-install it. 
See: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

EDIT: actually your way might work for the install, but you'd still have to edit the grub config per the above link to add windows to it.

i don't mind editing grub as long as i can keep my current installation of ubuntu.

---

### Post by Xezus on 2010-05-28
anyone know where i can download dell dimension 2400 drivers for 98se?

---

### Post by Zemblan on 2010-05-28
Probably have more luck asking where to find windows drivers on a forum which is for windows.

---

### Post by jerrrys on 2010-05-28
or just google it

[http://www.google.com/search?hl=en&as_q=dell+dimension+2400+drivers+for+98se&as_epq=&as_oq=&as_eq=&num=50&lr=&as_filetype=&ft=i&as_sitesearch=&as_qdr=all&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=images](http://www.google.com/search?hl=en&as_q=dell+dimension+2400+drivers+for+98se&as_epq=&as_oq=&as_eq=&num=50&lr=&as_filetype=&ft=i&as_sitesearch=&as_qdr=all&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=images)

---

### Post by Xezus on 2010-05-28
yeah i apologize for asking that.

---

