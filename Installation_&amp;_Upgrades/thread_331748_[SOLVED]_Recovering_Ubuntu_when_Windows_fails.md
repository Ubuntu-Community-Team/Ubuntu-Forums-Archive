---
title: "[SOLVED] Recovering Ubuntu when Windows fails"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by raxz on 2007-01-05
Hi all,

I am now quite familiar with Ubuntu thanks to ([psychocats]("http://www.psychocats.net/")) and some internal motivation. 

For reason I'd rather not disscuss, WinXP with service pack2 needs to be re-installed and I belive I can just install winXp without touching ubuntu6.06(have updated it since then but still using the version (?) below edgy).  I have found [this guide]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") But I am afraid I do not understand it fully.

I asked a co-worker and  here is how I think it goes:

1)Install winXP in the partition it was before hda1
2)insert the liveCD and go to the console and type in:

"sudo grub-install/hda" and that should do it? ](*,) 

thanks in advance :)

---

### Post by aysiu on 2007-01-05
I've never actually reinstalled Grub before in Ubuntu, but I think there's an option on the Desktop CD to "repair a Ubuntu installation." If you do that, it'll ask you a bunch of questions as if you're going to install Ubuntu and then give you some options... and one of those options should be to reinstall Grub.

---

### Post by raxz on 2008-01-10
solved...thanks sorry it took soo long to reply but the suggested solution worked.:lolflag:

---

