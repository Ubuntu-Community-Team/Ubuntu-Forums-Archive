---
title: "pdf fonts all jaggy"
date: 2009-04-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by akahige on 2009-04-21
Using CUPS as my printer (all I do is make PDF's), the fonts come out all jaggy and pixelated.

Looking at the dates of the files in my PDF directory, this started happening one week ago -- I just didn't notice it until now.

Anyone seeing this? Got any suggestions on how I might be able to fix it?

---

### Post by bennachie on 2009-04-21
Sorry, I don't quite understand the parameters of your situation. 

I have normally created documents in PDF format by exporting a file from Open Office, and have experienced no problems in printing those documents. Nor have I had any problems in printing PDF documents which have been downloaded or received via email. Clearly, you are doing something different. If you could expand on your explanation, I'd gladly check whether I can replicate the problem

---

### Post by akahige on 2009-04-21
I'm just creating PDF's from web pages (most frequently), or gedit. And the fonts in the resulting documents are jagged, as if they're very badly rendered.

In looking more carefully at the PDF's, the fonts in the document headers (usually stating file location and page number) are fine -- it's just the body fonts that are trashed. (Which would imply that the fonts have not been corrupted; screen fonts are fine.)

I'm not doing anything different than I've done for years. CUPS printing has always just worked. And it worked fine until something -- I'm guessing something in an update -- broke it.

System is an AMD64 running Ubuntu Jaunty with all the latest updates.

---

### Post by bennachie on 2009-04-21
OK, I think I understand. I've just printed this web page to file from Firefox 3.0.8 (initially selecting PDF rather than PS). The resulting document looks pretty much perfect when I open it in Document Viewer 2.26.0. When I actually print the document, however, there is a very noticeable loss of quality. I would probably describe the fonts as being "fuzzy" or "out-of-focus" rather than "jaggy", but that may just be down to our respective choice of words.

When the same web page is sent directly to the printer, or when it is first saved as a Postscript file, and then printed from Document Viewer, the output is perfect (the PS file itself looks slightly odd - the fonts could well be described as "jaggy" - when opened with Document Viewer, but the printout is sharp and clear).

Are these the effects to which you are referring?

I'm also running the 64-bit version of Jaunty, fully updated, but on an Intel-based machine.

---

### Post by akahige on 2009-04-21
> **bennachie said:**
> OK, I think I understand. I've just printed this web page to file from Firefox 3.0.8 (initially selecting PDF rather than PS). The resulting document looks pretty much perfect when I open it in Document Viewer 2.26.0. When I actually print the document, however, there is a very noticeable loss of quality. I would probably describe the fonts as being "fuzzy" or "out-of-focus" rather than "jaggy", but that may just be down to our respective choice of words.

I agree about the choice of words. I think we're talking about the same thing here.


> **bennachie said:**
> When the same web page is sent directly to the printer, or when it is first saved as a Postscript file, and then printed from Document Viewer, the output is perfect (the PS file itself looks slightly odd - the fonts could well be described as "jaggy" - when opened with Document Viewer, but the printout is sharp and clear).

Are these the effects to which you are referring?

I'm also running the 64-bit version of Jaunty, fully updated, but on an Intel-based machine.

Now that we're on the same page with regard to the description of the results, I tried some different things based on some of the tests that you ran...

If I PRINT a job using the PDF printer, it's got the fuzzy font problem.
If I SAVE the same job as a PS, it's perfect.
If I SAVE the same job as a PDF, it's also perfect.

Here's where things get very strange. I'm using Acrobat Reader 8.1.3 as my PDF viewer. If I look at the same problematic PDF's in Document Viewer 2.26.0, they look vastly better, but not perfect in all cases.

What does that suggest to you?

---

