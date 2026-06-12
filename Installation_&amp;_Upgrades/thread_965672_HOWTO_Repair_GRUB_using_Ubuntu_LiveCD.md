---
title: "HOWTO: Repair GRUB using Ubuntu LiveCD"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by RPDiep on 2008-10-31
Repairing/Reinstalling GRUB using Ubuntu LiveCD 
(using info from txuk, [http://ubuntuforums.org/archive/index.php/t-210820.html]("http://ubuntuforums.org/archive/index.php/t-210820.html"))

Sometimes you accidentally overwrite your MBR, leaving your system unbootable.
Here's how to fix that situation, with the Ubuntu LiveCD.

Step 1. Boot your LiveCD. Should not be too hard ;)

Step 2. Determine what drive partition the root partition is of your installed system.
	If you know how to, just do that. If not, here's an easy way to do it. Go to Places -> Computer.
	Rightclick on your drive and click "Mount volume". Open up a terminal and type "mount".
	Usually, the last lign appearing contains the name of your partition. 
	For example : "/dev/sda3 on /mnt/disk type ext3 (rw,relatime)" <--- /dev/sda3 is your drive here.
	Now unmount it again by typing "sudo umount /dev/sda3" (or whichever is your partition)

Step 3. Open up a terminal (Accessories -> Terminal). Change to the root by typing "cd /".
	Make a directory "mountedsystem" (sudo mkdir mountedsystem), and mount your partition here:
	"sudo mount /dev/sda3 /mountedsystem" 
	
Step 4. Mount your proc and dev directories in the mounted system:
	"sudo mount -o bind /proc /mountedsystem/proc" and "sudo mount -o bind /dev /mountedsystem/dev"

Step 5. Change the root to your mounted system:
	"sudo chroot /mountedsystem" 

Step 6. Now reinstall GRUB by using the following command:
	"sudo grub-install /dev/sda" <- that's your partition name minus the number.

This is how I got my system back running after installing Windows XP.

Good luck!

---

### Post by lockettowl on 2009-03-23
OK, I did this and got to the last step:
> sudo grub-install /dev/sda
And got:
> Your /usr is broken; please fix it before calling this wrapper!
What do I do next?

---

### Post by ambdeep on 2009-03-23
> OK, I did this and got to the last step:
Quote:
sudo grub-install /dev/sda
And got:
Quote:
Your /usr is broken; please fix it before calling this wrapper!
What do I do next?
you have to put a number after sda to select the drive you want to install it in......if you are not using dual boot i suggest sda1....but if you are then you should do it on hda0 or what ever you motherboard's address is.

---

### Post by lockettowl on 2009-03-23
I tried this, still get the same error

---

### Post by ambdeep on 2009-03-23
then the problem doent lie in GRUB but in the OS.....you will probably need to format it.

---

### Post by lockettowl on 2009-03-23
how do i do that from the live cd? (I can't boot from my hard drive)

---

### Post by ambdeep on 2009-03-23
just reinstall overwriting the current OS using the install option....you will loose all your current data though.

---

### Post by lockettowl on 2009-03-23
Is there no way to get to that data first and put it in a safe place (e-mail it to myself) then reinstall?

---

### Post by ambdeep on 2009-03-23
by data if you meen the currently installed software.....im not aware of any such method but if you meen music, movied and other stored data then just boout from the live cd, mount your drive and simply copy it onto a pen-drive or any portable media......if you have this data stored on another drive..then you need not format it(that is that drive only) if the default in the install suggests a format then you can bypass it by using a manual install.

---

