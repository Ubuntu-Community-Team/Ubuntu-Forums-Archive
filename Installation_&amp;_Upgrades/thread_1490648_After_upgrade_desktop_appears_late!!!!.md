---
title: "After upgrade desktop appears late!!!!"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by emma00 on 2010-05-22
Hi,

Does anyone who has upgraded to ubuntu 10.04 through update manager have this a little bit annoying problem that the screen comes a little late after grub loaded it never happened before.It occurred when it said to restart  the system first i thought it may be on first time but it is still load little late??????:confused:

---

### Post by linuxman94 on 2010-05-22
Is it taking longer after you log in?

---

### Post by Frogs Hair on 2010-05-22
There is a bug report filed  on Launch Pad about that issue.

---

### Post by proggy on 2010-05-22
> **Frogs Hair said:**
> There is a bug report filed  on Launch Pad about that issue.
Can you give a link please?

---

### Post by emma00 on 2010-05-23
> **linuxman94 said:**
> Is it taking longer after you log in?

yes it comes after logging..........

---

### Post by dino99 on 2010-05-23
everything is not perfect yet, and your issue is known by quite everyone at time. Check your hardware driver first to see if yours is well activated.

---

### Post by linuxman94 on 2010-05-23
Here is the bug report. [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/569290]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/569290")

If you have a floppy enabled in your BIOS then disable it.  It speeds up the load time greatly.

---

### Post by proggy on 2010-05-25
In Login Screen Settings i chose "log in as `user` automatically" it speeds up my entry into my desktop,seeing that i`m the only one using this computer of course it`s safe.

---

### Post by proggy on 2010-05-30
> **proggy said:**
> In Login Screen Settings i chose "log in as `user` automatically" it speeds up my entry into my desktop,seeing that i`m the only one using this computer of course it`s safe. No I recant it`s not much faster :-k

---

### Post by KermEd on 2010-05-30
Hola,

I had a similar problem.  I used to have a usplash screen that appeared between the boot loader and the OS.  But now that usplash changed to a black screen.

In my case I fixed it by StartUp-Manager, toggled 'Show boot splash' and rebooted.

However if you suspect its a video card issue:  [http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)  there are a couple of work arounds that might help you,

- lloyd

---

### Post by emma00 on 2010-05-31
> **KermEd said:**
> Hola,

I had a similar problem.  I used to have a usplash screen that appeared between the boot loader and the OS.  But now that usplash changed to a black screen.

In my case I fixed it by StartUp-Manager, toggled 'Show boot splash' and rebooted.

However if you suspect its a video card issue:  [http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)  there are a couple of work arounds that might help you,

- lloyd

where you in case says the StartUp-Manager is i cant see it in system menus.....
and thanks

---

### Post by KermEd on 2010-06-01
Hey Emma,

It's not installed by default - you have to install it.  You can find it in the Ubuntu Software Center under 'Startup-Manager'.   

Once its installed, you can access it from System > Administration > Startup-Manager.

---

### Post by proggy on 2010-06-01
> **linuxman94 said:**
> Here is the bug report. [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/569290](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/569290)

If you have a floppy enabled in your BIOS then disable it.  It speeds up the load time greatly.
That  solves it , i thought i had disabled it in my bios , did it again today and after login i get my desktop quite quickly.

---

### Post by emma00 on 2010-06-02
> **KermEd said:**
> Hey Emma,

It's not installed by default - you have to install it.  You can find it in the Ubuntu Software Center under 'Startup-Manager'.   

Once its installed, you can access it from System > Administration > Startup-Manager.

I did as you mentioned but nothing changed anyway thanks for your help now i will do a clean install to check if my video driver is the problem

---

