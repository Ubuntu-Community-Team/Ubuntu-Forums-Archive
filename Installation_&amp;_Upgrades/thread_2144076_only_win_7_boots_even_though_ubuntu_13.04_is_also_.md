---
title: "only win 7 boots even though ubuntu 13.04 is also installed"
date: 2013-05-11
forum: Installation &amp; Upgrades
---

### Post by Fred4106 on 2013-05-11
I did install it to seperate partitions, because i dont want the too systems interacting with each other, (unless im adding/removing files from the windows partitions from the linux side).

I found this question, [http://askubuntu.com/questions/291519/i-have-recently-installed-ubuntu-13-04-dual-booting-with-windows-7-but-cant-lo](http://askubuntu.com/questions/291519/i-have-recently-installed-ubuntu-13-04-dual-booting-with-windows-7-but-cant-lo) which leads to this guide, [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) which says generate the boot info [http://paste.ubuntu.com/5653461/](http://paste.ubuntu.com/5653461/) and get someone who knows what there doing to help you.

Thanks.  Sorry if this is a stuipid question.

---

### Post by oldfred on 2013-05-11
If you want to use EasyBCD, I suggest you use their forums.
 [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

We prefer grub as it is designed for multi-booting. Your EasyBCD actually has to use the old grub for Windows grub4dos to work around that Windows does not multi-boot anything other than another Windows.

You can just use Boot-Repair suggested fix of installing grub2 to the MBR.

---

