---
title: "How do I uninstall Adobe Reader?"
date: 2024-04-28
forum: Installation &amp; Upgrades
---

### Post by cbiweb on 2024-04-28
I installed Adobe Acrobat Reader with this command:
```

[COLOR=#000000][FONT=Arial][SIZE=2]wget ftp://ftp.adobe.com/pub/adobe/reader/unix/9.x/9.5.5/enu/AdbeRdr9.5.5-1_i386linux_enu.deb[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Arial][SIZE=2]--2024-04-28 11:09:39--  ftp://ftp.adobe.com/pub/adobe/reader/unix/9.x/9.5.5/enu/AdbeRdr9.5.5-1_i386linux_enu.deb[/SIZE][/FONT][/COLOR]

```
This is the ouput:
```

 [COLOR=#000000][FONT=Arial][SIZE=2]=> &#8216;AdbeRdr9.5.5-1_i386linux_enu.deb&#8217;[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial][SIZE=2]Resolving ftp.adobe.com (ftp.adobe.com)... 193.104.215.67[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial][SIZE=2]Connecting to ftp.adobe.com (ftp.adobe.com)|193.104.215.67|:21... connected.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial][SIZE=2]Logging in as anonymous ... Logged in![/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial][SIZE=2]==> SYST ... done.    ==> PWD ... done.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial][SIZE=2]==> TYPE I ... done.  ==> CWD (1) /pub/adobe/reader/unix/9.x/9.5.5/enu ... done.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial][SIZE=2]==> SIZE AdbeRdr9.5.5-1_i386linux_enu.deb ... 60085406[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial][SIZE=2]==> PASV ... done.    ==> RETR AdbeRdr9.5.5-1_i386linux_enu.deb ... done.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial][SIZE=2]Length: 60085406 (57M) (unauthoritative)[/SIZE][/FONT][/COLOR]
 
 
 [COLOR=#000000][FONT=Arial][SIZE=2]AdbeRdr9.5.5-1_i386 100%[===================>]  57.30M   376KB/s    in 2m 46s  [/SIZE][/FONT][/COLOR] 
 
 
 [COLOR=#000000][FONT=Arial][SIZE=2]2024-04-28 11:12:28 (353 KB/s) - &#8216;AdbeRdr9.5.5-1_i386linux_enu.deb&#8217; saved [60085406][/SIZE][/FONT][/COLOR]

```

After it finished, I checked Applications but it was nowhere to be found.
When I open a PDF, it still launches Document Reader.
There is no .deb or other package for it in Downloads.

Since I can't find Adobe Reader anywhere, no point in keeping it, but I don't know the uninstall command for it.

I tried the usual commands, but no go.

---

### Post by deadflowr on 2024-04-28
wget would have downloaded the deb to the current working directory.
So check the top level of Home.

---

### Post by cbiweb on 2024-04-28
> **deadflowr said:**
> wget would have downloaded the deb to the current working directory.
So check the top level of Home.

And there it is. Thank you!

---

### Post by deadflowr on 2024-04-28
Does it actually install?

---

### Post by TheFu on 2024-04-28
I haven't used anything from Adobe in about 15 yrs.  Their management lost their way and made poor choices with Flash, so they lost my trust.  For all this time, I've been very clear. If you don't earn a living using Adobe software, then it is best to avoid it completely. Definitely casual users should avoid Adobe stuff.  For many years, the number of security bugs in Adobe software was nearly as many as found in MSFT software and that's comparing about 50 MSFT products to perhaps 10-15 Adobe tools. Their quality of code was just some of the worst in the world that was used massively and found to be huge security risks, consistently.

To my knowledge, all Adobe Reader provides is the latest support for the PDF format which they are the corporate sponsor behind.  F/LOSS programs use libpdf with has supported v2.0 of the PDF spec for years now.  So unless the PDF creator just wants to screw with the world and defaults to using features that only the latest Adobe creation tools support (like Adobe Distiller), then you won't really have any compatibility issues with PDFs for about the last 3-4 yrs. Documents older than that will use 2.0 and older PDF formats, with v1.6 being the largest number of created documents.

Certain govt agencies are known to publish their PDF files initially with "use latest PDF version" enabled until a number of people complain and they republish using a few version older PDF version.

When I'm talking about PDF versions, those don't related to Adobe programs.  They are the industry group standards for the data format that a PDF document follows.

IMHO, Adobe tweaks the PDF document versions just to sell new software. There hasn't been anything added that was really important for 99.9999% of the world in over 15 yrs. Basically, we just want them to recompile their software for new OS releases and to use newer OS libraries.  But it is hard for a commercial software company to earn much doing that.

You can read up on which versions of PDF support which major features, if you care.  
[https://pdfa.org/resource/pdf-specification-archive/](https://pdfa.org/resource/pdf-specification-archive/)
[https://en.wikipedia.org/wiki/History_of_PDF](https://en.wikipedia.org/wiki/History_of_PDF) is probably easier to digest.

---

### Post by Impavidus on 2024-04-28
Adobe hasn't released a new version of Acrobat Reader for Linux since 2013, so I very much doubt it would install, let alone run. The libraries it depends on must be ancient history by now.

---

### Post by TheFu on 2024-04-28
If they only use core libraries and find functions by name, they will still work.  In theory.

---

