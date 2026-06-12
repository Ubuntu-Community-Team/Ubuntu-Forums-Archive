---
title: "Need suggestion on Virtual Machine"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by imjscn on 2008-06-24
I have one harddisk. I'm planning a clean install Xubuntu, after install, I will use virtual machine to run winxp.

I know VM doesn't need a real partition. But, is it more convinient if I plan a partition for the VM during my install of Xubuntu?

Or, maybe I should increase a certain partition size to make the VM running more efficient? Especially, should I increase Swamp partition? I guess when the VM is running, lots of winxp things that not needed can go to the Swamp, and the software I'm using can consume the RAM. Is this guess valid?

Another guess is...VM will leave a big file in the harddisk. Which partition is better for saving this big file?

Thanks!

---

### Post by p_quarles on 2008-06-24
There's no point in creating a separate partition for the virtual machine. If you were going to do that, you might as well dual-boot. The virtual hard drive is one file, which means that it is (for the purpose of backup and filemanagement) as good as having a separate partition.

It's called a *swap* partition (think exchanging and bartering things -- not dense undergrowth), and you don't need to do anything special to this to run a vm. Just make sure it's big enough to store a few tasks that can't stay in memory all the time.

Windows XP can still use a portion of the virtual hard drive as a "virtual" memory space / swap file.

---

### Post by imjscn on 2008-06-24
Thanks. I have 512MB RAM, my Swamp should be more or less 1G. So, how about I increase my Swamp to 2G ? I guess that can help a bit?

---

### Post by cuby on 2008-06-24
Well... I advise you to put the virtual machine image in a different partition. If you need to reinstall the distribution you will need to move a multi-gigabyte file... it is not that elegant.

If you have /home in a separate partition is good enough in there.

512MB ram is low for virtualization, 1GB of swap is good, more swap space is irrelevant for more speed... But is safer... once I crashed my computer because I used to much swap.

The perfect solution: Remember that virtualization is good because you have the 2 systems running simultaneously, so, if you have a spare disk around would be perfect for the image file.

---

### Post by imjscn on 2008-07-12
cuby, you are dam right...512MB is not enough to do serious job in VM. It's just enough to taste how nice the virtualization is. I'd upgrade later. My original RAM is 256 (Dell Demintion2400), I added one peice, now it's 512. If upgrade, what is the proper RAM size?

---

### Post by cuby on 2008-08-18
sorry for the delay...
If you can arrange 2GB would be a must. You will end with 1GB for the base system and the virtual machine.

note: I don't know the maximum memory capacity that you can put in the machine, you must check that in the manual.

---

