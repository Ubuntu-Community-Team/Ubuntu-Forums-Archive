---
title: "Ugly fonts in Evince, ePDFViewer...Poppler?"
date: 2009-09-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Bastanteroma on 2009-09-01
PDFs opened in Evince or ePDFViewer, both of which I think use the poppler library, display blocky fonts with no apparent anti-aliasing. The same PDFs in Acrobat or XPDF display fine.

This is true with PDFs that appear to have been scanned in and are maybe image-based and some that, as far as I can tell, are generated from text. Msftcorefonts are installed.

Screenshots attached.

---

### Post by sam81 on 2009-09-02
It's a known issue, there is a bug filed upstream [http://poppler.freedesktop.org/](http://poppler.freedesktop.org/)
hope it gets fixed soon...

---

### Post by hugmenot on 2009-09-02
This is not a font issue. It&#8217;s a problem of filtering images properly.

---

