---
title: "Add to Windows computer not dual boot"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by Musket on 2011-05-14
I have a windows 7 computer and want to try Ubuntu 11.04. I have created a boot CD and tried it out and it seems to recognise all my hardware and I would like to install it on a spare 250gig hard drive.

I do not want to go for wubi or dual boot as I don't want to risk my windows boot sector. I am able to select a drive at boot time with the F8 key. 2 questions.

1. Can I do a clean install and leave my windows installation alone and put ubuntu on a spare drive.

2. If it is possible can I just go for it of would it be wise to unplug my windows drive first.

Thanks
Tony

---

### Post by YesWeCan on 2011-05-14
Always a good idea to unplug the windows drive and any others first.

Then just do an install to your spare HD and choose "use whole disk" for the simplest install.

After install, shut down. Then reconnect the Windows HD. Boot and go into the bios settings and tell it to make the Ubuntu HD the first in boot order. It will now boot Ubuntu.

Now, in Ubuntu, do all updates and reboot if asked. Then you need to add Windows to the Grub menu so you get a choice of OS next time you reboot. Open a terminal and type 'sudo update-grub' and enter your password.

That's it. :)

[the reason it is a good idea to unplug Windows HD is to guarantee not to accidentally damage it and because Ubuntu's installer defaults to putting Grub on sda, which is likely your Win HD, and it is not always obvious how to change this to install Grub to your Ubuntu HD. With no Win HD and no other HDs Ubuntu installer has no choice but to use the right HD.]

---

### Post by MAFoElffen on 2011-05-14
> **Musket said:**
> I have a windows 7 computer and want to try Ubuntu 11.04. I have created a boot CD and tried it out and it seems to recognise all my hardware and I would like to install it on a spare 250gig hard drive.

I do not want to go for wubi or dual boot as I don't want to risk my windows boot sector. I am able to select a drive at boot time with the F8 key. 2 questions.

1. Can I do a clean install and leave my windows installation alone and put ubuntu on a spare drive.

2. If it is possible can I just go for it of would it be wise to unplug my windows drive first.

Thanks
Tony
#2 - Yes, safest.
#1 - Yes, if you do #2.

If you later decide to make it dual-boot, you could then either use the Winodws Boot manager or Grub.  If you choose grub, I find it safer in the long run to move/resize the Win partition to start on the 2nd sector of the HDD (leaves plenty of run for a boot manager).

---

### Post by Musket on 2011-05-14
Thanks both, I will give it a try. I may come back on the grub thing to load windows as well. I am definitely a linux newby

Tony

---

### Post by Dreigo42 on 2011-05-16
If update-grub was run after plugging the windows drive back in, it is already set to dual-boot using grub right? Windows should have been added to the Grub confinguration. I would imagine that it is a dual boot using grub while the Ubuntu drive is the primary boot drive and the Windows drive remained untouched because grub was installed on the Ubuntu drive.

---

### Post by Musket on 2011-06-02
Thanks YesWeCan and MAFoElffen, I have done as recommended and now have a working Linux. It has not affected my windows installation and the computer boots into windows as normal without a dual boot menu. If I want Linux I press F8 at the bios screen and I am given a selection of drives to boot from.

I will leave it like this for a bit as I am wanting to learn Linux which looks a bit of a steep learning curve. If and when I start using it more seriously, I will try the option of setting the bios to boot directly to the Linux drive and modify the Linux boot loader (grub?)

I have loads of questions but I guess they are not installation issues so I will post in another section. My first query is that when I booted from the CD, I was able to view both of my monitors. My installation to a hard drive does not see my second monitor.

Again, thanks you both for your assistance.

Tony

---

