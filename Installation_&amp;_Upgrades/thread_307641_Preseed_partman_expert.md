---
title: "Preseed partman expert"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by kha on 2006-11-26
Hello !

I am currently making an install server to install some other servers (network auto install).

I am using a DHCP server serving boot files through TFTP then preseed files so that ubuntu installs automatically.

I am using Ubuntu Edgy.

But i am stuck in configuring the partition schema : i do not want to use auto partitionning : i just want a swap partition and another partition (in reiserfs) for the whole system.

I searched two days on internet and the only thing i found is this example :

==============================================================
#d-i	partman-auto/expert_recipe	string boot-root :: 20 50 100 ext3 $primary{ } $bootable{ } method{ format } format{ } use_filesystem{ } filesystem{ ext3 } mountpoint{ /boot } .  500 10000 1000000000 ext3 method{ format } format{ } use_filesystem{ } filesystem{ ext3 } mountpoint{ / } .  64 512 300% linux-swap method{ swap } format{ } .
# For reference, here is that same recipe in a more readable form:
# 	boot-root ::
# 	40 50 100 ext3
#		$primary{ } $bootable{ }
#		method{ format } format{ }
#		use_filesystem{ } filesystem{ ext3 }
#		mountpoint{ /boot }
#	.
# 	500 10000 1000000000 ext3
#		method{ format } format{ }
#		use_filesystem{ } filesystem{ ext3 }
#		mountpoint{ / }
#	.
# 	64 512 300% linux-swap
#		method{ swap } format{ }
#	.
==============================================================

Can someone could explain me or indicate me some documents to have more help about teh syntax, the meaning to the numbers and arguments ?

Thank you for your help !

---

### Post by kha on 2006-11-27
i finally found this... I will try with it :)

[http://svn.debian.org/wsvn/d-i/trunk/installer/doc/devel/partman-auto-recipe.txt?op=file&rev=0&sc=0](http://svn.debian.org/wsvn/d-i/trunk/installer/doc/devel/partman-auto-recipe.txt?op=file&rev=0&sc=0)

---

