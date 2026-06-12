---
title: "Newbie ...pls help"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by tzufli on 2010-01-04
Hello,

this my first time in ubuntu so please bear with me.

I have a 64 bit machine, amd phenom 9950, 16 gb ram, nvidia 9600, 
with on hdd 400 GB with 3 partitions on it; 2x50gb partitions and a 300gb one.
I installed windows i7 64 bit on the second partition and after that i booted of a dvd 
ubuntu 9.10 64 bit downloaded from ubuntu.com
i used the first partition of 50 gb to put ubuntu and made it linux ext4

My problem is that right now...when i start my computer ... it always goes in Ubuntu...
and i can't choose if i want to load ubuntu or windows......
Is there any way to have the boot loader let me choose?
Can somebody help me out please?

Thank you very much,
Florin

---

### Post by kiridude on 2010-01-04
You should put XP in the first partition along with the MBR.

If you install XP in the first partition, then Ubuntu again in the second partition, it will install the MBR automatically.

You should then be presented with a list of options when booting.

---

### Post by yogesh.girikumar on 2010-01-04
Hi,
       You may have to edit the grub configuration for this. I'm assuming that the Ubuntu installation has taken care of the windows OS already present.
       Go to terminal by going to Applications -> Accessories -> Terminal
       then type this


```
$ sudo gedit /etc/default/grub
```give the password if prompted
       look for the following lines and make changes as follows:


       ```
GRUB_TIMEOUT="10"
```
       This line signifies the number of seconds the system waits until making the default selection. Setting this to -1 will display the menu until you make a selection (no timeout). Here I have opted for a 10 second display of GRUB menu.
       after that, save the file and close gedit.
       Then type in terminal the following command:
       ```
update-grub
```       The grub file will be updated and if you restart your system, it should show the menu.
       If this doesn't work, just copy and paste the contents of the file "/boot/grub/grub.cfg"
       Once you're done with that, you can edit the following line to select the default OS to boot during startup.
       

```
GRUB_DEFAULT=0
```
       This option sets the default entry to be selected in the absence of user input. Starts from 0. 0 is for the first menu item and 1 is for the second and so on..


       This link might be helpful : [https://wiki.ubuntu.com/Grub2#grub%20%28/etc/default/grub%29](https://wiki.ubuntu.com/Grub2#grub%20%28/etc/default/grub%29)

       Yogesh.

---

