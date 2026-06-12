---
title: "Printer"
date: 2009-03-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by allstar1971 on 2009-03-16
I am running Ubuntu Jaunty and when I try to access my printer to ake changes, it crashes and the printer box that lists the printer will not show up.

I am runnung AMD 3700+ 2gb memory and GF4 video card. Everything prints fine in openoffice, etc. 

But I added memory and I can't access my printer to make changes.

I have an hp8550

---

### Post by overdrank on 2009-03-16
Moved to  Jaunty Jackalope Testing and Discussion

---

### Post by sgosnell on 2009-03-16
No clue.  I haven't seen that behavior with my HP (different model) or with other printers.  Have you tried deleting the printer and adding a new one?  You might need to reinstall cups, but that wouldn't be my first try.

---

### Post by renkinjutsu on 2009-03-16
After updating hplip, i lost driver support for my HP Photosmart C4180.. anyone else experiencing something similar?

it's strange, because on hplip website, it says my printer model is supported, but i don't see any of the photosmart c4100 series in the list..

---

### Post by Gramps on 2009-03-16
With Jaunty being Alpha the 1st thing I woould do is any update to make sure all the packages are up to date.

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

I know the other day all of a sudden I couldn't print eithe local or over the network, my printer is on my Jaunty machine. What I ended up doing was turn the printer off, pulled the usb cable. Then deleted the printer. Plugged the usb cable in and power up the printer, Jaunty saw it and configured it and all was then fine. I had to go and tell it to broadcast the it was available but other than that it was good to go.

---

### Post by allstar1971 on 2009-03-17
I have run the latest updates and reinstalled everything. I noticed that 64-bit Ibex did the same thing. I will run more tests and have an update

---

### Post by allstar1971 on 2009-03-17
I have the same problem happening in ibex.

It says" Application Problem."

Sorry, the program "System-config-printer.py" closed unexpectedly.


It happens everytime I try to run the "configure printers" icon in "System-Administration."

---

### Post by DougieFresh4U on 2009-03-17
Yesterday I was not able to print using hp deskjet 5550. Kept getting error 'printer may not be connected'. I ended up  reinstalling cups and I reinstalled some foomatic packages and then all was good. Not sure which caused the error.
May not help, but updates over the last few days (un)did some thing.

---

### Post by sgosnell on 2009-03-17
Try reinstalling python.  If it's crashing running a python script, which it apparently is, you probably have a python problem, not a printer problem.

---

### Post by allstar1971 on 2009-03-18
The new update fixed the issue. Now the box shows up.

---

