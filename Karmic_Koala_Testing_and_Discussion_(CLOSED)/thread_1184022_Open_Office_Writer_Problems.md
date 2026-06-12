---
title: "Open Office Writer Problems?"
date: 2009-06-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-06-10
Gday all :)

Since I havent used Open Office Writer in any real depth before, I don't if this is a bug or that the app basically sucks.

When I open my MS Word docx or doc files in Word, its fine. Then I try to do the same in OO Writer and all the formatting is messed up.....

This effectively means I cant use OO because Im required to use the MS Word format in docos.

Bug or lame application?

---

### Post by psyke83 on 2009-06-10
> **Nullack said:**
> Gday all :)

Since I havent used Open Office Writer in any real depth before, I don't if this is a bug or that the app basically sucks.

When I open my MS Word docx or doc files in Word, its fine. Then I try to do the same in OO Writer and all the formatting is messed up.....

This effectively means I cant use OO because Im required to use the MS Word format in docos.

Bug or lame application?

Lame document format... ;)

---

### Post by Nullack on 2009-06-10
Probably, but theres nothing I can do to change that. I'm required to use MS Word format.

OO Writer needs to seamlessly handle this to be taken seriously in any real sense.

EDIT: Mate do you have time please to consider this thread:

[http://ubuntuforums.org/showthread.php?t=1178770](http://ubuntuforums.org/showthread.php?t=1178770)

---

### Post by super.rad on 2009-06-10
Give abiword a try it's always been better at opening word documents than OO, I've never liked OO anyway, way too bloated (takes up over 300mb for the whole thing).

---

### Post by benj1 on 2009-06-10
i swap documents between office and writer all the time and never had a problem, i don't know about .docx format, its newer so probably not as supported.

what problems are you having with .doc ?

---

### Post by Nullack on 2009-06-10
With the .doc Im getting major layout problems with tables and the like. On OO Writer one doco is 4 pages and in Word its only 3 for example. My experience that seems to be repeating itself is that Word to OO and back is very poor.

---

### Post by benj1 on 2009-06-10
ive never had problems with tables (not very helpful i know, sorry)

would the odf plugin for office be helpful (the sun one, not microsofts own included in the latest service pack, its not very good apparently, though don't know if thats just with spreadsheets)

---

### Post by crjackson on 2009-06-10
> **Nullack said:**
> With the .doc Im getting major layout problems with tables and the like. On OO Writer one doco is 4 pages and in Word its only 3 for example. My experience that seems to be repeating itself is that Word to OO and back is very poor.

Table formatting conversion IS a problem for OOo Writer. It actually does a good job, BUT they are trying to CONVERT a proprietary format and apparently that's pretty hard to do.

---

### Post by ranch hand on 2009-06-10
Before really ripping an app for not handeling non-native formats try an .odt in Word.

---

### Post by Nullack on 2009-06-10
Well, I can only say the FOSS ecosystem has done an excellent job with other proprietary formats - such as how we actually have faster and more robust multimedia decoders for technologies that are private closed source.

Unfortunately the ODF sun plugin is only available for Windows, so I cant use it on my wifes mac.

---

### Post by ktp on 2009-06-10
> **psyke83 said:**
> Lame document format... ;)

:lolflag:

---

### Post by ronacc on 2009-06-11
since microsoft is working harder on sabotaging OO compatibility than they are at squashing security bugs , I can only wish you luck and sympathy .

---

### Post by nanog on 2009-06-11
I have enormous problems with ms formats in open office. For enterprise level use (e.g. mb of embedded images, tables, forms, complex macros, VB etc.) its a very bad joke. And font conversion is still a complete fail. Arial narrow, in particular, is the bane of my ****ing existence.  

My current solution: Office 2007 in crossover office 8. In my experience, word runs nearly perfectly. Before crossover 8 I used virtualbox. I am no fan of microsoft but office 2007, once you get used to it, is surprisingly good software. 

(I personally use R or gnuplot for data analysis/graphics, Oo.o for text documents, and evince for presentations.)

---

### Post by knarf on 2009-06-11
> **Nullack said:**
> Gday all :)

Since I havent used Open Office Writer in any real depth before, I don't if this is a bug or that the app basically sucks.

When I open my MS Word docx or doc files in Word, its fine. Then I try to do the same in OO Writer and all the formatting is messed up.....

This effectively means I cant use OO because Im required to use the MS Word format in docos.

Bug or lame application?

Lame document format, as already said. As ODF is available even for Microsoft office you might be able to convince the powers-that-be to use it - in MS Office or another application of choice - at your work as well? As long as you save documents in ODF they should be transferrable between quite a large variety of applications. Even Microsoft Office can be tentatively used as long as you stay away from Microsoft's own ODF 'compatibility' (har har) efforts - use the Sun or CleverAge plugin instead.

There is more than enough material out there on the net you can you as a base to try to convince those who still think Microsoft Office file formats are a good choice for document longevity. They have never been a good choice and, given the current shenanigans Microsoft is pulling with regard to their file formats, seem unlikely to become one. ODF on the other hand is well documented, implemented by several unrelated teams and makes it possible to access the data in the document using nothing more than zip and a text editor if you're in a pinch. And no, that does not work in docx as those files contain binary blobs of unknown composition. If that sounds like something from the Invasion of the Document Snatchers all the better, stay away if you don't want to get assimilated...

---

### Post by Nullack on 2009-06-13
I dont have the influence to change what others specify as their document format. While you and I may care, many people dont. They just want it to work and are creatures of habit.

If Writer wants to be hit the mainstream its got to have seamless compatability with MS Word.

---

### Post by SteveDee on 2009-06-15
1

---

### Post by JohnJackson on 2009-06-16
When I open .docs with tables, all the content in the tables is missing. Opening the same .docs in OpenOffice 3.0 in Jaunty works fine so I think there is a problem with the current OO in Karmic.

---

### Post by nanog on 2009-06-16
> While you and I may care, many people dont.

Actually this misses the point entirely. 

I use open source software for *MY* projects. However, 99.9% of my colleagues don't. If I want to open, edit, or revise files they send me I am often forced to use proprietary software. And while it is theoretically possible to open and edit microsoft office files in open office, more often than not the files become corrupt. I've wasted alot of my colleagues time unwittingly sending corrupt forms, presentations, or text documents.

I've frankly given up on open office as a viable microsoft office replacement. (The fragmented development (sun Oo.o and novell Go.Oo) and terrible "attitude" on the OO.o forums turns me off.) My hope is that microsoft is serious about developing functional odf support. Unless novell or oracle step up with real support I think this is the only way we will get functional interoperability.

---

