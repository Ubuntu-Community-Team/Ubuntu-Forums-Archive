---
title: "Upgrade to Natty with Dual-Boot System"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by coljohnhannibalsmith on 2011-04-28
Hello,

I have  a dual boot Windows 7 / Lucid x64 System with Apache & Tomcat.

Can I upgrade with Update-Manager or will I have to rebuild the system from bare-metal?

It was a nightmare upgrading to Lucid with my Dual-Boot configuration, as I was asked when reinstalling GRUB, where I wanted to install the boot-loader.  I chose the wrong answer, which made my system unbootable; and I had to rebuild from scratch.  From now on, I always check 'all' the boxes, and let Update-Manager install the boot-loader everywhere, even where it doesn't belong.  That way I'm relatively certain to have a bootable system after an upgrade to GRUB.  I wish the install script would just *'read'* where the bootoader is located, and reinstall it in the same location, rather than offering me the 'opportunity' to hose my OS.

I wouldn't be a bit surprised if there are several problems with the upgrade; such as the repositories 'not' being fully populated, like with Lucid.

In any event, my biggest fear is that the upgrade to Natty will hose my Dual-Boot config.  Can anyone tell me if I'll be Ok or 'not,' and what other issues I should look-out for?



Thanks, Hannibal

---

### Post by Blasphemist on 2011-04-28
I also have dual boot and a development environment with apache and tomcat and all went well for me. I was at maverick not lucid though. You may want to use the cd and I think that will not give you issues with the dual boot. As for the web server, I expect that to be fine as well. I didn't use a cd to go to alpha natty and then did use a cd to go to beta 2 so I've done both.

---

### Post by coljohnhannibalsmith on 2011-04-28
Sorry,

I'm on "Maverick."  Thanks for the reply.



Hannibal

---

### Post by oldfred on 2011-04-28
Do not install grub to all. You will hose windows boots. It should just be installed to the MBR of the drive you boot or the drive with Ubuntu and make that the boot drive.

I upgraded from 6.06 to 9.04 every 6 months. Often had issues. But wanting ext4, grub2 and 64 bit I had to do a clean install of 9.10. I have done clean installs ever since but found that you have to have more than just /home to make it easy. Programs, some system settings, some sources may be copied, but usually require new versions, so you cannot just copy.

I had a new drive when I installed 9.10, so I kept 9.04 and now have 3 / (root) partitions that I use - Current, old & beta/alpha. Then I know new version works for me, before fully converting and I have old version to get info from or in an emergency boot.

---

### Post by coljohnhannibalsmith on 2011-05-01
> **Blasphemist said:**
> I also have dual boot and a development environment with apache and tomcat and all went well for me. I was at maverick not lucid though. You may want to use the cd and I think that will not give you issues with the dual boot. As for the web server, I expect that to be fine as well. I didn't use a cd to go to alpha natty and then did use a cd to go to beta 2 so I've done both.

Finally got up the courage to perform the upgrade, and Apache & Tomcat were unaffected, just like you stated.  ***Thank God for that!***

Anyway, I had *lots* of other problems, such as discovering that ***Unity is a POC!!!***  What a nightmare it was to go back to Gnome, and get my 'Desktop_Cube' back.  Also *Tork*, which I much prefer over Vidalia, since it allows *complete* control over you're spoofed location, and the relays you use, was removed without warning.  And Natty doesn't allow 'conky' to read 'acpitemp;' so I'm stuck guessing whether or not my rig is going to overheat. ***Not fun!***




Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2011-05-01
> **oldfred said:**
> Do not install grub to all. You will hose windows boots. It should just be installed to the MBR of the drive you boot or the drive with Ubuntu and make that the boot drive.

I upgraded from 6.06 to 9.04 every 6 months. Often had issues. But wanting ext4, grub2 and 64 bit I had to do a clean install of 9.10. I have done clean installs ever since but found that you have to have more than just /home to make it easy. Programs, some system settings, some sources may be copied, but usually require new versions, so you cannot just copy.

I had a new drive when I installed 9.10, so I kept 9.04 and now have 3 / (root) partitions that I use - Current, old & beta/alpha. Then I know new version works for me, before fully converting and I have old version to get info from or in an emergency boot.

Hey *oldfred* thanks for the reply,

You're right, ***what I really should do,*** is crank up 'gparted' to see which partition actually has the 'boot-flag,'  and install 'grub' to that partition only.  I just got nervous after botching my upgrade to Maverick.  I had Lucid installed on several different partitions, with several different file systems, for increased performance; and this exacerbated my problems.  Frankly, I think this separate-partition thing is going to go-away soon, since the prices of SSDs are coming down, and should be affordable within the next 3 years, by my estimation.  Also, ***EXT4 is pretty-snappy!***  It's a lot faster than EXT3, that's why I formatted / as EXT2, for Lucid.  I'm not doing all that now.  It just makes upgrading nigh-on to impossible, and the tiny extra performance margin just isn't worth that kind of extra trouble to me.

BTW, I have a different strategy for system recovery.  I simply clone my system drive about once a month, and revert to that, in the event of a system failure. Not the most elegant solution; ***but it works!***




Thanks, Hannibal

---

### Post by oldfred on 2011-05-01
Still no. Boot flag is used by windows (active partition) and again installing grub to the windows partition wipes out essential windows boot code in the partition boot sector.

Windows has to have a boot flag to use its boot loader, to install or to make repairs to a windows primary partition. Some BIOS require a boot flag on a primary partition just to boot even if you do not have windows. But grub does not use the boot flag.

---

### Post by coljohnhannibalsmith on 2011-05-02
Actually, I'm using GRUB to load Windows and Ubuntu, not the Windows boot-loader...

That's just how my dual-boot system got configured.  I installed Windows 7 first & then Ubuntu and I boot both under GRUB.

I suspect most dual-boot systems load Ubuntu with Windows-Loader.  This was how my first dual-boot system with Vista/Gusty worked.  It's the reverse now...

---

