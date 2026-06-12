---
title: "Update broke Grub, Ubuntu"
date: 2009-08-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Rippy on 2009-08-10
Ubuntu commit suicide again :/

I installed Alpha 3 from a CD, changed a couple preferences, then ran the update manager which downloaded an innocent-sounding 27 megs of updates. The end result of this was a murder-suicide: Ubuntu broke grub and then broke itself.

Now, on boot, grub does not display a list of options: it boots immediately into Ubuntu. Ubuntu gets through its loading bar and then freezes at a black screen. I tried restoring grub with the help of a tutorial aimed at restoring grub after installing Windows, but this did nothing.

Anyone know how I can repair this? At least get grub working again so that I can use XP? I know this is pre-release, but still, it's pretty late in development, and this is probably the third time Ubuntu completely destroys itself for me due to a simple update...

---

### Post by tekstr1der on 2009-08-10
The grub menu is now hidden by default. Just press Esc after BIOS loads to view the grub menu. Try to boot to single user mode.

---

### Post by mano cazalet on 2009-08-10
pressing ESC solves the grub menu issue.
but maybe there is something more with that blank screen

---

### Post by rajeev1204 on 2009-08-10
> **tekstr1der said:**
> The grub menu is now hidden by default.

Thats a bad idea.Are you sure of this?

---

### Post by Sub101 on 2009-08-10
Yep. Message sent out today was:

> As of today's GRUB 2 upload to Karmic, the boot menu is hidden by 
default, which was the way it was by default with GRUB Legacy. For those 
of you with other operating systems installed, this is not the correct 
default, but it was difficult to see how to preserve this automatically 
in a reasonable way. 
 
If you're upset by the boot menu being hidden all of a sudden, then you 
should edit /etc/default/grub, comment out the GRUB_HIDDEN_TIMEOUT line, 
and set GRUB_TIMEOUT to the timeout you want in seconds (say "10"), then 
run 'sudo update-grub'. 
 
Although I'm not *too* worried about upgrades through Karmic being a 
little rocky in the cause of getting to the right place in the end (so 
I'm just posting instructions here on the basis that most people running 
Karmic ought to be following -devel-announce), we do of course still 
need to clear up the upgrade for upgraders from 9.04. This is filed as 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/386789](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/386789). 
 
Thanks, 
 
-- 
Colin Watson                                       [cjwatson@ubuntu.com] 
 
-- 
ubuntu-devel-announce mailing list 
[email]ubuntu-devel-announce@lists.ubuntu.com[/email] 
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce) 


---

### Post by joepotter on 2009-08-10
> **Sub101 said:**
> Yep. Message sent out today was:

...

If you're upset by the boot menu being hidden all of a sudden, then you
should edit /etc/default/grub, comment out the GRUB_HIDDEN_TIMEOUT line,
and set GRUB_TIMEOUT to the timeout you want in seconds (say "10"), then
run 'sudo update-grub'. 

...

Hey, I don't have a /etc/default/grub !!

I feel cheated. On the other hand my /boot/grub/menu.lst file stile controls all and I am glad of that.

---

### Post by Sub101 on 2009-08-10
> **joepotter said:**
> Hey, I don't have a /etc/default/grub !!

I feel cheated. On the other hand my /boot/grub/menu.lst file stile controls all and I am glad of that.

Youll only have /etc/default/grub if your using grub2.

---

### Post by Rippy on 2009-08-10
Okay... How can I update grub through a livecd, considering my Ubuntu install is toast? I'd rather fix it before I try re-installing Ubuntu again. I'd be able to edit the files fine, but what about "sudo update-grub"? Will that work even on a livecd, or do I need some additional parameter to specify the drive?

Thanks for the help guys. Though I think it's terrible to hide the bootloader menu, especially without giving any warning to the user first... Can't it just detect if you have any other operating systems installed, and if so, show the menu by default?

---

### Post by wayne_cat on 2009-08-10
> **Rippy said:**
> Okay... How can I update grub through a livecd, considering my Ubuntu install is toast? I'd rather fix it before I try re-installing Ubuntu again. I'd be able to edit the files fine, but what about "sudo update-grub"? Will that work even on a livecd, or do I need some additional parameter to specify the drive?

Thanks for the help guys. Though I think it's terrible to hide the bootloader menu, especially without giving any warning to the user first... Can't it just detect if you have any other operating systems installed, and if so, show the menu by default?

From the Wiki ... Recover Grub via LiveCD:

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

