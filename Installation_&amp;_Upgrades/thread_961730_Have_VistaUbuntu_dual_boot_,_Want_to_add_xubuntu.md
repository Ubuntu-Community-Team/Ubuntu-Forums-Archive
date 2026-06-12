---
title: "Have Vista/Ubuntu dual boot , Want to add xubuntu"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by toulon on 2008-10-28
I have Vista and Ubuntu on my laptop . I read somewhere on here that you can add Xubuntu through Ubuntu , but it didnt say anything about having the 3 of them installed on one computer . So I guess my question is....is this safe to do and how do I do about it ? . I really dont want to have to use a CD of any kind .If possible , i'd like to get Xubuntu through Ubuntu the way I got Ubuntu through Vista ( wubi ) .:confused::confused:

---

### Post by snowpine on 2008-10-28
In Ubuntu, open a terminal (Applications->Accessories) and type:

```
sudo aptitude install xubuntu-desktop
```

Then, log out. At the log in screen, you can go to the Sessions menu and choose between Xfce (Xubuntu) or Gnome (Ubuntu). 

If you decide you don't like Xubuntu,

```
sudo aptitude remove xubuntu-desktop
```

You could also set up Xubuntu on a completely separate partition, in which case you would have a "true" triple boot. But, I recommend my method since it saves disk space and gives you full access to your personal files and settings whether you're using Xfce or Gnome.

Good luck!

---

### Post by toulon on 2008-10-29
I tried what you said....partly . I typed in the sudo part ok , but when it asked for my password , nothing showed on the screen . I pushed enter and a password error came up . What did I do wrong ?  Im new to Ubuntu....so Im guessing I did something wrong....or I missed something .

---

### Post by snowpine on 2008-10-29
> **toulon said:**
> I tried what you said....partly . I typed in the sudo part ok , but when it asked for my password , nothing showed on the screen . I pushed enter and a password error came up . What did I do wrong ?  Im new to Ubuntu....so Im guessing I did something wrong....or I missed something .

Type your password and press enter. Your password is invisible on the screen, for security purposes. :)

---

