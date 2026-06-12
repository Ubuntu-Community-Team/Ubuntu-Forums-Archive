---
title: "grub only boots to prompt (grub&gt;)"
date: 2019-06-02
forum: Installation &amp; Upgrades
---

### Post by aryehweiss on 2019-06-02
After attempting to install POP OS, boot will only produce the grub> prompt.

I can boot ubuntu manually  from this prompt using

linux (hd0,gpt5)/vmlinuz root=/dev/nvme0n1p5
initrd (hd0,gpt5)/initrd.img 
boot

Here is the URL that boot-repair created
[http://paste.ubuntu.com/p/3F85D8nnzp/](http://paste.ubuntu.com/p/3F85D8nnzp/)

I tried doing boot-repair -- it did its things, but I still have this problem

/dev/nvme0n1p1 is an EFI sysatem partition (fat32)
/dev/nvme0n1p2 is ext4 /boot/efi (where boot-repair said it put grub
/dev/nvme0n1p3 is a Windows7 ntfs partition that I can boot to if I interrupt the boot process with F12 and select the windows boot manager
/dev/nvme0n1p4 is a Lenovo recovery partition
/dev/nvme0n1p5 is the ubuntu root partition that I can boot from manually as described above
/dev/nvme0n1p6 is a swap partition

Obviously is it is a pain to have to boot linux from the grub command prompt. Any help in how to set this up correctly will be greatly appreciated. 

Tnx in advance
--aryeh

---

### Post by yancek on 2019-06-02
It looks like you have windows  7 installed in EFI mode.  Is Ubuntu also EFI?  Mount /dev/nvme0n1p1  and take a look to see if you have an ubuntu directory there with EFI files.  
Where (which partition) did you try to install Pop OS?  You have 2 EFI partitions which will create problems and the working one is likely the first partition which is why you need to mount it and look at the contents.  The first partition has your windows EFI files and likely Ubuntu also, veriify that and if that is correct, remove the second partition.  Not clear where you tried to install Pop OS?

In almost all cases, boot repair shows more info than your output has produced, specifically the grub.cfg file which does not show at all.

---

### Post by aryehweiss on 2019-06-02
Thank you for your reply.
I deleted the second partition. This did not fix the grub issue, but it caused Windows to fail to start.

POP OS was installed on the p5 partition.

The automatic recovery  tools failed to restore the windows startup, so i will need to do a Lenovo product recovery and start again.

---

### Post by oldfred on 2019-06-02
The report is not quite as good with NVMe drives but still useful.
       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

Boot-Repair's report uses bootinfoscript for first part of report & that has not been updated for NVMe drives. A user posted the fix in a bug report, but it has not been updated. Would you run the posted version just to test it works? See post by baedacool. If too long to post here, manually copy to pastebin site & post link to it.

[https://github.com/arvidjaar/bootinfoscript/issues/5](https://github.com/arvidjaar/bootinfoscript/issues/5)

---

### Post by aryehweiss on 2019-06-02
Again, thank you for you reply.
Once the installed windows systems and Lenovo recovery got toasted, I just did a clean install (wiping out everything on that disk).
That worked fine, but it means I cannot go back to see what might have worked. Fortunately, i did not have anything irreplaceable on that disk.

However, the I will be getting a new Lenovo X1, which will come with Windows preinstalled, and on that one I will try to maintain the installed Windows and install POP-OS next to it, so the links in your post may prove useful for that.

---

