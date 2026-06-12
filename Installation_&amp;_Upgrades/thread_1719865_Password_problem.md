---
title: "Password problem"
date: 2011-04-02
forum: Installation &amp; Upgrades
---

### Post by Birdsg on 2011-04-02
I have pruchased a Dell mini and the previous owner does not remember the password. I've had this unit for a couple of years and am currently reinvesting my interest in it and Unix Is there any help in getting around this password issue?

---

### Post by oldos2er on 2011-04-02
If it's running Ubuntu, see [http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)

---

### Post by coffeecat on 2011-04-02
@Birdsg, would that be a Dell Mini running Ubuntu 8.04? Normally I would agree with oldos2er about trying that psychocats link, but if memory serves correct Dell did something rather peculiar with the grub setup on their pre-installations by setting the menu timeout at zero with a hidden menu. Which means that however much or quickly you press esc (for legacy grub) you can't get to the grub menu in order to be able to boot up into recovery mode.

If that's not a Dell preinstall then ignore me, but if it is and you can't get to the grub menu, then have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1163371](http://ubuntuforums.org/showthread.php?t=1163371)

You can skip over my posts - I was not much help - but if you go down to where aysiu joins in (who coincidentally wrote that psychocats guide) he has a fix.

To be honest it puzzled me because if you can boot into a live USB running Ubuntu, you should be able to mount the internal Ubuntu partition and edit menu.lst directly - so long as you have legacy grub. Or perhaps I'm missing something.

---

### Post by gordintoronto on 2011-04-02
The other option would be to just install a current version of Ubuntu.

---

