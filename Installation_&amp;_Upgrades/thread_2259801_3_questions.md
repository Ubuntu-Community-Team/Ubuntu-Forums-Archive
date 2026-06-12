---
title: "3 questions"
date: 2015-01-07
forum: Installation &amp; Upgrades
---

### Post by gogo3 on 2015-01-07
**1st question**: If I were to install Lubuntu 11.10(Tested it on live CD, I love it) and had to delete it, how can I do that while having Windows XP installed alongside him?

**2nd question**: Is Lubuntu 11.10 bug-free or does he have some important bugs(GRUB, etc.)?

**3rd question**: How can I shutdown my PC from a live CD without Lubuntu telling me that I have no authorization(something like that)? Same goes with accessing my hard drive and USB.

Also, for everyone asking how to boot when it only shows the terminal, type in '**startx**'(works on live CD, don't know what to do on installed version).

Sorry for posting this in the Installation&Upgrades section, as I didn't know where to put it(this section fitted the best based on the questions).

---

### Post by ajgreeny on 2015-01-07
Using 11.10 will not help you as it is now out of support having reached end-of-life in April 2013.  There will be no easy way to add any new applications to it and no way to update it.  As for your specific problems I am afraid there is not much anyone can do to help because of the EOL status of 11.10.

What hardware are you using; knowing that may help us tell you how to avoid possible problems of the sort you have seen in your try-out.

Get a copy of Lubuntu 14.04 and you will have almost three remaining years of support and you will also get much more help from the forum; we can't help with 11.10.

---

### Post by sudodus on 2015-01-07
Welcome to the Ubuntu Forums :-)

0. Lubuntu 11.10 passed end of life years ago. It means that there are no repositories for program packages. You cannot install new packages, you get no updates/upgrades, not even security updates, so I discourage you to use that version of Lubuntu.
[URL="http://ubuntuforums.org/showthread.php?t=2229730"]
Forums Staff recommendations on EOL Ubuntu releases, in particular 10.04 desktop.[/URL]

Installing operating systems is risky, so please ***backup*** at least all personal files (pictures, documents etc) before starting. If you backup Windows too (with recovery disks), it will be better. The best is to restore the whole system, to make a compressed image with Clonezilla.

1. When installed, Lubuntu replaces the Windows bootloader with the grub bootloader. If you delete Lubuntu, you must reinstall the Windows bootloader, which can be done with Windows tools, or maybe even better, from a backup of the original system.

2. No operating system is bug free. It is way too complex to be bug free. In particular, it is old and contains several security holes.

3. If Lubuntu is working properly, it works to click the shutdown button without any passwords. I think you have some problem with some driver, that makes your Lubuntu boot in text mode. Otherwise you would not need startx. Maybe that can be solved with a boot option or combination of boot options. See these links

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

*. [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by grahammechanical on 2015-01-07
If the OS only loads to a command line prompt, then we log in and we can run commands like startx.

---

### Post by gogo3 on 2015-01-07
> **grahammechanical said:**
> If the OS only loads to a command line prompt, then we log in and we can run commands like startx.
Isn't that what I said? XD

Thanks for the replies. If it's not a problem, can you please give me a link of 12.04 and higher, but not 14.10? I'm afraid when it comes to bigger numbers, because when I downloaded 14.10, I realized it won't fit on an CD(It had 705MB, CD has 700MB space :P) Please gimme Lubuntu's link, Ubuntu and the other OS-s in the family are maybe a little overpowered(although I think my PC would run Xubuntu without a problem).

Specifications of my PC(11 years old, but Lubuntu works perfect on live sessions):
RAM=768MB
Graphics card=ATi Radeon 9250
Processor=Intel Celeron 2.53 GHz(single-core)
VRAM=128MB
HD=75GB
Other OS-s:
Windows XP Home Edition(Service Pack 3)
And some experience with Linux Puppy, which was too simple for me(but absolutely perfect for any PC, both in size and speed)

Also, thanks to everyone who made these amazing Linux OS-s :D

---

### Post by sudodus on 2015-01-07
Here is a link to Lubuntu: [http://cdimage.ubuntu.com/lubuntu/releases/](http://cdimage.ubuntu.com/lubuntu/releases/)

I suggest that you first try ***Lubuntu 14.04.1 LTS***, then some light-weight community re-spin based on Ubuntu 12.04 LTS: for example ***LXLE, Bento*** or ***Bodhi***. All these promise long time support until April 2017.

Remember to [try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

Good luck :-)

---

### Post by gogo3 on 2015-01-07
> **sudodus said:**
> Here is a link to Lubuntu: [http://cdimage.ubuntu.com/lubuntu/releases/](http://cdimage.ubuntu.com/lubuntu/releases/)

I suggest that you first try ***Lubuntu 14.04.1 LTS***, then some light-weight community re-spin based on Ubuntu 12.04 LTS: for example ***LXLE, Bento*** or ***Bodhi***. All these promise long time support until April 2017.

Remember to [try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

Good luck :-)
Thank you so much, gonna try 14.04 out(seems like it's smaller than 13.10, wow!). Thanks again :D

You can lock this if you lock posts around here.

---

### Post by sudodus on 2015-01-07
We don't close threads unless they break the forum rules or get too old (one year without any new post). Instead, please try for a while, and wait until you have installed a working version. Then you can click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by gogo3 on 2015-01-07
> **sudodus said:**
> We don't close threads unless they break the forum rules or get too old (one year without any new post). Instead, please try for a while, and wait until you have installed a working version. Then you can click on **Thread Tools** at the top of the page and mark this thread as SOLVED
I'd like to ask another question, just for safety(sorry, I'm extremely careful when it comes to installing OS-s).
I burnt my Lubuntu 14.04 at top speed(16x I think). Will this make any problems?

---

### Post by ajgreeny on 2015-01-07
If burning to a CD or DVD you are best to burn at the slowest speed possible.

Can your machine boot from a USB, as that may be the best option?

---

### Post by MartyBuntu on 2015-01-07
> **gogo3 said:**
> 
I burnt my Lubuntu 14.04 at top speed(16x I think). Will this make any problems?

Possibly not. But I always burn CD's anywhere between 8x to 12x. DVD's at 4x to 8x.

---

### Post by sudodus on 2015-01-08
> **ajgreeny said:**
> If burning to a CD or DVD you are best to burn at the slowest speed possible.

Can your machine boot from a USB, as that may be the best option?

+1

---

### Post by gogo3 on 2015-01-08
Sorry, my PC cannot boot from a USB. Only from a Floppy, CD or DVD. I'll try out this CD that I burned quickly in Live first, and then install if everything works like it should.
For me, this is solved.

---

### Post by ajgreeny on 2015-01-08
On the first menu you see from the bootup, where you see the option to either **Install** or **Try without installing**, there is also an option to "check the install disk".

Use that to be sure before installing.

---

