---
title: "cannot boot 10.04 final"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by mechlad on 2010-05-05
I have a gateway m305-crv laptop. I am unable to boot to my login page after installing 10.04. The beta 2 version booted fine, untill I updated through the update manager. then upon booting, I see the ubuntu splash screen then followed by a blank screen. 
I have reinstalled with the offical release of 10.04, but am getting the exact same thing as when I upgraded the beta2 version (splash followed by blank screen). i thne tried the alternative cd but same outcome.
the specs for the m305-crv are:
p4
1g ram
Intel 852MG chipset
 
any Idea why this is occuring or how to remedy?

---

### Post by Rasa1111 on 2010-05-05
Can you get to the 'purple screen'.. with the two white logos at the bottom?
[a keyboard and a person in a circle]

 If you can get to that screen...

Hit spacebar... and see if it doesnt pull up the regular Ubuntu menu... 

 This was happening to me as well,
but the member Irihapeti helped me, ...

and in the end, it was easier to 'fix' than we thought. 

Simply hitting spacebar at the purple screen was all it took for me to get into the menu to install. 

hope it helps, but if not.. someone else will be along....

good luck

---

### Post by kansasnoob on 2010-05-05
> **mechlad said:**
> I have a gateway m305-crv laptop. I am unable to boot to my login page after installing 10.04. The beta 2 version booted fine, untill I updated through the update manager. then upon booting, I see the ubuntu splash screen then followed by a blank screen. 
I have reinstalled with the offical release of 10.04, but am getting the exact same thing as when I upgraded the beta2 version (splash followed by blank screen). i thne tried the alternative cd but same outcome.
the specs for the m305-crv are:
p4
1g ram
Intel 852MG chipset
 
any Idea why this is occuring or how to remedy?

Can you run the Live CD, I mean run the Live Desktop from the CD?

If so post the output of:

```
lspci | grep VGA
```

I suspect something similar to this:

[http://ubuntuforums.org/showthread.php?t=1472430](http://ubuntuforums.org/showthread.php?t=1472430)

But that's a shot in the dark ;)

---

### Post by Rasa1111 on 2010-05-05
> **kansasnoob said:**
> Can you run the Live CD, I mean run the Live Desktop from the CD?

If so post the output of:

```
lspci | grep VGA
```I suspect something similar to this:

[http://ubuntuforums.org/showthread.php?t=1472430](http://ubuntuforums.org/showthread.php?t=1472430)

But that's a shot in the dark ;)


 I couldnt even get to the LiveCD desktop until I did what I said in me previous post.
it would just 'hang' and do nothing.

---

### Post by mechlad on 2010-05-05
I actually have it installed without any errors during the process. Upon the reboot after instaltion I get the boot screen and then nothing. I pressed shift after post and got into grub and selected low graphics mode and selected to run in that mode for this session only, then I can get to desktop.
9.1 worked almost flawlessly on this machine.

---

### Post by Rasa1111 on 2010-05-05
> **mechlad said:**
> I actually have it installed without any errors during the process. Upon the reboot after instaltion I get the boot screen and then nothing. I pressed shift after post and got into grub and selected low graphics mode and selected to run in that mode for this session only, then I can get to desktop.
9.1 worked almost flawlessly on this machine.

ohh, i see....
yeah that is beyond my abilities to help atm.. 
im sorry.

9.10 worked great on this machine to..
so I was rather disappointed when I learned that I could not get Lucid to work. 

after all the help here though...
my disappointment level went back down to zilch, really. 

and now I cannot believe how great it works.. ...

 When proper help does finally 'arrive' in this thread, and you do get it working....
I think you will be amazed with it. 

 I was amazed by 9.10..... 
but this [10.04]....
is just unbelievable to me. lol

So.. another [BUMP] for mechlads thread....
the fix is not far.. I can feel it........ lol

---

