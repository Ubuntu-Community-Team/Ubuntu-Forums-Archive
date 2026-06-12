---
title: "Installed 7.04, goes to blank screen"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by fritz3000g on 2008-02-02
I'm a new ubuntu user - haven't ever used anything but windows before.  I loaded version 7.04 from the Live CD and everything seemed to go fine.

Now when I start the computer it says that it's loading "Grub" (I don't know what that is), and then says "Starting up" but then goes to a black screen.

One time I was fooling around and got it to open ubuntu and I logged in, but I couldn't change the screen resolution to more than 640x480, so I think that I may have a graphics problem.  But since then I haven't been able to open ubuntu again - I just get the black screen

Can anyone help?

-Jer...

---

### Post by taurus on 2008-02-02
Boot into recovery mode from GRUB menu and reconfigure your X server again with

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```
What kind of graphic card do you have in your machine?

---

### Post by fritz3000g on 2008-02-02
Ok I did that.  It gave me a list of reconfigure options.

I'm not sure what kind of video card I have.  It's a dell inspiron from 2003.

Jer...

---

### Post by fritz3000g on 2008-02-02
Also it says that "r" is an unknown option.

---

### Post by taurus on 2008-02-02
To determine what graphic card do you have, look at the output of this command, VGA.

```
lspci
```

Did you run the command exactly like it was, rebooting your machine?

```
shutdown -r now
```

---

### Post by fritz3000g on 2008-02-02
Ok, so I did it again and got it to take me to a screen where I can choose from lots of different things.  I chose VGA and saw that several boxes were checked (one of them was 640x480).

I did "lspci" and this is what it said for VGA:

VGA intel corporation 828465g/gl[brookdale-g]/ge c hipset integrated graphics device (rev 03)

Jer...

---

### Post by fritz3000g on 2008-02-02
Ok, so I found out that some people have had the same problem I'm having, which is a problem with the video card.  Apparently this particular intel video card is buggy.  I tried the vesa and i810 drivers (I don't have the intel driver).

Any other ideas?

Thanks for the help, by the way.

---

