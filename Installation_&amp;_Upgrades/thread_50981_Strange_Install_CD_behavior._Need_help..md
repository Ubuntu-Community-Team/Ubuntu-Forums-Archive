---
title: "Strange Install CD behavior. Need help."
date: 2005-07-22
forum: Installation &amp; Upgrades
---

### Post by bravo_elf on 2005-07-22
Hi everyone! :)

I've downloaded the Kubutu 5.04 install CD and checked it with "md5sum" it was ok.
      But when I wanted to install it on my laptop (TravelMate 4602WLMi) it got to the first screen where I was need to push the "enter", after that  it went to the:[COLOR=Red]"Uncompressing Linux...Ok, booting the kernel"[/COLOR] row and right from this point my laptop totaly hangs.

But it perfectly works on PC (Pentium 3), it starts to boot all the things up and I can install it. 

So plz tell what is the problem with my laptop? (CD?) or whatever it is.

P.S. My laptop's CDROM seems to work fine... I mean I've got no errors in Win XP and it perfectly loads the "WIN XP" installation CD, "Fedora Core" CDs too and all other CD.

---

### Post by FLeiXiuS on 2005-07-22
I have had a problem like this with my laptop.  My solution was easy, disabling ACPI.  

Edit your /boot/grub/menu.lst and add "acpi=off" to your kernel options.

```

...
kernel          /vmlinuz ... ro quiet splash **acpi=off**
...

```

---

### Post by bravo_elf on 2005-07-22
Since Im completely n00b I would ask you to give me some "step by step" explanation:
where and what exactly I need to type?

---

### Post by FLeiXiuS on 2005-07-22
Ok, when you boot up your laptop you'll be sent to the POST then sent to grub.  In grub you can select an option of where to boot to.  Well you can also make changes.  (not permanent)

I believe the key to edit boot parameters is 'e'.  If not, read the bottom of the screen it will tell you.  Select the Ubuntu then press 'e' (or the corresponding key)

From there you will see the menu options for this selection.  Notice the kernel line...

```
 
kernel                    /vmlinuz-2... ro quiet splash

```
Or something simular.  Well at the end of splash you would want to add something like this...

```

kernel                    /vmlinuz-2... ro quiet splash **acpi=off**

```
This'll disable acpi for the next boot.  Now you can press 'B' to boot the changes and see if anything happens.  If not please respond on any errors you have encountered.  Please also take note to search google / wiki / forums for any user who has had this problem before.  Links are in my signature.  Good luck!

---

### Post by bravo_elf on 2005-07-22
We dont understand each other (or its only me)
my Kubuntu Is not installed yet. so how can I disable this problem in this situation?

---

### Post by FLeiXiuS on 2005-07-22
bah woops!!!

When you recieve this screen 

```
Boot:
```

Type "linux acpi=off" without the quotation marks.  Then press enter.  Sorry for the confusion I didn't read your post conclusively.

---

### Post by bravo_elf on 2005-07-22
Tnx a lot! I solved the problem. One more thing, if you type"linux acpi=off in the  "boot:" promt, so you wont need to configure it after, when you'll need to boot the Kubuntu. I have checked the "GRUB" bootsettings as you told and "acpi=off" was already there . :D

---

### Post by FLeiXiuS on 2005-07-22
[QUOTE=bravo_elf]Tnx a lot! I solved the problem. One more thing, if you type"linux acpi=off in the  "boot:" promt, so you wont need to configure it after, when you'll need to boot the Kubuntu. I have checked the "GRUB" bootsettings as you told and "acpi=off" was already there . :D[/QUOTE]

Awesome, I LOVE success stories.  bahah!  Congrats young Chap!  Welcome to Ubuntu.

---

