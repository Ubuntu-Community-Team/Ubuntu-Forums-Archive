---
title: "Installing Ubuntu 9.10 With XP installed first."
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by JoeyTrez on 2010-01-15
Hi, I'm sorry if this sounds totally noobish etc, but I am extremely new to Ubuntu.

My friend just helped me re-install XP onto my computer since it was totally bombed.
I want to install Ubuntu with about 25 gigs of space so I can have it as a sorta "backup" and use it for some other things.

The thing is that I'm having trouble with the partitioning.
I know I need to clear up space on my NTFS hard drive thing (70 something gigs) to make room for Ubuntu.

The problem is that it does not allow me to make room. I know I have to boot from the Iso CD, and I have no problem with that. But I know that at a certain point there SHOULD be a slider do-hickey to clear however much room I want. But it never shows up. It says there are 3 partitions:
1) a 31 GB "Dell Utility" thing
2) the 70 gig XP partition.
3) and some other 8 MB one.

I know I have to edit the second one to make room for it, but I never can.

I also tried going to the "try ubuntu without changes" and doing it through the Gparted partition editor, but no dice. It says something about how there is 1 bad sector. Im pretty sure it has something to do with that, but I have NO idea how to fix it.

Any general help at would be immensely appreciated. If you need any more info, I'd be glad to post it. Thanks.

-Joey

---

### Post by darkod on 2010-01-15
You did correct with Try Ubuntu and trying to use Gparted to resize your XP partition. Just one important note: after you do the resize make sure you boot XP few times to make sure it's happy with the resize and to do its disk checks. Otherwise it may create more problems down the line.

Probably the bad sector message is preventing you from doing the resize, you are right. I'm not so sure, because I never needed to use it, but I think Gparted also has check function for the partitions. In Gparted right-click on your XP partition and see which options you get. If there is a check option, do it and maybe it can repair it.

You might also consider booting XP and using the windows command, what was it called 'chkdsk', to check the disk for errors?? Google it.

---

### Post by ssulaco on 2010-01-15
I would defrag XP first before you install Ubuntu,during the installation process of Ubuntu you will use Ubuntu's partitioning tool to make room for ubuntu.........read this:
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1)

---

### Post by darkod on 2010-01-15
> **ssulaco said:**
> I would defrag XP first before you install Ubuntu,during the installation process of Ubuntu you will use Ubuntu's partitioning tool to make room for ubuntu.........read this:
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1)

You don't have to use it during the installation process, you can use Gparted in live desktop mode before that just to do the resize. That's what we are discussing as better option because after you can boot XP few times to do its disk checks after the resize.

If you do it in the single step during the installation, after the resize the ubuntu install goes trough right away, and sometimes XP can make problems for you because it didn't have the chance to do the disk checks after the resize.

---

### Post by ssulaco on 2010-01-15
> **darkod said:**
> 
If you do it in the single step during the installation, after the resize the ubuntu install goes trough right away, and sometimes XP can make problems for you because it didn't have the chance to do the disk checks after the resize.
Sorry for butting in,I didnt look at it that way,Ive always dual booted off 2 drives,my apologies.

---

### Post by darkod on 2010-01-15
> **ssulaco said:**
> Sorry for butting in,I didnt look at it that way,Ive always dual booted off 2 drives,my apologies.

Nothing to be sorry for. Every contribution is welcomed. That's how in these discussions we figure out the best way to do things. :)

And having said that, what's best for one person is not necessarily best for another. :)

---

