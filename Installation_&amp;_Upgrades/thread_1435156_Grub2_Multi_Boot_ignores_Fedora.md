---
title: "Grub2 Multi Boot ignores Fedora"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by bismay46 on 2010-03-21
I have set up my desktop pc with Windows 7, Windows XP, Ubuntu 9.10 and openSUSE 11.2 on disk sda.  My Swap partition and Fedora 12 are on disc sdb and my Home partions are on disc sdc. GRUB2 menu allows me to boot into all the operating system except Fedora. 
I have edited the file /etc/grub.d/40_custom as follows

                                 menuentry "Fedora 12 - 2.6.32.9-70 (on /dev/sdb2)" {  
     insmod ext2  
     set root=(hd1,2)   
     search --no-floppy --fs-uuid --set 745f4361-0629-41aa-9dfd-edd7f6679268  
     linux  /boot/vmlinuz-2.6.32.9-70.fc12 root=UUID= 745f4361-0629-41aa-9dfd-edd7f6679268 ro   quiet splash  
     initrd /boot/initrd-2.6.32.9-70.fc12   
 }  
 
but GRUB2 appears to ignore it completely and I cannot boot into Fedora.
Can anyone tell me what I am doing wrong?

---

### Post by tom4everitt on 2010-03-21
After editing 40_custom you have to run the command:

sudo update-grub

in a terminal for the changes to take effect. 

Also you should NOT remove the first lines of 40_custom when you add your fedora entry, if you remove them it won't work either.

---

### Post by bismay46 on 2010-03-22
Tom

Thanks for the reply. The new code I showed above was added to the end of the original 40_Custom file code. But after running making this file executable and running update-grub the resultant grub.cfg file text has not changed:- 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/SHARED: No such file or directory
Found Windows 7 (loader) on /dev/sda2
Found openSUSE 11.2 (x86_64) on /dev/sda6
done

I think the 30_Os-prober is only looking at disc sda? But if so, I don't know how to make it look at all 3 disks.

---

### Post by andrewthomas on 2010-03-22
> **bismay46 said:**
> 
I think the 30_Os-prober is only looking at disc sda? But if so, I don't know how to make it look at all 3 disks.
You are most likely not going to have much success getting the Os-prober to recognize Fedora.  Hopefully, you installed grub to Fedora's partition when you during Fedora's install.  If this is the case, you can just chainload that partition by using 

```
menuentry "chainload Fedora on sdb2"{
set root=(hd1,2)
chainloader +1
}
```

---

### Post by andrewthomas on 2010-03-22
> **bismay46 said:**
> 
I have edited the file /etc/grub.d/40_custom as follows

                                 menuentry "Fedora 12 - 2.6.32.9-70 (on /dev/sdb2)" {  
     insmod ext2  
     set root=(hd1,2)   
     search --no-floppy --fs-uuid --set 745f4361-0629-41aa-9dfd-edd7f6679268  
     linux  /boot/vmlinuz-2.6.32.9-70.fc12 root=UUID= 745f4361-0629-41aa-9dfd-edd7f6679268 ro   quiet splash  
     initrd /boot/**initrd**-2.6.32.9-70.fc12   
 }  
 
Alternatively, I think that you are missing a couple of things from your entry.
For 32-bit:
```
menuentry "Fedora 12 - 2.6.32.9-70 (on /dev/sdb2)" {
insmod ext2
set root=(hd1,2)
search --no-floppy --fs-uuid --set 745f4361-0629-41aa-9dfd-edd7f6679268
linux /boot/vmlinuz-2.6.32.9-70.fc12.**i686** ro root=UUID= 745f4361-0629-41aa-9dfd-edd7f6679268 LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
initrd /boot/**initramfs**-2.6.32.9-70.fc12.**i686.img**
} 
```Or 64-bit:
```
menuentry "Fedora 12 - 2.6.32.9-70 (on /dev/sdb2)" {
insmod ext2
set root=(hd1,2)
search --no-floppy --fs-uuid --set 745f4361-0629-41aa-9dfd-edd7f6679268
linux /boot/vmlinuz-2.6.32.9-70.fc12.**x86_64** ro root=UUID= 745f4361-0629-41aa-9dfd-edd7f6679268 LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
initrd /boot/**initramfs**-2.6.32.9-70.fc12.**x86_64.img**
} 
```

---

### Post by tom4everitt on 2010-03-22
> **bismay46 said:**
> Tom

Thanks for the reply. The new code I showed above was added to the end of the original 40_Custom file code. But after running making this file executable and running update-grub the resultant grub.cfg file text has not changed:- 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/SHARED: No such file or directory
Found Windows 7 (loader) on /dev/sda2
Found openSUSE 11.2 (x86_64) on /dev/sda6
done

I think the 30_Os-prober is only looking at disc sda? But if so, I don't know how to make it look at all 3 disks.

Dont care about the output of update-grub, thats only the output of the os-prober. Your fedora entry was most likely added anyway. Look in /boot/grub/grub.cfg to be sure.

---

### Post by oldfred on 2010-03-22
Related to andrewthomas's post. You have two drives so you have two MBR's. Did you (or can you) install Fedora's boot loader to the MBR of sdb?

You can also chainboot to the MBR.
menuentry "chainload Fedora on sdb"{
set root=(hd1)
chainloader +1
}

---

### Post by bismay46 on 2010-03-22
Thanks Tom, Andrew & Old Fred for your comments and advice.

I tried chainloading using Andrew's code. (I think Old Fred's would have the same result.)
The result was a new entry in the Grub Menu but when selected it I got the error message:
'BOOTMGR is missing
Press Ctrl+Alt+Delto restart'

I then added Andrew's 64bit code to the /etc/grub.d/40_custom record and executed update-grub. Again the result was a new entry in the Grub Menu but when selected it I got the error message:
'error: unknown command \|
Press any key to continue'

When I installed Fedora 12 I am not sure what I keyed into the Grub Screen. I do remember that the installer did not appear to recognise the other Operating Systems at the time and the Installation Guide did not clarify my problem. If anyone can tell me what to key into this screen, I will reinstall Fedora 12 and see if it gets round my problem. (Last time I was only able to log into Fedora until I recreated my Grub Files from a backup I had made.)

---

### Post by andrewthomas on 2010-03-22
> **bismay46 said:**
> 

  If anyone can tell me what to key into this screen, I will reinstall Fedora 12 and see if it gets round my problem. 

Look at the screenshot that I attached.  Just make sure that your BIOS order is correct and 
use
```
menuentry "chainload Fedora on sdb"{
set root=(hd1)
chainloader +1
}
```for the MBR of sdb method (although I'm not sure that the installer will give you this option) or
```
menuentry "chainload Fedora on sdb2"{
set root=(hd1,2)
chainloader +1
}
``` for the partition method

---

### Post by kansasnoob on 2010-03-22
I found that Lucid's (or Debian Sid's) grub2 had no problem finding the same. Here's my Boot Info Script RESULTS.text from that:

[ATTACH]151051[/ATTACH]

And upgrading to Lucid's grub2 is not difficult.

First make sure you don't have mixed legacy grub and grub2 files by running:

```
ls /boot/grub
```

If you see both a **menu.lst** and a **grub.cfg** stop! This won't help you! (It's all in alphabetical order so it's easy to see.)

Should you decide to upgrade to the latest grub2 you'll need to purge the old and install the new, but you need to know if you're running 32bit or 64bit Ubuntu so run:

```
uname -m
```

(&#65279;64 bit users would see x86_64, 32 bit users would see i686)

Then find the new packages here:

[http://packages.ubuntu.com/lucid/grub-common](http://packages.ubuntu.com/lucid/grub-common)

[http://packages.ubuntu.com/lucid/grub-pc](http://packages.ubuntu.com/lucid/grub-pc)

Once you know you've saved the new packages go to terminal and run:

```
sudo apt-get purge --remove grub-pc && sudo apt-get purge --remove grub-common
```

Then go to the location where you saved the two new packages and beginning with "grub-common" just double-click the packages and let gdebi do the work.

Then run:

```
sudo update-grub
```

And be patient! Wait until it says done! Did it find Fedora? If no try:

```
sudo apt-get install --reinstall libdebian-installer4
```

```
sudo os-prober
```

```
sudo update-grub
```

Still no go? Then it's time to see the output of the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by andrewthomas on 2010-03-22
> **kansasnoob said:**
> I found that Lucid's (or Debian Sid's) grub2 had no problem finding the same. 
I don't know why my os prober can never find fedora, but since chainloading works just fine for me, I gave up trying to figure it out.

---

