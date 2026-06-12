---
title: "Installed Ubuntu but it won't boot"
date: 2016-09-23
forum: Installation &amp; Upgrades
---

### Post by sbrail2 on 2016-09-23
As the title says, I've been trying to figure this out for two days now and just can't. I installed Ubuntu 16.04.1 LTS but it just doesn't boot. I've tried literally everything I've seen in every forum post and nothing yet so here I am.

I've tried boot-repair and everything.

Sorry guys, total Linux newbie

**[http://paste2.org/WjX6nacp](http://paste2.org/WjX6nacp)**

---

### Post by oldfred on 2016-09-23
Is this a hybrid drive or Intel SRT based system with small SSD as sdb & main drive as sda?

You show sda as MBR(msdos) but sdb as gpt with an UEFI install of Ubuntu.

Issue is that grub only installs in UEFI mode to ESP- efi system partition on drive seen as sda.
You best to convert sda to gpt and add an ESP.
I might also delete swap on sdb, as not needed. Make / slightly bigger. And maybe delete swap on sda, create ESP on sda and add anew swap at end of sda drive of 2 or 3GB which will probably never be used. You may have to edit fstab with new UUIDs of swap(s).

---

### Post by sbrail2 on 2016-09-23
I don't know how to do any of what you just said

---

### Post by RobGoss on 2016-09-23
Hello and welcome, is Ubuntu the only OS on this machine?

Tell us what you did when you installed Ubuntu on this machine it would help us figure how to approach this problem

**Oldfred **has given some good tips to get you started with this issue. If you're new to Ubuntu which it appears you are you might want to do some reading before you jump in the Ubuntu waters, it can be tricky for new users. I think what Oldfred is asking you is your machine** UEFI** or** BIOS,** this makes a big different when you're installing Ubuntu or other Linux distructions

---

### Post by sbrail2 on 2016-09-23
Yes Ubuntu is the only OS because in trying to install it, I wiped Windows (oops) so now I'm desperately trying to get this to work

I don't know whether it's UEFI or BIOS, to be honest... It's an HP Envy, if that helps?

---

### Post by RobGoss on 2016-09-23
> **sbrail2 said:**
> Yes Ubuntu is the only OS because in trying to install it, I wiped Windows (oops) so now I'm desperately trying to get this to work

I don't know whether it's UEFI or BIOS, to be honest... It's an HP Envy, if that helps?

In your first post you don't mention what method you're trying to install Ubuntu **USB** or **DVD**, In my option **USB **is the best way to go if your machine is able to boot from it. Are you able to boot in to the Live desktop environment?



[FONT=InconsolataMedium][COLOR=#282828][/COLOR][/FONT]

---

### Post by sbrail2 on 2016-09-23
Yeah it's through bootable USB and yes I've been doing things through the live desktop

---

### Post by oldfred on 2016-09-23
Since you erased just about everything on sda, you need to convert it to UEFI and use gpt partitioning. And then add an ESP - efi system partition which is fat32 formatted with the boot flag.

        I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... 

 MBR or gpt partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 
      
 Also links to more info
[http://gparted.org/documentation.php](http://gparted.org/documentation.php)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Then use Boot-Repair to totally reinstall grub2 from advanced options.

---

