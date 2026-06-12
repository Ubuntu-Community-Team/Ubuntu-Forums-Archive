---
title: "Grub-Update Bug for Normal Ubuntu Installation"
date: 2010-12-23
forum: Installation &amp; Upgrades
---

### Post by theasprint on 2010-12-23
Hi,

I understand that Wubi users from 9.10 onwards to the 10.10 version of Ubuntu experience problems where they actually receive a grub update from Synaptic Package Manager and once restarted, the PC shows the grub-rescue message with the UUID.
More info: [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) (courtesy of Rubi1200)

I was just wondering if there will be any Grub2 problems when Grub2 is the main boot-loader and there are Windows and Ubuntu (9.10 onwards, just as previous situation) installed.
That means that the Ubuntu installation is the original installation, not the Wubi type, and it is side-to-side with Windows.

In another context, I was just asking that does the grub update bug that happens to Wubi installations only affect Wubi installations?
 
Are non-Wubi Ubuntu side-to-side installations affected?

Thanks in advance.

---

### Post by Hippytaff on 2010-12-23
> 
In another context, I was just asking that does the grub update bug that happens to Wubi installations only affect Wubi installations?

As far as I know yes ;-)

---

### Post by Rubi1200 on 2010-12-23
Hippytaff is correct. These updates only affect Wubi installs, not a regular Ubuntu install to the hard-drive on a dedicated partition.

Please see my answer in the Wubi Megathread where you also posted.

Thanks.

---

### Post by theasprint on 2010-12-23
Hi,

Thanks for your reply.
So for confirmation, those that install Ubuntu side-by-side Windows via the LiveCD method and not the Wubi method **would not** be affected?

I would really want to confirm this. But so far I see those that have the grub-rescue prompt are Wubi installs and not the Original Installs.

Thanks

---

### Post by Hippytaff on 2010-12-23
> 
those that install Ubuntu side-by-side Windows via the LiveCD method and not the Wubi method **would not** be affected?

correct - not with the same issues, this partitcular problem is a grub & wubi issue only :-)

---

### Post by theasprint on 2010-12-23
Well its OK, just saw your reply Rubi1200.
I think I can stop worrying now, because I didn't use a Wubi install.

---

### Post by Hippytaff on 2010-12-23
Don't panick...
 
When you've broken ubuntu as many times as I have you stop worrying about it so much. If you don't break it you can't fix it ;-)

---

### Post by Rubi1200 on 2010-12-23
You're a funny guy (very presumptuous of me I know) Hippytaff :)

@theasprint:

Two things:

1. the updates affecting Wubi installs sometimes end with the user seeing a grub rescue prompt and sometimes with a regular grub prompt.

I don't know if there is necessarily a pattern to this.

2. Again, if you did not install Ubuntu via Wubi, you have nothing to be concerned about.

If you would like to learn more about your particular setup and what everything means, run the boot info script linked at the bottom of my post. You can do this either from within Ubuntu or from a LiveCD.

Post the results into a PM to me and I will explain it to you.

---

