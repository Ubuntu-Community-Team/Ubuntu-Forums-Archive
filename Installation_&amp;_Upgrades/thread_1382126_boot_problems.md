---
title: "boot problems"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by debugdom on 2010-01-15
Hello-

I've been running Ubuntu on my netbook now for a little while and its great, the other day I decided to try moblin so I partitioned my drive and installed it however it appears to have messed up my boot flag (I maybe wrong here) because grub isn't showing up and it just boots into moblin. what terminal commands do i need to set the boot back to the grub bit

many thanks in advance

dom

---

### Post by ajgreeny on 2010-01-15
If moblin uses grub2, which I have no idea about it should be possible simply to run update-grub in terminal as root, however you do that in moblin, and the grub.cfg should be updated and then include other OSs on the machine.  If it uses legacy grub, you may need to edit the menu.lst file manually to add ubuntu to it.

Have a look to see if you have a **/boot/grub/grub.cfg** or **/boot/grub/menu.lst** file and then we can go a bit further to help you out.  Also if you run ```
update-grub -v
``` in terminal it should say "1.97...." if grub2 is installed.  You can then try the ```
update grub
```command to see if ubuntu is found and added.

---

### Post by darkod on 2010-01-15
> **debugdom said:**
> Hello-

I've been running Ubuntu on my netbook now for a little while and its great, the other day I decided to try moblin so I partitioned my drive and installed it however it appears to have messed up my boot flag (I maybe wrong here) because grub isn't showing up and it just boots into moblin. what terminal commands do i need to set the boot back to the grub bit

many thanks in advance

dom

I'm worried about "I partitioned my drive". How did you do this? Did you shrink the ubuntu partition? Or you already had unallocated space on the hdd for moblin?

If you did shrink the ubuntu partition, did you shrink the filesystem first? In ubuntu there is different process for shrinking the filesystem first, and the actual partition size after that.

I hope you didn't mess up the ubuntu partition. It could be a simple case of needing to add ubuntu to the grub menu of moblin.

And a word of advice for future: one you have one version of linux and grub already on your hdd, there is NO NEED to install bootloader with any other linux you install. The original existing bootloader can boot it. In fact, with ubuntu 9.10 coming with grub2, all you needed to do was install moblin WITHOUT bootloader, and do update-grub after that.

---

### Post by presence1960 on 2010-01-15
Let's see exactly what you have on that machine. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

