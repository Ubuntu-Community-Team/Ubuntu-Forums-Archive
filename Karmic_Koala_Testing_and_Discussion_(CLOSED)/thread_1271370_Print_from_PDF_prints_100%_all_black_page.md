---
title: "Print from PDF prints 100% all black page"
date: 2009-09-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Skipnaz on 2009-09-20
My PDF opens in Document Viewer 2.27.90 and the images in the viewer look good
When I print the pages to my printer they come out all black
I can't say when this started cause I haven't printed a pdf to my Canon i850 in a long time
Test page, jpg, text prints properly, 
I clicked New button and a new i850 was created but that didn't help
Anyone see the same or is this just a alpha6 bug. Watch out on wasting a full page of ink

By the way, I just updated my alpha6 an hour ago with 68 updates all installed cause I waited a couple of days and my box boots

---

### Post by hambone79 on 2009-09-20
I don't know if this is related to the problem you are having, but every time I print a PDF from Evince Document Viewer it crops off about 1/4 of the outer edge of what I was trying to print. After wasting about half a pack of paper trying to print technical drawings for work, I finally gave up and installed Adobe Reader. I still use Evince to view documents, but I print everything with Adobe Reader.

---

### Post by kansasnoob on 2009-09-20
Hmmmm, I just tried printing a page from my Hanns-G pdf booklet and it came out totally blank other than a "-" at the top!

So you're not alone!

Hey, look mom, a new way to save ink:lolflag:

I have an HP Deskjet 5440, so it's not printer specific!

---

### Post by kansasnoob on 2009-09-20
I've done a bit of googling but I suppose we need to file a bug report as I'm not finding what we need.

Closest:

[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/258421](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/258421)

but that says, "fixed in Karmic".

I'm multi-booting so I'll try pdf printing in another OS, probably Jaunty, then I'll try my best to write a bug report.

I suck at writing bug reports!

---

### Post by kansasnoob on 2009-09-21
Well, this is odd.

I rebooted and tried Jaunty just to see if pdf printing worked OK there, and it did.

Then I booted back into Karmic and tried again thinking that I'd try to find some kind of cups records to produce a report from ............. but it seems to be working now!

No idea why, I don't think there have been any cups updates since I last rebooted.

But Nautilus crashes a lot! So maybe when Nautilus crashes it breaks other things.

---

### Post by Skipnaz on 2009-09-21
I think I got a bad PDF file or something. This pdf will print out correctly on my Jaunty box and prints solid black on my Karmic box. I checked a few other random pdf I had and they printed out on Karmic, so it seems that its just this one pdf that won't print on Karmic. I should have checked others before I posted this. Its a utility bill from my electric Co. All the previous ones print on paper OK, its just this one that won't and I just dnloaded it again and it still prints solid black as night. 
Thanks all

---

