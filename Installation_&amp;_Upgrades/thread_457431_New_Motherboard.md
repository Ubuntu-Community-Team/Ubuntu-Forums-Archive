---
title: "New Motherboard"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2007-05-28
I am getting a new board. It uses the same processor and memory as the existing board. Will I have to reinstall Ubuntu or will it work if I connect up the new board with the existing drives, etc.

---

### Post by hardyn on 2007-05-28
it more about the chipset, than the ram and processor... if it has a different chipset, it may be wise to reinstall.

---

### Post by Robbyx on 2007-05-29
Can you give me any guidance as to how to reinstall? Do I have to start from scratch or can I do a repair which would correct the change in chip set and thus save me the problem of having to reformat the HD and remember what extras  I have installed. Will I get away with loading the live CD and trying an install?

My current chipset is via and the new one Nvidia.

---

### Post by tommcd on 2007-05-29
I have read around these forums that if you change motherboards ubuntu will often boot up and work. If it does not, then I think the best option would be a clean install.
EDIT: If it does not work then you may be able to do a "sudo dpkg --configure -a" to get it working.

Just curious, which motherboard are you getting?

---

### Post by Robbyx on 2007-05-29
thanks for the response. I assume that the command line you quote above would be run from the live install disk otherwise how do I get access to the installed version of Ubuntu if it will not load?

I am getting   MSI P6N SLI-FI nvidia 650i Socket 775 ATX

---

### Post by tommcd on 2007-05-29
The nvidia 650i chipset should work well. Phoronix reviewed the Asus P5N sli board recently and everything worked:
[http://www.phoronix.com/scan.php?page=article&item=727&num=1](http://www.phoronix.com/scan.php?page=article&item=727&num=1)
As for running "sudo dpkg --configure -a", if ubuntu won't boot at all I guess you could run it from the live CD after you mount ubuntu like this:
sudo mkdir /mnt/ubuntu
sudo mount /dev/sdaX /mnt/ubuntu (replace X with your root partition)
sudo chroot /mnt/ubuntu
sudo dpkg --configure -a
somethig like that anyway. But if ubuntu won't even boot you may be better off just reinstalling. Good luck with the new motherboard.

---

### Post by Robbyx on 2007-05-29
sudo mount /dev/sdaX /mnt/ubuntu (replace X with your root partition)

Thank you for your helpful replies and the reference to the review. That is a useful site and I wish I had known about it before. 

In the command line quoted above you suggest I replace X with my root partition.  How do I find out what to put there? Presumably I will have to run a terminal command line so that I  know the drive ref.

---

### Post by tommcd on 2007-05-29
To find your root partition just run "cat /etc/fstab".  The root partition will say something like "ext3 defaults,errors=remount-ro 0 1"  (something like that. I'm at work atm). It will also have / as mount point.

---

