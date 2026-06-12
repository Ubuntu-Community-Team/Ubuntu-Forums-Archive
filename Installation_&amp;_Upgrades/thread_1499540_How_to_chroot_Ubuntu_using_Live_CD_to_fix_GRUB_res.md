---
title: "How to chroot Ubuntu using Live CD to fix GRUB rescue prompt"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by swamytk on 2010-06-02
Recently I messed up GRUB boot loader in my laptop installed with Ubuntu which resulted in grub rescue prompt. So I had to boot Ubuntu Live CD to get it fixed. Thought of blogging it, may be useful for some one.

This fix involves two steps. First one is to chroot into Ubuntu installation partition. Second one is to install the grub MBR (Master Boot Record). I am using Ubuntu Lucid 10.04 and Live CD also of same.

Continue reading here: [http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/](http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/)

---

### Post by tommcd on 2010-06-02
Glad you found the solution.
For future reference, this stuff is covered in the Ubuntu wiki:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
It is not really necessary to chroot to the Ubuntu install on the hard drive to reinstall grub2 to the MBR. See this:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
There is (apparently) more than one way to reinstall grub2.

---

