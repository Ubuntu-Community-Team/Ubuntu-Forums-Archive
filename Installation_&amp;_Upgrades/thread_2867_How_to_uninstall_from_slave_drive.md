---
title: "How to uninstall from slave drive?"
date: 2004-11-01
forum: Installation &amp; Upgrades
---

### Post by beancounter on 2004-11-01
Good Morning,
I have successfully installed Unbuntu on a clean slave drive whilst having WinXP Pro on my master drive.  I let Unbuntu set up the drive through it's install routine. From what I understand (I'm very much a newbie) the MBR on my master drive was modified to allow dual booting.  Just out of curiosity, how would I go about uninstalling Unbuntu from my system and restore it to it's "original" state?  
I'm not disappointed with Unbuntu, it's just that I want to know  how it's done out of experimental curiosity as a learning exercise.
Thanks in advance for any and all replies and help -- Beancounter

PS -- my system consists of the following:  MSI 6570 mobo with onboard graphics (Nvidia Nforce2 chipset) sound and ethernet controller, AMD Athlon 2400, 512 Mb DDR RAM, WD 10 Gb master drive with WinXP pro, WD 80 Gb slave drive with Unbuntu, LG 4081 DVD / CD drive and Sony 3.5" floppy.

PPS -- Hope I posted this thread in the proper forum --

---

### Post by robert3061 on 2004-11-01
[QUOTE=beancounter]Good Morning,
I have successfully installed Unbuntu on a clean slave drive whilst having WinXP Pro on my master drive.  I let Unbuntu set up the drive through it's install routine. From what I understand (I'm very much a newbie) the MBR on my master drive was modified to allow dual booting.  Just out of curiosity, how would I go about uninstalling Unbuntu from my system and restore it to it's "original" state?  
I'm not disappointed with Unbuntu, it's just that I want to know  how it's done out of experimental curiosity as a learning exercise.
Thanks in advance for any and all replies and help -- Beancounter

PS -- my system consists of the following:  MSI 6570 mobo with onboard graphics (Nvidia Nforce2 chipset) sound and ethernet controller, AMD Athlon 2400, 512 Mb DDR RAM, WD 10 Gb master drive with WinXP pro, WD 80 Gb slave drive with Unbuntu, LG 4081 DVD / CD drive and Sony 3.5" floppy.

PPS -- Hope I posted this thread in the proper forum --[/QUOTE]
 bean counter,
i got back to my xp o/s and I'll monitor your posting from xp. once the duel boot was installed i could get back to xp. i just did not let unbantu reinstall
Bob

---

### Post by Joeb on 2004-11-01
[QUOTE=beancounter]Good Morning,
I have successfully installed Unbuntu on a clean slave drive whilst having WinXP Pro on my master drive.  I let Unbuntu set up the drive through it's install routine. From what I understand (I'm very much a newbie) the MBR on my master drive was modified to allow dual booting.  Just out of curiosity, how would I go about uninstalling Unbuntu from my system and restore it to it's "original" state?  
I'm not disappointed with Unbuntu, it's just that I want to know  how it's done out of experimental curiosity as a learning exercise.
Thanks in advance for any and all replies and help -- Beancounter

PS -- my system consists of the following:  MSI 6570 mobo with onboard graphics (Nvidia Nforce2 chipset) sound and ethernet controller, AMD Athlon 2400, 512 Mb DDR RAM, WD 10 Gb master drive with WinXP pro, WD 80 Gb slave drive with Unbuntu, LG 4081 DVD / CD drive and Sony 3.5" floppy.

PPS -- Hope I posted this thread in the proper forum --[/QUOTE]

You could use any partitioning tool to wipe out the linux partitions created on your slave drive (even the one that's part of Ubuntu's install program).  To restore the original Windows XP bootloader, I believe windows has a program for XP on the CD called fixmbr.  Running that would remove Grub and replace it with the Windows boot loader.

Although I've never used it, I believe you access the program by booting off the Windows XP cd and select restoration console and enter fixmbr there.  That should do it, or so I'm told.

---

### Post by robert3061 on 2004-11-01
[QUOTE=robert3061]bean counter,
i got back to my xp o/s and I'll monitor your posting from xp. once the duel boot was installed i could get back to xp. i just did not let unbantu reinstall
Bob[/QUOTE]
 Matt you geek,
I called Doug and he gave me the exact process to un-install ubantu. Thanks for the help this guy realy knows his stuff, I'll have to remember to call him on any of my other issues.
Bob

---

### Post by FLeiXiuS on 2004-11-01
I would reccomend booting into windows and use a partitioning tool to wipe the entired linux partitions.  (Partition Magic is a good program)

Afterwards, pop in your XP restore cd then reboot.  

Boot from the cd and enter recovery mode.

Once your in there type
```

fixmbr

```

This will fix the mbr to boot to the primary master first.  That should be all.

---

### Post by beancounter on 2004-11-02
Thanks for all the replies.  The help here is fantastic.  Once again I have learned something valuable from the forums.  Thank you again -- Beancounter

---

