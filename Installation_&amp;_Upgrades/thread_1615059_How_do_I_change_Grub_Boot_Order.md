---
title: "How do I change Grub Boot Order?"
date: 2010-11-06
forum: Installation &amp; Upgrades
---

### Post by bigtel on 2010-11-06
I have installed Ubuntu on my laptop but still want Vista as the primary operating system (for now) and i want it to boot as default. How do I change the grub order?

Thanks

---

### Post by nitstorm on 2010-11-06
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by ryadav on 2010-11-06
The grub 2 boot menu is regenerated each time you install grub, although you should not edit it by hand, it is safe to do so in this case

first back up the grub config file

**sudo cp /boot/grub/grub.cfg /boot/grub/grub.cfg.backup**

then edit the file as root with you fav editor, look up you windows entry section that beings with menuentry, and move the section to be the 1st **menuentry** { ......

it will look something like this but will be a bit different depending on the drive and partition you have windows installed on

menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set aa1ccf831ccf48d1
    drivemap -s (hd0) ${root}
    chainloader +1
}

---

### Post by bigtel on 2010-11-06
Thanks guys:)

---

### Post by nitstorm on 2010-11-06
if you follow the link that i mentioned above, it's a neat and safe process.

anyhoo here are the steps:

1.
```

cat /boot/grub/grub.cfg

```

2. Search for the line that says something like
```
 
menuentry "Microsoft Windows XP Professional (on /dev/sda1)"

```

3. Highlight the words after menuentry (i.e., "Microsoft Windows XP Professional (on /dev/sda1)" ) . Now, right-click and copy the text.

4. Open another terminal. Type 
```

gksudo gedit /etc/default/grub

```

5. The first line says GRUB_DEFAULT=0.
Make it look as
```

GRUB_DEFAULT="Microsoft Windows XP Professional (on /dev/sda1)"

```

6. Save the file and close it.

7. Type the following command to update the grub
```

sudo update-grub

```

8. The changes will all be done.

Hope this was somewhat useful :) Cheers!  :)

---

### Post by sikander3786 on 2010-11-06
Many good posts have already been made.

Just to make a note, you can use startup-manager, a gui to manage grub easily.

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)


Edit:

> The grub 2 boot menu is regenerated each time you install grub, although you should not edit it by hand, it is safe to do so in this case.....

```
sudo cp /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
```

It is never safe to do that manually as the grub.cfg is going to be regenerated every time you get a related update and it will again break the order. Instead **nitstorm's** method is a better option.

---

### Post by bigtel on 2010-11-08
Thanks for your help on this. The steps look easy enough to follow so I will give it a go..!

---

### Post by morenogabr on 2011-01-02
> **nitstorm said:**
> if you follow the link that i mentioned above, it's a neat and safe process.

anyhoo here are the steps:

1.
```

cat /boot/grub/grub.cfg

```

2. Search for the line that says something like
```
 
menuentry "Microsoft Windows XP Professional (on /dev/sda1)"

```

3. Highlight the words after menuentry (i.e., "Microsoft Windows XP Professional (on /dev/sda1)" ) . Now, right-click and copy the text.

4. Open another terminal. Type 
```

gksudo gedit /etc/default/grub

```

5. The first line says GRUB_DEFAULT=0.
Make it look as
```

GRUB_DEFAULT="Microsoft Windows XP Professional (on /dev/sda1)"

```

6. Save the file and close it.

7. Type the following command to update the grub
```

sudo update-grub

```

8. The changes will all be done.

Hope this was somewhat useful :) Cheers!  :)

Perfect thanks!!

---

