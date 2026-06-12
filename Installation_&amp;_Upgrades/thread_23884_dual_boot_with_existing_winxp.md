---
title: "dual boot with existing winxp"
date: 2005-04-04
forum: Installation &amp; Upgrades
---

### Post by jkndrkn on 2005-04-04
My exposure to unix in school has led me to an interest in linux. I decided on ubuntu since it boasted a gentler learning curve than other linux distributions.

My first install of ubuntu went poorly, as my Grub seemed to have become corrupted and I was unable to boot into windows xp or ubuntu.

I am following some of the hints and procedures here:

[http://www.ubuntulinux.org/wiki/WindowsDualBootHowTo/view?searchterm=dual%20boot](http://www.ubuntulinux.org/wiki/WindowsDualBootHowTo/view?searchterm=dual%20boot)

This is my hard disk layout.

hd0 20gb with winxp using 5gb
hd1 80gb with softs installed to winxp and media using 40gb
hd2 120gb with media using 50gb

My first attempt at a dual-boot install was to partition hd2 for linux, the linux swap file, a fat32 region for sharing data, and the remaining partition in ntfs for use by windows.

After regrouping and doing a little more research, I've decided that the best route would be to use partition magic to split up hd0 into partitions to for the existing windows installation, the linux partition, the linux swap file, and the fat32 datashare.

I want to use winxp's boot loader and not grub, since winxp will be my main OS (at least for now).

Is this a good course to take? Any special considerations I should be making? Any advice? Is there a free utility that I can use to _safely_ resize ntfs partitions that contain data?

I'm excited about my install. Hope I haven't asked too much, and thanks in advance for any advice.

---

### Post by grendelkhan on 2005-04-04
Resizing NTFS partitions is dicey although Partition Magic has always done a nice job if you just sit back and let it go.

My advice would be setting up at least a root partition (mounted under "/"), swap and a seperate /home.  This last part is an AMAZING innovation that will let you in a flash reload your entire system and still keep all your personal settings.

Honestly, GRUB can maintain your bootloader duties fairly well.  And with a seperate /home partition, you can always use XP to fix the MBR and then reload linux and be back to the races in less than an hour.

---

