---
title: "Problems with Ubuntu 11.04 installation"
date: 2012-01-12
forum: Installation &amp; Upgrades
---

### Post by debutant10 on 2012-01-12
Hello,

I am trying to install ubuntu 11.04 (64b) on my 
imac 27 equipped with a ATI Radeon 4850 graphic
card. 

From a liveCD, I get the main menu:
```

	Try Ubuntu without installing
	Install Ubuntu
	...
	F1 Help F2 Language ... F6 Other Options

```

With "Install Ubuntu" I get a black screen.
I guess it is because my graphic card in not 
known.

From the main menu if I type 'esc' I am
asked if I want to quit the graphical boot 
interface and start the text mode interface.
If I say yes I get the boot prompt:
	>boot:

What should I do from here ? 
'Enter' sends me back to the main menu.


I would have wanted also to try with a safe 
graphical mode to use a default driver for the
graphic card but I did not find the appropriate 
option.
But I can make appear the command line corresponding
to "Install Ubuntu" using F6:
```

 Boot Options eed boot = casper only-ubiquity initrd=/casper/initrd.lz quiet splash -- 

```
If I add to this line something like (I am not really sure what should be good) vesa=3EE6 or vga=791
I again end up with a black screen.

Could somebody be kind enough to help me with that matter ? 
Thanks a lot in advance

---

### Post by adityamagadi on 2012-01-12
are you tryint to install ubuntu with windows alongside it?if yes then first run wubi in windows it ll automatically restart then boot from your ubuntu DVD try this and let me know if it worked :)

---

### Post by debutant10 on 2012-01-12
No I will not have windows alongside ...

---

### Post by adityamagadi on 2012-01-12
why don't u first try booting in as a live session user and then installing it from there.?

---

### Post by debutant10 on 2012-01-12
because both "Try Ubuntu without installing" and "Install Ubuntu"
end up with the same black screen.

---

### Post by adityamagadi on 2012-01-13
then you have either not burnt the iso image properly or your downloaded iso image is itself corrupted.

---

