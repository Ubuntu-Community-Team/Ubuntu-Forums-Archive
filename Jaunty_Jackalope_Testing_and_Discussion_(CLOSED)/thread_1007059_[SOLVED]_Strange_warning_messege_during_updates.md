---
title: "[SOLVED] Strange warning messege during updates"
date: 2008-12-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2008-12-10
There were like 48 updates this eve. during the set up part of updates (I use terminal) the following messege appeared. I am not sure what this means and also if there is some thing more I need to look into to fix.
Did any one else see this?
[B]```
Setting up lilo (1:22.8-7ubuntu1) ...

WARNING: kernel & initrd not found in the root directory (/vmlinuz & /initrd.img)
WARNING: Do NOT reboot or LILO may fail to boot if your kernel+initrd is large.
WARNING: Please read /usr/share/doc/lilo/README.Debian


```[/B]
This is what /usr/share/doc/lilo/README.Debian has to say:
```
[B]--[ Distribution upgrade

If you are upgrading or dist-upgrading, it is recommended to run 
/sbin/lilo after that.

--[ Large initrd files and lilo

By default, LILO loads the initrd file into the first 15MB of memory
to avoid a BIOS limitation with older systems (earlier than 2001).

However, with newer kernels the combination of kernel and initrd
may not fit into the first 15MB of memory and so the system will not
boot properly. It seems that the boot issues appear when the
kernel+initrd combination is larger than 8MB.

If this machine has a recent BIOS without the 15MB limitation, you can
add the 'large-memory' option to /etc/lilo.conf to instruct LILO to use
more memory for passing the initrd to the kernel. You will need to
re-run the 'lilo' command to make this option take effect.

If this machine has an older BIOS, you may need to reduce the size of
the initrd *before* rebooting.

If you are using initramfs-tools, you should replace MODULES=most with
MODULES=dep in your configuration and regenerate your initrd file:

sed -i -e s/MODULES=most/MODULES=dep/ /etc/initramfs-tools/initramfs.conf
update-initramfs -u

If you are using yaird or any other initrd generator, please consult
the documentation for your initrd generator.[/B]
```
I am not sure how to handle this or should it be ignored.

---

### Post by cariboo on 2008-12-10
If you haven't rebooted yet just purge lilo, keep using grub, it way easier to configure.

Jim

---

### Post by DougieFresh4U on 2008-12-10
> **cariboo907 said:**
> If you haven't rebooted yet just purge lilo, keep using grub, it way easier to configure.

Jim

Good morning, thanks for your response.
No, I have not rebooted yet.
Could you please provide an exact code to purge lilo as I do not want to 'bork' any thing.
Thanks.

---

### Post by ShirishAg75 on 2008-12-10
Hi DougieFresh4U

First do 
```
$ sudo apt-get install grub
```
Then follow this guide at  [http://www.enterprisenetworkingplanet.com/netos/article.php/3340051](http://www.enterprisenetworkingplanet.com/netos/article.php/3340051) .

---

### Post by DougieFresh4U on 2008-12-10
ShirishAg75, thanks for info. i haven't done any thing yet as I am still reading more info. I want to make sure I make changes correctly.

---

### Post by ShirishAg75 on 2008-12-10
The best of course if you are using a live CD to test/do stuff is to install at grub time itself, that way no issues at all :)

---

### Post by DougieFresh4U on 2008-12-10
> **ShirishAg75 said:**
> Hi DougieFresh4U

First do 
```
$ sudo apt-get install grub
```

Grub is already installed. Should I just purge lilo and all should be good? This has me really worried as the thought of a reboot not booting up is scary. I thought 'lilo'  has been installed for a while now and this morning was just an update to 'lilo'.
I would like to hear more thoughts and suggestions regarding how to proceed with this.

---

### Post by ShirishAg75 on 2008-12-10
Are you booting using LILO or using GRUB. If using GRUB just do a ```
 $ sudo aptitude purge LILO 
``` and reboot. All should work fine. If however if you have been using LILO to boot your hardware and its pre 2001 then you may have to follow the guide I linked to before.

---

### Post by autocrosser on 2008-12-10
Just use Synaptic to remove LILO or sudo apt-get remove lilo---it's a remainder from Debian import--you can use synaptic to reinstall grub if you want....grub should still be there in any case.  I just purge lilo---it's a packaging fault.....

---

### Post by DougieFresh4U on 2008-12-10
Removed 'lilo' via synaptic and rebooted. All seems well except the Intel issue is still doing it's thing.
Sorry for the panic, thanks to all who replied.

---

