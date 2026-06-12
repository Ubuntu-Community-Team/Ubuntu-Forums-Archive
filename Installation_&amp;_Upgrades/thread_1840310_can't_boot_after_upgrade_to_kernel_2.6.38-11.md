---
title: "can't boot after upgrade to kernel 2.6.38-11"
date: 2011-09-07
forum: Installation &amp; Upgrades
---

### Post by haw on 2011-09-07
as a title, i can't boot to my ubuntu 11.04 64 bit after i upgrade to newer kernel, i think something error with my grub and i have to reinstall my grub, and nothing happen with my ubuntu
in my laptop, i have ubuntu 11.04, openSUSE 11.2 and Win*** with grub from ubuntu i still can boot to my opensuse and other operating system, if i want to boot my ubuntu, whatever kernel i choice, 2.6.38-11 or 2.6.38-10 i can't boot and grub's say 

error : no such disk
error : you need to load the kernel first

note : after i upgrade my ubuntu, i found something abnormal with my grub, the background's back to old version (black and white, not like my first grub in 11.04 with purple background) but in header said version 1.9

thanks for attention and i need your help

---

### Post by dino99 on 2011-09-07
sudo dpkg-reconfigure grub-pc

---

### Post by haw on 2011-09-07
> **dino99 said:**
> sudo dpkg-reconfigure grub-pc

where i do this command ?
on live cd ?

---

### Post by Hakunka-Matata on 2011-09-07
If you are still having problems, I suggest you download and run the boot_info_script program listed in my signature.

Post the output information file '**RESULTS.txt'** that boot_info_script.sh generates.


[LIST]
[*] Open the RESULTS.txt file,
[*]highlight and copy the ENTIRE text of the file,
[*]paste that copied text into a New Reply
[*]highlight the entire text field again,
[*]click on code tags icon **# **to enclose the text in [ code]  paste text here  [ /code]
[/LIST]

---

### Post by Hakunka-Matata on 2011-09-07
> **haw said:**
> where i do this command ?
on live cd ?

Yes, you can use LiveCD, 

Open a Terminal window [B]System>Applications>Terminal
[/B]or if using the unity desktop scheme, click on upper most, left hand side, white ubuntu symbol and search for **Terminal.  **

```
sudo dpkg-reconfigure grub-pc
```

---

### Post by haw on 2011-09-08
i give up, i'll reinstall my ubuntu, i think is the best i can do, but i never stop to know why it's happen to my ubuntu

thanks for Hakunka-Matata and dino99 for helping me

---

### Post by fig_wright on 2011-09-18
[http://ubuntuforums.org/showthread.php?p=11200815](http://ubuntuforums.org/showthread.php?p=11200815)

---

