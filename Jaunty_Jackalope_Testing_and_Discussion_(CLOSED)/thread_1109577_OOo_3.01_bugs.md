---
title: "OOo 3.01 bugs"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by John Jason Jordan on 2009-03-28
I have been a power user of OOo since before moving from Windows to Linux (Hoary). If anyone is going to find something wrong it is me.

To test this you need OOo 3.01 on Jaunty, although it also happens on Intrepid. But if you install 3.01 on Hardy it does not happen. It is an Intrepid bug that has not been fixed in Jaunty, which is why I think I need to report it as a bug.

Here is a test: Open a new, blank Writer (text) document. Create a frame with two or more columns. In the frame insert a table with one row and two columns. Set the first column to half an inch or 1.5 cm, or thereabouts, leaving the right column for the rest of the table.

With the cursor in the right column go to Insert > Object > Formula. When the formula editing window appears enter the following in the syntax window:

font Sans bold left [ font Serif nbold { alignl stack { something # anything # nothing # everything } } right ]

Having done so, exit the formula editing window by clicking anywhere in the document except on the formula.

Now copy the table, hit a carriage return, and paste it in below. Double click on the second formula to make the editing window appear. Delete the last item from the stack. Again, click anywhere in the document other than in the formula to make the formula editing window disappear.

Repeat, deleting another item from the stack so you now have three formulas in tables in a column in your frame. The formulas will have 4, 3, and 2 items in their stacks.

In OOo 3.01 in Hardy the brackets are all the same, just bold. What you will see on screen for Intrepid/Jaunty is that the left and right bracket are bolder according to how many items in the stack. The more items, the bolder the bracket. 

Print the page. You will find that the brackets probably print just bold.

Now go back to the formulas and make the items in the stack longer, like change "something" to "something-something-something." Print again. While the screen view remains the same (incorrect because the thickness of the bracket varies according to the number of items in the stack), the print output will eventually print one of the brackets super-fat, like six times as bold as it is supposed to be.

Now export to PDF and open in your favorite PDF viewer. You will find that the brackets vary according to the number of items in the stack. In other words, OOo PDF export must be using the screen view somehow.

It is actually more sinister and deep than the above indicates. I find constant problems in OOo and in Scribus when I apply bold attributes to a font. This never happened in Hardy, started in Intrepid, and continues in the beta of Jaunty.

The above has been confirmed by another user on the OOo user e-list. He has machines with Hardy and Intrepid, and each has OOo 2.4.1 and 3.0.1. His machines are all 32-bit and mine is x86_64.

I suspect the problem is somehow related to the new video drivers that came with Intrepid, although the problem continues in Intrepid whether I use the nv driver or the nVidia driver for my nVidia video chip.

I can also confirm that similar problems occur when bolding text in Scribus and AbiWord. In other words, it an Ubuntu problem, not just an OOo problem. Having said that, it may lie in Gnome rather than OOo itself.

I feel I need to file a bug report, and ASAP, due to the fast approaching deadlines for Jaunty. I don't even know how to file a bug report. I need confirmation from someone else here, and instructions for how to file the bug report.

---

### Post by Nullack on 2009-03-28
Please look at the contributing to Jaunty thread, theres lots of info.

---

### Post by John Jason Jordan on 2009-03-29
I need someone to confirm the problem. I have discovered that it happens in KWord and Scribus as well as OOo, so the problem is somewhere in Jaunty.

Open a new, blank document in OOo, KWord or Scribus. Copy and paste the following line:

Linguists need combining diacriticals to type a word like [b&#618;t&#865;&#643;].

Now set the sentence to Bold. What happens to the IPA characters at the end?

I have constant problems using Bold attribute for text. Sometimes the character simply drops out. Other times the program I am using will think the font does not have the character and substitute the character from another font. 

I also have problems with programs not seeing all the glyphs available in a font. 

I first noticed this problem in Intrepid using OOo. I have confirmation from a user on the OOo e-list that it happens for him in Intrepid also, but that it does not happen in Hardy (he has test machines). 

I intend to file a bug report, but whatever confirmation I can get from this forum will help steer the bug report to where it belongs.

---

### Post by John Jason Jordan on 2009-03-29
I have filed a bug report on this here:

[https://bugs.launchpad.net/ubuntu/+bug/351080]("https://bugs.launchpad.net/ubuntu/+bug/351080")

---

