---
title: "Can I install Vista (Ubuntu already installed)"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by onlyonehere on 2008-03-30
Hi, there. I am a beginning user of Ubuntu. I bought a new hard disk drive and I installed Ubuntu firstly. The "/" and the "swap" were both installed in the two primary partitions. Now, I want to install Windows Vista Home Premium in the third primary partition and then make dual-boot Ubuntu/Vista. I don't know whether I can install Vista successfully.

I don't want to install Windows Vista firstly. So I ask a question here. I must install Ubuntu firstly and I did it.

After installing Windows Vista, can I reinstall Ubuntu to rewrite GRUB? I don't want to use LiveCD to rewrite GRUB.

I just want to know whether I can install Windows Vista on my disk drive which was installed Ubuntu firstly. And I also want to know whether I can reinstall Ubuntu to make dual-booting.

I hope you can tell me if you know how to do it.

I really want to know the answers. I am so confused because of this problem.
 
Thank you very much.

---

### Post by A$h X on 2008-03-30
Both vista and XP will overwrite GRUB. It seems a little over-zealous to completely re-install ubuntu just to get GRUB back, it's the same thing just to use the live CD to re-install GRUB, try it out, you won't lose vista's entry in the boot table.

---

### Post by pasmeh on 2008-03-30
heh, iv tried that a few times and i always stuff my windows install. I would recommend wiping HDD, install vista and then install Ubuntu.

---

### Post by Del Piero on 2008-03-30
Another good reason why people should stop using GRUB!

If you have LILO installed on your Ubuntu partition instead of the MBR and GAG as your main boot loader you won't have to worry about anything, you'd be able quad boot remove whatever or add whatever without worrying about stupid GRUB.

---

### Post by housam on 2008-03-30
> **onlyonehere said:**
> Hi, there. I am a beginning user of Ubuntu. I bought a new hard disk drive and I installed Ubuntu firstly. The "/" and the "swap" were both installed in the two primary partitions. Now, I want to install Windows Vista Home Premium in the third primary partition and then make dual-boot Ubuntu/Vista. I don't know whether I can install Vista successfully.

I don't want to install Windows Vista firstly. So I ask a question here. I must install Ubuntu firstly and I did it.

After installing Windows Vista, can I reinstall Ubuntu to rewrite GRUB? I don't want to use LiveCD to rewrite GRUB.

I just want to know whether I can install Windows Vista on my disk drive which was installed Ubuntu firstly. And I also want to know whether I can reinstall Ubuntu to make dual-booting.

I hope you can tell me if you know how to do it.

I really want to know the answers. I am so confused because of this problem.
 
Thank you very much.


you can always[[COLOR="Red"]_ fix ubuntu after installing windows _[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub")

---

### Post by drhou on 2008-03-30
> **onlyonehere said:**
> I just want to know whether I can install Windows Vista on my disk drive which was installed Ubuntu firstly. And I also want to know whether I can reinstall Ubuntu to make dual-booting.


Check this website out, it may have the answer to your question;):

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

---

