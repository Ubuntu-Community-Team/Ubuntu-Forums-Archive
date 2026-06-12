---
title: "How to remove windows from dual-boot system"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by markiz on 2010-05-12
Actually, i want to remove kubuntu. But my last post.. nobody gave me an answer :)

The thing is, i'm getting thin on hd space so i have to remove it.
I have read that i could just format linux partition and than boot with windows cd and fix motherboard, but i do not have windows cd on me. Can i use another tool, that would allow me to fix the "damage" grub did? Acronis or something like that?

To avoid to complicated answers, just give me a solution that works without criptic linux commands, i get lost in that.

Also, i hope this post has better luck than the last one.

Also, i am actually a supporter of open source and free software, but i also think that linux is nowhere near being easy to use for the general population, no matter the microsofts conditioning. So i guess ill give it a go at 11.00 again to see whats going on :)

---

### Post by darkod on 2010-05-12
So, if I understood correctly you want to remove kubuntu and you are worried about grub2 remaining on the MBR? You are right, the system will be unbootable if you just delete the kubuntu partition.

From kubuntu in terminal do:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr 
(I assume your hdd is /dev/sda, if other, change accordingly in the command)

Ignore the warnings it will give you. That will write generic MBR on your hdd and after restart it should boot windows directly.

After that you can delete the kubuntu partition and do as you wish with the unallocated space.

PS. You didn't have to change the title of the thread. It's not that we don't reply to threads how to remove ubuntu. It just depends who is online, timezones, etc.

---

### Post by markiz on 2010-05-12
dobro zemljak ;)
yes, you understood me correctly.
if it makes any difference, i have windows 7. will this generic MBR work with it for sure?

---

### Post by Wa1k3rTXRang3r on 2010-05-12
You could also press F8 while booting Windows 7 and choose repair mode and fix the MBR from there by opening the Command Prompt and typing: 

```
bootrec.exe /fixmbr
```

That would repair the MBR. From there, just boot into Windows and delete the Kubuntu partition from Disk Management.

I have done this multiple times for different reasons with no negative effects.

---

### Post by oldfred on 2010-05-12
You should always have another way to boot your computer. I like to have several system rescue type disks as well as my Ubuntu install CDs and now USB flashdrive with ISOs.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently) but can run check disk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

