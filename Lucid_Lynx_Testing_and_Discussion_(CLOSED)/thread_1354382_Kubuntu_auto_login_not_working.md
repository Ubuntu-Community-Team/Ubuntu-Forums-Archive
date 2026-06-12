---
title: "Kubuntu auto login not working?"
date: 2009-12-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Taoye on 2009-12-13
I'm not sure if this problem is specific to the Lucid alpha, or to Kubuntu in general, but I'll post here because I am using the alpha so it might simply be a broken feature. Basically the automatic login does not work. I go into System Settings -> Advanced -> Login Manager -> Convenience, and check off "Enable Auto-Login" for my user. However when I reboot the machine, I am still presented with the login window and need to enter my username/password to get in.

Anyone else had this issue and have any insight on how to get it to work?

---

### Post by ronacc on 2009-12-13
yes there is a problem with autologin in kubuntu lucid A1 .Autologin works in gnome .

---

### Post by Arla on 2009-12-18
Since this impacts the LiveCD as well, what is the default userid/password?

I was wanting to try out Kubuntu and see if wireless was any better (although reading around here, sounds like it's still kinda broken) and would allow me to use Kubuntu at all.

---

### Post by ranch hand on 2009-12-19
There is no password on the LiveCD.  If the login comes up just hit enter.

---

### Post by Arla on 2009-12-19
> **ranch hand said:**
> There is no password on the LiveCD.  If the login comes up just hit enter.

Doesn't seem to work, I suspect because I'm not entering a UserID, it's just a blank login screen (for UserID and password).

---

### Post by ranch hand on 2009-12-19
If you have a LiveCD working like that I would file a bug because it is not the way they work at all.  They normally just boot right to the desktop.  If there is a log in you wait like 10 seconds and it will boot to the desktop, or you can do as I said and it will boot to the desktop.

You must have another LiveCD, try it again and see.

If you pull up the terminal you will need to use sudo before administrative tasks but it will not ask for a password.

The long and the short of it is that the user is "ubuntu" and there is no password.

As for the poor OP that we are ignoring, file a bug and use your password.  Hopefully in a few updates it will be cured.

---

