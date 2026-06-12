---
title: "Ubuntu 11.04 on a HP Pavilion"
date: 2011-07-21
forum: Installation &amp; Upgrades
---

### Post by Sergio_ on 2011-07-21
Hi there, this is my first post in this forum. I have just installed ubuntu 11.04 on this laptop:

Hp Pavilion dv 5000
RAM 512mb
procesor AMD Turion 64
Graphics ATI Radeon XPRESS 200M

I have been trying to set swappinnes value to 10 (I was reading this faq[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")) and I keep getting this error 

[http://imageshack.us/f/225/pantallazoerrorsetswapp.png/]("http://imageshack.us/f/225/pantallazoerrorsetswapp.png/")

Also I have been asking myself, if I have installed everything ok??Because isn´t sopposed Ubuntu to be faster, and I dont think that with my actual installation.
I hope you can help, I was reading all day I didnt found that much.Thx

---

### Post by Mr. Shannon on 2011-07-21
> Also I have been asking myself, if I have installed everything ok??Because isn´t sopposed Ubuntu to be faster, and I dont think that with my actual installation.

What did you have before Ubuntu? Remember that Ubuntu is a modern operating system and thus it is best with 1G+ of memory. As I am typing this I am using about 730mb of memory (just 3 applications and a couple docks running).  Bring up the system monitor and look at your memory usage.  If you are topping out on memory then you can either buy more memory or use a lighter version of Ubuntu like Xubuntu.

Also you did not say how fast your processor is.

---

### Post by mastablasta on 2011-07-21
you GPU is the one responsible for slowness.
 
you can try adding **edgers PPA** (latest opensource drivers) to improve performance. you can also turn off special effects and use unity 2D interface to help it porcess the whole thing faster.
 
You could also try 10.04 version but you would definatelly have to upgrade drivers on that one.
 
you computer was made for year 2005-2007, Ubuntu was made for 2011 :-)
just kidding, porbably it's the drivers and default special effects that slow you down a bit. also try Xubuntu (it's a bit lighter on resources)

---

### Post by Sergio_ on 2011-07-25
> **Mr. Shannon said:**
> What did you have before Ubuntu? Remember that Ubuntu is a modern operating system and thus it is best with 1G+ of memory. As I am typing this I am using about 730mb of memory (just 3 applications and a couple docks running).  Bring up the system monitor and look at your memory usage.  If you are topping out on memory then you can either buy more memory or use a lighter version of Ubuntu like Xubuntu.

Also you did not say how fast your processor is.

Mr. Shannon thx for your ans. Before Ubuntu, I had windows XP. Right now I have open just Chrome, with 3 tabs (1 is facebook and the other 2 are ubuntu forums) and my memory usage is 361 of 491 (thats what the system recognize) and the CPU usage is 41%.

I tried a command that I found on this forum, Code: lshw, and it shown this info. 

*-cpu
          product: AMD Turion(tm) 64 Mobile Technology ML-34
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 1
          bus info: cpu@0
          size: 800MHz
          capacity: 800MHz
          width: 64 bits

> **mastablasta said:**
> you GPU is the one responsible for slowness.
 
you can try adding **edgers PPA** (latest opensource drivers) to improve performance. you can also turn off special effects and use unity 2D interface to help it porcess the whole thing faster.
 
You could also try 10.04 version but you would definatelly have to upgrade drivers on that one.
 
you computer was made for year 2005-2007, Ubuntu was made for 2011 :-)
just kidding, porbably it's the drivers and default special effects that slow you down a bit. also try Xubuntu (it's a bit lighter on resources)

jajaja I know its a little old the notebook, but it was the alternative, that a friend borrow, to my water-damaged MAC =(

Im going to try turning off special effects and use 2d interface and see how its goes. I wouldnt try 10.04, Im kind of new in ubuntu, prefere a lite version, instead of. Ok thx for responding, tell you later whats better

---

### Post by Sergio_ on 2011-07-26
hi there again. I had just installed 2D interface, boot, and then in the login screen, in the bottom appears the option of 2D, I selected it, but when system starts it looks exactly the same as before. what the problem could be?? do I have to do something as root???

---

