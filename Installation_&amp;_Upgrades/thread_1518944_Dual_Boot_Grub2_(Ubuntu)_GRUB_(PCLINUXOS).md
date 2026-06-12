---
title: "Dual Boot Grub2 (Ubuntu) GRUB (PCLINUXOS)"
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by neu5eeCh on 2010-06-27
Hi Folks,

I'm using a second partition for exploring distros and I enjoy learning from distros that are "far" removed from Ubuntu (someday I'll work up to Linux from Scratch). Right now, I'm trying out PCLINUXOS with E-17.

When I update GRUB2, it picks up the wrong partition from GRUB. Here's the problem:

> menuentry "linux (on /dev/sda9)" --class mandrake --class os --group group_/dev/sda9 {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 51523a32-585c-4c61-80c5-30ddf27cbf1e
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=51523a32-585c-4c61-80c5-30ddf27cbf1e resume=UUID=ecf7177a-e39f-44a5-b0f0-aa63917df99a splash=silent vga=788
    initrd [COLOR=DarkRed]**(hd0,8 )**[/COLOR]/boot/initrd.imgThat last line *should* read: (hd0,**[COLOR=DarkRed]9[/COLOR]**)

Question: What's the most elegant solution to this? The first is to change grub2 to grub (but I like grub2). Another involves adding a manual entry (40_custom), but this doesn't remove the incorrect entries from the grub menu. Another solution is to make OS Prober non-executable, among other files, making the updating of grub2 completely manual.

Any other solutions out there? Just curious...

---

### Post by darkod on 2010-06-27
Do you have separate /boot partition for PCLinux? If you do, it should be right because the kernel files will be on the /boot partition.
You can run the boot info script from my signature and see what is where. No need to post the results here unless you have questions.

---

### Post by oldfred on 2010-06-27
It is just part of grub's osprober copying the boot info from a system that uses grub legacy and grub legacy uses a different partiiton numbering.

I would use the 40_custom version to update but the entry of (hd8,0) is not required even with old grub. You could try editing the menu.lst of PCLINUXOS to just remove that part of the entry. You can manually edit it once to boot using e on the menu and scroll down and just remove it. Once in your system edit the menu.lst to remove the entry. Then when you update grub2 in ubuntu it should not find it. (until next time you update PCLINUXOS). Not sure if there is a setting to remove it always.

---

### Post by neu5eeCh on 2010-06-27
Thanks for both your responses. To answer the first, first. No, I don't have a separate boot partition. I thought of that approach, but what I did was to let PCLos over-write the MBR. Then used Super Grub Disk to boot back into Ubuntu, then updated the MBR with Grub2. Don't know why, but thought that technique might short-circuit some of these issues. It didn't. Olfred's solution sounds like a good one. I think I'll try that.

As it is, I edited the CFG file. That should be good until I update GRUB2 (or, in my case, BURG).

---

### Post by kalwisti on 2010-06-28
> **oldfred said:**
> It is just part of grub's osprober copying the boot info from a system that uses grub legacy and grub legacy uses a different partiiton numbering.

I would use the 40_custom version to update but the entry of (hd8,0) is not required even with old grub. You could try editing the menu.lst of PCLINUXOS to just remove that part of the entry. You can manually edit it once to boot using e on the menu and scroll down and just remove it. Once in your system edit the menu.lst to remove the entry. Then when you update grub2 in ubuntu it should not find it. (until next time you update PCLINUXOS). Not sure if there is a setting to remove it always.

Many, many thanks to oldfred for this tip. His advice worked great in my similar situation: a Linux dual-boot, with Lucid Lynx on /sda and PCLinuxOS Phoenix (Xfce edition) on /sdb. As in VTPoet's case, I could not boot PCLOS from the main GRUB2 menu. (Although there was an entry in the menu, it had picked up incorrect partition information.)

My PCLOS installation's root partition is located on /sdb10 [*(hd1,10)* in GRUB2 notation]. That was identified correctly; however, there was a mistake in the final line of the stanza:

```
initrd (hd1,9) /boot/initrd.img
```

As oldfred noted, the *(hd1,9)* is notation from Legacy GRUB and it is not required here ...

In case this will help someone else in the future, here are the steps I followed to fix this. I'm relying on memory, but I believe that this information is accurate:


1. I rebooted the computer to get to the main GRUB2 menu. 

2. I found the entry for PCLOS which had been created by GRUB2's osprober. I chose "e" from the menu to edit this entry.

3. I scrolled down to the line containing *initrd (hd1,9) /boot/initrd.img* and deleted the "(hd1,9)" portion from it.

4. I typed Control-X [?] to try and boot the entry.

5. Joy! It booted successfully.

6. I decided to try editing the menu entry for a permanent fix. To do this, I first used gedit to copy the originally created PCLOS stanza from /boot/grub/grub.cfg. (I saved it to a temporary file in my /home folder).

**Note**: I did **not** edit grub.cfg in any way; I only copied the relevant PCLinuxOS entry from it.

7. Again using gedit, I opened the 40_custom script file found in /etc/grub.d/ 

8. I pasted the PCLOS GRUB2 stanza which I'd just copied into the 40_custom file.

9. I deleted the "(hd1,9)" partition reference from the initrd line and saved the file.

10. I updated GRUB2 by typing ```
sudo update-grub
``` in a Terminal.

11. I rebooted the machine to double-check whether a new custom entry had been added for PCLinuxOS, and whether it booted correctly. Yay! It did.

HTH. Kudos to oldfred for his GRUB2 knowledge.

---

### Post by BigSilly on 2011-03-19
I'd like to thank everyone involved in this thread for demystifying GRUB2 a little for me and allowing me to boot successfully into my PCLinuxOS easily. Brilliant!

However, I'm bumping this thread also because I need a little further help. I've successfully reinstated a working PCLinuxOS entry as I say thanks to the above assistance, but after running sudo update-grub the older and non-functioning PCLinuxOS entry is still showing in the GRUB menu at boot as well as the second correctly working one. How would I go about removing the older entry? Thanks. :)

---

### Post by miltonsj on 2012-02-02
This was an absolute life saver for me as well. I stumbled onto this site looking for this exact solution. Kudos to everyone who participated! :D

---

