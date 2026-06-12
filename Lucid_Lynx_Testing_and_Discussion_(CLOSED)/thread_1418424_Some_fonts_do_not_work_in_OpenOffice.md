---
title: "Some fonts do not work in OpenOffice"
date: 2010-02-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by cristianrosa on 2010-02-28
I'm running Lucid Aplha3 Live and I was playing with Open Office writer when I realized that the fonts "Century Schoolbook L" and "URW Palladio L" are not working, they fallback to some another font.
Look at the screenshot attached.

Does anyone have the same problem?

---

### Post by nanog on 2010-02-28
Yes. Grrrrr! 

A microsoft font patent issue compounded by open office's idiotic font handling causes this very unfortunate bug. Some fonts that install perfectly well in ubuntu do not show up in open office.

```
/usr/lib/openoffice/program/spadmin
``` 

[PHP]click the "Fonts" button and then "add".[/PHP]

You will need the TTF fonts from another install/os.

I place them in my ~/.fonts directory for convenience.

---

### Post by cristianrosa on 2010-03-01
Thank you, maybe the best solution for Lucid would be not to list the not working fonts. This way people won't try to use it?

---

### Post by nanog on 2010-03-03
There was an open bug about this. I think the problem is that sun/openoffice believe this is a "feature" not a bug.

---

