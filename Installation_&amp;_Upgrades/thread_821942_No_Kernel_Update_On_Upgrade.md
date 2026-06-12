---
title: "No Kernel Update On Upgrade?"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by NoVista on 2008-06-07
Upgrading from Gutsy to Hardy, on bootup, it still says Gutsy?

Now I should mention, I already have a fresh Hardy install on another drive, and a Windows OS too.
I don't see how that would make a difference though.

Why won't the kernel update on an upgrade?

---

### Post by logos34 on 2008-06-07
try 
[B]
sudo grub-install /dev/sda[/B] (or whatever your drive is)

**sudo update-grub**

If no change, post

**ls /boot**

**cat /boot/grub/menu.lst**

---

### Post by NoVista on 2008-06-07
Ok thanks. I'll give that a whirl on the next attempt.

---

### Post by NoVista on 2008-06-07
Wait, I have seperate home partition.

---

### Post by zvacet on 2008-06-08
How many kernels do you have installed?Go to the synaptic and in search box type **linux-image** and you will see all kernelswhich are installed in your system.You can keep last Gutsy kernel ( if I remember correctly there were updates of that kernel) and of course Hardy kernel.Delete all others with lower number.After restart you should see Hardy kernel on grub.

---

### Post by NoVista on 2008-06-08
Ok zvacet. I have a lot of kernels.

Is there a limit on how many kernels one can have?

---

### Post by JSnake on 2008-06-08
> **NoVista said:**
> Ok zvacet. I have a lot of kernels.

Is there a limit on how many kernels one can have?

Generally, it's wise to delete previous kernels after every new kernel update.

---

### Post by logos34 on 2008-06-08
> **JSnake said:**
> Generally, it's wise to delete previous kernels after every new kernel update.

It is?  I thought the general rule was to keep the previous (working) kernel in case you ever need it in a pinch

---

### Post by zvacet on 2008-06-08
@ **logos34**

You are right,but I think we get 3 or 4 kernel upgrades in Hardy.If just one of them work it is O.K.If they all work even better.In that case he can delete all previous kernels(Gutsy,Feisty maybe...) and still have few working kernels which will show up in grub.Correct me if I´m wrong.

---

### Post by logos34 on 2008-06-08
> **zvacet said:**
> @ **logos34**

You are right,but I think we get 3 or 4 kernel upgrades in Hardy.

Yeah, I was just talking about Hardy.  You know, update to -18, but keep the most recent working kernel, like -16 or -17, whatever...Ditch all the rest from previous releases (gutsy, feisty, etc)

---

