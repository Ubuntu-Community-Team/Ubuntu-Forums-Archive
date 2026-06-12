---
title: "Printer problems"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Ewingo401 on 2009-04-05
Hey guys.  I've got an Epson Stylus-CX4800 that I'm having some problems with in Jaunty.  It seems to at least recognize the printer because every time I try to print it says "Stylus-CX4800 may not be connected".  I have of course verified that it is turned on and connected properly.  This printer worked without any issues in Intrepid.  Does anyone have ideas I might try to get it up and running again?

---

### Post by bennachie on 2009-04-05
> **Ewingo401 said:**
> Hey guys.  I've got an Epson Stylus-CX4800 that I'm having some problems with in Jaunty.  It seems to at least recognize the printer because every time I try to print it says "Stylus-CX4800 may not be connected".  I have of course verified that it is turned on and connected properly.  This printer worked without any issues in Intrepid.  Does anyone have ideas I might try to get it up and running again?

Did you have any problems, or any unusual responses, while configuring the printer using system>administration>printing ?

---

### Post by Ewingo401 on 2009-04-06
I never actually configured it.  It seems to have picked it up automatically as it did in Intrepid.  I did notice that if I go into printer properties it shows "printer state idle Printing page 1, 12%" but there is nothing currently in the print queue.  And if I got to ink/toner levels the status message is still showing "printer may not be connected".

---

### Post by nwadams on 2009-04-06
ya, umm it does that for me too. try to reinstall it and instead of using the default driver, use the foomatic driver or whatever its called

---

### Post by Ewingo401 on 2009-04-06
> **nwadams said:**
> ya, umm it does that for me too. try to reinstall it and instead of using the default driver, use the foomatic driver or whatever its called

That fixed the problem.  Thank you very much!

---

### Post by nwadams on 2009-04-06
your welcome, for some reason the new default recommended drivers do not work...

---

### Post by BazinFS on 2009-04-06
Thanks, I had the same problem with my Epson stylus CX4800

---

### Post by wieman01 on 2009-04-11
Just to recapture what I did to resolve the problem. 

a. Reinstall Foomatic.
b. Removed the old printer using CUPS web interface.
c. Add it again.
d. Print a test page.

Works fine for me now. Thank you, guys. Good job!

---

### Post by Kivech on 2009-04-12
Had the same problem with my Stylus Office BX300F and got it printing now.

Anyone have any idea how to get the scanner part working? Xsane doesn't even recognize it.

---

### Post by nwadams on 2009-04-12
i've never used a scanner before so i'm somewhat in the dark. Did it work in intrepid/hardy? if so check the drivers ofr it because it may have been using the "new" driver that doesn't work.

---

