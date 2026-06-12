---
title: "[SOLVED] Grub Error 17"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by chillpenguin on 2008-07-03
I just used the Live CD to install Ubuntu onto my primary HDD. There are two other HDDs in this system. I am not attempting to dual-boot; I only want to use Ubuntu on this machine.

After the install, I get the "error 17" message. I googled the message and found others giving advice about booting into the Live CD and checking the /boot/grub directory.

The problem here is that I do not have a /boot/grub directory. There is a /boot directory, but no grub sub directory.

Can any one provide advice?

---

### Post by SkonesMickLoud on 2008-07-03
Boot into the LiveCD, then in a terminal type:

```
sudo grub
```

Then inside the grub terminal:

```
find /boot/grub/stage1
```

You should get a return along the lines of:

```
(hdx,x)
```

Then type:

```
root (hdx,x)
```

Then:

```
setup (hd0)
```

Finally:

```
quit
```

Then reboot into your newly grubbed system.

---

### Post by chillpenguin on 2008-07-03
If only I had waited to see your response. In frustration I yanked out the power cords to the other two HDDs and reinstalled. That got me passed the error, but I haven't plugged the other two HDDs back in. I'm about to plug them back in and see what happens.

Thank you for your help!

---

### Post by sulekha on 2008-07-03
> **chillpenguin said:**
> If only I had waited to see your response. In frustration I yanked out the power cords to the other two HDDs and reinstalled. That got me passed the error, but I haven't plugged the other two HDDs back in. I'm about to plug them back in and see what happens.

Thank you for your help!

i had this error , then every time i had to do find /boot/grub/stage1

then setup(hd0,2) and all that stuff. but in my experience this problem will recurr. what you have to make sure is that 

make sure that

 1)your H.D.D is not corrupted.
 2) you have got  steady voltage levels
 3) your SMPS is working properly

if all of the above are up to the mark ,then you wont get that error again

---

### Post by chillpenguin on 2008-07-04
> **sulekha said:**
> i had this error , then every time i had to do find /boot/grub/stage1

then setup(hd0,2) and all that stuff. but in my experience this problem will recurr. what you have to make sure is that 

make sure that

 1)your H.D.D is not corrupted.
 2) you have got  steady voltage levels
 3) your SMPS is working properly

if all of the above are up to the mark ,then you wont get that error again

I'm not sure if I'm going to run into this issue b/c when I plugged my HDDs back in and rebooted, Ubuntu started up just fine and even recognized the two drives.

---

