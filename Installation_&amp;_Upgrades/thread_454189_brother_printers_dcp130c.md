---
title: "brother printers dcp130c"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by mszl_1 on 2007-05-25
i have a brother dcp 130c multifiunction printer. i know it works in linux as  linuxprinting informs me so. i also know it is not (yet) part of the foomatic thingy, however i need to get this printer to work. thing is how do i do that?? 
thanks

---

### Post by stefaan.dutry on 2007-05-25
Have you tried the method suggested at this page yet?

[http://www.freesoftwaremagazine.com/articles/printing_ubuntu]("http://www.freesoftwaremagazine.com/articles/printing_ubuntu")

Sorry if it's not to the point, I don't know much but i still try to help anyway.

---

### Post by mszl_1 on 2007-05-28
stefaan.dutry
ive read the page however when i open the list of printers that are suppirted in the database,  my printer is not there. its younger brother is though(pardon the pun) i know i have to download the cups wrapper and someting else, what, i dont know. this is why im posting to get info so i can try to get the printer to work.

---

### Post by stefaan.dutry on 2007-05-29
> **mszl_1 said:**
> stefaan.dutry
ive read the page however when i open the list of printers that are suppirted in the database,  my printer is not there. its younger brother is though(pardon the pun) i know i have to download the cups wrapper and someting else, what, i dont know. this is why im posting to get info so i can try to get the printer to work.

This is the page i think you'll need:

[http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html]("http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html")

Problem is I see 2 types of drivers on it and i don't know which one you'll need to use (scroll down to see the driver itself, there's a list of printers there)

Also i see on the following page:

[http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install.html]("http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install.html")

instruction to install the cups wrapper. Again for 2 types, and again I don't know which one you'll need.

So since I know so little about these things,  that's all the help i can offer you.

Hope the sites were of some use.

Sorry for my ignorance on the matter.

---

### Post by mszl_1 on 2007-05-29
ok, now since  we know that does that mean that i would have to DL the Debian drivers as Ubuntu is Debian based?

---

### Post by dolphin_oracle on 2007-05-29
yep.  i've got a mfc9700 running on edgy.  Use the debian files.

---

### Post by mszl_1 on 2007-05-29
thanks ill have a go tonight. i do not know how to complie from sourse (yet) im hoping i dont have to do so in order to get the printer working!!;)

---

### Post by dolphin_oracle on 2007-05-29
no source compiling required...the debs are binary files.  I looked up the info for your printer, and you'll need to get both the lpr drivers and the cupswrapper driver.  Just read the faqs and instructions on Brother's site (there is a set specifically for your printer).

You may also like a faq by Bob Songs. Its about another Brother printer, but they all install about the same way.

good luck.

[http://ubuntuforums.org/showthread.php?t=105703](http://ubuntuforums.org/showthread.php?t=105703)

---

