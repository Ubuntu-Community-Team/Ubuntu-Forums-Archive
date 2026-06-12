---
title: "boot stops before grub unless dvd drive has bootable disk"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by bholtby on 2008-07-14
I'm a newbie (to linux). Installed Poseidon v3 (ubuntu derivative) onto second SATA drive (sdb). First SATA drive (sda) has WinXP. There are als0 two IDE drives. Install went normally without errors. Reboot stopped after the BIOS searched both DVD drives with only a flashing cursor on screen. The machine responds to ctrl-alt-del so it isn't hung just in some error state. The machine is set to boot first from DVD and then from hard disks. I discovered that boot goes to grub and both linux and XP will boot fine if there is a disk in either of the DVD drives-the bios asks if I want to boot from the DVD and if I do nothing grub appears and will boot into either OS. If I reset the bios to first boot from the HD then same result if SATA1 is first but if SATA2 is first then grub returns error 17. Is solution to figure out where grub is installed and then to set that drive first in line for boot? Thanks for any help.

---

### Post by logos34 on 2008-07-14
> **bholtby said:**
> and if I do nothing grub appears and will boot into either OS. 

Which hard disk was set as the boot drive at that point?

---

### Post by bholtby on 2008-07-14
SATA#1, the disk that windows is on is first and then sata#2, the disk that ubuntu is on, then one of the ide drives.

---

### Post by prabbit237 on 2008-07-14
I realize this is off-topic but.....

"Food for thought: "Since the human genome is 3 billion base pairs long, 3 gigabytes of computer data storage space are needed to store the entire genome." "

Even disregarding the 1024!=1000 and also ignoring being able to use a non-lossy compression, you still would only need .75 gigabytes of storage since the genome is base-4 and thus only needs 2 bits/base pair. So a byte can hold 4 base-pair's worth of info.

---

### Post by logos34 on 2008-07-14
> **prabbit237 said:**
> I realize this is off-topic but.....

I'm only quoting the Human Genome Project webpage.  Maybe I'll pull it frm my sig...

---

### Post by logos34 on 2008-07-14
> **bholtby said:**
> SATA#1, the disk that windows is on is first and then sata#2, the disk that ubuntu is on, then one of the ide drives.

Well, one thing we know is your grub files and menu.lst are on the ubuntu drive, in /boot/grub.  But grub stage1 is on the mbr of sata1, and it also appears to be on sata2 mbr because when you boot from that you get a grub error (the Bios location of root partition changes whenever you change the boot order).  

So you could try again booting from sata2, but press 'e' to edit, 'e' again on the root line and change to '(hd**0**,?).  'b' to boot 

More on error 17 [here]("http://users.bigpond.net.au/hermanzone/p15.htm#17").

Or try Super Grub Disk.

---

### Post by Pumalite on 2008-07-14
The chimpanzee genome is 98% identical to a human being.

---

### Post by prabbit237 on 2008-07-15
> **logos34 said:**
> I'm only quoting the Human Genome Project webpage.  Maybe I'll pull it frm my sig...

I just sent them a note via their webpage about it. It'll be interesting to see if they reply/change the website. And now I'll quit the off-topic stuff.

---

### Post by bholtby on 2008-07-15
First, thanks to the folks who discoursed on the chimp's genome-very useful. 

I've tried every conceivable combination of boot ordering and get either a grub error 17 or a stalled boot. I've read dozens of pages of tech talk about grub and tried several suggested fixes with no reward. Supergrub has no difficulty in finding both my windows and ubuntu boot information but can't fix the problem. I've read about the exploits of those hearty tinkerers who struggle to get multidisk systems dual booting. I arrived at the realization that I have neither the time nor the skills to do other than:
1. dig out my XP install disk, boot to the recovery console and fixmbr, and confirm that XP is undamaged (5 minutes).
2. remove ubuntu and reformat the drive for XP (2 minutes)
3. unearth a 1 gHz Athlon that has lots of memory and several large disks (10 minutes)
4. install Poseidon (5 minutes + a coffee break)
5. After less than 1 hour, I now have a fully functioning, reasonably fast, and several hours later still working customized Ubuntu.
6 crack a cold one and reflect on the fact that the genomes of all human monsters and saints are 100% identical.

cheers
4. install Poseidon

---

